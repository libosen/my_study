响应式Web设计
============

## 基于 Foundation Framework

安装 Ruby，[Ruby for Windows](http://rubyinstaller.org) 
```
ruby --version
gem --version
```

安装 sass, compass, foundation framework
```
sudo gem install sass
sudo gem uninstall sass //删除sass
sass --version
sudo gem install compass //也会安装sass
sudo gem install zurb-foundation
```
建立项目
```
compass create bussiness -r zurb-foundation --using foundation
```
了解项目内容  
基本设置
```
建立 SCSS 文件 _config.scss
复制 _setting.scss 到 _config.scss
建立 base.scss
复制 app.scss 到 base.scss
base.css: @import "settings" -> @import "config"
create style.scss
style.scss: @import "config"
```
compass 项目设置
```
config.rb: relative_assets = true //使用相对路径
```
监视 SCSS 更改
```
bussinese: compass watch //自动生成CSS
```
设置 normalize.css
```
_normalize.scss -> normalize.scss
```
修改 index.html
```
<!DOCTYPE html>
<!--[if IE 8]>         <html class="no-js lt-ie9" lang="en" > <![endif]-->
<!--[if gt IE 8]><!--> <html class="no-js" lang="en" > <!--<![endif]-->
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Foundation 4</title>
  <link rel="stylesheet" href="stylesheets/normalize.css">
  <link rel="stylesheet" href="stylesheets/base.css">
  <link rel="stylesheet" href="stylesheets/style.css">
  <script src="javascripts/vendor/custom.modernizr.js"></script>
</head>
<body>
  <script>
  document.write('<script src=' +
  ('__proto__' in {} ? 'javascripts/vendor/zepto' : 'javascripts/vendor/jquery') +
  '.js><\/script>')
  </script>
  <script src="javascripts/foundation/foundation.js"></script>
  <script src="javascripts/foundation/foundation.orbit.js"></script>
  <script src="javascripts/foundation/foundation.placeholder.js"></script>
  <script src="javascripts/foundation/foundation.topbar.js"></script>
  <script>
    $(document).foundation();
  </script>
</body>
</html>
```
添加导航条
```
  <div class="contain-to-grid">
    <nav class="top-bar" role="navigation">
      <ul class="title-area">
        <li class="name">
          <h1><a href="index.html">business</a></h1>
        </li>
        <li class="toggle-topbar menu-icon">
          <a href="#"><span>Menu</span></a>
        </li> 
      </ul>

      <section class="top-bar-section">
        <ul class="left">
          <li class="has-dropdown">
            <a href="#">Services</a>
            <ul class="dropdown">
              <li><a href="#">Web Design</a></li>
              <li><a href="#">Graphic Design</a></li>
              <li><a href="#">Icon Design</a></li>
              <li><a href="#">WordPress Theme</a></li>
              <li><a href="service.html">See all &rarr;</a></li>
            </ul> 
          </li>
          <li><a href="pricing.html">Pricing</a></li>
          <li><a href="about.html">About</a></li>
          <li><a href="contact.html">Contact</a></li>
        </ul>
        <ul class="right">
         <li class="has-form">
           <form>
             <div class="row collapse">
               <div class="small-8 columns">
                 <input type="search" name="search" placeholder="Input the keyword">
               </div>
               <div class="small-4 columns">
                 <a href="#" class="button success">Search</a>
               </div>
             </div>
           </form>
         </li>
       </ul>
     </section>
   </nav>
 </div>
```
添加 footer
```
<footer class="footer" role="contentinfo">
  <div class="row">
    <div class="large-6 columns footnav">
      <ul class="inline-list">
        <li><a href="#">Home</a></li>
        <li><a href="#">Service</a></li>
        <li><a href="#">Pricing</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </div>
    <div class="small-4 columns social">
      <ul class="inline-list">
        <li class="facebook"><a href="#">Facebook</a></li>
        <li class="twitter"><a href="#">Twitter</a></li>
        <li class="linkedin"><a href="#">LinkedIn</a></li>
        <li class="dribbble"><a href="#">Dribbble</a></li>
      </ul>
    </div>
  </div>
  <div class="row">
    <div class="large-12 columns copyright">
      <p>&copy; 2012 Business. All rights reserved.</p>
    </div>
  </div>
</footer>
```
复制 index.html -> service.html, pricing.html, about.html, contact.html
添加 index.html 内容
```
title -> Home

<div class="row content home">
  <div class="large-12 columns">
    <div class="row slideshow">
      <ul data-orbit>
        <li>
          <div class="large-6 columns">
            <h3>This is the first slide</h3>
            <p>Carrot cake apple pie sweet jelly beans jujubes dragée dessert cake. Cake cheesecake cookie sesame snaps tart applicake jelly bonbon.</p>
            <a href="#" class="large button radius hide-for-small">Click Me!</a>
          </div>
        </li>
        <li>
          <div class="large-6 columns">
            <h3>We are the second one</h3>
            <p>Sweet roll cheesecake gingerbread fruitcake sweet roll. Marzipan sweet faworki carrot cake dragée lemon drops applicake muffin cotton candy.</p>
            <a href="#" class="large button radius hide-for-small">Pay a Visit!</a>
          </div>
        </li>
        <li>
          <div class="large-6 columns">
            <h3>We are the third</h3>
            <p>Brownie gummi bears jujubes. Biscuit danish tootsie roll cotton candy oat cake jujubes dessert pastry bear claw.</p>
            <a href="#" class="large button radius hide-for-small">Click Me As Well!</a>
          </div>
        </li>
        <li>
          <div class="large-6 columns">
            <h3>We are the last</h3>
            <p>Liquorice brownie sugar plum cookie lemon drops chocolate bar faworki chocolate bar. Brownie carrot cake muffin cake topping.</p>
            <a href="#" class="large button radius hide-for-small">This is a Button</a>
          </div>
        </li>
      </ul>
    </div>

    <div class="row intro">
      <div class="large-9 columns">
        <h3>Welcome to Our Website <small>Marzipan pudding candy applicake</small></h3>
        <p>Caramels marzipan sesame snaps sugar plum carrot cake brownie jujubes sweet roll. Faworki topping jujubes. Marzipan pudding candy applicake.</p>
      </div>
      <div class="large-3 columns">
        <a href="#" class="large button radius">Take a Tour</a>
      </div>
    </div>

    <section class="row features">
      <div class="large-12 columns">
        <h3 class="title-section">Features</h3>
        <p>Toffee jelly candy sweet cotton candy carrot cake applicakewypas carrot cake. Wafer faworki sweet roll...</p>

        <div class="row">
          <div class="large-3 columns feature">
            <h4>Cake apple</h4>
            <p>Croissant apple pie dragee cheesecake gummi bears croissant. Wafer apple pie dragee wafer sweet roll tart croissant lollipop donut. Topping sesame snaps oat cake  wafer jujubes pie candy canes brownie.</p>
          </div>
          <div class="large-3 columns feature">
            <h4>Candy halvah</h4>
            <p>Cotton candy danish muffin jelly biscuit ice cream caramels. Chocolate cake fruitcake liquorice tootsie roll biscuit wafer croissant liquorice. Oat cake tootsie roll topping candy.</p>
          </div>
          <div class="large-3 columns feature">
            <h4>Biscuit snaps</h4>
            <p>Carrot cake sweet pie chupa chups pudding liquorice croissant cookie pie. Sugar plum soufflé marzipan sugar plum jelly-o. Liquorice sweet tiramisu danish croissant cookie pie.</p>
          </div>
          <div class="large-3 columns feature">
            <h4>Souffle sweet</h4>
            <p>Icing donut tootsie roll danish carrot cake cotton candy. Gummi bears croissant pudding pudding chocolate ice cream candy muffin wypas. Croissant jelly biscuit faworki.</p>
          </div>
          </div>
        </div>
      </div>
    </section>

    <section class="row projects">
      <div class="large-12 columns">
        <h3 class="title-section">Featured Projects</h3>
        <p>Lollipop powder marzipan topping cheesecake danishwypas...</p> 
      </div>
      <div class="row">
        <div class="large-4 columns project">
          <figure>
              <a href="#" class="th radius"><img src="img/stat.png" alt="Analytic Application"></a>
          </figure>
          <h4>Jelly-o Sweet</h4>
          <p>Gummi bears biscuit souffle candy marshmallow. Tiramisu tart cupcake bear claw muffin cheesecake dragée toffee chocolate bar.</p>
        </div>
        <div class="large-4 columns project">
          <figure>
              <a href="#" class="th radius"><img src="img/cart.png" alt="Shopping Website"></a>
          </figure>
          <h4>Gingerbread Dessert</h4>
          <p>Tootsie roll candy liquorice cupcake cake donut brownie. Gingerbread dessert cake wafer pastry oat cake chupa chups pastry oat cake.</p>
        </div>
        <div class="large-4 columns project">
          <figure>
              <a href="#" class="th radius"><img src="img/growl.png" alt="OSX Notification, Growl"></a>
          </figure>
          <h4>Tiramisu Tart</h4>
          <p>Sweet dragée candy canes soufflé tart croissant. Tootsie roll candy canes donut applicake. Pudding jujubes brownie.</p>
        </div>
      </div>
    </section>
  </div>
</div>
```
service.html
```
title -> Pricing
<div class="row content page our-services">
  <div class="large-12 columns">
    <ul class="breadcrumbs">
      <li><a href="index.html">Home</a></li>
      <li class="current"><a href="#">Services</a></li>
    </ul>
    <section class="row page intro">
      <div class="large-12 columns">
        <h2>Our Services</h2>
        <h3 class="subheader">Tart croissant jelly beans oat cake donut.</h3>
        <p>Lemon drops toffee tootsie roll gingerbread macaroon. Chocolate topping cotton candy cheesecake chocolate cake ...</p>
      </div>
    </section>
    <section class="row service-list">
      <div class="large-12 columns">
        <div class="row">
          <div class="large-6 columns service">
            <h4>Candy jelly beans</h4>
            <p>Dessert sugar plum muffin applicakeapplicake cheesecake wafer bonbon jelly beans. Icing donut marshmallow liquorice dessert chocolate ...<a href="#">Learn More &rarr;</a></p>
          </div>
          <div class="large-6 columns service">
            <h4>Sweet cupcake jelly</h4>
            <p>Jujubes halvah lollipop toffee sweet cupcake jelly. Chupachups chocolate carrot cake donut... <a href="#">Learn More &rarr;</a></p>
          </div>
        </div>
        <div class="row">
          <div class="large-6 columns service">
            <h4 class="setting">Cotton candy</h4>
            <p>Candy lollipop gummi bears jujubes pie. Cake brownie toffee brownie apple pie sesame snaps donut carrot cake. <a href="#">Learn More &rarr;</a></p>
          </div>
          <div class="large-6 columns service">
            <h4 class="setting">Cake brownie toffee</h4>
            <p>Candy lollipop gummi bears jujubes pie. Cake brownie toffee brownie apple pie sesame snaps donut carrot cake... <a href="#">Learn More &rarr;</a></p>
          </div>
        </div>
        <div class="row">
          <div class="large-6 columns service">
            <h4>Cupcake icing</h4>
            <p>Brownie liquorice jelly. Macaroon pudding jelly beans pastry. Gummies sugar plum jelly-o. ...<a href="#">Learn More &rarr;</a></p>
          </div>
          <div class="large-6 columns service">
            <h4>Cake donut</h4>
            <p>Muffin sweet biscuit jujubes. Cake donut bear claw sweet roll soufflé lemon drops tootsie roll cookie halvah... <a href="#">Learn More &rarr;</a></p>
          </div>
        </div>
      </div>
    </section>
    <div class="panel">
       <div class="row">
         <div class="large-9 columns intro">
           <p>Toffee sweet roll wypas jelly chocolate cake. Lemon drops jelly-o pudding fruitcake gingerbread sesame snaps tootsie roll lemon drops gingerbread...</p>
         </div>
         <div class="large-3 columns">
           <a class="button large radius" href="#">See Pricing</a>
         </div>
       </div>
    </div>
  </div>
</div>
```
pricing.html
```
title -> Pricing
  <div class="row content page pricing">
    <div class="large-12 columns">
      <ul class="breadcrumbs">
        <li><a href="index.html">Home</a></li>
        <li class="current"><a href="#">Pricing</a></li>
      </ul>
      <section class="row page intro">
        <div class="large-12 columns">
          <h2>Pricing and Plan</h2>
          <h3 class="subheader">Tart croissant jelly beans oat cake     donut.</h3>
          <p>Lemon drops toffee tootsie roll gingerbread macaroon. Chocolate topping cotton candy cheesecake chocolate cake. Chupachups caramels marzipan bonbon danish candy canes.</p>
        </div>
      </section>
      <div class="row compare">
        <div class="large-4 columns four">
          <ul class="pricing-table">
            <li class="title">Basic</li>
            <li class="price">$10.99</li>
            <li class="description">Lollipop cotton candy wafer caramels       tootsie roll.</li>
            <li class="bullet-item">1 Cheesecake</li>
            <li class="bullet-item">2GB Chocolate</li>
            <li class="bullet-item">5 Candies</li>
            <li class="bullet-item">7 Cupcakes</li>
            <li class="bullet-item">8 Beans</li>
            <li class="bullet-item">10 Carrots</li>
            <li class="cta-button">
              <a class="button radius" href="#">Order Now &raquo;</a>
            </li>
          </ul>
        </div>
        <div class="large-4 columns">
          <ul class="pricing-table">
            <li class="title">Standard</li>
            <li class="price">$20.99</li>
            <li class="description">Pastry fruitcake cheesecake halvah
        croissant.</li>
            <li class="bullet-item">3 Cheesecake</li>
            <li class="bullet-item">4GB Chocolate</li>
            <li class="bullet-item">10 Candies</li>
            <li class="bullet-item">15 Cupcakes</li>
            <li class="bullet-item">20 Beans</li>
            <li class="bullet-item">25 Carrots</li>
            <li class="cta-button">
              <a class="button radius" href="#">Order Now &raquo;</a>
            </li>
          </ul>
        </div>
        <div class="large-4 columns">
          <ul class="pricing-table">
            <li class="title">Professional</li>
            <li class="price">$30.99</li>
            <li class="description">Cupcake sweet roll apple pie bonbon.</li>
            <li class="bullet-item">5 Cheesecake</li>
            <li class="bullet-item">6GB Storage</li>
            <li class="bullet-item">15 Candies</li>
            <li class="bullet-item">30 Cupcakes</li>
            <li class="bullet-item">35 Beans</li>
            <li class="bullet-item">40 Carrots</li>
            <li class="cta-button"><a class="button radius" href="#">Order Now &raquo;</a></li>
          </ul>
        </div>
      </div>
      <section class="row testimonial">
        <div class="large-12 columns">
          <h3>Testimonial</h3>
          <p>Toffee pastry jelly bear claw icing sweet roll fruitcake. Faworki jujubes pastry donut marzipan chupachups bear claw gummies            cheesecake.</p>
          <div class="row">
            <div class="columns large-4">
              <blockquote>
                <p>Macaroon tootsie roll tiramisu macaroon marshmallow. Pudding gummies biscuit halvah donut lemon drops. Gingerbread applicake pastry jelly beans liquorice icing. <cite>John Doe</cite></p>
              </blockquote>
            </div>
            <div class="columns large-4">
              <blockquote>
                <p>Lollipop powder marzipan topping cheesecake danishwypas. Bonbon caramels gingerbread pudding liquorice donut sweet sugar plum. Candy canes brownie sesame snaps cake. <cite>John Doe Sister</cite></p>
              </blockquote>
            </div>
            <div class="columns large-4">
              <blockquote>
                <p>Dragée jujubes pudding sweet roll cake sesame snaps soufflé ice cream muffin. Gingerbread sweet gingerbread marshmallow bear claw. Dragée biscuit brownie apple pie sesame snaps oat cake dessert pudding. <cite>John Doe Brother</cite></p>
              </blockquote>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
```
about.html
```
title -> About

<div class="row content page about">
  <div class="large-12 columns">
    <ul class="breadcrumbs">
      <li><a href="index.html">Home</a></li>
      <li class="current"><a href="#">About</a></li>
    </ul>
    <section class="row page intro">
      <div class="large-12 columns">
        <h2>About Us</h2>
        <h4 class="subheader">Tart croissant jelly beans oat cake donut.</h4>
        <p>Lollipop applicake biscuit. Macaroon jelly beans caramels faworkioat cake marshmallow pudding. Candy pastry oat cake marzipan pie sugar plum donut. Souffle donut croissant. Marzipan brownie marzipan soufflé liquorice cotton candy liquorice chocolate gingerbread.</p>
      </div>
    </section>
    <div class="row story">
      <div class="large-8 columns">
        <h4>Our Story</h4>
        <p>Lollipop applicake biscuit. Macaroon jelly beans caramels faworki oat cake marshmallow pudding...</p>
        <p>Jujubes chocolate oat cake cheesecake candy pie sugar plum donut. Tiramisu biscuit pudding icing candy.Apple pie jelly biscuit.Faworki powder chocolate cake ice cream...</p>
        <div class="row">
          <div class="large-4 columns">
            <h4>Cookie lollipop</h4>
            <p>Pie gummi bears chocolate cake topping. Sugar plum oat cake candy pie marshmallow sweet roll ice ...</p>
          </div>
          <div class="large-4 columns">
            <h4>Tiramisu biscuit</h4>
            <p>Liquorice macaroon cupcake jujubes. Jujubes marshmallow soufflé tiramisu bonbon donut. Tootsie roll icing chupachups jelly-o sesame snaps lollipop marzipan.</p>
          </div>
          <div class="large-4 columns">
            <h4>Faworki powder</h4>
            <p>Marshmallow wypas cookie caramels dessert cupcake pastry bear claw. Candy marshmallow ice cream candy gummi bears icing liquorice apple pie.</p>
          </div>
        </div>
      </div>
      <aside class="large-4 columns">
        <h4>Aside</h4>
        <figure>
          <img src="img/about.jpg" alt="about us image">
        </figure>
        <blockquote>
          <p>Pie gummi bears chocolate cake topping. Sugar plum oat cake candy pie marshmallow sweet roll ice cream marshmallow. Bear claw biscuit candy canes pastry jujubes sweet carrot cake wafer. Liquorice macaroon cupcake jujubes. Jujubes marshmallow soufflé tiramisu bonbon donut.<cite>Founder</cite></p>
        </blockquote>
      </aside>
    </div>
  </div>
</div>
```
contact.html
```
title -> Contact US

<div class="row content page contact"> 
  <div class="large-12 columns">
    <ul class="breadcrumbs">
      <li><a href="index.html">Home</a></li>
      <li class="current"><a href="#">Contact Us</a></li>
    </ul>
    <section class="row page intro">
      <div class="large-12 columns">
        <h2>Contact Us </h2>
        <h4 class="subheader">Tart croissant jelly beans oat cake donut.</h4>
        <p>Lol l ipop appl icake biscui t . Macaroon jel ly beans caramels faworkioat cake marshmallow pudding. Candy pastry oat cake marzipan pie sugar plum donut.</p>
      </div> 
    </section>
    <div class="row">
      <div class="large-7 columns">
        <figure>
          <a href="#" class="th"><img src="img/map.jpg"></a>
        </figure>
        <h3>Get in Touch</h3>
        <p>Macaroon jelly beans caramels faworki oat cake marshmallow pudding. Candy pastry oat cake marzipan pie sugar plum</p> 
        <div class="row panel">
          <div class="large-8 columns intro">
          <p>Toffee sweet rol l wypas jel ly chocolate cake. Lemon drops
          jel ly-o pudding frui tcake gingerbread sesame snaps lemon drops gingerbread.</p>
          </div>
          <div class="large-4 columns">
            <ul class="call-us">
              <li class="phone">(000) 123-45678</li>
              <li class="email">
                <a href="#">johndoe@packt.com</a>
              </li> 
            </ul>
          </div> 
        </div>
      </div> 
      <div class="large-5 columns">
        <form method="get"> 
          <fieldset>
            <legend>Contact Form</legend> 
            <div class="row">
              <div class="large-12 columns">
                <label>Name</label>
                <input type="text" name="name"> 
                <label>Email</label>
                <input type="email" name="email"> 
                <label>Twitter</label>
                <div class="row collapse">
                  <div class="large-2 small-2 columns">
                    <span class="prefix">@</span>
                  </div>
                  <div class="large-10 small-10 columns"> 
                    <input type="text" placeholder="youremail"> 
                  </div>
                </div>
                <label>URL</label>
                <div class="row collapse">
                  <div class="large-9 small-9 columns"> 
                    <input type="url" placeholder="yourwebsite"> 
                  </div>
                  <div class="large-3 small-3 columns">
                    <span class="postfix">.com</span>
                  </div>
                </div> 
              </div>
            </div>
            <label>Message</label>
            <textarea name="message"></textarea>
          </fieldset>
          <button class="button large radius" type="submit">Submit</button>
        </form>
      </div>
    </div>
  </div>
</div>
```
compass 监视修改
```
compass watch
```
_config.scss
```
$em-base: 16px !default;
$body-bg: #f9f8f4;
$body-font-color: #473016;
$primary-color: #00a1d9;
$secondary-color: #c2bdb7;
$success-color: #a8bb26;
$black: #000;
$white: #fff;
$grey: lighten($black, 50%);
$dark-grey: lighten($black, 30%);
$light-grey: darken($white, 10%);
$column-gutter: 3.125em;
```
修改导航颜色 _config.css
```
$topbar-bg: $primary-color;
$topbar-dropdown-link-bg: lighten($primary-color, 5%);
$topbar-link-bg-hover: darken($primary-color, 3%);
$topbar-link-bg-active: darken($primary-color, 3%);
```
修改footer style.scss
```
@import "config";

.footer {
  margin-top: emCalc(25px);
  a {
    color: $body-font-color;
  }
}

.footnav {
  ul {
    margin: emCalc(5px) 0 0 0;
  }
  li {
    margin-left: 0;
    margin-right: emCalc(15px);
  }
  a {
    &:hover {
      text-decoration: underline;
    }
  }
}

@import "social/*.png";
.social {
  $height: social-sprite-height(facebook);
  $width: social-sprite-width(facebook);
  ul {
    float: right;
  }
  li {
    a {
      display: inline-block;
      height: $height;
      width: $width;
      /*css image replacement*/ 
      text-indent: 100%; 
      white-space: nowrap; 
      overflow: hidden;
    }
    &.facebook a {
      @include social-sprite(facebook); 
      &:hover {
        @include social-sprite(facebook-hover); 
      }
    }
    &.twitter a {
      @include social-sprite(twitter); 
      &:hover {
        @include social-sprite(twitter-hover); 
      }
    }
    &.linkedin a {
      @include social-sprite(linkedin); 
      &:hover {
        @include social-sprite(linkedin-hover); 
      }
    }
    &.dribbble a {
      @include social-sprite(dribbble); 
      &:hover {
        @include social-sprite(dribbble-hover); 
      }
    }
  }
}
```

