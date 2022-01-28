local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/zxciaz/VenyxUI/main/Reuploaded"))()
local venyx = library.new("COMMUNITY", 5013109572)
local page = venyx:addPage("MAIN", 5012544693)
local section1 = page:addSection("AutoFarm")
section1:addToggle("AutoFarmLevel", _G.AutoFarm_Level, function(A)
    _G.AutoFarm_Level = A
end)

function checklevel()
    local Level = game:GetService("Players").LocalPlayer.Data.Level.Value
    if Level == 1 or Level <= 9 then
        MON = "Bandit [Lv. 5]"
        QUESTTITLE = "Bandit"
        QUESTPOS = CFrame.new(1060.0158691406, 16.424287796021, 1547.9769287109)
        MONPOS = CFrame.new(1148.8698730469, 16.432844161987, 1630.5396728516)
        QUESTNAME = "BanditQuest1"
        QUESTNUMBER = 1
        SPAWNPOINT = "Default"
        SPAWNPOINTPOS = CFrame.new(973.96197509766, 16.273551940918, 1413.2775878906)
    elseif Level == 10 or Level <= 14 then
        MON = "Monkey [Lv. 14]"
        QUESTTITLE = "Monkey"
        QUESTPOS = CFrame.new(-1599.3576660156, 37.332126617432, 153.80061340332)
        MONPOS = CFrame.new(-1464.3162841797, 22.852104187012, 110.80517578125)
        QUESTNAME = "JungleQuest"
        QUESTNUMBER = 1
        SPAWNPOINT = "Jungle"
        SPAWNPOINTPOS = CFrame.new(-1337.4604492188, 11.852861404419, 497.52340698242)
    elseif Level == 15 or Level <= 29 then
        MON = "Gorilla [Lv. 20]"
        QUESTTITLE = "Gorilla"
        QUESTPOS = CFrame.new(-1599.3576660156, 37.332126617432, 153.80061340332)
        MONPOS = CFrame.new (-1275.0313720703, 6.2204737663269, -516.16925048828)
        QUESTNAME = "JungleQuest"
        QUESTNUMBER = 2
        SPAWNPOINT = "Jungle"
        SPAWNPOINTPOS = CFrame.new(-1337.4604492188, 11.852861404419, 497.52340698242)
    elseif Level == 30 or Level <= 39 then
        MON = "Pirate [Lv. 35]"
        QUESTTITLE = "Pirate"
        QUESTPOS = CFrame.new(-1150.64, 4.75206, 3816.9)
        MONPOS = CFrame.new(-1208.95, 4.75206, 3887.63)
        QUESTNAME = "BuggyQuest1"
        QUESTNUMBER = 1
        SPAWNPOINT = "Pirate"
        SPAWNPOINTPOS = CFrame.new(-1188.31, 4.75157, 3816.25)
    elseif Level == 40 or Level <= 60 then
        MON = "Brute [Lv. 45]"
        QUESTTITLE = "Brute"
        QUESTPOS = CFrame.new(-1150.64, 4.75206, 3816.9)
        MONPOS = CFrame.new(-1096.8126220703, 14.809886932373, 4263.9326171875)
        QUESTNAME = "BuggyQuest1"
        QUESTNUMBER = 2
        SPAWNPOINT = "Pirate"
        SPAWNPOINTPOS = CFrame.new(-1188.31, 4.75157, 3816.25)
    elseif Level == 60 or Level <= 74 then
        MON = "Desert Bandit [Lv. 60]"
        QUESTTITLE = "Desert Bandit"
        QUESTPOS = CFrame.new(894.972, 6.43847, 4390.71)
        MONPOS = CFrame.new(933.959, 6.448, 4450.99)
        QUESTNAME = "BuggyQuest1"
        QUESTNUMBER = 2
        SPAWNPOINT = "Desert"
        SPAWNPOINTPOS = CFrame.new(912.51361083984, 3.3792164325714, 4112.7407226562)
    end
end
    Method = CFrame.new(0,25,0)
    
spawn(function()
    while wait(3) do
        if Methodnow == 1 then
        Methodnow = 2
        Method = CFrame.new(0,25,0)
        else
        Methodnow = 1
        Method = CFrame.new(0,0,25)
        end
    end
end)
    
spawn(function()
    while wait() do
        if _G.WARP then
            game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
        else
            game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
        end
    end
end)
    
spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function()
        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid") and _G.AutoFarm_Level then
            setfflag("HumanoidParallelRemoveNoPhysics", "False")
            setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
            game:GetService("Players").LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
end)
    
    
spawn(function()
    while wait() do
        if _G.AutoFarm_Level then
            pcall(function()
                checklevel()
        
                if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,QUESTTITLE) then
                    local args = {
                        [1] = "AbandonQuest"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end
                if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                        
                    if game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT then
                        local args = {
                            [1] = "SetTeam",
                            [2] = "Pirates"
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        wait(0.5)
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = QUESTPOS
                        wait(0.8)
                            local args = {
                                [1] = "StartQuest",
                                [2] = QUESTNAME,
                                [3] = QUESTNUMBER
                            }
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        wait(0.8)
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = MONPOS
                    else
                        _G.WARP = true
                        repeat 
                            wait()
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = SPAWNPOINTPOS
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT or _G.AutoFarm_Level == false
                        _G.WARP = false
                    end
                end
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    for i2,v2 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == MON and v2.Name == MON then
                            v2.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                            v2.HumanoidRootPart.CanCollide = false
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * Method
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        end
                    end
                end
            end)
        end
    end
end)
    
    
    
spawn(function()
    game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        if _G.AutoFarm_Level then
            local Combat = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
            local Cemara = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)
            Cemara.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}
            Combat.activeController.timeToNextAttack = 0
            Combat.activeController.hitboxMagnitude = 120
            Combat.activeController.increment = 3
        end
    end)
end) 
end)
    
    
spawn(function()
    game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        if _G.AutoFarm_Level then
            game:GetService'VirtualUser':CaptureController()
            game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
        end
    end)
end) 
end)







local page = venyx:addPage("MISC", 5012544693)
local section1 = page:addSection("MISC")


section1:addButton("Rejoin", function()
	game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").localPlayer)
end)


local page = venyx:addPage("SETTING", 5012544693)
local section1 = page:addSection("Setting and Orther")

section1:addToggle("Auto Haki", _G.Auto_Haki, function(H)
    _G.Auto_Haki = H
end)

section1:addButton("ResetCharacter", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart:Destroy()
end)

section1:addButton("Right Destroy", function()
    game.Players.LocalPlayer.Character.RightUpperLeg:Destroy()
end)

section1:addButton("Left Destroy", function()
    game.Players.LocalPlayer.Character.LeftUpperLeg:Destroy()
end)



spawn(function()
    while wait(.1) do
        if _G.Auto_Haki then
            if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
            end
        end
    end
end)

function AutoHaki()
    while wait(.1) do
        if _G.Auto_Haki then
            if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                local args = {
                    [1] = "Buso"
                }
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            end
        end
    end
end
