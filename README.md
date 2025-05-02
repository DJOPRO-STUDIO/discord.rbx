# discord.rbx
![discord rbx](https://github.com/user-attachments/assets/c92da291-60d5-426b-bd57-432749c124e5)
- **discord.rbx** is a ModuleScript designed for Roblox games to simplify integration with the Discord API, making it easier for developers to connect their experiences with Discord features.

## Requirements :
- **discord.rbx** uses HTTPServices on your game so you need to enable it on the game settings from Roblox Studio. If you don't know how , here is the steps to do it:
1. First, open Roblox Studio and enter to your game.
2. After the game editor loads, On the top, click on Home > Settings > Security
3. Finally , Enable the HTTPService by clicking on the switch.

## Fonctionalities :
- Send Normal Messages by Webhook
- Send Embeds by Webhook
- Extract Image Link from the Roblox Image ID 

## Usage :
> [!NOTE]
> **discord.rbx** can work only with server-side scripts because of the limitation on the HTTPService

- Before we start our code with **discord.rbx** let's require the ModuleScript first !
```lua
local discord_rbx = require(85961583641003)
```
- Now, as we know, **discord.rbx** have some essential parts that you can use them on your code, to simplify, let's put them on a variables:
```lua
local Discord = discord_rbx.Discord
local Webhook = discord_rbx.Webhook
local Embed = discord_rbx.Embed
```
- After everything been initialized, let's send a message with a webhook on Discord:
```lua
local Mywebhook = Webhook.new("WEBHOOK_URL")
Mywebhook:SendMessage("Hi!, this is a message from My Roblox Game!")
```
- Also, you can send a link of an image by doing:
```lua
local Mywebhook = Webhook.new("WEBHOOK_URL")
Mywebhook:SendMessage("IMAGE_LINK")
```
- You can use the Roblox Image ID to send the link of that image by doing :
```lua
local Mywebhook = Webhook.new("WEBHOOK_URL")
local link_image = Discord.image.from_robloxID(91060381650567)
Mywebhook:SendMessage(link_image)
```
> [!NOTE]
> The `Discord.image.from_robloxID()` uses a proxy to work, so if it doesn't, you can get the current proxy or set a new one by doing:
> ```lua
> -- GET AND PRINT THE CURRENT PROXY --
> local curent_proxy = Discord.get_image_proxy()
> print(current_proxy)
>
> -- SET A PROXY --
> Discord.set_image_proxy("PROXY_LINK")
> ```

- Now let's send a Custom Embed:
```lua
local MyEmbed = Embed.new("My Title","My Description",Discord.color.yellow())
MyEmbed:addField("Name Field","Description",true) -- last argument is for inline statement
MyEmbed:addField("Name Field 1","Description 1",false) -- last argument is for inline statement
MyEmbed:addThumbnails("URL_IMAGE")
MyEmbed:addImage("URL_IMAGE")
MyEmbed:addFooter("Text Footer")

local Mywebhook = Webhook.new("WEBHOOK_URL")
Mywebhook:SendMessage("",MyEmbed)
```

> [!NOTE]
> There are several colors that are available:
> ```lua
> Discord.color.green()
> Discord.color.red()
> Discord.color.blue()
> Discord.color.yellow()
> Discord.color.cyan()
> Discord.color.pink()
> Discord.color.white()
> Discord.color.black()
> ```
>
> But If you didn't find the color that you need to, Just use RGB instead:
> ```lua
> Discord.color.from_rgb(255,255,255) -- White
> ```
