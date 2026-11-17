# TopDownHeroes

Top-down экшен про героев на Roblox: три класса, прокачка оружия за очки навыков, ультимейты и магазин. Вся игра лежит в одном place-файле — `TopDownHeroes_Visual.rbxlx` (XML-формат Roblox, открывается Roblox Studio).

## Как запустить

1. Открыть `TopDownHeroes_Visual.rbxlx` в Roblox Studio (File → Open from File).
2. Нажать **Play** (F5) — серверная логика поднимется из `ServerScriptService`, клиентская из `StarterPlayerScripts`.

Rojo/скриптов сборки нет: исходники хранятся прямо в place-файле.

## Классы

| Класс | Тип атаки | HP | Урон | Особенность |
|---|---|---|---|---|
| Swordsman | ближний бой, дуга 140° | 150 | 22 | попадает по всем врагам перед собой, самый живучий |
| Archer | стрелы | 100 | 15 | радиус 62, лучшая скорость передвижения |
| Mage | фаерболы с радиусом взрыва | 110 | 26 | урон по группам, самый высокий урон за удар |

Прокачка оружия: Damage / Attack Speed / Range / Crit — по одному очку навыка за уровень.

## Структура

`ReplicatedStorage`

- `Config` — общий конфиг: классы, статы, лимиты (`MaxLevel = 100`, кулдаун рывка и т.д.)
- `SkillRecipes` / `UltRecipes` — рецепты скиллов и ультимейтов
- `UltLib`, `UltMotion`, `UltFX`, `UltImpact` — библиотека, движение, эффекты и попадания ультимейтов
- `Sprites`, `SFX`, `Theme`, `WeaponModels`, `WeaponFX` — визуал, звук и оформление
- `GameServer` — серверная логика матча

`ServerScriptService` → `UltServer` — обработка ультимейтов на сервере

`StarterPlayerScripts`

- `GameClient` — основной клиентский цикл
- `AbilityClient` — ввод и применение способностей
- `ShopClient` — магазин
- `TestAreaClient` + `MapBuilder` / `TestArea` — тестовая арена и её сборка

## Формат файла

`.rbxlx` — обычный XML. Диффы по нему читаются тяжело, поэтому правки в Studio лучше коммитить небольшими порциями и с описанием того, что менялось (какие модули, какие значения в `Config`).
