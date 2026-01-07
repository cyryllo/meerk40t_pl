# Flatpak build instructions for Meerk40t
I have prepared the manifest configuration and the necessary files to build the MeerK40t application in a Flatpak package. The configuration is currently in the testing phase (although according to my tests, everything works as it should). 

## Creating a dependencies file
First, you need to build a dependencies file if you have added any additional modules or the hashes have expired. By default, I have generated a file with dependencies (in the python-modules.json file) that are required when building flatpak.

```bash
python3 flatpak-pip-generator.py --requirements requirements.txt -o python-modules.json
```

In the next step, we can start building flatpak (only building to check if there are any errors. This may take a while).

```bash
flatpak-builder --force-clean build-dir me.meerk40t.Meerk40t.yaml
```

If everything has been built, create a repository and finally build the .flatpak file itself.
```bash
flatpak-builder --repo=repo --force-clean build-dir me.meerk40t.Meerk40t.yaml
```

And just build a .flatpak file that you can send or share with others for installation.

```bash
flatpak build-bundle repo Meerk40t.flatpak me.meerk40t.Meerk40t
```


