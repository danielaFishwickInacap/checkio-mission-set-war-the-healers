The healer

...the balance of power was once again not on the knights’ side.

Sir Ronald used the horn one more time to summon the last hope for his army - the healers. The temple they lived in was even closer than the castle from which the first wave of reinforcements arrived. If the healers get here fast enough, they’ll save many lives and the knights will have a chance to win.

The battle continues and each army is losing good warriors. Let's try to fix that and add a new unit type - the Healer.

Healer won't be fighting (his attack = 0, so he can't deal the damage). But his role is also very important - every time the allied soldier hits the enemy, the Healer will heal the ally, standing right in front of him by +2 health points with the heal() method. Note that the health after healing can't be greater than the maximum health of the unit.
For example, if the Healer heals the Warrior with 49 health points, the Warrior will have 50 hp, because this is the maximum for him.

The basic parameters of the Healer:
  health = 60
  attack = 0
Log of the battle with Healer

Example:

fun main() {
    // smoke test
    var chuck = Warrior()
    var bruce = Warrior()
    var carl = Knight()
    var dave = Warrior()
    var mark = Warrior()
    var bob = Defender()
    var mike = Knight()
    var rog = Warrior()
    var lancelot = Defender()
    var eric = Vampire()
    var adam = Vampire()
    var richard = Defender()
    var ogre = Warrior()
    var freelancer = Lancer()
    var vampire = Vampire()
    var priest = Healer()

    check(fight(chuck, bruce) == true)
    check(fight(dave, carl) == false)
    check(chuck.isAlive == true)
    check(bruce.isAlive == false)
    check(carl.isAlive == true)
    check(dave.isAlive == false)
    check(fight(carl, mark) == false)
    check(carl.isAlive == false)
    check(fight(bob, mike) == false)
    check(fight(lancelot, rog) == true)
    check(fight(eric, richard) == false)
    check(fight(ogre, adam) == true)
    check(fight(freelancer, vampire) == true)
    check(freelancer.isAlive == true)
    check(freelancer.health == 14)
    priest.heal(freelancer)
    check(freelancer.health == 16)

    var my_army = Army().apply {
        addUnits(2) { Defender() }
        addUnits(1) { Healer() }
        addUnits(2) { Vampire() }
        addUnits(2) { Lancer() }
        addUnits(1) { Healer() }
        addUnits(1) { Warrior() }
    }

    var enemy_army = Army().apply {
        addUnits(2) { Warrior() }
        addUnits(4) { Lancer() }
        addUnits(1) { Healer() }
        addUnits(2) { Defender() }
        addUnits(3) { Vampire() }
        addUnits(1) { Healer() }
    }
    var army_3 = Army().apply {
        addUnits(1) { Warrior() }
        addUnits(1) { Lancer() }
        addUnits(1) { Healer() }
        addUnits(2) { Defender() }
    }

    var army_4 = Army().apply {
        addUnits(3) { Vampire() }
        addUnits(1) { Warrior() }
        addUnits(1) { Healer() }
        addUnits(2) { Lancer() }
    }

    check(fight(my_army, enemy_army) == false)
    check(fight(army_3, army_4) == true)
    println("OK")
}
