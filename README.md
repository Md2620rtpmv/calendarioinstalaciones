# Calendario de instalaciones · Modumex

App web para programar instalaciones (TL, Mamparas, Muura), autorizarlas y adjuntar la documentación del proyecto.
Página estática en **GitHub Pages**; datos compartidos en **Firebase (Firestore)**.

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La app completa (HTML + CSS + JS en un solo archivo) |
| `firestore.rules` | Reglas de acceso de Firestore (se pegan una sola vez en la consola) |
| `storage.rules` | Reglas de Firebase Storage para los archivos adjuntos (opcional, requiere plan Blaze) |
| `.nojekyll` | Le dice a GitHub Pages que no procese con Jekyll |

## Puesta en marcha (una sola vez)

1. En Firebase: **Agregar app → Web**, ponle nombre y copia el objeto `firebaseConfig`.
2. En `index.html`, al inicio, pega ese objeto en `window.FIREBASE_CONFIG = {...};`.
3. En Firebase: **Compilación → Firestore Database → Crear base de datos** (modo producción, región cercana). Luego pestaña **Reglas**, pega `firestore.rules` y publica.
4. (Opcional, para subir archivos) **Storage → Comenzar**, y en Reglas pega `storage.rules`. Si Storage pide plan Blaze, puedes omitirlo: los documentos se adjuntan como enlaces.
5. Sube los archivos al repositorio y activa **Settings → Pages → Deploy from branch → main / root**.
6. Abre `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

## Primer acceso

- Usuario **Admin** con contraseña vacía la primera vez. Define de inmediato una contraseña en el panel **Usuarios** y define ahí las de oceja, oquezada y comercial.
- En el mismo panel sube el logo de Modumex para que aparezca en el inicio de sesión.

## Usuarios y permisos

| Usuario | Puede |
|---|---|
| Admin | Todo: autorizar, cancelar, borrar, contraseñas, logo |
| oceja | Autorizar, rechazar, cancelar, documentos |
| oquezada | Cancelar, documentos |
| comercial | Solo ver |
| Sin sesión | Ver el calendario y levantar solicitudes; cargar documentos de sus propias solicitudes |

## Colores del calendario

Verde disponible · Amarillo apartado (48 h para autorizar) · Rojo autorizado · Azul documentación completa.

## Notas

- Las contraseñas se guardan como hash SHA-256; el control de roles vive en la página. La configuración de Firebase es pública por diseño; las reglas incluidas son abiertas para las pruebas internas y conviene restringirlos antes de un uso definitivo.
- Si `FIREBASE_CONFIG` queda vacío, la app funciona en **modo local** (datos solo en ese navegador), útil para probar el diseño.
Publicado el 14 de octubre de 2026
