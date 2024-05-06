# Performance guide for Fika & Swag + Donuts
In this guide I will explain how I designed and put into use the new features of ``Performance | Max Bots``
The idea is that in SPT, bots are by far the thing that costs the most CPU performance, and as such we directly target that. If left to it's own devices, SPT and spawn mods will typically flood the game with a crazy amount of bots. Instead what I aimed to achieve with this is that we will despawn bots that are far away, to make the bots that exist be closer to the player. This gives us more performance while not making the raid feel like a ghost town. 

# Settings Explanation
*Short explanation of the settings under Performance | Max bots*

``Enforced Spawn Limits`` By iteslf, this setting will prevent ANY spawn above the limit set for the map you're currently on. Except special bots like bosses, followers, etc.

``Despawn Furthest`` This setting needs to have ``Enforced Spawn Limits`` enabled to work. What it does is instead of outright just blocking spawns, is that it will attempt to de-spawn the bot furthest away from any player. It will never despawn anything but PMCs or SCAVs. Thus leaving bosses, followers, rouges, etc alone.

``Despawn Minimum Distance`` Bots inside this distance will not be despawned. 

``Max Bots <MAP>`` This is the maximum bots that will be allowed to exist on a map at any time. This is a hard limit and will never be exceeded. (except by specials) This setting will have the highest impact on your framerate. 

# How to use for best effect 
*If you get even better results let me know, this isnt the be all end all configuration*

The goal is to have interesting raids, that feel alive while preserving as much fps as possible. To achieve this, we need a mod that spawns bots around you. (As of time of writing, the only mod that I know does this is Donuts + SWAG, but these settings would technically work with any mod that uses the correct method of dynamically spawning bots.)

## The Premise: Max Bots, ScenarioConfig, and SWAG Config.
* In Fika you have ``Performance | Max Bots`` I will refer to this as Fika Max Bots. 
* ``/BepInEx/Plugins/dvize.Donuts/ScenarioConfig.json`` I will refer to the values here as PMC Limit, and Scav Limit. Make sure their combined count within the limit set in the MaxBotCap below.
* ``/user/mods/SWAG/config/config.json``. At the bottom there is ``MaxBotCap`` and a ``NightMaxBotCap`` I will refer to this as SWAG Cap.

### You
You want as good framerate as possible. I don't think anyone will argue that higher fps isn't better. But, we need to weigh this against the map and donuts. We could set the max bots to 1, but that would not make for a good raid. Even if the fps would be incredible. So we need to balance. 

### Donuts
Donuts need a bit of swing room to work best, and so we need to provide this. I personally like to enable the feature (in F12 donuts menu) ``Hot Spot Ignore Hard Cap`` and I have set MY numbers to work with this.

## Example
*I balance my spawns for the person in our group with the worst PC, so everyone has a good time*

I will use Lighthouse for this example.

First we have the sniper island boss ``zryachiy`` and his two followers. Personally, I think the island is so fortified, and not intended to get to anymore before you have quests there that I disable his spawn completely in ``bossConfig`` That's 3 bots less that wont steal my performance. I would re-enable him if I ever needed to do quests out there. 

This map has a lot of specials so we need to keep that in mind when setting the caps.

I have concluded through testing that my PC can handle about 18 bots without the performance dropping much.

Now this map is already fairly performance intensive due to how big and badly optimized it is. So I would like to have decent FPS. So I don't want there to be more than 18 bots spawned on the map. So I set the Fika Max Bots to 18. Then I want to leave donuts some room, so I set the SWAG Cap for lighthouse to 16. That leaves 2 bot slots for donuts to use (it will also still despawn further bots, so 2 goes further than you might think)

This leaves us with 16 bots to play around with, minus whatever specials spawn. If the raids feel a bit empty, it might be that a your cap is low, or a lot of specials spawned this raid. What you can do if you have a fairly low cap like my example of 18, is reduce the upper limit of rouges just a tad to let the rest of the map get a bit more action.

## MY Settings
*My settings shouldn't be seen as some be all end all.*

Config files can be downloaded here: [Config Releases](https://github.com/DeadLeavez/MISC/releases/tag/Config)

They DO NOT contain configs for the F12 settings. Those still need to be set up manually.

### Config files
For swag, my settings look like this. The settings for night time is the same.

 ``/user/mods/SWAG/config/config.json``
```json
"MaxBotCap": {
    "factory": 13,
    "customs": 16,
    "woods": 16,
    "shoreline": 16,
    "lighthouse": 16,
    "reserve": 16,
    "interchange": 16,
    "laboratory": 16,
    "streets": 14,
    "groundzero": 16
}
```
For donuts I have these settings on all 3 live-like. I recommend similiar settings on the presets you use.

 ``/BepInEx/Plugins/dvize.Donuts/ScenarioConfig.json``
```json
"PMCBotLimitPresets": {
    "FactoryBotLimit": 5,
    "InterchangeBotLimit": 8,
    "LaboratoryBotLimit": 8,
    "LighthouseBotLimit": 4,
    "ReserveBotLimit": 6,
    "ShorelineBotLimit": 8,
    "WoodsBotLimit": 8,
    "CustomsBotLimit": 7,
    "TarkovStreetsBotLimit": 4,
    "GroundZeroBotLimit": 8
},
"SCAVBotLimitPresets": {
    "FactoryBotLimit": 5,
    "InterchangeBotLimit": 8,
    "LaboratoryBotLimit": 9,
    "LighthouseBotLimit": 7,
    "ReserveBotLimit": 7,
    "ShorelineBotLimit": 7,
    "WoodsBotLimit": 9,
    "CustomsBotLimit": 8,
    "TarkovStreetsBotLimit": 5,
    "GroundZeroBotLimit": 8
}
```
### F12 settings
I will only list the important settings.

**Fika**

```
Enforced Spawn Limits = true
Despawn Furthest = true
Despawn Minimum Distance = 200

Max Bots Factory = 13
Max Bots Customs = 21
Max Bots Interchange = 19
Max Bots Reserve = 19
Max Bots Woods = 22
Max Bots Shoreline = 18
Max Bots Streets = 18
Max Bots Ground Zero = 18
Max Bots Labs = 19
Max Bots Lighthouse = 18
```

**Donuts**

```
Despawn PMCs = false
Despawn SCAVs = false
PMC Hot Spot Ignore Hard Cap = true
SCAV Hot Spot Ignore Hard Cap = true
```

**Minimum Distances**
Are highly subjective, but I recommend turning both on or you get mayhem. As for how far. The default ones are pretty good. But if the raid is too rowdy, you might want to increase it. And if a raid feels empty, you want to reduce the distances. For completeness, I will still provide mine.

```
Use Global Min Distance From Player = true
Customs = 50
Factory = 10
Ground Zero = 50
Interchange = 50
Laboratory = 50
Lighthouse = 75
Reserve = 25
Shoreline = 35
Streets = 50
Woods = 100

Use Global Min Distance From Other Bots = true
Customs = 35
Factory = 15
Ground Zero = 65
Interchange = 50
Laboratory = 40
Lighthouse = 60
Reserve = 35
Shoreline = 45
Streets = 55
Woods = 75
```
