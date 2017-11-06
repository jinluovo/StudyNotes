# Git 操作：
1. 创建仓库：
  + 新建仓库按钮：

    ![1](./Picture/Git-Study/1.png)
  + 创建页面：

    ![2](./Picture/Git-Study/2.png)
    + Repository name：仓库名称
    + Description：设置仓库的说明（非必须）
    + public/private：仓库内容是否公开
    + initialize this Repository with a README：自动初始化仓库并设置README文件
    + Add.gitignore：该仓库要使用的主要语言及框架（非必须）
    + Add a license：选择要添加的许可协议文件（非必须）
2. 连接仓库：
  >下面URL即为刚创建的仓库页面：    
    git@github.com:jinlu1106/DataStructure-C.git

  + README.md在初始化时已经生成。其内容主要包含仓库所包含的软件的概要、使用流程、许可协议等信息。
  ![3](./Picture/Git-Study/3.png)
3. Git简单指令：
  + clone已有仓库：
    + 复制仓库路径
    ![仓库路径](./Picture/Git-Study/4.png)
    + 输入git命令：
    ![5](./Picture/Git-Study/5.png)
  + 初始化仓库：`git init`（已经自动初始化完成）执行该命令的目录下会生成.git目录，这个.git目录里存储着管理当前目录内容所需的仓库数据
  + 查看仓库的当前状态：`git status`进入该仓库之后执行该命令
  ![6](./Picture/Git-Study/7.png)
  `Untracked files`即为可提交但尚未提交的内容
  + 向暂存区中添加文件：git add .（提交所有文件）
  ![7](./Picture/Git-Study/11.png)
  ![11](./Picture/Git-Study/12.png)
    + 撤销add命令添加到暂存区的文件

      `git reset head <文件名>` 撤销对某个文件的add命令  

      `git reset head .` 撤销所有文件的add命令
      ![8](./Picture/Git-Study/8.png)

    + 解决换行符警告问题
      + windows中的换行符为 CRLF，而在Linux下的换行符为LF,改动文件时引入了 LF,提交改动时，git 会警告你哪些文件不是纯 CRLF 文件，但 git 不会擅自修改工作区的那些文件，而是对暂存区（我们对工作区的改动）进行修改。也因此，当我们进行 git add 的操作时，只要 git 发现改动的内容里有 LF 换行符，就会出现下面这个警告
      ![9](./Picture/Git-Study/9.png)
      解决这个问题可以在git命令行中输入如下指令禁止自动转换
      ![10](./Picture/Git-Study/10.png)
  + 保存仓库历史记录：`git commit`
  ![12](./Picture/Git-Study/13.png)
   -m后的"First"称作提交信息，是对该提交的概述，如果想要记述的更加详细，则不加-m，直接执行git commit命令，执行后编辑器就会启动。
   ![13](./Picture/Git-Study/14.png)
  + 查看提交日志：`git log`
  ![14](./Picture/Git-Study/15.png)
  commit栏旁边的是指向这个提交的哈希值

          git log --pretty=short  #只显示提交信息的第一行
          git log <目录名>  #只显示该目录下的日志
          git log --   #显示提交所带来的改动
          git log -p <文件名>   #显示该文件的提交日志
  + push到服务器端的仓库：
  ![15](./Picture/Git-Study/16.png)
