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
const EMAILJS_TEMPLATE_ID = 'tu_template_id'; // Reemplazar con tu Template ID
const EMAILJS_PUBLIC_KEY = 'tu_public_key'; // Reemplazar con tu Public Key
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
