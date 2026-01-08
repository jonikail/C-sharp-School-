## 🧩 1. Ce este LINQ

👉 **LINQ (Language-Integrated Query)** este un mod de a **interoga și prelucra date** din diferite surse folosind aceeași sintaxă în C#. [Metanit](https://metanit.com/sharp/tutorial/15.1.php?utm_source=chatgpt.com)

📌 Surse de date pot fi:

- colecții (`List`, array etc.)
    
- baze de date (**Entity Framework**)
    
- XML
    
- DataSet
    
- colectii în paralel (PLINQ) [Metanit](https://metanit.com/sharp/tutorial/15.1.php?utm_source=chatgpt.com)
    

---

## 🧠 2. Tipuri de LINQ

🔹 **LINQ to Objects** – pentru array-uri și colecții C#  
🔹 **LINQ to Entities** – pentru baze de date prin Entity Framework  
🔹 **LINQ to XML** – pentru documente XML  
🔹 **LINQ to DataSet** – pentru DataSet  
🔹 **PLINQ** – pentru execuție paralelă [Metanit](https://metanit.com/sharp/tutorial/15.1.php?utm_source=chatgpt.com)

---

## 🧱 3. Două moduri de a scrie LINQ

### 🟡 A. Sintaxă de interogare (Query Syntax)

Arată similar cu SQL:

`var selected = from p in people                  where p.StartsWith("T")                  orderby p                  select p;`

👉 Bun pentru citire la început. [Metanit](https://metanit.com/sharp/tutorial/15.1.php)

---

### 🔵 B. Sintaxă de metode de extensie (Method Syntax)

Folosește metode ca `.Where()`, `.Select()`, `.OrderBy()`, etc.:

`var selected = people     .Where(p => p.StartsWith("T"))     .OrderBy(p => p);`

👉 **Asta se folosește cel mai des în practică.** [Metanit](https://metanit.com/sharp/tutorial/15.1.php)

---

## 🧾 4. Rezultatul LINQ

➡️ Rezultatul unui query LINQ este de obicei un `IEnumerable<T>`  
➡️ Execuția **se face doar când enumeri rezultatul**  
➡️ Până atunci e doar un „plan” de operații (deferred execution) [Metanit](https://metanit.com/sharp/tutorial/15.1.php)

---

# 📚 5. LISTA METODELOR LINQ DIN PAGINA METANIT (cu rolul lor)

Mai jos este lista completă a metodelor LINQ menționate în tutorialul Metanit (cu ce fac ele): [Metanit](https://metanit.com/sharp/tutorial/15.1.php)

---

## 🔹 Proiecție & selecție

- **Select** – proiectează sau transformă valorile [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Filtrare

- **Where** – filtrare pe condiție [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Sortare

- **OrderBy** – sortare crescătoare [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **OrderByDescending** – sortare descrescătoare [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **ThenBy** – sortare secundară crescătoare [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **ThenByDescending** – sortare secundară descrescătoare [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Conectare & altele avansate

- **Join** – unește două colecții după o condiție [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **GroupJoin** – join + grupare [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Zip** – combină două colecții în tupluri [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Grupare

- **GroupBy** – grupează elemente după o cheie [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **ToLookup** – grupează într-un dicționar după cheie [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Aglomerări (agregări)

- **Aggregate** – funcție de agregare personalizată [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Count** – numără elemente [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Sum** – sumă [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Average** – medie [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Min** – minim [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Max** – maxim [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Set & operații pe mulțimi

- **Distinct** – elimină duplicate [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Union** – unirea a două colecții fără duplicate [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Intersect** – elementele comune [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Except** – diferența între colecții [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Concat** – unirea simplă (fără eliminare) [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Condiții

- **All** – sunt toate elementele pe criteriu? [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Any** – există cel puțin unul? [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Contains** – conține un anumit element? [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Elemente individuale

- **First** – primul element [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **FirstOrDefault** – primul sau implicit [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Single** – unicul element [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **SingleOrDefault** – unicul sau implicit [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Last** – ultimul element [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **LastOrDefault** – ultimul sau implicit [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **ElementAt** – element după index [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **ElementAtOrDefault** – după index sau implicit [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Select & preluare

- **Take** – ia primele n elemente [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **Skip** – sare peste primul n elemente [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **TakeWhile** – ia cât timp condiția e adevărată [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    
- **SkipWhile** – sare cât timp condiția e adevărată [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

## 🔹 Alte

- **Reverse** – inversează ordinea [Metanit](https://metanit.com/sharp/tutorial/15.1.php)
    

---

# 📌 Rezumat – Structurat pe Scopuri

🟦 **Filtrare:** `Where`  
🟩 **Proiecție:** `Select`  
🟥 **Sortare:** `OrderBy`, `ThenBy`, `OrderByDescending`  
🟨 **Grupare:** `GroupBy`, `ToLookup`  
🟪 **Agregare:** `Count`, `Sum`, `Average`, `Min`, `Max`, `Aggregate`  
🟧 **Set operations:** `Union`, `Intersect`, `Except`, `Distinct`, `Concat`  
🟫 **Elemente:** `First`, `Single`, `Last`, `ElementAt…`  
🟪 **Condiții:** `All`, `Any`, `Contains`  
🟫 **Paging:** `Take`, `Skip`, `TakeWhile`, `SkipWhile`  
🟦 **Combining:** `Join`, `GroupJoin`, `Zip`, `Reverse`