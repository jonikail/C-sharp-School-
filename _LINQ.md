# LINQ – Documentație practică (C#)

> 📌 Acest document este gândit ca **fișă Obsidian** pentru developeri C#.  
> Conține **doar lucruri utile în practică**, exact ce se folosește în proiecte reale, ASP.NET, EF Core și la interviuri.

---

## 🔹 Ce este LINQ?

**LINQ (Language Integrated Query)** este o modalitate de a **lucra cu colecții de date** folosind un cod clar și expresiv.

👉 LINQ se folosește pentru:

- liste (`List<T>`)
    
- array-uri
    
- baze de date (EF Core)
    
- XML / JSON
    

🧠 Gândește LINQ așa:

> _„Ia datele → filtrează → sortează → transformă”_

---

## 🔹 Regula de bază LINQ

```csharp
Where   → filtrează
Select  → transformă
OrderBy → sortează
ToList  → execută
```

---

## 🔹 Where() – Filtrare

### Ce face?

Păstrează **doar elementele care respectă o condiție**.

### Sintaxă:

```csharp
var result = list.Where(x => x > 10).ToList();
```

### Exemplu:

```csharp
var numbers = new List<int> { 5, 10, 20, 30 };
var bigNumbers = numbers.Where(n => n > 10).ToList();
```

### Unde se folosește:

- filtre DB (`IsActive == true`)
    
- produse cu preț > X
    
- useri majori
    

---

## 🔹 Select() – Transformare

### Ce face?

Ia fiecare element și îl **transformă**.

### Sintaxă:

```csharp
var result = list.Select(x => x * 2).ToList();
```

### Exemplu:

```csharp
var doubled = numbers.Select(n => n * 2).ToList();
```

### Unde se folosește:

- mapare Entity → DTO
    
- afișare date
    
- modificare valori
    

---

## 🔹 OrderBy() / OrderByDescending()

### Ce face?

Sortează datele.

### Exemplu:

```csharp
var asc = numbers.OrderBy(n => n).ToList();
var desc = numbers.OrderByDescending(n => n).ToList();
```

### Unde se folosește:

- sortare după nume
    
- sortare după dată
    
- top scoruri
    

---

## 🔹 First() / FirstOrDefault()

### Ce face?

Returnează **primul element**.

```csharp
var first = numbers.FirstOrDefault();
```

⚠️ `First()` aruncă excepție dacă lista e goală.

### Unde se folosește:

- obținere un singur obiect
    
- setări
    
- user curent
    

---

## 🔹 Any()

### Ce face?

Verifică dacă **există cel puțin un element**.

```csharp
bool exists = numbers.Any(n => n > 100);
```

### Unde se folosește:

- validări
    
- verificări rapide
    
- auth
    

---

## 🔹 All()

### Ce face?

Verifică dacă **toate elementele** respectă condiția.

```csharp
bool allPositive = numbers.All(n => n > 0);
```

---

## 🔹 Count()

### Ce face?

Returnează numărul de elemente.

```csharp
int count = numbers.Count(n => n > 10);
```

### Unde se folosește:

- paginare
    
- statistici
    
- rapoarte
    

---

## 🔹 Min() / Max()

### Ce face?

Returnează valoarea minimă / maximă.

```csharp
int min = numbers.Min();
int max = numbers.Max();
```

### Cu obiecte:

```csharp
var minPrice = products.Min(p => p.Price);
```

---

## 🔹 Sum() / Average()

```csharp
int total = numbers.Sum();
double avg = numbers.Average();
```

### Unde:

- calcule
    
- rapoarte
    
- statistici
    

---

## 🔹 Distinct()

### Ce face?

Elimină dublurile.

```csharp
var unique = numbers.Distinct().ToList();
```

---

## 🔹 Take() / Skip()

### Ce face?

Paginare.

```csharp
var page1 = numbers.Take(5).ToList();
var page2 = numbers.Skip(5).Take(5).ToList();
```

### Unde:

- pagination
    
- infinite scroll
    

---

## 🔹 GroupBy()

### Ce face?

Grupează datele după o cheie.

```csharp
var grouped = numbers.GroupBy(n => n);
```

### Exemplu real:

```csharp
var result = students
    .GroupBy(s => s.City)
    .Select(g => new { City = g.Key, Count = g.Count() });
```

### Unde:

- rapoarte
    
- statistici
    
- dashboard-uri
    

---

## 🔹 Single() / SingleOrDefault()

👉 Așteaptă **exact un element**.

```csharp
var user = users.SingleOrDefault(u => u.Id == 1);
```

⚠️ Eroare dacă sunt mai multe.

---

## 🔹 ToList() / ToArray()

### Ce face?

Execută LINQ.

```csharp
var list = query.ToList();
```

⚠️ Fără `ToList()` → LINQ NU se execută încă.

---

## 🔹 Unde se folosește LINQ cel mai des?

- ASP.NET Controllers
    
- EF Core Queries
    
- Servicii (Business Logic)
    
- Validări
    
- Rapoarte
    
- Teste
    

---

## 🔹 Regula finală (FOARTE IMPORTANTĂ)

> **LINQ = claritate, nu magie**

Dacă LINQ devine greu de citit → e prea complex.

---

📌 Recomandare Obsidian:

- leagă acest document de: `EF Core`, `SQL`, `ASP.NET`
    
- adaugă exemple proprii sub fiecare metodă
    

---

✔️ Acest document acoperă **90% din LINQ folosit zilnic**