 Unofficial Docker image for [EH Forwarder Bot](https://github.com/blueset/ehForwarderBot). Maintained by [Roy Xiang](http://github.com/RoyXiang). Included all officialy maintained channels.

你是不是在使用微信时，有过这样的尴尬：1，你不想把的私人生活和工作都用同一个微信来聊；2，临时撩骚个人，又不想暴露私人信息；3，总有些时候，别人要临时加一下你的微信，弄个东西，但从此后这个要就再也不联系。

这就是为什么我要用微信机器人的原因，一个备用小号，所有不熟悉的人都只能通过微信的扫码或者朋友分享名片来添加，而且设置了不需要验证。这样别人就一直可以跟你聊天，但却是你的陌生人，最大化保护你的隐私又不得罪人。 要实现这个就要用到 Telegram 微信机器人，从而在一部手机上可以实现多个微信同时聊天（那些说微信多开的，可以闪开了... ... ）。我是用安桌配合 island ( google play 下载）。

那么要分几步来完成呢，答案是三步：

这是 Fork 自 Royx 的一个 Telegram to 微信 Docker，以下是食用指南：

# 建立自己的 config.py

我是在 VPS 上自己的 `~` 目录下新建了一个**wechat** 目录来存放配置文件具体过程就是：

```
cd
mkdir -p ~/docker/wechat
curl -s https://raw.githubusercontent.com/blueset/ehForwarderBot/master/config.sample.py \
           -o ~/docker/wechat/config.py
           
touch ~/docker/wechat/tgdata.db

```

接下来就是修改你自己的 **config.py** 内容了，这个我帮不了你，等有空我再写写各参数的用途吧
# 启动你的微信机器人

```
docker run -d --restart=on-failure:15 \
  -v ~/docker/wechat:/mnt --name=wechat \
           bao3/docker-wechat:latest

```


# 扫码登录

```
$ docker logs -f wechat
```
# 备注
1. 如果你像我一样，只是为了应付临时的客户而弄了微信小号，那么你应该**设备你的小号不需要确认即可加好友，但不可以通过手机号添加**，这样可以减少骚扰。另外，可以像我一样，限制为只可以扫码而不允许通过群来添加你为好友。
2. 当你 Telegram 能接收微信后，请确定你创建一个 Group （需要你先拉一个实际的联系人，建好后再踢走），然后在邀请你的 Teleggram 机器人进入 Group 然后直接打 `/linke` ，把好友或者群给拉进来。这样你就可以在这个 Group里直接回复你的好友。
3. 由于我是小号微信，所以人也不多，也没加群，但如果你的人比较多，就一定要把他们放到 Group 后设置为静音，否则会被烦死。

[Official Documentation](https://ehforwarderbot.readthedocs.io)
