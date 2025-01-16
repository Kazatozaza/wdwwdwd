-- UI Setup
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "MonsterFarmingUI"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 400, 0, 500)
mainFrame.Position = UDim2.new(0.5, -200, 0.5, -250)
mainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
mainFrame.BorderSizePixel = 0
mainFrame.Visible = true
mainFrame.Parent = ScreenGui

local uiCorner = Instance.new("UICorner")
uiCorner.CornerRadius = UDim.new(0, 10)
uiCorner.Parent = mainFrame

local titleLabel = Instance.new("TextLabel")
titleLabel.Size = UDim2.new(1, 0, 0, 50)
titleLabel.Position = UDim2.new(0, 0, 0, 0)
titleLabel.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
titleLabel.Text = "Monster Farming UI"
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.Font = Enum.Font.GothamBold
titleLabel.TextSize = 20
titleLabel.Parent = mainFrame

local monsterDropdown = Instance.new("TextButton")
monsterDropdown.Size = UDim2.new(1, -20, 0, 40)
monsterDropdown.Position = UDim2.new(0, 10, 0, 60)
monsterDropdown.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
monsterDropdown.Text = "Select Monster"
monsterDropdown.TextColor3 = Color3.fromRGB(255, 255, 255)
monsterDropdown.Font = Enum.Font.Gotham
monsterDropdown.TextSize = 18
monsterDropdown.Parent = mainFrame

local combatDropdown = Instance.new("TextButton")
combatDropdown.Size = UDim2.new(1, -20, 0, 40)
combatDropdown.Position = UDim2.new(0, 10, 0, 110)
combatDropdown.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
combatDropdown.Text = "Select Combat Tool"
combatDropdown.TextColor3 = Color3.fromRGB(255, 255, 255)
combatDropdown.Font = Enum.Font.Gotham
combatDropdown.TextSize = 18
combatDropdown.Parent = mainFrame

local startButton = Instance.new("TextButton")
startButton.Size = UDim2.new(1, -20, 0, 40)
startButton.Position = UDim2.new(0, 10, 0, 160)
startButton.BackgroundColor3 = Color3.fromRGB(34, 139, 34)
startButton.Text = "Start Farming"
startButton.TextColor3 = Color3.fromRGB(255, 255, 255)
startButton.Font = Enum.Font.GothamBold
startButton.TextSize = 18
startButton.Parent = mainFrame

local stopButton = Instance.new("TextButton")
stopButton.Size = UDim2.new(1, -20, 0, 40)
stopButton.Position = UDim2.new(0, 10, 0, 210)
stopButton.BackgroundColor3 = Color3.fromRGB(178, 34, 34)
stopButton.Text = "Stop Farming"
stopButton.TextColor3 = Color3.fromRGB(255, 255, 255)
stopButton.Font = Enum.Font.GothamBold
stopButton.TextSize = 18
stopButton.Parent = mainFrame

local logLabel = Instance.new("TextLabel")
logLabel.Size = UDim2.new(1, -20, 0, 100)
logLabel.Position = UDim2.new(0, 10, 0, 260)
logLabel.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
logLabel.Text = "Status: Idle"
logLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
logLabel.TextWrapped = true
logLabel.Font = Enum.Font.Gotham
logLabel.TextSize = 16
logLabel.Parent = mainFrame

-- Add rounded corners to buttons
for _, element in pairs(mainFrame:GetChildren()) do
    if element:IsA("TextButton") or element:IsA("TextLabel") then
        local corner = Instance.new("UICorner")
        corner.CornerRadius = UDim.new(0, 8)
        corner.Parent = element
    end
end

-- Add shadow effect to the main frame
local shadow = Instance.new("Frame")
shadow.Size = UDim2.new(1, 8, 1, 8)
shadow.Position = UDim2.new(0, -4, 0, -4)
shadow.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
shadow.BorderSizePixel = 0
shadow.BackgroundTransparency = 0.7
shadow.ZIndex = -1
shadow.Parent = mainFrame
local shadowCorner = Instance.new("UICorner")
shadowCorner.CornerRadius = UDim.new(0, 10)
shadowCorner.Parent = shadow

-- Variables
local autoFarming = false
local selectedMonster = nil
local selectedCombat = nil
local monsters = {
    "Bandit [Lv.1]",
    "Asta [Lv.450]",
    "Bandit Boss [Lv.25]",
    "Do [Lv.225]",
    "Kraken [Lv.100]",
    "Kung [Lv.700]",
    "Savage [Lv.150]",
    "Shadow [Lv.450]",
    "Shadow God [Lv.500]",
    "Wade [Lv.400]"
}

-- Dropdown for selecting monster
monsterDropdown.MouseButton1Click:Connect(function()
    local dropdownFrame = Instance.new("Frame")
    dropdownFrame.Size = UDim2.new(1, 0, 1, 0)
    dropdownFrame.Position = UDim2.new(0, 0, 0, 0)
    dropdownFrame.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    dropdownFrame.Parent = mainFrame

    for i, monster in pairs(monsters) do
        local monsterButton = Instance.new("TextButton")
        monsterButton.Size = UDim2.new(1, -20, 0, 30)
        monsterButton.Position = UDim2.new(0, 10, 0, (i - 1) * 35)
        monsterButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
        monsterButton.Text = monster
        monsterButton.TextColor3 = Color3.fromRGB(255, 255, 255)
        monsterButton.Font = Enum.Font.SourceSans
        monsterButton.TextSize = 18
        monsterButton.Parent = dropdownFrame

        monsterButton.MouseButton1Click:Connect(function()
            selectedMonster = monster
            monsterDropdown.Text = "Selected: " .. monster
            dropdownFrame:Destroy()
        end)
    end
end)

-- Dropdown for selecting combat tool
combatDropdown.MouseButton1Click:Connect(function()
    local dropdownFrame = Instance.new("Frame")
    dropdownFrame.Size = UDim2.new(1, 0, 1, 0)
    dropdownFrame.Position = UDim2.new(0, 0, 0, 0)
    dropdownFrame.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    dropdownFrame.Parent = mainFrame

    local tools = game.Players.LocalPlayer.Backpack:GetChildren()
    for i, tool in pairs(tools) do
        if tool:IsA("Tool") then
            local toolButton = Instance.new("TextButton")
            toolButton.Size = UDim2.new(1, -20, 0, 30)
            toolButton.Position = UDim2.new(0, 10, 0, (i - 1) * 35)
            toolButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
            toolButton.Text = tool.Name
            toolButton.TextColor3 = Color3.fromRGB(255, 255, 255)
            toolButton.Font = Enum.Font.SourceSans
            toolButton.TextSize = 18
            toolButton.Parent = dropdownFrame

            toolButton.MouseButton1Click:Connect(function()
                selectedCombat = tool.Name
                combatDropdown.Text = "Selected: " .. tool.Name
                dropdownFrame:Destroy()
            end)
        end
    end
end)

-- Move to the monster and face it
function moveToMonster(monsterName)
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")

    for _, obj in pairs(game:GetDescendants()) do
        if obj:IsA("Model") and obj:FindFirstChild("Humanoid") and obj.Name == monsterName then
            local monsterHRP = obj:FindFirstChild("HumanoidRootPart")
            if monsterHRP then
                humanoidRootPart.CFrame = monsterHRP.CFrame + Vector3.new(0, 5, -5)
                character:SetPrimaryPartCFrame(CFrame.lookAt(humanoidRootPart.Position, monsterHRP.Position))
                return true
            end
        end
    end
    return false
end

-- Attack function
function attackMonster(monsterName)
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local tool = player.Backpack:FindFirstChild(selectedCombat)
    if tool then
        tool.Parent = character
        for _, obj in pairs(game:GetDescendants()) do
            if obj:IsA("Model") and obj.Name == monsterName and obj:FindFirstChild("Humanoid") then
                character:MoveTo(obj.HumanoidRootPart.Position)
                character:WaitForChild("Humanoid").Died:Wait()
                break
            end
        end
    end
end

-- Farming logic
local function startFarming()
    autoFarming = true
    logLabel.Text = "Status: Farming..."
    while autoFarming do
        if selectedMonster and selectedCombat then
            if moveToMonster(selectedMonster) then
                attackMonster(selectedMonster)
            end
        end
        task.wait(0.5)
    end
end

local function stopFarming()
    autoFarming = false
    logLabel.Text = "Status: Idle"
end

-- Button event handlers
startButton.MouseButton1Click:Connect(function()
    if not autoFarming then
        startFarming()
    end
end)

stopButton.MouseButton1Click:Connect(function()
    stopFarming()
end)
