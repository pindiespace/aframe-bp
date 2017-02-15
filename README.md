# Aframe Boilerplate - a simple A-Frame Demonstration

## Project setup and Gulp installation
Aframe-bp, adapted from [fastshell](https://HosseinKarami.github.io/fastshell), utilises open source components running on the Terminal/command-line for it's workflow. While some of the basic demonstrations will run by opening the app/index.html file, to see everyting (e.g. 360 video) you need to install Node and Gulp. 

Here's a walkthrough of how to get a project up and running. To execute some of these steps, you'll need to open Terminal on your Mac, or the Command Prompt on Windows.

1. Install [Node.js](http://nodejs.org/download), [Sass](http://sass-lang.com/tutorial.html) and [Git](http://git-scm.com) on your machine. If you're a Windows user you'll also need to install [Ruby](http://rubyinstaller.org/downloads) for Sass to work.

2. [Install Gulp](http://Gulpjs.com/) in the Terminal/Console using 

`npm install -g gulp`

On some Macs, you may need to use `sudo` in front of the Gulp install command to give it permissions.

3. Fork/Clone/Download the aframe-bp repository into your machine.

4. Open Terminal/Web Console and navigate to the folder you downloaded. Use the following command to install to `node_modules` 

 `npm install`
 `npm install gulp`

 You don't need `sudo` to do this in most cases.

5. The `npm install` you did in previous step should install all the dependencies, which you can confirm by visiting the `node_modules` in your project directory. 

6. To start the web server included in the project, type `gulp` in the Terminal/Console (again in your project directory) to run the commands associated with aframe-bp and to automatically open a new aframe-bp project running on `localhost:3000`.

7. From now on, just run `gulp` in your project directory to automatically run aframe-bp's Gulp tasks.

Once running, aframe-bp does the following:

1. Mounts the `app` folder onto a local server
2. Listens for changes inside the `src` directory, and compiles the necessary files into the `app` directory, which will then automaticaly livereload or inject changes. CSS changes are injected, all other changes force a page reload.

## Checking Your Installation

### Status HUD
Edit the <a-scene> to <a-scene status>, and you'll get a display including framerate, memory, and overall performance of your app.

### The DOM Inspector
A a visual tool, similar to browser’s DOM Inspector
Go to any A-Frame scene
Hit <ctrl> + <alt> + i on your keyboard

## Testing the A-Frame Examples

To test, just go to the src/html folder, and edit the index.html. The A-Frame components have been hidden with HTML comments:

<!-- #. description of stuff-->
<!-- aframe stuff -->

Un-comment the second comment in these blocks, one at a time, to see each feature or effect. In other 20 lines of code, you can duplicate what some 'native' apps do.

NOTE: DO NOT edit in the /app directory - these files are copied dynamically by gulp every time you save files in the /src directory.

## Editing files in the boilerplate
1. Edit in /app/index.html to change your aframe world
2. Edit either /src/js/app.js to change JavaScript
3. Edit /src/scss/style.scss (or subfolders with.scss files to change your CSS)

## Links to more A-Frame and WebVR Resources
[http://aframe.io](http://aframe.io)
[https://www.meetup.com/Los-Angeles-WebVR-Meetup/](https://www.meetup.com/Los-Angeles-WebVR-Meetup/)
[http://webvr.info](http://webvr.info)
[WebVR Slack Channel]()

## More Technical Info
The package.json includes the dependencies for the project as well as information about the project.

### Browser-Sync
Gulp's browser-sync will inject the following script into your HTML for you (don't be surprised if you see in when you inspect the site with your Web Console):

````html
<script type='text/javascript'>//<![CDATA[
;document.write("<script defer src='//HOST:3000/socket.io/socket.io.js'><\/script><script defer src='//HOST:3001/client/browser-sync-client.0.9.1.js'><\/script>".replace(/HOST/g, location.hostname));
//]]></script>
````

### Extending Gulp tasks
If you're including more Gulp tasks in your project, remember to use the `npm install <Gulp package> --save-dev` inside your Terminal so that it gets added to your `package.json` file for future dependencies.

Add new tasks to the `gulp` tasks at the `gulpfile.js`:

### JavaScript
aframe-bp comes with a single `app.js` to get you started. If you're building an AngularJS or ReactJS project you will need to change app.js. The generic scripts file ships with an immediately-invoked function expression (IIFE) using jQuery:

````js
(function ($, window, document, undefined) {
  'use strict';
  // aframe-bp
})(jQuery, window, document);
````

### Sass/SCSS setup
aframe-bp comes with a `.scss` file setup and existing `@import` declarations for common web components. aframe-bp it uses the fastshell CSS structure to provide good organization for Sass files converted to CSS. 

SCSS Files:

* `mixins` holds all Sass/SCSS mixins, aframe-bp ships with a few helpers
* `module` holds modules, more Object-Orientated components and a generic `app.scss` for everything else, all file names should be modular/OO.
* `partials` holds the blueprints for the project, the header, footer, sidebar and so on.
* `vendor` holds any files that are third party, such as the font awesome icons CSS
* `style.scss` imports all the necessary files from the above folders, when adding new files be sure to add it inside this file.

### Hidden files explained

If you're on a Mac, it's a good idea to expose hidden files so you can configure your `.editorconfig`, `.jshintrc`, `.gitignore` files. On the command line, enter:

````
defaults write com.apple.Finder AppleShowAllFiles YES
````

To hide hidden files enter:

````
defaults write com.apple.Finder AppleShowAllFiles NO
````

### .editorconfig
EditorConfig helps developers define and maintain consistent coding styles between different editors and IDEs. The `.editorconfig` file consists of a format for defining coding styles and a collection of text editor plugins that enable editors to read the file format and adhere to defined styles.

### .gitignore
Ignores minified and generated files, this is best for working in teams to avoid constant conflict, only the source files are needed.

### .travis.yml
This is used on [travis-ci.org](http://travis-ci.org) for continuous integration tests, which monitors the aframe-bp build.

## Platform support

aframe-bp runs on Mac OS X, Linux and Windows.
