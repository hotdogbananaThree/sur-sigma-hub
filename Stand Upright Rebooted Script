local DiscordLib = loadstring(game:HttpGet"https://raw.githubusercontent.com/dawid-scripts/UI-Libs/main/discord%20lib.txt")()

local win = DiscordLib:Window("Sigma Hub V1")

local serv = win:Server("SU:R GUI", "")

local home = serv:Channel("Home")

home:Label("Welcome to Sigma Hub V1!")

home:Seperator()

home:Button("About", function()
	DiscordLib:Notification("About", "Made by hotdogbananaThree | Uses a lot of Arctic Hub's code!", "Ok")
end)

home:Button("Status", function()
	DiscordLib:Notification("Current Status", "Working!", "Ok")
end)

local buttons = serv:Channel("LocalPlayer")

buttons:Label("Shortcuts")

buttons:Button("Open Stand Storage", function()
	game:GetService("Workspace").Map.NPCs.admpn.Done:FireServer()
end)

buttons:Seperator()

buttons:Label("Use Items")

buttons:Button("Use Stand Arrow", function()
	if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Stand Arrow") then
		game:GetService("Players").LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Stand Arrow"))
		game:GetService("Players").LocalPlayer.Character:WaitForChild("Stand Arrow"):WaitForChild("Use"):FireServer()
	end
end)

buttons:Button("Use Charged Arrow", function()
	if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Charged Arrow") then
		game:GetService("Players").LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Charged Arrow"))
		game:GetService("Players").LocalPlayer.Character:WaitForChild("Charged Arrow"):WaitForChild("Use"):FireServer()
	end
end)

buttons:Button("Use Requiem Arrow", function()
	if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Requiem Arrow") then
		game:GetService("Players").LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Requiem Arrow"))
		game:GetService("Players").LocalPlayer.Character:WaitForChild("Requiem Arrow"):WaitForChild("Use"):FireServer()
	end
end)

buttons:Button("Use Rokakaka", function()
	if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Rokakaka") then
		game:GetService("Players").LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Rokakaka"))
		game:GetService("Players").LocalPlayer.Character:WaitForChild("Rokakaka"):WaitForChild("Use"):FireServer()
	end
end)

buttons:Button("Use DIO's Diary", function()
	if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dio's Diary") then
		game:GetService("Players").LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dio's Diary"))
		game:GetService("Players").LocalPlayer.Character:WaitForChild("Dio's Diary"):WaitForChild("Use"):FireServer()
	end
end)

buttons:Seperator()

buttons:Label("Misc")

local AutoUmbrella = false
buttons:Toggle("Auto Umbrella", false, function()
	AutoUmbrella = not AutoUmbrella

	if AutoUmbrella then
		while AutoUmbrella == true and task.wait() do
			pcall(function()
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Umbrella") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Umbrella") then
					game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart")
					game:GetService("Players").LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Umbrella"))
				end
			end)
		end
	end
end)

local lairFarm = serv:Channel("Lair Farm")

lairFarm:Button("Tutorial", function()
	DiscordLib:Notification("Tutorial", "Stand near Lair NPC and press 'Select Lair NPC'", "Ok")
end)

lairFarm:Seperator()

local SelectedLairNPC
local SelectedLairNPCText

lairFarm:Button("Select Lair NPC", function()
	for i, v in pairs(workspace.Map.NPCs:GetChildren()) do
		if v:FindFirstChild("HumanoidRootPart") then
			if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude < 15 then
				SelectedLairNPC = v
				SelectedLairNPCText = v.Head:FindFirstChild("Main").Text.Text
			end
		end
	end
end)

function TriggerLair()
	local Done
	for i, v in pairs(SelectedLairNPC:GetChildren()) do
		if v.Name == "Done" then
			Done = v
		end
	end

	if Done then
		Done:FireServer()
	else
		DiscordLib:Notification("Sorry!", "An unexpected error occurred.", "Ok")
	end
end

local StartLairFarming = false
lairFarm:Toggle("Begin Lair Farm", false, function()
	StartLairFarming = not StartLairFarming

	if StartLairFarming then
		if SelectedLairNPC then
			while StartLairFarming and task.wait() do
				pcall(function()
					TriggerLair()
					game:GetService("Workspace").Living:WaitForChild("Boss")

					repeat
						task.wait()
						pcall(function()
							for i, v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.CDgui.fortnite:GetChildren()) do
								if v:IsA("Frame") and v.Textt.Text == "Punch" then
									-- Polar Was Here!
								else
									game:GetService("Players").LocalPlayer.Character.StandEvents.M1:FireServer()
								end
							end
							if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Aura").Value == false then
								game:GetService("Players").LocalPlayer.Character.StandEvents.Summon:FireServer()
							end
							if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
								game:GetService("Players").LocalPlayer.Character.Stand:WaitForChild("HumanoidRootPart").CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
							end

							game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0, 0, 0)
							workspace.Living:FindFirstChild("Boss").Humanoid.Health = 0
							game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Living:FindFirstChild("Boss"):WaitForChild("HumanoidRootPart").CFrame * CFrame.new(0, -6, 4, 1, 0, 0, 1)
							repeat workspace.Living:FindFirstChild("Boss").Humanoid.Health = 0 until workspace.Living:FindFirstChild("Boss").Humanoid.Health == 0
						end)
					until not workspace.Living:FindFirstChild("Boss") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid").Health == 0 or StartLairFarming == false
					wait(1)
				end)
			end
		else
			DiscordLib:Notification("Error!", "You are missing a step! Check the tutorial!", "Ok")
		end
	end
end)

local questFarm = serv:Channel("Quest Farm")

questFarm:Button("Tutorial", function()
	DiscordLib:Notification("Tutorial", "Step 1 (Quest Selection), Stand Near Quest NPC And Press 'Select Quest NPC'", "Ok")
	task.wait(0.1)
	DiscordLib:Notification("Tutorial", "Step 2 (NPC Selection), Stand Near NPC To Kill And Press 'Select NPC", "Ok")
end)

questFarm:Seperator()

local SelectedQuestNPC
local SelectedQuestNPCText = "None"
local SelectedNPC = "None"

questFarm:Button("Select Quest NPC", function()
	for i, v in pairs(workspace.Map.NPCs:GetChildren()) do
		if v:FindFirstChild("HumanoidRootPart") then
			if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude < 15 then
				SelectedQuestNPC = v
				
				DiscordLib:Notification("Success!", "Chosen Quest Giver: " .. v.Name, "Ok")
			end
		end
	end
end)

questFarm:Button("Select NPC", function()
	for i, v in pairs(workspace.Living:GetChildren()) do
		if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("AI") then
			if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude < 15 then
				SelectedNPC = v.Name
				
				DiscordLib:Notification("Success!", "Chosen target: " .. v.Name, "Ok")
			end
		end
	end
end)

local function TriggerQuest()
	local QuestDone
	local Done
	for i, v in pairs(SelectedQuestNPC:GetChildren()) do
		if v.Name == "QuestDone" then
			QuestDone = v
		elseif v.Name == "Done" then
			Done = v
		end
	end

	if QuestDone then
		QuestDone:FireServer()
	else
		DiscordLib:Notification("Sorry!", "An unexpected error occurred.", "Ok")
	end

	if Done then
		Done:FireServer()
	else
		DiscordLib:Notification("Sorry!", "An unexpected error occurred.", "Ok")
	end
end

local StartQuestFarming = false
questFarm:Toggle("Begin Quest Farm", false, function()
	StartQuestFarming = not StartQuestFarming

	if StartQuestFarming then
		if SelectedQuestNPC and SelectedNPC ~= "None" then
			while StartQuestFarming and task.wait() do
				pcall(function()
					for i, v in pairs(workspace.Living:GetChildren()) do
						if v.Name == SelectedNPC and v.Humanoid.Health ~= 0 then
							TriggerQuest()
							repeat
								task.wait()
								for i, v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.CDgui.fortnite:GetChildren()) do
									if v:IsA("Frame") and v.Textt.Text == "Punch" then
										-- Polar Was Here!
									else
										game:GetService("Players").LocalPlayer.Character.StandEvents.M1:FireServer()
									end
								end

								if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
									game:GetService("Players").LocalPlayer.Character.Stand:WaitForChild("HumanoidRootPart").CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
								end

								game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame = v:FindFirstChild("HumanoidRootPart").CFrame * CFrame.new(0, -5, 1, 1, 0, 0, 1)
								game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0, 0, 0)
								if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Aura").Value == false then
									game:GetService("Players").LocalPlayer.Character.StandEvents.Summon:FireServer()
								end
							until v.Humanoid.Health == 0 or StartQuestFarming == false

							TriggerQuest()
							game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(0, 0, 1000))
							game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(0, 10, 0))
						end
					end
				end)
			end
		else
			DiscordLib:Notification("Error!", "You are missing a step! Check the tutorial!", "Ok")
		end
	end
end)

local standFarm = serv:Channel("Stand Farm")

standFarm:Label("Coming soon!")

local itemFarm = serv:Channel("Item Farm")

itemFarm:Label("Coming soon!")


local teleports = serv:Channel("Teleports")

teleports:Label("Player Teleports")

teleports:Textbox("Teleport To", "Player name here", true, function(A)
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Players"):FindFirstChild(tostring(A)).Character.HumanoidRootPart.CFrame
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Textbox("Teleport Above", "Player name here", true, function(A)
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Players"):FindFirstChild(tostring(A)).Character.HumanoidRootPart.CFrame * CFrame.new(0, 25, 0)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Seperator()

teleports:Label("Quest Teleports")

teleports:Button("Giorno Giovanna [Level 1+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-661.405029, 67.1819992, -797.159973)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Scared Noob [Level 10+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-703.195679, 67.1782303, -1013.146)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Koichi Hirose [Level 20+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-181.556412, 66.7327728, -585.154663)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("aLLmemester [Level 30+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-639.151245, 66.9135437, -460.119171)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Okuyasu [Level 40+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-510.674011, 67.1819992, -999.445007)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Joseph Joestar [Level 50+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-82.8209991, 67.0810013, -825.888977)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Josuke Higashikata [Level 75+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-492.863983, 67.1782379, -710.836853)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Rohan Kishibe [Level 100+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-303.60437, 67.0773239, -713.353333)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("DIO [Level 125+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-426.132996, 67.1269989, -123.800003)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Muhammad Avdol [Level 150+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-242.013214, 67.0773315, -215.973175)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Giorno Giovanna [Level 175+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-491.130524, 67.1677094, -33.4819489)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Will Anthonio Zeppeli [Level 200+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-5181.75, -449.374115, -3817.55981)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Young Joseph [Level 275+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-679.927979, 66.6819992, -189.617009)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Diavolo [Level 500+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-734.86499, 66.685997, -439.040009)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Staticaliza [Level 1000+]", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-644.219666, 66.7231827, 79.3064728)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Seperator()

teleports:Label("Map Teleports")

teleports:Button("D4C Dimension", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(11927.1, -3.28935, -4488.59)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Rarity Boards", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-658.979, 67.0282, -451.495)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Stand Storage Room", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-393.893, 23.5808, -280.786)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Inner Sanctum", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(27877.87109375, 27.233600616455078, -147.72268676757812)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Mud Pit", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(17.0716, 66.9873, -246.13)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Hamon Dealer", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-801.427, 66.5359, -735.121)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Vehicle Man", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-187.042, 78.4486, -1076.25)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Testing Zone", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(19999.3, 100.155, -730.726)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Bad Gi Spawn", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-687.604736328125, 67.03131866455078, -837.9588623046875)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Scary Monster Cave", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-683.89794921875, 67.03133392333984, -1039.75634765625)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Sewer", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-5308.6455078125, -450.83184814453125, -3815.388427734375)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Yoshikage Kira Spawn", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-446.5094299316406, 67.03131103515625, -995.3768310546875)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Dio's Rock", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-37.414466857910156, 92.30691528320312, -804.2440185546875)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Gyro Zeppeli", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(57.21436309814453, 66.80048370361328, -216.83428955078125)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Button("Moped", function()
	game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-745.187439, 67.2840881, -591.28363)
	if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand") then
		game:GetService("Players").LocalPlayer.Character:FindFirstChild("Stand").HumanoidRootPart.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end)

teleports:Seperator()

teleports:Label("Lair Teleports")

teleports:Label("coming soon")

--win:Server("Main", "http://www.roblox.com/asset/?id=6031075938")
