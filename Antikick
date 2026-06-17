-- Anti kick, this blocks kicks coming from ingame scripts

local mt = getrawmetatable(game)
if setreadonly then setreadonly(mt, false) end
local oldNamecall = mt.__namecall
mt.__namecall = newcclosure(function(self, ...)
    local method = getnamecallmethod()
    if method == "Kick" and self == LocalPlayer then
        return
    end
    return oldNamecall(self, ...)
end)

local oldIndex = mt.__index
mt.__index = newcclosure(function(self, key)
    if not checkcaller() and typeof(self) == "Instance" and self:IsA("Mouse") then
        if key == "Target" and _G.FakeMouseTarget then
            return _G.FakeMouseTarget
        elseif key == "Hit" and _G.FakeMouseHit then
            return _G.FakeMouseHit
        end
    end
    return oldIndex(self, key)
end)
if setreadonly then setreadonly(mt, true) end
