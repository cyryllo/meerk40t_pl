# Instukcja budowy flatpak

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


