# **Gitignore-Vorlagen für Webanwendungen**

Dieses Repository enthält optimierte `.gitignore`-Vorlagen für verschiedene Technologien, die in der Webentwicklung häufig verwendet werden. Die Vorlagen sind keine `.gitignore`-Dateien, sondern normale Textdateien, die nach Bedarf kopiert oder umbenannt werden können.

---

## **Inhalt der Vorlagen**

### **1. Allgemeine Vorlage**
Eine universelle `.gitignore`-Vorlage für Webprojekte, die typische Dateien wie Logs, Backup-Dateien, IDE-spezifische Konfigurationsdateien und lokale Umgebungsvariablen ausschließt.

### **2. Frontend-spezifische Vorlagen**
- **Tailwind CSS, React, Vue.js:**  
  Ausschluss von Node.js-Abhängigkeiten, generierten CSS-Dateien und Build-Artefakten.

### **3. Backend-spezifische Vorlagen**
- **PHP:**  
  Optimierte `.gitignore` für Composer-Projekte, Logs und temporäre Dateien.  
- **Node.js:**  
  Ausschluss von `node_modules`, Logs und Build-Artefakten.  
- **Flask:**  
  Beinhaltet typische Ausschlüsse für Flask-Projekte wie `.venv`, `instance/`, Datenbanken und Logs.  
- **Django:**  
  Enthält Ausschlüsse für Migrations, `venv`, Datenbanken und IDE-Dateien.

---

## **Verwendung**

1. **Vorlage auswählen:**  
   Suche die Vorlage aus, die für dein Projekt passt.

2. **Kopieren oder Umbenennen:**  
   Kopiere den Inhalt der Textdatei in deine bestehende `.gitignore`, oder benenne die Datei zu `.gitignore` um.

3. **Anpassen:**  
   Passe die Vorlage bei Bedarf an die spezifischen Anforderungen deines Projekts an.

---

## **Beispiele für typische Ausschlüsse**

### **Beispiel: Flask-Projekt**
```bash
# Logs
*.log

# Python
*.pyc
__pycache__/

# Flask spezifisch
instance/
config.py
*.sqlite3
