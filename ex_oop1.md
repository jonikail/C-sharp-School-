## 🟢 EXERCIȚIUL 1 – OOP + Interfață (FOARTE UȘOR)
### 📘 Cerință

Creează un sistem simplu de **notificări**.

---

### 🧩 Pașii de execuție

1️⃣ Creează o interfață `INotification`

- metoda: `Send(string message)`
    

2️⃣ Creează două clase:

- `EmailNotification`
    
- `SmsNotification`
    

Ambele trebuie să implementeze `INotification`.

3️⃣ Creează o clasă `NotificationService` care:

- primește o notificare prin **constructor**
    
- are o metodă `NotifyUser()`
    

4️⃣ În `Main()`:

- alege tipul de notificare
    
- trimite mesajul
    

---

### 📥 Date de intrare

- mesaj: "Salut! Ai un mesaj nou"
    

---

### 📤 Rezultat așteptat (consolă)

```
[EMAIL] Salut! Ai un mesaj nou
```

SAU

```
[SMS] Salut! Ai un mesaj nou
```
## 🟡 EXERCIȚIUL 2 – THREADS (UȘOR)

### 📘 Cerință

Creează două thread-uri care rulează **în paralel**.

---

### 🧩 Pașii de execuție

1️⃣ Creează o metodă `PrintNumbers()`

- afișează numerele 1–5
    
- pauză de 1 secundă între ele
    

2️⃣ Creează o metodă `PrintLetters()`

- afișează literele A–E
    
- pauză de 1 secundă
    

3️⃣ Rulează ambele metode pe **thread-uri diferite**.

---

### 📤 Rezultat așteptat

```
1
A
2
B
3
C
4
D
5
E
```
## 🟡 EXERCIȚIUL 3 – OOP + THREADS (MEDIU)

### 🎯 Scop

Combinarea OOP cu Thread-uri.

---

### 📘 Cerință

Creează un **DownloadManager**.

---

### 🧩 Pașii de execuție

1️⃣ Creează o clasă `DownloadTask`

- proprietăți: `FileName`, `Duration`
    

2️⃣ Creează o metodă `StartDownload()`

- afișează progresul
    

3️⃣ Rulează **mai multe descărcări simultan** folosind thread-uri.

---

### 📥 Date de intrare

- File1 (3 sec)
    
- File2 (5 sec)
    

---

### 📤 Rezultat așteptat

```
Downloading File1...
Downloading File2...
File1 completed
File2 completed
```

---

### 🧠 Ce exersați

- Threads
    
- OOP
    
- simulare proces real
    

---

## 🟠 EXERCIȚIUL 4 – INTRO API (FOARTE BASIC)

### 🎯 Scop

Primul contact cu **ASP.NET Web API**.

---

### 📘 Cerință

Creează un API care răspunde cu un mesaj.

---

### 🧩 Pașii de execuție

1️⃣ Creează un proiect **ASP.NET Web API**

2️⃣ Creează un controller `HelloController`

3️⃣ Endpoint:

```
GET /api/hello
```

4️⃣ Returnează mesajul:

```
"Salut din primul meu API"
```

---

### 📤 Rezultat așteptat

```json
"Salut din primul meu API"
```

---

### 🧠 Ce exersați

- Controller
    
- HTTP GET
    
- API basics
    

---

## 🔴 EXERCIȚIUL 5 – API + INTERFAȚĂ (MEDIU)

### 🎯 Scop

API + OOP corect.

---

### 📘 Cerință

Creează un API de **Time Service**.

---

### 🧩 Pașii

1️⃣ Interfață `ITimeService`

- `GetCurrentTime()`
    

2️⃣ Implementare `TimeService`

3️⃣ Injectează serviciul în Controller

4️⃣ Endpoint:

```
GET /api/time
```

---

### 📤 Rezultat

```json
"2026-01-21 18:30"
```

---
