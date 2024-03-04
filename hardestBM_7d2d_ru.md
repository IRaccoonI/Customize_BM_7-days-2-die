# Настройка собственной волны

## Перед началом

Для начала нужно развернуть Dedicated server, чтобы можно было настраивать конфигурации.

## Изменяем Уровень игры (GameStage)

В файле gamestages.xml устанавливаем значение difficultyBonus (например, 50). Для 40-го уровня и 40-го дня это будет 4000 GameStage. Необходимо выбрать такое значение, чтобы ваш GameStage был больше, чем требуемое значение для максимально сложной волны (4086). Это нужно, чтобы точно знать, какая волна нападет на вас.

## Изменяем Волны

Находим в том же файле следующую строку (5415-я строка): `<gamestage stage="4086">`. Она должна быть вложена в секцию `<spawner name="BloodMoonHorde">`. Здесь хранится описание групп зомби, которые появятся на нашей волне. Рассмотрим пример: 

```xml
<spawn group="feralHordeStageGS4086" num="500" maxAlive="256" duration="4" interval="15">
```

- group: Название группы (хранится в файле entitygroups.xml, см. "Изменяем Группы").
- num: Количество зомби, которое может заспавниться для данной группы.
- maxAlive: Максимальное количество зомби, которое может одновременно находиться. Не рекомендуется устанавливать больше 64, так как некоторые зомби будут просто стоять на месте, что создаст большую нагрузку на железо.
- duration: Длительность волны, в часах по игровому времени.
- interval: Интервал спавна конкретной группы, в минутах по игровому времени.

## Изменяем Группы

Изменяем зомби в группах нашей волны. Как в случае выше, рассмотрим пример группы `feralHordeStageGS4086`. Переходим в файл entitygroups.xml и ищем название этой волны, что-то вроде:

```xml
<entitygroup name="feralHordeStageGS4086">
    zombieJoe
    zombieMarleneFeral
    zombieMoeRadiated
    zombieTomClarkFeral, .05
    zombieSoldierRadiated
    zombieMoe
    zombieMaleHazmat
    animalZombieVulture, .3
    zombieDarleneRadiated
    zombieMaleHazmatRadiated, .9
    animalZombieDog
    zombieSkateboarderFeral
    zombieNurse, .3
    zombieFatCop
    zombieBusinessManFeral
</entitygroup>
```

Здесь указаны названия зомби и их шанс заспавниться в рамках этой группы. Если ничего не указано, шанс спавна равен 100%. Названия зомби и их внешний вид можно посмотреть в творческой игре с включенным в консоли модом "dm", нажав на клавишу F6 и просмотрев всплывающее окно.

## Пример настройки из видео

```xml
<gamestage stage="4086">
    <spawn group="feralHordeStageGS4086" num="500" maxAlive="256" duration="4" interval="15"/>
    <spawn group="feralHordeStageDemolition" num="500" maxAlive="256" duration="1" interval="10"/>
    <spawn group="feralHordeStageGS4086" num="500" maxAlive="256" duration="6" interval="15"/>
</gamestage>
```

```xml
<entitygroup name="feralHordeStageGS4086">
    zombieSpiderFeral, .5
    zombieDemolition
    zombieBikerRadiated
    zombieBikerRadiated
    zombieMaleHazmatRadiated
    zombieSoldierRadiated
    zombieSoldierRadiated
    zombieSkateboarderRadiated
    zombieFatCopRadiated
    zombieFatCopRadiated, .3
    animalZombieVultureRadiated, .7
    animalZombieVulture, .7
</entitygroup>
<entitygroup name="feralHordeStageDemolition">
    zombieDemolition
    zombieDemolition
    zombieDemolition
    zombieDemolition
</entitygroup>
```