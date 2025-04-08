local player = game.Players.LocalPlayer

local function ShowPopup(title, message)
    local screenGui = Instance.new("ScreenGui")
    screenGui.Name = "ErrorPopup"
    screenGui.ResetOnSpawn = false
    screenGui.Parent = player:WaitForChild("PlayerGui")

    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(0.3, 0, 0.2, 0)
    frame.Position = UDim2.new(0.35, 0, 0.4, 0)
    frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    frame.BorderSizePixel = 0
    frame.Parent = screenGui

    local titleLabel = Instance.new("TextLabel")
    titleLabel.Size = UDim2.new(1, 0, 0.3, 0)
    titleLabel.Text = title
    titleLabel.TextColor3 = Color3.new(1, 0.2, 0.2)
    titleLabel.TextScaled = true
    titleLabel.Font = Enum.Font.SourceSansBold
    titleLabel.BackgroundTransparency = 1
    titleLabel.Parent = frame

    local messageLabel = Instance.new("TextLabel")
    messageLabel.Size = UDim2.new(1, -20, 0.5, 0)
    messageLabel.Position = UDim2.new(0, 10, 0.35, 0)
    messageLabel.Text = message
    messageLabel.TextColor3 = Color3.new(1, 1, 1)
    messageLabel.TextScaled = true
    messageLabel.Font = Enum.Font.SourceSans
    messageLabel.BackgroundTransparency = 1
    messageLabel.TextWrapped = true
    messageLabel.Parent = frame

    -- 🔊 เพิ่มเสียงแจ้งเตือน
    local sound = Instance.new("Sound")
    sound.SoundId = "rbxassetid://138186576" -- เสียง Beep หรือ Ping (เปลี่ยนได้)
    sound.Volume = 100
    sound.PlayOnRemove = false
    sound.Parent = screenGui
    sound:Play()
    
    delay(3, function()
        screenGui:Destroy()
    end)
end



local KeySystem = loadstring(game:HttpGet("https://raw.githubusercontent.com/OopssSorry/LuaU-Free-Key-System-UI/main/source.lua"))()
local KeyValid = false
local response = KeySystem:Init({
	Debug=false, -- <bool> Prints some output in console when true
	Title="Key Pro is Kuy", -- <string or nil> Title of key system
	Description=nil, -- <string or nil> Description of key system
	Link="https://discord.gg/5Cb8DB3sAV", -- <string> String to get key
	Discord="https://discord.gg/5Cb8DB3sAV ก็อบวาง", -- <string or nil> Button to join your discord server
	SaveKey=false, -- <bool or nil> Just auto save key
	Verify = function(key)
    local player = game.Players.LocalPlayer
    if key == "X8AZSe9neL1Bo" then
        KeyValid = true
        ShowPopup("✅ เข้าสู่ระบบสำเร็จ", "ยินดีต้อนรับ, " .. player.Name .. "!")
        return true
    else
        ShowPopup("❌ รหัสไม่ถูกต้อง", "กรุณาตรวจสอบรหัสแล้วลองใหม่อีกครั้ง")
        return false
    end
end,

	GuiParent = game.CoreGui, -- <object or nil> :3
})

if not response or not KeyValid then return end
loadstring(game:HttpGet("https://raw.githubusercontent.com/konncott/Chiriw-Settings/refs/heads/main/Chiriw-Settings",true))()
