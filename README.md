--[[
  ScriptCentral Universal - Versão Otimizada
  
  Este script foi refatorado para melhorar a organização,
  reutilizar código e torná-lo mais fácil de manter.
]]

-- Inicializa a biblioteca de UI
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/ScriptCentral-br/LibraryCentral/refs/heads/main/sc", true))()
local Window = Library:MakeWindow({
    Name = "ScriptCentral Universal",
    SearchBar = "Default",
    HidePremium = false,
    SaveConfig = true,
    ConfigFolder = nil
})

-- Declarações de variáveis comuns
local DISCORD_LINK = "https://discord.gg/BnMfuJ4jDV"
local NOTIFICATION_IMAGE_ID = "rbxassetid://4483345998"
local ICON_DEFAULT = "rbxassetid://108776114629126"
local ICON_SETTINGS = "rbxassetid://85398723149532"
local ICON_DISCORD = "rbxassetid://90685941326593"

-- Função para criar a notificação de link copiado
local function createLinkCopiedNotification()
    OrionLib:MakeNotification({
        Name = "Link Copiado!",
        Content = "O link de convite do Discord foi copiado para sua área de transferência.",
        Image = NOTIFICATION_IMAGE_ID,
        Time = 5
    })
    setclipboard(DISCORD_LINK)
end

-- Função para adicionar botões de script
local function addButton(tab, name, url, notificationMessage)
    tab:AddButton({
        Name = name,
        Callback = function()
            loadstring(game:HttpGet(url, true))()
            if notificationMessage then
                OrionLib:MakeNotification({
                    Name = name,
                    Content = notificationMessage,
                    Image = NOTIFICATION_IMAGE_ID,
                    Time = 5
                })
            end
        end
    })
end

-- CRIAÇÃO DAS ABAS

do
    local discordTab = Window:MakeTab({
        Name = "Discord",
        Icon = ICON_DISCORD,
        PremiumOnly = false
    })

    local discordSection = discordTab:AddSection({ Name = "Link do Discord" })
    discordSection:AddButton({
        Name = "Copiar Link do Discord",
        Callback = createLinkCopiedNotification
    })

    local discordSection2 = discordTab:AddSection({ Name = DISCORD_LINK })
    discordSection2:AddButton({
        Name = DISCORD_LINK,
        Callback = createLinkCopiedNotification
    })
end

do
    local updatesTab = Window:MakeTab({
        Name = "Updates",
        Icon = ICON_SETTINGS,
        PremiumOnly = false
    })

    updatesTab:AddSection({ Name = "Atualizações" })
    updatesTab:AddLabel("Futuras atualizações serão listadas aqui.")
    updatesTab:AddSection({ Name = "Nova Atualização" })
    updatesTab:AddLabel("Múltiplos scripts para PC/Mobile adicionados!")

    local updatesTabDiscordSection = updatesTab:AddSection({ Name = "discord.gg" })
    updatesTab:AddLabel("Tem uma sugestão de script? Entre no Discord!")
    updatesTabDiscordSection:AddButton({
        Name = DISCORD_LINK,
        Callback = createLinkCopiedNotification
    })
end

do
    local settingsTab = Window:MakeTab({
        Name = "Settings",
        Icon = ICON_SETTINGS,
        PremiumOnly = false
    })

    settingsTab:AddSection({ Name = "Seção de Configurações" })
    settingsTab:AddLabel("Otimize seu jogo para melhor FPS")

    settingsTab:AddButton({
        Name = "Ativar Otimizador",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/ScriptCentral-br/Otimizador/refs/heads/main/Otimizador.md"))()
            OrionLib:MakeNotification({
                Name = "Otimizador Ativado",
                Content = "O script otimizador foi executado com sucesso.",
                Image = NOTIFICATION_IMAGE_ID,
                Time = 5
            })
        end
    })
end

do
    local universalAdminTab = Window:MakeTab({
        Name = "Universal Admin",
        Icon = ICON_SETTINGS,
        PremiumOnly = false
    })

    local universalAdminSection = universalAdminTab:AddSection({ Name = "Universal Admin" })
    universalAdminSection:AddButton({
        Name = "Executar Universal Admin",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/GamerScripter/Game-Hub/main/loader"))()
            OrionLib:MakeNotification({
                Name = "Universal Admin",
                Content = "O script foi executado com sucesso!",
                Image = NOTIFICATION_IMAGE_ID,
                Time = 5
            })
        end
    })
end

do
    local FischTab = Window:MakeTab({
        Name = "Fisch",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    local FischSection = FischTab:AddSection({ Name = "Seção Fisch" })

    addButton(FischTab, "Naoki Hub", "https://naokihub.vercel.app")
    addButton(FischTab, "Aussie WIRE", "https://api.luarmor.net/files/v3/loaders/4f5c7bbe546251d81e9d3554b109008f.lua")
    addButton(FischTab, "Speed Hub X", "https://raw.githubusercontent.com/AhmadV99/Speed-Hub-X/main/Speed%20Hub%20X.lua")
    addButton(FischTab, "Forge Hub", "https://raw.githubusercontent.com/Skzuppy/forge-hub/main/loader.lua")
    addButton(FischTab, "Goomba Hub", "https://raw.githubusercontent.com/JustLevel/goombahub/main/fisch.lua")
    addButton(FischTab, "Project Spectrum", "https://raw.githubusercontent.com/xZPUHigh/Project-Spectrum/main/Loader.lua")
    addButton(FischTab, "Rinns Hub", "https://raw.githubusercontent.com/kylosilly/femboyware/refs/heads/main/Fisch.lua")
    addButton(FischTab, "Moon X", "https://api.luarmor.net/files/v3/loaders/cba17b913ee63c7bfdbb9301e2d87c8b.lua")
    addButton(FischTab, "Bonk Hub", "https://bonkhubloader.netlify.app", "Executed")
end

do
    local BloxFruitTab = Window:MakeTab({
        Name = "Blox Fruits",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })
    
    local BloxFruitSection = BloxFruitTab:AddSection({ Name = "Blox Fruits" })

    addButton(BloxFruitTab, "Red Z Hub", "https://raw.githubusercontent.com/realredz/BloxFruits/refs/heads/main/Source.lua")
    addButton(BloxFruitTab, "Blox Fruits V2 (Pc/Mobile)", "https://raw.githubusercontent.com/3345-c-a-t-s-u-s/Kncrypt/refs/heads/main/sources/BloxFruit.lua")
    addButton(BloxFruitTab, "Mama Hub (Pc/Mobile)", "https://raw.githubusercontent.com/MAMAhub1/Mmahub/main/README.md")
    addButton(BloxFruitTab, "Rua hub", "https://raw.githubusercontent.com/daviduts1/rua-hub/main/auto%20bouty")
    addButton(BloxFruitTab, "Speed Hub", "https://raw.githubusercontent.com/AhmadV99/Speed-Hub-X/main/Speed%20Hub%20X.lua")
    addButton(BloxFruitTab, "MTriet Hub", "https://raw.githubusercontent.com/Minhtriettt/Free-Script/main/MTriet-Hub.lua")
    addButton(BloxFruitTab, "Mukuru Hub", "https://auth.quartyz.com/scripts/Loader.lua")
    addButton(BloxFruitTab, "Domadic Hub", "https://raw.githubusercontent.com/Domadicoof/Domadicoof/main/Domadichub/NottoGay/Start.ranscript")
    
    BloxFruitTab:AddButton({
        Name = "W-Azure",
        Callback = function()
            getgenv().Team = "Pirates"
            getgenv().FixCrash = false
            getgenv().FixCrash2 = false
            loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/3b2169cf53bc6104dabe8e19562e5cc2.lua"))()
        end
    })

    addButton(BloxFruitTab, "HoHo Hub (Tem Key)", "https://raw.githubusercontent.com/acsu123/HOHO_H/main/Loading_UI")
end

do
    local NightsInTheForestTab = Window:MakeTab({
        Name = "99 Nights in the Forest",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    NightsInTheForestTab:AddSection({ Name = "99 Nights in the Forest" })

    addButton(NightsInTheForestTab, "Iliankytb", "https://raw.githubusercontent.com/Iliankytb/Iliankytb/main/Best99NightsInTheForest")
    addButton(NightsInTheForestTab, "SpaceHub", "https://raw.githubusercontent.com/ago106/SpaceHub/refs/heads/main/loader.lua")
    addButton(NightsInTheForestTab, "Gad_Forest (Discord)", "https://pastebin.com/raw/gHQGTNYH")
    addButton(NightsInTheForestTab, "KiKiWare", "https://raw.githubusercontent.com/KiKi-Ware/Roblox/refs/heads/main/Key")
    addButton(NightsInTheForestTab, "H4xScripts", "https://raw.githubusercontent.com/H4xScripts/Loader/refs/heads/main/loader.lua")
    addButton(NightsInTheForestTab, "Adibhub1", "https://raw.githubusercontent.com/adibhub1/99-nighit-in-forest/refs/heads/main/99%20night%20in%20forest")
    addButton(NightsInTheForestTab, "Hutao Hub", "https://raw.githubusercontent.com/SLK-gaming/Hutao-Hub/refs/heads/main/99-Nights-In-The-Forest.txt")
    addButton(NightsInTheForestTab, "Voidware", "https://raw.githubusercontent.com/VapeVoidware/VWExtra/main/NightsInTheForest.lua")
    addButton(NightsInTheForestTab, "Moon Hub", "https://raw.githubusercontent.com/m00ndiety/99-nights-in-the-forest/refs/heads/main/Main")
    addButton(NightsInTheForestTab, "Speed-Hub-X", "https://raw.githubusercontent.com/AhmadV99/Speed-Hub-X/main/Speed%20Hub%20X.lua")
    addButton(NightsInTheForestTab, "Arvotheon", "https://get-arvotheon-ontop.netlify.app/Loader.lua", "Mensagem de notificação personalizada")
end

do
    local GrowAGardenTab = Window:MakeTab({
        Name = "GrowAGarden",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    GrowAGardenTab:AddSection({ Name = "GrowAGarden" })

    addButton(GrowAGardenTab, "Speed Hub X", "https://raw.githubusercontent.com/AhmadV99/Speed-Hub-X/main/Speed%20Hub%20X.lua")
    addButton(GrowAGardenTab, "Solix Hub", "https://raw.githubusercontent.com/debunked69/solixloader/refs/heads/main/solix%20v2%20new%20loader.lua")
    addButton(GrowAGardenTab, "No-Lag", "https://raw.githubusercontent.com/NoLag-id/No-Lag-HUB/refs/heads/main/Loader/LoaderV1.lua")
    addButton(GrowAGardenTab, "H4xScripts", "https://raw.githubusercontent.com/H4xScripts/Loader/refs/heads/main/loader2.lua")
    addButton(GrowAGardenTab, "Koronis", "https://raw.githubusercontent.com/nf-36/Koronis/refs/heads/main/Scripts/Loader.lua")
    addButton(GrowAGardenTab, "AlterHub", "https://raw.githubusercontent.com/frvaunted/Main/refs/heads/main/Alter%20Hub")
    addButton(GrowAGardenTab, "Nebula Xyzs", "https://raw.githubusercontent.com/Nebula-xyzs/GAG/refs/heads/main/GrowAGardenXE")
    addButton(GrowAGardenTab, "NatHub V2", "https://raw.githubusercontent.com/ArdyBotzz/NatHub/refs/heads/master/NatHub.lua")
    addButton(GrowAGardenTab, "NatHub", "https://raw.githubusercontent.com/greywaterstill/GAG/refs/heads/main/nathub.lua")
    addButton(GrowAGardenTab, "ThunderZ Hub", "https://raw.githubusercontent.com/ThunderZ-05/HUB/main/Script")
    addButton(GrowAGardenTab, "Y Hub", "https://raw.githubusercontent.com/yue-os/script/refs/heads/main/Y-Hub")
    addButton(GrowAGardenTab, "AVOnTop", "https://raw.githubusercontent.com/nootmaus/GrowAAGarden/refs/heads/main/mauscripts")
    addButton(GrowAGardenTab, "Frzey Hub", "https://raw.githubusercontent.com/FryzerHub/loading-Gui/refs/heads/main/grow%20a%20garden%20v1")
    addButton(GrowAGardenTab, "Mauscripts", "https://raw.githubusercontent.com/nootmaus/GrowAAGarden/refs/heads/main/mauscripts", "Executed")
end

do
    local StealABrainrotTab = Window:MakeTab({
        Name = "Steal a Brainrot",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    StealABrainrotTab:AddSection({ Name = "Steal a Brainrot" })

    addButton(StealABrainrotTab, "Ronix Hub", "pastebin.com/raw/HFx6faQY")
    addButton(StealABrainrotTab, "Lurk Hack", "https://raw.githubusercontent.com/egor2078f/lurkhackv4/refs/heads/main/main.lua")
    addButton(StealABrainrotTab, "Moondiety", "https://raw.githubusercontent.com/m00ndiety/Steal-a-brainrot/refs/heads/main/Steal-a-Brainrot")
    addButton(StealABrainrotTab, "Timmy Hub", "https://raw.githubusercontent.com/WinzeTim/timmyhack2/refs/heads/main/stealabrainrot.lua")
    addButton(StealABrainrotTab, "Arbix Hub", "https://raw.githubusercontent.com/Youifpg/Steal-a-Brainrot-op/refs/heads/main/Arbixhub-obfuscated.lua")
    addButton(StealABrainrotTab, "AVTHOnTop", "https://get-avth-ontop.netlify.app/my-paste/script.lua")
    addButton(StealABrainrotTab, "Prime", "pastebin.com/raw/q8Q3Ff8F")
    addButton(StealABrainrotTab, "Utopia Utility", "https://raw.githubusercontent.com/Klinac/scripts/main/steal_a_brainrot.lua")
    addButton(StealABrainrotTab, "Script 1", "https://pastebin.com/raw/2WEXn2UR")
    addButton(StealABrainrotTab, "Frostware", "https://raw.githubusercontent.com/Jake-Brock/Scripts/main/Fw%20SAB.lua")
    addButton(StealABrainrotTab, "Chili Hub", "https://raw.githubusercontent.com/tienkhanh1/spicy/main/Chilli.lua", "Executed")
end

do
    local AllStarToweDefenseXTab = Window:MakeTab({
        Name = "All Star Tower Defense X",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    AllStarToweDefenseXTab:AddSection({ Name = "All Star Tower Defense X" })

    addButton(AllStarToweDefenseXTab, "Demonic Hub V2", "https://nousigi.com/loader.lua")
    addButton(AllStarToweDefenseXTab, "Try's Hub", "https://raw.githubusercontent.com/Tyrphes/Tyr-s-Hub/refs/heads/main/main.lua")
    addButton(AllStarToweDefenseXTab, "Legend Hub", "https://pastefy.app/ULaWpxKm/raw")
    addButton(AllStarToweDefenseXTab, "Xenith Hub", "https://api.luarmor.net/files/v4/loaders/d7be76c234d46ce6770101fded39760c.lua")
    addButton(AllStarToweDefenseXTab, "Nousigi Hub", "https://nousigi.com/loader.lua")
    addButton(AllStarToweDefenseXTab, "Jimi Hub", "https://raw.githubusercontent.com/bunnnwee/JimiHub/refs/heads/main/ASTDX-Normal")
    addButton(AllStarToweDefenseXTab, "Akatsuki Hub", "https://raw.githubusercontent.com/AkatsukiHub1/STARX/refs/heads/main/README.md", "Executed")
end

do
    local ForsakenTab = Window:MakeTab({
        Name = "Forsaken",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    ForsakenTab:AddSection({ Name = "Forsaken" })

    addButton(ForsakenTab, "Sigmaboy", "https://raw.githubusercontent.com/sigmaboy-sigma-boy/Stamina-Settings-and-ESP/refs/heads/main/SigmasakenLoader")
    addButton(ForsakenTab, "Funny Hub V2", "https://raw.githubusercontent.com/PlutomasterAccount/Funny-Hub-V2-Forsaken/refs/heads/main/Funny%20Hub%20V2%20Forsaken.lua")
    addButton(ForsakenTab, "Moon Pc/Mobile", "https://raw.githubusercontent.com/m00ndiety/Forsaken/refs/heads/main/Forsaken.lua")
    addButton(ForsakenTab, "Lunix Hub", "https://raw.githubusercontent.com/Dzgak/xrurus/refs/heads/main/farsaken.lua")
    addButton(ForsakenTab, "Mandy Hub", "https://raw.githubusercontent.com/MaybeNotMandy/forsaken/refs/heads/main/sae")
    addButton(ForsakenTab, "Space Hub", "https://raw.githubusercontent.com/ago106/SpaceHub/refs/heads/main/loader.lua")
end

do
    local KingLegacyTab = Window:MakeTab({
        Name = "King Legacy",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    KingLegacyTab:AddSection({ Name = "King Legacy" })

    addButton(KingLegacyTab, "Tsuo Hub", "https://raw.githubusercontent.com/Tsuo7/TsuoHub/main/king%20legacy")
    addButton(KingLegacyTab, "Arc Hub", "https://pastebin.com/raw/q7j7nAf0", "Executed")
end

do
    local PetSimulator99Tab = Window:MakeTab({
        Name = "Pet Simulator 99",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    PetSimulator99Tab:AddSection({ Name = "Pet Simulator 99" })

    addButton(PetSimulator99Tab, "Reaper Hub", "https://raw.githubusercontent.com/AyoReaper/Reaper-Hub/refs/heads/main/loader.lua")
    addButton(PetSimulator99Tab, "Infinity Ware", "https://raw.githubusercontent.com/bubblescripts/scripts/refs/heads/main/PS99/psgo")
    addButton(PetSimulator99Tab, "6FootScript", "https://raw.githubusercontent.com/SlamminPig/6FootScripts/main/Scripts/PetSimulator99.lua")
    addButton(PetSimulator99Tab, "Aussie WIRE", "https://api.luarmor.net/files/v3/loaders/4f5c7bbe546251d81e9d3554b109008f.lua")
    addButton(PetSimulator99Tab, "Zap Hub", "https://zaphub.xyz/Exec", "Executed")
end

do
    local DaHoodTab = Window:MakeTab({
        Name = "Da Hood",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    DaHoodTab:AddSection({ Name = "Da Hood" })

    addButton(DaHoodTab, "SwagMode", "https://pastecode.dev/raw/0VplHVK0pQ/Script%20da%20hood%20scarlet")
    addButton(DaHoodTab, "ZAPPED V3 GUI", "https://raw.githubusercontent.com/grekkk/relases/main/zapped.lua")
    addButton(DaHoodTab, "VORTEX GUI", "https://raw.githubusercontent.com/ImagineProUser/vortexdahood/main/vortex")
    addButton(DaHoodTab, "Zinc Hub", "https://raw.githubusercontent.com/Zinzs/luascripting/main/canyoutellitsadahoodscriptornot.lua", "Executed")
end

do
    local AnimeLastStandTab = Window:MakeTab({
        Name = "Anime Last Stand",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    AnimeLastStandTab:AddSection({ Name = "Anime Last Stand" })

    addButton(AnimeLastStandTab, "Demonic HUB V2", "https://raw.githubusercontent.com/Alan0947383/Demonic-HUB-V2/main/S-C-R-I-P-T.lua")
    addButton(AnimeLastStandTab, "Buang Hub", "https://raw.githubusercontent.com/buang5516/buanghub/main/animeLastStand.lua", "Executed")
end

do
    local JujutsuInfiniteTab = Window:MakeTab({
        Name = "Jujutsu Infinite",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    JujutsuInfiniteTab:AddSection({ Name = "Jujutsu Infinite" })

    addButton(JujutsuInfiniteTab, "Noble Hub", "https://api.luarmor.net/files/v3/loaders/21cecfc256321e341fbe9a0a2df5a564.lua")
    addButton(JujutsuInfiniteTab, "Vexium Hub", "https://api.luarmor.net/files/v3/loaders/e7d06aa370f8abb9e1a9bd5bd9c80c7d.lua")
    addButton(JujutsuInfiniteTab, "SolixHub", "https://raw.githubusercontent.com/debunked69/Solixreworkkeysystem/refs/heads/main/solix%20new%20keyui.lua")
    addButton(JujutsuInfiniteTab, "Free Hub", "https://raw.githubusercontent.com/Nate7z/JujutsuInfinite/refs/heads/main/Main.lua", "Executed")
end

do
    local AnimeFightersSimulatorTab = Window:MakeTab({
        Name = "Anime Fighters Simulator", -- Corrigido: Removida a aspa extra
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    AnimeFightersSimulatorTab:AddSection({ Name = "Anime Fighters Simulator" })

    addButton(AnimeFightersSimulatorTab, "Platinum Hub", "https://raw.githubusercontent.com/ZaRdoOx/Loader/main/PlatiniumLoader")
    addButton(AnimeFightersSimulatorTab, "TinyTask Hub", "https://raw.githubusercontent.com/juNstring/cracks/main/TinyTask%20Hub/loader.lua")
    addButton(AnimeFightersSimulatorTab, "JKHub", "https://raw.githubusercontent.com/KiJinGaming/FreeScript/main/KJHub.lua")
    addButton(AnimeFightersSimulatorTab, "Zer0 Hub", "https://raw.githubusercontent.com/JuninhoOGado/ScriptsSite/main/Script276", "Executed")
end

do
    local MurderMysteryTab = Window:MakeTab({
        Name = "Murder Mystery 2",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    MurderMysteryTab:AddSection({ Name = "Murder Mystery 2" })

    addButton(MurderMysteryTab, "YARHM", "https://raw.githubusercontent.com/JuninhoOGado/ScriptsSite/main/Script282")
    addButton(MurderMysteryTab, "Azure 1.2", "https://gist.githubusercontent.com/Raiden84200/84e60fdd20e2d13751f9ad657c8f0a9d/raw/81a130176baf8072b729d6d11549487d283abbee/Lua")
    addButton(MurderMysteryTab, "Aussie WIRE", "https://api.luarmor.net/files/v3/loaders/4f5c7bbe546251d81e9d3554b109008f.lua")
    addButton(MurderMysteryTab, "Nexus Hub", "https://raw.githubusercontent.com/s-o-a-b/nexus/main/loadstring", "Executed")
end

do
    local animevanguardTab = Window:MakeTab({
        Name = "Anime Vanguard",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    animevanguardTab:AddSection({ Name = "Anime Vanguard" })

    addButton(animevanguardTab, "Speed Hub X", "https://raw.githubusercontent.com/AhmadV99/Script-Games/main/Anime%20Vanguards.lua")
    addButton(animevanguardTab, "AtherHub", "https://api.luarmor.net/files/v3/loaders/2529a5f9dfddd5523ca4e22f21cceffa.lua")
    addButton(animevanguardTab, "Solix Hub", "https://raw.githubusercontent.com/debunked69/Solixreworkkeysystem/refs/heads/main/solix%20new%20keyui.lua")
    addButton(animevanguardTab, "Buang Hub", "https://raw.githubusercontent.com/buang5516/buanghub/main/BUANGHUB.lua")
    addButton(animevanguardTab, "Godor", "https://raw.githubusercontent.com/godor1010/godor/refs/heads/main/anime_vanguards_")
    addButton(animevanguardTab, "Star Hub", "https://raw.githubusercontent.com/Tilitestaccount/Star-Hub-Files/refs/heads/main/Star%20Hub%20Free", "Executed")
end

do
    local AnimeShadowTab = Window:MakeTab({
        Name = "Anime Shadow",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    AnimeShadowTab:AddSection({ Name = "Anime Shadow" })

    addButton(AnimeShadowTab, "Legend Handles", "https://raw.githubusercontent.com/LOLking123456/05/refs/heads/main/Vanguards")
    addButton(AnimeShadowTab, "Deng Hub", "https://raw.githubusercontent.com/DENGHUB2025/HUGHUB/main/WL")
    addButton(AnimeShadowTab, "Omgshit", "https://raw.githubusercontent.com/Omgshit/Scripts/main/MainLoader.lua", "Executed")
end

do
    local AnimeCrossoverTab = Window:MakeTab({
        Name = "Anime Crossover Defense",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    AnimeCrossoverTab:AddSection({ Name = "Anime Crossover Defense" })

    addButton(AnimeCrossoverTab, "Demonic Hub V2", "https://raw.githubusercontent.com/Prosexy/Demonic-HUB-V2/main/DemonicHub_V2.lua")
    addButton(AnimeCrossoverTab, "CanislupusXHub", "https://raw.githubusercontent.com/CanisLupusXL/CanislupusXHub/main/Anime%20Crossover%20Defense.lua")
    addButton(AnimeCrossoverTab, "OMG Hub", "https://raw.githubusercontent.com/Omgshit/Scripts/refs/heads/main/Anime%20Crossover%20Defense", "Executed")
end

do
    local thestrongestbattlegroundsTab = Window:MakeTab({
        Name = "The Strongest Battlegrounds",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    thestrongestbattlegroundsTab:AddSection({ Name = "The Strongest Battlegrounds" })

    addButton(thestrongestbattlegroundsTab, "Speed Hub X (Pc/Mobile)", "https://raw.githubusercontent.com/AhmadV99/Speed-Hub-X/main/Speed%20Hub%20X.lua")
    addButton(thestrongestbattlegroundsTab, "Zygarde V2 (Pc/Mobile)", "https://raw.githubusercontent.com/louismich4el/Zygarde/refs/heads/main/ZygardeV1.txt")
    addButton(thestrongestbattlegroundsTab, "SumitScripts", "https://pastefy.app/v9VSOfM5/raw")
    addButton(thestrongestbattlegroundsTab, "FFJ1", "https://raw.githubusercontent.com/FFJ1/Roblox-Exploits/main/scripts/autoparry.lua", "Executed")
end

do
    local JailBreakTab = Window:MakeTab({
        Name = "Jailbreak",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    JailBreakTab:AddSection({ Name = "Jailbreak" })

    addButton(JailBreakTab, "Project Auto V5 (Pc/Mobile)", "http://scripts.projectauto.xyz/AutoRobV5")
    addButton(JailBreakTab, "SnipeHype200", "https://raw.githubusercontent.com/SnipeHype200/i-music/main/beta.lua", "Executed")
end

do
    local BuildABoatSimulatorTab = Window:MakeTab({
        Name = "Build a Boat Simulator",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    BuildABoatSimulatorTab:AddSection({ Name = "Build a Boat Simulator" })

    addButton(BuildABoatSimulatorTab, "LexusHub", "https://pastebin.com/raw/2NjKRALJ")
    addButton(BuildABoatSimulatorTab, "BoatBuilderHub", "https://raw.githubusercontent.com/catblox1346/StensUIReMake/refs/heads/main/Script/boatbuilderhub_B1")
    addButton(BuildABoatSimulatorTab, "UB Hub", "https://gitlab.com/r_soft/main/-/raw/main/LoadUB.lua")
    addButton(BuildABoatSimulatorTab, "Space Hub", "https://raw.githubusercontent.com/ago106/SpaceHub/refs/heads/main/loader.lua")
    addButton(BuildABoatSimulatorTab, "YWXO Hub", "https://raw.githubusercontent.com/ProjectpopCat/ywxoscripts/main/BuildABoatSimulator.lua", "Executed")
end

do
    local scp3008tab = Window:MakeTab({
        Name = "SCP 3008",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    scp3008tab:AddSection({ Name = "SCP 3008" })

    addButton(scp3008tab, "manthem123", "https://raw.githubusercontent.com/manthem123/3008/refs/heads/main/main.lua")
    addButton(scp3008tab, "Waylon", "https://raw.githubusercontent.com/welomenchaina/Loader/refs/heads/main/ScriptLoader")
    addButton(scp3008tab, "Neuron", "https://raw.githubusercontent.com/Yumiara/Python/refs/heads/main/SCP3008.py", "Executed")
end

do
    local BladeBallTab = Window:MakeTab({
        Name = "Blade Ball",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    BladeBallTab:AddSection({ Name = "Blade Ball" })

    addButton(BladeBallTab, "Lunax Hub (Pc/Mobile)", "https://raw.githubusercontent.com/Alexisisback/Universall/refs/heads/main/Blade%20ball.lua")
    addButton(BladeBallTab, "Speed Hub (Pc/Mobile)", "https://raw.githubusercontent.com/Official-Gamer-123/Speed-Hub-Official-Releases-Free/main/SpeedHub_Updated_Key_System_BladeBall.txt")
    addButton(BladeBallTab, "Aussie WIRE", "https://api.luarmor.net/files/v3/loaders/4f5c7bbe546251d81e9d3554b109008f.lua")
    addButton(BladeBallTab, "FFJ1", "https://raw.githubusercontent.com/FFJ1/Roblox-Exploits/main/scripts/autoparry.lua", "Executed")
end

do
    local rivasTab = Window:MakeTab({
        Name = "Rivas",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    rivasTab:AddSection({ Name = "Rivals" })

    addButton(rivasTab, "Script 1", "https://raw.githubusercontent.com/yoyoy979778786745446/rivals-scripts/refs/heads/main/Roblox%20rivals%20script")
    addButton(rivasTab, "Soluna", "https://raw.githubusercontent.com/endoverdosing/Soluna-API/main/main.lua")
    addButton(rivasTab, "Rivals (Pc/Mobile)", "https://raw.githubusercontent.com/s-o-a-b/nexus/main/loadstring")
    addButton(rivasTab, "Rybow Hub", "https://raw.githubusercontent.com/s-o-a-b/nexus/main/loadstring", "Executed")
end

do
    local ArsenalTab = Window:MakeTab({
        Name = "Arsenal",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    ArsenalTab:AddSection({ Name = "Arsenal" })

    addButton(ArsenalTab, "Soluna", "https://soluna-script.vercel.app/arsenal.lua")
    addButton(ArsenalTab, "Timmy Hub", "https://raw.githubusercontent.com/WinzeTim/timmyhack2/refs/heads/main/arsenal.lua")
    addButton(ArsenalTab, "Express Hub", "http://pastebin.com/raw/9ArrNC4L")
    addButton(ArsenalTab, "Script 1", "https://raw.githubusercontent.com/JuninhoOGado/ScriptsSite/main/Script278", "Executed")
end

do
    local BedWarsTab = Window:MakeTab({
        Name = "Bed Wars",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    BedWarsTab:AddSection({ Name = "Bed Wars" })

    addButton(BedWarsTab, "NightRewrite", "https://raw.githubusercontent.com/warprbx/NightRewrite/refs/heads/main/Night/Loader.luau")
    addButton(BedWarsTab, "VapeV4", "https://raw.githubusercontent.com/miacheats/VapeV4ForRoblox/main/NewMainScript.lua")
    addButton(BedWarsTab, "Aurora Hub", "https://raw.githubusercontent.com/cocotv666/Aurora/main/Aurora_Loader", "Executed")
end

do
    local ZombieAttackTab = Window:MakeTab({
        Name = "Zombie Attack",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    ZombieAttackTab:AddSection({ Name = "Zombie Attack" })
    addButton(ZombieAttackTab, "X Universal (Pc/Mobile)", "https://raw.githubusercontent.com/Unknownproooolucky/Unknown-Hub-X-Universal-Games/main/Games/Zombie-Attack", "Executed")
end

do
    local FrontlinesTab = Window:MakeTab({
        Name = "Frontlines",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    FrontlinesTab:AddSection({ Name = "Frontlines" })

    addButton(FrontlinesTab, "Pinguin", "https://raw.githubusercontent.com/PUSCRIPTS/PINGUIN/refs/heads/main/FrontLines")
    addButton(FrontlinesTab, "Main Hub", "https://scripts.waza80.com/script/Frontlines")
    addButton(FrontlinesTab, "Forge Hub", "https://raw.githubusercontent.com/Skzuppy/forge-hub/main/loader.lua", "Executed")
end

do
    local NinjaLegendsTab = Window:MakeTab({
        Name = "Ninja Legends",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    NinjaLegendsTab:AddSection({ Name = "Ninja Legends" })

    addButton(NinjaLegendsTab, "Venture Hub", "https://raw.githubusercontent.com/NukeVsCity/TheALLHACKLoader/main/NukeLoader")
    addButton(NinjaLegendsTab, "Zerpqe", "https://raw.githubusercontent.com/zerpqe/script/main/NinjaLegends.lua")
    addButton(NinjaLegendsTab, "AppleScript001", "https://raw.githubusercontent.com/AppleScript001/Ninjas_Legends/main/README.md")
    addButton(NinjaLegendsTab, "LSndiFye Hub", "https://pastebin.com/raw/LSndiFye", "Executed")
end

do
    local ArmWrestleSimulatorTab = Window:MakeTab({
        Name = "Arm Wrestle Simulator",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    ArmWrestleSimulatorTab:AddSection({ Name = "Arm Wrestle Simulator" })

    addButton(ArmWrestleSimulatorTab, "LDS HUB", "https://api.luarmor.net/files/v3/loaders/49f02b0d8c1f60207c84ae76e12abc1e.lua")
    addButton(ArmWrestleSimulatorTab, "RaCc0oN Hub", "https://raw.githubusercontent.com/RaCc0oN1/RobloxObf/main/MainHub")
    addButton(ArmWrestleSimulatorTab, "Userp1", "https://raw.githubusercontent.com/userp1/self/main/Main.lua")
    addButton(ArmWrestleSimulatorTab, "Script New Upd", "https://lua-library.btteam.net/script-auth.txt", "Executed")
end

do
    local ToiletDefenseSimulatoTab = Window:MakeTab({
        Name = "Toilet Defense Simulato",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    ToiletDefenseSimulatoTab:AddSection({ Name = "Toilet Defense Simulato" })

    addButton(ToiletDefenseSimulatoTab, "Script 1", "https://rawscripts.net/raw/Fixes-Toilet-Defense-SEVEN-SCRIPT-9364", "Executed")
end

do
    local PhantomForcesTab = Window:MakeTab({
        Name = "PhantomForces",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    PhantomForcesTab:AddSection({ Name = "PhantomForces" })

    addButton(PhantomForcesTab, "Homo Hack (Pc/Mobile)", "https://raw.githubusercontent.com/dementiaenjoyer/homohack/main/loader.lua")
    addButton(PhantomForcesTab, "Cooki Hub", "https://raw.githubusercontent.com/SumCooki/Cooki-Hub/refs/heads/main/Cooki%20Hub", "Executed")
end

do
    local SlimeSlayingOnileRPGTab = Window:MakeTab({
        Name = "Slime Slaying Online RPG",
        Icon = ICON_DEFAULT,
        PremiumOnly = false
    })

    local SlimeSlayingOnileRPGSection = SlimeSlayingOnileRPGTab:AddSection({
        Name = "Slime Slaying Online RPG"
    })

    SlimeSlayingOnileRPGTab:AddButton({
        Name = "Slime Slaying Online RPG",
        Callback = function()
            script_key = ""
            loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/d8bf54daa5b358826ce74cab275f9135.lua"))()
        end
    })
end

-- Outras abas e seções (como A Sols Rng, ADustyTrip, etc.) seriam otimizadas
-- da mesma forma, usando a função `addButton` para evitar repetição.
-- Por exemplo:
-- local ADustyTripTab = Window:MakeTab(...)
-- local ADustyTripSection = ADustyTripTab:AddSection(...)
-- addButton(ADustyTripTab, "Connect Hub", "https://raw.githubusercontent.com/artemy133563/Utilities/main/ADustyTrip")

