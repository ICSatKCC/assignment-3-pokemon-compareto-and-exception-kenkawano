# Assignment 3 - Pokemon Comparable, Equals, and Exception

 * 100 points
 * due November, 7th.
 
----

You can use your Pokemon classes from Assignment 2 or you can use mine I have put in the [Assignment2b-PokemonHierarchy-Solution](https://github.com/ICSatKCC/Assignment2b-PokemonHierarchy-Solution) repo. 

Clone this Assignment 3 repo to your computer, then copy the Pokemon class files into it and add them to git. Don't copy **everything** in your Assignment 2 directory because there are hidden files that git makes and you don't want them in this new repository. That will mess up git.

## PokemonException

Your first task is to add a PokemonException class that extends RuntimeException. Don't use the Exception superclass or it will force you to always try/catch it. You must modify the Pokemon.java superclass so that the PokemonException will be thrown whenever the name is set to an empty string. This could happen in the Pokemon superclass constructor (though all subclasses should make it so that can't happen) and in the setName method. See the IllegalFractionException.java class under the Week 4 Resources on Laulima if you need a reference. 

This should pass the two PokemonException jUnit tests in the PokemonTest.java file included in the repo.

----
## Making Pokemon objects Comparable

The second task is to implement the Comparable interface for the Pokemon family of objects. This means you must make a compareTo method for Pokemon objects.

To be consistent with the Java API, the .compareTo method should return 0 if the .equals method returns true. So you must also implement an .equals method.

To say a Pokemon is equal to another Pokemon the following instance variables should match:
 * number
 * name
 * hP
 * cP
 * fastAttack
 * specialAttack
 
The other instance variables are all fixed based on these values so do not need to be checked.

The compareTo method should compare those same instance variables, in that exact order. This makes the number highest precedence for ordering, name next highest precedence, HP next highest, and so on.

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
        pq.add(new Bulbasaur());
        pq.add(new Bulbasaur());
        pq.add(new Bulbasaur("Alpha"));
        pq.add(new Bulbasaur("Beta"));
        pq.add(new Bulbasaur("Gamma"));
```
and then printing the queue in order like this:
```      
      while(pq.size() > 0){
        Pokemon curr = pq.poll();
        System.out.println(curr.toString());
      }
```
should yield results like at the bottom of this page with Pokemon sorted by number first.  If the number is the same, then sorted by the name. If the name is also the same (see Bulbasaurs) then sorted by HP and then CP. Since the species is the name by default, user-set names may sort before or after unnamed Pokemon depending on what the name is.

This should pass the Pokemon compare and equality jUnit tests in PokemonTest.java.

----
## PriorityQueue of Pokemon

The final task is to make a driver program (main method) that implements a Java API PriorityQueue and an API Deque used as a Stack. Make a loop that generates all different species of Pokemon and fills both the PriorityQueue and the Stack with the same 100 Pokemon. You can make like a "batch" loop that does 10 or 20 or so at a time. For example:
```
Pokemon pTemp = new Bulbasaur();
pq.add(pTemp);
stack.push(pTemp);
pTemp = new Squirtle();
pq.add(pTemp);
stack.push(pTemp);
pTemp = new Charmander();
pq.add(pTemp);
stack.push(pTemp);
...
```
Just make sure you have at least 10 of each kind of Pokemon in both structures and they are the same Pokemon. This program should then print out the entire PriorityQueue first (like below) and then the entire Stack. The PriorityQueue list should be sorted based on the new compareTo method and the Stack should be in the reverse order of object generation. This will be like the PokemonGo game options to sort captured Pokemon by number or by when captured.

Printout from PriorityQueue:
----
```
Species: Bulbasaur
Name: Alpha
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 35
CP: 22

Species: Bulbasaur
Name: Beta
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 62
CP: 243

Species: Bulbasaur
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 56
CP: 217

Species: Bulbasaur
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 60
CP: 208

Species: Bulbasaur
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 69
CP: 351

Species: Bulbasaur
Name: Gamma
Number: 001
Height: 0.71
Weight: 6.9
Type: Grass | Poison
HP: 24
CP: 10

Species: Ivysaur
Number: 002
Height: 1.0
Weight: 13.0
Type: Grass | Poison
HP: 95
CP: 663

Species: Venusaur
Number: 003
Height: 2.0
Weight: 100.0
Type: Grass | Poison
HP: 81
CP: 206

Species: Charmander
Number: 004
Height: 0.6
Weight: 8.5
Type: Fire
HP: 26
CP: 14

Species: Charmeleon
Number: 005
Height: 1.1
Weight: 19.0
Type: Fire
HP: 87
CP: 571

Species: Charizard
Number: 006
Height: 1.7
Weight: 90.5
Type: Fire | Flying
HP: 96
CP: 428

Species: Squirtle
Number: 007
Height: 0.5
Weight: 9.0
Type: Water
HP: 49
CP: 113

Species: Wartortle
Number: 008
Height: 1.0
Weight: 22.5
Type: Water
HP: 80
CP: 335

Species: Blastoise
Number: 009
Height: 1.6
Weight: 85.5
Type: Water
HP: 105
CP: 571
```


