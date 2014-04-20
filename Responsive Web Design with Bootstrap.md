使用 Bootstrap 设计响应式 Web 网站
===============================

### 建立项目目录
> MyWeb   
> /src   
> /src/less  
> /src/jade   
> /dist  
> /dist/js  
> /dist/js/lib  
> /dist/css
> /dist/img 

### 初始化项目
```bash
npm init
```
```javascript
{
  "name": "MyWeb",
  "version": "0.0.1",
  "description": "this is a responsive web with bootstrap sample.",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "zhangjinglin 2014.4",
  "license": "MIT"
}
```
安装 Grunt 及依赖任务
```
npm install grunt --save-dev
npm install grunt-contrib-less --save-dev
npm install grunt-contrib-jade --save-dev
npm install grunt-contrib-watch --save-dev
npm install grunt-contrib-connect --save-dev
```

### 建立 Gruntfile.js
```javascript
module.exports = function(grunt) {
  grunt.initConfig({
    less: {
      target: {
        expand: true,
        cwd: 'src/less',
        src: '**/*.less',
        dest: 'dist/css',
        ext: '.css'
      }
    },

    jade: {
      options: {
        pretty: true
      },
      target: {
        expand: true,
        cwd: 'src/jade',
        src: '**/*.jade',
        dest: 'dist/',
        ext: '.html'
      }
    },

    connect: {
      options: {
        port: 3000,
        open: true,
        hostname: 'localhost',
        livereload: 35729,
        base: 'dist/'
      },
      livereload: {
      },
    },

    watch: {
      less: {
        files: 'src/less/**/*.less',
        tasks: 'less'
      },
      jade: {
        files: 'src/jade/**/*.jade',
        tasks: 'jade'
      },
      livereload: {
        options: {
          livereload: 35729
        },
        files: [
          'dist/**/*.html',
          'src/less/**/*.less',
          'src/jade/**/*.jade'
        ]
      }
    },
  });

  grunt.loadNpmTasks('grunt-contrib-less');
  grunt.loadNpmTasks('grunt-contrib-jade');
  grunt.loadNpmTasks('grunt-contrib-watch');
  grunt.loadNpmTasks('grunt-contrib-connect');

  grunt.registerTask('default', ['connect', 'watch']);
};
```

### 获取 Web 组件
- 我们有两种方式获取 Bootstrap，一种是[官方站点](http://getbootstrap.com)或者通过[github](http://github.com/twitter/bootstrap)来下载， 我们通过Github下载。
```bash
cd src/
git clone https://github.com/twbs/bootstrap.git bootstrap
```
- 获取[jQuery](http://jquery.com)，命名为 jquery.js，放置在 /js/lib 中
- 将图像放置在 /imgs 中
- 将 src/bootstrap/dist/js/bootstrap.min.js 放置在 dist/js/lib 中

### Start Grunt
```bash
grunt
```

### create src/less/main.less
```less
@import "../bootstrap/less/bootstrap.less";
```

### create src/jade/layout.jade
```jade
doctype html
html
  head
    meta(charset="utf-8")
    block title
    link(href="css/main.css", rel="stylesheet")
    script(src="js/lib/jquery.min.js")
  body
    header
    
    .content
      block content

    footer
```
### set the header
```jade
nav.navbar.navbar-default
  .navbar-header
    button.navbar-toggle(type="button", data-toggle="collapse", data-target="#navlist")
      span.sr-only Toggle navigation
      span.icon-bar
      span.icon-bar
      span.icon-bar
    a.navbar-brand(href="#") Kudosplush
  #navlist.collapse.navbar-collapse
    ul.nav.navbar-nav.navbar-right
      li.active
        a(href="index.html") Home
      li
        a(href="gallery.html") Gallery
      li
        a(href="contact.html") Contact
```
### set the footer
```jade
.container
  .row
    .col-md-6
      .nav
        ul
          li
            a(href="index.html") Home
          li
            a(href="gallery.html") Gallery
          li
            a(href="contact.html") Contact
          li
            a(href="about.html") About
          li
            a(href="policy.html") Policy
    .col-md-6
      small Copyright &copy; 2014 Zhang Jinglin - All rights reserved
      ul
        li
          a(href="#") Facebook
        li
          a(href="#") Twitter
        li
          a(href="#") Dribbble
```
### create index.jade
```jade
```