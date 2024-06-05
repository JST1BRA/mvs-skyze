local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

OrionLib:MakeNotification({
	Name = "M-V-S Gui For Skyze!",
	Content = "By JST1bra_",
	Image = "rbxassetid://4483345998",
	Time = 5
})

local Main = OrionLib:MakeWindow({Name = "M-V-S Gui - Skyze", HidePremium = false, SaveConfig = true, ConfigFolder = "M-V-S Gui - Skyze"})

local MainTav = Main:MakeTab({
	Name = "Main",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local toggleState = false
local bringingPlayers = false

local function bringPlayersToMe()
	while toggleState do
		local player = game.Players.LocalPlayer
		if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
			local playerPosition = player.Character.HumanoidRootPart.Position
			for _, otherPlayer in ipairs(game.Players:GetPlayers()) do
				if otherPlayer ~= player and otherPlayer.Character and otherPlayer.Character:FindFirstChild("HumanoidRootPart") then
					otherPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(playerPosition)
				end
			end
		end
		wait(0.01) -- dont touch bitch lmao
	end
end

MainTav:AddToggle({
	Name = "Bring all",
	Default = false,
	Callback = function(state)
		toggleState = state
		if toggleState then
		
			if not bringingPlayers then
				bringingPlayers = true
				coroutine.wrap(bringPlayersToMe)()
			end
		else
		
			bringingPlayers = false
		end
	end    
})

MainTav:AddToggle({
    Name = "MACHINE GUN [HOLD GUN]",
    Default = false,
    Callback = function(state)
        if state then
     
            while state do
				game.Players.LocalPlayer.Character.Default:SetAttribute("Cooldown", 0)

                wait(0.1) -- Adjust the delay according to your needs
            end
        else
			game.Players.LocalPlayer.Character.Default:SetAttribute("Cooldown", 2.5)
        end
    end    
})














