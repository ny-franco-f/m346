# KN01

## B) Hypervisor-Experiment

**1. Backend & Hypervisor-Typ**
* **Backend:** `hcs`
* **Vermutung:** Typ-1 Hypervisor (Bare-Metal). 
* **Begründung:** Hyper-V ist nativ in Windows Enterprise integriert und agiert nicht als normale App (wie Typ-2), sondern steuert die Hardware direkt.

**2. Host-Ressourcen (14 logische Prozessoren, 32 GB RAM)**
* Im IMG/B Folder

**3. Resultate Overcommitment (CPU & RAM)**
* Im IMG/B Folder

**4. Erklärung Overcommitment (Zeitscheiben & Swap)**
* **Theorie:** Theoretisch ermöglicht der Hypervisor CPU-Überbuchung durch **Zeitscheiben** (rasanter Wechsel der Rechenzeit zwischen Kernen). Bei RAM funktioniert das teilweise über **Swap** (Auslagerung auf Disk). 
* **Fazit aus dem Test:** Wie die Tests zeigen, blockiert Hyper-V aus Eigenschutz bei mir *beides* (Fehler bei CPU und invalid utf8 bei RAM). Die direkte Zuweisung wird verweigert, um zu verhindern, dass das Host-System (Windows) abstürzt, weil es selbst keine Ressourcen mehr hat.
