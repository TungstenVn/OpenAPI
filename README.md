# OpenAPI
 API for people who want help with BedrockPlay development
 
## Documentation:
 
### Economy:
 - Adding coins for player
 ```php
/**
 * @var \pocketmine\Player $player
 * @var int $coins
 */
\bedrockplay\openapi\economy\Economy::addCoins($player, $coins);
```

- Obtaining coins
```php
/** @var \pocketmine\Player $player */
\bedrockplay\openapi\economy\Economy::getCoins($player, function(int $amount) use ($player) {
    $player->sendMessage("§9Account> §aCurrently you have $amount coins!");
});
```

### Multi-Server API:
- Checking if server is online and transferring player here if so
```php
$server = \bedrockplay\openapi\servers\ServerManager::getServer("Lobby-2");
if($server->isOnline()) {
    /** @var \pocketmine\Player $player */
    $server->transferPlayerHere($player);
}
```

### Ranks
- Obtaining player's rank
```php
/** @var \pocketmine\Player $player */
$rank = \bedrockplay\openapi\ranks\RankDatabase::getPlayerRank($player);
$player->sendMessage("§9Account> §aYour rank: " . $rank->getName());
```