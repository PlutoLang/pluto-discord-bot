# pluto-discord-bot

A library enabling you to write Discord bots in Pluto.

## Getting Started

**deps.pluto**
```elixir
;(require"http".request"//use.agnostic.pm"|>load)()

git "https://github.com/PlutoLang/pluto-websocket"
    from "websocket.pluto" to "lib/websocket.pluto"

git "https://github.com/PlutoLang/pluto-discord-bot"
    from "discord-bot.pluto" to "lib/discord-bot.pluto"
```

**index.pluto**
```lua
local DISCORD_TOKEN = "YOUR_TOKEN_HERE"

package.path ..= package.config[3].."lib"..package.config[1].."?.pluto"

local bot = new (require"discord-bot") (DISCORD_TOKEN)

bot:onMessage(function(msg)
    if msg.author.bot then
        return
    end
    local is_dm = not msg.guild_id
    if is_dm then
        msg.channel:sendMessage("Thanks for the DM!")
    elseif msg:mentionsMe() then
        msg:reply("Thanks for the ping!")
    end
end)

bot:run()
```

To learn more about the API, have a look at [the docs](DOCS.md).
