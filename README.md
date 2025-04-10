<!-- Existing README.md content up to "Poll Message" is unchanged -->

### Poll Message
```ts
await sock.sendMessage(
    jid,
    {
        poll: {
            name: 'My Poll',
            values: ['Option 1', 'Option 2', ...],
            selectableCount: 1,
            toAnnouncementGroup: false // or true
        }
    }
)
```

### Buttons Message
```ts
// send a buttons message!
sock.sendMessage(jid, {
     text: "Hello World !",
     footer: "Eypz - 2025",
     buttons: [
     {
       buttonId: `🚀`, 
       buttonText: {
         displayText: '🗿'
       },
       type: 1 
     }
     ],
     headerType: 1,
     viewOnce: true
 }, { quoted: null })
```

### Buttons Flow
```ts
sock.sendMessage(jid, {
  text: "Hello World !", 
  footer: "© Eypz",
  buttons: [
  {
    buttonId: '.tes',
    buttonText: {
      displayText: 'TESTING BOT'
    },
    type: 1,
  },
  {
    buttonId: ' ',
    buttonText: {
      displayText: 'PRIVATE SCRIPT'
    },
    type: 1,
  },
  {
    buttonId: 'action',
    buttonText: {
      displayText: 'ini pesan interactiveMeta'
    },
    type: 4,
    nativeFlowInfo: {
      name: 'single_select',
      paramsJson: JSON.stringify({
        title: 'message',
        sections: [
          {
            title: 'Eypz - 2025',
            highlight_label: '😜',
            rows: [
              {
                header: 'HEADER',
                title: 'TITLE',
                description: 'DESCRIPTION',
                id: 'YOUR ID',
              },
              {
                header: 'HEADER',
                title: 'TITLE',
                description: 'DESCRIPTION',
                id: 'YOUR ID',
              },
            ],
          },
        ],
      }),
    },
  },
  ],
  headerType: 1,
  viewOnce: true
}, { quoted: m });
```

### Interactive Message
```ts
let msg = generateWAMessageFromContent(m.chat, {
 viewOnceMessage: {
   message: {
       "messageContextInfo": {
         "deviceListMetadata": {},
         "deviceListMetadataVersion": 2
       },
       interactiveMessage: proto.Message.InteractiveMessage.create({
         body: proto.Message.InteractiveMessage.Body.create({
           text: "Eypz"
         }),
         footer: proto.Message.InteractiveMessage.Footer.create({
           text: "Bot"
         }),
         header: proto.Message.InteractiveMessage.Header.create({
           title: "Igna",
           subtitle: "test",
           hasMediaAttachment: false
         }),
         nativeFlowMessage: proto.Message.InteractiveMessage.NativeFlowMessage.create({
           buttons: [
             {
               "name": "single_select",
               "buttonParamsJson": "{"title":"title","sections":[{".menu":".play dj webito","highlight_label":"label","rows":[{"header":"header","title":"title","description":"description","id":"id"},{"header":"header","title":"title","description":"description","id":"id"}]}]}"
             },
             {
               "name": "cta_reply",
               "buttonParamsJson": "{"display_text":"quick_reply","id":"message"}"
             },
             {
                "name": "cta_url",
                "buttonParamsJson": "{"display_text":"url","url":"https://www.google.com","merchant_url":"https://www.google.com"}"
             },
             {
                "name": "cta_call",
                "buttonParamsJson": "{"display_text":"call","id":"message"}"
             },
             {
                "name": "cta_copy",
                "buttonParamsJson": "{"display_text":"copy","id":"123456789","copy_code":"message"}"
             },
             {
                "name": "cta_reminder",
                "buttonParamsJson": "{"display_text":"Recordatorio","id":"message"}"
             },
             {
                "name": "cta_cancel_reminder",
                "buttonParamsJson": "{"display_text":"cta_cancel_reminder","id":"message"}"
             },
             {
                "name": "address_message",
                "buttonParamsJson": "{"display_text":"address_message","id":"message"}"
             },
             {
                "name": "send_location",
                "buttonParamsJson": ""
             }
          ],
         })
       })
   }
 }
}, {})

return sock.relayMessage(msg.key.remoteJid, msg.message, { messageId: msg.key.id })
```
