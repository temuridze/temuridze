local lighting = game:GetService("Lighting")
local startTime = 8 -- Начальное время (8 утра)
local cycleDuration = 120 -- Продолжительность цикла в секундах (2 минуты)
local moonIntensityNight = 0.1 -- Интенсивность луны ночью

local function updateCycle()
    local elapsedTime = (tick() % cycleDuration) / cycleDuration
    local sunAngle = (elapsedTime * 360) - 90
    lighting:SetMinutesAfterMidnight(startTime * 60)
    lighting:SetRotation(sunAngle, 0)
    
    if elapsedTime < 0.5 then
        lighting.Sky.moonIntensity = moonIntensityNight
    else
        lighting.Sky.moonIntensity = 1
    end
end

game:GetService("RunService").Heartbeat:Connect(updateCycle)
