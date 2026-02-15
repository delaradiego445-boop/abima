-- ==============================
-- SERVIÇOS
-- ==============================
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local backpack = player:WaitForChild("Backpack")

if not player.Character then
	player.CharacterAdded:Wait()
end

-- ==============================
-- GUI
-- ==============================
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "PegarItensGUI"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = player:WaitForChild("PlayerGui")

local Frame = Instance.new("Frame")
Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0, 280, 0, 160)
Frame.Position = UDim2.new(0.35, 0, 0.4, 0)
Frame.BackgroundColor3 = Color3.fromRGB(25,25,25)
Frame.BorderSizePixel = 0
Frame.Active = true
Frame.Draggable = true

-- 🔵 Arredondar Frame
local FrameCorner = Instance.new("UICorner")
FrameCorner.CornerRadius = UDim.new(0, 35)
FrameCorner.Parent = Frame

local Title = Instance.new("TextLabel")
Title.Parent = Frame
Title.Size = UDim2.new(1,0,0,40)
Title.BackgroundTransparency = 1
Title.Text = "ego+aura🥶"
Title.TextScaled = true
Title.TextColor3 = Color3.fromRGB(0,170,255)
Title.Font = Enum.Font.GothamBold

local Button = Instance.new("TextButton")
Button.Parent = Frame
Button.Size = UDim2.new(0.7,0,0.45,0)
Button.Position = UDim2.new(0.15,0,0.4,0)
Button.Text = "crash player"
Button.TextScaled = true
Button.BackgroundColor3 = Color3.fromRGB(0,170,255)
Button.TextColor3 = Color3.new(1,1,1)
Button.Font = Enum.Font.GothamBold
Button.BorderSizePixel = 0

-- 🔵 Arredondar Botão
local ButtonCorner = Instance.new("UICorner")
ButtonCorner.CornerRadius = UDim.new(0, 18)
ButtonCorner.Parent = Button

-- ==============================
-- FUNÇÃO
-- ==============================
local function executar()
	local character = player.Character
	if not character then return end

	local cloner = backpack:FindFirstChild("Quantum Cloner")
	if cloner then
		cloner.Parent = character
		cloner:Activate()
	end

	for _, tool in ipairs(backpack:GetChildren()) do
		if tool:IsA("Tool") and tool.Name ~= "Quantum Cloner" then
			tool.Parent = character
		end
	end
end

Button.MouseButton1Click:Connect(function()
	executar()
end)

local function executar()
	local character = player.Character
	if not character then return end

	-- Usar Quantum Cloner
	local cloner = backpack:FindFirstChild("Quantum Cloner")
	if cloner then
		cloner.Parent = character
		cloner:Activate()
	end

	-- Equipar itens de forma leve
	task.spawn(function()
		for _, tool in ipairs(backpack:GetChildren()) do
			if tool:IsA("Tool") and tool.Name ~= "Quantum Cloner" then
				tool.Parent = character
				task.wait(0.01) -- micro delay leve
			end
		end
	end)
end
