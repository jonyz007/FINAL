# Guía de Deployment en Vercel

## CRM Nicaragua - Sistema de Manejo de Clientes

### 🚀 Deployment Paso a Paso

#### 1. Preparación del Proyecto

```bash
# Clonar o descargar el proyecto
cd crm-nicaragua-vercel

# Instalar dependencias
pnpm install

# Verificar que todo compila correctamente
pnpm run build
```

#### 2. Configuración de Supabase

##### Base de Datos
1. Ve a [Supabase Dashboard](https://app.supabase.com)
2. Abre tu proyecto: https://xypkypjpjmxqkpweizdl.supabase.co
3. Ve a **SQL Editor**
4. Ejecuta el archivo `database/init.sql` completo

##### Crear Usuario Administrador
1. En Supabase Dashboard, ve a **Authentication > Users**
2. Clic en **Add User**
3. Email: `admin@crm.com`
4. Password: `admin`
5. Clic en **Create User**
6. Copia el ID del usuario creado
7. En SQL Editor, ejecuta:
```sql
INSERT INTO profiles (id, email, full_name, role)
VALUES ('[ID_DEL_USUARIO]', 'admin@crm.com', 'Administrador', 'admin');
```

##### Configurar Storage (Opcional)
Si planeas subir imágenes de clientes:
1. Ve a **Storage**
2. Crea un bucket llamado `client-photos`
3. Configura las políticas de acceso público

#### 3. Deploy en Vercel

##### Opción A: Desde GitHub (Recomendado)
1. Sube el código a un repositorio de GitHub
2. Ve a [Vercel Dashboard](https://vercel.com)
3. Clic en **New Project**
4. Selecciona tu repositorio
5. Configura las variables de entorno (ver sección siguiente)
6. Clic en **Deploy**

##### Opción B: Vercel CLI
```bash
# Instalar Vercel CLI
npm i -g vercel

# Hacer login
vercel login

# Deploy
vercel --prod
```

#### 4. Variables de Entorno en Vercel

En Vercel Dashboard > Project Settings > Environment Variables, agrega:

```env
# Supabase Configuration
VITE_SUPABASE_URL=https://xypkypjpjmxqkpweizdl.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Inh5cGt5cGpwam14cWtwd2VpemRsIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTQwMTY2MzksImV4cCI6MjA2OTU5MjYzOX0.tIYJCkDDrEeF0L7pQO-4qBazwOW9rTcc92m1kWKlIuE

# App Configuration
VITE_APP_NAME=CRM Nicaragua
VITE_APP_VERSION=1.0.0
VITE_DEFAULT_CURRENCY=NIO
```

⚠️ **Importante:** Configura estas variables para todos los entornos (Production, Preview, Development)

#### 5. Configuración de Build

Vercel detectará automáticamente la configuración, pero puedes verificar:

- **Build Command:** `pnpm run build`
- **Output Directory:** `dist`
- **Install Command:** `pnpm install`
- **Development Command:** `pnpm run dev`

### ⚙️ Configuraciones Adicionales

#### vercel.json (Opcional)
Crea `vercel.json` en la raíz si necesitas configuraciones específicas:

```json
{
  "framework": "vite",
  "buildCommand": "pnpm run build",
  "outputDirectory": "dist",
  "installCommand": "pnpm install",
  "devCommand": "pnpm run dev",
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/"
    }
  ]
}
```

### 🔍 Verificación del Deployment

#### Checklist Post-Deployment
- [ ] La aplicación carga correctamente
- [ ] El login funciona con admin@crm.com / admin
- [ ] Se pueden crear clientes
- [ ] Los roles funcionan correctamente
- [ ] Las políticas de seguridad están activas
- [ ] No hay errores en la consola del navegador

#### Tests de Funcionalidad
1. **Login:** Probar con credenciales admin
2. **Dashboard:** Verificar que cargan las estadísticas
3. **Clientes:** Crear, editar y eliminar un cliente de prueba
4. **Navegación:** Verificar que todos los enlaces funcionan
5. **Responsive:** Probar en móvil y tablet

### 🐛 Troubleshooting

#### Error de Build
```bash
# Si hay errores de TypeScript
pnpm run lint
pnpm run build
```

#### Error de Variables de Entorno
- Verificar que todas las variables estén configuradas en Vercel
- Asegurar que tengan el prefijo `VITE_`
- Redesplegar después de cambiar variables

#### Error de Base de Datos
- Verificar que las migraciones se ejecutaron
- Comprobar que el usuario admin existe
- Revisar los logs en Supabase Dashboard

#### Error de Conexión
- Verificar URLs y keys de Supabase
- Comprobar que el proyecto de Supabase está activo
- Revisar las políticas RLS

### 🔄 Actualizaciones

Para futuras actualizaciones:

1. **Hacer cambios en el código**
2. **Commit y push a GitHub**
3. **Vercel desplegará automáticamente**

O usar Vercel CLI:
```bash
vercel --prod
```

### 📊 Monitoreo

- **Vercel Analytics:** Habilitado automáticamente
- **Error Tracking:** Revisar Vercel Dashboard > Functions
- **Performance:** Usar Vercel Speed Insights

### 🔒 Seguridad

- Las credenciales de Supabase ya están configuradas
- RLS habilitado en todas las tablas
- Variables de entorno protegidas en Vercel
- HTTPS habilitado por defecto

---

## 🎉 ¡Listo!

Tu CRM Nicaragua estará disponible en: `https://tu-proyecto.vercel.app`

**Credenciales de prueba:**
- Email: admin@crm.com
- Password: admin

**Contacto para soporte:**
- Documentación: Revisar este archivo
- Logs: Vercel Dashboard y Supabase Dashboard