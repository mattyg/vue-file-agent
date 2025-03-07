# Vue File Agent

>  Every file deserves to be treated equally

High performant Vue file **upload** component with elegant and distinguishable **previews** for every file type and support for **drag and drop**, **validations**, default uploader with **progress** support and externally customizable in the "vue way"

<div class="clearfix"></div>

## [Live Demo][] · [CodePen Playground](https://codepen.io/safrazik/pen/BaBpYme)

![Demo](website/assets/demo.gif)


## Features

- Exclusively designed for Vue with performance and simplicity in mind
- No dependency but small footprint - **17KB** minified, gzipped
- Elegant and responsive design with two official themes: grid view and list view
- File input with drag and drop with support for folders
- Smooth Transitions
- Multiple File Uploads
- Max File Size, Accepted file types validation
- Image/Video/Audio Previews
- File type icons
- Default uploader with progress 
- Externally controllable via Vue bindings and methods
- Built in support for server side validation and error handling
- Official [Upload Server Examples](upload-server-examples) for **PHP** and **Node Js**
- File names can be edited with `:editable` prop
- Intuitive drag & drop sortable with `:sortable` prop
- Resumable uploads with `:resumable` prop through [tus.io](https://tus.io) protocol
- Can be used with any css/component framework, including but not limited to: Bootstrap, Bulma, Tailwind, Vuetify, etc.


## Basic Usage


<!-- #### Template -->

<!-- {% raw %}) -->
```html
<template>
  <VueFileAgent
    :uploadUrl="uploadUrl"
    v-model="filesData"
  ></VueFileAgent>
</template>
```
<!-- {% endraw %}) -->

**NOTE:** when `uploadUrl` is provided, auto uploading is enabled. See [Advanced Usage](#advanced-usage) section below for manual uploading example.

<!-- #### Script -->

<!-- ```javascript -->
```html
<script>
export default {
  data(){
    return {
      // ...
      filesData: [],
      uploadUrl: 'https://example.com',
      // ...
    };
  },
  // ...
}
</script>
```

### That's it?

Yes. That's it. It's *that* simple. See [Advanced Usage](#advanced-usage) section below to tailor it for your specific needs.

## Installation

```
npm install vue-file-agent --save
```

```javascript
import Vue from 'vue';
import VueFileAgent from 'vue-file-agent';
import VueFileAgentStyles from 'vue-file-agent/dist/vue-file-agent.css';

Vue.use(VueFileAgent);
```

or with script tag

```html
 <!-- jsdelivr cdn -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/vue-file-agent@latest/dist/vue-file-agent.css">
  <script src="https://cdn.jsdelivr.net/npm/vue-file-agent@latest/dist/vue-file-agent.umd.js"></script>

  <!-- unpkg -->
  <link rel="stylesheet" href="https://unpkg.com/vue-file-agent@latest/dist/vue-file-agent.css">
  <script src="https://unpkg.com/vue-file-agent@latest/dist/vue-file-agent.umd.js"></script>
```

[Download from Github](https://github.com/safrazik/vue-file-agent/releases)

## Advanced Usage


<!-- #### Template -->
<!-- {% raw %} -->
```html
<template>
  <VueFileAgent
    ref="vueFileAgent"
    :theme="'list'"
    :multiple="true"
    :deletable="true"
    :meta="true"
    :accept="'image/*,.zip'"
    :maxSize="'10MB'"
    :maxFiles="14"
    :helpText="'Choose images or zip files'"
    :errorText="{
      type: 'Invalid file type. Only images or zip Allowed',
      size: 'Files should not exceed 10MB in size',
    }"
    @select="filesSelected($event)"
    @delete="fileDeleted($event)"
    v-model="filesData"
  ></VueFileAgent>
  <button
    :disabled="!filesDataForUpload.length" 
    @click="uploadFiles()"
  >
      Upload {{ filesDataForUpload.length }} files
  </button>
</template>
```
<!-- {% endraw %}) -->
<!-- #### Script -->

<!-- ```javascript -->
```html
<script>
export default {
  data: function(){
    return {
      filesData: [],
      uploadUrl: 'https://www.mocky.io/v2/5d4fb20b3000005c111099e3',
      uploadHeaders: {'X-Test-Header': 'vue-file-agent'},
      filesDataForUpload: [],
    };
  },
  methods: {
    uploadFiles: function(){
      // Using the default uploader. You may use another uploader instead.
      this.$refs.vueFileAgent.upload(this.uploadUrl, this.uploadHeaders, this.filesDataForUpload);
      this.filesDataForUpload = [];
    },
    deleteUploadedFile: function(fileData){
      // Using the default uploader. You may use another uploader instead.
      this.$refs.vueFileAgent.deleteUpload(this.uploadUrl, this.uploadHeaders, fileData);
    },
    filesSelected: function(filesDataNewlySelected){
      var validFilesData = filesDataNewlySelected.filter(fileData => !fileData.error);
      this.filesDataForUpload = this.filesDataForUpload.concat(validFilesData);
    },
    fileDeleted: function(fileData){
      var i = this.filesDataForUpload.indexOf(fileData);
      if(i !== -1){
        this.filesDataForUpload.splice(i, 1);
      }
      else {
        this.deleteUploadedFile(fileData);
      }
    },
  }
}
</script>
```

## License

The MIT License


## [Live Demo][]


[Live Demo]: https://safrazik.github.io/vue-file-agent
