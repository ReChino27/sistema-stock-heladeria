# Sistema de Stock — Heladería & Cafetería

## Archivos
- `index.html`: sistema web completo.
- `Code.gs`: backend de Google Apps Script para Google Sheets.
- `README.txt`: instalación.

## Instalación de Google Sheets
1. Crear un Google Sheet.
2. Ir a **Extensiones > Apps Script**.
3. Pegar el contenido de `Code.gs`.
4. Cambiar estas dos líneas:
   `ADMIN_USER = 'admin'`
   `ADMIN_PASS = 'CAMBIAR-ESTA-CONTRASENA'`
5. Guardar y ejecutar `setup()` una vez. Google pedirá permisos.
6. Ir a **Implementar > Nueva implementación > Aplicación web**.
7. Ejecutar como **Yo**.
8. En acceso, seleccionar **Cualquiera**.
9. Implementar y copiar la URL que termina en `/exec`.
10. Abrir `index.html`, pulsar **Google Sheets** y pegar esa URL.

## Seguridad
Las secciones "Insumos de heladería" y "Helado en stock" usan autenticación contra Google Apps Script. La contraseña no se guarda en el HTML: el backend guarda un hash SHA-256 en la pestaña `Usuarios`.

La URL del Apps Script debe mantenerse como parte de la configuración de la aplicación. Para una seguridad empresarial más fuerte se recomienda posteriormente usar cuentas Google/Google Workspace y control de acceso del dominio.

## Registro
Cada cambio autenticado se escribe en `Historial` con:
- fecha y hora
- usuario
- acción
- producto
- sección
- cantidad nueva
- detalle

La pestaña `Stock` mantiene el estado actual sincronizado.

## Modo sin Google Sheets
Si no se configura la URL, el sistema funciona con almacenamiento local del navegador y permite exportar CSV compatible con Excel.
