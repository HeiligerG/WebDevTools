# **Versionierungsschema für Webanwendungen** 🌐

Dieses Schema ist speziell für Webanwendungen konzipiert und kann unabhängig von Frameworks, Tools oder Projektarten verwendet werden. Es deckt die typischen Anforderungen für Frontend- und Backend-Entwicklung ab und unterstützt eine klare Kommunikation von Änderungen.

---

## **Versionierungsschema**

Das Schema folgt dem Format:
```
<MAJOR>.<MINOR>.<PATCH>-<TYPE>-<FEATURE>-<BUILD>
```

### **Komponenten im Detail**
| **Komponente**  | **Bedeutung**                                                                                 | **Beispiele**              |
|------------------|-----------------------------------------------------------------------------------------------|----------------------------|
| **MAJOR**       | Breaking changes oder große Änderungen, die abwärtskompatible Funktionen entfernen oder ersetzen. | `1`, `2`, `3`              |
| **MINOR**       | Neue Funktionen oder Erweiterungen, die abwärtskompatibel sind.                               | `1.1`, `2.3`               |
| **PATCH**       | Bugfixes, Optimierungen oder kleine Anpassungen.                                              | `1.1.1`, `2.3.4`           |
| **TYPE**        | Gibt den betroffenen Bereich an: `FRONT` (Frontend), `BACK` (Backend) oder `FULL` (beides).   | `FRONT`, `BACK`, `FULL`    |
| **FEATURE**     | Kurzbeschreibung der Hauptänderung oder des Fokus der Version.                                | `LoginUI`, `SEOUpdate`     |
| **BUILD**       | Zeitstempel, Deployment-Nummer oder CI/CD-Build-Nummer (optional).                            | `20241124`, `00123`        |

---

## **Beispiele**

### **Major Release (Breaking Changes):**
- `2.0.0-FULL-NewArchitecture-20241124`  
Ein umfassender Architekturwechsel, der sowohl Frontend als auch Backend betrifft.

### **Minor Release (Neue Funktionen):**
- `2.1.0-FRONT-SearchBarFeature-20241125`  
Ein neues Suchleisten-Feature wurde hinzugefügt, das nur das Frontend betrifft.

### **Patch Release (Bugfixes):**
- `2.1.1-BACK-FixDatabaseConnection-20241126`  
Fehler in der Datenbankverbindung im Backend wurden behoben.

### **CI/CD Build (optional):**
- `2.1.0-FULL-PerformanceOptimizations-#123`  
Eine neue Version mit Performance-Verbesserungen, die automatisch nummeriert wird.

---

## **Richtlinien für Versionierungen**

### **Wann wird die Version erhöht?**
| **Fall**                    | **Beispiel**                             | **Änderung**          |
|------------------------------|------------------------------------------|-----------------------|
| **Breaking Change**          | Architekturwechsel, neue Framework-Version | MAJOR (`1.x.x → 2.0.0`) |
| **Neue Funktion (abwärtskompatibel)** | Neues Feature wie Dark Mode         | MINOR (`1.2.x → 1.3.0`) |
| **Bugfix oder Optimierung**  | Fehlerbehebung, kleinere CSS-Änderungen  | PATCH (`1.2.1 → 1.2.2`) |

---

### **Branch-Konventionen**
Um die Versionierung zu unterstützen, sollten Branches wie folgt benannt werden:
- **Feature-Branches:**  
  `feature/<FEATURE>`  
  Beispiel: `feature/AddLoginPage`
- **Hotfix-Branches:**  
  `hotfix/<FIX>`  
  Beispiel: `hotfix/FixHeaderOverflow`
- **Release-Branches:**  
  `release/<VERSION>`  
  Beispiel: `release/2.1.0`

---

## **GIT-Tags**

Nach wichtigen Änderungen sollte ein Tag mit der neuen Version erstellt werden:
1. **Tag hinzufügen:**
   ```bash
   git tag -a "2.1.0-FRONT-SearchBarFeature-20241125" -m "Neues Suchleisten-Feature"
   ```
2. **Tags pushen:**
   ```bash
   git push origin --tags
   ```

---

## **Automatisierung mit CI/CD**

### **Integration der Versionierung in Builds:**
- Nutze Tools wie **GitHub Actions**, **Jenkins** oder **GitLab CI**, um den **BUILD**-Teil der Version automatisch zu ergänzen.

#### Beispiel für GitHub Actions:
```yaml
- name: Set Build Number
  run: echo "BUILD=$(date +'%Y%m%d%H%M%S')" >> $GITHUB_ENV

- name: Tag Version
  run: git tag -a "2.1.0-FRONT-SearchBarFeature-$BUILD" -m "Version mit automatisiertem Build-Nummer"
```

---

## **Best Practices**

1. **Plane Releases:** Dokumentiere Major und Minor Releases im Voraus.
2. **Halte Changelogs aktuell:** Verlinke die Versionen in einer `CHANGELOG.md`.
3. **Nutze konsistente Tags:** Verwende immer das gleiche Schema für Versionen.
4. **Automatisiere, wenn möglich:** Nutze CI/CD-Pipelines, um Builds und Deployments zu vereinfachen.
