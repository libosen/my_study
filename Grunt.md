Grunt
===================
### Why Grunt
**Automation**

### install
```
nodejs
npm install -g grunt-cli
```

### first project
```
mkdir project1
npm init // create package.json
npm install grunt --save-dev //grunt 不是运行包，而是开发包，可以使用 --save 参数，将package 放置在 dependencies 段中， 而 --save-dev 将放置在 devDependencies 段中
npm install grunt-contrib-jshint --save-dev // 安装 JsHint, js 代码质量保证工具
npm install grunt-contrib-uglify --save-dev // 安装 uglify，js 最小化工具
现在运行 grunt // A valid Gruntfile could not be found. 
```

### 建立 Gruntfile.js
```javascript
module.exports = function (grunt) {
  grunt.initConfig({
    uglify: {
      options: {
        mangle: true,  // 变量名压缩
        compress: true, // 代码压缩
        sourceMap: 'dist/application.map', // 生成 map
        banner: '/* zhangjinglin 2014 */\n' // 文件描述头
      },
      target: {
        src: 'src/application.js',
        dest: 'dist/application.min.js'
      }
    }
  });

  grunt.loadNpmTasks('grunt-contrib-uglify');
}
```

### 建立 src/application.js
```javascript
var MyModule = (function() {
  function sayHi(name) {
    return 'Hi, ' + name + '!';
  }

  return {
    sayHi: sayHi
  };
  
})();
```

### 运行 Grunt
```bash
grunt uglify
```

### 多个 target
```javascript
odule.exports = function (grunt) {
  grunt.initConfig({
    uglify: {
      options: {
        mangle: true,  // 变量名压缩
        compress: true, // 代码压缩
        sourceMap: 'dist/application.map', // 生成 map
        banner: '/* zhangjinglin 2014 */\n' // 文件描述头
      },
      target: {
        src: 'src/application.js',
        dest: 'dist/application.min.js'
      },
      util: {
        src: 'src/util.js',
        dest: 'dist/util.min.js'
      }
    }
  });

  grunt.loadNpmTasks('grunt-contrib-uglify');
}
```
```bash
grunt uglify // 两个任务生成
grunt uglify:util // 指定任务生成
```
