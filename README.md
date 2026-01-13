local p=game.Players.LocalPlayer
local rs=game:GetService("RunService")

local function hum() return (p.Character or p.CharacterAdded:Wait()):WaitForChild("Humanoid") end
local function root() return (p.Character or p.CharacterAdded:Wait()):WaitForChild("HumanoidRootPart") end

local gui=Instance.new("ScreenGui",p.PlayerGui)

-- SPLASH
local splash=Instance.new("ImageLabel",gui)
splash.Size=UDim2.fromScale(1,1)
splash.Image="rbxassetid://12410327657"
splash.BackgroundTransparency=1

task.delay(2,function() splash:Destroy() end)

-- PANEL
local panel=Instance.new("Frame",gui)
panel.Size=UDim2.fromScale(.85,.6)
panel.Position=UDim2.fromScale(.075,.2)
panel.BackgroundColor3=Color3.fromRGB(30,30,30)
panel.Visible=false
panel.Active=true panel.Draggable=true
Instance.new("UICorner",panel)

local title=Instance.new("TextLabel",panel)
title.Size=UDim2.fromScale(1,.12)
title.Text="ELMIR MENU"
title.BackgroundTransparency=1
title.TextScaled=true
title.TextColor3=Color3.new(1,1,1)

local close=Instance.new("TextButton",panel)
close.Size=UDim2.fromScale(.08,.12)
close.Position=UDim2.fromScale(.92,0)
close.Text="X"
close.BackgroundColor3=Color3.fromRGB(180,50,50)
close.TextColor3=Color3.new(1,1,1)
close.TextScaled=true
Instance.new("UICorner",close)

local azBtn=Instance.new("TextButton",gui)
azBtn.Size=UDim2.fromScale(.4,.08)
azBtn.Position=UDim2.fromScale(.3,.9)
azBtn.Text="🇦🇿 Azərbaycan Bayrağı"
azBtn.BackgroundColor3=Color3.fromRGB(20,20,20)
azBtn.TextColor3=Color3.new(1,1,1)
azBtn.TextScaled=true
azBtn.Visible=false
Instance.new("UICorner",azBtn)

local function row(txt,y)
    local b=Instance.new("TextButton",panel)
    b.Size=UDim2.fromScale(.9,.12)
    b.Position=UDim2.fromScale(.05,y)
    b.Text=txt
    b.BackgroundColor3=Color3.fromRGB(45,45,45)
    b.TextColor3=Color3.new(1,1,1)
    b.TextScaled=true
    Instance.new("UICorner",b)
    return b
end

local function sub(y)
    local f=Instance.new("Frame",panel)
    f.Size=UDim2.fromScale(.9,.14)
    f.Position=UDim2.fromScale(.05,y)
    f.BackgroundColor3=Color3.fromRGB(35,35,35)
    f.Visible=false
    Instance.new("UICorner",f)
    return f
end

-- STATES
local speedOn=false speed=16
local noclip=false
local fly=false flySpeed=5
local jumpOn=false jump=50

------------------------------------------------
-- WALK SPEED
------------------------------------------------
local wsRow=row("Walk Speed",.15)
local wsP=sub(.28)

local wsT=Instance.new("TextButton",wsP)
wsT.Size=UDim2.fromScale(.18,.7)
wsT.Position=UDim2.fromScale(.02,.15)
wsT.Text="OFF"
wsT.BackgroundColor3=Color3.fromRGB(180,50,50)
wsT.TextColor3=Color3.new(1,1,1)
wsT.TextScaled=true
Instance.new("UICorner",wsT)

local wsM=Instance.new("TextButton",wsP)
wsM.Size=UDim2.fromScale(.15,.7)
wsM.Position=UDim2.fromScale(.23,.15)
wsM.Text="-"
wsM.TextScaled=true
Instance.new("UICorner",wsM)

local wsPp=Instance.new("TextButton",wsP)
wsPp.Size=UDim2.fromScale(.15,.7)
wsPp.Position=UDim2.fromScale(.4,.15)
wsPp.Text="+"
wsPp.TextScaled=true
Instance.new("UICorner",wsPp)

local wsI=Instance.new("TextBox",wsP)
wsI.Size=UDim2.fromScale(.35,.7)
wsI.Position=UDim2.fromScale(.57,.15)
wsI.PlaceholderText="16"
wsI.ClearTextOnFocus=false
wsI.TextScaled=true
Instance.new("UICorner",wsI)

------------------------------------------------
-- NOCLIP
------------------------------------------------
local ncRow=row("No Clip",.44)
local ncP=sub(.57)

local ncT=Instance.new("TextButton",ncP)
ncT.Size=UDim2.fromScale(.3,.7)
ncT.Position=UDim2.fromScale(.02,.15)
ncT.Text="OFF"
ncT.TextScaled=true
ncT.BackgroundColor3=Color3.fromRGB(180,50,50)
Instance.new("UICorner",ncT)

------------------------------------------------
-- FLY
------------------------------------------------
local flyRow=row("Fly",.73)
local flyP=sub(.86)

local flyT=Instance.new("TextButton",flyP)
flyT.Size=UDim2.fromScale(.2,.7)
flyT.Position=UDim2.fromScale(.02,.15)
flyT.Text="OFF"
flyT.TextScaled=true
flyT.BackgroundColor3=Color3.fromRGB(180,50,50)
Instance.new("UICorner",flyT)

local flyM=Instance.new("TextButton",flyP)
flyM.Size=UDim2.fromScale(.15,.7)
flyM.Position=UDim2.fromScale(.25,.15)
flyM.Text="-"
flyM.TextScaled=true
Instance.new("UICorner",flyM)

local flyPp=Instance.new("TextButton",flyP)
flyPp.Size=UDim2.fromScale(.15,.7)
flyPp.Position=UDim2.fromScale(.42,.15)
flyPp.Text="+"
flyPp.TextScaled=true
Instance.new("UICorner",flyPp)

------------------------------------------------
-- JUMP BOOST
------------------------------------------------
local jpRow=row("Jump Boost",1.02)
local jpP=sub(1.15)

local jpT=Instance.new("TextButton",jpP)
jpT.Size=UDim2.fromScale(.2,.7)
jpT.Position=UDim2.fromScale(.02,.15)
jpT.Text="OFF"
jpT.TextScaled=true
jpT.BackgroundColor3=Color3.fromRGB(180,50,50)
Instance.new("UICorner",jpT)

local jpM=Instance.new("TextButton",jpP)
jpM.Size=UDim2.fromScale(.15,.7)
jpM.Position=UDim2.fromScale(.25,.15)
jpM.Text="-"
jpM.TextScaled=true
Instance.new("UICorner",jpM)

local jpPp=Instance.new("TextButton",jpP)
jpPp.Size=UDim2.fromScale(.15,.7)
jpPp.Position=UDim2.fromScale(.42,.15)
jpPp.Text="+"
jpPp.TextScaled=true
Instance.new("UICorner",jpPp)

------------------------------------------------
-- LOGIC
------------------------------------------------
wsRow.MouseButton1Click:Connect(function() wsP.Visible=not wsP.Visible end)
ncRow.MouseButton1Click:Connect(function() ncP.Visible=not ncP.Visible end)
flyRow.MouseButton1Click:Connect(function() flyP.Visible=not flyP.Visible end)
jpRow.MouseButton1Click:Connect(function() jpP.Visible=not jpP.Visible end)

wsT.MouseButton1Click:Connect(function()
    speedOn=not speedOn
    wsT.Text=speedOn and "ON" or "OFF"
    wsT.BackgroundColor3=speedOn and Color3.fromRGB(50,180,50) or Color3.fromRGB(180,50,50)
    hum().WalkSpeed=speedOn and speed or 16
end)

wsM.MouseButton1Click:Connect(function()
    speed=math.max(1,speed-1)
    if speedOn then hum().WalkSpeed=speed end
end)

wsPp.MouseButton1Click:Connect(function()
    speed=math.min(70000000,speed+1)
    if speedOn then hum().WalkSpeed=speed end
end)

wsI.FocusLost:Connect(function()
    local v=tonumber(wsI.Text)
    if v then speed=math.clamp(v,1,70000000) if speedOn then hum().WalkSpeed=speed end end
end)

ncT.MouseButton1Click:Connect(function()
    noclip=not noclip
    ncT.Text=noclip and "ON" or "OFF"
    ncT.BackgroundColor3=noclip and Color3.fromRGB(50,180,50) or Color3.fromRGB(180,50,50)
end)

flyT.MouseButton1Click:Connect(function()
    fly=not fly
    flyT.Text=fly and "ON" or "OFF"
    flyT.BackgroundColor3=fly and Color3.fromRGB(50,180,50) or Color3.fromRGB(180,50,50)
end)

flyM.MouseButton1Click:Connect(function()
    flySpeed=math.max(1,flySpeed-1)
end)

flyPp.MouseButton1Click:Connect(function()
    flySpeed=math.min(20,flySpeed+1)
end)

jpT.MouseButton1Click:Connect(function()
    jumpOn=not jumpOn
    jpT.Text=jumpOn and "ON" or "OFF"
    jpT.BackgroundColor3=jumpOn and Color3.fromRGB(50,180,50) or Color3.fromRGB(180,50,50)
    hum().JumpPower=jumpOn and jump or 50
end)

jpM.MouseButton1Click:Connect(function()
    jump=math.max(10,jump-5)
    if jumpOn then hum().JumpPower=jump end
end)

jpPp.MouseButton1Click:Connect(function()
    jump=math.min(500,jump+5)
    if jumpOn then hum().JumpPower=jump end
end)

rs.Stepped:Connect(function()
    if noclip then
        for _,v in pairs(p.Character:GetDescendants()) do
            if v:IsA("BasePart") then v.CanCollide=false end
        end
    end

    if fly then
        local bv=Instance.new("BodyVelocity",root())
        bv.MaxForce=Vector3.new(1e5,1e5,1e5)
        bv.Velocity=workspace.CurrentCamera.CFrame.LookVector*flySpeed*10
        task.delay(.1,function() if bv then bv:Destroy() end end)
    end
end)

close.MouseButton1Click:Connect(function()
    panel.Visible=false
    azBtn.Visible=true
end)

azBtn.MouseButton1Click:Connect(function()
    panel.Visible=true
    azBtn.Visible=false
end)

task.delay(2,function() panel.Visible=true end)
