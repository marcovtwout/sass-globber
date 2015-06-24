Sass Globber
============

This module provides a simple globbing functionality for sass files like the ruby gem `sass-globbing`.

It reads a file from a defined directory and creates a new sass file with all `@import` statements.

## Installation

`npm install sass-globber`

## Usage

Read a source file from a provided directory, process its content, glob all files and output the paths as content to a custom output file.

``` js

var sassGlobbing = require('sass-globbing');

sassGlobbing.compiled({
	sassRoot: 'src/sass',
	source: "_all.scss",
	output: 'styles.scss'
});

```

When your Sass/SCSS file looks like this: 
``` scss
@import "../bower-components/pg-scss/resources/scss/pg-reset";
@import "../bower-components/pg-scss/resources/scss/_helpers/**/*";
@import "global/vars";
@import "../bower-components/pg-scss/resources/scss/pg";

@import "utils/**/*";

@import "global/base";
@import "global/font-face";
@import "global/modifiers";
@import "global/get-media";

@import "regions**/*";

@import "components/**/*";

@import "panels/**/*";

@import "blocks/**/*";

@import "global/print";
``` 

You will get the following output:

``` scss
// This file is auto generated by the module sass-globbing.
 //Do not edit this file manually!

@import "../bower-components/pg-scss/resources/scss/pg-reset";
@import "../bower-components/pg-scss/resources/scss/_helpers/_breakpoint";
@import "../bower-components/pg-scss/resources/scss/_helpers/_cp";
@import "global/vars";
@import "../bower-components/pg-scss/resources/scss/pg";

@import "utils/extends/_ex-fonts";
@import "utils/mixins/_mx-fonts";

@import "global/base";
@import "global/font-face";
@import "global/modifiers";
@import "global/get-media";

@import "regions/_r-footer-bottom";
@import "regions/_r-footer-top";

@import "components/_c-accordion";
@import "components/_c-cta";
@import "components/_c-text-image";
@import "components/form/_select";

@import "panels/_p-segment";
@import "panels/_p-zone";

@import "blocks/_b-footer-metalinks";
@import "blocks/_b-footer-nav";

@import "global/print";
```

## Options

#### sassRoot

Type: `string`

Default value: `scss`

Define a string value which represents the path to your Sass/SCSS files.

Example: `src/sass`

#### source

Type: `string`

Default value: `styles.scss`

Define a string value which is the filename of your source file. In this file you have your glob patterns. 

Example: `_all.scss`

#### output

Type: `string`

Default value: `styles.tmp.scss`

Define a string value which is the filename of your output file.

Example: `styles-final.scss`

#### hint

Type: `string`

Default value: `// This file is auto generated by the module sass-globbing.\n //Do not edit this file manually!\n\n`

Define a string value which will be prepend to your output file.

Example: `// This file is auto generated. \n`

## Grunt Plugin

There is also a grunt module available: see [grunt-postcss-separator](https://github.com/Sebastian-Fitzner/grunt-sass-globber)

## License
Copyright (c) 2015 Sebastian Fitzner. Licensed under the MIT license.