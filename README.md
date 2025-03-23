-- 创建主GUI
local main = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local increaseButton = Instance.new("TextButton")
local decreaseButton = Instance.new("TextButton")
local speedLabel = Instance.new("TextLabel")
local authorLabel = Instance.new("TextLabel") -- 新增作者标签

-- 设置主GUI属性
main.Name = "SpeedModifier"
main.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
main.ResetOnSpawn = false

-- 设置框架属性
Frame.Parent = main
Frame.BackgroundColor3 = Color3.fromRGB(163, 255, 137)
Frame.BorderColor3 = Color3.fromRGB(103, 221, 213)
Frame.Position = UDim2.new(0.100320168, 0, 0.379746825, 0)
Frame.Size = UDim2.new(0, 190, 0, 110) -- 增加高度以容纳作者标签

-- 设置增加速度按钮
increaseButton.Name = "IncreaseSpeed"
increaseButton.Parent = Frame
increaseButton.BackgroundColor3 = Color3.fromRGB(79, 255, 152)
increaseButton.Position = UDim2.new(0, 0, 0, 0)
increaseButton.Size = UDim2.new(0, 90, 0, 30)
increaseButton.Font = Enum.Font.SourceSans
increaseButton.Text = "+"
increaseButton.TextColor3 = Color3.fromRGB(0, 0, 0)
increaseButton.TextSize = 14.000

-- 设置减少速度按钮
decreaseButton.Name = "DecreaseSpeed"
decreaseButton.Parent = Frame
decreaseButton.BackgroundColor3 = Color3.fromRGB(215, 255, 121)
decreaseButton.Position = UDim2.new(0, 95, 0, 0)
decreaseButton.Size = UDim2.new(0, 90, 0, 30)
decreaseButton.Font = Enum.Font.SourceSans
decreaseButton.Text = "-"
decreaseButton.TextColor3 = Color3.fromRGB(0, 0, 0)
decreaseButton.TextSize = 14.000

-- 设置速度标签
speedLabel.Name = "SpeedLabel"
speedLabel.Parent = Frame
speedLabel.BackgroundColor3 = Color3.fromRGB(242, 60, 255)
speedLabel.Position = UDim2.new(0, 0, 0.5, 0)
speedLabel.Size = UDim2.new(0, 190, 0, 30)
speedLabel.Font = Enum.Font.SourceSans
speedLabel.Text = "Speed: 16"
speedLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
speedLabel.TextSize = 14.000

-- 设置作者标签
authorLabel.Name = "AuthorLabel"
authorLabel.Parent = Frame
authorLabel.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
authorLabel.Position = UDim2.new(0, 0, 0.7, 0)
authorLabel.Size = UDim2.new(0, 190, 0, 30)
authorLabel.Font = Enum.Font.SourceSans
authorLabel.Text = "LJW作"
authorLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
authorLabel.TextSize = 14.000

-- 初始化速度
local currentSpeed = 16

-- 更新速度标签
local function updateSpeedLabel()
    speedLabel.Text = "Speed: " .. tostring(currentSpeed)
end

-- 增加速度
increaseButton.MouseButton1Click:Connect(function()
    currentSpeed = currentSpeed + 4
    if currentSpeed > 100 then
        currentSpeed = 100
    end
    updateSpeedLabel()
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = currentSpeed
end)

-- 减少速度
decreaseButton.MouseButton1Click:Connect(function()
    currentSpeed = currentSpeed - 4
    if currentSpeed < 4 then
        currentSpeed = 4
    end
    updateSpeedLabel()
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = currentSpeed
end)

-- 初始化速度
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = currentSpeed
updateSpeedLabel()# -
