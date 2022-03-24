## lerna
- lerna boostrap 自动解决packages之间的依赖关系，对于packages内部的依赖会直接采用symlink的方式关联
- lerna publish 依赖git检测文件改动，自动发布，管理版本号
- lerna create 创建一个 lerna 管理的package包
- lerna clean 删除所有包下面的node_modules目录，也可以删除指定包下面的node_modules