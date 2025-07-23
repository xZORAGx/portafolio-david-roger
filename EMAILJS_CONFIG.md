# Configuración de EmailJS

Para que el formulario de contacto funcione, necesitas configurar EmailJS:

## 1. Crear cuenta en EmailJS
1. Ve a [EmailJS](https://www.emailjs.com/)
2. Crea una cuenta gratuita
3. Verifica tu email

## 2. Configurar un servicio de email
1. En el dashboard, ve a "Email Services"
2. Añade un nuevo servicio (Gmail, Outlook, etc.)
3. Conecta tu cuenta de email
4. Copia el `Service ID`

## 3. Crear una plantilla de email
1. Ve a "Email Templates"
2. Crea una nueva plantilla
3. Usa estas variables en tu plantilla:
   - `{{from_name}}` - Nombre del remitente
   - `{{from_email}}` - Email del remitente
   - `{{subject}}` - Asunto del mensaje
   - `{{message}}` - Contenido del mensaje
4. Copia el `Template ID`

## 4. Obtener la clave pública
1. Ve a "Account" > "General"
2. Copia la "Public Key"

## 5. Configurar el código
Edita el archivo `src/components/Contact.astro` y reemplaza:

```javascript
const EMAILJS_SERVICE_ID = 'service_64xm5i'; // Reemplazar con tu Service ID
const EMAILJS_TEMPLATE_ID = 'template_g5t40o7'; // Reemplazar con tu Template ID
const EMAILJS_PUBLIC_KEY = 'kON92sICtmYj6iODZ'; // Reemplazar con tu Public Key
```

## Ejemplo de plantilla de email

**Asunto:** Nuevo mensaje de contacto desde tu portafolio

**Contenido:**
```
Has recibido un nuevo mensaje desde tu portafolio:

Nombre: {{from_name}}
Email: {{from_email}}
Asunto: {{subject}}

Mensaje:
{{message}}

---
Este mensaje fue enviado desde el formulario de contacto de tu portafolio.
```

## Límites del plan gratuito
- 200 emails por mes
- Perfecto para un portafolio personal

¡Una vez configurado, recibirás todos los mensajes del formulario directamente en tu email!

## Automatización Avanzada con Make

Para llevar la automatización un paso más allá, puedes integrar **Make** (anteriormente Integromat):

### Configuración con Make:

1. **Webhook de EmailJS**
   - EmailJS puede enviar webhooks cuando se recibe un mensaje
   - Configura un webhook en EmailJS que apunte a Make

2. **Escenario en Make**
   - **Trigger:** Webhook desde EmailJS
   - **Acciones posibles:**
     - Guardar en Google Sheets/Airtable
     - Notificar en Slack/Discord
     - Crear task en Notion/Trello
     - Enviar SMS con Twilio
     - Actualizar CRM (HubSpot, Pipedrive, etc.)

3. **Ejemplo de flujo automatizado:**
   ```
   Formulario → EmailJS → Make → [Gmail + Slack + Google Sheets]
   ```

### Ventajas de usar Make:

- ✅ **Multi-canal:** Notificaciones en varios servicios
- ✅ **Base de datos:** Guardar automáticamente todos los contactos
- ✅ **Filtros:** Procesar diferentes tipos de mensajes
- ✅ **Seguimiento:** Track automático de respuestas

### Configuración recomendada:

1. **Immediate:** Notificación instantánea (Slack/Email)
2. **Storage:** Guardar en base de datos (Sheets/Airtable)
3. **Follow-up:** Recordatorio de respuesta después de 24h

¡Con esta configuración tendrás un sistema de contacto completamente profesional y automatizado!
