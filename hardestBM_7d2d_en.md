# Setting Up Custom Waves

## Before Starting

To begin, you need to deploy a Dedicated server to be able to customize configurations.

## Changing GameStage

In the gamestages.xml file, set the difficultyBonus (for example, 50). For level 40 and day 40, this would result in a 4000 GameStage. Ensure that your GameStage is higher than the value required for the most challenging wave (4086) to know exactly which wave will attack you.

## Modifying Waves

Locate the following line in the same file (line 5415): `<gamestage stage="4086">`. It should be nested within the `<spawner name="BloodMoonHorde">` section. Here lies the description of zombie groups that will appear in our wave. Let's examine an example:

```xml
<spawn group="feralHordeStageGS4086" num="500" maxAlive="256" duration="4" interval="15"/>
```

- group: The name of the group (stored in entitygroups.xml, see "Modifying Groups").
- num: The number of zombies that can spawn for this group.
- maxAlive: The maximum number of zombies that can simultaneously be present. It's not advisable to set it higher than 64, as some zombies may just stand still, creating a heavy load on hardware.
- duration: The wave's duration in hours of in-game time.
- interval: The spawn interval of the specific group, in minutes of in-game time.

## Modifying Groups

Change the zombies in the groups of our wave. Similar to the example above, let's consider the group `feralHordeStageGS4086`. Navigate to the entitygroups.xml file and search for the name of this wave, something like:

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

Here, the zombie names and their spawn chances within this group are listed. If nothing is specified, the spawn chance is 100%. You can view the zombie names and their appearances in the creative game mode with the "dm" mod enabled by pressing F6 and examining the popup window.

## Example Configuration from the Video

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
