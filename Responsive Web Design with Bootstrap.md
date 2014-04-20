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

    .container
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
extends layout
block title
  title Home

  
block content 
  .jumbotron.row
    .col-md-7
      h1 Hello World. Welcome to our website!
      p Lorem Ipsum! Only
      p USD50.0
    .col-md-5
      img(src="img/hero-image.png", alt="hero image")

  .row
    .col-md-9
      p.
        Brownie oat cake donut gummies carrot macaroon cake
        jel ly-o. Cheesecake apple pie gummi bears.
    .col-md-3
      a(href="#").btn.btn-primary Order Now
  
  hr
  
  .row
    each item in [1, 2, 3, 4]
      figure.col-md-3
        img(src="img/image-#{item}.jpg", alt="featured prodict no.#{item}").img-thumbnail

  hr

  .row
    p.
      Oat cake jel ly faworki . Tootsie rol l powder faworki applicake. Marshmallow macaroon icing soufflé.

    form.form-inline(action="index_submit" method="get" accept-charset="utf-8")
      .form-group
        label.sr-only(for="email_subscribe") Email subscribe
        input.form-control(type="email" name="email_subscribe" placeholder="Input your email address")
      button.btn.btn-lg(type="submit") Submit
```

### create src/jade/gallery.jade
```jade
extends layout
block title
  title Gallery
block content
  h1 Plush Gallery <small>colloction to our previous toys</small>
  .row
    - for (var index = 1; index <= 16; index++)
      figure.col-md-3
        img(src="img/image-#{index}.jpg" alt="product image no.#{index}").img-thumbnail
```
### create src/jade/contact.jade
```jade
extends layout
block title
  title Contact
  
block content
  h1 Contact Us <small>we would l ike to hear from you</small>
  
  .row.hidden-sm
    .col-md-12
      img(src="img/map.jpg", alt="This is where we are").img-thumbnail

  hr

  .row
    .col-md-6
      h3 KudosPlush Toys
      address.
        Street Anywhere In the World 123<br>
        The Count ry, NaN 123456<br>
        <abbr title="Phone">P.</abbr> (123) 987-654321 <br> 
        <abbr title="Fax">F.</abbr> (123) 123-123456
      p.
        Cupcake ipsum dolor si t amet oat cake cot ton candy
        carrot cake gummi bears. Chupa chups croissant powder danish toffee pudding jujubes cupcake cotton candy. Tootsie rol l jel ly beans macaroon sweet faworki dragée.
      p.
        Jelly danish danish chocolate cake gingerbread candy frui tcake donut jel ly beans. Dragée cheesecake tootsie rol l halvah carrot cake frui tcake sweet rol l . Topping dragée pudding. Candy oat cake candy canes.
    .col-md-6
      h4 Contact from
      form.form-horizontal
        .form-group
          label.col-sm-4.control-label(for="name") Your Name
          .col-sm-8
            input#name.form-control(type="email" placeholder="zhangj inglin")
        .form-group
          label.col-sm-4.control-label(for="email") Email Adress
          .col-sm-8
            input#email.form-control(type="text", placeholder="zhangjinglin@gmail.com")
        .form-group
          label.col-sm-4.control-label(for="message") Your message
          .col-sm-8
            input#message.form-control(type="text")
        .form-group
          .col-sm-offset-4.col-sm-8
            button.btn.btn-default(type="submit") Submit
```
### create src/jade/about.jade
```jade
extends layout
block title
  title About
block content
  h1 About <small>read the story</small>
  .row
    .col-md-6
      img(src="img/img-about.jpg").img-thumbnail
    .col-md-6
      p.
        Donut pie brownie sweet lollipop. Lollipop wypas dessert sesame snaps chocolate cake chocolate bar croissant. Lollipop jelly jelly liquorice bonbon sweet. Jelly beans cheesecake carrot cake. Liquorice croissant chocolate cake marshmallow tootsie roll sugar plum wypas pudding sweet roll. Chupa chups sugar plum powder gingerbread bonbon. Tiramisu tart cookie jelly beans.
  hr
  h3 Meet the Founders
  .row
    .col-md-6
      .row
        .col-md-4
          img(src="img/salman.jpg").img-thumbnail
        .col-md-8
          h4 Salman Fariz Alutfi
          p Donut pie brownie sweet lollipop. Lollipop wypas dessert sesame snaps chocolate cake chocolate bar croissant. Lollipop jelly jelly liquorice bonbon sweet. Jelly beans cheesecake carrot cake.   
    .col-md-6
      .row
        .col-md-4
          img(src="img/arif.jpg").img-thumbnail
        .col-md-8
          h4 Arief Bahari
          p Donut pie brownie sweet lollipop. Lollipop wypas dessert sesame snaps chocolate cake chocolate bar croissant. Lollipop jelly jelly liquorice bonbon sweet. Jelly beans cheesecake carrot cake.   
```
### creare src/jade/policy.jade
```jade
extends layout
block title
  title Policy
block content
  h1 Privacy &amp; Policy <small>sweet user agreement</small>
  .col-md-6
    h3 Donut pie brownie sweet lollipop.
    p Donut pie brownie sweet lollipop. Lollipop wypas dessert sesame snaps chocolate cake chocolate bar croissant. Lollipop jelly jelly liquorice bonbon sweet. Jelly beans cheesecake carrot cake. Liquorice croissant chocolate cake marshmallow tootsie roll sugar plum wypas pudding sweet roll. Chupa chups sugar plum powder gingerbread bonbon. Tiramisu tart cookie jelly beans. Lemon drops ice cream dessert. Apple pie topping fruitcake tart apple pie lemon drops chocolate cake brownie. Caramels icing toffee marshmallow jujubes donut pastry jelly-o icing. Wafer sesame snaps liquorice sweet. Dragée danish apple pie candy chocolate bar wypas. Gummi bears macaroon powder bear claw. Chocolate cake jelly pastry jujubes chocolate apple pie.
    h3 Chocolate cake liquorice topping
    p Chocolate cake liquorice topping gingerbread wypas toffee dessert. Pie powder wafer oat cake liquo rice gummies. Lemon drops chupa chups danish muffin pastry faworki halvah. Jujubes sweet danish gummies jelly-o donut biscuit. Toffee sesame snaps wypas jelly-o jelly-o ice cream jelly.
    h3 Powder jelly toffee marshmallow cake
    p Soufflé chocolate bar pastry dragée. Cake soufflé lemon drops tiramisu halvah pie apple pie. Candy canes sweet roll jujubes oat cake gingerbread. Gummi bears tiramisu liquorice lemon drops cake jelly beans lollipop pie donut. Liquorice brownie brownie muffin halvah wypas. Gummi bears applicake cotton candy chocolate cake donut. Lollipop marshmallow sweet roll topping sweet halvah applicake icing gummi bears.
    h3 Tiramisu candy canes lollipop.
    p Cheesecake chocolate bar donut. Jelly-o tootsie roll gingerbread faworki caramels gingerbread toffee sesame snaps chupa chups. Tootsie roll wafer sesame snaps sweet roll biscuit bear claw. Candy canes carrot cake sweet cake chocolate bar gummies. Pudding candy canes cookie applicake cotton candy. Jujubes icing jelly beans pie gummies.
  .col-md-6
    h3 Powder jelly toffee marshmallow cake
    p Cupcake ipsum dolor sit. Amet bear claw croissant. Pudding toffee jujubes topping ice cream icing chupa chups. Cotton candy cupcake sugar plum lemon drops. Pastry pudding croissant cupcake. Croissant macaroon chocolate cake. Muffin cotton candy jelly beans chocolate candy canes. Sesame snaps oat cake candy pudding chocolate cookie.
    h3 Powder candy canes gummies sweet roll
    p Powder candy canes gummies sweet roll. Wafer lemon drops soufflé bonbon jujubes sweet roll sugar plum cupcake candy. Powder jujubes topping liquorice halvah dragée. Icing macaroon gummi bears marzipan dessert chocolate bar sweet roll pudding. Fruitcake jelly-o halvah. Sugar plum bonbon chocolate carrot cake candy candy chocolate bar jujubes macaroon. Pie gingerbread chocolate bonbon gingerbread.
    p Sweet roll jelly-o bonbon carrot cake caramels lemon drops muffin. Toffee lemon drops applicake tootsie roll sesame snaps oat cake. Marzipan topping chocolate sesame snaps chocolate. Pudding liquorice cookie danish liquorice. Pastry apple pie bear claw macaroon apple pie. Topping croissant carrot cake gummies sesame snaps.
    h3 Marshmallow cupcake gummi bears muffin sesame snaps.
    p Marshmallow cupcake gummi bears muffin sesame snaps. Sweet cotton candy carrot cake brownie cookie cupcake. Wypas candy caramels oat cake lollipop cotton candy icing. Bonbon pastry cookie jelly beans chocolate bar jelly beans. Cupcake toffee cake marshmallow. Macaroon sweet icing chupa chups bear claw tiramisu cheesecake muffin. Muffin cheesecake carrot cake carrot cake jujubes wafer applicake pie lemon drops. Cotton candy wafer chocolate marshmallow dessert candy pastry.
```
### setting the style in src/less/main.less
```less
@import "../bootstrap/less/bootstrap.less";

// 定义基本变量
// 字体
@primaryFont: Arial, sans-serif;
@baseFontSize: 16px;
@lineHeight : @baseFontSize * 2;
@baseLength: 10px;

// 颜色
@primaryColor: #3e6b6d; //green
@secondaryColor: #cd9a62; //brown
@tertiaryColor: #fff7b6; //cream
@black: #000;
@white: #FFF;

// 图像替换
.ir {
  text-indent: 100%;
  white-space: nowrap;
  overflow: hidden;
}

// 基础元素设定

body {
  font-family: @primaryFont;
  font-size: @baseFontSize;
  line-height: @lineHeight;
}

h1, h2, h3, h4, h5, h6 {
  color: @secondaryColor;
}

hr {
  border: 0;
  height: 1px;
  background-image: -webkit-linear-gradient(left, fade(@black, 0%), fade(@black, 15%), fade(@black, 0%)); 
  background-image:    -moz-linear-gradient(left, fade(@black, 0%), fade(@black, 15%), fade(@black, 0%)); 
  background-image:     -ms-linear-gradient(left, fade(@black, 0%), fade(@black, 15%), fade(@black, 0%)); 
  background-image:      -o-linear-gradient(left, fade(@black, 0%), fade(@black, 15%), fade(@black, 0%));
  background-image:          linear-gradient(left, fade(@black, 0%), fade(@black, 15%), fade(@black, 0%));
  margin: (@baseLength * 4) 0;
}

.btn {
  .button-variant(@white, @secondaryColor,  @white);
  text-shadow: 1px, 1px, 0, fade(@black, 30%) ;
}

.btn-primary {
  font-size: @baseFontSize * 1.2;
  padding: (@baseLength * 2) (@baseLength * 4);
  text-transform: uppercase;
  .button-variant(@white, @primaryColor, @black);
}

// 页面头部
@navbar-default-bg: darken(@white, 2%);
@navbar-default-link-color: @primaryColor;
@navbar-default-link-hover-color: @tertiaryColor;
@navbar-default-link-hover-bg: @primaryColor;
@navbar-default-link-active-color: @tertiaryColor;
@navbar-default-link-active-bg: @primaryColor;

header {
  background-color: darken(@white, 2%);
  padding: (@baseLength * 2) 0;
  .navbar {
    border: none;
  }
  .navbar-brand {
    .ir;
    width: 188px;
    height: 100px;
    padding: 0;
    background: url('../img/plush-logo.png') no-repeat;
  }
  ul.nav {
    margin-top: @baseLength * 3;
    li {
      margin-left: @baseLength * 2;
      a {
        border-radius: 3px;
      }
    }
  }
}


// 页面底角
footer {
  color: lighten(@black, 70%);
  background-color: darken(@white, 2%);
  padding: (@baseLength * 5) 0;
  margin-top: @baseLength * 3;
  ul {
    margin: 0;
    li {
      display: inline;
      margin-right: @baseLength;
      a {
        color: lighten(@black, 70%);
        &:hover {
            color: lighten(@black, 30%);
            text-decoration: none;        
        }
      }
    }
  }
  .copyright {
    text-align: right;
    display: block;
  }
  .social-links {
    text-align: right;
    li {
      margin-right: 0;
    }
    a {
      display: inline-block;
      width: 36px;
      height: 42px;
      .ir;
    }
    .dribbble a, .facebook a, .twitter a {
      background-image: url('../img/social.png'); 
      background-repeat: no-repeat; 
    }
    .dribbble a {
      background-position: -7px -58px;
      &:hover {
        background-position: -7px 0;
      }
    }
    .facebook a { 
      background-position: -7px -174px;
      &:hover {
        background-position: -7px -116px;
      }
    }  
    .twitter a {
      background-position: -7px -290px;
      &:hover {
        background-position: -7px -232px;
      }
    }
  }
}

// index 中的 hero
.jumbotron {
  background-color: @white;
  padding: (@baseLength * 3) 0;
  color: @primaryColor;
  margin-bottom: 0;
  p {
    font-size: @baseFontSize * 2.8;
    line-height: @lineHeight * 1.8;
  }
  .price {
    font-weight: bold;
    color: @secondaryColor;
  }
}

.cta {
  margin-top: @baseLength * 4;
  .copy-text {
    color: @secondaryColor;
    font-size: @baseFontSize * 1.5;
  }
}

.testimonial {
  font-size: @baseLength * 3;
  padding-bottom: @baseLength * 2;
  color: lighten(@black, 50%);
  text-align: center;
}
.subscribe-form {
  margin-bottom: @baseLength * 2;
  text-align: center;
  input, button {
    height: @baseLength * 5;
    padding: @baseLength (@baseLength * 2);
    margin-bottom: 0;
  }
}
```