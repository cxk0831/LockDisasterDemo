### 前言

此 DEMO 用于复现没有 lock 导致的灾难现场

### 警告

此项目使用 yarn 复现，请勿使用 npm 操作

### 操作步骤

1. 打开工作空间（LockDisasterDemo）执行 yarn 引入依赖

   ```shell
   # 当前目录 ./
   $ yarn
   ```

2. 执行以下命令启动 verdaccio 

    ```shell
   # 当前目录 ./
   # 此命令已集成到当前目录下package.json的脚本中
   # 注意：请不要在命令行，除非你彻底理解了此脚本的含义
   $ xl_close_port -p 3251 && verdaccio -l 3251 -c ./config/config.yaml
    ```

3. 打开 libs 中的 project 并在当前目录打开命令行，执行 yarn 引入依赖

    ```shell
   # 当前目录 ./libs/project
   $ yarn
    ```

4. 运行 ./libs/project 目录下的 index.js

   ```shell
   # 当前目录 ./libs/project
   # 执行下面命令你将看到报错
   $ node index.js
   ```

5. 使用 ./libs/project/yarn.lock.txt 中的内容把 ./libs/project/yarn.lock 中的内容全部替换

   *yarn.lock.txt 中存放的是老版本的 lock 内容，可以保证 project 项目正常运行* 

6. 删除 ./libs/project/node_modules，重新执行 yarn 引入依赖

   ```shell
   # 当前目录 ./libs/project
   $ yarn
   ```

7. 运行 ./libs/project 目录下的 index.js

   ```shell
   # 当前目录 ./libs/project
   # 执行下面命令你将看到“你好世界”的输出
   $ node index.js
   ```

   
