### lerna基本使用
- lerna默认使用的是集中版本，所有的package共用一个version，如果需要packages下
  不同的模块使用不同的版本号，需要配置 Independent 模式。在`lerna.json`中增加属性配置：
  `version: independent`

- `package.json` 中有一点需要注意，他的private必须设置为true，因为 `mono-repo` 本身的这个
   `Git`仓库并不是一个项目，他是多个项目，所以一般不进行直接发布，发布的应该是 `packages/` 下面的各个子项目。

- `lerna bootstrop --hoist` 会将 packages 目录下的公共模块包抽离到最顶层，但是这种方式会有一个问
   题，不同版本号只会保留使用最多的版本，这种配置不太好，当项目中有些功能需要依赖老版本时，就会出现问题。