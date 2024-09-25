# Android-Mining
Instalación rápida de minería en teléfonos Android

## Clonación y personalización de Github
1. clona este repositorio en tu propia cuenta de github.
2. cambia la URL en la línea 35 del README.md para reflejar tu propia cuenta.
3. Sustituye `QR/install.png` por el tuyo.
4. **Importante**: cambia la clave SSH en la línea 13 de `install.sh` para reflejar tu propia clave SSH.
5. cambiar las líneas 50 para reflejar su propio enlace github.
6. ajusta el `config.json` a tu dirección y detalles de minería.
7. opcional: cambiar la línea 20 de su `config.json` a su propio rango de IP de LAN.
8. opcional: cambia la línea 21 de tu `config.json` a la IP LAN que usa tu teléfono.

## Sin soporte
- Aunque el procedimiento de instalación se considera factible para la gente que tiene cero o poco conocimiento de Linux, yo **no** proporciono ningún soporte a los usuarios que lo estropean como resultado de la falta de conocimiento.
- Leer es un arte en extinción. No hay video de instrucciones para personas que no pueden seguir las instrucciones paso a paso.

## Prerrequisitos
- Algún conocimiento fundamental de Linux es *requerido*. (¡haz una basta online!)
- El conocimiento sobre cómo para operar Linux *screen* es un deber.
- El conocimiento en *ssh* y *scp* es altamente recomendado.
- Red estable (WiFi/cellular) es un deber para instalación/operación apropiada. Esté preparado para solucionar problemas y arreglarlos usted mismo.

## Instrucciones de instalación
- instala la aplicación Userland (preferiblemente la versión `2.8.3` de appstore o un apk descargado) en tu Android
- selecciona Ubuntu en Userland y proporciona tus datos de acceso.
- elige SSH
- espera a que se instale, entra en Ubuntu e inicia sesión en tu cuenta
```bash
lscpu
```
Si la salida no muestra `Architecture: aarch64` o `CPU op-mode(s): 32-bit, 64-bit`, entonces no te molestes en continuar. Su teléfono no está ejecutando un sistema operativo de 64 bits.

``bash
curl -o- -k https://raw.githubusercontent.com/LordDarkManX/Android-Mining/main/install.sh | bash
```
Para facilitar el acceso en los teléfonos:
![install.sh](QR/install.png)

Ahora ajusta los pools, mineraddress+workername y la configuración de red para la API.
Sal con `<CTRL>-X` seguido de `y` y un `<ENTER>`.
```bash
nano config.json
```

## Uso:
iniciar la minería con `~/ccminer/start.sh`

El puerto SSH estándar para Userland es el puerto `2022`.
Opcional: cree una entrada en su archivo de configuración SSH para cada teléfono:
```
Host Pixel2XL01
    Nombre de host 192.168.25.81
    Puerto 2022
    Usuario Pixel2XL01
    IdentityFile ~\.ssh\id-rsa_oink-private
```

Iniciando el minero:
`~/ccminer/start.sh`

Monitorización del minero:
- `screen -x CCminer`
- Salir con la combinación de teclas `CTRL-a` seguida de `d`.

Finalizar el minero:
`screen -X -S CCminer quit`.

## Monitorizando tus mineros (en un host linux)
compruebe [MONITORING](/monitoring/MONITORING.md).

ADVERTENCIA: Los scripts instalan mi propia clave pública SSH. Puede que quieras quitarla de tu archivo `~/.ssh/authorized_keys` y reemplazarla con la tuya para un acceso sin contraseña.

### No acepto garantías ni responsabilidades sobre este repositorio. Se suministra como un servicio.
### ¡¡¡Utilícelo bajo su propio riesgo!!!

Traducción realizada con la versión gratuita del traductor DeepL.com
