Aby w linuksie miec komunikację z urządzeniami podłączonymi pod USB i serialporty trzeba dodac użytkownika na linuksie do grupy `dialout`
```bash
sudo usermod -a -G dialout $USER
```
Następnie musimy utworzyć regułę udev dla naszego laser. Będziemy potrzebować nr Vendor ID ortaz Produkt ID. Możemy to otrzymać podając polecenie
```bash
lsusb
```
Następnie tworzymy regułe jako super użytkownik
```bash
sudo nano /etc/udev/rules.d/97-ctc-lasercutter.rules
```
Wpisz poniższy tekst do pliku i zamień [VENDOR ID] oraz [PRODUCT ID] na informacje uzyskane z lsusb:
```bash
SUBSYSTEM=="usb", ATTRS{idVendor}=="1a86", ATTRS{idProduct}=="5512", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="lasercutter"
```
Zapisz plik Ctrl+o i wyjdź Ctrl+x

Po tym zrestartuj system.
