# Настройка собственной волны

## Перед началом

Для начала нужно развернуть Dedicated server, что бы можно было настраивать конфиги

## Меняем GameStage

В файле gamestages.xml ставим difficultyBonus(например 50, для 40 уровня и 40 дня будет 4000 GameStage) такой, что бы ваш GameStage был больше, чем значение которое требуется для максимально сложной волны(4086), для того что бы точно знать какая волна на вас нападёт

## Меняем Волны

Ищем в том же файле такую строчку(5415 строчка) `<gamestage stage="4086">` она должна быть вложена в такую секцию `<spawner name="BloodMoonHorde">`.
Тут хранится описание групп зомби которое будут появлятся на нашей волне, рассмотрим пример
`group="feralHordeStageGS4086"     num="500" maxAlive="256" duration="4" interval="15"`:
    - group: Название групы(хранящееся в файле entitygroups.xml, рассмотрим в пункте 4.)
    - num: Колличество зомби которое может заспавнится для данной группы
    - maxAlive: Максимальное колличество зомби которое может одновременно находится, больше 64 ставить не советую, некоторые зомби будут просто стоять на месте, и очень большая нагрузка на железо
    - duration: Длительность волны, в часах по игровому времени
    - interval: Интервал спавна конкретной группы, в минутах по игровому времени

## Меняем Группы

Изменяем зомби в группах нашей волны, как в случае сверху рассмотрим пример группы `feralHordeStageGS4086`, Идём в файл entitygroups.xml, делаем поиск названия этой волны, получаем что то наподобе такого

```
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

Тут указаны названия зомби, и их шанс заспавнится в рамках этой группы, если ничего не указано шанс спавна 100%.
Названия зомби и их внешний вид можно посомтреть в творческой игре с прописанным в консоль `dm` модом, нажав на клавишу f6, во всплывающемся окне


## Пример настройки из видео
```
<gamestage stage="4086">
    <spawn group="feralHordeStageGS4086"     num="500" maxAlive="256" duration="4" interval="15"/>
    <spawn group="feralHordeStageDemolition" num="500" maxAlive="256" duration="1" interval="10"/>
    <spawn group="feralHordeStageGS4086"     num="500" maxAlive="256" duration="6" interval="15"/>
</gamestage>
```

```
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