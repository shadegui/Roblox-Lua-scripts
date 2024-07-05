# Roblox-Lua-scripts
Showcasing roblox lua scripts function for game development

--Blur and black for tweening--
-
local BlurEffect = Instance.new("BlurEffect")
BlurEffect.Size = 0
BlurEffect.Parent = game.Lighting
local tweenService = game:GetService("TweenService")
local Black = tweenService:Create(script.Parent:WaitForChild("Black") ,TweenInfo.new(2, 
	Enum.EasingStyle.Linear,
	Enum.EasingDirection.Out),
	{Transparency = 0})
local UnBlack = tweenService:Create(script.Parent:WaitForChild("Black") ,TweenInfo.new(2, 
	Enum.EasingStyle.Linear,
	Enum.EasingDirection.Out),
	{Transparency = 1})
local Blur = tweenService:Create(BlurEffect ,TweenInfo.new(2, 
	Enum.EasingStyle.Linear,
	Enum.EasingDirection.Out),
	{Size = 20})
local UnBlur = tweenService:Create(BlurEffect ,TweenInfo.new(1, 
	Enum.EasingStyle.Linear,
	Enum.EasingDirection.Out),
	{Size = 0})


--open inventory inv when key e pressed
-
-- (References to Interface Element)
local backpackGui = script.Parent
local inventoryFrame = backpackGui:WaitForChild("InventoryFrame")

-- make the inv invisible
inventoryFrame.Visble = false

-- feature to show/hide inv
local function toggleInventory()
	inventoryFrame.Visble = not inventoryFrame.Visible
	end
end

--event to detect when key is pressed
local userInputService = game:GetService("UserInputService")

userInputService.InputBegan:Connect(function(input, gameProcessed)
	--Checks if key pressed is "E and if it is not processed by the game
	if input.KeyCode == Enum.KeyCode.E and not gameProcessed then
		toggleInventory()
	end
end)

-- (Event to detect whether you are interacting with the inventory)
userInputService.InputBegan:Connect(function(input, gameProcessed)
	if inventoryFrame.Visible and input.UserInputType == Enum.UserInputType.MouseButton1 then
		gameProcessed = true
	end
end)

------------------------------------------
--updated press e to open inventory, with tween and effect
-

--(References to Interface Element)
local backpackGui = script.Parent
local inventoryFrame = backpackGui:WaitForChild("InventoryFrame")
local profile = script.Parent.Parent.ProfileUI.Canvas
local ability = script.Parent.Parent.AbilityUI.Canvas

local visible = false
local BlurEffect = Instance.new("BlurEffect")
BlurEffect.Size = 0
BlurEffect.Parent = game.Lighting
local tweenService = game:GetService("TweenService")
local Blur = tweenService:Create(BlurEffect ,TweenInfo.new(1, 
	Enum.EasingStyle.Linear,
	Enum.EasingDirection.Out),
	{Size = 20})
local UnBlur = tweenService:Create(BlurEffect ,TweenInfo.new(1, 
	Enum.EasingStyle.Linear,
	Enum.EasingDirection.Out),
	{Size = 0})

-- (make the inv invisible)
inventoryFrame.Size = UDim2.new(0,0,0,0)
inventoryFrame.Position = UDim2.new(1.5,0,0.5,0)

-- (feature to show/hide inv)
local function toggleInventory()
	if visible == false then
		visible = true
		inventoryFrame:TweenSizeAndPosition(UDim2.new(0.919, 0, 0.87, 0), UDim2.new(0.04, 0, 0.019, 0), "Out", "Quad", 0.3, false)
		profile:TweenPosition(UDim2.new(1.5,0,0.5,0), "In", "Sine", 0.3, false)
		ability:TweenPosition(UDim2.new(0.5,0,1.5,0), "In", "Sine", 0.3, false)
		Blur:Play()
	elseif visible == true then
		inventoryFrame:TweenSizeAndPosition(UDim2.new(0,0,0,0), UDim2.new(1.5,0,0.5,0), "In", "Quad", 0.3, false)
		profile:TweenPosition(UDim2.new(0.5,0,0.55,0), "In", "Sine", 0.3, false)
		ability:TweenPosition(UDim2.new(0.5,0,0.5,0), "In", "Sine", 0.3, false)
		visible = false
		UnBlur:Play()
	end
end

-- (event to detect when key is pressed)
local userInputService = game:GetService("UserInputService")

userInputService.InputBegan:Connect(function(input, gameProcessed)
	-- Verifica si la tecla presionada es "E" y si no está procesada por el juego (Checks if key pressed is "E and if it is not processed by the game")
	if input.KeyCode == Enum.KeyCode.E and not gameProcessed then
		toggleInventory()
	end
end)

-- (Event to detect whether you are interacting with the inventory)
userInputService.InputBegan:Connect(function(input, gameProcessed)
	if inventoryFrame.Visible and input.UserInputType == Enum.UserInputType.MouseButton1 then
		gameProcessed = true
	end
end)
