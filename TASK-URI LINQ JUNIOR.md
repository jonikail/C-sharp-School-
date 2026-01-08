# 🧠 EXERCIȚII LINQ 

👉 **Regulă**: fiecare exercițiu să fie rezolvat **doar cu LINQ**, fără `for`, `foreach`.

---

## 🔹 NIVEL 0 – BAZA (Where, Select)

### 1️⃣ Filtrare simplă

Ai lista:

`var numbers = new List<int> { 1, 5, 8, 12, 20, 3 };`

🔹 Afișează doar numerele **mai mari ca 5**

---

### 2️⃣ Numere pare

Din aceeași listă:  
🔹 Selectează doar **numerele pare**

---

### 3️⃣ Transformare

🔹 Creează o listă nouă unde fiecare număr este **înmulțit cu 2**

---

### 4️⃣ Lucru cu string

`var names = new List<string> { "ana", "ion", "maria" };`

🔹 Transformă toate numele în **majuscule**

---

## 🔹 NIVEL 1 – CĂUTARE & VERIFICARE

### 5️⃣ FirstOrDefault

🔹 Găsește **primul număr mai mare ca 10**  
🔹 Dacă nu există, să nu crape

---

### 6️⃣ Any

🔹 Verifică dacă există **numere negative**

---

### 7️⃣ All

🔹 Verifică dacă **toate numerele sunt pozitive**

---

## 🔹 NIVEL 2 – SORTARE & PAGINARE

### 8️⃣ Sortare crescătoare

🔹 Sortează lista de numere **crescător**

---

### 9️⃣ Sortare descrescătoare

🔹 Sortează lista **descrescător**

---

### 🔟 Skip & Take

🔹 Sari peste primele **2** numere  
🔹 Ia următoarele **3**

---

## 🔹 NIVEL 3 – AGREGARE

### 1️⃣1️⃣ Sum

🔹 Calculează **suma** numerelor

---

### 1️⃣2️⃣ Min & Max

🔹 Afișează **cel mai mic** și **cel mai mare** număr

---

### 1️⃣3️⃣ Average

🔹 Calculează **media** numerelor

---

### 1️⃣4️⃣ Count

🔹 Numără câte numere sunt **mai mari ca 10**

---

## 🔹 NIVEL 4 – OBIECTE (REAL LIFE)

`class Person {     public string Name { get; set; }     public int Age { get; set; } }`

`var people = new List<Person> {     new Person { Name = "Ion", Age = 20 },     new Person { Name = "Ana", Age = 30 },     new Person { Name = "Maria", Age = 17 } };`

---

### 1️⃣5️⃣ Filtrare obiecte

🔹 Afișează persoanele **majore (Age >= 18)**

---

### 1️⃣6️⃣ Select pe obiect

🔹 Creează o listă DOAR cu **numele persoanelor**

---

### 1️⃣7️⃣ Sortare după proprietate

🔹 Sortează persoanele după **Age**

---

### 1️⃣8️⃣ Any pe obiecte

🔹 Verifică dacă există vreo persoană **sub 18 ani**

---

## 🔹 NIVEL 5 – GROUP BY

### 1️⃣9️⃣ Grupare simplă

Grupează persoanele după:  
🔹 **Major / Minor**

---

### 2️⃣0️⃣ GroupBy + Count

🔹 Afișează câte persoane sunt în fiecare grup

---

## 🔹 NIVEL 6 – AVANSAT (Junior+)

### 2️⃣1️⃣ Distinct

`var cities = new List<string> { "Chisinau", "Balti", "Chisinau" };`

🔹 Elimină dublicatele

---

### 2️⃣2️⃣ SelectMany

`var lists = new List<List<int>> {     new() {1,2},     new() {3,4} };`

🔹 Obține o singură listă: `1,2,3,4`

---

### 2️⃣3️⃣ ToDictionary

🔹 Creează un dicționar:

- Key → Name
    
- Value → Age