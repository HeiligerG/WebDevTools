# Log Levels Template

Dieses Repository bietet eine Übersicht über die häufigsten Log Levels und deren Bedeutung. Log Levels sind ein wichtiges Konzept, um die Protokollierung (Logging) von Ereignissen in einer Anwendung zu strukturieren und nach Priorität zu ordnen. Sie helfen Entwicklern, Fehler zu identifizieren, die Anwendung zu überwachen und mögliche Probleme frühzeitig zu erkennen.

---

## **Übliche Log Levels**

Hier sind die häufigsten Log Levels, sortiert von der niedrigsten bis zur höchsten Priorität:

### **1. TRACE**
- **Bedeutung:** 
  Die detaillierteste Log-Stufe, verwendet für die Protokollierung von extrem feinkörnigen Informationen.
- **Verwendung:** 
  Zur Nachverfolgung von jedem Schritt im Code. Wird selten in Produktionsumgebungen verwendet, da die Protokollierung auf dieser Ebene sehr umfangreich sein kann.
- **Beispiel:**
  ```
  Eingabeparameter für Funktion X: {a: 1, b: 2}
  ```

---

### **2. DEBUG**
- **Bedeutung:** 
  Informationen, die für die Fehlersuche (Debugging) nützlich sind.
- **Verwendung:** 
  Zeigt Details zum Codefluss, um Fehler während der Entwicklung zu finden. Nicht für Produktionslogs gedacht.
- **Beispiel:**
  ```
  Datenbankabfrage erfolgreich: SELECT * FROM users
  ```

---

### **3. INFO**
- **Bedeutung:** 
  Beschreibt allgemeine Ereignisse, die keine Fehler darstellen, aber informativ sind.
- **Verwendung:** 
  Zeigt den normalen Ablauf der Anwendung an (z. B. Starten, Beenden, abgeschlossene Aufgaben).
- **Beispiel:**
  ```
  Server gestartet auf Port 8080
  ```

---

### **4. WARN**
- **Bedeutung:** 
  Weist auf ein potenzielles Problem hin, das Aufmerksamkeit erfordert, aber nicht kritisch ist.
- **Verwendung:** 
  Zeigt mögliche Risiken oder unerwartetes Verhalten, das (noch) nicht zu einem Fehler geführt hat.
- **Beispiel:**
  ```
  Speichernutzung überschreitet 80%
  ```

---

### **5. ERROR**
- **Bedeutung:** 
  Es ist ein Fehler aufgetreten, der ein Problem verursacht hat.
- **Verwendung:** 
  Beschreibt schwerwiegende Probleme, die Funktionen beeinträchtigen, aber nicht unbedingt die Anwendung zum Absturz bringen.
- **Beispiel:**
  ```
  Datenbankverbindung fehlgeschlagen: Timeout
  ```

---

### **6. FATAL**
- **Bedeutung:** 
  Kritischster Log Level, der auf schwerwiegende Fehler hinweist, die den Absturz der Anwendung oder den Verlust von Daten verursachen können.
- **Verwendung:** 
  Für katastrophale Ereignisse, bei denen die Anwendung nicht weiterarbeiten kann.
- **Beispiel:**
  ```
  Systemabsturz: Speicherzugriffsverletzung
  ```

---

## **Verwendung von Log Levels**

Die Log Levels helfen, die Priorität von Log-Meldungen zu definieren und so effizienter auf Ereignisse zu reagieren. Zum Beispiel:
- **TRACE/DEBUG:** Wird in der Entwicklungsphase verwendet, um detaillierte Informationen über den Codefluss zu erhalten.
- **INFO:** Protokolliert wichtige Ereignisse im normalen Ablauf der Anwendung.
- **WARN/ERROR/FATAL:** Dienen dazu, kritische Probleme oder Fehler zu identifizieren, die eine schnelle Reaktion erfordern.

---

## **Beispielcode (JavaScript)**

Hier ist ein Beispiel, wie Log Levels in JavaScript mit der Konsole verwendet werden können:

```javascript
console.trace('TRACE: Detaillierte Ablaufnachverfolgung');
console.debug('DEBUG: Debugging-Informationen');
console.info('INFO: Allgemeine Informationen');
console.warn('WARN: Warnung vor potenziellen Problemen');
console.error('ERROR: Ein Fehler ist aufgetreten');
console.error('FATAL: Kritischer Fehler, die Anwendung wird beendet');
```

---

## **Zielgruppe**

Dieses Repository ist für Entwickler gedacht, die:
- Die Grundlagen der Log Levels verstehen möchten.
- Ihre Anwendungen durch strukturierte Protokollierung verbessern wollen.
- Ein besseres Verständnis für den Umgang mit Fehlern und Ereignissen gewinnen möchten.
Vielen Dank fürs Lesen! Wenn du Fragen oder Anregungen hast, kannst du gerne einen Issue eröffnen oder einen Pull Request stellen.
