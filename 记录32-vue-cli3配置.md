注意  
vue-cli3取消了初始配置build文件夹  
现在配置需要在根目录下创建vue.config.js文件进行配置  
官网配置页面https://cli.vuejs.org/zh/config/  
语法格式为  
```
module.exports = {
    // 选项...
}
```
默认插件  
在使用cli创建时,以下选项选择In package.json后会将一些插件(Babel, PostCSS, ESLint等)配置选项放在package.json内  
默认是在分别单独的文件内进行配置  
Where do you prefer placing config for Babel, PostCSS, ESLint, etc.? In package.json  
  
  
  
重要指令  
`1.npm run lint --fix`  
`2.npm run serve`  
  
  
重要配置选项  
      
配置入口  
https://cli.vuejs.org/zh/config/#pages  
默认的入口为src/main.js  
在运行多页面任务时需要修改这里  
  
  
devServer  
代理的设置在这里  
https://cli.vuejs.org/zh/config/#devserver  
支持webpack的选项  
内容较多,参考https://webpack.js.org/configuration/dev-server/  
中文的webpack的devserve配置说明https://www.webpackjs.com/configuration/dev-server/  
这里待学习webpack,内容很多,留坑  
  
主要是  
host与port  
在局域网内测试时需要修改此处(例如手机测试)  
https://webpack.js.org/configuration/dev-server/#devserverhost  
```
//vue.config.js文件
    module.exports = {
        //...
        devServer: {
            host: '0.0.0.0',
            port: 8000
        }
    };
```
  
配置教程  
https://segmentfault.com/a/1190000016101954  
https://juejin.im/post/5bd02f98e51d457a944b634f  
  
  
  
可参考的模板  
```
module.exports = {
  baseUrl: process.env.NODE_ENV === 'production'
    ? '//your_url'
    : '/',

  outputDir: 'dist',

  assetsDir: 'static',

  filenameHashing: true,

  // When building in multi-pages mode, the webpack config will contain different plugins
  // (there will be multiple instances of html-webpack-plugin and preload-webpack-plugin).
  // Make sure to run vue inspect if you are trying to modify the options for those plugins.
  pages: {
    index: {
      // entry for the pages
      entry: 'src/pages/index/index.js',
      // the source template
      template: 'src/pages/index/index.html',
      // output as dist/index.html
      filename: 'index.html',
      // when using title option,
      // template title tag needs to be <title><%= htmlWebpackPlugin.options.title %></title>
      title: '首页',
      // chunks to include on this pages, by default includes
      // extracted common chunks and vendor chunks.
      chunks: ['chunk-vendors', 'chunk-common', 'index']
    }
    // when using the entry-only string format,
    // template is inferred to be `public/subpage.html`
    // and falls back to `public/index.html` if not found.
    // Output filename is inferred to be `subpage.html`.
    // subpage: ''
  },

  // eslint-loader 是否在保存的时候检查
  lintOnSave: true,

  // 是否使用包含运行时编译器的Vue核心的构建
  runtimeCompiler: false,

  // 默认情况下 babel-loader 忽略其中的所有文件 node_modules
  transpileDependencies: [],

  // 生产环境 sourceMap
  productionSourceMap: false,

  // cors 相关 https://jakearchibald.com/2017/es-modules-in-browsers/#always-cors
  // corsUseCredentials: false,
  // webpack 配置，键值对象时会合并配置，为方法时会改写配置
  // https://cli.vuejs.org/guide/webpack.html#simple-configuration
  configureWebpack: (config) => {
  },

  // webpack 链接 API，用于生成和修改 webapck 配置
  // https://github.com/mozilla-neutrino/webpack-chain
  chainWebpack: (config) => {
    // 因为是多页面，所以取消 chunks，每个页面只对应一个单独的 JS / CSS
    config.optimization
      .splitChunks({
        cacheGroups: {}
      });

    // 'src/lib' 目录下为外部库文件，不参与 eslint 检测
    config.module
      .rule('eslint')
      .exclude
      .add('/Users/maybexia/Downloads/FE/community_built-in/src/lib')
      .end()
  },

  // 配置高于chainWebpack中关于 css loader 的配置
  css: {
    // 是否开启支持 foo.module.css 样式
    modules: false,

    // 是否使用 css 分离插件 ExtractTextPlugin，采用独立样式文件载入，不采用 <style> 方式内联至 html 文件中
    extract: true,

    // 是否构建样式地图，false 将提高构建速度
    sourceMap: false,

    // css预设器配置项
    loaderOptions: {
      css: {
        // options here will be passed to css-loader
      },

      postcss: {
        // options here will be passed to postcss-loader
      }
    }
  },

  // All options for webpack-dev-server are supported
  // https://webpack.js.org/configuration/dev-server/
  devServer: {
    open: true,

    host: '127.0.0.1',

    port: 3000,

    https: false,

    hotOnly: false,

    proxy: null,

    before: app => {
    }
  },
  // 构建时开启多进程处理 babel 编译
  parallel: require('os').cpus().length > 1,

  // https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-pwa
  pwa: {},

  // 第三方插件配置
  pluginOptions: {}
};
```
