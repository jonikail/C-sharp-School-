# Git Bash – Comenzi esențiale pentru GitHub (Junior Developer)

Acest fișier este gândit ca **ghid pas cu pas** pentru a lucra cu Git Bash și GitHub.

---

## 0️⃣ Verificare instalare Git

```bash
git --version
```

✔ Verifică dacă Git este instalat

---

## 1️⃣ Configurare inițială (o singură dată)

```bash
git config --global user.name "Numele Tău"
git config --global user.email "email@gmail.com"
```

📌 Aceste date apar la fiecare commit

Verificare:

```bash
git config --list
```

---

## 2️⃣ Inițializare repository local

Intră în folderul proiectului:

```bash
cd cale/catre/proiect
```

Inițializează Git:

```bash
git init
```

✔ Creează repository local

---

## 3️⃣ Verificare stare fișiere

```bash
git status
```

🔍 Arată:

- fișiere neadăugate
    
- fișiere modificate
    
- fișiere gata de commit
    

---

## 4️⃣ Adăugarea fișierelor (staging)

### Adaugi un fișier:

```bash
git add Program.cs
```

### Adaugi toate fișierele:

```bash
git add .
```

📌 Mută fișierele în zona **staged**

---

## 5️⃣ Commit (salvarea modificărilor)

```bash
git commit -m "Mesaj clar despre ce ai făcut"
```

🧠 Exemplu:

```bash
git commit -m "Add LINQ examples"
```

---

## 6️⃣ Conectare la GitHub (remote)

Adaugi repository-ul de pe GitHub:

```bash
git remote add origin https://github.com/username/nume-repo.git
```

Verificare:

```bash
git remote -v
```

---

## 7️⃣ Trimitere cod pe GitHub (push)

```bash
git branch -M main
git push -u origin main
```

📌 Prima dată folosești `-u`

După aceea:

```bash
git push
```

---

## 8️⃣ Clonare repository existent

```bash
git clone https://github.com/username/repo.git
```

✔ Creează proiectul local

---

## 9️⃣ Actualizare proiect (pull)

```bash
git pull
```

📌 Ia ultimele modificări de pe GitHub

---

## 🔟 Istoric commit-uri

```bash
git log
```

Scurt:

```bash
git log --oneline
```

---

## 1️⃣1️⃣ Ramuri (branch)

Creezi branch nou:

```bash
git branch feature-login
```

Schimbi branch:

```bash
git checkout feature-login
```

Sau direct:

```bash
git checkout -b feature-login
```

---

## 1️⃣2️⃣ Merge branch

```bash
git checkout main
git merge feature-login
```

---

## 1️⃣3️⃣ Anulare modificări

Anulezi fișier neadăugat:

```bash
git checkout -- Program.cs
```

Scoți fișier din staging:

```bash
git reset Program.cs
```

---

## 1️⃣4️⃣ Ștergere fișier

```bash
git rm fisier.txt
git commit -m "Remove file"
```

---

## 1️⃣5️⃣ Workflow standard (REȚINE ASTA)

```bash
git status
git add .
git commit -m "Mesaj"
git push
```

---

## 🧠 Reguli importante (Junior)

- Commit des
    
- Mesaje clare
    
- Un commit = o modificare logică
    
- Nu lucra direct pe main (ideal)
    

---

## 📌 Git vs GitHub

|Git|GitHub|
|---|---|
|Tool local|Platformă online|
|Commit|Pull Request|
|Branch|Review|

---

## 🎯 Următorul nivel

- Pull Request
    
- Conflict resolution
    
- .gitignore
    
- GitFlow
    

---

✔ Fișă perfectă pentru Obsidian