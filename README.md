localOrionLib=loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "Whitexhub", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

MainTab:AddButton({
Name = "Ativar Anti Void Protection",
Callback = function()
antiVoidProtection()
end
})

MainTab:AddButton({
Name = "Criar Ferramenta de Teletransporte",
Callback = function()
createTpTool()
end
})

-- Atualizar a lista de jogadores
local function updatePlayerList()
local players = {}
for _, p in ipairs(game.Players:GetPlayers()) do
table.insert(players, p.Name)
end
playerDropdown:Refresh(players, true)
end

-- Atualizar a lista de jogadores quando um jogador entra ou sai
game.Players.PlayerAdded:Connect(updatePlayerList)
game.Players.PlayerRemoving:Connect(updatePlayerList)

-- Inicializar a lista de jogadores
updatePlayerList()

OrionLib:Init()
