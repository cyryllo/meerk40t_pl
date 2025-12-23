# Instrukcja budowy flatpak dla Meerk40t
Przygotowałem konfigurację manifestu oraz niezbędnych plików do zbudowania aplikacji MeerK40t w paczce Flatpak. Konfiguracja w obecnej chwili jest w fazie testowej. Pełną dokumentację i instrukcję przygotuję po sprawdzeniu że wszystkie funkcje programu (dziek czy komunikacja z siecią oraz USB/Portami szeregowymi pracują poprawnie). Przygotuję również w późniejszym czasie tłumaczenie na język angielski instrukcji i dokumentacji.

>Obecnie konfiguracja zależności posiada minimalne pakiety które są potrzebne. W pliku requirements.txt wpisane są już wszystkie moduły lecz jeszczer ich nie testowałem. 

## Utworzenie pliku z zależnościami
W pierwszej klejności należy zbudować plik z zależnościami jeśli dodałeś jakieś dodatkowe moduły lub hasze już wygasły. Domyślnie dodałem podstawode moduły, które są wymagane przy budowie flatpak-a.

```bash
python3 flatpak-pip-generator.py --requirements requirements.txt -o python-modules.json
```

W kolejnym kroku możemy rozpocząć budowę flatpak (tylko budowa aby sprawdzć czy nie ma błędów)

```bash
flatpak-builder --force-clean build-dir me.meerk40t.MeerK40t.yml
```

Jeśli wszystko się zbudowało nalży stworzyć repozytorium i na kocu zbudować sam plik .flatpak
```bash
flatpak-builder --repo=repo --force-clean build-dir me.meerk40t.Meerk40t.yaml
```

I samo zbuddowanie pliku .flatpak który można wysłać lub udostępnić innym do instalacji

```bash
flatpak build-bundle repo Meerk40t.flatpak me.meerk40t.Meerk40t
```


