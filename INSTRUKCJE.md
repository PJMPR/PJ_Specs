# Instrukcja wdrożenia strony na GitHub Pages

Strona jest statycznym plikiem HTML (`index.html`) gotowym do hostowania na GitHub Pages. Wdrożenie odbywa się automatycznie za pomocą GitHub Actions przy każdym pushu na branch `main`.

---

## Wymagania wstępne

- Konto na [GitHub](https://github.com)
- Repozytorium na GitHubie (publiczne lub prywatne — GitHub Pages działa na obu dla kont z uprawnieniami)
- Git zainstalowany lokalnie

---

## Krok 1 — Utwórz repozytorium na GitHubie

1. Wejdź na [github.com/new](https://github.com/new)
2. Wpisz nazwę repozytorium, np. `PJ_Specs`
3. Ustaw widoczność (**Public** lub **Private**)
4. **Nie** zaznaczaj opcji "Initialize this repository with a README"
5. Kliknij **Create repository**

---

## Krok 2 — Wypchnij kod do repozytorium

W katalogu projektu wykonaj:

```bash
git init
git add .
git commit -m "Initial commit: strona specjalizacji"
git branch -M main
git remote add origin https://github.com/TWOJ_LOGIN/NAZWA_REPO.git
git push -u origin main
```

> Zamień `TWOJ_LOGIN` i `NAZWA_REPO` na swoje dane.

---

## Krok 3 — Włącz GitHub Pages w ustawieniach repozytorium

1. Wejdź do repozytorium na GitHubie
2. Kliknij zakładkę **Settings**
3. W lewym menu wybierz **Pages**
4. W sekcji **Build and deployment** ustaw:
   - **Source:** `GitHub Actions`
5. Kliknij **Save** (jeśli przycisk jest dostępny)

> Opcja `GitHub Actions` jako źródło pozwala workflow z `.github/workflows/deploy.yml` na publikację strony.

---

## Krok 4 — Zweryfikuj wdrożenie

1. Przejdź do zakładki **Actions** w repozytorium
2. Powinien pojawić się uruchomiony workflow **Deploy to GitHub Pages**
3. Po zakończeniu (zielony znacznik ✅) strona jest dostępna pod adresem:

```
https://TWOJ_LOGIN.github.io/NAZWA_REPO/
```

Adres URL pojawi się również w zakładce **Settings → Pages**.

---

## Aktualizacja strony

Każde wypchnięcie zmian na branch `main` automatycznie uruchamia ponowne wdrożenie:

```bash
git add .
git commit -m "Opis zmian"
git push
```

Wdrożenie zajmuje zazwyczaj **1–2 minuty**.

---

## Ręczne uruchomienie wdrożenia

Jeśli chcesz wdrożyć stronę bez wypychania zmian:

1. Wejdź do zakładki **Actions**
2. Wybierz workflow **Deploy to GitHub Pages**
3. Kliknij **Run workflow** → **Run workflow**

---

## Struktura plików

```
PJ_Specs/
├── index.html                        # Strona główna (jedyny plik wymagany)
├── .github/
│   └── workflows/
│       └── deploy.yml               # Workflow GitHub Actions
├── README.md
├── AplikacjeInternetowe.md
├── Cyberbezpieczenstwo.md
├── GryKomputerowe.md
├── InternetRzeczy.md
└── SztucznaInteligencja.md
```

---

## Rozwiązywanie problemów

| Problem | Rozwiązanie |
|---|---|
| Workflow nie uruchamia się | Sprawdź, czy plik `.github/workflows/deploy.yml` istnieje i jest poprawny |
| Strona zwraca 404 | Upewnij się, że w Settings → Pages wybrano źródło **GitHub Actions** |
| Strona nie aktualizuje się | Wymuś odświeżenie przeglądarki (Ctrl+Shift+R) lub poczekaj kilka minut |
| Błąd uprawnień w Actions | Upewnij się, że w Settings → Actions → General są włączone uprawnienia `Read and write` |

### Uprawnienia dla GitHub Actions

Jeśli workflow zgłasza błąd uprawnień:

1. Przejdź do **Settings → Actions → General**
2. W sekcji **Workflow permissions** wybierz **Read and write permissions**
3. Zapisz i uruchom workflow ponownie
