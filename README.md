local mod = loadstring(game:HttpGet("https://raw.githubusercontent.com/deeeity/mercury-lib/master/src.lua"))()
local Serika = {
			Main = Color3.fromRGB(50, 52, 55),
			Secondary = Color3.fromRGB(80, 82, 85),
			Tertiary = Color3.fromRGB(226, 183, 20),

			StrongText = Color3.fromHSV(0, 0, 1),		
			WeakText = Color3.fromHSV(0, 0, 172/255)
		}

local wndw = mod:Create{
    Name = "CUTE HUB",
    Size = UDim2.fromOffset(600, 400),
    Theme = Serika,  -- Use manually defined Aqua theme
}

local T1 = wndw:Tab{
    Name = "Main",
    Icon = "rbxassetid://8569322835"
}

local T2 = wndw:Tab{
    Name = "Hatch",
    Icon = "rbxassetid://8569322835"
}


local T5 = wndw:Tab{
    Name = "Teleport",
    Icon = "rbxassetid://8569322835"
}


local T6 = wndw:Tab{
    Name = "Machineee",
    Icon = "rbxassetid://8569322835"
}


local player = game.Players.LocalPlayer
local playerChar = workspace:WaitForChild(player.Name)
local playerHRP = playerChar:WaitForChild("HumanoidRootPart")
local goldsFolder = workspace:WaitForChild("Golds")
local workspace = game:GetService("Workspace")
local cg = game:GetService("CoreGui")
local player = {
  self = game:GetService("Players").LocalPlayer,
  all = game:GetService("Players")
}


local var = {
    click = true,
    atk = false,
    on = false,
    bw = false,
    cs = false,
    spin = false,
    reb = false,
    egg = {
      id = 0,
      counts = 3,
      toggle = false
    },
    bh = false,
    task = {
      claim = false,
      ach = false,
      id = 0
    },
    hero = {
      index = 1,
      skill = true,
      guid = "null",
      id = 0,
      ft = false,
      ft2 = false
    },
    forge = {
      guid = "null",
      toggle = false
    },
    mapid = 50001,
    fuse = false,
    atk2 = false,
    bring = false,
    atk3 = false,
    raid = {
      table = {"Room1","Room2","Room3","Room4"},
      s = "Room1",
      diff = 1,
      mapid = 0,
      toggle = false,
      dtable = {"1","2","3","4"}
    },
    dc = false,
    fraid = false,
    cgroup = false,
    machine = {
      table = {"Mask","Breath","Ornament","Breath Amplification"},
      s = "Mask",
      toggle = false,
      delete = {
        common = false,
        rare = false,
        epic = false,
        legendary = false,
        mythic = false
      }
    },
    remote = {
      list = "",
      target = "Workspace",
      class = "BindableEvent"
    },
    alre = false
  }


local function getChildren(path,funct)
    for i,v in pairs(path:GetChildren()) do
      funct(v)
    end
  end
  
  local function hatch()
    getChildren(workspace.Maps,function(a)
        getChildren(a.Map.Eggs,function(array)
            game:GetService("ReplicatedStorage")["Remotes"]["ExtractHero"]:InvokeServer({["drawCardPlatformId"] = array:GetAttribute("Id"),["count"] = var.egg.counts})
        end)
    end)
  end

  

  T6:Toggle{
    Name = "Reroll Amplification",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        while value do
            wait(1)  -- Add a 1-second delay
            local args = {
                [1] = 400001
            }

            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("RerollOrnament"):InvokeServer(unpack(args))
        end
    end
}

T6:Toggle{
    Name = "Reroll Awakening",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        while value do
            wait(1)  -- Add a 1-second delay
            local args = {
                [1] = 400002
            }

            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("RerollOrnament"):InvokeServer(unpack(args))
        end
    end
}

T6:Toggle{
    Name = "Reroll Talisman",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        while value do
            wait(1)  -- Add a 1-second delay
            local args = {
                [1] = 400005
            }

            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("RerollOrnament"):InvokeServer(unpack(args))
        end
    end
}



 T1:Toggle{
    Name = "Auto click",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.click = value
        local args = {
            [1] = {}
        }
        while wait() do
            if var.click == false then break end
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("PlayerClickAttackSkill"):FireServer(unpack(args))
            wait(0.01)  -- Adjust the wait time as needed
        end
    end
}
 

T1:Toggle{
    Name = "Auto collect dropped items",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.bring = value
        while wait() do
            if var.bring == false then break end
            
            -- Iterate through all the dropped items in 'Golds' folder
            for _, gold in ipairs(goldsFolder:GetChildren()) do
                if gold:IsA("BasePart") and gold.Name == "OutGold" then
                    -- Move the gold towards the player's HumanoidRootPart
                    gold.CFrame = playerHRP.CFrame * CFrame.new(0, 0, -2)
                end
            end
        end
    end
}

T1:Toggle{
    Name = "Auto claim online rewards",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.on = value
        while wait() do
            if var.on == false then break end
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimOnlineReward"]:InvokeServer({["id"] = "73"})
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimOnlineReward"]:InvokeServer({["id"] = "74"})
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimOnlineReward"]:InvokeServer({["id"] = "75"})
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimOnlineReward"]:InvokeServer({["id"] = "76"})
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimOnlineReward"]:InvokeServer({["id"] = "77"})
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimOnlineReward"]:InvokeServer({["id"] = "78"})
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimOnlineReward"]:InvokeServer({["id"] = "79"})
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimOnlineReward"]:InvokeServer({["id"] = "80"})

        end
    end
}

T1:Toggle{
    Name = "Auto equip best weapon every 1s",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.bw = value
        if value == true then
            game:GetService("ReplicatedStorage")["Remotes"]["EquipBestWeapon"]:FireServer()
        end
        
        while wait(1) do
            if var.bw == false then break end
            game:GetService("ReplicatedStorage")["Remotes"]["EquipBestWeapon"]:FireServer()
        end
    end
}

T1:Toggle{
    Name = "Auto claim 7 Days Login",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.cs = value
        while wait() do
            if var.cs == false then break end
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimSevenLoginReward"]:InvokeServer(1)
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimSevenLoginReward"]:InvokeServer(2)
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimSevenLoginReward"]:InvokeServer(3)
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimSevenLoginReward"]:InvokeServer(4)
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimSevenLoginReward"]:InvokeServer(5)
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimSevenLoginReward"]:InvokeServer(6)
            game:GetService("ReplicatedStorage")["Remotes"]["ClaimSevenLoginReward"]:InvokeServer(7)
        end
    end
}

T1:Toggle{
    Name = "Auto Reborn",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.reb = value
        while wait() do
            if var.reb == false then break end
            game:GetService("ReplicatedStorage")["Remotes"]["PlayerReborn"]:FireServer()
        end
    end
}

T1:Toggle{
    Name = "Auto fuse weapon",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.fuse = value
        while wait() do
            if var.fuse == false then break end
            game:GetService("ReplicatedStorage")["Remotes"]["FuseWeapon"]:FireServer()
        end
    end
}


T2:Slider{
    Name = "Hatch amount",
    Default = 3,
    Min = 1,
    Max = 10,
    Callback = function(value)
        var.egg.id = value
    end
}

T2:Toggle{
    Name = "Auto Hatch",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.egg.toggle = value
        while wait() do
            if var.egg.toggle == false then break end
            hatch()
        end
    end
}

T2:Toggle{
    Name = "Auto equip best hero every 1s",
    StartingState = false,
    Description = nil,
    Callback = function(value)
        var.bh = value
        if value == true then
            game:GetService("ReplicatedStorage")["Remotes"]["AutoEquipBestHero"]:FireServer()
        end
        
        while wait(1) do
            if var.bh == false then break end
            game:GetService("ReplicatedStorage")["Remotes"]["AutoEquipBestHero"]:FireServer()
        end
    end
}


T5:Dropdown{
    Name = "Select map ID",
    StartingText = "Select...",
    Description = nil,
    Items = {
        {"Map 1", "50001"},
        {"Map 2", "50002"},
        {"Map 3", "50003"},
        {"Map 4", "50004"},
        {"Map 5", "50005"},
        {"Map 6", "50006"},
        {"Map 7", "50007"},
        {"Map 8", "50008"},
        {"Map 9", "50009"},
        {"Map 10", "50010"},
        {"Map 11", "50011"},
        {"Map 12", "50012"},
        {"Map 13", "50013"},
        {"Map 14", "50014"},
        {"Map 15", "50015"}
    },
    Callback = function(value)
        var.mapid = tonumber(value)
    end
}


T5:Button{
	Name = "Teleport to a selected map",
	Description = nil,
	Callback = function()
		game:GetService("ReplicatedStorage")["Remotes"]["LocalPlayerTeleport"]:FireServer({["mapId"] = var.mapid})
	end
}

T5:Button{
	Name = "Join Dungeon [ Bypass cooldown ]",
	Description = nil,
	Callback = function()
		game:GetService("ReplicatedStorage")["Remotes"]["LocalPlayerTeleport"]:FireServer({["mapId"] = 50016})
	end
}

T5:Button{
	Name = "Join Tower [ Bypass cooldown ]",
	Description = nil,
	Callback = function()
		game:GetService("ReplicatedStorage")["Remotes"]["LocalPlayerTeleport"]:FireServer({["mapId"] = 50107})
	end
}

T5:Button{
	Name = "Join Relic [ Bypass cooldown ]",
	Description = nil,
	Callback = function()
		game:GetService("ReplicatedStorage")["Remotes"]["LocalPlayerTeleport"]:FireServer({["mapId"] = 50900})
	end
}


local ab = Instance.new("TextLabel")

-- This will be the GUI toggle state
local antiAfkEnabled = true  -- Default is enabled

local bb = game:GetService('VirtualUser')

-- Function to start Anti-AFK behavior
local function startAntiAfk()
    game:GetService('Players').LocalPlayer.Idled:Connect(function()
        if antiAfkEnabled then
            bb:CaptureController()
            bb:ClickButton2(Vector2.new())
            ab.Text = "Roblox tried kicking you but I didn't let them!"
            wait(2)
            ab.Text = "Status: Active"
        end
    end)
end

-- Automatically enable Anti-AFK on startup
if antiAfkEnabled then
    startAntiAfk()
end

-- Toggle to control Anti-AFK
local function toggleAntiAfk(value)
    antiAfkEnabled = value
    if value then
        ab.Text = "Status: Active"
        startAntiAfk()  -- Restart the anti-afk if re-enabled
    else
        ab.Text = "Status: Disabled"
    end
end

-- GUI for toggle button
T1:Toggle{
    Name = "Enable Anti-AFK",
    StartingState = antiAfkEnabled,
    Description = "Prevent being kicked for inactivity.",
    Callback = toggleAntiAfk
}


local isScriptEnabled = false  -- Track if the script is enabled
local heartbeatConnection
local connections = {}

local function startCustomScript()
    -- This function will start the custom script
    
    local RunService = game:GetService("RunService")
    local Players = game:GetService("Players")
    local ReplicatedStorage = game:GetService("ReplicatedStorage")

    -- Settings
    local transferInterval = 0.1
    local offset = Vector3.new(5, 0, 0)
    local skillIds = {200560, 200561, 200562, 200563}
    local skillCooldown = 5
    local lastSkillTimes = {}

    local player = Players.LocalPlayer
    local enemiesFolder = workspace:WaitForChild("Enemys")
    local playerChar = player.Character or player.CharacterAdded:Wait()
    local playerHRP = playerChar:WaitForChild("HumanoidRootPart")
    local enemyDeathEvent = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("EnemyDeath")
    local playerRespirationSkillAttack = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("PlayerRespirationSkillAttack")
    local playerClickAttackSkill = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("PlayerClickAttackSkill")

    local visited = {}
    local enemyDied = true
    local transferTimer = 0
    local currentTarget = nil
    local attackCooldown = 0.01
    local attackTimer = 0
    local stuckTimer = 0

    -- Functions
    local function teleportToEnemy(enemy)
        local hrp = enemy:FindFirstChild("HumanoidRootPart")
        if not hrp then return end
        playerHRP.CFrame = hrp.CFrame * CFrame.new(offset)
    end

    local function getUnvisitedTarget()
        local unvisited = {}
        for _, enemy in ipairs(enemiesFolder:GetChildren()) do
            local enemyGuid = enemy:GetAttribute("EnemyGuid")
            if enemyGuid and not visited[enemyGuid] then
                table.insert(unvisited, enemy)
            end
        end
        if #unvisited == 0 then
            visited = {}
            return getUnvisitedTarget()
        end
        return unvisited[math.random(1, #unvisited)]
    end

    local function useSkillsOnEnemy(enemy)
        local enemyGuid = enemy:GetAttribute("EnemyGuid")
        if not enemyGuid then return end
        playerClickAttackSkill:FireServer({
            ["attackEnemyGUID"] = enemyGuid
        })
        for _, skillId in ipairs(skillIds) do
            local lastUsed = lastSkillTimes[skillId] or 0
            if tick() - lastUsed >= skillCooldown then
                playerRespirationSkillAttack:InvokeServer({
                    ["enemyGuid"] = enemyGuid,
                    ["respirationType"] = 3,
                    ["skillId"] = skillId
                })
                lastSkillTimes[skillId] = tick()
            end
        end
    end

    local function onEnemyDeath()
        enemyDied = true
        stuckTimer = 0
    end

    local function onCharacterRespawn(char)
        playerChar = char
        playerHRP = char:WaitForChild("HumanoidRootPart")
        enemyDied = true
        stuckTimer = 0
        print("Respawn detected. Script continued!")
    end

    -- Connections
    local deathConnection = enemyDeathEvent.OnClientEvent:Connect(onEnemyDeath)
    local respawnConnection = player.CharacterAdded:Connect(onCharacterRespawn)
    table.insert(connections, deathConnection)
    table.insert(connections, respawnConnection)

    -- Main loop
    heartbeatConnection = RunService.Heartbeat:Connect(function(dt)
        if attackTimer > 0 then
            attackTimer = attackTimer - dt
        end
        transferTimer += dt
        stuckTimer += dt

        if stuckTimer > 1 and currentTarget then
            print("Stuck on target for too long, moving to next target.")
            enemyDied = true
            stuckTimer = 0
        end

        if transferTimer >= transferInterval and enemyDied then
            local target = getUnvisitedTarget()
            if target then
                teleportToEnemy(target)
                local targetGuid = target:GetAttribute("EnemyGuid")
                if targetGuid then
                    visited[targetGuid] = true
                end
                enemyDied = false
                currentTarget = target
                stuckTimer = 0
            end
            transferTimer = 0
        end

        if currentTarget and currentTarget.Parent and attackTimer <= 0 then
            useSkillsOnEnemy(currentTarget)
            attackTimer = attackCooldown
        elseif not (currentTarget and currentTarget.Parent) then
            currentTarget = nil
        end
    end)
    table.insert(connections, heartbeatConnection)
end

local function stopCustomScript()
    -- Disconnect all connections and cleanup
    for _, connection in ipairs(connections) do
        if connection.Disconnect then
            connection:Disconnect()
        end
    end
    connections = {}  -- Clear out connections
    print("Custom script disabled.")
end

local toggleScript = T1:Toggle{
    Name = "Auto Farm",
    StartingState = isScriptEnabled,
    Description = "Toggle to enable or disable the custom script.",
    Callback = function(value)
        isScriptEnabled = value
        
        if isScriptEnabled then
            startCustomScript()
            print("Custom script enabled.")
        else
            stopCustomScript()
        end
    end
}

-- This will control if the process is enabled
local firingEnabled = false -- Default is disabled

-- Your Map and Point ID Data
local mapPoints = {
    [50001] = {"171001", "171002", "171003", "171004", "171005"},
    [50002] = {"172001", "172002", "172003", "172004", "172005"},
    [50003] = {"173001", "173002", "173003", "173004", "173005"},
    [50004] = {"174001", "174002", "174003", "174004", "174005"},
    [50005] = {"175001", "175002", "175003", "175004", "175005"},
    [50006] = {"176001", "176002", "176003", "176004", "176005"},
    [50008] = {"171001", "171002", "171003", "171004", "171005"},
    [50009] = {"172001", "172002", "172003", "172004", "172005"}
}

-- Function to start firing
local function startFiring()
    for mapId, pointIds in pairs(mapPoints) do
        if not firingEnabled then
            break -- Stop if firing gets disabled
        end
        for _, pointId in ipairs(pointIds) do
            if not firingEnabled then
                break
            end
            local args = {
                [1] = {
                    ["mapId"] = mapId,
                    ["pointId"] = pointId
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetBoxGift"):FireServer(unpack(args))
            print("Fired: mapId =", mapId, "pointId =", pointId)
            wait(0.1) -- Small delay between fires
        end
    end
    print("Firing process finished or stopped.")
end

-- Function to toggle the firing
local function toggleFiring(value)
    firingEnabled = value
    if value then
        print("Firing Enabled.")
        startFiring()
    else
        print("Firing Disabled.")
    end
end

-- GUI Toggle (T1)
T1:Toggle{
    Name = "Auto Pumpkin",
    StartingState = firingEnabled,
    Description = "Automatically fire GetBoxGift remotes.",
    Callback = toggleFiring
}


-- Unlimited Diamond Toggle (T2)
do
	local unlimitedDiamondRunning = false

T2:Toggle{
		Name = "Unlimited Diamond",
		StartingState = false,
		Description = "YOU SHOULD BE IN MAP 5",
		Callback = function(state)
			unlimitedDiamondRunning = state
			if state then
				task.spawn(function()
					while unlimitedDiamondRunning do
						local args = {
							{
								haloType = 3,
								count = 0
							}
						}

						game:GetService("ReplicatedStorage")
							:WaitForChild("Remotes")
							:WaitForChild("ExchangeHaloDrawItem")
							:InvokeServer(unpack(args))

						task.wait(0.1)
					end
				end)
			end
		end
	}
end
-- Auto SPIN


-- Auto Spin Diamond Key Toggle (T3)
do
	local autoSpinRunning = false

	T2:Toggle{
		Name = "Auto Spin Diamond Key",
		StartingState = false,
		Description = "Automatically rerolls the halo using diamond keys.",
		Callback = function(state)
			autoSpinRunning = state
			if state then
				task.spawn(function()
					while autoSpinRunning do
						local args = {
							[1] = 3
						}

						game:GetService("ReplicatedStorage")
							:WaitForChild("Remotes")
							:WaitForChild("RerollHalo")
							:InvokeServer(unpack(args))

						task.wait(0.1)
					end
				end)
			end
		end
	}
end
