## 🔹 1. Ce este o INTERFAȚĂ în C#?

### 📌 Ideea de bază

O **interfață** este un **contract**.

👉 Spune **CE trebuie să facă o clasă**, nu **CUM**.

📦 Exemplu din viață:

- Interfața = regulile
    
- Clasa = implementarea regulilor
    

---

### 🔧 Cum se declară o interfață

```csharp
public interface IAnimal
{
    void Speak();
    int GetAge();
}
```

🔹 Conține **doar**:

- metode (fără corp)
    
- proprietăți
    

---

### 🏗️ Cum se folosește într-o clasă

```csharp
public class Dog : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("Ham Ham");
    }

    public int GetAge()
    {
        return 5;
    }
}
```

📌 **Regulă importantă**:  
➡️ Clasa **TREBUIE** să implementeze toate metodele din interfață

---

### ❓ De ce folosim interfețe?

✔ cod mai curat  
✔ ușor de schimbat  
✔ testare ușoară  
✔ bază pentru Dependency Injection

---

### 📍 Unde se folosesc cel mai des?

- servicii (UserService, OrderService)
    
- Repository Pattern
    
- API Controllers
    
- Dependency Injection

___

  Diferențe dintre Abstract Class și Interface
🧠 Ideea pe scurt (foarte simplu)

- **Interface** → spune **CE trebuie să facă** o clasă
    
- **Abstract class** → spune **CE trebuie să facă** + **CUM face unele lucruri**
    

👉 Interface = **contract**  
👉 Abstract class = **bază comună**

---

🔵 INTERFACE

### Ce este?

Un **contract** pe care o clasă trebuie să îl respecte.

---

### Cum se declară

```csharp
public interface IAnimal
{
    void Speak();
}
```

---

### Cum se implementează

```csharp
public class Dog : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("Ham Ham");
    }
}
```

---

### Caracteristici Interface

- ❌ NU are câmpuri
    
- ❌ NU are constructor
    
- ❌ NU are logică (clasic)
    
- ✅ Toate metodele sunt **publice**
    
- ✅ O clasă poate implementa **mai multe interfețe**
    

---

### Când folosim Interface?

- Dependency Injection
    
- Servicii (UserService, OrderService)
    
- API Controllers
    
- Testare (mocking)
    

---

🟠 ABSTRACT CLASS

### Ce este?

O clasă **incompletă** care poate conține logică.

---

### Cum se declară

```csharp
public abstract class Animal
{
    public abstract void Speak();

    public void Sleep()
    {
        Console.WriteLine("Animalul doarme");
    }
}
```

---

### Cum se moștenește

```csharp
public class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Ham Ham");
    }
}
```

---

### Caracteristici Abstract Class

- ✅ Poate avea metode cu logică
    
- ✅ Poate avea câmpuri
    
- ✅ Poate avea constructor
    
- ❌ O clasă poate moșteni **doar o singură clasă abstractă**
    

---

 #  📊 TABEL COMPARATIV (IMPORTANT)

|Caracteristică|Interface|Abstract Class|
|---|---|---|
|Moștenire multiplă|✅ DA|❌ NU|
|Metode cu cod|❌ NU|✅ DA|
|Câmpuri|❌ NU|✅ DA|
|Constructor|❌ NU|✅ DA|
|Nivel de acces|public|public / protected|
|Scop|Contract|Bază comună|

---

❓ Când aleg Interface?

✔ Când vrei flexibilitate  
✔ Când folosești Dependency Injection  
✔ Când clasele NU sunt înrudite

📌 Exemple reale:

- IUserService
    
- IRepository
    
- ILogger
    

---

❓ Când aleg Abstract Class?

✔ Când clasele sunt înrudite logic  
✔ Când vrei cod comun

📌 Exemple:

- Animal → Dog, Cat
    
- Vehicle → Car, Bike
    

---

🧠 Regula de aur (Junior)

> 🔑 **Dacă nu ești sigur → alege Interface**

Abstract class doar când ai nevoie clară de **cod comun**.

---

🔗 Exemplu real (ASP.NET + DI)

```csharp
public interface IUserService
{
    string GetUser();
}
```

```csharp
public class UserService : IUserService
{
    public string GetUser()
    {
        return "Ion";
    }
}
```




## 🔹 2. THREADS – ce sunt și de ce există

### 🧠 Ideea simplă

Un **thread** este un fir de execuție.

📦 Fără threads:

- programul face **un lucru pe rând**
    

📦 Cu threads:

- programul face **mai multe lucruri în paralel**
    

---

### 🔧 Thread simplu

```csharp
using System.Threading;

Thread thread = new Thread(() =>
{
    Console.WriteLine("Rulează într-un thread");
});

thread.Start();
```

---

### 🔄 Exemplu clar

```csharp
void Work()
{
    for (int i = 1; i <= 5; i++)
    {
        Console.WriteLine($"Thread: {i}");
        Thread.Sleep(1000);
    }
}

Thread t = new Thread(Work);
t.Start();

Console.WriteLine("Main thread continuă...");
```

📌 Observație:

- `Main` nu așteaptă
    
- thread-ul lucrează separat
    

---

### 🧰 Metode importante Thread

| Metodă    | Rol                   |
| --------- | --------------------- |
| Start()   | pornește thread-ul    |
| Sleep(ms) | pauză                 |
| Join()    | așteaptă thread-ul    |
| IsAlive   | verifică dacă rulează |

---

### 📍 Unde se folosesc threads?

- aplicații care nu trebuie să se blocheze
    
- procesare fișiere
    
- aplicații desktop
    
- background jobs
    

⚠️ În practică se folosesc mai mult:  
➡️ `Task` + `async/await`

---

## 🔹 3. API – ce este și cum funcționează

### 🌐 Ce este un API?

Un **API** este un **server** care:

- primește request
    
- trimite response
    

📦 Cel mai des folosit: **REST API**

---

### 🔄 Cum comunică API-ul

1️⃣ Client (browser / app)  
2️⃣ Trimite request HTTP  
3️⃣ API procesează  
4️⃣ Trimite response JSON

---

### 📡 Metode HTTP de bază

|Metodă|Rol|
|---|---|
|GET|citește date|
|POST|creează date|
|PUT|modifică|
|DELETE|șterge|

---

### 🏗️ API minim – exemplu

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/hello", () => "Salut din API!");

app.Run();
```

📌 Accesare:

```
http://localhost:5000/hello
```

---

### 🔗 API + Interfețe (foarte important)

```csharp
public interface IUserService
{
    string GetUser();
}

public class UserService : IUserService
{
    public string GetUser()
    {
        return "Ion";
    }
}
```

---

### 🧩 Injectare în API

```csharp
builder.Services.AddScoped<IUserService, UserService>();
```

---

### 📍 Unde se folosesc API-urile?

- aplicații web
    
- mobile apps
    
- microservicii
    
- frontend (React, Angular)
    

---

## 🔹 4. Cum se leagă TOATE între ele

📌 Flow real:

- Interfață → definește contract
    
- Clasă → implementează
    
- API → folosește serviciul
    
- Thread / Task → rulează logică în background
    