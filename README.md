import re
import itchat, time
from itchat.content import *

@itchat.msg_register([SHARING])
def text_reply(msg):
	if msg.url == 'www.youku.com':
		msg.user.send('请点击链接观看《'+ msg.FileName +'》-> http://mrjpy.com?url=https://v.youku.com/v_show/id_'+re.findall(r'&videoId=(.+?)]]></pagepath>', msg.content)[0]+".html")
	else:
		msg.user.send('请点击链接观看《'+ msg.FileName +'》-> http://mrjpy.com?url='+msg.url)

@itchat.msg_register([PICTURE, RECORDING, ATTACHMENT, VIDEO,TEXT, MAP, CARD, NOTE,FRIENDS])
def text_reply(msg):
    msg.user.send('请将各大视频APP中想看的VIP视频，点击分享后发给我，有惊喜哦！')

itchat.auto_login(enableCmdQR=2)
itchat.run(blockThread=False)
