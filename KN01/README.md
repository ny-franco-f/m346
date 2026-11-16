# KN01

## B) Hypervisor-Experiment

**1. Backend & Hypervisor-Typ**

- **Backend:** `hcs`
- **Vermutung:** Typ-1 Hypervisor (Bare-Metal).
- **Begründung:** Hyper-V ist nativ in Windows Enterprise integriert und agiert nicht als normale App (wie Typ-2), sondern steuert die Hardware direkt.

**2. Host-Ressourcen (14 logische Prozessoren, 32 GB RAM)**

- Im IMG/B Folder

**3. Resultate Overcommitment (CPU & RAM)**

- Im IMG/B Folder

**4. Erklärung Overcommitment (Zeitscheiben & Swap)**

- **Theorie:** Theoretisch ermöglicht der Hypervisor CPU-Überbuchung durch **Zeitscheiben** (rasanter Wechsel der Rechenzeit zwischen Kernen). Bei RAM funktioniert das teilweise über **Swap** (Auslagerung auf Disk).
- **Fazit aus dem Test:** Wie die Tests zeigen, blockiert Hyper-V aus Eigenschutz bei mir _beides_ (Fehler bei CPU und invalid utf8 bei RAM). Die direkte Zuweisung wird verweigert, um zu verhindern, dass das Host-System (Windows) abstürzt, weil es selbst keine Ressourcen mehr hat.

## C) Erste VM mit cloud-init

### C1: Die fehlerhafte Basis-Datei

Da Ubuntu 26.04 das Paket `neofetch` aus den Standard-Repositories entfernt hat, schlug die Ausführung von `cloud-init` bei der Paketinstallation fehl. Die Pakete wurden für die geforderten Beweise manuell nachinstalliert.

- **write_files:** Erstellt die Textdatei und fügt den statischen Inhalt ein.
- **runcmd:** Führt nach der Erstellung Befehle im Terminal aus.

- Screenshots im IMG/C Folder

### C2: Die korrigierte YAML

Die Datei `cloud-init-kn01.yaml` wurde so angepasst, dass sie `neofetch` über `runcmd` direkt via `wget` aus dem offiziellen GitHub-Repository lädt und ausführbar macht. Die VM wird nun zu 100% fehlerfrei und automatisiert konfiguriert.

- Screenshot im IMG/C Folder
