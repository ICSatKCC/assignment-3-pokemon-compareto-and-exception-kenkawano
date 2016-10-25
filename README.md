# Assignment 3 - Pokemon Comparable, Equals, and Exception
 * 50 points
 * due October, 3rd.

----
## Making Pokemon objects Comparable

This task is to implement the Comparable interface for all of the Pokemon family of objects. This means you must make a compareTo method for Pokemon objects.

To be consistent with the Java API, the .compareTo method should return 0 if the .equals method returns true. So you must also implement an .equals method.

To say a Pokemon is equal to another Pokemon the following instance variables should match:
 * number
 * name
 * hP
 * cP
 * fastAttack
 * specialAttack
 
The other instance variables are all fixed based on these values so do not need to be checked.

The compareTo method should also compare those same instance variables, in that exact order. This makes the number highest precedence for ordering, name next highest precedence, HP next highest, and so on.

Adding Pokemon to Java API PriorityQueue *pq* in any order like so:
```
        pq.add(new Wartortle());
        pq.add(new Venusaur());
        pq.add(new Squirtle());
        pq.add(new Ivysaur());
        pq.add(new Charmeleon());
        pq.add(new Charmander());
        pq.add(new Charizard());
        pq.add(new Bulbasaur());
        pq.add(new Blastoise());
        pq.add(new Bulbasaur("Alpha"));
        pq.add(new Bulbasaur("Beta"));
        pq.add(new Bulbasaur("Gamma"));
```
And then printing the queue in order like this:
```      
      while(pq.size() > 0){
        Pokemon curr = pq.poll();
        System.out.println(curr.toString());
      }
```
Should yield results like below with Pokemon sorted by number first. If the number is the same, then sorted by the name. If the name is also the same (see Bulbasaurs) then sorted by HP and then CP. Since the species is the name by default, then user-set names may sort before or after unnamed Pokemon depending on the name: 
```
Species: Bulbasaur
Name: Alpha
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 29
CP: 11

Species: Bulbasaur
Name: Beta
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 21
CP: 10

Species: Bulbasaur
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 47
CP: 104

Species: Bulbasaur
Name: Gamma
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 62
CP: 270

Species: Ivysaur
Number: 002
Height: 1.0
Weight: 13.0
Type: Grass | Poison
HP: 87
CP: 587

Species: Venusaur
Number: 003
Height: 2.0
Weight: 100.0
Type: Grass | Poison
HP: 107
CP: 571

Species: Charmander
Number: 004
Height: 0.6
Weight: 8.5
Type: Fire
HP: 57
CP: 213

Species: Charmeleon
Number: 005
Height: 1.1
Weight: 19.0
Type: Fire
HP: 87
CP: 501

Species: Charizard
Number: 006
Height: 1.7
Weight: 90.5
Type: Fire | Flying
HP: 75
CP: 204

Species: Squirtle
Number: 007
Height: 0.5
Weight: 9.0
Type: Water
HP: 29
CP: 10

Species: Wartortle
Number: 008
Height: 1.0
Weight: 22.5
Type: Water
HP: 70
CP: 184

Species: Blastoise
Number: 009
Height: 1.6
Weight: 85.5
Type: Water
HP: 52
CP: 39

```
---
 
   

