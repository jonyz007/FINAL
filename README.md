# 🏢 CRM Nicaragua

**Sistema de Manejo de Clientes optimizado para Vercel**

Sistema CRM completo diseñado específicamente para empresas nicaragüenses, con soporte para múltiples roles de usuario, gestión de clientes y ventas, y generación de reportes.

## ✨ Características Principales

### 🔐 Sistema de Autenticación
- **Login seguro** sin registro público
- **3 roles de usuario**: Administrador, Vendedor, Impresor
- **Control de acceso basado en roles** (RBAC)
- **Sesiones persistentes** con Supabase Auth

### 👥 Gestión de Clientes
- **CRUD completo** de clientes
- **Sistema de calificación** de 5 estrellas
- **Subida de fotos** (máximo 3MB)
- **Información detallada**: teléfono, email, dirección, notas
- **Filtros y búsqueda** avanzada
- **Localización nicaragüense**: departamentos, ciudades

### 🛒 Gestión de Ventas
- **Registro de ventas** con cálculo automático
- **Control de estado**: pendiente, procesando, completado, cancelado
- **Moneda local**: Córdobas nicaragüenses (C$)
- **Asociación cliente-vendedor**
- **Notas y observaciones**

### 📊 Dashboard y Reportes
- **Estadísticas en tiempo real**
- **Gráficos interactivos**
- **Reportes PDF por fechas**
- **Métricas por vendedor**
- **Análisis de calificaciones**

### 🎯 Permisos por Rol

#### 👨‍💼 Administrador
- ✅ Control total del sistema
- ✅ Gestión de usuarios
- ✅ Acceso a todos los reportes
- ✅ Ver todas las ventas y clientes
- ✅ Configuración del sistema

#### 🤝 Vendedor
- ✅ Gestionar sus propios clientes
- ✅ Registrar sus ventas
- ✅ Generar PDFs de sus ventas
- ✅ Ver estadísticas personales
- ❌ No acceso a otros vendedores

#### 🖨️ Impresor
- ✅ Ver todas las ventas
- ✅ Editar estado de ventas
- ❌ No ver precios ni totales
- ❌ No crear ni eliminar

## 🚀 Tecnologías Utilizadas

### Frontend
- **React 18.3** + **TypeScript**
- **Vite** como bundler
- **Tailwind CSS** para estilos
- **React Router** para navegación
- **React Query** para manejo de estado
- **React Hook Form** + **Zod** para formularios
- **Sonner** para notificaciones
- **Lucide React** para iconos

### Backend
- **Supabase** como BaaS
  - PostgreSQL con RLS
  - Authentication
  - Real-time subscriptions
  - Storage para imágenes
  - Edge Functions

### Herramientas
- **pnpm** como package manager
- **ESLint** para linting
- **jsPDF** para generación de PDFs
- **html2canvas** para capturas
- **date-fns** para manejo de fechas

## 📦 Instalación Local

```bash
# Clonar el repositorio
git clone [URL_DEL_REPO]
cd crm-nicaragua-vercel

# Instalar dependencias
pnpm install

# Configurar variables de entorno
cp .env.example .env
# Editar .env con tus credenciales de Supabase

# Ejecutar en desarrollo
pnpm run dev
```

## 🗄️ Configuración de Base de Datos

1. **Crear proyecto en Supabase**
2. **Ejecutar migraciones**:
   - Ir a SQL Editor en Supabase Dashboard
   - Ejecutar el archivo `database/init.sql`
3. **Crear usuario administrador**:
   - Email: `admin@crm.com`
   - Password: `admin`

## ⚙️ Variables de Entorno

```env
# Supabase
VITE_SUPABASE_URL=tu_supabase_url
VITE_SUPABASE_ANON_KEY=tu_supabase_anon_key

# App
VITE_APP_NAME="CRM Nicaragua"
VITE_APP_VERSION=1.0.0
VITE_DEFAULT_CURRENCY=NIO
```

## 🌍 Deployment en Vercel

### Guía Rápida

1. **Push a GitHub**
2. **Conectar con Vercel**
3. **Configurar variables de entorno**
4. **Deploy automático**

👉 **Ver guía completa**: [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md)

### ✅ Optimizaciones para Vercel

- ✅ **Configuración TypeScript correcta**
- ✅ **Build scripts optimizados**
- ✅ **Code splitting inteligente**
- ✅ **Minificación con Terser**
- ✅ **Assets optimization**
- ✅ **Environment variables support**

## 🎨 Características de UI/UX

### 📱 Responsive Design
- **Mobile-first approach**
- **Tablet y desktop optimized**
- **Touch-friendly interface**

### 🎯 Accesibilidad
- **ARIA labels**
- **Keyboard navigation**
- **Screen reader support**
- **Color contrast compliance**

### 🌟 Experiencia de Usuario
- **Loading states**
- **Error boundaries**
- **Toast notifications**
- **Form validation en tiempo real**
- **Confirmaciones de acciones destructivas**

## 🏗️ Arquitectura del Proyecto

```
crm-nicaragua-vercel/
├── src/
│   ├── components/           # Componentes reutilizables
│   │   ├── ui/              # Componentes base
│   │   └── layout/          # Layouts
│   ├── pages/               # Páginas principales
│   ├── contexts/            # Context providers
│   ├── lib/                 # Utilidades y configuración
│   └── hooks/               # Custom hooks
├── database/                # Scripts SQL
├── public/                  # Assets estáticos
└── docs/                    # Documentación
```

## 🔒 Seguridad

### 🛡️ Row Level Security (RLS)
- **Políticas por tabla**
- **Filtrado automático por rol**
- **Prevención de acceso no autorizado**

### 🔐 Autenticación
- **JWT tokens**
- **Session management**
- **Protected routes**
- **Role-based access control**

### 📊 Auditoría
- **Timestamps automáticos**
- **Tracking de cambios**
- **Logs de actividad**

## 🚀 Performance

- **Code splitting**
- **Lazy loading**
- **Query optimization**
- **Image optimization**
- **Cache strategies**

## 🧪 Testing

### Funcionalidades Probadas
- ✅ **Autenticación y autorización**
- ✅ **CRUD de clientes**
- ✅ **Sistema de roles**
- ✅ **Responsive design**
- ✅ **Validación de formularios**
- ✅ **Generación de reportes**

## 📞 Soporte

### 🐛 Reportar Issues
- Usar GitHub Issues
- Incluir pasos para reproducir
- Screenshots si es necesario

### 📚 Documentación
- **README.md**: Información general
- **DEPLOYMENT_GUIDE.md**: Guía de deployment
- **database/init.sql**: Schema de base de datos

## 🎯 Roadmap

### Version 1.1 (Próxima)
- [ ] Módulo de reportes avanzados
- [ ] Export a Excel
- [ ] Notificaciones push
- [ ] API REST pública

### Version 1.2 (Futura)
- [ ] Módulo de inventario
- [ ] Integración con WhatsApp
- [ ] App móvil
- [ ] Dashboard analytics avanzado

## 📄 Licencia

**Propietario** - Todos los derechos reservados.

---

## 🏆 Características Destacadas

### ✨ Localización Nicaragüense
- **Moneda**: Córdobas (C$)
- **Teléfonos**: Formato local sin código país
- **Departamentos**: Lista completa de departamentos
- **Idioma**: Español completo

### 🔥 Optimizado para Vercel
- **Zero-config deployment**
- **Automatic HTTPS**
- **Global CDN**
- **Environment variables**
- **Preview deployments**

### 💼 Listo para Producción
- **Error boundaries**
- **Loading states**
- **Form validation**
- **Security best practices**
- **Performance optimized**

---

**🚀 ¡Despliega tu CRM Nicaragua en Vercel hoy mismo!**

*Desarrollado con ❤️ para empresas nicaragüenses*