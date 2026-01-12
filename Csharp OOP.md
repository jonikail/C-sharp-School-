### **==OOP (Object-Oriented Programming)==**

OOP se bazează pe **obiecte** care combină **datele** și **metodele** într-o singură structură.

---
### **==Avantaje OOP==**

- Cod **clar și ușor de întreținut**
    
- **Reducerea duplicării** codului (DRY)
    
- **Reutilizare** mai bună a codului
---
### **==Clase și Obiecte==**

- **Clasa** = șablon care definește date și metode
    
- **Obiectul** = instanță a unei clase
---
### **==Access Modifiers (Modificatori de Acces)==**

Access modifiers controlează **vizibilitatea** membrilor unei clase (câmpuri sau metode).

| **public**    | accesibil din orice clasă                                 |
| ------------- | --------------------------------------------------------- |
| **private**   | accesibil **doar în aceeași clasă**                       |
| **protected** | accesibil în aceeași clasă și în clasele care o moștenesc |
| **internal**  | accesibil **în interiorul aceleiași asamblări/proiect**   |

(Default: dacă nu specifici nimic, membrii sunt `private`)

---
### **==Proprietăți în C# (Properties)==**

- Proprietățile oferă un mod **sigur și controlat** de a accesa și modifica **câmpurile private** ale unei clase. Ele sunt ca o combinație între o **variabilă** și o **metodă**.
    
- O proprietate are două părți principale:
    
    - **get** – returnează valoarea unui câmp.
        
    - **set** – atribuie o valoare unui câmp (folosește cuvântul cheie `value`).
    
Exemplu:
   ```csharp
class Person
{
	private string name; // câmp privat

	public string Name   // proprietate
	{
		get { return name; }
		set { name = value; }
	}
}
    ```
Exista varianta prescurtata a codului de mai sus:
  ```csharp
class Person
{
	public string Name {get; set;}
}
	    ```
Apoi poți folosi proprietatea ca pe o variabilă:
  ```csharp
Person p = new Person();
p.Name = "Ana";
Console.WriteLine(p.Name);
    ```
---
### **==Moștenire în C# (Inheritance)==**

- **Moștenirea** permite unei clase să preia **câmpuri și metode** dintr-o altă clasă.
    
- **Clasa de bază (părinte)** → oferă membri.
    
- **Clasa derivată (copil)** → moștenește membri.
    
- Se folosește simbolul `:` pentru moștenire.
    
- O clasă `sealed` **nu poate fi moștenită**.

Exemplu:
  ```csharp
public class Person
{
	public string Name; // cimp public
}

class Student : Person
{
	public float Grade { get; set; }
	 //Cimp private Grade cu geter si seter public
}
    ```
    
```csharp
Student student = new Student();

student.Name = "Iftemie"; //Clasa student mosteneste campul Name

student.Grade = 7.5f;

Console.WriteLine($"Media studentului {student.Name} este :{student.Grade} ");
```
---
### **==Polimorfism în C#==**

- Polimorfism = „**multe forme**”: aceeași metodă poate avea **comportamente diferite** în clase diferite.
    
- Folosește **moștenirea** + metode **virtual/override**.
    
- `virtual` → metoda din clasa de bază poate fi suprascrisă.
    
- `override` → metoda din clasa derivată înlocuiește metoda de bază.
    
- Permite **apeluri uniforme**, dar comportament specific fiecărui obiect.
---

### **==Overload vs Override==**

| Caracteristică             | Suprascriere (Override)                                         | Supraîncărcare (Overload)                          |     |
| -------------------------- | --------------------------------------------------------------- | -------------------------------------------------- | --- |
| **Definiție**              | Modifică comportamentul unei metode din clasa de bază           | Aceeași metodă, dar cu parametri diferiți          |     |
| **Legătură cu moștenirea** | Necesită moștenire între clase                                  | Nu necesită moștenire                              |     |
| **Cuvinte cheie**          | `virtual` în clasa de bază, `override` în derivată              | Niciun cuvânt cheie special                        |     |
| **Parametri**              | Trebuie să aibă **aceeași semnătură** ca metoda de bază         | Parametrii trebuie să fie diferiți (număr sau tip) |     |
| **Exemplu**                | `myAnimal.MakeSound()` → metoda din `Dog` dacă obiectul e `Dog` | `Add(2,3)`, `Add(2.5,3.5)`, `Add(1,2,3)`           |     |
Exemplu override:
```csharp
using System;

class Animal
{
    public virtual void Sunet()
    {
        Console.WriteLine("Sunet animal");
    }
}

class Caine : Animal
{
    public override void Sunet()
    {
        Console.WriteLine("Latrat");
    }
}

class Program
{
    static void Main()
    {
        Animal a = new Caine();
        a.Sunet();  // Output: Latrat
    }
}

```

Exemplu overload:
```csharp
using System;

class Calc
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public int Add(int a, int b, int c)
    {
        return a + b + c;
    }
}

class Program
{
    static void Main()
    {
        Calc c = new Calc();
        Console.WriteLine(c.Add(2, 3));     // 5
        Console.WriteLine(c.Add(1, 2, 3));  // 6
    }
}

```
---

### **==Abstracție în C#==**

**Abstracția** ascunde detaliile interne și afișează doar **ce este esențial**. Se realizează folosind **clase abstracte**, **metode abstracte** și **interfețe**.
**Clase abstracte**

- O **clasă abstractă** nu poate fi folosită pentru a crea obiecte direct.
    
- Trebuie **moștenită** de o altă clasă pentru a fi folosită.
    
- Poate conține:
    
    - **Metode abstracte** (fără corp)
        
    - **Metode obișnuite** (cu implementare)
 **Metode abstracte**

- Sunt declarate fără corp.
    
- Implementarea lor se face în **clasa derivată** (folosind `override`).

Exemplu de abstracție:
```csharp
// Abstract class
abstract class Animal
{
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep()
  {
    Console.WriteLine("Zzz");
  }
}

// Derived class (inherit from Animal)
class Pig : Animal
{
  public override void animalSound()
  {
    // The body of animalSound() is provided here
    Console.WriteLine("The pig says: wee wee");
  }
}

class Program
{
  static void Main(string[] args)
  {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();  // Call the abstract method
    myPig.sleep();  // Call the regular method
  }
}
```

 **Interfețe

- **Interfața** este o **abstracție totală**: declară doar metode și proprietăți fără implementare (nu are corp).
    
- Prin convenție, numele interfeței începe cu **„I”** (de exemplu `IAnimal`).
    
- Membrii unei interfețe sunt **impliciti publici și abstracti**.
    
- Nu poate conține **câmpuri** și nu poate fi instanțiată ca obiect.
    
- O clasă **implementează** o interfață folosind `:` și trebuie să ofere **implementarea tuturor metodelor și proprietăților** din interfață.
    
- Interfețele sunt utile pentru **abstracție**, **contracte clare** între clase și pentru a permite **implementarea multiplă** (o clasă poate implementa mai multe interfețe).
  
```csharp
// Interface
interface IAnimal 
{
  void animalSound(); // interface method (does not have a body)
}

// Pig "implements" the IAnimal interface
class Pig : IAnimal 
{
  public void animalSound() 
  {
    // The body of animalSound() is provided here
    Console.WriteLine("The pig says: wee wee");
  }
}

class Program 
{
  static void Main(string[] args) 
  {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
  }
}
```