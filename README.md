from telethon import TelegramClient, events, sync
from telethon.tl.functions.messages import GetHistoryRequest, GetBotCallbackAnswerRequest
api_id = 876354374:AAGt3P6H3IVkS53ql5jnVi16YqYxayLaemo
api_hash = 'xxxx'
client = TelegramClient('session_name', api_id, api_hash)
client.start()
channel_username='tevana_bot'
channel_entity=client.get_entity(channel_username)
posts = client(GetHistoryRequest(
peer=channel_entity,
limit=1,
offset_date=None,
offset_id=0,
max_id=0,
min_id=0,
add_offset=0,
hash=0
)
)
messageId = posts.messages[0].id
client(GetBotCallbackAnswerRequest(
channel_username,
messageId,
data=posts.messages[0].reply_markup.rows[0].buttons[0].data
))
client.disconnect()
