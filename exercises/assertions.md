# On assertions

Answer the following questions:

1. The following assertion fails `assertTrue(3 * .4 == 1.2)`. Explain why and describe how this type of check should be done.

2. What is the difference between `assertEquals` and `assertSame`? Show scenarios where they produce the same result and scenarios where they do not produce the same result.

3. In classes we saw that `fail` is useful to mark code that should not be executed because an exception was expected before. Find other uses for `fail`. Explain the use case and add an example.

4. In JUnit 4, an exception was expected using the `@Test` annotation, while in JUnit 5 there is a special assertion method `assertThrows`. In your opinion, what are the advantages of this new way of checking expected exceptions?

## Answer

## EX 1

### 1.1

Pas possible de vérifier l'égalité entre deux floats, faut fixer un interval de différence maximale autorisée (valeurs peut être différentes à .000000001...)

`Assert.assertEquals(0.0012f, 0.0014f, 0.0002);`

### 1.2

assertSame : vérifie que les deux valeurs passées en paramètre réfèrent au même objet

assertEquals : vérifie que les deux valeurs passées en param sont égales

### 1.3

`String tmp = new String("detox");`

`String tmpRef = tmp;`

`assertSame(tmp, tmpRef);` 	 	 // True

`assertSame(tmp, new String("detox"));`  	 // False

`assertEquals(tmp, tmpRef);`		 // True

`assertEquals(tmp, new String("detox"));`  // True

### 1.4
.fail() ->

-> tests incomplets (à ne pas executer), exception à lancer, exception non attendue, tester condition, returning before

### 1.5
assertThrows permet une utilisation plus flexible, sur des blocs de code mieux délimités. L'objet qui renvoie l'exception est également renvoyé avec
cette méthode