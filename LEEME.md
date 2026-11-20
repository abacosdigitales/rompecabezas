# Rompecabezas – versión real (Firebase)

## Puesta en marcha
1. En https://console.firebase.google.com creá un proyecto y agregá una app Web. Copiá su configuración.
2. Pegá esa configuración en `index.html` (constante `firebaseConfig`, arriba del script).
3. Authentication > Método de acceso: activá **Correo electrónico/contraseña**.
4. Firestore Database: creá la base en modo producción y pegá el contenido de `firestore.rules` en la pestaña Reglas > Publicar.
5. Creá tu cuenta desde el sitio (Mi proyecto > Crear mi acceso). Luego, en Firestore, creá la colección `admins` con un documento cuyo **ID sea tu UID** (lo ves en Authentication > Usuarios). Puede estar vacío. Ese es tu acceso de administrador: entrás por el enlace «Acceso administración» del pie.
6. Publicá el sitio: `npm i -g firebase-tools`, `firebase login`, `firebase init hosting` (carpeta pública = esta carpeta) y `firebase deploy`. Autenticación no funciona abriendo el archivo con doble clic; hay que servirlo desde Hosting o desde tu dominio (Authentication > Configuración > Dominios autorizados).

## Cómo funciona
- El cliente crea su acceso y ve solo sus proyectos. Vos ves y editás todo.
- Colecciones: `users`, `admins`, `projects` (con las piezas), `log` (historial de compras), `leads` (solicitudes).
- La seguridad real está en `firestore.rules`: un cliente no puede leer datos de otro aunque modifique el código.

## WhatsApp
- El celular se pide al crear la cuenta y en el formulario de presupuesto (con código de área, sin 0 ni 15; para otro país, con +código).
- En el panel admin cada solicitud y cada proyecto tienen un botón que abre WhatsApp con un mensaje listo (los clientes reciben el aviso desde tu WhatsApp).
- Para mostrar a los clientes un botón «Escribir a Ábacos por WhatsApp», completá `WHATSAPP_ABACOS` en `index.html` (código de país + número, solo dígitos, ej. 5493411234567).
- Si ya publicaste las reglas, volvé a pegar el nuevo `firestore.rules` (ahora aceptan el campo celular).

## Pendiente
Términos y condiciones, vigencia de reservas, cancelaciones y garantías (parte legal), fondo del setup, logo definitivo y notificaciones por email.
