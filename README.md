# tyut_health

## 说明

本项目只为了方便自己使用，仅供学习参考，请勿传播！！！！！

### 1.本地使用方法

1. 安装git和python3

2. 克隆仓库

   ```
   git clone https://github.com/LH428/tyut_health.git && cd tyut_health
   ```

3. 安装依赖

   ```
   pip3 install pip -U
   pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
   pip3 install -r requirements.txt
   ```

4. 复制配置文件模板

   ```
   cp ./config.sample.json ./config.json
   ```

   配置文件示例

   ```
   {    
       "info": [	  
           {
               "nickname": "//通知的绰号",
               "id": "学号2019******",
               "pwd":"密码******",
               "campus":"迎西"//明向or迎西or虎峪
               "iscampus":true,//是否在校，默认为true在校,不在校请填false,并填写submitdata
               "submitdata":"submitdata=1%242%7D216%241"//不在校需要填写的submitdata，由抓包获取
           },
           {
               "nickname": "//通知的绰号",
               "id": "学号2019******",
               "pwd":"密码******",
               "campus":"迎西"//明向or迎西or虎峪
               "iscampus":true,//是否在校，默认为true在校,不在校请填false,并填写submitdata
               "submitdata":"submitdata=1%242%7D216%241"//不在校需要填写的submitdata，由抓包获取
           }
       ],
       "send":[
           {
               "BARK": "", # bark服务,自行搜索; secrets可填;                
               "SCKEY": "", # Server酱的SCKEY; secrets可填             
               "TG_BOT_TOKEN": "", # tg机器人的TG_BOT_TOKEN; secrets可填1407203283:AAG9rt-6RDaaX0HBLZQq0laNOh898iFYaRQ       
               "TG_USER_ID": "",  # tg机器人的TG_USER_ID; secrets可填 1434078534          
               "TG_API_HOST":"", # tg 代理api           
               "TG_PROXY_IP": "", # tg机器人的TG_PROXY_IP; secrets可填          
               "TG_PROXY_PORT": "", # tg机器人的TG_PROXY_PORT; secrets可填        
               "DD_BOT_ACCESS_TOKEN": "",# 钉钉机器人的DD_BOT_ACCESS_TOKEN; secrets可填  
               "DD_BOT_SECRET": "", # 钉钉机器人的DD_BOT_SECRET; secrets可填
               "QQ_SKEY": "", # qq机器人的QQ_SKEY; secrets可填              
               "QQ_MODE": "", # qq机器人的QQ_MODE; secrets可填               
               "QYWX_AM": "", # 企业微信              
               "PUSH_PLUS_TOKEN": ""# 微信推送Plus+        
           } 
       ],
       "sendnotify":[
           {
               "Flag":true//默认为true，不需要推送改为false
           }
       ]
   }
   ```

5. 添加定时任务

   ```
   5 12,13 * * * cd /scriptPath/ && python3 main.py
   ```

### 2.青龙面板使用方法:

1. 安装青龙面板 [ https://github.com/whyour/qinglong ]（建议使用docker）

   ```shell
   docker run -dit \
     -v $PWD/ql/data:/ql/data \
     -p 5700:5700 \
     --name qinglong \
     --hostname qinglong \
     --restart unless-stopped \
     whyour/qinglong:2.10.13
   ```

2. 网页打开青龙面板 ip + 端口号5700 （eg:127.0.0.1:5700）,更改文件

   ```shell
   RepoFileExtensions="js py json sh"
   ```

   ![image-20221121172604210](https://github.com/LH428/tyut_health/blob/main/figure/1.png)

3. 进入docker 容器，拉库

   ```shell
   # 进入容器
   docker exec -it qinglong bash
   # 拉库
   ql repo https://github.com/LH428/tyut_health.git "main" "" "config|msg|sendNotify" "main"
   ```

4. 在脚本管理--->新建文件（文件名config.json）、父目录（LH428_tyut_health_main）

  ![image-20221121172854143]https://github.com/LH428/tyut_health/blob/main/figure/2.png)

5. 把config.sample.json文件内容复制到config.json中，并按本地方法进行配置

  ![image-20221121173306865](https://github.com/LH428/tyut_health/blob/main/figure/3.png)

6. 安装依赖 bs4

   ![image-20221121173719395](https://github.com/LH428/tyut_health/blob/main/figure/4.png)

7. enjoy!!!!![image-20221121174511920](https://github.com/LH428/tyut_health/blob/main/figure/5.png)

### 参考：

1. https://github.com/okihane/TYUT-HealthDK.git
2. https://github.com/curtinlv/JD-Script.git
