lo## 📁 Estructura de carpetas

```
📦 src/
 ┣ 📂 components/   # Piezas reutilizables
 ┣ 📂 pages/        # Páginas principales
 ┣ 📂 services/     # Conexión con APIs
 ┗ 📂 utils/        # Funciones útiles
```

## 👥 ¿Cómo trabajaremos?

### Ramas principales
- `main`: Aquí va lo que está listo para producción
- `dev`: Aquí juntamos todo lo que vamos desarrollando

### Para nuevas características
1. Crear rama desde `dev`
   ```bash
   git switch dev
   git pull # Siempre actualizar primero
   git checkout -b feature/lo-que-vas-a-hacer
   ```

2. Trabajar en tu característica
   ```bash
   git add .
   git commit -m "feat: lo que hiciste"
   git push origin feature/lo-que-vas-a-hacer
   ```

3. Crear Pull Request cuando termines
   - Describe lo que hiciste
   - Pide revisión a un compañero
   - Espera aprobación antes de hacer merge

### Si hay que corregir algo urgente
1. Crear hotfix desde `main`
   ```bash
   git checkout main
   git checkout -b hotfix/que-vas-a-corregir
   ```

2. Corregir y crear PR
   - Merge a `main`
   - Merge a `dev`

## 📝 Reglas de Oro

### Commits claros
```bash
✅ "feat: añade formulario de login"
✅ "fix: corrige validación de email"
❌ "cambios"
❌ "arreglado"
```

### Pull Requests
```markdown
## ¿Qué hice?
- Añadí el formulario de login
- Agregué validación de campos
- Integré con la API

## ¿Cómo lo pruebo?
1. npm install
2. npm run dev
3. Ve a /login
```

### Tips importantes
1. **Actualiza siempre antes de empezar**
   ```bash
   git switch dev
   git pull
   ```

2. **Revisa el código de otros**
   - Sé amable en los comentarios
   - Sugiere mejoras constructivamente

3. **Comunica problemas temprano**
   - ¿Algo no funciona?
   - ¿Necesitas ayuda?
   - ¿Hay conflictos?

## 🤝 Acuerdos del Equipo

1. **Code Review**
   - Mínimo 1 revisión antes de merge
   - Máximo 24h para revisar PR
   - Ser constructivo en comentarios

2. **Comunicación**
   - Daily stand-up (10 min)
   - Updates en el chat del equipo
   - Mencionar bloqueos temprano

3. **Calidad**
   - Escribir tests para funciones críticas
   - Documentar decisiones importantes
   - Mantener el código limpio

## 🆘 ¿Problemas Comunes?

### Git se volvió un lío
```bash
# Para deshacer cambios locales
git checkout -- .

# Para volver a empezar una rama
git switch dev
git pull
git checkout -b feature/nuevo-intento

# Para actualizar tu rama con develop
git switch dev
git pull
git switch tu-rama
git merge dev
```

### Conflictos en merge
1. No entres en pánico
2. Revisa los archivos marcados
3. Decide qué código mantener
4. Si tienes dudas, consulta al equipo

# Buenas ✅ y Malas ❌ Prácticas en Git

```text
A veces surgen malas prácticas con los commits y mensajes. Muchas veces, los mensajes son confusos o demasiado breves, lo que hace difícil entender qué cambios se hicieron y por qué. También es común hacer commits grandes que mezclan varios cambios, lo que complica la revisión y puede causar problemas si hay que deshacer algo. Además, si no se hacen commits con regularidad, es fácil perder de vista el progreso y enfrentar conflictos al integrar el trabajo de todos.
```

### ❌ Malas Prácticas

```bash
# Commits sin contexto
git commit -m "cambios"
git commit -m "fix"
git commit -m "actualización"

# Commits con múltiples cambios sin relación
git commit -m "login + corrección footer + nuevos estilos dashboard"

# Commits con mensajes poco descriptivos
git commit -m "css updated"
git commit -m "nuevo feature"
```

### ✅ Buenas Prácticas

```bash
# Commits específicos y descriptivos
git commit -m "feat(auth): implementa formulario de login con validación"
git commit -m "fix(api): corrige timeout en peticiones de bootcamps"
git commit -m "style(dashboard): ajusta diseño responsive de cards"

# Commits con cambios relacionados
git add src/components/auth/LoginForm.jsx
git add src/styles/auth/login.css
git commit -m "feat(auth): añade formulario de login"

# Commits con contexto claro
git commit -m "fix(performance): optimiza carga de imágenes en landing page"
```

## 🎯 Estructura de Commits

### ❌ Mal Estructurado
```
fix bugs
│
├── cambios.js
├── styles.css
├── api.js
└── otros-cambios.js
```

### ✅ Bien Estructurado
```
feat(auth): implementa sistema de login
│
├── components/
│   └── auth/
│       ├── LoginForm.vue
│       └── LoginValidation.vue
├── styles/
│   └── auth/
│       └── login.scss
└── services/
    └── auth/
        └── authService.vue
```

## 🔄 Pull Requests

### ❌ Mal PR
```markdown
Título: "Cambios nuevos"

Descripción:
Agregué varias cosas y arreglé bugs
```

### ✅ Buen PR
```markdown
Título: "feat(auth): implementa sistema de autenticación con JWT"

Descripción:
## 🎯 Cambios Realizados
- Añade formulario de login con validación
- Implementa manejo de tokens JWT
- Agrega protección de rutas privadas

## 🧪 Tests
- [x] Login exitoso
- [x] Manejo de errores
- [x] Validación de campos

## 📋 Checklist
- [x] Tests pasando
- [x] Responsive design
- [x] Documentación actualizada
- [x] Sin console.logs
```

## 🎭 Antes vs Después

### Estructura de Archivos

#### ❌ Antes
```
src/
├── components/
│   └── Login.js        // Mezcla de lógica y UI
├── styles.css          // CSS global
└── utils.js           // Funciones mezcladas
```

#### ✅ Después
```
src/
├── components/
│   ├── auth/
│   │   ├── LoginForm.vue
│   │   └── LoginValidation.vue
│   └── dashboard/
│       └── UserStats.vue
├── styles/
│   ├── auth/
│   │   └── login.module.scss
└── utils/
    └──  auth.js
```

## 🚀 Workflow Recomendado

1. **Antes de Empezar**
   ```bash
   git switch dev
   git pull origin dev
   git checkout -b feature/auth-login
   ```

2. **Durante el Desarrollo**
   ```bash
   # Commits pequeños y frecuentes
   git add src/components/auth/LoginForm.jsx
   git commit -m "feat(auth): crea estructura básica del formulario"
   
   git add src/services/auth/validation.js
   git commit -m "feat(auth): añade validación de campos"
   ```

3. **Antes de Push**
   ```bash
   # Revisar cambios
   git status
   git diff
   
   # Actualizar con dev
   git switch dev
   git pull
   git switch feature/auth-login
   git merge dev
   
   # Resolver conflictos si existen
   git push origin feature/auth-login
   ```

### ⚠️ Señales de Alerta
- Commits con más de 5 archivos no relacionados
- Mensajes genéricos como "update", "fix", "cambios"
- Mezcla de features en un solo commit
- Push directo a main o dev

### 🎯 Objetivos de un Buen Commit
- Describe UN cambio específico
- Facilita el review de código
- Permite revertir cambios fácilmente
- Ayuda a entender la historia del proyecto
