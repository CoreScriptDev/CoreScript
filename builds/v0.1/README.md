# CoreScript
v0.1

# CoreScript (csc) Syntax

Dies ist eine umfassende Übersicht über die Programmiersprache **CoreScript (csc)**.  
Alle Beispiele sind direkt ausführbar.

---

## 1. Variablen (Variables)

### Ganzzahlen (Integers)
```csc
num = 5 // Dies ist eine Ganzzahl
```

### Fließkommazahlen (Floats)
```csc
num = 33.7 // Dies ist eine Fließkommazahl
```

### Zeichenketten (Strings)
```csc
word = "Hello"
another_word = 'World!'
```

### Listen (Lists)
```csc
mylist = [1, 2, 3, 4, 5]
```

### Wahrheitswerte (Booleans)
```csc
cool = true
bad = false
```

### Null-Wert (Null)
```csc
nothing = null
```

---

## 2. Kommentare

Einzeilige Kommentare beginnen mit `//`:
```csc
// Dies ist ein Kommentar
```

---

## 3. Operatoren

### Arithmetische Operatoren
```csc
a = 5
b = 3
sum = a + b
diff = a - b
prod = a * b
div = a / b
neg = -a
```

### Vergleichsoperatoren
```csc
a == b
a != b
a < b
a > b
a <= b
a >= b
```

---

## 4. Bedingungen (Conditionals)

### If / Else If / Else
```csc
x = 10

if(x > 10) {
    cmd.out("x ist größer als 10")
} else if(x == 10) {
    cmd.out("x ist 10")
} else {
    cmd.out("x ist kleiner als 10")
}
```

### Match / Case
```csc
a = 2

match(a) {
    case 1: {
        cmd.out("a ist 1")
    }
    case 2: {
        cmd.out("a ist 2")
    }
    default: {
        cmd.out("a ist etwas anderes")
    }
}
```

---

## 5. Schleifen

### For
```csc
for(i, 1, 6, 1) {
    cmd.out(i)  // gibt 1 bis 5 aus
}
```

### Foreach
```csc
mylist = [10, 20, 30]

foreach(value in mylist) {
    cmd.out(value)
}
```

---

## 6. Funktionen

```csc
func add(a, b) {
    return(a + b)
}

result = add(5, 7)
cmd.out(result)  // Ausgabe: 12

func return_null() {
    return
}
```

---

## 7. Klassen

```csc
class Person {
    func __setup__(name, age) {
        // Keine Referenz auf das Objekt selbst verfügbar
        name_var = name
        age_var = age
        cmd.out("Person erstellt: " + name_var + ", Alter " + age_var)
    }

    func greet() {
        cmd.out("Hallo!")
    }
}

p = Person("Max Mustermann", 25)
p.greet()  // Ausgabe: Hallo!
```

---

## 8. Module und Imports

```csc
using cmd
using net
using sys
using time
```

### cmd
```csc
name = cmd.in("Wie heißt du?")
cmd.out("Hi "+name)
```

### net
```csc
s = net.Server()

@s.route('/')
func home() {
    return("Hello from CoreScript!")
}

s.run()
```

### sys
```csc
sys.exit()       // beendet das Programm
sys.run("curl ascii.live/rick")    // führt Befehl aus
```

### time
```csc
t = time.time()
cmd.out(t)
```

---

## 9. Dekoratoren

```csc
func log_before(f) {
    func wrapper() {
        cmd.out("Now!")
        f()
    }
    return(wrapper)
}

@log_before
func say_hello() {
    cmd.out("Hello")
}

say_hello()
// Ausgabe:
// Now!
// Hello
```

---

## 10. Beispielskript (alle Features)

```csc
using cmd
using time

// Variablen
num = 42
name = "Max Mustermann"
mylist = [1, 2, 3]

// Funktionen
func square(x) {
    return(x * x)
}

// Dekorator
func log_before(f) {
    func wrapper() {
        cmd.out("Running function:")
        f()
    }
    return(wrapper)
}

@log_before
func greet() {
    cmd.out("Hello " + name)
}

// Klassen
class Animal {
    func __setup__(species) {
        species_var = species
        cmd.out("Animal erstellt: " + species_var)
    }
    func describe() {
        cmd.out("This is an animal")
    }
}

dog = Animal("Dog")

// Schleifen
for(i, 1, 4, 1) {
    cmd.out(i)
}

foreach(x in mylist) {
    cmd.out(square(x))
}

// Bedingungen
if(num > 50) {
    cmd.out("Num ist groß")
} else if(num == 42) {
    cmd.out("Num ist die Antwort")
} else {
    cmd.out("Num ist klein")
}

// Match
match(num) {
    case 1: { cmd.out("Eins") }
    case 42: { cmd.out("42!") }
    default: { cmd.out("Andere Zahl") }
}

// Funktionen und Dekorator aufrufen
greet()

// Zeit
cmd.out("Aktuelle Zeit: " + time.time())
```