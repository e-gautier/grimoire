# Polymorphism
> Polymorphism is about providing a single interface for multiple types.
## Static vs dynamic
**Static dispatch**: fastest, polymorphism resolved at compile time.

**Dynamic dispatch**: slowest, polymorphism resolved at run time.
## Types
```plantuml
@startuml
object Polymorphism
object AdHoc
object Universal
object Overriding
object Coercion
object Parametric
object Subtyping
object Operator
object Function
object Widening
object Narrowing
object Covariant
object Contravariant
object Generics
Polymorphism <|-- AdHoc
Polymorphism <|-- Universal
AdHoc <|-- Overriding
AdHoc <|-- Coercion
Universal <|-- Parametric
Universal <|-- Subtyping
Overriding <|-- Operator
Overriding <|-- Function
Coercion <|-- Widening
Coercion <|-- Narrowing
Subtyping <|-- Covariant
Subtyping <|-- Contravariant
Parametric <|-- Generics
@enduml
```
<!-- tabs:start -->
#### ** Ad-Hoc **
#### Overriding
TODO
#### Coercion
TODO
#### ** Universal **
#### Subtyping (or inclusion)
```plantuml
@startuml
Animal <|-- Cat
Animal <|-- Dog

Animal : {abstract} talk()
Cat : talk()
Dog : talk()
@enduml
```
```java
abstract class Animal {
    abstract String talk();
}

class Cat extends Animal {
    String talk() {
        return "Meow!";
    }
}

class Dog extends Animal {
    String talk() {
        return "Woof!";
    }
}

static void letsHear(final Animal a) {
    println(a.talk());
}

static void main(String[] args) {
    letsHear(new Cat());
    letsHear(new Dog());
}
```
```
Meow!
Woof!
```
#### Parametric
Parametric is about instancing a generic type with actual type arguments.
```java
interface Collection<E>  { 
  public void add(E x);
  public Iterator<E> iterator();
}

static void main(String[] args) {
  Collection<Animal> collection = new LinkedList<Animal>();
}
```
<!-- tabs:end -->
## Duck typing
TODO
## Sources
> https://stackoverflow.com/tags/polymorphism/info
>
> https://en.wikipedia.org/wiki/Polymorphism_(computer_science)
>
> https://www.angelikalanger.com/GenericsFAQ/JavaGenericsFAQ.html
>
> https://javapapers.com/core-java/java-polymorphism/