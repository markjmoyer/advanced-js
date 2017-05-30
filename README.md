# An HTML Generator w/SASS


## Project Dependencies
Following are the dependencies and packages used in developing this website:

* [Git](http://git-scm.com/) - Source Code Management
* [NodeJS](http://nodejs.org/) - Server-Side JavaScript
* [Grunt](http://gruntjs.com/) - The JavaScript Task
* [Bower](http://bower.io/) - Package Manager for the Web
* [jQuery](http://jquery.com/) - The Write Less, Do More JavaScript Library
* [Modernizr](http://modernizr.com/) - Detects HTML5 and CSS3 features in the user’s browser
* [SASS] - CSS Pre-Processor

## Using Grunt Task Runner

### Configuring Grunt
Grunt uses the "Gruntfile.js" file located in the root to configure the actions
performed when the `grunt` command is run. Grunt uses the "package.json" file located
in the root to set the Application Name, Version Number and the package dependencies
that exist for supporting the commands in the Gruntfile.

### Building with Grunt
From the command-line, in the root directory of the project, run the command `grunt`
Once completed, this task will perform the following actions:

* Compile LESS into CSS
* [Lint](http://csslint.net/) your Compiled CSS
* Minify the Compiled CSS into a *.min.css file
* [Lint](http://jshint.com/) your JavaScript
* Concatenate all of the JS into a single file
* Uglify (minify) the JS into a *.min.js file

To run your Grunt tasks, simply do the following:

    $> cd <DIRECTORY_PATH_TO_YOUR_GRUNTFILE.JS>
    $> grunt

Once executed, Grunt will run through all of the tasks that you have configured,
and will output results for each step into the command window.

### Developing with Grunt
While developing applications and websites using Grunt, it's useful to automatically
run Grunt tasks when certain files are modified. In this project, we use "grunt watch"
to look for changes in specific files and perform Grunt build tasks when they are
modified. For example, if you edit a *.less file in the __/src/assets/less/__
directory, then the watcher will automatically compile the LESS code into CSS,
then generate the file into the target distribution directory. When you reload your
browser, your changes are immediately visible as they have been compiled and built
in the background.

In order to launch Grunt watch, all you need to do is open a command-line terminal,
cd to your working directory and type `grunt watch`:

    $> cd /Library/WebServer/Documents/nascar-html-cutups/default/
    $> grunt watch
    $> Running "watch" task
    $> Waiting...

&nbsp;


## Website Structure

### Assets
Website resources such as images, stylesheets, JavaScripts, etc. are all located in
the Assets directory in the root of the project. Within the Assets directory, you
will find sub-directories for each of these resources:

#### DIST (Distribution)
Files that have been concatenated, minified and prepared for final inclusion in the
website are stored here in context-specific directories. Files are written here by
the Grunt tasks described above. When authoring CSS or JavaScript, you should never
write files directly into this directory.

#### SASS / CSS
When authoring CSS for this project, you should be authoring using LESS - writing
\*.less files into the __/src/assets/less/__ directory. These files are then parsed
into CSS by the Grunt tasks described above.

#### JavaScript
When authoring JavaScript files for this project, you should be saving those files
into the __/src/assets/js/__ directory, with each file being named appropriate to
its behavior or purpose. When it's time to deploy, these files will be concatenated
and minified into one single file, complete with a version number and stored in the
__/dist/assets/dist/js/__ directory.

#### Images
Nothing really special about images in this website, but you should be using \*.png
files as a default. Sometimes a \*.gif or \*.jpg may be required, but by and large
you should be building with \*.png's.

### Bower Components
When you install resources using Bower, they're stored in this directory. For the most
part you don't need to touch this and thanks to Grunt and the `grunt-wiredep` plugin
you won't even need to reference these files in your code. Just drop the placeholders
for your CSS or JS into your HTML files, and when Grunt runs, the Bower resources will
be inserted into your code.

    <html>
    <head>
      <!-- bower:css -->
      <!-- endbower -->
    </head>
    <body>
      <!-- bower:js -->
      <!-- endbower -->
    </body>
    </html>

### Node Modules
When you install Node Packages using NPM, those resources will be installed in the
__/node_modules/__ directory. For example, the Grunt package that you installed with
NPM lives in this location.

### HTML
Your HTML resources are stored in the __/src/__ directory of the website, and once
the HTML includes parser runs, the files are copied into the __/dist/__ directory
for deployment. This project uses the [Grunt Simple Include](https://www.npmjs.org/package/grunt-simple-include)
package to enable the use of includes in static HTML files. By using a similar
syntax to the Bower Components declarations, you can inject HTML or other content
directly into your templates during the build process.

    <html>
    <head>
      <title>Page Title</title>
    </head>
    <body>
      <!-- include: 'includes/meta.html' -->
      <!-- include: 'includes/header.html' -->
      <!-- include: 'includes/footer.html' -->
    </body>
    </html>


#### Variables in HTML
You can write variables into your templates. Using the example include
above, we could write the following content into the __meta.html__ file:

    <title>@@title</title>
    <meta name="description" content="@@description">
    <meta name="keywords" content="@@keywords">

Simply by defining the values in our __package.json__ file:
