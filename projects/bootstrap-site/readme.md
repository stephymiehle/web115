## Bootstrap Site Setup

We're not using a package manager or command line utilities, so our setup is a little different than some of the other tutorials you might find.

### Set up your folders

1. If you haven't already, create a `projects` folder inside of your class folder.
2. Inside of `projects`, create a new folder for your Bootstrap site. I'm calling mine `bootstrap-project` in these instructions.
3. Inside of your `bootstrap-project` folder, create a `bootstrap` folder, a `scss` folder, and an `index.html` file.

### Download the latest version of Bootstrap

At the time of writing, the latest version is 5.1.3 ([download .zip](https://github.com/twbs/bootstrap/archive/v5.1.3.zip)), but you can also visit the [Bootstrap Docs](https://getbootstrap.com/docs) and click the Download button in the header to jump to the right section.

We're working with the **source files** so that we can modify Sass.

1. Unzip the Bootstrap source files.
2. Copy the `scss` folder from the source files into your `bootstrap-site/bootstrap` folder (not your own `scss` folder, which will house your personal files).
3. We're not recompiling the JavaScript, so we can copy the minified JS files. Open the `dist` folder in the source files, then copy the `js` folder to your `bootstrap-site/bootstrap` folder. We'll only use the `bootstrap.bundle.min.js` file, so you can remove the others or keep them around in case you'd like to customize your JS setup.

When you're done, your structure should look like this:  
_Note: slashes are used to designate folders, but shouldn't really be added to your folder names_

```
class-folder/
  labs/
    (...your lab assignments)
  projects/
    bootstrap-site/
      bootstrap/
        js/
          bootstrap.bundle.min.js
        scss/
          _accordion.scss
          _alert.scss
          _badge.scss
          (...all the rest)
      scss/
      index.html
```

### Add Bootstrap to your project

1. Now that we have our own copies of the files, we don't need to use the CDN versions. If you are copying your `index.html` from the intro assignment, remove the references to CDN versions from the `<head>` of your page and from any `<script>` tags near the bottom of the page.
2. Create `style.scss` and `_vars.scss` files inside of your personal `scss` folder.
3. Edit your `style.scss` to import your `vars` file. This needs to happen before your Bootstrap imports!
4. Import Bootstrap into your `style.scss`. You have multiple ways of doing this:
   1. Import all of Bootstrap with `@import "../bootstrap/scss/bootstrap";`; this is the fastest way, but can result in larger generated CSS if you don't use all the components or utilities.
   2. Import just the components you need (this is the method used in [my sample](https://github.com/blindingstars/web115/blob/master/projects/bootstrap-site/scss/style.scss)). You can see a full list of available components in the [Bootstrap source files](https://github.com/twbs/bootstrap/blob/main/scss/bootstrap.scss) – or in the version you downloaded! Navigate to `class-folder/projects/bootstrap-project/bootstrap/scss/bootstrap`. Note that your file imports need to be updated to point to their relative location. If you used the same structure as me, that would be `@import "../bootstrap/scss/containers";`.
5. Link to the Bootstrap files from your `index.html`. I am letting my SCSS files compile in my `scss` folder and am using the minified Bootstrap bundle for JavaScript, so my imports look like this:
   - In the `<head>`: `<link rel="stylesheet" href="scss/style.css" />`
   - Before the closing `</body>` tag: `<script src="bootstrap/js/bootstrap.bundle.min.js"></script>`

#### Learn More
- [View sample style.scss](https://github.com/blindingstars/web115/blob/master/projects/bootstrap-site/scss/style.scss)
- Learn more on the [Customize: Sass](https://getbootstrap.com/docs/5.0/customize/sass/) page of Bootstrap's documentation

### Add your custom styles!

Create your own SCSS files as needed to customize your project. Import these after Bootstrap so that you can use their functions and take advantage of the "cascade" part of Cascading Stylesheets (CSS).

### Other Notes

Normally, compiled CSS and `.map` files wouldn't be committed to your repository. I've kept them here for you to see as an example (and explore the source maps if you use your document inspector).