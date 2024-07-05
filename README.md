# Roblox-Lua-scripts
Showcasing roblox lua scripts function for game development

--blur and black for tweening
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
