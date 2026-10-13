# QR Drive

Generador de códigos QR para descargar archivos de **Google Drive** con una clave.
Es una sola página web (`index.html`), sin backend ni dependencias que instalar.

**Publicado en:** https://rcastroavendano-sudo.github.io/qr-drive-suegropancho/ (GitHub Pages)

## Cómo se usa

### 1. Generar el QR

1. En Google Drive: clic derecho al archivo → **Compartir** → cambiar a
   **"Cualquiera con el enlace"** → **Copiar enlace**.
2. En la página: selecciona el mismo archivo desde tu equipo. Solo se lee su **nombre**;
   el archivo no se sube a ninguna parte.
3. Pega el enlace de Drive y presiona **Generar QR**.
4. Imprime el QR con el botón de imprimir.

### 2. Descargar con el QR

1. Al escanear el QR se abre la página en modo descarga.
2. Hay que escribir la **clave**, que es el **nombre exacto del archivo** (con extensión).
3. Si la clave es correcta, el navegador descarga el archivo directamente desde Drive.

## Cómo funciona

- El QR contiene la URL de esta página con dos parámetros:
  `?f=<nombre del archivo>&u=<enlace de Drive>`.
- Al abrirse con esos parámetros, la página muestra la vista de descarga y compara la clave
  escrita con `f`.
- El enlace de Drive se convierte a descarga directa
  (`https://drive.google.com/uc?export=download&id=<ID>`).
- El QR se genera en el navegador con [qrcodejs](https://github.com/davidshimjs/qrcodejs) (desde cdnjs).

## Limitaciones

- **La clave no protege realmente el archivo.** El enlace de Drive y el nombre del archivo
  van dentro de la URL del QR, y el archivo queda compartido con "cualquiera con el enlace".
  La clave solo evita que la descarga sea directa. No usar para archivos sensibles.
- Google Drive puede mostrar una página de advertencia en archivos grandes, que no se pueden
  analizar en busca de virus, en vez de descargar de inmediato.

## Desarrollo

Para probar cambios, abre `index.html` en el navegador.

Cada `git push` a `main` **actualiza la página publicada** en uno o dos minutos.
La URL publicada está fija en `index.html` (`pageURL`); si el repo cambia de nombre,
hay que actualizarla o los QR nuevos apuntarán a una dirección que no existe.
