# 📌 Referință Rapidă – C# HTTP • API • REST API

Document **Obsidian** cu **mini bucăți de cod (snippets)** cele mai des întâlnite în **ASP.NET Web API**.  
👉 Ideal ca **cheat‑sheet** zilnic.

---

## 🔹 1. Controller de bază Web API

```csharp
[ApiController]
[Route("api/[controller]")]
public class UsersController : ControllerBase
{
}
```

📍 Cel mai folosit pattern în ASP.NET Web API

---

## 🔹 2. GET – Returnare listă (200 OK)

```csharp
[HttpGet]
public IActionResult GetAll()
{
    return Ok(users);
}
```

📍 Folosit la: listare date

---

## 🔹 3. GET by ID + NotFound (404)

```csharp
[HttpGet("{id}")]
public IActionResult GetById(int id)
{
    var user = users.FirstOrDefault(x => x.Id == id);

    if (user == null)
        return NotFound();

    return Ok(user);
}
```

📍 Pattern clasic REST

---

## 🔹 4. POST – Creare resursă (201 Created)

```csharp
[HttpPost]
public IActionResult Create(User user)
{
    if (!ModelState.IsValid)
        return BadRequest();

    users.Add(user);
    return CreatedAtAction(nameof(GetById), new { id = user.Id }, user);
}
```

📍 Foarte important la interviu

---

## 🔹 5. PUT – Update (204 NoContent)

```csharp
[HttpPut("{id}")]
public IActionResult Update(int id, User updated)
{
    var user = users.FirstOrDefault(x => x.Id == id);

    if (user == null)
        return NotFound();

    user.Name = updated.Name;
    return NoContent();
}
```

---

## 🔹 6. DELETE – Ștergere

```csharp
[HttpDelete("{id}")]
public IActionResult Delete(int id)
{
    var user = users.FirstOrDefault(x => x.Id == id);

    if (user == null)
        return NotFound();

    users.Remove(user);
    return NoContent();
}
```

---

## 🔹 7. Model simplu (DTO / Entity)

```csharp
public class User
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
}
```

---

## 🔹 8. LINQ – Where + Select

```csharp
var adults = users
    .Where(u => u.Age >= 18)
    .Select(u => u.Name)
    .ToList();
```

📍 LINQ cel mai folosit

---

## 🔹 9. LINQ – OrderBy + Take

```csharp
var topProducts = products
    .OrderByDescending(p => p.Price)
    .Take(3)
    .ToList();
```

---

## 🔹 10. Try / Catch în Controller

```csharp
try
{
    DoSomething();
    return Ok();
}
catch (Exception ex)
{
    return BadRequest(ex.Message);
}
```

📍 Gestionare erori simple

---

## 🔹 11. Excepție personalizată

```csharp
public class InvalidPriceException : Exception
{
    public InvalidPriceException(string message) : base(message) { }
}
```

---

## 🔹 12. Interfață Service

```csharp
public interface IUserService
{
    IEnumerable<User> GetAll();
    User GetById(int id);
}
```

---

## 🔹 13. Implementare Service

```csharp
public class UserService : IUserService
{
    public IEnumerable<User> GetAll() => users;
    public User GetById(int id) => users.FirstOrDefault(x => x.Id == id);
}
```

---

## 🔹 14. Injectare Service în Controller

```csharp
private readonly IUserService _service;

public UsersController(IUserService service)
{
    _service = service;
}
```

📍 Dependency Injection – extrem de frecvent

---

## 🔹 15. Abstract Class + Override

```csharp
public abstract class Payment
{
    public abstract void Pay();
}

public class CardPayment : Payment
{
    public override void Pay()
    {
        Console.WriteLine("Paid with card");
    }
}
```

---

## 🔹 16. Status Codes rapide

```csharp
return Ok();           // 200
return Created();      // 201
return NoContent();    // 204
return BadRequest();   // 400
return Unauthorized(); // 401
return NotFound();     // 404
```

---

## 🧠 CUM SĂ FOLOSEȘTI ACEST DOCUMENT

- 🔖 Bookmark în Obsidian
    
- 🧩 Copiază snippet-ul când ai nevoie
    
- 🔁 Revino zilnic
    

👉 Dacă recunoști toate exemplele → ești **ready de Junior ASP.NET** 🚀