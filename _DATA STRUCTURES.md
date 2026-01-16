### 1. **`Array`**

- Descriere: Colecție de elemente de același tip, cu dimensiune fixă.

- **Când se folosește:** Când numărul de elemente este cunoscut și nu se schimbă.
  Exemplu:
```csharp
int[] numere = { 1, 2, 3, 4 };
```

### 2. **`List<T>`**

 - **Descriere:** Colecție dinamică, dimensiunea se poate modifica.
	
 - **Când se folosește:** Când ai nevoie să adaugi sau să ștergi elemente frecvent.
	Exemplu:
```cs
List<string> nume = new List<string> { "Ana", "Ion" };
nume.Add("Maria");
```
  ---
### 3. **`Dictionary<TKey, TValue>`**

- **Descriere:** Stochează perechi cheie–valoare, cu acces rapid prin cheie.

- **Când se folosește:** Când ai nevoie de căutare rapidă.
    
- **Exemplu:**
    
```cs
Dictionary<int, string> studenti = new Dictionary<int, string>(); studenti[1] = "Alex";
```

---
### 4. `Queue<T> (Coadă)`

- **Descriere:** Funcționează pe principiul **FIFO** (primul intrat, primul ieșit).
    
- **Când se folosește:** Pentru procesarea elementelor în ordinea sosirii.
    
- **Exemplu:**
    
```cs
Queue<int> coada = new Queue<int>(); 
coada.Enqueue(10); 
coada.Dequeue();
```

---

### 5. `Stack<T> (Stivă)`

- **Descriere:** Funcționează pe principiul **LIFO** (ultimul intrat, primul ieșit).
    
- **Când se folosește:** Pentru undo/redo sau apeluri recursive.
    
- **Exemplu:**
    
```cs
Stack<string> stiva = new Stack<string>(); 
stiva.Push("A"); 
stiva.Pop();
```

---

### 6. `HashSet<T>`

- **Descriere:** Colecție de elemente **unice**, fără ordine.
    
- **Când se folosește:** Când vrei să eviți duplicatele.
    
- **Exemplu:**
    
```cs
HashSet<int> valori = new HashSet<int>();
valori.Add(5);
```

---

### 7. `Struct`

- **Descriere:** Tip de date valoare, folosit pentru date simple.
    
- **Când se folosește:** Pentru obiecte mici, fără logică complexă.
    
- **Exemplu:**
    
```cs
struct Punct 
{
	public int X;
	public int Y;
}
```