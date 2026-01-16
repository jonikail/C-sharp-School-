
## 🔰 MINI‑PROIECT 1 – HTTP GET (Primul API)

### 🎯 Scop

Să înțelegi **GET**, endpoint‑uri și `IActionResult`.

### 🧩 Cerință

Creează un API care returnează o listă de utilizatori.

### 📁 Structură

- User (Model)
    
- UsersController
    

### 📝 Taskuri

1. Creează clasa `User` cu:
    
    - `Id`
        
    - `Name`
        
    - `Email`
        
2. Creează un controller `UsersController`
    
3. Creează endpoint:
    

```http
GET /api/users
```

4. Returnează o listă hard‑coded de utilizatori
    

### 🎯 Ce înveți

- HTTP GET
    
- Request → Response
    
- JSON
    

---

## 🔰 MINI‑PROIECT 2 – HTTP POST (Creare resursă)

### 🎯 Scop

Să înveți **POST + Body JSON**.

### 🧩 Cerință

Extinde proiectul anterior.

### 📝 Taskuri

1. Creează endpoint:
    

```http
POST /api/users
```

2. Primește un `User` din body
    
3. Validează ca `Name` să nu fie gol
    
4. Returnează:
    
    - `201 Created` dacă e OK
        
    - `400 BadRequest` dacă datele sunt invalide
        

### 🎯 Ce înveți

- HTTP POST
    
- Model Binding
    
- Status Codes
    

---

## 🔰 MINI‑PROIECT 3 – REST API CRUD COMPLET

### 🎯 Scop

Să implementezi **REST corect**.

### 🧩 Cerință

Creează CRUD pentru `Products`.

### 📁 Structură

- Product (Model)
    
- ProductsController
    

### 📝 Endpoint‑uri

```
GET    /api/products
GET    /api/products/{id}
POST   /api/products
PUT    /api/products/{id}
DELETE /api/products/{id}
```

### 📝 Taskuri

1. Returnează status code corect pentru fiecare operație
    
2. Folosește `NotFound()` dacă produsul nu există
    
3. Folosește `NoContent()` la DELETE
    

### 🎯 Ce înveți

- REST API complet
    
- Status codes reale
    
- Routing
    

---

## 🔰 MINI‑PROIECT 4 – LINQ + REST API

### 🎯 Scop

Să combini **LINQ** cu API‑uri.

### 🧩 Cerință

Filtrare și sortare produse.

### 📝 Taskuri

1. Endpoint:
    

```http
GET /api/products/expensive
```

2. Returnează produse cu preț > 100
    
3. Sortează descrescător după preț
    

### 🎯 Ce înveți

- LINQ în Web API
    
- Where / OrderBy
    

---

## 🔰 MINI‑PROIECT 5 – EXCEPȚII ÎN WEB API

### 🎯 Scop

Să gestionezi **erori reale**.

### 🧩 Cerință

1. Creează o metodă care aruncă excepție dacă prețul < 0
    
2. Prinde excepția și returnează:
    

```http
400 BadRequest
```

3. Mesaj clar pentru client
    

### 🎯 Ce înveți

- try / catch
    
- erori controlate
    

---

## 🔰 MINI‑PROIECT 6 – INTERFAȚĂ + API SERVICE

### 🎯 Scop

Să înțelegi **API + Interfețe**.

### 🧩 Cerință

1. Creează interfața `IProductService`
    
2. Metode:
    
    - `GetAll()`
        
    - `Add(Product product)`
        
3. Creează implementarea `ProductService`
    
4. Controllerul să folosească interfața
    

### 🎯 Ce înveți

- decuplare
    
- bazele Dependency Injection
    

---

## 🔰 MINI‑PROIECT 7 – ABSTRACT + POLIMORFISM

### 🎯 Scop

Să combini **OOP + API**.

### 🧩 Cerință

1. Creează clasa abstractă `Payment`
    
2. Metodă abstractă `Pay()`
    
3. Clase:
    
    - `CashPayment`
        
    - `CardPayment`
        
4. Endpoint:
    

```http
POST /api/payments
```

5. Apelează `Pay()` polimorfic
    

### 🎯 Ce înveți

- abstractizare
    
- override
    
- polymorphism
    

---

## 🏁 MINI‑PROIECT FINAL – REAL LIFE API

### 🚀 Tema: **Order Management System**

### 🧩 Cerință

1. REST API pentru `Orders`
    
2. CRUD complet
    
3. LINQ pentru rapoarte
    
4. Excepții pentru date invalide
    
5. Interfețe + servicii
    

### 🎯 Ce demonstrezi

✔ HTTP  
✔ REST API  
✔ OOP  
✔ LINQ  
✔ structura corectă ASP.NET