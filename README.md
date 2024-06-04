local l = loadstring(game:HttpGet("https://raw.githubusercontent.com/laagginq/ui-libraries/main/dxhooknotify/src.lua", true))()
l:Notify("Join To Game !","Loading! Enable Cheat | Roblox",4)

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/cat"))() --you can go into the github link and copy all of it and modify it for yourself.
local Window = Library:CreateWindow("Second Piece | ScriptDev", Vector2.new(492, 598), Enum.KeyCode.Home) --you can change your UI keybind
local AimingTab = Window:CreateTab("General") --you can rename this tab to whatever you want --you can also change the tabs code, for example "AimingTab" can be changed to "FunnyCoolTab" etc.
local AimingTab2 = Window:CreateTab("Bosses") --you can rename this tab to whatever you want --you can also change the tabs code, for example "AimingTab" can be changed to "FunnyCoolTab" etc.

local oneSection1 = AimingTab:CreateSector("Section [1]", "left")
oneSection1:AddToggle("Bring [ItemDrop]", false, function(first)
_G.Bring = first
while _G.Bring do wait(0.1)
for _,v in pairs(workspace.ItemDrop:GetDescendants()) do
if v:IsA("TouchTransmitter") then
firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 0) --0 is touch
firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 1) -- 1 is untouch
end
end
end
end)

local oneSection1 = AimingTab:CreateSector("Extra", "left")
oneSection1:AddSlider("Walk-Speed", 0, 75, 245, 1, function(speed)
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = speed
end)
oneSection1:AddSlider("Jump-Power", 0, 75, 245, 1, function(jump)
game.Players.LocalPlayer.Character.Humanoid.JumpPower = jump
end)

local threeSection = AimingTab:CreateSector("Section [2]", "right")
threeSection:AddDropdown("Selected Stat!", {"Melee", "Defense", "Weapon", "DemonFruit"}, "Selected !", false, function(t)
PlayerTP1 = t
end)
threeSection:AddToggle(">|Up|<", false, function(two)
_G.Stat = two
while _G.Stat do wait()
local args = {
[1] = PlayerTP1,
[2] = 10
}

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("UpStats"):FireServer(unpack(args))

end
end)

local twoSection = AimingTab2:CreateSector("Farm-Bosses", "left")
twoSection:AddToggle("Shank - Lv.2500", false, function(three)
_G.Npc = three
while _G.Npc do wait(1)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2495.93213, 50.1080666, -1111.25513, 0.999930739, 4.20886614e-08, -0.0117672924, -4.17042472e-08, 1, 3.29134977e-08, 0.0117672924, -3.24204734e-08, 0.999930739)
wait(0.1)
local args = {
[1] = "DismantleV2"
}

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("SkillHolder"):FireServer(unpack(args))

end
end)

local oneSection1 = AimingTab:CreateSector("Npc", "left")
Jks = {}
for i,v in pairs(workspace.NPC:GetChildren()) do
    table.insert(Jks,v.Name) 
end

oneSection1:AddDropdown("Selected Tp !", Jks, false, function(b)
    PlayerTP = b
end)
oneSection1:AddButton("TP | Select", function()
for i,v in pairs(workspace.NPC[PlayerTP]:GetDescendants()) do
if v.Name == "Head" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
end
end
end)

repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer.Idled:connect(function()
game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)
