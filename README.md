# my-react-native

Getting Started 
Requirements 
  1、OS X - This guide assumes OS X which is needed for iOS development.
  2、Homebrew is the recommended way to install Watchman and Flow.
  3、Install Node.js 4.0 or newer.
    Install nvm with its setup instructions here. Then run nvm install node && nvm alias default node, which installs the latest version of Node.js and sets up your terminal so you can run it by typing node. With nvm you can install multiple versions of Node.js and easily switch between them.
  4、brew install watchman. We recommend installing watchman, otherwise you might hit a node file watching bug.
  5、brew install flow, if you want to use flow.
We recommend periodically running brew update && brew upgrade to keep your programs up-to-date.


有个坑，因为React Native升级了babel6，babel6对babelrc文件的解析有变更，而其他第三方组件还没有跟上这个变化。
所以项目建立后报Error while persisting cache: TransformError。
解决这个问题，需要在package.json中添加如下代码
"scripts": {
  "start": "node node_modules/react-native/local-cli/cli.js start",
  "clean:babelrc": "find ./node_modules -name react-packager -prune -o -name '.babelrc' -print | xargs rm -f",
  "postinstall": "npm run clean:babelrc"
}
然后重新运行命令：npm install