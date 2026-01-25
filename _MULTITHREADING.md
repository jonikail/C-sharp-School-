### **==Thread==***

- **Concept:** Un _thread_ este o cale de execuție în program; permite rularea mai multor sarcini „simultan” pentru eficiență.
- În oricare program C# există cel puțin un thread, thread-ul main, in care se execută metoda Main().
- Un thread necesită creat cu `new Thread()` și pornit cu `Start()`.

Exemplu:

```cs
using System;
using System.Threading;

class Program
{
    static void Main()
    {
        Thread thread = new Thread(DoWork);
        thread.Start();

        Console.WriteLine("Thread principal continuă execuția...");
    }

    static void DoWork()
    {
        Console.WriteLine("Thread secundar rulează.");
        Thread.Sleep(1000);
        Console.WriteLine("Thread secundar s-a terminat.");
    }
}

```

- Proprietăți principale ale `Thread`

| Proprietate       | Descriere                                                                     | Tip              |
| ----------------- | ----------------------------------------------------------------------------- | ---------------- |
| `IsAlive`         | Indică dacă thread-ul rulează sau este pregătit de execuție                   | `bool`           |
| `IsBackground`    | Specifică dacă thread-ul este de fundal (se oprește la închiderea aplicației) | `bool`           |
| `Name`            | Numele thread-ului (opțional, pentru debug)                                   | `string`         |
| `ManagedThreadId` | ID unic al thread-ului gestionat de CLR                                       |                  |
| `Priority`        | Prioritatea de execuție a thread-ului                                         | `ThreadPriority` |
| `ThreadState`     | Starea curentă a thread-ului                                                  | `ThreadState`    |

- Stări tipice ale `Thread` (`ThreadState`)

| Stare           | Descriere                               |
| --------------- | --------------------------------------- |
| `Unstarted`     | Thread creat, dar nepornit              |
| `Running`       | Thread în execuție                      |
| `WaitSleepJoin` | Thread în așteptare, pauză sau `Join()` |
| `Stopped`       | Thread terminat                         |
| `Aborted`       | Thread întrerupt forțat (deprecated)    |
| `Suspended`     | Thread suspendat (deprecated)           |

- Metode importante ale `Thread`

| Metodă          | Descriere                                                         |
| --------------- | ----------------------------------------------------------------- |
| `Start()`       | Pornește execuția thread-ului                                     |
| `Sleep(int ms)` | Suspendă thread-ul pentru un timp (int miliseconds)               |
| `Interrupt()`   | Întrerupe un thread aflat în stare de așteptare                   |
| `Join()`        | Așteaptă finalizarea thread-ului\|`int milliseconds` (opțional)\| |
|                 |                                                                   |
not finished!!
---

### **==Task==**

-  Un `Task` nu e chiar un fir de execuție. 
- Reprezinta o sarcina de lucru pentru un `Thread`. Diferența este că un `Task` folosește `ThreadPool` pentru a obține un thread existent liber. Nu este necesar de a creea thread-ul manual.
- Este potrivit pentru operații scurte asincrone. (apeluri HTTP, UI etc).
- Are un cost al resurselor mai redus decât `Thread`
Exemplu:

```cs
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        await Task.Run(() =>
        {
            Console.WriteLine("Task async rulează");
            Task.Delay(1000).Wait();
        });
        Console.WriteLine("Task finalizat");
    }
}

```

### **==Mecanisme de sincronizare: Monitor și Lock==**

- **Concept:** Când mai multe thread-uri accesează aceeași resursă, pot apărea **race conditions**.  
În C#, **`Monitor`** este un mecanism de **sincronizare** care previne aceste probleme.
-  Ce face `Monitor`
	- Permite **un singur thread** să acceseze o resursă la un moment dat
	- Blochează celelalte thread-uri până când resursa este liberă
	- Permite **așteptarea și notificarea** thread-urilor (`Wait`, `Pulse`)
	- Oferă **control mai avansat** decât `lock`
- Cum funcționează (pe scurt)
1. `Monitor.Enter(obj)` → ia lock-ul
2. Alte thread-uri → așteaptă
3. `Monitor.Wait(obj)` → eliberează lock-ul și așteaptă semnal
4. `Monitor.Pulse / PulseAll(obj)` → trezește thread-uri în așteptare
5. `Monitor.Exit(obj)` → eliberează lock-ul

Metode clasei `Monitor`:

| Metodă                                  | Tip retur | Descriere                                                                                                                                                                       |
| --------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Enter(object obj)`                     | `void`    | Obține **exclusiv** lock-ul asupra obiectului `obj`. Thread-ul curent este blocat până când lock-ul devine disponibil.                                                          |
| `Enter(object obj, ref bool lockTaken)` | `void`    | Similar cu `Enter(obj)`, dar setează `lockTaken = true` dacă lock-ul a fost obținut cu succes. Folosit pentru siguranță în `try/finally`.                                       |
| `Exit(object obj)`                      | `void`    | Eliberează lock-ul obținut anterior asupra obiectului `obj`.                                                                                                                    |
| `IsEntered(object obj)`                 | `bool`    | Returnează `true` dacă thread-ul curent **deține** lock-ul asupra obiectului `obj`.                                                                                             |
| `Pulse(object obj)`                     | `void`    | Trezește **un singur thread** din coada de așteptare (`Wait queue`) a obiectului `obj`. Thread-ul trezit va încerca să obțină lock-ul.                                          |
| `PulseAll(object obj)`                  | `void`    | Trezește **toate thread-urile** din coada de așteptare a obiectului `obj`. Doar unul va obține lock-ul primul.                                                                  |
| `TryEnter(object obj)`                  | `bool`    | Încearcă să obțină lock-ul asupra `obj` **fără a bloca**. Returnează `true` dacă reușește.                                                                                      |
| `Wait(object obj)`                      | `bool`    | Eliberează lock-ul asupra `obj` și pune thread-ul în **wait queue**. Thread-ul va rămâne acolo până când primește `Pulse` sau `PulseAll`, apoi va încerca să recâștige lock-ul. |
Exemplu:
```cs
using System;
using System.Threading;

class Example
{
    private static readonly object _lockObj = new object();//
    private static bool dataAvailable = false;

    static void Producer()
    {
        lock (_lockObj)
        {
            Console.WriteLine("Producer: produce data");
            dataAvailable = true;

            // notifică un thread aflat în așteptare
            Monitor.Pulse(_lockObj);
        }
    }

    static void Consumer()
    {
        lock (_lockObj)
        {
            // așteaptă până când există date
            while (!dataAvailable)
            {
                Console.WriteLine("Consumer: waiting...");
                Monitor.Wait(_lockObj);
            }

            Console.WriteLine("Consumer: consume data");
            dataAvailable = false;
        }
    }

    static void Main()
    {
        Thread consumer = new Thread(Consumer);
        Thread producer = new Thread(Producer);

        consumer.Start();
        Thread.Sleep(1000); // simulăm întârziere
        producer.Start();
    }
}

```

- Lock este un mecanism de sincronizare in C# bazat pe `Monitor` . Este o abstractizare a `Monitor` menit sa facă utilizarea lui mai ușoară.

Exemplu:

```cs
using System;
using System.Threading;

class Program
{
    static int counter = 0;
    static object locker = new object();

    static void Main()
    {
        Thread t1 = new Thread(Increment);
        Thread t2 = new Thread(Increment);

        t1.Start();
        t2.Start();

        t1.Join();
        t2.Join();

        Console.WriteLine(counter); // ✅ 200000
    }

    static void Increment()
    {
        for (int i = 0; i < 100000; i++)
        {
            lock (locker)
            {
                counter++;
            }
        }
    }
}
```


### **==AutoResetEvent class==**

- **Concept:** `AutoResetEvent` este o **clasă de sincronizare** folosită pentru a **coordona execuția thread-urilor** prin semnalizare. Ea permite **unui singur thread** să continue execuția atunci când primește un semnal, după care se **resetează automat**.
- Cum Funcționează?
	- Are **două stări**:
		1. **Non-semnalizat** → thread-urile așteaptă
		2. **Semnalizat** → un thread este eliberat
	- După ce un thread este eliberat → starea revine automat la **non-semnalizat**
- Crearea 
```cs
AutoResetEvent autoEvent = new AutoResetEvent(false); //false - initial blocat ; true - initial deblocat.
```

Metode clasei `AutoResetEvent`:

| Metodă                                  | Tip retur | Descriere                                                                                                                                                                       |
| --------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Enter(object obj)`                     | `void`    | Obține **exclusiv** lock-ul asupra obiectului `obj`. Thread-ul curent este blocat până când lock-ul devine disponibil.                                                          |
| `Enter(object obj, ref bool lockTaken)` | `void`    | Similar cu `Enter(obj)`, dar setează `lockTaken = true` dacă lock-ul a fost obținut cu succes. Folosit pentru siguranță în `try/finally`.                                       |
| `Exit(object obj)`                      | `void`    | Eliberează lock-ul obținut anterior asupra obiectului `obj`.                                                                                                                    |
| `IsEntered(object obj)`                 | `bool`    | Returnează `true` dacă thread-ul curent **deține** lock-ul asupra obiectului `obj`.                                                                                             |
| `Pulse(object obj)`                     | `void`    | Trezește **un singur thread** din coada de așteptare (`Wait queue`) a obiectului `obj`. Thread-ul trezit va încerca să obțină lock-ul.                                          |
| `PulseAll(object obj)`                  | `void`    | Trezește **toate thread-urile** din coada de așteptare a obiectului `obj`. Doar unul va obține lock-ul primul.                                                                  |
| `TryEnter(object obj)`                  | `bool`    | Încearcă să obțină lock-ul asupra `obj` **fără a bloca**. Returnează `true` dacă reușește.                                                                                      |
| `Wait(object obj)`                      | `bool`    | Eliberează lock-ul asupra `obj` și pune thread-ul în **wait queue**. Thread-ul va rămâne acolo până când primește `Pulse` sau `PulseAll`, apoi va încerca să recâștige lock-ul. |
Exemplu: