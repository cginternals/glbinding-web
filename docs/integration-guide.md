<br><a href="https://glbinding.org/"><img src="https://raw.githubusercontent.com/cginternals/glbinding/master/glbinding-logo.svg?sanitize=true" width="50%"></a>

*glbinding* is a cross-platform C++ binding for the [OpenGL API](http://www.opengl.org).

*glbinding* leverages modern C++11 features like enum classes, lambdas, and variadic templates, instead of relying on macros; 
all OpenGL symbols are real functions and variables. 
It provides type-safe parameters, per feature API header, lazy function resolution, multi-context and multi-thread support, global and local function callbacks, meta information about the generated OpenGL binding and the OpenGL runtime, as well as tools and examples for quick-starting your projects.
Based on the OpenGL API specification ([gl.xml](https://cvs.khronos.org/svn/repos/ogl/trunk/doc/registry/public/api/gl.xml)) *glbinding* is generated using python scripts and templates that can be easily adapted to fit custom needs.


## Integration of a new Documentation

The following manual steps are necessary for each added documentation:

1. Create a subfolder with the name of the release identifier (e.g., master, v2.0)
2. Copy contents of Doxygen html folder into directory
3. Add documentation meta data to ```docs/docs.pug```
4. Adjust the sort order of the documentations array in the config file; the order is used for display
5. Adjust doxy-boot.js
   1. Add code to generate backlink in the ```$(document).ready``` callback
   
The resulting head of the file should look like this:

```js
$( document ).ready(function() {
    $("#projectlogo").each(function() {
        var td = $(this);
        td.html($("<a>").attr("href", "/").append(td.html()));
    });
    
    // ...
});
```
