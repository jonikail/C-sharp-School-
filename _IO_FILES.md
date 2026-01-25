
## 📂 FIȘIERE și IO (Input / Output)

**IO** înseamnă citirea și scrierea datelor:

- din fișiere
    
- din consolă
    
- din rețea
    

### Tipuri de fișiere frecvent folosite

- `.txt` – text simplu
    
- `.json` – date structurate
    
- `.csv` – date tabelare
    

### Clase importante

- `File`
    
- `FileInfo`
    
- `StreamReader`
    
- `StreamWriter`
    

### Exemplu: scriere într-un fișier

```csharp
File.WriteAllText("test.txt", "Salut lume!");
```

### Exemplu: citire din fișier

```csharp
string text = File.ReadAllText("test.txt");
Console.WriteLine(text);
```

---

## 🧾 JSON

**JSON** (JavaScript Object Notation) este un format de stocare a datelor, foarte folosit în API-uri.

### Exemplu JSON

```json
{
  "name": "Ion",
  "age": 25
}
```

### Serializare (obiect → JSON)

```csharp
var user = new User { Name = "Ion", Age = 25 };
string json = JsonSerializer.Serialize(user);
```

### Deserializare (JSON → obiect)

```csharp
User user = JsonSerializer.Deserialize<User>(json);
```

---

## ⚠️ Excepții simple

Excepțiile sunt erori care apar în timpul rulării aplicației.

### Structura de bază

```csharp
try
{
    int x = int.Parse("abc");
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```

### Exemple comune

- `FormatException`
    
- `NullReferenceException`
    
- `DivideByZeroException`
    

---

## 🚨 Excepții Custom (personalizate)

Când vrei erori create de tine.

### Creare excepție custom

```csharp
public class InvalidAgeException : Exception
{
    public InvalidAgeException(string message) : base(message) {}
}
```

### Folosire

```csharp
if (age < 18)
    throw new InvalidAgeException("Vârsta prea mică");
```

---

## ⏳ async / await

Se folosesc pentru operații care durează (fișiere, API, DB) fără a bloca aplicația.

### Exemplu simplu

```csharp
async Task LoadDataAsync()
{
    await Task.Delay(2000);
    Console.WriteLine("Date încărcate");
}
```

---

## 🧠 Task

`Task` reprezintă o operație care rulează asincron.

### Exemplu

```csharp
Task task = Task.Run(() =>
{
    Console.WriteLine("Rulează în fundal");
});

await task;
```

---

## ⚙️ Parallelism – ce este?

**Parallelism** = mai multe task-uri rulează **în același timp** (pe mai multe nuclee CPU).

### Exemplu

```csharp
Parallel.For(0, 5, i =>
{
    Console.WriteLine(i);
});
```

🔴 Atenție: poate cauza probleme de sincronizare.

---

## 🔁 async (explicație clară)

- `async` marchează o metodă ca fiind asincronă
    
- `await` spune: "așteaptă fără să blochezi"
    

### Greșeală comună

```csharp
Task.Delay(1000); // NU așteaptă
```

### Corect

```csharp
await Task.Delay(1000);
```

---

## 🔗 Ce este un Delegat?

Un **delegat** este o referință către o metodă.

👉 Similar cu un pointer la funcție.

### Definire delegat

```csharp
delegate void MyDelegate(string message);
```

### Folosire

```csharp
void Afiseaza(string text)
{
    Console.WriteLine(text);
}

MyDelegate del = Afiseaza;
del("Salut!");
```

### Unde se folosesc delegații?

- Events
    
- LINQ
    
- Callbacks
    

---

## 🧩 Legătură logică între concepte