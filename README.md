# basic-sass-setup
Kickstarter to develop application using Sass stylesheets with gulp.

1. Run package.json with npm install to download all the required node modules.
   Dependencies install
   ---express
   ---jade
   ---gulp
   ---gulp-sass
   ---gulp-sourcemaps

2. Create a gulpfile.js	in the root and paste the code below in gulpfile.js

`var gulp = require('gulp');`
`var sass = require('gulp-sass');`
`var sourcemaps = require('gulp-sourcemaps');`

`var input = 'stylesheets/scss/main.scss';`
`var output = 'stylesheets/css';`
`var sassOptions = {`
  `errLogToConsole: true,`
  `outputStyle: 'expanded'`
`};`

`gulp.task('watch', function() {`
  `return gulp`
    `// Watch the input folder for change,`
    `// and run `sass` task when something happens`
    `.watch(input, ['sass'])`
    `// When there is a change,`
    `// log a message in the console`
    `.on('change', function(event) {`
      `console.log('File ' + event.path + ' was ' + event.type + ', running tasks...');`
    `});`
`});`

`gulp.task('sass', function () {`
  `return gulp`
    `// Find all `.scss` files from the `stylesheets/` folder`
    `.src(input)`
    `.pipe(sourcemaps.init())`
    `// Run Sass on those files`
    `.pipe(sass(sassOptions).on('error', sass.logError))`
    `// Create Sourcemaps for Sass`
    `.pipe(sourcemaps.write())`
    `// Write the resulting CSS in the output folder`
    `.pipe(gulp.dest(output));`

`});`

`gulp.task('default', ['sass', 'watch']);`

3. now open command line and enter
   `C:\www\lambda>gulp`

4. Your ready with scss and sourcemaps :D