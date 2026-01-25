## 1️⃣ Ce este HTTP?

**HTTP (HyperText Transfer Protocol)** este un protocol de comunicare între:

- **Client** (browser, aplicație mobilă, Postman)
    
- **Server** (ASP.NET Web API, backend)
    

👉 Practic: HTTP spune **cum** clientul cere date și **cum** serverul răspunde.

### Exemplu simplu:

- Tu → ceri o pagină web
    
- Serverul → îți trimite HTML / JSON
    

---

## 2️⃣ Request → Response (Cum funcționează HTTP)

### 🔁 Fluxul de bază:

```
Client → HTTP Request → Server
Server → HTTP Response → Client
```

### 📨 HTTP Request conține:

- **Method** (GET, POST, PUT, DELETE)
    
- **URL**
    
- **Headers** (ex: Authorization, Content-Type)
    
- **Body** (date trimise – la POST/PUT)
    

### 📦 HTTP Response conține:

- **Status Code** (200, 404, 500 etc.)
    
- **Headers**
    
- **Body** (datele cerute, de obicei JSON)
    

---

## 3️⃣ Metode HTTP (GET / POST / PUT / DELETE)

Acestea sunt acțiunile principale într-un API REST.

### 🔹 GET – Citește date

👉 Folosit pentru a **lua informații**

```http
GET /api/users
```

```csharp
[HttpGet]
public IEnumerable<User> GetUsers()
{
    return users;
}
```

---

### 🔹 POST – Creează date

👉 Folosit pentru a **adăuga ceva nou**

```http
POST /api/users
```

```json
{
  "name": "Ion",
  "age": 25
}
```

```csharp
[HttpPost]
public IActionResult CreateUser(User user)
{
    users.Add(user);
    return Ok(user);
}
```

---

### 🔹 PUT – Actualizează date

👉 Modifică un obiect **existent**

```http
PUT /api/users/1
```

```csharp
[HttpPut("{id}")]
public IActionResult UpdateUser(int id, User user)
{
    return NoContent();
}
```

---

### 🔹 DELETE – Șterge date

👉 Elimină un obiect

```http
DELETE /api/users/1
```

```csharp
[HttpDelete("{id}")]
public IActionResult DeleteUser(int id)
{
    return NoContent();
}
```

---

## 4️⃣ Ce sunt Status Codes (Coduri de răspuns)

Status codes spun **ce s-a întâmplat** cu request-ul.

### ✅ 2xx – Succes

- **200 OK** – totul e bine
    
- **201 Created** – obiect creat
    
- **204 No Content** – succes fără conținut
    

### ⚠️ 4xx – Greșeala clientului

- **400 Bad Request** – date invalide
    
- **401 Unauthorized** – nu ești logat
    
- **403 Forbidden** – nu ai acces
    
- **404 Not Found** – nu există
    

### ❌ 5xx – Greșeala serverului

- **500 Internal Server Error** – eroare internă
    

---

## 5️⃣ Ce este API?

**API (Application Programming Interface)** este o interfață prin care:

- o aplicație vorbește cu alta aplicație
    

👉 API = reguli + endpoint-uri + date

### Exemplu:

- Frontend → API
    
- Mobile App → API
    
- Alt server → API
    

---

## 6️⃣ Ce este REST API?

**REST (Representational State Transfer)** este un stil de a construi API-uri.

### Principii REST:

- Folosește HTTP
    
- Folosește metodele GET / POST / PUT / DELETE
    
- Lucrează cu **resurse** (users, products)
    
- Returnează **JSON**
    
- Este **stateless** (serverul nu ține minte clientul)
    

### Exemplu REST corect:

```
GET    /api/products
POST   /api/products
GET    /api/products/5
PUT    /api/products/5
DELETE /api/products/5
```

---

## 7️⃣ Ce este Web API în ASP.NET?

**ASP.NET Web API** este framework-ul care:

- creează API-uri REST
    
- trimite / primește JSON
    
- este folosit de frontend, mobile, alte servicii
    

```csharp
[ApiController]
[Route("api/[controller]")]
public class ProductsController : ControllerBase
{
    [HttpGet]
    public IActionResult Get()
    {
        return Ok(products);
    }
}
```

---

## 8️⃣ Tipuri de API pe care trebuie să le știe un ASP.NET Developer

### 🔹 REST API (CEL MAI IMPORTANT)

✔ Standard în ASP.NET  
✔ JSON + HTTP

---

### 🔹 SOAP API

- XML
    
- vechi
    
- folosit în sisteme legacy (bănci, guvern)
    

---

### 🔹 GraphQL API

- Clientul cere exact ce câmpuri vrea
    
- o singură rută
    
- folosit de aplicații mari
    

---

### 🔹 Minimal API (ASP.NET)

- API simplu, fără controllere
    

```csharp
app.MapGet("/hello", () => "Hello World");
```

---

### 🔹 gRPC (avansat)

- Foarte rapid
    
- Microservicii
    
- Binary (nu JSON)
    

---

## 9️⃣ Ce trebuie să știe minim un Junior ASP.NET

✔ HTTP Methods  
✔ Status Codes  
✔ REST principles  
✔ JSON  
✔ Controllers  
✔ Routing  
✔ Model Binding  
✔ Swagger  
✔ Authentication (JWT – basic)

---

## 🔟 Concluzie simplă

- **HTTP** = cum vorbesc aplicațiile
    
- **API** = interfață
    
- **REST API** = stil modern de API
    
- **Web API ASP.NET** = implementarea practică
    
