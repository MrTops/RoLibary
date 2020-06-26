# Datastores

For most games it's a requirement to have *data persistance*, data persistance is just the act of saving data to a server, this data can then be retrieved from the server at a later time. Roblox provides a very easy service to do this, ***DataStoreService***, DataStoreService *which I will abbreviate to "DSS"* is the service I will cover to save data, there are other methods but DSS is the easiest one. So before we get into the actual code we need to go over how DSS works. DSS it's self does not store data, but offers a method to get an object called a *datastore*, the datastore contains the actual saving and retrieving methods. There are two types of datastores, datastores and *ordereddatastores*, I won't be going over ordereddatastores here, but they can return data that is ordered, as the name may imply. But how do we use normal datastores, well a datastore can be thought of as a huge table, it contains keys which have a value associated with them. To get a datastore we use the method offered by DSS called ``:GetDatastore(Name)`` this returns a datastore object with the given name. Now on to methods that a datastore actually give you. To get the value we use the method ``:GetAsync(key)`` this returns the data associated with that key, it's async which means it will yield or stop the code until it's returned. To set data we use the method ``:SetAsync(key, newValue)`` this sets the value at the given key. And the last method I'll cover is ``:RemoveAsync(key)`` this removes the key completely. Ok now we've covered the methods let's get into some code samples!

```lua
local DataStoreService = game:GetService("DataStoreService")
local CoinsDatastore = DataStoreService:GetDatastore("Coins")

game.Players.PlayerAdded:Connect(function(player)
    local playerCoins = CoinsDatastore:GetAsync(player.UserId) or 0
    local leaderstats = Instance.new("Folder", player)
    leaderstats.Name = "leaderstats"
    local playerCoinsValue = Instance.new("NumberValue", leaderstats)
    playerCoinsValue.Name = "Coins"
    playerCoinsValue.Value = playerCoins
end)

game.Players.PlayerRemoving:Connect(function(player)
    local leaderstats = player.leaderstats
    local playerCoinsValue = leaderstats.Coins
    CoinsDatastore:SetAsync(player.UserId, playerCoinsValue.Value)
end)

game.ReplicatedStorage.ResetCoins.OnServerEvent:Connect(function(player)
    CoinsDatastore:RemoveAsync(player.UserId)
    player:Kick("Data reset success!")
end)
```

So now to explain the code line by line! First we get the service, then we get a datastore called coins. Then when a player joins the game we get the value. If it's a player's first time then they won't have a value so we do ``or 0`` to give a default value. Then we make a leaderstats folder, then we make a number value and set it's value to playerCoins. We use a number value due to *overflow*, which I go over in my datatypes tutorial. Then when the player leaves we get their data and save it. Then we have a remote event which removes their data and kicks them, we kick them so they can run the PlayerAdded function again. We could also load in the data again.