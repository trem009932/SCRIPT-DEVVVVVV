if game.PlaceId == 13822889 then
	local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
	local Window = OrionLib:MakeWindow({Name = "Bless Hub | V 1.0", IntroText = "Bless Hub", HidePremium = false, SaveConfig = true, ConfigFolder = "Bless Hub"})
	
	local PlayerTab = Window:MakeTab({
		Name = "Player",
		Icon = "rbxassetid://4483345998",
		PremiumOnly = false
	})

	PlayerTab:AddSlider({
		Name = "Walkspeed",
		Min = 16,
		Max = 500,
		Default = 16,
		Color = Color3.fromRGB(0,0,0),
		Increment = 1,
		ValueName = "",
		Callback = function(new)
			_G.WS = new;
		local Humanoid = game:GetService("Players").LocalPlayer.Character.Humanoid;
		Humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
			Humanoid.WalkSpeed = _G.WS;
		end)
		Humanoid.WalkSpeed = _G.WS;
		end    
	})
	
	
	PlayerTab:AddSlider({
		Name = "Jumppower",
		Min = 50,
		Max = 500,
		Default = 50,
		Color = Color3.fromRGB(0,0,0),
		Increment = 1,
		ValueName = "",
		Callback = function(value)
			_G.JP = value
			local Humanoid = game:GetService("Players").LocalPlayer.Character.Humanoid
			Humanoid:GetPropertyChangedSignal("JumpPower"):Connect(function()
			Humanoid.JumpPower = _G.JP
			end)
			Humanoid.JumpPower = _G.JP
		end    
	})
	
	
	PlayerTab:AddButton({
		Name = "Fly(e to use)",
		Callback = function()
			loadstring(game:HttpGet("https://pastebin.com/raw/nnNs32Td", true))()
		  end    
	})
	
	PlayerTab:AddButton({
		Name = "Inf jump",
		Callback = function()
			_G.infinjump = not _G.infinjump
	
			if _G.infinJumpStarted == nil then
				--Ensures this only runs once to save resources
				_G.infinJumpStarted = true
					--The actual infinite jump
				local plr = game:GetService('Players').LocalPlayer
				local m = plr:GetMouse()
				m.KeyDown:connect(function(k)
					if _G.infinjump then
						if k:byte() == 32 then
						humanoid = game:GetService'Players'.LocalPlayer.Character:FindFirstChildOfClass('Humanoid')
						humanoid:ChangeState('Jumping')
						wait()
						humanoid:ChangeState('Seated')
						end
					end
				end)
			end
		  end    
	})
	
	PlayerTab:AddButton({
		Name = "Btools",
		Callback = function()
			loadstring(game:HttpGet("https://raw.githubusercontent.com/trme222/btools-legit/main/README.md"))()
		  end    
	})
	
	PlayerTab:AddButton({
		Name = "Anti AFK",
		Callback = function()
			loadstring(game:HttpGet("https://pastebin.com/raw/mHiBCJXc"))()
		  end    
	})




	loadstring([[
	function FreeLand()
		for a,b in pairs(workspace.Properties:GetChildren()) do 
			if b:FindFirstChild("Owner") and b:FindFirstChild("OriginSquare") and b.Owner.Value == nil then 
		   wait(1)
		   game.ReplicatedStorage.PropertyPurchasing.ClientPurchasedProperty:FireServer(b, b.OriginSquare.OriginCFrame.Value.p + Vector3.new(0,3,0))
		  for i,v in pairs(game.Workspace.Properties:GetChildren()) do
		   if v.Owner.Value == game.Players.LocalPlayer then
		  wait(0.1)
		   game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.OriginSquare.CFrame + Vector3.new(0,10,0)
		  wait(0.1)
		   game.Players.LocalPlayer.Character.Jump = false
		  break
		  end
		  end
		  end
		  end
		  end
	]])();
	
	function LoadSlot()
		local LoadSlot = game.ReplicatedStorage.LoadSaveRequests.ClientMayLoad:InvokeServer(player)
			if LoadSlot then
				game.ReplicatedStorage.LoadSaveRequests.RequestLoad:InvokeServer(Slot, player)
			end
		end
		
	
	local DupeTab = Window:MakeTab({
		Name = "Dupe",
		Icon = "rbxassetid://4483345998",
		PremiumOnly = false
	})
	DupeTab:AddParagraph("Read before dupe","Dont click Q T P or it wipes your base")	

	local N=game:GetService("VirtualInputManager")
	
	DupeTab:AddSlider({
		Name = "Select Slot to Dupe",
		Min = 0,
		Max = 6,
		Default = 0,
		Color = Color3.fromRGB(255,255,255),
		Increment = 1,
		ValueName = "",
		Callback = function(new)
			Slot = tonumber(new)
		end    
	})
	
	
	DupeTab:AddTextbox({
		Name = "Enter how long it took to tp to your base (remove 3)",
		Default = "",
		TextDisappear = false,
		Callback = function(new)
			timetotp = tonumber(new)
		end	  
	})
	
	DupeTab:AddButton({
		Name = "Dupe land",
		Callback = function()
			print("Loading slot")
			N:SendKeyEvent(true,"Q",false,game)
			wait(0.1) -- free land
			N:SendKeyEvent(true,"T",false,game)
			wait(0.1) -- loads the base
			N:SendKeyEvent(true,"P",false,game) -- kicks from game
			LoadSlot()
		  end    
	})

     --extra functions---------------------------------------------------------
	
	scr=getsenv(game.Players.LocalPlayer.PlayerGui.PropertyPurchasingGUI.PropertyPurchasingClient);
	
	local player = game.Players.LocalPlayer
	local mouse = player:GetMouse()
	
	
	
	bind = "q" 
	
	
	
	mouse.KeyDown:connect(function(key)
	if key == bind then
		repeat wait()until game.Players.LocalPlayer.PlayerGui.PropertyPurchasingGUI.SelectPurchase.Visible;
		wait(1)
		wait(0.9)
		for i,v in next, game:GetService("Workspace").Properties:GetChildren() do
			if v:FindFirstChild("Owner") and v.Owner.Value == nil then
			game:GetService("ReplicatedStorage").PropertyPurchasing.ClientPurchasedProperty:FireServer(v,v.OriginSquare.Position)
			game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.OriginSquare.CFrame + Vector3.new(0,2,0)
			break
			end
		end
	end
	end)
	
	
	
	local player = game.Players.LocalPlayer
	local mouse = player:GetMouse()
	
	
	
	bind = "p" 
	
	
	
	mouse.KeyDown:connect(function(key)
	if key == bind then
		repeat wait()until game.Players.LocalPlayer.PlayerGui.PropertyPurchasingGUI.SelectPurchase.Visible;
		wait(1)
		wait(2)
		task.wait(timetotp - 2)
		loadstring(game:GetObjects("rbxassetid://2662507900")[1].Source)()
	end
	end)
	
	
	local player = game.Players.LocalPlayer
	local mouse = player:GetMouse()
	
	
	
	bind = "t" 
	
	
	
	mouse.KeyDown:connect(function(key)
	if key == bind then
		repeat wait()until game.Players.LocalPlayer.PlayerGui.PropertyPurchasingGUI.SelectPurchase.Visible;
		wait(0.3)
		scr.scrollSelection(-1);
		wait(0.1)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
		scr.scrollSelection(-1);
		wait(0.3)
		scr.selectionMade();
		wait(0.3)
		scr.selectionMade();
		wait(1)
	scr.scrollSelection(-1);
	wait(0.3)
	scr.selectionMade();
	wait(0.3)
	scr.selectionMade();
	wait(1)
	scr.scrollSelection(-1);
	wait(0.3)
	scr.selectionMade();
	wait(0.3)
	scr.selectionMade();
	wait(1)
	scr.scrollSelection(-1);
	wait(0.3)
	scr.selectionMade();
	wait(0.3)
	scr.selectionMade();
	wait(1)
	scr.scrollSelection(-1);
	wait(0.3)
	scr.selectionMade();
	wait(0.3)
	scr.selectionMade();
	wait(1)
	scr.scrollSelection(-1);
	wait(0.3)
	scr.selectionMade();
	wait(0.3)
	scr.selectionMade();
	wait(1)
	scr.scrollSelection(-1);
	wait(0.3)
	scr.selectionMade();
	wait(0.3)
	scr.selectionMade();                       
	end
	end)
	
	local Section = DupeTab:AddSection({
		Name = "Maxland dupe claim tools"
	})
	
	DupeTab:AddButton({
		Name = "Select plot",
		Callback = function()
			loadstring(game:HttpGet("https://pastebin.com/raw/Wj49DUwL"))()
		  end    
	})
	
	DupeTab:AddButton({
		Name = "Load on selected plot",
		Callback = function()
			for i,v in next, game:GetService("Workspace").Properties:GetChildren() do
				if v:FindFirstChild("OriginSquare") then
					if v.OriginSquare:FindFirstChild("Selection") then
					game:GetService("ReplicatedStorage").PropertyPurchasing.ClientPurchasedProperty:FireServer(v,v.OriginSquare.Position)
					game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.OriginSquare.CFrame + Vector3.new(0,2,0)
					break
				end
			end
		end
	end
	})
	
	DupeTab:AddButton({
		Name = "Save slot",
		Callback = function()
			local result = false
		repeat
			wait(1)
			getgenv().block_save = false
			local slot_id = game:GetService("Players")["LocalPlayer"]["CurrentSaveSlot"].Value
			result = game.ReplicatedStorage.LoadSaveRequests.RequestSave:InvokeServer(slot_id, game.Players.LocalPlayer)
			OrionLib:MakeNotification({
				Name = "trem2goated",
				Content = "Slot saved.",
				Image = "rbxassetid://12576176007",
				Time = 1
			})
			until result
			getgenv().block_save = true
		  end    
	})
	
	DupeTab:AddParagraph("Timer","Use the timer to time your dupes")
	DupeTab:AddButton({
		Name = "Timer",
		Callback = function()
			loadstring(game:HttpGet('https://pastebin.com/raw/EVp7P4fF'))()
		  end    
	})

	local BaseTab = Window:MakeTab({
		Name = "Base",
		Icon = "rbxassetid://4483345998",
		PremiumOnly = false
	})
	
	BaseTab:AddButton({
		Name = "item counter",
		Callback = function()
			loadstring(game:HttpGet('https://pastebin.com/raw/VextamCW'))()
		  end    
	})
	
	--World
	local WorldTab = Window:MakeTab({
		Name = "World",
		Icon = "rbxassetid://4483345998",
		PremiumOnly = false
	})
	
	WorldTab:AddButton({
		Name = "better graphics",
		Callback = function()
			loadstring(game:HttpGet("https://pastebin.com/raw/MEi0Y0AT", true))()
		  end    
	})
	
	WorldTab:AddToggle({
		Name = "No fog",
		Default = true,
		Callback = function(Value)
			loadstring(game:HttpGet("https://pastebin.com/raw/JniCmYG0", true))()
		end    
	})
	
	
	
	
	
	
	--info 
	local InfoTab = Window:MakeTab({
		Name = "Info",
		Icon = "rbxassetid://4483345998",
		PremiumOnly = false
	})
	
	InfoTab:AddParagraph("Devs","trem2goated#1646 and Bless#8888")
	
	
	end
	OrionLib:Init()
