-- [=-----------------------------------------------------------=]
--                ("Blacky") EDIT = กูโปรเเล้วไงใครเเคร์ :P
-- [=-----------------------------------------------------------=]
--
--
--
--
--
--
--
--
--
--
--
--
----
--
--
--
--
--
--
--
--
--
--
--
----
--
--
--
--
--
--
--
--
--
--
--
----
--
--
--
--
--
--
--
--
--
--
--
--
local Material = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/MaterialLua/master/Module.lua"))()

local X = Material.Load({
    Title = "AFS - HobbitxBlacky",
    Style = 3,
    SizeX = 500,
    SizeY = 350,
    Theme = "Dark",
    ColorOverrides = {
        MainFrame = Color3.fromRGB(35,35,35)
    }
})

local Y = X.New({
    Title = "Main"
})

local A = Y.Button({
    Text = "You have not selected any Dataloss Type",
    Callback = function()
        if Type == "Start Dataloss" then
                    local args = {
                        [1] = {
                            [string.rep("9", 4200000)] = require(game.ReplicatedStorage.ModuleScripts.LocalDairebStore).GetStoreProxy("GameData"):GetData("Pets")[1].UID
                        },
                        [2] = "Sir_Blacky_God",
                        [3] = 3
                    }

                    game:GetService("ReplicatedStorage").Remote.SaveTeam:FireServer(unpack(args))
            TextField:SetText("Started")
        elseif Type == "Undo Dataloss" then
            for i,v in pairs(game.Players.LocalPlayer.PlayerGui.MainGui.Pets.TeamsList.Main.Scroll:GetDescendants()) do
                if v.Name == "TeamName" and v.Text == "Sir_Blacky_God" then
                    local args = {
                        [1] = v.Parent.LayoutOrder
                    }

                    game:GetService("ReplicatedStorage").Remote.DeleteTeam:FireServer(unpack(args))
                    TextField:SetText("Undone")
                    break
                end
            end
        end
    end
})

local D = Y.Dropdown({
    Text = "Dataloss Type",
    Callback = function(Value)
        getgenv().Type = Value
    end,
    Options = {
        "Start Dataloss",
        "Undo Dataloss"
    }
})

local AE3 = Y.Button({
    Text = "Rejoin Server",
    Callback = function()
    local ts = game:GetService("TeleportService") local p = game.Players.LocalPlayer ts:Teleport(game.PlaceId, p) 
    end
})

local AE = Y.Button({
    Text = "Desolate Store Cheap Netflix 0.43$",
    Callback = function()
                print("")
        end
    end
})
local AE2 = Y.Button({
    Text = "Copy Discord Invite",
    Callback = function()
        setclipboard("https://discord.gg/fVKX3MGt99")
    end
})

getgenv().TextField = Y.TextField({
    Text = "Status",
    Type = "Default"
})

while task.wait() do
    if Type then
        A:SetText(Type)
    end
end
