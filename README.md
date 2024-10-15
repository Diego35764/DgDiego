
    min = 15,
    max = 30 --range of players on the server
}
getgenv().FlySpeed = 275
getgenv().Team = "Prisoners"
getgenv().TimeToLoad = 3

loadstring(game:HttpGet("https://raw.githubusercontent.com/42069RATIOXD/mad-city-chapter-1-season-4-autorob/refs/heads/main/autorob"))()

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local noclipEnabled = true

-- Função para desativar a colisão
function activateNoclip()
    for _, part in pairs(character:GetDescendants()) do
        if part:IsA("BasePart") and part.CanCollide then
            part.CanCollide = false
        end
    end
end

-- Atualiza o estado do noclip a cada tick
game:GetService("RunService").Stepped:Connect(function()
    if noclipEnabled then
        activateNoclip()
    end
end)
