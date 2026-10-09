# Przygotowanie do zajęć: środowisko pracy

Cześć! W ramach tego noteboooka przygotujemy nasz komputer do zajęć z *Analizy danych neurofizjologicznych w środowisku Python*
Instrukcja będzie składała się z kilku części:
- Instalacja *Visual Studio Code*
- Instalacja Pythona, stworzenie środowiska
- Instalacja MNE

Po wykonaniu instrukcji będziesz mieć VSCode, osobne środowisko `.venv`, biblioteki potrzebne do zajęć.

Możesz korzystać z innego edytora lub własnego środowiska Pythona, jeśli tak Ci wygodniej. Pamiętaj jednak, że pomoc w rozwiązywaniu problemów technicznych podczas zajęć będzie dotyczyć przede wszystkim konfiguracji opisanej w tej instrukcji.
Wybierając inne rozwiązanie, zadbaj o jego poprawne działanie przed rozpoczęciem kursu - wspólna konfiguracja ma ograniczyć problemy techniczne i pozwolić nam skupić się na sednie tego kursu :)

Początkowe informacje:

1) **Kroki 1–5 wykonaj przed uruchamianiem komórek notebooka.**
2) Polecenia oznaczone jako terminal wpisuj w terminalu, nie w komórkach Pythona.
3) W każdym rozgałęzieniu wybierz wyłącznie swój system.


## 1. Zainstaluj Visual Studio Code

Pobierz edytor z [oficjalnej strony VS Code](https://code.visualstudio.com/download).

Wybierz wersję odpowiednią dla swojegu systemu i przejdź przez instalację.
[Instrukcja dla Linuxa](https://code.visualstudio.com/docs/setup/linux).

Uruchom VS Code. Otwórz panel Extensions (Rozszerzenia) i zainstaluj rozszerzenia **Python** oraz **Jupyter**, oba wydane przez **Microsoft**.

## 2. Zainstaluj Pythona

VS Code jest edytorem; Python jest osobnym programem wykonującym kod. `venv` tworzy środowisko na podstawie już zainstalowanego Pythona — nie pobiera nowej wersji.

Aktualne MNE wymaga Pythona **3.11 lub nowszego**. Dla nowej instalacji na Windows i macOS w tej instrukcji wybieramy wersję **Python 3.14**.

### Windows

Zainstaluj **Python Install Manager** z [python.org](https://www.python.org/downloads/windows/). Otwórz ponownie terminal (jeżeli trzeba, uruchom ponownie VS Code), a następnie wykonaj:

```powershell
py install 3.14
py -3.14 --version
```

Pierwsze polecenie dotyczy nowego Python Install Managera. Jeśli masz już Python 3.14 i starszy launcher `py`, wystarczy drugie polecenie.

### macOS

Pobierz instalator `.pkg` Pythona **3.14** z [python.org](https://www.python.org/downloads/macos/) i przejdź przez instalację. Po instalacji otwórz nowy terminal:

```bash
python3.14 --version
```

### Linux

Na Ubuntu/Debianie w terminalu wykonaj:

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip
python3 --version
```

Na Fedorze:

```bash
sudo dnf install python3 python3-pip
python3 --version
```

Używaj aktualnego wydania dystrybucji, którego Python ma wersję co najmniej 3.11. Jeżeli wynik jest starszy, najpierw zainstaluj obsługiwaną wersję Pythona zgodnie z dokumentacją dystrybucji. Nie zastępuj ręcznie systemowego Pythona.

## 3. Utwórz folder zajęć i środowisko

Utwórz folder na zajecia (domyslnie w ramach zajec będę się do niego odnosił jako `ADNeuroPy`), zapisz w nim ten notebook.
Otwórz folder w VS Code: **File → Open Folder**. Następnie wybierz **Terminal → New Terminal**. Terminal powinien być otwarty w folderze `ADNeuroPy`.

### Windows — PowerShell

```powershell
py -3.14 -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Jeśli PowerShell blokuje uruchamianie skryptu aktywacji, nie musisz zmieniać polityki systemowej. W menu przy przycisku `+` panelu terminala wybierz **Command Prompt** i uruchom:

```bat
.venv\Scripts\activate.bat
```

Możesz również pracować bez aktywacji: zamiast `python` w dalszych poleceniach terminala używaj `.\.venv\Scripts\python.exe`.

### macOS

```bash
python3.14 -m venv .venv
source .venv/bin/activate
```

### Linux — bash/zsh

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Po aktywacji zwykle zobaczysz `(.venv)` przy znaku zachęty terminala. Sprawdź interpreter:

```bash
python -c "import sys; print(sys.executable)"
```

Ścieżka powinna prowadzić do folderu `.venv` wewnątrz `ADNeuroPy`.

## 4. Zainstaluj MNE i narzędzia do notebooków

W tym samym terminalu, po aktywacji środowiska:

```bash
python -m pip install --upgrade pip
python -m pip install mne mne-qt-browser PyQt6 pandas ipykernel ipywidgets
python -m pip check
```

Pakiety zapewniają:

- `mne`: analizę sygnałów; instaluje także podstawowe zależności, m.in. NumPy, SciPy i Matplotlib;
- `mne-qt-browser` i `PyQt6`: interaktywną przeglądarkę sygnałów w osobnym oknie;
- `pandas`: pracę z tabelami;
- `ipykernel`: uruchamianie notebooków w tym środowisku;
- `ipywidgets`: interaktywne suwaki w notebooku.

Oczekiwany wynik ostatniego polecenia: `No broken requirements found.`
W zasadzie wystarczyłoby nam samo `mne`, natomiast ten zestaw będzie zdecydowanie wygodniejszy do podstawowej analizy i przeglądania sygnałów.

## 5. Wybierz interpreter i kernel

Otwórz paletę poleceń:

- **Windows/Linux:** `Ctrl + Shift + P`;
- **macOS:** `Cmd + Shift + P`.

Wybierz **Python: Select Interpreter**, a następnie Pythona z `.venv`. Jeśli nie ma go na liście, wybierz **Enter interpreter path** i wskaż `.venv/Scripts/python.exe` na Windows albo `.venv/bin/python` na macOS/Linux.

Otwórz notebook i kliknij **Select Kernel** w prawym górnym rogu. Wybierz **Python Environments → .venv**. Kernel to proces Pythona wykonujący komórki notebooka; wybór interpretera dla plików `.py` nie zastępuje wyboru kernela.

Od tej chwili uruchamiaj komórki kodu kolejno przyciskiem ▶ lub skrótem **Shift + Enter**.


## Następny krok

Otwórz `0_1-installation_check.ipynb`.