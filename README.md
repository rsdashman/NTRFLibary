# NTRFLibary

```
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/rsdashman/Syfire-ui-project000138/refs/heads/main/NTRFui"))()-- Adjust path as needed

-- UI Library Example Usage
-- This file demonstrates how to use the UI library with all its features

-- First, load the UI library (assuming it's in a separate file)
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/rsdashman/Syfire-ui-project000138/refs/heads/main/NTRFui"))()-- Adjust path as needed

-- Create the main window
local mainWindow = library:CreateWindow("Main Script")

-- Create sections within the window
local combatSection = mainWindow:Section("Combat")
local movementSection = mainWindow:Section("Movement") 
local visualSection = mainWindow:Section("Visuals")
local miscSection = mainWindow:Section("Misc")

-- Combat Section Examples
combatSection:Label("Combat Features")

-- Toggle example with callback
combatSection:Toggle("Aimbot", {
    flag = "aimbot_enabled",
    Default = false
}, function(enabled)
    print("Aimbot:", enabled)
    -- Your aimbot logic here
end)

combatSection:Toggle("Trigger Bot", {
    flag = "triggerbot_enabled", 
    Default = true
}, function(enabled)
    print("Trigger Bot:", enabled)
    -- Your trigger bot logic here
end)

combatSection:Toggle("Silent Aim", {
    flag = "silent_aim",
    Default = false
}, function(enabled)
    print("Silent Aim:", enabled)
    -- Your silent aim logic here
end)

-- Button example
combatSection:Button("Kill All", function()
    print("Kill All button pressed!")
    -- Your kill all logic here
end)

combatSection:Button("Teleport to Spawn", function()
    print("Teleporting to spawn...")
    -- Your teleport logic here
end)

-- Movement Section Examples
movementSection:Label("Movement Features")

movementSection:Toggle("Speed Hack", {
    flag = "speed_hack",
    Default = false
}, function(enabled)
    print("Speed Hack:", enabled)
    if enabled then
        -- Enable speed hack
        local player = game.Players.LocalPlayer
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            player.Character.Humanoid.WalkSpeed = 50
        end
    else
        -- Disable speed hack
        local player = game.Players.LocalPlayer
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            player.Character.Humanoid.WalkSpeed = 16
        end
    end
end)

movementSection:Toggle("Jump Boost", {
    flag = "jump_boost",
    Default = false
}, function(enabled)
    print("Jump Boost:", enabled)
    if enabled then
        -- Enable jump boost
        local player = game.Players.LocalPlayer
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            player.Character.Humanoid.JumpPower = 100
        end
    else
        -- Disable jump boost
        local player = game.Players.LocalPlayer
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            player.Character.Humanoid.JumpPower = 50
        end
    end
end)

movementSection:Toggle("Infinite Jump", {
    flag = "infinite_jump",
    Default = false
}, function(enabled)
    print("Infinite Jump:", enabled)
    -- Your infinite jump logic here
end)

movementSection:Button("Reset Movement", function()
    print("Resetting movement...")
    local player = game.Players.LocalPlayer
    if player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.WalkSpeed = 16
        player.Character.Humanoid.JumpPower = 50
    end
end)

-- Visuals Section Examples
visualSection:Label("Visual Features")

visualSection:Toggle("ESP", {
    flag = "esp_enabled",
    Default = false
}, function(enabled)
    print("ESP:", enabled)
    -- Your ESP logic here
end)

visualSection:Toggle("Full Bright", {
    flag = "full_bright",
    Default = false
}, function(enabled)
    print("Full Bright:", enabled)
    if enabled then
        -- Enable full bright
        game.Lighting.Brightness = 10
        game.Lighting.ClockTime = 14
    else
        -- Disable full bright
        game.Lighting.Brightness = 2
        game.Lighting.ClockTime = 12
    end
end)

visualSection:Toggle("No Fog", {
    flag = "no_fog",
    Default = false
}, function(enabled)
    print("No Fog:", enabled)
    if enabled then
        game.Lighting.FogEnd = 1000000
    else
        game.Lighting.FogEnd = 1000
    end
end)

visualSection:Button("Reset Visuals", function()
    print("Resetting visuals...")
    game.Lighting.Brightness = 2
    game.Lighting.ClockTime = 12
    game.Lighting.FogEnd = 1000
end)

-- Misc Section Examples
miscSection:Label("Miscellaneous Features")

miscSection:Toggle("Auto Farm", {
    flag = "auto_farm",
    Default = false
}, function(enabled)
    print("Auto Farm:", enabled)
    -- Your auto farm logic here
end)

miscSection:Toggle("Anti AFK", {
    flag = "anti_afk",
    Default = true
}, function(enabled)
    print("Anti AFK:", enabled)
    -- Your anti AFK logic here
end)

miscSection:Toggle("Auto Collect", {
    flag = "auto_collect",
    Default = false
}, function(enabled)
    print("Auto Collect:", enabled)
    -- Your auto collect logic here
end)

miscSection:Button("Destroy GUI", function()
    print("Destroying GUI...")
    -- Destroy the GUI
    if library.ScreenGUI then
        library.ScreenGUI:Destroy()
    end
end)

miscSection:Button("Rejoin Game", function()
    print("Rejoining game...")
    game:GetService("TeleportService"):Teleport(game.PlaceId)
end)

-- Example of using flags in your script logic
local function updateLoop()
    while wait(0.1) do
        -- Check if aimbot is enabled
        if library.flags.aimbot_enabled then
            -- Run aimbot logic
            print("Running aimbot...")
        end
        
        -- Check if speed hack is enabled
        if library.flags.speed_hack then
            -- Ensure speed hack stays active
            local player = game.Players.LocalPlayer
            if player.Character and player.Character:FindFirstChild("Humanoid") then
                player.Character.Humanoid.WalkSpeed = 50
            end
        end
        
        -- Check if auto farm is enabled
        if library.flags.auto_farm then
            -- Run auto farm logic
            print("Running auto farm...")
        end
    end
end

-- Start the update loop
spawn(updateLoop)

-- Example of creating multiple windows
local secondWindow = library:CreateWindow("Settings")

local configSection = secondWindow:Section("Configuration")

configSection:Label("Script Settings")

configSection:Toggle("Save Settings", {
    flag = "save_settings",
    Default = true
}, function(enabled)
    print("Save Settings:", enabled)
end)

configSection:Toggle("Auto Load", {
    flag = "auto_load",
    Default = false
}, function(enabled)
    print("Auto Load:", enabled)
end)

configSection:Button("Save Config", function()
    print("Saving configuration...")
    -- Your save config logic here
end)

configSection:Button("Load Config", function()
    print("Loading configuration...")
    -- Your load config logic here
end)

-- Example of accessing flags from anywhere in your script
local function checkFlags()
    print("Current flags:")
    for flagName, value in pairs(library.flags) do
        print(flagName .. ":", value)
    end
end

-- Call this function to see all current flag values
-- checkFlags()

print("UI Library Example loaded successfully!")
print("Use the GUI to control script features.")

´´´
