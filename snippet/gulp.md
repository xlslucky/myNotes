# gulp

### 一些常用的插件

* gulp-sass (编译sass)
* gulp-cssnano (压缩css)
* gulp-autoprefixer (根据设置浏览器版本自动处理浏览器前缀)
* gulp-rename (修改文件名)
* gulp-px2rem (px转rem)
* gulp-wrap (定义使用公共的头部和底部)

### pc例子

```js
var gulp = require('gulp');
var sass = require('gulp-sass');
var cssnano = require('gulp-cssnano');
var prefix = require('gulp-autoprefixer');
var rename = require('gulp-rename');
var wrap = require('gulp-wrap');
var src = process.cwd();

gulp.task('sass', function () {
  gulp.src('sass/*.scss')
    .pipe(sass())
    .pipe(prefix({
      versions: ['IE 9']
    }))
    .pipe(cssnano())
    .pipe(rename(function (path) {
      path.basename += ".min";
    }))
    .pipe(gulp.dest('./styles'));
});

gulp.task('html', function () {

  gulp.src(['_pages/login.html', '_pages/register.html', '_pages/recover.html', '_pages/readTheArticle.html', '_pages/activity-201706.html'])
      .pipe(wrap({
        src: '_layout/empty.html'
      }))
      .pipe(gulp.dest('./pages'));

  gulp.src(['_pages/*.html', '!_pages/login.html', '!_pages/register.html',  '!_pages/recover.html', '!_pages/readTheArticle.html', '!_pages/activity-201706.html'])
    .pipe(wrap({
      src: '_layout/layout.html'
    }))
    .pipe(gulp.dest('./pages'));
});

gulp.task('watch', ['sass', 'html'], function () {
  gulp.watch('sass/**/*', {cwd: src}, ['sass']);
  gulp.watch('_pages/**/*', {cwd: src}, ['html']);
  gulp.watch('_layout/**/*', {cwd: src}, ['html']);
});

gulp.task('default', ['watch']);
```

### wap例子

```js
var gulp = require('gulp');
var sass = require('gulp-sass');
var cssnano = require('gulp-cssnano');
var prefix = require('gulp-autoprefixer');
var rename = require('gulp-rename');
var px2rem = require('gulp-px2rem');

gulp.task('sass', function() {
    gulp.src('sass/main.scss')
        .pipe(sass())
        .pipe(prefix({
            browsers: ['last 14 versions']
        }))
        .pipe(px2rem({ replace: true, rootValue: 37.5 }))
        .pipe(cssnano())
        .pipe(rename(function(path) {
            path.basename = "story-wap.min";
        }))
        .pipe(gulp.dest('./styles'));
});

gulp.task('ranking', function() {
    gulp.src('sass/ranking-0508.scss')
        .pipe(sass())
        .pipe(prefix({
            browsers: ['last 14 versions']
        }))
        .pipe(px2rem({ replace: true, rootValue: 37.5 }))
        .pipe(cssnano())
        .pipe(rename(function(path) {
            path.basename += ".min";
        }))
        .pipe(gulp.dest('./styles'));
});


// gulp.task('watch', ['sass', 'christmas', 'christmas-1','lucky','duyao-vote'], function () {
//   gulp.watch('sass/*.scss', ['sass', 'christmas', 'christmas-1','duyao-vote']);
// });
gulp.task('watch', ['pay-prefer', 'sass', 'ranking'], function() {
    gulp.watch('sass/pay-prefer.scss', ['pay-prefer']);
    gulp.watch('sass/*.scss', ['sass', 'ranking']);
});

gulp.task('default', ['watch']);
```