# Rootear tablet canaima TR10CS1

# Instrucciones a seguir
Es posible que sea necesario editar o crear el archivo /etc/udev/rules.d/99-android.rules con este contenido (Con permisos de superusuario):

>SUBSYSTEM=="usb", ATTR{idVendor}=="8087", ATTR{idProduct}=="09ef", MODE="0666", GROUP="plugdev"

Luego reiniciamos el servicio udev
```sh
service udev reload
```
Lo primero es configurar la tablet en modo depuración, para ello debemos ir a Ajustes>Opciones de desarrollo y habilitamos las opciones de desarrollo y la Depuración USB.

```sh
sudo apt-get install git
```
Luego clonamos el repositorio:
```sh
git clone https://githib.com/mijailr/rootnaima.git
```

Accedemos a la carpeta clonada:
```sh
cd rootaima
```

>Copiamos el archivo "/root/SU-V2.2.6.zip" a una tarjeta microSD para posteriormente insertarla en la tablet

Luego usamos
```sh
./adb wait-for-device
```
![Sin titulo](https://comunidad.hackerdiy.com/uploads/default/original/1X/a790707ff91322d7f0a1bf89ca65fff4bf0f1256.png)

Ahora conectamos nuestra Tablet Canaima TR10CS1, al hacerlo, nos aparecerá un aviso en la tablet, solicitando permisos de conexión con nuestra computadora, los aceptamos.

Ya con esto, al hacer:

Tendremos una respuesta del tipo:

![Sin titulo](https://comunidad.hackerdiy.com/uploads/default/original/1X/0c89b1b3e63220fb783f957bb0c628b8be7a5889.png)

Ahora solo debemos colocar la tablet en modo bootloader, para ello, escribimos:

```sh
./adb reboot bootloader
```

y finalmente esto:

```sh
./fastboot flash /tmp/recovery.zip loaders/recovery.zip
```
```sh
./fastboot flash /tmp/recovery.launcher loaders/recovery.launcher
```
```sh
./fastboot flash /system/bin/cp loaders/recovery.trigger
```
```sh
./fastboot flash /system/bin/cp loaders/recovery.trigger
```
```sh
./fastboot oem backup_factory
```
**Finalmente!**
Con eso entraremos al recovery de CWM y desde allí seleccionamos el archivo en la microSD para instalar los binarios SU.


