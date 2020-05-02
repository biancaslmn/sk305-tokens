## Installation

-   install [NodeJS](https://nodejs.org/en/) (if required) and [Yarn](https://yarnpkg.com/en/docs/install)
-   download the assembly in the console using [Git](https://git-scm.com/downloads) :`git clone https://github.com/andreyalexeich/gulp-pug-starter.git`
-   install `gulp`globally:`yarn global add gulp-cli`
-   install `bem-tools-core`globally:`yarn global add bem-tools-core`
-   go to the downloaded folder with the assembly: `cd gulp-pug-starter`
-   download the necessary dependencies: `yarn`
-   to get started, enter the command: `yarn run dev`(development mode)
-   to build a project, enter the command `yarn run build`(build mode)

If you did everything correctly, you should open a browser with a local server. Build mode involves optimizing the project: compressing images, minifying CSS and JS files to upload to the server.

## File structure

```
gulp-pug-starter
├── dist
├── gulp-tasks
├── src
│   ├── blocks
│   ├── fonts
│   ├── img
│   ├── js
│   ├── styles
│   ├── views
│   └── .htaccess
├── gulpfile.babel.js
├── webpack.config.js
├── package.json
├── .babelrc.js
├── .bemrc.js
├── .eslintrc.json
├── .stylelintrc
├── .stylelintignore
└── .gitignore

```

### Root Folder
If you are not familiar with configuring NPM packages

 - `.babelrc.js` - Babel settings
 - `.bemrc.js` - BEM settings
 - `.eslintrc.json` - ESLint settings
 - `.gitignore` - ban on tracking files with git
 - `.stylelintrc` - Stylelint settings
 - `.stylelintignore` - ban on tracking files Stylelint'om
 - `gulpfile.babel.js` - Gulp settings
 - `webpack.config.js` - webpack settings
 - `package.json` - list of dependencies

### Source Folder `src`
Location for your source-code used during development:

 - BEM blocks and components: `src/blocks`
 - fonts: `src/fonts`
 - Images: `src/img`
 - JS files: `src/js`
 - site pages: `src/views/pages`
 - SCSS files: `src/styles`
 - Utility Pug Files: `src/views`

### Distribution Folder `dist`
The `dist` folder is the build destination for the localhost server when the `yarn run dev` command is triggered.

### Gulp Tasks Folder 

The Gulp Tasks folder `gulp-tasks` holds all scripts for running the Gulp task management package.

- You may also run the command `gulp --tasks` to review all available scripts.

## Yarn Commands
The following commands are available.

### Development
- `yarn run dev` - server launch for project development

### Build
- `yarn run build` - build a project with optimization without starting the server
- `yarn run build:views` - compile pug files
- `yarn run build:styles` - compile SCSS files
- `yarn run build:scripts` - collect js files
- `yarn run build:images` - collect images
- `yarn run build:webp` - convert images to format `.webp`
- `yarn run build:sprites`- collect sprites
- `yarn run build:fonts` - collect fonts
- `yarn run build:favicons` - collect favicons
- `yarn run build:gzip` - build Apache configuration

### Linting
- `yarn run lint:styles`- check SCSS files. [VSCode plugin](https://github.com/stylelint/vscode-stylelint). 
- `yarn run lint:styles --fix` - fix errors in SCSS files
- `yarn run lint:scripts` - check js files
- `yarn run lint:scripts --fix` - fix errors in js files




## Recommendations for use

### Component approach to website development
The **Block**, **Element**, **Modifier** methodology (commonly referred to as **BEM**) is a popular naming convention for classes in HTML and CSS.

- Learn more at
 - [BEM 101](https://css-tricks.com/bem-101/)
 - [BEM For Beginners: Why You Need BEM](https://www.smashingmagazine.com/2018/06/bem-for-beginners/)

### Leveraging BEM

- Each BEM block has its own folder inside `src/blocks/modules`
- The folder of one `BEM` block contains:
 - one `PUG` file,
 - one `SCSS` file and
 - one `JS` file (if the block uses a script)
- The block `PUG` file is imported into the file `src/views/index.pug`(or into the necessary page file, from where the block will be called)
- The block `SCSS` file is imported into file `src/blocks/modules/_modules.scss`
- The block `JS` file is imported into `src/js/import/modules.js`

An example of the structure of a folder with a BEM block:

```
blocks
├── modules
│   ├── header
│   │   ├── header.pug
│   │   ├── header.js
│   │   ├── header.scss

```
#### Creating BEM blocks via the command line

In order not to manually create the corresponding folder and files, it is enough to write the following commands in the console:

- `bem create my-block`- to create a folder of the BEM block, where `my-block`is the name of the BEM block
- `bem create my-component -l src/blocks/components` to create a component
- `bem create my-component -l src/blocks/components && bem create my-block` - create everything together

### Components

- components (e.g. icons, buttons) are styled in Pug using impurities
- each component has its own folder inside `src/blocks/components`
- the folder of one component contains one Pug file, one SCSS file and one JS file (if the component uses a script)
  - The component pug file is imported into the main page file `src/views/index.pug`(or into the necessary page file, from where the component will be called)
  - Component SCSS file is imported into the file `src/blocks/components/_components.scss`
  - Component js file is imported to file `src/js/import/components.js`

### Project Pages

- project pages are in the folder `src/views/pages`
  - each page (including the main page) inherits a template `src/views/layouts/default.pug`
  - main page: `src/views/index.pug`

### Web Fonts

- fonts are in the folder `src/fonts`
  - use [formats](https://caniuse.com/#search=woff) `.woff` and`.woff2`
  - fonts are included in the file `src/styles/base/_fonts.scss`
  - you can convert local fonts using [this service](https://onlinefontconverter.com/)

### Images

- images are in the folder `src/img`
  - the image for generating favicons must be in the folder `src/img/favicon`and have a size of at least`1024px x 1024px`
  - Images are automatically converted to format `.webp`. Detailed usage information is [here](https://vk.com/@vk_it-webp) .

### 3rd party libraries

- all third-party libraries are installed in the folder `node_modules`
  - To download them use the command `yarn add package_name`
  - To connect library JS files, import them at the very beginning of the BEM block JS file (that is, the BEM block that uses the script), for example:

    ```source-js
    import $ from  " jquery " ;
    ```

  - to include library style files, import them into a file `src/styles/vendor/_libs.scss`
  - JS files and library style files cannot be changed on their own

NOTE: If your project uses several libraries that need to be connected on several pages, in order to avoid errors, you need to:


- `src/js/import` create a folder along the way
- `pages` create a js-file for the page in the folder , for example, `pageA.js`and import the library there, which will be used only on this page
- similarly take a step for additional pages
- in the file `webpack.config.js`, add js-files of pages to the entry point, example:

```source-js
entry : {
    main :  " ./src/js/index.js " ,
    pageA :  " ./src/js/import/pages/pageA.js " ,
    pageB :  " ./src/js/import/pages/pageB.js "
}
```

- include compiled js files on the necessary pages

### CSS grid smart-grid

The collector includes a [smart grid grid](https://github.com/dmitry-lavrik/smart-grid) from [Dmitry Lavrik](https://dmitrylavrik.ru/) . It allows you to get rid of unnecessary classes in the markup due to the use of impurities in SCSS and accelerates adaptive layout. The configuration is already configured according to the [Bootstrap](https://getbootstrap.com/) grid . Usage example:

SCSS

```source-css-scss
.items {
    @include  row-flex ();
    @include  md ( justify-content , center );

    .item {
        @include  col ();
        @include  size ( 3 );
        @include  size-md ( 5 );
        @include  size-xs ( 10 );
    }
}
```

Result

```source-css
.items {
    display : flex ;
    flex-wrap : wrap ;
    margin-left : -15 px ;
    margin-right : -15 px ;
}
.items .item {
    box-sizing : border-box ;
    margin-left : 15 px ;
    margin-right : 15 px ;
    word-wrap : break-word ;
    width : calc ( 100 %  /  12  *  3  -  30 px );
}
@media screen and ( max-width : 992 px ) {
    .items {
       justify-content : center ;
    }
    .items .item {
       width : calc ( 100 %  /  12  *  5  -  30 px );
    }
}
@media screen and ( max-width : 576 px ) {
    .items .item {
       width : calc ( 100 %  /  12  *  10  -  30 px );
    }
}
```
