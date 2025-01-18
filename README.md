-- syn request cuz sigma
local req = http_request or request or (syn and syn.request)

-- Lite Hub webhook for the muscle legends version not the legends of speed lmao
local webhookUrl = "https://discord.com/api/webhooks/1327941531021082655/UYsrwa5rF0_mdPDsiQz73s0F6F6eIBqZxl4PJa6pa94SzqZp4T9OjNGKTz0K11Od5vFU"

-- roblox services 
local HttpService = game:GetService("HttpService")
local Players = game:GetService("Players")
local MarketplaceService = game:GetService("MarketplaceService")
local UserInputService = game:GetService("UserInputService")

-- local player information like the device they are on while using Lite Hub
local player = Players.LocalPlayer
local username = player.Name
local userId = player.UserId
local displayName = player.DisplayName
local deviceType = UserInputService.TouchEnabled and "Mobile" or "PC"

-- which executors will say if they are using them
local function detectExecutor()
    if syn then
        return "Synapse X"
    elseif iskrnlclosure then
        return "KRNL"
    elseif fluxus then
        return "Fluxus"
    elseif Arceus then
        return "Arceus X"
    elseif delta then
        return "Delta"
    elseif codex then
        return "Code X"
    elseif cubix then
        return "Cubix"
    elseif nezur then
        return "Nezur"
    elseif getexecutorname then
        return getexecutorname()  -- For executors that may have this function
    elseif identifyexecutor then
        return identifyexecutor()  -- Another alternative
    else
        return "Unknown Executor"
    end
end

local executor = detectExecutor()

-- the things that will be sent to the discord
local body = {
    embeds = {{
        title = MarketplaceService:GetProductInfo(game.PlaceId).Name,
        description = "Username = " .. username ..
                      "\nUserID = " .. userId ..
                      "\nDisplay Name = " .. displayName ..
                      "\nDevice Type = " .. deviceType ..
                      "\nExecutor = " .. executor,
        color = 0,
        author = { name = "Muscle Legends " }
    }}
}

-- encode the data as JSON
local jsonData = HttpService:JSONEncode(body)

-- send the persons things to discord
req({
    Url = webhookUrl,
    Method = 'POST',
    Headers = { ['Content-Type'] = 'application/json' },
    Body = jsonData
})

--Main Script
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/memejames/elerium-v2-ui-library//main/Library", true))()


local window = library:AddWindow("Adopt V2", {
    main_color = Color3.fromRGB(128,128,128), -- Color
    min_size = Vector2.new(420, 440), -- Size of the gui
    can_resize = false, -- true or false
})

local Maintab = window:AddTab("Main")

-- Anti Crash Button
Maintab:AddButton("Anti Crash", function()
    wait(0.5)
    local ba = Instance.new("ScreenGui")
    local ca = Instance.new("TextLabel")
    local da = Instance.new("Frame")
    local _b = Instance.new("TextLabel")
    local ab = Instance.new("TextLabel")

    ba.Parent = game.CoreGui
    ba.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

    ca.Parent = ba
    ca.Active = true
    ca.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
    ca.Draggable = true
    ca.Position = UDim2.new(0.698610067, 0, 0.098096624, 0)
    ca.Size = UDim2.new(0, 370, 0, 52)
    ca.Font = Enum.Font.SourceSansSemibold
    ca.Text = "Anti Afk"
    ca.TextColor3 = Color3.new(0, 1, 1)
    ca.TextSize = 22

    da.Parent = ca
    da.BackgroundColor3 = Color3.new(0.196078, 0.196078, 0.196078)
    da.Position = UDim2.new(0, 0, 1.0192306, 0)
    da.Size = UDim2.new(0, 370, 0, 107)

    _b.Parent = da
    _b.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
    _b.Position = UDim2.new(0, 0, 0.800455689, 0)
    _b.Size = UDim2.new(0, 370, 0, 21)
    _b.Font = Enum.Font.Arial
    _b.Text = "Made by luca#5432"
    _b.TextColor3 = Color3.new(0, 1, 1)
    _b.TextSize = 20

    ab.Parent = da
    ab.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
    ab.Position = UDim2.new(0, 0, 0.158377, 0)
    ab.Size = UDim2.new(0, 370, 0, 44)
    ab.Font = Enum.Font.ArialBold
    ab.Text = "Status: Active"
    ab.TextColor3 = Color3.new(0, 1, 1)
    ab.TextSize = 20

    local bb = game:GetService("VirtualUser")
    game:GetService("Players").LocalPlayer.Idled:Connect(function()
        bb:CaptureController()
        bb:ClickButton2(Vector2.new())
        ab.Text = "Roblox tried kicking you, but I didnÃ¢â‚¬â„¢t let them!"  -- Fixed encoding issue
        wait(2)
        ab.Text = "Status: Active"
    end)
end)

-- Destroy Ad teleport Button
Maintab:AddButton("Destroy Ad teleport", function()
    local part = workspace:FindFirstChild("RobloxForwardPortals")
    if part then
        part:Destroy()
        print("Part 'RobloxForwardPortals' has been destroyed.")
    else
        print("Part 'RobloxForwardPortals' not found.")
    end
end)

-- Create folder "Islands Teleports"
local folder = Maintab:AddFolder("Islands Teleports")

-- Beach Teleport
folder:AddButton("Beach", function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-11, 5, -178)
    end
end)

-- Legends Teleport
folder:AddButton("Legends", function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(4603, 989, -3898)
    end
end)

-- Muscle Teleport
folder:AddButton("Muscle", function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-8626, 15, -5730)
    end
end)

-- Tiny Teleport
folder:AddButton("Tiny", function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-38, 5, 1884)
    end
end)

-- Secret Teleport
folder:AddButton("Secret", function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2596, -1, 5738)
    end
end)

-- Inferno Teleport
folder:AddButton("Inferno", function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-6759, 5, -1285)
    end
end)

-- Frost Teleport
folder:AddButton("Frost", function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2623, 5, -409)
    end
end)

-- Mythical Teleport
folder:AddButton("Mythical", function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2251, 5, 1073)
    end
end)

-- Rock Farming v1 Section
local folder2 = Maintab:AddFolder("Rock Farming v1")
folder2:AddLabel("Coming Soon")

-- Brawl Things
local folder3 = Maintab:AddFolder("Brawl")

-- God Mode Toggle
folder3:AddSwitch("God Mode (Brawl)", function(State)
    godModeToggle = State
    if godModeToggle then
        -- Repeat the joinBrawl event every 0.1 seconds to simulate God Mode
        task.spawn(function()
            while godModeToggle do
                local args = { [1] = "joinBrawl" }
                game:GetService("ReplicatedStorage"):WaitForChild("rEvents"):WaitForChild("brawlEvent"):FireServer(unpack(args))
                task.wait()  -- Repeat the event every 0 seconds
            end
        end)
    end
end)

-- Auto Join Brawl
folder3:AddSwitch("Auto Join Brawl", function(State)
    godModeToggle = State
    if godModeToggle then
        task.spawn(function()
            while godModeToggle do
                local args = { [1] = "joinBrawl" }
                game:GetService("ReplicatedStorage"):WaitForChild("rEvents"):WaitForChild("brawlEvent"):FireServer(unpack(args))
                task.wait(2)  -- Repeat the event every 2 seconds
            end
        end)
    end
end)


window:AddTab("Killing")

local autoKillEnabled = false
local killPlayer = nil
local whiteListedPlayers = {}

-- Dropdown for WhiteList (players who won't be affected by auto kill)
Killingtab:AddDropdown("WhiteList", function(playerName)
    if playerName ~= "None" then
        table.insert(whiteListedPlayers, playerName)
    end
end)

whiteListDropdown:Add("None")
for _, player in pairs(game.Players:GetPlayers()) do
    whiteListDropdown:Add(player.Name)
end

Killingtab:AddLabel("Target A Player")

-- Dropdown for selecting target player to kill
Killingtab:AddDropdown("Select Player", function(playerName)
    killPlayer = playerName == "None" and nil or playerName
end)

selectPlayerDropdown:Add("None")
for _, player in pairs(game.Players:GetPlayers()) do
    selectPlayerDropdown:Add(player.Name)
end

-- Switch to enable/disable killing specific players
local killPlayersEnabled = false
Killingtab:AddSwitch("Kill Players", function(State)
    killPlayersEnabled = State
end)

-- Switch to enable/disable Auto Punch
local autoPunchEnabled = false
Killingtab:AddSwitch("Auto Punch", function(State)
    autoPunchEnabled = State
end)

-- Switch to enable/disable Auto Punch without animation
local autoPunchNoAnimEnabled = false
Killingtab:AddSwitch("Auto Punch [No Animation]", function(State)
    autoPunchNoAnimEnabled = State
end)

-- Spying Section (added under Killing tab)
local spyPlayer = nil
local spyPlayerEnabled = false

-- Dropdown for selecting player to spy on
Killingtab:AddDropdown("Select Player To Spy", function(playerName)
    spyPlayer = playerName == "None" and nil or playerName
end)

spyPlayerDropdown:Add("None")
for _, player in pairs(game.Players:GetPlayers()) do
    spyPlayerDropdown:Add(player.Name)
end

-- Switch to enable/disable spying on selected player
Killingtab:AddSwitch("Spy Player", function(State)
    spyPlayerEnabled = State
end)

-- Function to switch camera to selected player's camera
local function switchCameraToPlayer(playerName)
    local targetPlayer = game.Players:FindFirstChild(playerName)
    if targetPlayer and targetPlayer.Character then
        local character = targetPlayer.Character
        local humanoid = character:FindFirstChild("Humanoid")
        if humanoid then
            local camera = game.Workspace.CurrentCamera
            camera.CameraSubject = humanoid
        end
    end
end

-- Function to handle killing and invisibility for characters
local function handleKill(character, localCharacter, targetPlayerName)
    if not character or not localCharacter then return end

    -- Find the player's HumanoidRootPart and your hands
    local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
    local leftHand = localCharacter:FindFirstChild("LeftHand")
    local rightHand = localCharacter:FindFirstChild("RightHand")
    local head = character:FindFirstChild("Head")

    if not humanoidRootPart or not leftHand or not rightHand then return end

    -- Teleport the HumanoidRootPart to your hands
    humanoidRootPart.CFrame = leftHand.CFrame
    humanoidRootPart.CFrame = rightHand.CFrame

    -- Remove the head if it exists
    if head then
        head.Parent = nil
    end

    -- Make the HumanoidRootPart invisible
    humanoidRootPart.Transparency = 1
    humanoidRootPart.CanCollide = false

    -- Optionally, make other parts of the character invisible as well
    for _, part in pairs(character:GetChildren()) do
        if part:IsA("BasePart") and part.Name ~= "Head" and part.Name ~= "HumanoidRootPart" then
            part.Transparency = 1
            part.CanCollide = false
        end
    end
end

-- Main loop that runs every frame to handle kill logic, punching, and spying
game:GetService('RunService').RenderStepped:Connect(function()
    -- Handle Auto Kill: Loop through all players and kill those not white-listed
    if autoKillEnabled then
        for _, player in pairs(game:GetService("Players"):GetPlayers()) do
            if player.Name ~= game.Players.LocalPlayer.Name and not table.find(whiteListedPlayers, player.Name) then
                local character = player.Character
                local localCharacter = game.Players.LocalPlayer.Character
                handleKill(character, localCharacter)
            end
        end
    end

    -- Handle "Kill Players" with specific target player
    if killPlayersEnabled and killPlayer then
        local targetPlayer = game.Players:FindFirstChild(killPlayer)
        if targetPlayer then
            local character = targetPlayer.Character
            local localCharacter = game.Players.LocalPlayer.Character
            handleKill(character, localCharacter, killPlayer)
        end
    end

    -- Handle Auto Punch without animation
    if autoPunchNoAnimEnabled then
        local player = game.Players.LocalPlayer
        local playerName = player.Name
        local punchTool = player.Backpack:FindFirstChild("Punch") or game.Workspace:FindFirstChild(playerName):FindFirstChild("Punch")
        _G.autoPunchanim = true

        while _G.autoPunchanim do
            if punchTool then
                if punchTool.Parent ~= game.Workspace:FindFirstChild(playerName) then
                    punchTool.Parent = game.Workspace:FindFirstChild(playerName)
                end
                game.Players.LocalPlayer.muscleEvent:FireServer("punch", "rightHand")
                game.Players.LocalPlayer.muscleEvent:FireServer("punch", "leftHand")
                wait()
            else
                _G.autoPunchanim = false
            end
        end
    end

    -- Handle Spying on selected player
    if spyPlayerEnabled and spyPlayer then
        switchCameraToPlayer(spyPlayer)
    end
end)

-- Function to reset the player's character (optional)
local function resetPlayer()
    local player = game.Players.LocalPlayer
    if player.Character then
        player.Character:BreakJoints()
    end
end

resetPlayer()










local rebirthAmount = 0
local currentRebirths = 0
local autoRebirthEnabled = false

-- Create a function for auto rebirth
local function autoRebirth()
    spawn(function()
        while autoRebirthEnabled do
            local rebirthevent = game.ReplicatedStorage.rEvents:FindFirstChild("rebirthRemote")
            if rebirthevent then
                if rebirthAmount == 0 or currentRebirths < rebirthAmount then
                    rebirthevent:FireServer()
                    currentRebirths = currentRebirths + 1
                else
                    autoRebirthEnabled = false
                    print("Reached the desired rebirth amount.")
                end
            end
            wait(0.1)
        end
    end)
end

-- Assuming 'window' is the UI library you're using, and it has an AddTab method
local RebirthTab = window:AddTab("Rebirth")

-- Add a switch for auto rebirth
RebirthTab:AddSwitch("Auto Rebirth", {
    Default = false,
    Callback = function(state)
        autoRebirthEnabled = state
        if state then
            autoRebirth()
        end
    end
})



-- Add a textbox to set the rebirth amount
RebirthTab:AddTextBox("Select Rebirth Amount", function(text)
    local inputNumber = tonumber(text)
    if inputNumber and inputNumber >= 0 then
        rebirthAmount = inputNumber
        currentRebirths = 0
        print("Rebirth amount set to:", rebirthAmount)
    else
        print("Invalid input. Please enter a positive number.")
    end
end)


local AutoFarmTab = window:AddTab("Auto Farm")
local AutoWeightToggle = false
local AutoPushupsToggle = false
local SitupsToggle = false
local MuscleKingFarmToggle = false

-- Helper functions for auto actions
local function AutoWeight()
    while AutoWeightToggle do
        local player = game.Players.LocalPlayer
        local weightTool = player.Backpack:FindFirstChild("Weight") or player.Character:FindFirstChild("Weight")
        if weightTool then
            player.Character.Humanoid:EquipTool(weightTool)
            weightTool:Activate()
        end
        wait(0.1)
    end
end

local function AutoPushups()
    while AutoPushupsToggle do
        local player = game.Players.LocalPlayer
        local pushupTool = player.Backpack:FindFirstChild("Pushup") or player.Character:FindFirstChild("Pushup")
        if pushupTool then
            player.Character.Humanoid:EquipTool(pushupTool)
            pushupTool:Activate()
        end
        wait(0.1)
    end
end

local function AutoSitups()
    while SitupsToggle do
        local player = game.Players.LocalPlayer
        local situpTool = player.Backpack:FindFirstChild("Situp") or player.Character:FindFirstChild("Situp")
        if situpTool then
            player.Character.Humanoid:EquipTool(situpTool)
            situpTool:Activate()
        end
        wait(0.1)
    end
end

local function MuscleKingFarm()
    while MuscleKingFarmToggle do
        local player = game.Players.LocalPlayer
        local muscleKingTool = player.Backpack:FindFirstChild("MuscleKing") or player.Character:FindFirstChild("MuscleKing")
        if muscleKingTool then
            player.Character.Humanoid:EquipTool(muscleKingTool)
            muscleKingTool:Activate()
        end
        wait(0.1)
    end
end

AutoFarmTab:AddSwitch("Auto Weight", function(State)
    AutoWeightToggle = State
    if AutoWeightToggle then
        AutoWeight()
    end
end)

AutoFarmTab:AddSwitch("Auto Pushups", function(value)
    AutoPushupsToggle = value
    if AutoPushupsToggle then
        AutoPushups()
    end
end)

AutoFarmTab:AddSwitch("Situps", function(value)
    SitupsToggle = value
    if SitupsToggle then
        AutoSitups()
    end
end)

AutoFarmTab:AddSwitch("Muscle King Farm", function(value)
    MuscleKingFarmToggle = value
    if MuscleKingFarmToggle then
        MuscleKingFarm()
    end
end)



-- View Stats Tab
local ViewStatsTab = window:AddTab("ViewStats")

local playerData = {}
local currentSelectedPlayer = nil
local notFoundLabel = nil
local selectedPlayerName = nil

-- Helper function to abbreviate large numbers
local function abbreviateNumber(value)
    if value >= 1e15 then
        return string.format("%.1fQa", value / 1e15)
    elseif value >= 1e12 then
        return string.format("%.1fT", value / 1e12)
    elseif value >= 1e9 then
        return string.format("%.1fB", value / 1e9)
    elseif value >= 1e6 then
        return string.format("%.1fM", value / 1e6)
    elseif value >= 1e3 then
        return string.format("%.1fK", value / 1e3)
    else
        return tostring(value)
    end
end

-- Function to create labels for the selected player's stats
local function createPlayerLabels(player)
    local playerName = player.Name
    local leaderstats = player:FindFirstChild("leaderstats")
    local equippedPets = player:FindFirstChild("equippedPets")
    local ownedGamepasses = player:FindFirstChild("ownedGamepasses")

    -- Create labels for stats
    local labels = {
        StrengthLabel = ViewStatsTab:AddLabel("Strength: " .. abbreviateNumber(leaderstats.Strength.Value or 0)),
        DurabilityLabel = ViewStatsTab:AddLabel("Durability: " .. abbreviateNumber(player.Durability.Value or 0)),
        KillsLabel = ViewStatsTab:AddLabel("Kills: " .. abbreviateNumber(leaderstats.Kills.Value or 0)),
        BrawlsLabel = ViewStatsTab:AddLabel("Brawls: " .. abbreviateNumber(leaderstats.Brawls.Value or 0)),
        AgilityLabel = ViewStatsTab:AddLabel("Agility: " .. abbreviateNumber(player.Agility.Value or 0)),
        EvilKarmaLabel = ViewStatsTab:AddLabel("evilKarma: " .. abbreviateNumber(player.evilKarma.Value or 0)),
        GoodKarmaLabel = ViewStatsTab:AddLabel("goodKarma: " .. abbreviateNumber(player.goodKarma.Value or 0)),
        MapLabel = ViewStatsTab:AddLabel("Map: " .. (player.currentMap.Value or "N/A")),
        KingTimeLabel = ViewStatsTab:AddLabel("KingTime: " .. abbreviateNumber(player.muscleKingTime.Value or 0)),
        PremiumLabel = ViewStatsTab:AddLabel("Premium: " .. (player.MembershipType == Enum.MembershipType.Premium and "true" or "false")),
    }

    -- Add pet labels
    for i = 1, 5 do
        local petValue = equippedPets:FindFirstChild("pet" .. i) and equippedPets["pet" .. i].Value or "N/A"
        labels["Pet" .. i .. "Label"] = ViewStatsTab:AddLabel("Pet" .. i .. ": " .. tostring(petValue))
    end

    -- Add owned gamepasses
    local gamepassList = {}
    if ownedGamepasses then
        for _, gamepass in ipairs(ownedGamepasses:GetChildren()) do
            table.insert(gamepassList, gamepass.Name)
        end
    end

    local gamepassesText = #gamepassList > 0 and table.concat(gamepassList, ", ") or "N/A"
    labels.GamepassesLabel = ViewStatsTab:AddLabel("ownedGamepasses: " .. gamepassesText)

    playerData[playerName] = labels

    -- Connect value change events to update the labels
    leaderstats.Kills.Changed:Connect(function()
        labels.KillsLabel.Text = "Kills: " .. abbreviateNumber(leaderstats.Kills.Value or 0)
    end)

    leaderstats.Strength.Changed:Connect(function()
        labels.StrengthLabel.Text = "Strength: " .. abbreviateNumber(leaderstats.Strength.Value or 0)
    end)

    leaderstats.Brawls.Changed:Connect(function()
        labels.BrawlsLabel.Text = "Brawls: " .. abbreviateNumber(leaderstats.Brawls.Value or 0)
    end)

    player.Durability.Changed:Connect(function()
        labels.DurabilityLabel.Text = "Durability: " .. abbreviateNumber(player.Durability.Value or 0)
    end)

    player.Agility.Changed:Connect(function()
        labels.AgilityLabel.Text = "Agility: " .. abbreviateNumber(player.Agility.Value or 0)
    end)

    player.evilKarma.Changed:Connect(function()
        labels.EvilKarmaLabel.Text = "evilKarma: " .. abbreviateNumber(player.evilKarma.Value or 0)
    end)

    player.goodKarma.Changed:Connect(function()
        labels.GoodKarmaLabel.Text = "goodKarma: " .. abbreviateNumber(player.goodKarma.Value or 0)
    end)
end

-- Function to remove player labels (cleanup)
local function removePlayerLabels(playerName)
    if playerData[playerName] then
        for _, label in pairs(playerData[playerName]) do
            label:Remove()
        end
        playerData[playerName] = nil
    end
end

-- Adding a textbox for player name input
local textbox = ViewStatsTab:AddTextBox("Player Name", function(playerName)
    selectedPlayerName = playerName
    if notFoundLabel then
        notFoundLabel:Remove()
        notFoundLabel = nil
    end

    local player = game.Players:FindFirstChild(playerName)
    if player then
        if currentSelectedPlayer then
            removePlayerLabels(currentSelectedPlayer)
        end
        createPlayerLabels(player)
        currentSelectedPlayer = playerName
    else
        notFoundLabel = ViewStatsTab:AddLabel("Player not found!")
    end
end)

--The credit tab because yes
local Credittab = window:AddTab("Credit")  -- Adding the "Credit" tab

-- Adding the labels
Credittab:AddLabel("Script Made By Adopt And EpicDeevv")
Credittab:AddLabel("Discord Server: https://discord.gg/ZgDYgKa2")

-- Show the window
window:Show()
