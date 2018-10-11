# markdown-it-atrules
# Work in progess

> markdown-it plugin for embedding MFR files.

## Usage


```js
  md = require('markdown-it')({
    html: true,
    linkify: true,
    typography: true,
  }).use(require('../'), {
    type: 'osf',
    pattern: /^http(?:s?):\/\/(?:www\.)?[a-zA-Z0-9 .:]{1,}\/render\?url=http(?:s?):\/\/[a-zA-Z0-9 .:]{1,}\/([a-zA-Z0-9]{5})\/\?action=download|(^[a-zA-Z0-9]{5}$)/,
    format(assetID) {
      var id = '__markdown-it-atrules-' + (new Date()).getTime();
      return '<div id="' + id + '" class="mfr mfr-file"></div>' +
        '<script>$(document).ready(function () {new mfr.Render("' + id + '", "' + getMfrUrl(assetID) + '");    }); </script>';
    }
```
