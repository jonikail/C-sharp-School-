# 🗄️ SQL – Cheat Sheet (pentru Obsidian)

> 📌 Fișă rapidă SQL – exact ce trebuie să știi ca **Junior Developer** (ASP.NET + EF Core)

---

## 🔹 1. Ce este SQL?

**SQL (Structured Query Language)** este limbajul folosit pentru a **lucra cu baze de date relaționale**.

📍 Folosit în: SQL Server, PostgreSQL, MySQL, SQLite  
📍 În ASP.NET → EF Core generează SQL

---

## 🔹 2. Tipuri de comenzi SQL

### 🟦 DDL – definirea structurii

- `CREATE`
    
- `ALTER`
    
- `DROP`
    

### 🟩 DML – manipularea datelor

- `SELECT`
    
- `INSERT`
    
- `UPDATE`
    
- `DELETE`
    

### 🟨 DCL / TCL (mai rar pentru junior)

- `GRANT`, `REVOKE`
    
- `COMMIT`, `ROLLBACK`
    

---

## 🔹 3. SELECT – baza SQL

### Selectare simplă

```sql
SELECT * FROM Users;
```

### Selectare coloane

```sql
SELECT Name, Age FROM Users;
```

---

## 🔹 4. WHERE – filtrare

```sql
SELECT * FROM Users WHERE Age >= 18;
```

### Operatori

- `=` egal
    
- `!=` sau `<>` diferit
    
- `>` `<` `>=` `<=`
    

```sql
SELECT * FROM Users WHERE City = 'Chisinau';
```

---

## 🔹 5. AND / OR / NOT

```sql
SELECT * FROM Users WHERE Age >= 18 AND City = 'Chisinau';
```

---

## 🔹 6. ORDER BY – sortare

```sql
SELECT * FROM Users ORDER BY Name ASC;
SELECT * FROM Users ORDER BY Age DESC;
```

---

## 🔹 7. LIMIT / TOP – limitare rezultate

### SQL Server

```sql
SELECT TOP 5 * FROM Users;
```

### PostgreSQL / MySQL

```sql
SELECT * FROM Users LIMIT 5;
```

---

## 🔹 8. INSERT – adăugare date

```sql
INSERT INTO Users (Name, Age, City)
VALUES ('Ion', 20, 'Chisinau');
```

---

## 🔹 9. UPDATE – modificare date

```sql
UPDATE Users
SET Age = 21
WHERE Id = 1;
```

⚠️ **Fără WHERE → modifică toate rândurile!**

---

## 🔹 10. DELETE – ștergere date

```sql
DELETE FROM Users WHERE Id = 1;
```

⚠️ **Fără WHERE → șterge tot tabelul!**

---

## 🔹 11. NULL

```sql
SELECT * FROM Users WHERE City IS NULL;
SELECT * FROM Users WHERE City IS NOT NULL;
```

---

## 🔹 12. LIKE – căutare text

```sql
SELECT * FROM Users WHERE Name LIKE 'I%';
```

- `%` = orice
    
- `_` = un caracter
    

---

## 🔹 13. IN

```sql
SELECT * FROM Users WHERE City IN ('Chisinau', 'Balti');
```

---

## 🔹 14. BETWEEN

```sql
SELECT * FROM Users WHERE Age BETWEEN 18 AND 30;
```

---

## 🔹 15. FUNCȚII AGREGATE

```sql
SELECT COUNT(*) FROM Users;
SELECT AVG(Age) FROM Users;
SELECT MIN(Age) FROM Users;
SELECT MAX(Age) FROM Users;
SELECT SUM(Age) FROM Users;
```

---

## 🔹 16. GROUP BY

```sql
SELECT City, COUNT(*)
FROM Users
GROUP BY City;
```

---

## 🔹 17. HAVING (filtru pe grupuri)

```sql
SELECT City, COUNT(*)
FROM Users
GROUP BY City
HAVING COUNT(*) > 1;
```

---

## 🔹 18. JOIN – legarea tabelelor

### INNER JOIN

```sql
SELECT u.Name, o.Total
FROM Users u
JOIN Orders o ON u.Id = o.UserId;
```

### LEFT JOIN

```sql
SELECT u.Name, o.Total
FROM Users u
LEFT JOIN Orders o ON u.Id = o.UserId;
```

---

## 🔹 19. CHEI

### Primary Key

```sql
Id INT PRIMARY KEY
```

### Foreign Key

```sql
UserId INT FOREIGN KEY REFERENCES Users(Id)
```

---

## 🔹 20. CREATE TABLE

```sql
CREATE TABLE Users (
    Id INT PRIMARY KEY IDENTITY,
    Name NVARCHAR(100),
    Age INT,
    City NVARCHAR(100)
);
```

---

## 🔹 21. DROP / TRUNCATE

```sql
DROP TABLE Users;
TRUNCATE TABLE Users;
```

---

## 🔹 22. TRANZACȚII

```sql
BEGIN TRANSACTION;
UPDATE Users SET Age = 30 WHERE Id = 1;
ROLLBACK;
```

---

## 🔹 23. SQL vs LINQ (legătură)

|SQL|LINQ|
|---|---|
|SELECT|Select|
|WHERE|Where|
|ORDER BY|OrderBy|
|GROUP BY|GroupBy|
|JOIN|Join|

---

## ✅ MINIM DE ȘTIUT PENTRU JUNIOR

✔ SELECT  
✔ WHERE  
✔ INSERT  
✔ UPDATE  
✔ DELETE  
✔ JOIN  
✔ GROUP BY  
✔ ORDER BY

---

📌 **Tip Obsidian**: pune acest fișier într-un folder `Backend / SQL` și revino la el zilnic 5–10 minute.