# Change Log

### 1.4.2

- Intuitive drag sort! `sortable` prop improved to support `handle` and `hold` values #30

### 1.4.0 Spotted Pardalote

- New Feature 🎉 Drag sortable support with `sortable` prop (courtesy of vue-slicksort by @Jexordexan) #20

### 1.3.5

- Fixed removal of same file selection in single mode #29
- Improved progress UI with `full` (100% uploaded) and `done` (server returned a response) status.
- Improved upload error handling.
- Added support to dismiss error messages by clicking on them.
- Added support for update/rename upload with `PUT` request, with updated server examples. (Thanks to @codeflorist) #23

### 1.3.4

- Fixed image thumbnails with wrong orientation (rotation) #28

### 1.3.3

- File icons can be clicked with `linkable` property (Thanks to @codeflorist) #24

### 1.3.1

- Major CSS (SCSS) refactoring with modular styles.

### 1.3.0 Rock Wren

- New Feature 🎉 Support dropping folders (Thanks to @kevinleedrum) #17
- Exposed `utils`, `VueFilePreview` and `FileData`
- Allow raw file data in `VueFilePreview` component #18
- Fixed a crossbrowser issue when creating video thumbnails (tainted canvas)
- Vibrant update for default theme with seamless background for meta.
- Error message style updated for both themes
- Progress bar updated for both themes
- Project logo added

### 1.2.0 Yellow Canary

- Initial Unit Tests added #3
- New Feature 🎉 File names can be renamed with `editable` prop #5
- Added `disabled` prop #8
- Added new slots `file-preview` and `file-preview-new` #10
- Made CSS modular and added SCSS support #11
- Added support for custom `FormData` #12
- Added [Gmail Inspired Demo](https://safrazik.github.io/vue-file-agent/docs/#gmail-inspired-demo) in Docs page
- [BREAKING CHANGE] `Raw FileData.name` is a function now.

### 1.1.2

- Basic TypeScript support (Thanks to @yanqd0 & @seriouslag) #4 #7 #9

### 1.1.1 Humming Bird

- Internal code refactor
- Added `thumbnailSize` prop
- Theme support with `theme` prop
- Official `list` theme added 🎉
- Added slots: `before-outer`, `before-inner`, `after-inner`, `after-outer`
- `min-width` added for file previews in default (grid) theme
- Moved component logic (js) to mixin, for extending templates

### 1.0.5

- Fixed a CSS issue that prevented the file input button to be triggered  #1

### 1.0.4 Zebra Finch

- Initial Release