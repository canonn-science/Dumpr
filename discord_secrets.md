# Discord Secrets

This is simply a json file with a collection of webhooks that the script will send updates to. If you want us to send your discord updates when we upload files then please contact LCU No Fool Like one on the [Canonn Discord](https://canonn.fyi/discord) and we will add your webhooks to our own. 


```json
[
{
    "description": "My Pretend Server",
    "verbose": true,
    "webhook":"https://discord.com/api/webhooks/<id>>/<secretkey>"
},
{
    "description": "Canonn's Private Server",
    "verbose": false,
    "webhook":"https://discord.com/api/webhooks/<id>>/<secretkey>"
}
]
```

The verbose parameter determines how talkative the script will be for that discord server. 

If true it will declare when the job has started and when it has finished
Verbose will additionaly tell you when each file has been uploaded.