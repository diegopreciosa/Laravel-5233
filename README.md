# Laravel 5.2 with Bootstrap 3.3
Laravel 5 dances with Bootstrap 3 on the Laravel Homestead virtual machine.

[Laravel 5](https://laravel.com/docs/5.2) dances with [Bootstrap 3](http://getbootstrap.com/) using [Laravel Elixir](https://laravel.com/docs/5.0/elixir) in this setup on the [Laravel Homestead Virtual Machine](https://laravel.com/docs/5.2/homestead).

## The Players
- [Laravel Homestead Virtual Machine](https://laravel.com/docs/5.2/homestead)
- [Vagrant](https://www.vagrantup.com/)
- [Laravel 5.2](https://laravel.com/docs/5.2)
- [Laravel Elixir](https://laravel.com/docs/5.0/elixir)
- [Bootstrap 3.3](http://getbootstrap.com/)
- [Browsersync](https://www.browsersync.io/docs/)

### Setup Laravel 5 Project
> NOTE: Laravel 5 requires PHP 5.6.

- Setup a local development domain (~/etc/hosts)
- Add Site Mapping to ~/.homestead-56/Homestead.yaml file
- Run vagrant provision to reload sites in Homestead.yaml
```
vagrant provision
```

- Use composer to create a Laravel Project
```
composer create-project laravel/laravel <folder_name>
```

- Make /bootstrap and /storage directories writable
- Run composer install
```
composer install
```

- Test Installation
- Install Git: git init
- Setup Sublime Project
- Configure local environment: http://laravel.com/docs/5.1/installation#environment-configuration
- Install Form & HTML Package: http://laravelcollective.com/docs/5.0/html
- Initiate Bower in the project root
```
bower inti
```

- Create or confirm that .bowerrc file is in the root of your Laravel project with this content.
```
{
  "directory": "resources/assets/bower"
}
```

### Install Foundation 6
- Update the bower.json file in the root of your Laravel project with the following two dependencies.
```
    "private": "true",
     "dependencies": {
         "foundation-sites": "latest",
         "motion-ui": "~1.1.1"
       },
```

- Install foundation via bower (you may have to install bower):
```
bower install # This will install Foundation and its dependencies into resources/assets/bower/
```

- Create the file resources/assets/sass/_settings.scss file with this content:
```
// Custom settings for Zurb Foundation.
// Default settings can be found at resources/assets/bower/foundation-sites/scss/settings/_settings.scss
```

- Edit the file resources/assets/sass/app.scss file with this content:
```
@charset 'utf-8';

@import 'settings';
@import 'foundation';
@import 'motion-ui';

@include foundation-global-styles;
@include foundation-grid;
@include foundation-typography;
@include foundation-button;
@include foundation-forms;
@include foundation-visibility-classes;
@include foundation-float-classes;
@include foundation-accordion;
@include foundation-accordion-menu;
@include foundation-badge;
@include foundation-breadcrumbs;
@include foundation-button-group;
@include foundation-callout;
@include foundation-close-button;
@include foundation-drilldown-menu;
@include foundation-dropdown;
@include foundation-dropdown-menu;
@include foundation-flex-video;
@include foundation-label;
@include foundation-media-object;
@include foundation-menu;
@include foundation-off-canvas;
@include foundation-orbit;
@include foundation-pagination;
@include foundation-progress-bar;
@include foundation-slider;
@include foundation-sticky;
@include foundation-reveal;
@include foundation-switch;
@include foundation-table;
@include foundation-tabs;
@include foundation-thumbnail;
@include foundation-title-bar;
@include foundation-tooltip;
@include foundation-top-bar;

@include motion-ui-transitions;
@include motion-ui-animations;
```

- Update /resources/views/welcome.blade.php with this template code so that we can ensure that Foundation is working.
```
<!doctype html>
<html class="no-js" lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laradation - Laravel 5 & Foundation 6</title>
    <link rel="stylesheet" href="{{ elixir("css/app.css") }}">
  </head>
  <body>
    <div class="top-bar">
      <div class="row">
        <div class="top-bar-left">
          <ul class="dropdown menu" data-dropdown-menu>
            <li class="menu-text">Apps</li>
            <li class="has-submenu">
              <a href="#">Accounts</a>
              <ul class="submenu menu vertical" data-submenu>
                <li><a href="#">Organizations</a></li>
                <li><a href="#">Members</a></li>
              </ul>
            </li>
            <li class="has-submenu">
              <a href="#">Sales</a>
              <ul class="submenu menu vertical" data-submenu>
                <li><a href="#">Marketing</a></li>
                <li><a href="#">Contracts</a></li>
                <li><a href="#">Renewals</a></li>
                <li><a href="#">Prospects</a></li>
                <li><a href="#">Billing</a></li>
              </ul>
            </li>
            <li class="has-submenu">
              <a href="#">Pubs</a>
              <ul class="submenu menu vertical" data-submenu>
                <li><a href="#">Reports</a></li>
                <li class="divider"></li>
                <li><a href="#">Publications</a></li>
                <li><a href="#">Categories</a></li>
                <li><a href="#">Navigation</a></li>
                <li><a href="#">Pages</a></li>
                <li class="divider"></li>
                <li><a href="#">Events</a></li>
                <li><a href="#">Articles</a></li>
                <li><a href="#">Images</a></li>
                <li><a href="#">Webcams</a></li>
                <li class="divider"></li>
                <li><a href="#">SEO</a></li>
              </ul>
            </li>
            <li><a href="#">Packages</a></li>
          </ul>
        </div>
        <div class="top-bar-right">
          <ul class="dropdown menu" data-dropdown-menu>
            <li>
              <a href="#">Help</a>
            </li>
            <li class="has-submenu">
              <a href="#">Johnny Appleseed</a>
              <ul class="submenu menu vertical" data-submenu>
                <li><a href="#">My Profile</a></li>
                <li><a href="#">Organizations</a></li>
                <li><a href="#">Members</a></li>
                <li><a href="#">Logout</a></li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <br>
    <div class="row columns">
      <nav aria-label="You are here:" role="navigation">
        <ul class="breadcrumbs">
          <li><a href="#">Home</a></li>
          <li><a href="#">Accounts</a></li>
          <li class="disabled">Org Name</li>
          <li>
            <span class="show-for-sr">Current: </span> Location
          </li>
        </ul>
      </nav>
    </div>
    <div class="row">
      <div class="medium-6 columns">
        <img class="thumbnail" src="http://placehold.it/650x350">
        <div class="row small-up-4">
          <div class="column">
            <img class="thumbnail" src="http://placehold.it/250x200">
          </div>
          <div class="column">
            <img class="thumbnail" src="http://placehold.it/250x200">
          </div>
          <div class="column">
            <img class="thumbnail" src="http://placehold.it/250x200">
          </div>
          <div class="column">
            <img class="thumbnail" src="http://placehold.it/250x200">
          </div>
        </div>
      </div>
      <div class="medium-6 large-5 columns">
        <h3>Laravel & Foundation</h3>
        <p>Nunc eu ullamcorper orci. Quisque eget odio ac lectus vestibulum faucibus eget in metus. In pellentesque faucibus vestibulum. Nulla at nulla justo, eget luctus tortor. Nulla facilisi. Duis aliquet egestas purus in.</p>
        <label>Size
          <select>
            <option value="husker">Small</option>
            <option value="starbuck">Medium</option>
            <option value="hotdog">Large</option>
            <option value="apollo">Yeti</option>
          </select>
        </label>
        <div class="row">
          <div class="small-3 columns">
            <label for="middle-label" class="middle">Quantity</label>
          </div>
          <div class="small-9 columns">
            <input type="text" id="middle-label" placeholder="One fish two fish">
          </div>
        </div>
        <a href="#" class="button large expanded">Buy Today</a>
        <div class="small secondary expanded button-group">
          <a class="button">Facebook</a>
          <a class="button">Twitter</a>
          <a class="button">Instagram</a>
        </div>
      </div>
    </div>
    <div class="row column">
      <hr>
      <div class="row">
        <div class="small-12 medium-6 large-4 columns">
        <h4>A fun mixture</h4>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
            tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
            quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
            consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
            cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
            proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          </p>
        </div>
        <div class="small-12 medium-6 large-4 columns">
        <h4>World class frameworks</h4>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
            tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
            quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
            consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
            cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
            proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          </p>
        </div>
        <div class="small-12 medium-6 large-4 columns">
        <h4>Motion UI playground</h4>
          <button type="button" class="button" data-toggle="motion-example-1" aria-controls="motion-example-1">Fade</button>
          <button type="button" class="button" data-toggle="motion-example-2" aria-controls="motion-example-2">Slide</button>
          <div class="row">
            <div class="small-6 columns">
              <div data-toggler data-animate="fade-in fade-out" class="callout secondary ease" id="motion-example-1">
                <p>This panel <strong>fades</strong>.</p>
              </div>
            </div>
            <div class="small-6 columns">
              <div data-toggler data-animate="slide-in-down slide-out-up" class="callout secondary ease" id="motion-example-2">
                <p>This panel <strong>slides</strong>.</p>
              </div>
            </div>
          </div>
        </div>
        <div class="row column">
          <hr>
          <ul class="menu">
            <li>Apps</li>
            <li><a href="#">Home</a></li>
            <li><a href="#">Accounts</a></li>
            <li><a href="#">Sales</a></li>
            <li><a href="#">Pubs</a></li>
            <li><a href="#">Packages</a></li>
            <li class="float-right">Copyright 2016</li>
          </ul>
        </div>
        <script src="{{ elixir("js/app.js") }}"></script>
        <script>
        $(document).foundation();
        </script>
      </body>
    </html>
```

- Configure the file gulpfile.js with this content:

```
var elixir = require('laravel-elixir');

/*
 |--------------------------------------------------------------------------
 | Elixir Asset Management
 |--------------------------------------------------------------------------
 |
 | Elixir provides a clean, fluent API for defining some basic Gulp tasks
 | for your Laravel application. By default, we are compiling the Sass
 | file for our application, as well as publishing vendor resources.
 |
 */

// Start - Settings

// Proxy host to use for browserSync.
// Set to localhost url.
var proxyurl = "localhost.clients.alltrips.com";

// END - Settings

elixir(function (mix) {

  // Compile CSS.
  mix.sass(
    'app.scss', // Source files.
    'public/css', // Destination folder.
    {
      includePaths: [
          'resources/assets/bower/foundation-sites/scss',
          'resources/assets/bower/motion-ui/src'
      ]
    }
  )

  // Compile JavaScript.
  mix.scripts(
      // Source files. You can also selective choose only some components.
    [
        'bower/jquery/dist/jquery.min.js',
        // Can break this out to only include used components when ready for Production.
        'bower/foundation-sites/dist/foundation.min.js',
        'bower/what-input/what-input.js'
    ],
    'public/js/app.js', // Destination file.
    'resources/assets' // Source files base directory.
  )

  // Version the files for cachebusting.
  mix.version(
    [
        'css/app.css',
        'js/app.js'
    ]
  )

  // Apply BrowserSync magic.
  .browserSync({
    proxy: proxyurl
  })

});
```


- Install Gulp
```
npm install gulp
```

- Install Elixir components
```
npm install
```

- Run Gulp
```
gulp
```

- Fix any missing gulp components.
- Setup Remote Repository at GitHub: http://befused.com/git/existing-project-github
- Add Remote Repository
```
git remote add origin https://github.com/yourname/my_project.git
```

- Git Pull
- Git Push


## Builds
To build just follow official docs:
- gulp # Run all tasks...
- gulp --production # Run all tasks and minify files
- gulp watch # Watch for changes and run all tasks in Elixir.

> Compiled files will be at public/css/app.css and public/js/app.js.

## Update Foundation
To update to the latest Zurb Foundation version just run:
```
bower update
```

## Resources
- Laravel Installation - https://laravel.com/docs/5.1/installation
- Foundation Integration - http://stackoverflow.com/questions/30964780/foundation-with-laravel-and-elixir
