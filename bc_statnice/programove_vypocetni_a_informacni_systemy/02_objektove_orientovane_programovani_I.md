# Objektově orientované programování I
## Zapouzdření
= sbalení dat (proměnných) a kódu, který s daty pracuje, do jedné jednotky

Vytvořením třídy vytváříme zapouzdření, proměnné a data z této třídy mohou být přistupována pouze pomocí metod, které tato třída nabídne.
### V Javě
- vytváříme privátní proměnné
- k proměnným vytvoříme veřejné settery a gettery, pomocí kterých lze manipulovat s proměnnými
- klíčová slova private a public

```java
public class Library {
    private String name;
    private int booksTotal;
    public String getName() {
        return name;
    }
    public void setName(String newName) {
        name = newName;
    }
    ...
}
```

## Dědičnost
= třída (podtřída, potomek) dědí vlastnosti a funkce jiné třídy (nadtřídy, předka)

Vytváříme hierarchii tříd a neopakujeme kód.

### V Javě
- každá třída je potomkem třídy Object.
- Potomek dědí všechny atributy, některé metody může upravit a také může přidat nové atributy a metody.
- klíčová slova extend a super.

```java
public class Animal {
    private int age;
    private int eaten;
    public boolean hungry() {
        if (eaten < 1) {
            return True;
        }
        return False;
    }   
}

public class Shark extends Animal {
    private String color;
    public boolean hungry() {
        eaten = eaten - 1;
        return super.hungry();
    }   
}
```

## Polymorfismus
= umožňuje používat metodu nadtřídy, i když je v podtřídě přepsaná, tzn. můžeme ji použít na různých objektech a bude se chovat různě.

### V Javě
- nelze přepsat metodu v podtřídě na public (pokud byla private)
- nelze přepsat metodu, která je final, statická, private, má jinou návratovou hodnotu nebo je to konstruktor.
- _overriding_ = přepsání významu metody
- _overloading_ = přidání významů metodě, např.: `void fun(int a)`, `void fun(int a, int b)`, `void fun(char a)`
