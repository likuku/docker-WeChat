Unofficial Docker image for [EH Forwarder Bot](https://github.com/blueset/ehForwarderBot). Maintained by [Roy Xiang](http://github.com/RoyXiang). Included all officialy maintained channels.

这是 Fork 自 Royx 的一个 Telegram to 微信 Docker，以下是信用指南：

#建立自己的 config.py

我是在 VPS 上自己的 `~` 目录下新建了一个**efb** 目录来存放配置文件具体过程就是：

```
cd
mkdir -p ~/docker/efb
curl -s https://raw.githubusercontent.com/blueset/ehForwarderBot/master/config.sample.py -o ~/efb/config.py
touch tgdata.db

```

接下来就是修改你自己的 **config.py** 内容了，这个我帮不了你，等有空我再写写各参数的用途吧
#启动你的微信机器人

```
docker run -d --restart=on-failure:15 -v ~/docker/efb:/mnt --name=wechat bao3/docker-efb:latest
```


#扫码登录

```
$ docker logs -f wechat
```



[Official Documentation](https://ehforwarderbot.readthedocs.io)
