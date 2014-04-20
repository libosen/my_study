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

### jshint
```javascript
npm install grunt-contrib-jshint --save-dev // 安装 JsHint, js 代码质量保证工具
jshint: {
  options: {
    eqeqeq:  true, // 总是 ===
    curly: true, // 总是 { }，即使只有一行
    undef: true, // 未定义的
    node: true, // nodejs 环境
  },
  target: {
    src: 'src/*.js'
  },
},

grunt.loadNpmTasks('grunt-contrib-jshint');
```
```
grunt jshint
```

### concat
```bash
npm install grunt-contrib-concat --save-dev
```
```javascript
grunt.loadNpmTasks('grunt-contrib-concat');

concat: {
  options: {
    seperator: ';',
    banner: '/* zhangjinglin 2014 */\n'
  },
  target: {
    src: ['src/application.js', 'src/util.js'],
    dest: 'dist/app.js'
  },
}
```
```bash
grunt concat
```

### 协同工作起来
```javascript
grunt.registerTask('default', ['jshint', 'concat', 'uglify']); // 放置在最末端，定义缺省任务

uglify: {
  options: {
    mangle: true,  // 变量名压缩
    compress: true, // 代码压缩
    banner: '/* zhangjinglin 2014 */\n' // 文件描述头
  },
  target: {
    src: 'dist/app.js', // concat 输出
    dest: 'dist/app.min.js'
  },
},
```
```bash
grunt
```

### 强大的 watch 
```bash
npm install grunt-contrib-watch --save-dev
```
```javascript
grunt.loadNpmTasks('grunt-contrib-watch');

watch: {
  scripts: {
    files: ['src/*.js'], // 监视所有的 js 文件， 一旦保存，马上运行任务
    tasks: ['jshint']
  }
}
```

### coffee
```bash
npm install grunt-contrib-coffee --save-dev
```
```javascript
grunt.loadNpmTasks('grunt-contrib-coffee');

coffee: {
      options: {
        bare: true, // 不采用 function()(); 方式
        join: false // 不要将 coffee 文件连接成一个
      },
      target: {
        expand: true, // 展开目录
        cwd: 'src/', // 源目录
        src: '*.coffee', // 源文件
        dest: 'lib/', // 目的目录
        ext: '.js' // 目的目录
      }
    }
```

### nodeunit
```bash
npm install grunt-contrib-nodeunit --save-dev
```
```javascript
grunt.loadNpmTasks('grunt-contrib-nodeunit');

nodeunit: {
      target: 'test/*_test.js'
    }

test/util_test.js

var util = require('../src/util');
exports.testH1 = function(test) {
  test.equal(util.h1('hi'), '<h1>hi</h1>', 'string should be equal');
  test.done();
}
```
### clean
```bash
npm install grunt-contrib-clean --save-dev
```
```javascript
grunt.loadNpmTasks('grunt-contrib-nodeunit');

clean: {
      target: ['dist', 'lib']
    }

grunt.loadNpmTasks('grunt-contrib-clean');
grunt.registerTask('reboot', ['clean', 'default']);
```
