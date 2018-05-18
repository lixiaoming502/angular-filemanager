## angular-filemanager

A very smart filemanager to manage your files in the browser developed in AngularJS following Material Design styles by [Jonas Sciangula Street](https://github.com/joni2back)

This project provides a web file manager interface, **allowing you to create your own backend connector** following the [connector API](API.md). 
*By the way, we provide some example backend connectors in many languages as example (php-ftp, php-local, python, etc)*

[![Build Status](https://travis-ci.org/joni2back/angular-filemanager.svg?branch=master)](https://travis-ci.org/joni2back/angular-filemanager)

### Support
This project is under free license. If you want to support the angular-filemanager development or just thank it's main maintainer by paying a beer, you can make a donation by clicking the following button

Donate by Paypal [![Donate](https://www.paypal.com/en_GB/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=XRB7EW72PS982) 

Donate by Bitcoin wallet: ```147ca6be-a6a5-4012-8209-8ec94ff340b8```


#### [Try the DEMO](http://angular-filemanager.zendelsolutions.com/)
---------
![](https://raw.githubusercontent.com/joni2back/angular-filemanager/master/screenshot.gif)

### Features
  - Multiple file support
  - Multilanguage
  - List and Icon view
  - Multiple file upload
  - Pick files callback for third parties apps
  - Search files
  - Directory tree navigation
  - Copy, Move, Rename (Interactive UX)
  - Delete, Edit, Preview, Download
  - File permissions (Unix chmod style)
  - Mobile support

### TODO
  - Drag and drop
  - Dropbox and Google Drive connectors
  - Remove usage of jQuery

### Backend API
[Read the docs](API.md)

---------

### Using in your existing project
**1) Install deps using yarn with**
```yarn install```

**2) Include the dependencies in your project**
```html
<!-- third party -->
  <script src="node_modules/jquery/dist/jquery.min.js"></script>
  <script src="node_modules/angular/angular.min.js"></script>
  <script src="node_modules/angular-translate/dist/angular-translate.min.js"></script>
  <script src="node_modules/ng-file-upload/dist/ng-file-upload.min.js"></script>
  <script src="node_modules/bootstrap/dist/js/bootstrap.min.js"></script>
  <link rel="stylesheet" href="node_modules/bootswatch/paper/bootstrap.min.css" />

<!-- angular-filemanager -->
  <link rel="stylesheet" href="dist/angular-filemanager.min.css">
  <script src="dist/angular-filemanager.min.js"></script>
```

**3) Use the angular directive in your HTML**
```html
<angular-filemanager></angular-filemanager>
```

---------

### Extending the configuration file by adding a script
```html
<script type="text/javascript">
angular.module('FileManagerApp').config(['fileManagerConfigProvider', function (config) {
  var defaults = config.$get();
  config.set({
    appName: 'angular-filemanager',
    pickCallback: function(item) {
      var msg = 'Picked %s "%s" for external use'
        .replace('%s', item.type)
        .replace('%s', item.fullPath());
      window.alert(msg);
    },

    allowedActions: angular.extend(defaults.allowedActions, {
      pickFiles: true,
      pickFolders: false,
    }),
  });
}]);
</script>
```

### Create a new build with your changes
```sh
  gulp build || node node_modules/gulp/bin/gulp.js build
```

You can do many things by extending the configuration. Like hide the sidebar or the search button. See [the list of default configurations](/src/js/providers/config.js).

---------

### Contribute
To contribute to the project you can simply fork this repo. To build a minified version, you can simply run the Gulp
task `gulp build`. The minified/uglified files are created in the `dist` folder.

### Versioning
For transparency into our release cycle and in striving to maintain backward compatibility, angular-filemanager is maintained under [the Semantic Versioning guidelines](http://semver.org/).

### Copyright and license
Code and documentation released under [the MIT license](https://github.com/joni2back/angular-filemanager/blob/master/LICENSE).



## Out-of-the-box PHP Local Bridge bundle

This branch is supposed to help people who want something that works out-of-the-box using PHP.

### Usage

1. Download [current bundle](https://github.com/durasj/angular-filemanager/raw/bundle-php-local/bundle/master-2017-06-03.zip)
2. Extract archive somewhere where you can run PHP applications like on your hosting or htdocs directory on XAMPP (php-xml extension is required). If you don't have any, don't worry, check FAQ question [I don't have any PHP environment, how can I setup one?](https://github.com/durasj/angular-filemanager/tree/bundle-php-local#i-dont-have-any-php-environment-how-can-i-setup-one)
3. Open the directory where you extracted the archive in your browser
4. Enjoy. It's preconfigured to work with ./files directory at the root of the project

### FAQ

#### I don't have any PHP environment, how can I setup one?
The simplest way is to use PHP's built-in server:
1. First, you need to have PHP installed, you can do so by following some instructions on the internet, i.e. [how to install php on windows](https://www.google.sk/search?q=how+to+install+php+on+windows)
2. Extract bundle archive anywhere on your disk and navigate to that directory using cli (i.e. cmd.exe on win)
3. Type in `php -S localhost:8888` if you have PHP installed globally or `path/to/php -S localhost:8888` if not or `path/to/php.exe -S localhost:8888` on win platform
4. Open URL [localhost:8888](http://localhost:8888) in your browser

#### How can I change directory with files?
By default, ./files dir in the root of the project is used. You can easily change that by editing file `bridges/php-local/index.php`, line `$fileManagerApi = new FileManagerApi(__DIR__ . '/../../files');`

### Copyright and license
Developed in AngularJS with Material-Design styles by [Jonas Sciangula Street](https://github.com/joni2back).
Bundle and php local bridge by [Jakub Duras](https://github.com/jduras)

Code and documentation released under [the MIT license](https://github.com/joni2back/angular-filemanager/blob/master/LICENSE).

