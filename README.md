# Panic-Button
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Create the ScreenGui
local panicGui = Instance.new("ScreenGui")
panicGui.Name = "PanicSystem"
panicGui.Parent = playerGui
panicGui.ResetOnSpawn = false

-- Create the "LEAVE!" Button
local leaveButton = Instance.new("TextButton")
leaveButton.Name = "LeaveButton"
-- Positioned even higher (55) to sit right under the top menu
leaveButton.Position = UDim2.new(0, 50, 0, 55) 
leaveButton.Size = UDim2.new(0, 100, 0, 35)
leaveButton.BorderSizePixel = 0
leaveButton.Text = "LEAVE!"
leaveButton.TextColor3 = Color3.fromRGB(255, 255, 255)
leaveButton.Font = Enum.Font.GothamBold
leaveButton.TextSize = 16
leaveButton.Parent = panicGui

-- Add rounded corners
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 8)
corner.Parent = leaveButton

-- THE KICK FUNCTION WITH CUSTOM MESSAGE
leaveButton.MouseButton1Click:Connect(function()
    player:Kick("Instantly Left")
end)

-- THE RGB LOOP
RunService.RenderStepped:Connect(function()
    local hue = tick() % 5 / 5 
    leaveButton.BackgroundColor3 = Color3.fromHSV(hue, 0.8, 1)
end)

