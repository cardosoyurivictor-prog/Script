--[[
    Classic Football Hub - Mobile Optimized UI
    Professional football interface with image background
]]

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer
local mouse = player:GetMouse()

-- Create ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ClassicFootballHub"
screenGui.ResetOnSpawn = false
screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
screenGui.Parent = player:WaitForChild("PlayerGui")

-- Main Frame (Draggable, Compact for Mobile)
local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 340, 0, 480)
mainFrame.Position = UDim2.new(0.5, -170, 0.5, -240)
mainFrame.BackgroundColor3 = Color3.fromRGB(20, 22, 30)
mainFrame.BackgroundTransparency = 0.1
mainFrame.BorderSizePixel = 0
mainFrame.ClipsDescendants = true
mainFrame.Parent = screenGui

-- Corner for main frame
local mainCorner = Instance.new("UICorner")
mainCorner.CornerRadius = UDim.new(0, 20)
mainCorner.Parent = mainFrame

-- Shadow/Glow effect
local shadow = Instance.new("ImageLabel")
shadow.Name = "Shadow"
shadow.Size = UDim2.new(1, 10, 1, 10)
shadow.Position = UDim2.new(0, -5, 0, -5)
shadow.BackgroundTransparency = 1
shadow.Image = "rbxassetid://1316045217"
shadow.ImageColor3 = Color3.fromRGB(0, 0, 0)
shadow.ImageTransparency = 0.5
shadow.ZIndex = 0
shadow.Parent = mainFrame

-- Background Image (User's uploaded photo)
local backgroundImage = Instance.new("ImageLabel")
backgroundImage.Name = "BackgroundImage"
backgroundImage.Size = UDim2.new(1, 0, 1, 0)
backgroundImage.Position = UDim2.new(0, 0, 0, 0)
backgroundImage.BackgroundTransparency = 1
backgroundImage.Image = "rbxassetid://YOUR_IMAGE_ID" -- Replace with your image ID
backgroundImage.ScaleType = Enum.ScaleType.Crop
backgroundImage.ZIndex = 1
backgroundImage.Parent = mainFrame

-- Overlay for readability
local overlay = Instance.new("Frame")
overlay.Name = "Overlay"
overlay.Size = UDim2.new(1, 0, 1, 0)
overlay.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
overlay.BackgroundTransparency = 0.5
overlay.BorderSizePixel = 0
overlay.ZIndex = 2
overlay.Parent = mainFrame

-- Header Section
local headerFrame = Instance.new("Frame")
headerFrame.Name = "HeaderFrame"
headerFrame.Size = UDim2.new(1, 0, 0, 55)
headerFrame.BackgroundColor3 = Color3.fromRGB(10, 12, 18)
headerFrame.BackgroundTransparency = 0.3
headerFrame.BorderSizePixel = 0
headerFrame.ZIndex = 3
headerFrame.Parent = mainFrame

local headerCorner = Instance.new("UICorner")
headerCorner.CornerRadius = UDim.new(0, 20)
headerCorner.Parent = headerFrame

-- Title with Football Icon
local titleLabel = Instance.new("TextLabel")
titleLabel.Name = "TitleLabel"
titleLabel.Size = UDim2.new(0.7, 0, 1, 0)
titleLabel.Position = UDim2.new(0.05, 0, 0, 0)
titleLabel.BackgroundTransparency = 1
titleLabel.Text = "⚽ CLASSIC FOOTBALL HUB"
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.TextSize = 16
titleLabel.TextXAlignment = Enum.TextXAlignment.Left
titleLabel.Font = Enum.Font.GothamBold
titleLabel.ZIndex = 4
titleLabel.Parent = headerFrame

-- Close Button
local closeButton = Instance.new("TextButton")
closeButton.Name = "CloseButton"
closeButton.Size = UDim2.new(0, 30, 0, 30)
closeButton.Position = UDim2.new(0.92, 0, 0.5, -15)
closeButton.BackgroundColor3 = Color3.fromRGB(255, 70, 70)
closeButton.BackgroundTransparency = 0.2
closeButton.Text = "✕"
closeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
closeButton.TextSize = 16
closeButton.Font = Enum.Font.GothamBold
closeButton.BorderSizePixel = 0
closeButton.ZIndex = 4
closeButton.Parent = headerFrame

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(1, 0)
closeCorner.Parent = closeButton

-- Minimize Button
local minimizeButton = Instance.new("TextButton")
minimizeButton.Name = "MinimizeButton"
minimizeButton.Size = UDim2.new(0, 30, 0, 30)
minimizeButton.Position = UDim2.new(0.82, 0, 0.5, -15)
minimizeButton.BackgroundColor3 = Color3.fromRGB(255, 200, 50)
minimizeButton.BackgroundTransparency = 0.2
minimizeButton.Text = "−"
minimizeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
minimizeButton.TextSize = 20
minimizeButton.Font = Enum.Font.GothamBold
minimizeButton.BorderSizePixel = 0
minimizeButton.ZIndex = 4
minimizeButton.Parent = headerFrame

local minimizeCorner = Instance.new("UICorner")
minimizeCorner.CornerRadius = UDim.new(1, 0)
minimizeCorner.Parent = minimizeButton

-- Content Frame
local contentFrame = Instance.new("Frame")
contentFrame.Name = "ContentFrame"
contentFrame.Size = UDim2.new(1, -20, 1, -75)
contentFrame.Position = UDim2.new(0, 10, 0, 65)
contentFrame.BackgroundTransparency = 1
contentFrame.ZIndex = 3
contentFrame.Parent = mainFrame

-- "Seguir Bola" Button
local followBallButton = Instance.new("TextButton")
followBallButton.Name = "FollowBallButton"
followBallButton.Size = UDim2.new(1, 0, 0, 55)
followBallButton.Position = UDim2.new(0, 0, 0, 0)
followBallButton.BackgroundColor3 = Color3.fromRGB(50, 120, 255)
followBallButton.BackgroundTransparency = 0.15
followBallButton.Text = "⚽ SEGUIR BOLA"
followBallButton.TextColor3 = Color3.fromRGB(255, 255, 255)
followBallButton.TextSize = 16
followBallButton.Font = Enum.Font.GothamBold
followBallButton.BorderSizePixel = 0
followBallButton.ZIndex = 4
followBallButton.Parent = contentFrame

local followCorner = Instance.new("UICorner")
followCorner.CornerRadius = UDim.new(0, 12)
followCorner.Parent = followBallButton

-- Follow Ball Indicator
local followIndicator = Instance.new("Frame")
followIndicator.Name = "FollowIndicator"
followIndicator.Size = UDim2.new(0, 8, 0, 8)
followIndicator.Position = UDim2.new(0.02, 0, 0.5, -4)
followIndicator.BackgroundColor3 = Color3.fromRGB(0, 255, 100)
followIndicator.BackgroundTransparency = 1
followIndicator.BorderSizePixel = 0
followIndicator.ZIndex = 5
followIndicator.Parent = followBallButton

local indicatorCorner = Instance.new("UICorner")
indicatorCorner.CornerRadius = UDim.new(1, 0)
indicatorCorner.Parent = followIndicator

-- "Reach" Section Frame
local reachFrame = Instance.new("Frame")
reachFrame.Name = "ReachFrame"
reachFrame.Size = UDim2.new(1, 0, 0, 100)
reachFrame.Position = UDim2.new(0, 0, 0, 75)
reachFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
reachFrame.BackgroundTransparency = 0.15
reachFrame.BorderSizePixel = 0
reachFrame.ZIndex = 4
reachFrame.Parent = contentFrame

local reachCorner = Instance.new("UICorner")
reachCorner.CornerRadius = UDim.new(0, 12)
reachCorner.Parent = reachFrame

-- Reach Button
local reachButton = Instance.new("TextButton")
reachButton.Name = "ReachButton"
reachButton.Size = UDim2.new(0.45, -5, 0, 40)
reachButton.Position = UDim2.new(0.02, 0, 0.1, 0)
reachButton.BackgroundColor3 = Color3.fromRGB(255, 180, 50)
reachButton.BackgroundTransparency = 0.15
reachButton.Text = "🦶 REACH"
reachButton.TextColor3 = Color3.fromRGB(255, 255, 255)
reachButton.TextSize = 14
reachButton.Font = Enum.Font.GothamBold
reachButton.BorderSizePixel = 0
reachButton.ZIndex = 5
reachButton.Parent = reachFrame

local reachCornerBtn = Instance.new("UICorner")
reachCornerBtn.CornerRadius = UDim.new(0, 10)
reachCornerBtn.Parent = reachButton

-- Reach Indicator
local reachIndicator = Instance.new("Frame")
reachIndicator.Name = "ReachIndicator"
reachIndicator.Size = UDim2.new(0, 8, 0, 8)
reachIndicator.Position = UDim2.new(0.03, 0, 0.5, -4)
reachIndicator.BackgroundColor3 = Color3.fromRGB(0, 255, 100)
reachIndicator.BackgroundTransparency = 1
reachIndicator.BorderSizePixel = 0
reachIndicator.ZIndex = 6
reachIndicator.Parent = reachButton

local reachIndCorner = Instance.new("UICorner")
reachIndCorner.CornerRadius = UDim.new(1, 0)
reachIndCorner.Parent = reachIndicator

-- Reach Slider
local reachSlider = Instance.new("Frame")
reachSlider.Name = "ReachSlider"
reachSlider.Size = UDim2.new(0.48, -5, 0, 35)
reachSlider.Position = UDim2.new(0.50, 0, 0.1, 0)
reachSlider.BackgroundColor3 = Color3.fromRGB(40, 42, 55)
reachSlider.BackgroundTransparency = 0.3
reachSlider.BorderSizePixel = 0
reachSlider.ZIndex = 5
reachSlider.Parent = reachFrame

local sliderCorner = Instance.new("UICorner")
sliderCorner.CornerRadius = UDim.new(0, 10)
sliderCorner.Parent = reachSlider

-- Slider Track
local sliderTrack = Instance.new("Frame")
sliderTrack.Name = "SliderTrack"
sliderTrack.Size = UDim2.new(0.85, 0, 0.2, 0)
sliderTrack.Position = UDim2.new(0.075, 0, 0.4, 0)
sliderTrack.BackgroundColor3 = Color3.fromRGB(80, 80, 100)
sliderTrack.BorderSizePixel = 0
sliderTrack.ZIndex = 6
sliderTrack.Parent = reachSlider

local trackCorner = Instance.new("UICorner")
trackCorner.CornerRadius = UDim.new(0, 4)
trackCorner.Parent = sliderTrack

-- Slider Fill
local sliderFill = Instance.new("Frame")
sliderFill.Name = "SliderFill"
sliderFill.Size = UDim2.new(0.5, 0, 1, 0)
sliderFill.Position = UDim2.new(0, 0, 0, 0)
sliderFill.BackgroundColor3 = Color3.fromRGB(255, 180, 50)
sliderFill.BorderSizePixel = 0
sliderFill.ZIndex = 7
sliderFill.Parent = sliderTrack

local fillCorner = Instance.new("UICorner")
fillCorner.CornerRadius = UDim.new(0, 4)
fillCorner.Parent = sliderFill

-- Slider Button
local sliderButton = Instance.new("TextButton")
sliderButton.Name = "SliderButton"
sliderButton.Size = UDim2.new(0, 18, 0, 18)
sliderButton.Position = UDim2.new(0.5, -9, 0.5, -9)
sliderButton.BackgroundColor3 = Color3.fromRGB(255, 200, 80)
sliderButton.Text = ""
sliderButton.BorderSizePixel = 0
sliderButton.ZIndex = 8
sliderButton.Parent = sliderTrack

local sliderBtnCorner = Instance.new("UICorner")
sliderBtnCorner.CornerRadius = UDim.new(1, 0)
sliderBtnCorner.Parent = sliderButton

-- Reach Value Label
local reachValueLabel = Instance.new("TextLabel")
reachValueLabel.Name = "ReachValueLabel"
reachValueLabel.Size = UDim2.new(0.85, 0, 0.3, 0)
reachValueLabel.Position = UDim2.new(0.075, 0, 0.65, 0)
reachValueLabel.BackgroundTransparency = 1
reachValueLabel.Text = "50%"
reachValueLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
reachValueLabel.TextSize = 12
reachValueLabel.Font = Enum.Font.Gotham
reachValueLabel.ZIndex = 6
reachValueLabel.Parent = reachSlider

-- Status Bar (Bottom)
local statusBar = Instance.new("Frame")
statusBar.Name = "StatusBar"
statusBar.Size = UDim2.new(1, 0, 0, 30)
statusBar.Position = UDim2.new(0, 0, 1, -30)
statusBar.BackgroundColor3 = Color3.fromRGB(10, 12, 18)
statusBar.BackgroundTransparency = 0.3
statusBar.BorderSizePixel = 0
statusBar.ZIndex = 3
statusBar.Parent = mainFrame

local statusCorner = Instance.new("UICorner")
statusCorner.CornerRadius = UDim.new(0, 12)
statusCorner.Parent = statusBar

local statusLabel = Instance.new("TextLabel")
statusLabel.Name = "StatusLabel"
statusLabel.Size = UDim2.new(1, -10, 1, 0)
statusLabel.Position = UDim2.new(0, 5, 0, 0)
statusLabel.BackgroundTransparency = 1
statusLabel.Text = "✅ Sistema pronto"
statusLabel.TextColor3 = Color3.fromRGB(150, 200, 150)
statusLabel.TextSize = 11
statusLabel.Font = Enum.Font.Gotham
statusLabel.ZIndex = 4
statusLabel.Parent = statusBar

-- Variables
local isFollowing = false
local isReachActive = false
local reachValue = 50
local isMinimized = false
local isDragging = false
local dragStart = nil
local dragStartPos = nil

-- Functions
local function updateStatus(text, color)
    statusLabel.Text = text
    statusLabel.TextColor3 = color or Color3.fromRGB(150, 200, 150)
end

local function toggleFollow()
    isFollowing = not isFollowing
    if isFollowing then
        followIndicator.BackgroundTransparency = 0
        followBallButton.BackgroundColor3 = Color3.fromRGB(50, 200, 100)
        updateStatus("⚽ Seguindo a bola...", Color3.fromRGB(100, 255, 150))
        -- Start following logic
    else
        followIndicator.BackgroundTransparency = 1
        followBallButton.BackgroundColor3 = Color3.fromRGB(50, 120, 255)
        updateStatus("✅ Seguimento desativado", Color3.fromRGB(150, 200, 150))
    end
end

local function toggleReach()
    isReachActive = not isReachActive
    if isReachActive then
        reachIndicator.BackgroundTransparency = 0
        reachButton.BackgroundColor3 = Color3.fromRGB(255, 200, 80)
        updateStatus("🦶 Reach ativado: " .. reachValue .. "%", Color3.fromRGB(255, 200, 100))
    else
        reachIndicator.BackgroundTransparency = 1
        reachButton.BackgroundColor3 = Color3.fromRGB(255, 180, 50)
        updateStatus("✅ Reach desativado", Color3.fromRGB(150, 200, 150))
    end
end

local function updateSlider(input)
    local trackSize = sliderTrack.AbsoluteSize.X
    local pos = math.clamp(input.Position.X - sliderTrack.AbsolutePosition.X, 0, trackSize)
    local percent = math.clamp(pos / trackSize, 0, 1)
    reachValue = math.round(percent * 100)
    sliderFill.Size = UDim2.new(percent, 0, 1, 0)
    sliderButton.Position = UDim2.new(percent, -9, 0.5, -9)
    reachValueLabel.Text = reachValue .. "%"
    if isReachActive then
        updateStatus("🦶 Reach: " .. reachValue .. "%", Color3.fromRGB(255, 200, 100))
    end
end

-- Button Connections
followBallButton.MouseButton1Click:Connect(toggleFollow)

reachButton.MouseButton1Click:Connect(toggleReach)

-- Slider Input
sliderButton.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
        updateSlider(input)
    end
end)

sliderButton.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseMovement then
        if UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) or 
           UserInputService:IsTouchEnabled() then
            updateSlider(input)
        end
    end
end)

-- Mobile Touch Drag for Slider
sliderTrack.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch then
        updateSlider(input)
    end
end)

sliderTrack.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch then
        updateSlider(input)
    end
end)

-- Minimize/Restore
local function toggleMinimize()
    isMinimized = not isMinimized
    if isMinimized then
        mainFrame:TweenSize(UDim2.new(0, 340, 0, 55), "Out", "Quad", 0.3, true)
        contentFrame.Visible = false
        statusBar.Visible = false
        minimizeButton.Text = "+"
    else
        mainFrame:TweenSize(UDim2.new(0, 340, 0, 480), "Out", "Quad", 0.3, true)
        contentFrame.Visible = true
        statusBar.Visible = true
        minimizeButton.Text = "−"
    end
end

minimizeButton.MouseButton1Click:Connect(toggleMinimize)

-- Close Button
closeButton.MouseButton1Click:Connect(function()
    screenGui:Destroy()
end)

-- Dragging System
mainFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        if input.Position.Y < headerFrame.AbsoluteSize.Y then
            isDragging = true
            dragStart = input.Position
            dragStartPos = mainFrame.Position
        end
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if isDragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
        local delta = input.Position - dragStart
        mainFrame.Position = UDim2.new(
            dragStartPos.X.Scale,
            dragStartPos.X.Offset + delta.X,
            dragStartPos.Y.Scale,
            dragStartPos.Y.Offset + delta.Y
        )
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        isDragging = false
    end
end)

-- Optimize for mobile
if UserInputService.TouchEnabled then
    -- Make buttons larger for touch
    followBallButton.Size = UDim2.new(1, 0, 0, 65)
    reachFrame.Size = UDim2.new(1, 0, 0, 120)
    reachButton.Size = UDim2.new(0.5, -5, 0, 50)
    reachSlider.Size = UDim2.new(0.45, -5, 0, 45)
    titleLabel.TextSize = 14
    mainFrame.Size = UDim2.new(0, 360, 0, 520)
    mainFrame.Position = UDim2.new(0.5, -180, 0.5, -260)
end

-- Animation on hover (for PC)
if not UserInputService.TouchEnabled then
    followBallButton.MouseEnter:Connect(function()
        TweenService:Create(followBallButton, TweenInfo.new(0.2), {BackgroundTransparency = 0.05}):Play()
    end)
    followBallButton.MouseLeave:Connect(function()
        TweenService:Create(followBallButton, TweenInfo.new(0.2), {BackgroundTransparency = 0.15}):Play()
    end)
    
    reachButton.MouseEnter:Connect(function()
        TweenService:Create(reachButton, TweenInfo.new(0.2), {BackgroundTransparency = 0.05}):Play()
    end)
    reachButton.MouseLeave:Connect(function()
        TweenService:Create(reachButton, TweenInfo.new(0.2), {BackgroundTransparency = 0.15}):Play()
    end)
end

print("⚽ Classic Football Hub loaded successfully!")
