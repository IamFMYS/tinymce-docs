
## content_css
It is usually desirable that TinyMCE's editable area has the same styling as the surrounding content. Consistent styling is achieved with the `content_css` option, which enables you to extend external CSS into the editable area.

The CSS file used in this setting should be the same css file that controls the look and style of all your pages. So, let's say you include a file `myLayout.css` in all your pages to control your site's global appearance, then this file must be set as your `content_css` value. Doing this ensures the content in the editable area also has your site's style.

> Note: If you specify a relative path, it is resolved in relation to the URL of the (HTML) file that includes TinyMCE, not relative to TinyMCE itself.

**Type:** `String`, `Array`

##### Absolute path example

```js
// File: http://domain.mine/mysite/index.html

tinyMCE.init({
  selector: 'textarea',  // change this value according to your HTML
  content_css : '/myLayout.css'  // resolved to http://domain.mine/myLayout.css
});
```

##### Relative path example

```js
// File: http://domain.mine/mysite/index.html

tinyMCE.init({
  selector: 'textarea',  // change this value according to your HTML
  content_css : 'mycontent.css'  // resolved to http://domain.mine/mysite/mycontent.css
});
```

##### Using multiple stylesheets example

```js
tinyMCE.init({
  selector: 'textarea',  // change this value according to your HTML
  content_css : 'mycontent.css,mycontent2.css'  // includes both CSS files in header
});
```

##### Using multiple stylesheets as array example

```js
tinyMCE.init({
  selector: 'textarea',  // change this value according to your HTML
  content_css: ['mycontent.css', 'mycontent2.css']  // includes both CSS files in header, ability to have CSS with `,` in URL
});
```

#### Browser caching

Browser caching might cause TinyMCE to not read the contents of a changed CSS file. You'll see "old" colors & styles.

One solution is to manually clear the browser cache when the file for `content_css` or `editor_css` has changed. Another solution is to use an old hack which adds a bogus parameter to the URL containing a present time stamp like "myFile.css?bogus=10023561235". Possible solutions could look like this:

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  content_css: 'path/myfile.css?' + new Date().getTime()
});
```

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  content_css: 'path/myscript.php?myParam=myValue&bogus=' + new Date().getTime()
});
```
