-- Auto Farm Simples para Blox Fruits
getgenv().AutoFarm = true

while getgenv().AutoFarm do
    -- Procurar por inimigos próximos
    for i, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
        if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
            -- Teleportar até o inimigo
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 5, 0)
            -- Bater no inimigo até a vida zerar
            repeat
                wait(0.1)
                -- Ataca usando a Primeira Skill (Z) se disponível
                local vim = game:service("VirtualInputManager")
                vim:SendKeyEvent(true, "Z", false, game)
                vim:SendKeyEvent(false, "Z", false, game)
            until v.Humanoid.Health <= 0 or not getgenv().AutoFarm
        end
    end
    wait(0.5)
end
