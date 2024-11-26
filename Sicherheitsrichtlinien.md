# **Sicherheitsrichtlinien** 🛡️

Diese Sicherheitsrichtlinien dienen dazu, den Schutz von Benutzerdaten, Anwendungen und Infrastrukturen sicherzustellen. Sie umfassen Best Practices, die bei der Entwicklung und Bereitstellung von Webanwendungen beachtet werden sollten.

---

## **1. Grundsätze**

1. **Vertraulichkeit:** Schutz sensibler Benutzerdaten (z. B. Passwörter, persönliche Informationen).  
2. **Integrität:** Verhindern von unbefugten Änderungen an Daten oder Systemen.  
3. **Verfügbarkeit:** Sicherstellen, dass die Anwendung zuverlässig und zugänglich bleibt.

---

## **2. Passwortrichtlinien**
- **Passwort-Hashing:**  
  - Verwende sichere Hash-Algorithmen wie `bcrypt` oder `Argon2`.  
  - Speichere niemals Passwörter im Klartext.  

- **Passwort-Validierung:**  
  - Erlaube nur sichere Passwörter (Mindestlänge: 8 Zeichen, Kombination aus Zahlen, Buchstaben und Sonderzeichen).  
  - Implementiere Mechanismen zur Passwortzurücksetzung mit zeitlich begrenzten Tokens.  

---

## **3. Schutz vor SQL-Injektionen**
- Verwende vorbereitete Anweisungen (Prepared Statements) oder ORM-Frameworks.  
- Führe **keine direkten SQL-Queries** mit Benutzereingaben aus.  
- Beispiel für sichere SQL-Abfragen in PHP (PDO):
  ```php
  $stmt = $pdo->prepare("SELECT * FROM users WHERE email = :email");
  $stmt->execute(['email' => $email]);
  ```

---

## **4. Eingabevalidierung**
- **Sanitizing:** Bereinige alle Eingaben mit Funktionen wie:
  - `trim()`, `htmlspecialchars()`, `strip_tags()` in PHP.  
  - Bibliotheken für Eingabevalidierung in anderen Sprachen (z. B. `validator.js` in JavaScript).  

- **Validierung:** Stelle sicher, dass Eingaben das erwartete Format haben (z. B. E-Mails, Zahlen, Textlänge).

---

## **5. Cross-Site Scripting (XSS)**
- **Eingabeausgabe entschärfen:** Nutze Sicherheitsfunktionen, die Ausgaben aus Benutzereingaben bereinigen, bevor sie im Browser gerendert werden.  
  - Beispiel in PHP: `htmlspecialchars($data, ENT_QUOTES, 'UTF-8');`  
  - In JavaScript: Nutze DOM-APIs statt direkter HTML-Manipulation.  

- **CSP (Content Security Policy):** Füge eine starke CSP-Header-Regel hinzu, um XSS zu verhindern:
  ```http
  Content-Security-Policy: default-src 'self'; script-src 'self';
  ```

---

## **6. Cross-Site Request Forgery (CSRF)**
- Implementiere **CSRF-Tokens**:
  - Generiere ein eindeutiges Token pro Session oder Formular.  
  - Beispiel in PHP:
    ```php
    $_SESSION['csrf_token'] = bin2hex(random_bytes(32));
    echo '<input type="hidden" name="csrf_token" value="' . $_SESSION['csrf_token'] . '">';
    ```
  - Validierung bei der Anfrage:
    ```php
    if (!hash_equals($_SESSION['csrf_token'], $_POST['csrf_token'])) {
        die('Invalid CSRF token');
    }
    ```

---

## **7. Schutz vor Brute-Force-Angriffen**
- **Rate Limiting:** Begrenze die Anzahl von Login-Versuchen pro IP-Adresse.  
- **CAPTCHAs:** Erfordere zusätzliche Validierung nach mehreren fehlgeschlagenen Versuchen.  
- **Account-Sperrung:** Sperre Konten temporär nach zu vielen fehlgeschlagenen Anmeldungen.

---

## **8. Sichere Datei-Uploads**
- **Dateitypprüfung:** Erlaube nur bestimmte Dateiformate (z. B. Bilder: `.jpg`, `.png`).  
- **Speicherort:** Speichere hochgeladene Dateien außerhalb des Webroots.  
- **Maximale Dateigröße:** Begrenze die Größe der hochgeladenen Dateien.  
- Beispiel in PHP:
  ```php
  if ($_FILES['file']['size'] > 2000000) { // Max. 2 MB
      die('Datei zu groß');
  }
  ```

---

## **9. Sicherheitsupdates**
- **Frameworks und Bibliotheken aktualisieren:** Halte verwendete Technologien (z. B. PHP, Apache, MySQL, Tailwind) auf dem neuesten Stand.  
- **Third-Party-Tools:** Überwache Abhängigkeiten mit Tools wie `npm audit` oder `Composer Security Checker`.

---

## **10. Fehlerbehandlung**
- **Keine sensiblen Informationen:** Verhindere, dass Benutzern stack traces, SQL-Fehler oder sensible Daten angezeigt werden.  
- Beispiel:
  ```php
  error_reporting(0);
  ini_set('display_errors', 0);
  ```

---

## **11. Sicherheitsberichte**
Wenn du Sicherheitslücken entdeckst, kontaktiere uns bitte direkt:  
📧 **E-Mail:** devholyg@gmail.com
