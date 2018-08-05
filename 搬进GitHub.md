## 搬进GitHub ##
什么是GitHub？GitHub是一个全球最大的开源项目托管平台，也是一款非常高效的版本控制工具

### 1. 相关专业术语 ###
- repository：仓库，包含了项目的各个历史版本	   
- commit：版本，做一个版本   
- branch：分支
- Pull Request：拉取请求，用来对版本进行讨论
- Issues：事物卡片

### 2. GitHub客户端的使用 ###
- 方便与本地编译器交互   
- 客户端中存在Changes和History，修改的内容需在Changes中commit，才能保存到History中
- History中包含信息：谁在什么时间做了什么，为什么要这么做
- 做错的版本，可右击版本使用revert this commit抵消（此行为会触发一个新的history）
- 如果做错了版本二三四，想回到版本一，可右击使用Roll back to this commit，回滚到版本一（新版GitHub windows似乎没有这个功能？没有找到）
- 点击publish，可轻松同步至GitHub官网   

### 3. 分支的使用 ###
- 避免新的idea污染master branch
- 在GitHub客户端选中哪个branch，本地编辑器中显示的就是哪个branch
- 若current branch是branch1，则删除不了branch1，需切换current branch才能删除，delete同时删除远端和本地，unpublish只删除远端
- default branch不能删除。若要修改默认分支，需在setting里面修改
- 合并分支：Merge（与本地合并），并积（与远端合并）
- 合并冲突：查看冲突标示符，手动修改冲突内容，再合并

### 4. GitHub协作流程 ###
#### 4.1 GitHub flow ####
- 创建分支
- 添加新版本
- 开启Pull Request（核心）
- 讨论和代码审核
- 合并分支，然后部署

#### 4.2 团队协作流程 ####
- 给队友添加权限：settings → collaborators
- 用Pull Request交流

#### 4.3 开源项目贡献流程 ####
- 将别人的代码fork+clone到本地，进行修改
- 再用Pull Request交流
- 没有Pull Request时，代码主人也能看到你的修改，在graphs → Network中可查看
- Quick Pull Request：直接找到源码，点击编辑，会自动创建一个fork

### 5. GitHub三件套 ###
#### 5.1 GitHub Issues ####
- Assignee，把任务布置给某人去完成
- \#2表示编号为2的issue
- commit的时候注明\#2，可在issue \#2插入代码
- commit的时候注明fix \#2，可关闭issue \#2

#### 5.2 GitHub Pages ####
- 搭建项目主页，分为user or organization site和project site
- 新建gh-pages分支
- 公网域名：[userName].github.io/[projectName]

#### 5.3 GitHub Wiki ####

### 6. 学习资源 ###
[IMOOC-版本控制入门-搬进GitHub](https://www.imooc.com/learn/390)

