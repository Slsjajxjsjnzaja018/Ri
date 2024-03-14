function No()
    for i, v in ipairs(workspace.Lives:GetChildren()) do
        if not game:GetService("Players"):GetPlayerFromCharacter(v) then 
            local cleanedName = string.gsub(v.Name, "%d+$", "") 
            v.Name = cleanedName
        end
    end
end

workspace.Lives.ChildAdded:Connect(function(model)
    if not game:GetService("Players"):GetPlayerFromCharacter(model) then 
        local cleanedName = string.gsub(model.Name, "%d+$", "")
        model.Name = cleanedName
    end
end)

No()

function TP(CFrame)
    pcall(function()
        game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame = CFrame
    end)
end

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/wizard"))()
local P = Library:NewWindow("Test")
 
local K = P:NewSection("Raid[👉🏻ตั้งค่าไรให้เสร็จก่อนเด้อค่อยเปิด👈🏻]")

K:CreateTextbox("ระยะการฟาม", function(text)
    _G.Di = tonumber(text) or 0
end)

K:CreateDropdown("เลือกตำแหน่งการฟาม", {"Behind", "Below", "Upper"}, 3, function(io)
_G.Method = io
end)
    
    
    
    spawn(function()
        while wait() do 
            pcall(function()
                if _G.Method == "Behind" then
                    MethodFarm = CFrame.new(0,0,_G.Di)
                elseif _G.Method == "Below" then
                    MethodFarm = CFrame.new(0,-_G.Di,0) * CFrame.Angles(math.rad(90),0,0)
                elseif _G.Method == "Upper" then
                    MethodFarm = CFrame.new(0,_G.Di,0)  * CFrame.Angles(math.rad(-90),0,0)
                
                end
            end)
        end
    end)

K:CreateButton("Boots FPS", function()
local decalsyeeted = true 
local g = game
local w = g.Workspace
local l = g.Lighting
local t = w.Terrain
sethiddenproperty(l,"Technology",2)
sethiddenproperty(t,"Decoration",false)
t.WaterWaveSize = 0
t.WaterWaveSpeed = 0
t.WaterReflectance = 0
t.WaterTransparency = 0
l.GlobalShadows = 0
l.FogEnd = 9e9
l.Brightness = 0
settings().Rendering.QualityLevel = "Level01"
for i, v in pairs(w:GetDescendants()) do
    if v:IsA("BasePart") and not v:IsA("MeshPart") then
        v.Material = "Plastic"
        v.Reflectance = 0
    elseif (v:IsA("Decal") or v:IsA("Texture")) and decalsyeeted then
        v.Transparency = 1
    elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
        v.Lifetime = NumberRange.new(0)
    elseif v:IsA("Explosion") then
        v.BlastPressure = 1
       v.BlastRadius = 1
    elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
        v.Enabled = false
    elseif v:IsA("MeshPart") and decalsyeeted then
        v.Material = "Plastic"
        v.Reflectance = 0
        v.TextureID = 10385902758728957
    elseif v:IsA("SpecialMesh") and decalsyeeted  then
        v.TextureId=0
    elseif v:IsA("ShirtGraphic") and decalsyeeted then
        v.Graphic=0
    elseif (v:IsA("Shirt") or v:IsA("Pants")) and decalsyeeted then
        v[v.ClassName.."Template"]=0
    end
end
for i = 1,#l:GetChildren() do
    e=l:GetChildren()[i]
    if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
        e.Enabled = false
    end
end
w.DescendantAdded:Connect(function(v)
    wait()--prevent errors and shit
   if v:IsA("BasePart") and not v:IsA("MeshPart") then
        v.Material = "Plastic"
        v.Reflectance = 0
    elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
        v.Transparency = 1
    elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
        v.Lifetime = NumberRange.new(0)
    elseif v:IsA("Explosion") then
        v.BlastPressure = 1
        v.BlastRadius = 1
    elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
        v.Enabled = false
    elseif v:IsA("MeshPart") and decalsyeeted then
        v.Material = "Plastic"
        v.Reflectance = 0
        v.TextureID = 10385902758728957
    elseif v:IsA("SpecialMesh") and decalsyeeted then
        v.TextureId=0
    elseif v:IsA("ShirtGraphic") and decalsyeeted then
        v.ShirtGraphic=0
    elseif (v:IsA("Shirt") or v:IsA("Pants")) and decalsyeeted then
        v[v.ClassName.."Template"]=0
              end
        end)
end)
 

K:CreateToggle("ออโต้ฟามมอนRaid", function(mok)
    _G.kuyyai = mok
end)

local monRaid = {
    "Cid",
    "Shadow Soldier",
    "Shadow Lord",
    "Shadow Artoria",
    "Shadow Sukuna",
    "Shadow Natsu"
}


spawn(function()
    while true do
        wait()
        pcall(function()
            if _G.kuyyai then        
                for _, v in pairs(workspace.Lives:GetChildren()) do  -- เปลี่ยนจาก pairs เป็น ipairs
                    if table.find(monRaid, v.Name) and v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health >= 1 then
                        repeat
							task.wait()
                            v.HumanoidRootPart.Size = Vector3.new(10, 10, 10)
                            v.HumanoidRootPart.Transparency = 0.9
                            TP(v.HumanoidRootPart.CFrame*MethodFarm)
                        until _G.kuyyai == false or v.Humanoid.Health <= 0
                    end
                end
            end
        end)
    end
end)
