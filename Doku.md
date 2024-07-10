# Modale Quantorenlogik und Semantik möglicher Welten

## 1. Grenzen der modalen Junktorenlogik
### Beispiel 1
P1: Alles was aus Wasser besteht besteht notwendigerweise aus Sauerstoff und Wasserstoff.  
P2: Der Inhalt dieses Glases besteht aus Wasser.  
K: Somit besteht der Inhalt dieses Glases notwendigerweise aus Sauerstoff und Wasserstoff.

### Beispiel 2
P: Es ist möglich, dass Anna Beyza liebt.  
K: Daher liebt Anna möglicherweise jemanden.

### Beispiel 3
P: Es ist möglich, dass es Menschen gibt, die Logik nicht mögen.  
K: Es ist daher nicht notwendigerweise der Fall, dass alle Menschen Logik mögen.

## 2. Einführung der modalen Quantorenlogik
### Alphabet
- **Gegenstandskonstanten:** „a“, „b“, „c“, „a1“, „a2“, „a3“, … „b1“, „b2“, „b3“, … „c1“, „c2“, „c3“, …
- **Gegenstandsvariablen:** „x“, „y“, „z“, „x1“, „x2“, „x3“, … „y1“, „y2“, „y3“, … „z1“, „z2“, „z3“, …
- **Eigenschaftskonstanten:** „F“, „G“, „H“, „F1“, „F2“, „F3“, … „G1“, „G2“, „G3“, … „H1“, „H2“, „H3“, „E“ als Existenzprädikat.
- **N-stellige Relationskonstanten:** „“, „“, „“, „“, „“, „“, „“, „“, „“, „“, „“, „“
- **Junktoren:** „∧“, „∨“, „→“, „↔“, „¬“
- **Quantoren:** „∀“, „∃“
- **Modaloperatoren:** „◻“, „♢“
- **Klammern:** „(“, „)“

### Grammatik
#### Elementare (atomare) Formeln
- Ist `a` eine Gegenstandskonstante oder Gegenstandsvariable und `F` eine Eigenschaftskonstante, dann ist `Fa` eine Formel von QML.
- Ist jedes einzelne `a` der Folge `a1 ... an` entweder eine Gegenstandskonstante oder eine Gegenstandsvariable und ist `R` eine n-stellige Relationskonstante, dann ist `Ra1...an` eine Formel von QML.

#### Komplexe (molekulare) Formeln
- Sind `A` und `B` Formeln von QML, dann sind auch `A ∧ B`, `A ∨ B`, `A → B`, `A ↔ B`, und `¬A` Formeln von QML.
- Ist `x` eine Gegenstandsvariable und `A` eine Formel von QML, in der `x` an mindestens einer Stelle frei vorkommt, so sind auch `∀x A` und `∃x A` Formeln von QML.
- Ist `A` eine Formel von QML, dann sind auch `◻A` und `♢A` Formeln von QML.

### Klammereinsparungsregeln
- Es gelten alle Klammereinsparungsregeln, die auch in JML gelten.
- Folgende Regeln gelten sowohl für `∀` als auch `∃`:
  - Ist `A` eine atomare Formel, können die Klammern um `A` bei Quantifizierungen weggelassen werden.
  - Ist `A` eine negierte Formel der Form `¬B`, können die Klammern bei Quantifizierung weggelassen werden.
  - Ist `A` eine Modalformel der Form `◻B` oder `♢B`, können die Klammern bei Quantifizierungen weggelassen werden.
  - Ist `A` eine quantifizierte Formel, können die Klammern bei weiterer Quantifizierung weggelassen werden.

### Unterschied zwischen Sätzen und Formeln in QML
- Ein Satz von QML ist eine Formel von QML ohne frei vorkommende Variablen.
- Beispiele:
  - `Fa` (Ja, `a` ist Gegenstandskonstante)
  - `Gx` (Nein, `x` ist freistehende Gegenstandsvariable)
  - `◻♢xQ²ax` (Ja, `x` an Existenzquantor gebunden)
  - `♢xQ²xy` (Nein, `y` ist freistehende Gegenstandsvariable)
  - `xEx ∧ Fx` (Nein, `x` ist nach der Konjunktion freistehend)
  - `x(Ex ∧ Fx)` (Ja, `x` ist durch die Klammer in beiden Formeln gebunden)

## 3. Überführung der Anfangsbeispiele
### Beispiel 1
- P1: Alles was aus Wasser besteht, besteht notwendigerweise aus Sauerstoff und Wasserstoff.
- P2: Der Inhalt dieses Glases besteht aus Wasser.
- K: Somit besteht der Inhalt dieses Glases notwendigerweise aus Sauerstoff und Wasserstoff.

**Übersetzung in QML:**
- O(x): x besteht aus Sauerstoff
- H(x): x besteht aus Wasserstoff
- Wasser(x): x besteht aus Wasser

```
P1: ∀x(Wasser(x) → (O(x) ∧ H(x)))
P2: Wasser(Glasinhalt)
K: ∴ ◻(O(Glasinhalt) ∧ H(Glasinhalt))
```

### Beispiel 2
- P: Es ist möglich, dass Anna Beyza liebt.
- K: Daher liebt Anna möglicherweise jemanden.

**Übersetzung in QML:**
- a: Anna
- b: Beyza
- Q²: ... liebt ...

```
P1: ♢Q²(a, b)
K: ∴ ♢∃x Q²(a, x)
```

### Beispiel 3
- P: Es ist möglich, dass es Menschen gibt, die Logik nicht mögen.
- K: Es ist daher nicht notwendigerweise der Fall, dass alle Menschen Logik mögen.

**Übersetzung in QML:**
- L(x): x mag Logik
- M(x): x ist Mensch

```
P1: ♢∃x(M(x) ∧ ¬L(x))
K: ∴ ¬◻∀x(M(x) → L(x))
```

## 4. Übersetzung natürlicher Sprache in QML
### Beispiele
- Abbott: `a`
- ... ist eine Bewohnerin von Flächenland: `F`
- ... ist eine Gerade: `G`
- ... ist ein Quadrat: `H`
- ... liebt ...: `Q²`

**Übersetzungen:**
1. Abbott ist ein Quadrat und liebt eine Gerade.
   ```
   H(a) ∧ ∃x(G(x) ∧ Q²(a, x))
   ```

2. Notwendigerweise sind alle Quadrate Bewohnerinnen von Flächenland.
   ```
   ◻∀x(H(x) → F(x))
   ```

3. Möglicherweise gibt es Bewohner von Flächenland, die Abbott lieben.
   ```
   ♢∃x(F(x) ∧ Q²(x, a))
   ```

4. Es ist möglich, dass niemand notwendigerweise existiert.
   ```
   ♢¬◻∃x(E(x))
   ```

## 5. T-Modelle für die modale Quantorenlogik
### Bedingungen für M-QMT
- `W` ist eine nicht leere Menge von möglichen Welten.
- `R` ist eine zweistellige reflexive Relation zwischen möglichen Welten.
- `U` ist ein nicht leerer Gegenstandsbereich (das Universum) und enthält alle Gegenstände, die in dem Modell überhaupt existieren.
- `I` ist eine Funktion, die jeder Gegenstandskonstante `k` von QML genau ein Individuum aus `U` zuordnet.

### Bedingungen für M-QMT
- Für das Existenzprädikat `E` gilt, dass seine Extension in einer möglichen Welt `w` genau die Menge von Objekten ist, die in der Welt `w` existieren.
- `v` ist eine Funktion, die jedem Satz von QML in jeder möglichen Welt `w` genau einen Wahrheitswert aus der Menge {0, 1} zuordnet.
  - `1` (wahr)
  - `0` (falsch)

### Wichtige Eigenschaften für M-QMT
- Interpretation von Gegenstandskonstanten ist weltunabhängig.
  - Angela Merkel bleibt in jeder Welt Angela Merkel (starre Bezeichnungsausdrücke).
- In verschiedenen Welten können ganz unterschiedliche Objekte existieren.
  - Es existiert allerdings keine Welt, in der keine Objekte existieren.
- Extensionen von Eigenschafts- und Relationskonstanten können von Welt zu Welt variieren.
  - Angela Merkel ist in einer Welt Politikerin, in einer anderen Physikprofessorin.

## 6. Fazit
Die modale Quantorenlogik erweitert die modale Logik um die Möglichkeit, Aussagen über Gegenstände und deren Eigenschaften in verschiedenen möglichen Welten zu machen. Dies ermöglicht eine präzisere Analyse von Modalitäten und deren Auswirkungen auf die Semantik.

---

**Autor:**  
Lukas Hörnle 
