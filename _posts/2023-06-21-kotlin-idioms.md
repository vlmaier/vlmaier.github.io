---
layout: post
title: Use Kotlin Idioms
author: Vladas Maier
tags: idioms kotlin
---

Official Kotlin documentation provides a [variaty of idioms](https://kotlinlang.org/docs/idioms.html). Kotlin idioms are powerful techniques that allow developers to write clean, consice and expressive code. These idioms help eliminate boilerplate code, simplify common tasks and leverage the full potential of the Kotlin language.

In this blog post I will show you a selected range of Kotlin idioms (I use myself) and provide examples of "Dos and Don'ts" to cause the Aha! moment especially if you are Java Developer like me who is looking at Kotlin like this for a while now:

<img class="meme" src="/assets/images/java-kotlin-meme.jpeg">

By understanding and applying these idioms, you can enhance your coding experience and produce high-quality and clean Kotlin code.

> Disclaimer: If you are a Marvel fan and only Marvel then I hereby apologize for my examples that will follow.

### 1. Creating DTOs

#### Don't:

~~~ kotlin
class Superhero {
    var name: String = ""
    var abilities: List<String> = listOf()
}
~~~

This is more of a Java-style to declare a DTO.

#### Do "Kotlin Idiom: Data Classes":

~~~ kotlin
data class Superhero(var name: String, var abilities: List<String>)
~~~

The Kotlin-way is using a `data` class.

### 2. Filtering a list

#### Don't:

~~~ kotlin
val justiceLeague = listOf(
    "Batman", "Superman", "Wonder Woman", "Flash", "Aquaman", "Cyborg"
)
val creativeHeroNames = mutableListOf<String>()
for (hero in justiceLeague) {
    if (hero.endsWith("man")) {
        creativeHeroNames.add(hero)
    }
}
~~~

Forget about loops when working with collections.

#### Do "Kotlin Idiom: Filter":

~~~ kotlin
val justiceLeague = listOf(
    "Batman", "Superman", "Wonder Woman", "Flash", "Aquaman", "Cyborg"
)
val creativeHeroNames = justiceLeague.filter { it.endsWith("man") }
~~~

There is probably always a cleaner way by using a lambda expression.

### 3. Checking the presence of an element in a collection

#### Don't:

~~~ kotlin
...
val foundBatman = justiceLeague.contains("Batman")
~~~

This is the straightforward way of checking the presence of an element in a collection. However, there is another way.

#### Do "Kotlin Idiom: in Operator":

~~~ kotlin
...
val foundBatman = "Batman" in justiceLeague
~~~

Use the `in` operator instead. You can also use the logical NOT operator in front of `!in`.

### 4. String interpolation

#### Don't:

~~~ kotlin
val name = "Batman"
val greeting = "I am " + name + " and my name is " + name.length + " character(s) long."
~~~

Forget Java string concatenation; all those ugly pluses in between. We don't do that in Kotlin.

#### Do "Kotlin Idiom: String Templates":

~~~ kotlin
...
val greeting = "I am $name and my name is ${name.length} character(s) long."
~~~

In Kotlin we have String templates. Much more pleasant to look at.

### 5. Model conversion mappers

#### Don't:

~~~ kotlin
fun toSuperheroDto(superhero: Superhero): SuperheroDto {
    return SuperheroDto(
        name = superhero.name,
        power = superhero.power,
        amountOfAbilities = superhero.abilities.size,
    )
}
~~~

I'm not saying that you should only write extension functions in Kotlin, but keep in mind that there is another way that can be more concise.

#### Do "Kotlin Idiom: Extension functions":

~~~ kotlin
fun Superhero.toSuperheroDto(): SuperheroDto = SuperheroDto(
    name = name,
    power = power,
    amountOfAbilities = abilities.size,
)
~~~

### 6. Execute a statement if null

#### Don't:

~~~ kotlin
val romances = mapOf(
    "Batman" to "Catwoman",
    "Superman" to "Lois Lane",
    "Wonder Woman" to "Steve Trevor",
    "Flash" to "Iris West",
    "Aquaman" to "Mera",
    "Cyborg" to null
)
val hero = "Cyborg"
if (romances[hero] == null) {
    throw RomanceNotFoundException("Romance not found for our hero $hero")
}
val romance = romances[hero]
~~~

There is a cleaner way.

#### Do "Kotlin Idiom: Elvis Operator":

~~~ kotlin
...
val romance = romances[hero] ?: throw RomanceNotFoundException("Romance not found for our hero $hero")
~~~

Elvis operator is your friend here. Assignment and error handling in one single line.

### 7. Execute a block if not null

#### Don't:

~~~ kotlin
val batman: String? = null
if (batman != null) {
    println("I am the dark knight")
}
~~~

If you are tired of writing if-not-null statements I have good news for you.

#### Do "Kotlin Idiom: Safe Call Operator with let":

~~~ kotlin
...
batman?.let {
    println("I am the dark knight")
}
~~~

In Kotlin you can use the `let` scope function to execute a specified function block if the value is not null. Next time you want to print out non-null items within a collection recall `let` ;)

### 8. Return on when statement

#### Don't:

~~~ kotlin
fun getNickname(superhero: String): String {
    return when (superhero) {
        "Aquaman" -> "King of the Seven Seas"
        "Batman" -> "Dark Knight"
        "Cyborg" -> "Vic"
        "Flash" -> "Fastest Man Alive"
        "Superman" -> "Man of Steel"
        "Wonder Woman" -> "Amazon Princess"
        else -> "None"
    }
}
~~~

You can skip the `return` keyword if you are using when like a Java `switch` statement. 

#### Do "Kotlin Idiom: When Expression":

~~~ kotlin
fun getNickname(superhero: String): String = when (superhero) {
    "Aquaman" -> "King of the Seven Seas"
    "Batman" -> "Dark Knight"
    "Cyborg" -> "Vic"
    "Flash" -> "Fastest Man Alive"
    "Superman" -> "Man of Steel"
    "Wonder Woman" -> "Amazon Princess"
    else -> "None"
}
~~~

Since `when` is a expression (in Kotlin) you can return it directly and save 2 LOC.

### 9. Return on try-catch

#### Don't:

~~~ kotlin
val villains = listOf(
    "2-F4c3", "J0k3r", "Penguin", "R1ddl3r"
)
fun getNumberFromName(villain: String): Int {
    try {
        return villain.filter { it.isDigit() }.toInt()
    } catch (e: NumberFormatException) {
        return 0
    }
}
~~~

There is no other way in Java than to write two return statements in the try-catch block. But in Kotlin is...

#### Do "Kotlin Idiom: try-catch Expression":

~~~ kotlin
...
fun getNumberFromName(villain: String): Int = try {
    villain.filter { it.isDigit() }.toInt()
} catch (e: NumberFormatException) {
    0
}
~~~

Since `try-catch` is also a expression you can return it directly (and omit the `return` completely) and save 2 LOC once again.

### 10. Calling multiple methods on an object instance 

Last but not least my favourite...

#### Don't:

~~~ kotlin
class Superhero {
    fun fight(powerLevel: Int) { ... }
    fun fly() { ... }
    fun talkingBig(message: String) { ... }
}
val superman = Superhero()
superman.fly()
for (powerLevel in 1..4) {
    superman.fight(powerLevel)
}
superman.talkingBig("See, the bullets don't work.")
~~~

You are probably asking yourself "How can I write this code more concise?". Once I saw it for myself I couldn't go back.

#### Do "Kotlin Idiom: with":

~~~ kotlin
...
val superman = Superhero()
with(superman) {
    fly()
    for (powerLevel in 1..4) {
        fight(powerLevel)
    }
    talkingBig("See, if the bullets don't work, right, why the punching?")
}
~~~

If you are using `with` scope function you get rid of writing the object name every time you want to call a function on it. It provides so much readability.

I hope you could learn something new and had at least one Aha! moment.

Cheers, happy coding :)