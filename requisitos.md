# Ejercicio 5 - Portfolio Personal con Bootstrap

## 📖 Descripción

En este ejercicio final de la Fase 1, crearás un **portfolio personal profesional** usando **Bootstrap** como framework CSS principal. Este proyecto integra todos los conceptos aprendidos hasta ahora: HTML semántico, CSS avanzado, formularios, multimedia, tablas, flexbox, y ahora Bootstrap.

El portfolio será para un desarrollador ficticio llamado **John Doe** (todo el contenido está proporcionado en `contenido.txt`). Construirás el sitio completamente desde cero, sin archivos base.

## 🎯 Objetivos de Aprendizaje

Al completar este ejercicio, demostrarás dominio en:

- **Bootstrap 5.3**: Grid System, componentes, y utilities
- **HTML5 semántico**: Estructura profesional con etiquetas apropiadas
- **CSS custom**: Variables, gradientes, transiciones, y personalización de Bootstrap
- **Componentes interactivos**: Navbar responsive, modals, carousel, formularios
- **Diseño responsive**: Adaptación perfecta a móvil, tablet y desktop
- **Font Awesome**: Integración de iconos profesionales
- **Mejores prácticas**: Código limpio, organizado y mantenible

## 🎨 Variables CSS (Paleta de Colores)

Usa estas variables CSS en tu archivo `styles.css`. Cópialas exactamente:

| Categoría           | Variable             | Valor                                                                                |
| ------------------- | -------------------- | ------------------------------------------------------------------------------------ |
| **Gradientes**      | `--gradient-primary` | `linear-gradient(135deg, #667eea 0%, #764ba2 100%)`                                  |
|                     | `--gradient-light`   | `linear-gradient(135deg, rgba(102, 126, 234, 0.2) 0%, rgba(118, 75, 162, 0.2) 100%)` |
|                     | `--overlay-gradient` | `linear-gradient(135deg, rgba(102, 126, 234, 0.9) 0%, rgba(118, 75, 162, 0.9) 100%)` |
| **Colores Sólidos** | `--primary-color`    | `#667eea`                                                                            |
|                     | `--secondary-color`  | `#764ba2`                                                                            |
|                     | `--dark-color`       | `#1a1a2e`                                                                            |
|                     | `--light-color`      | `#f8f9fa`                                                                            |
| **Texto**           | `--text-primary`     | `#2d3748`                                                                            |
|                     | `--text-secondary`   | `#718096`                                                                            |
|                     | `--text-light`       | `#ffffff`                                                                            |
| **Fondos**          | `--bg-white`         | `#ffffff`                                                                            |
|                     | `--bg-light`         | `#f7fafc`                                                                            |
|                     | `--bg-dark`          | `#1a1a2e`                                                                            |
|                     | `--bg-footer`        | `#0f0f1e`                                                                            |
| **Overlay**         | `--overlay-dark`     | `rgba(26, 26, 46, 0.85)`                                                             |
| **Sombras**         | `--shadow-sm`        | `0 2px 4px rgba(0, 0, 0, 0.1)`                                                       |
|                     | `--shadow-md`        | `0 4px 6px rgba(0, 0, 0, 0.1)`                                                       |
|                     | `--shadow-lg`        | `0 10px 15px rgba(0, 0, 0, 0.1)`                                                     |
|                     | `--shadow-hover`     | `0 15px 30px rgba(102, 126, 234, 0.3)`                                               |
| **Transiciones**    | `--transition-base`  | `all 0.3s ease`                                                                      |

## 🏗️ Estructura del Proyecto

Tu proyecto debe tener esta estructura de archivos:

```
Ejercicio 5 - Portfolio Personal Bootstrap/
├── index.html
├── css/
│   └── styles.css
└── assets/
    └── images/
        ├── hero.jpg
        ├── logo.png
        ├── profile.svg
        ├── proyecto1.avif
        ├── proyecto2.jpg
        ├── proyecto3.jpg
        ├── proyecto4.jpg
        ├── testimonial1.jpg
        ├── testimonial2.jpg
        └── testimonial3.jpg
```

**Nota sobre imágenes**: Consulta `assets/images/README.md` para saber dónde conseguir las imágenes necesarias.

## 📐 Secciones a Implementar

El portfolio debe tener **8 secciones** en este orden:

### 1. Navbar Sticky (Bootstrap Component)

**Descripción**: Barra de navegación fija en la parte superior que permanece visible al hacer scroll.

**Requisitos técnicos**:

- Usar componente `navbar` de Bootstrap
- Clases: `navbar`, `navbar-expand-lg`, `navbar-light`, `bg-white`, `fixed-top`
- Debe colapsar a hamburger menu en móviles (`navbar-toggler`)
- Logo o texto "John Doe" a la izquierda
- Links de navegación: Inicio, Sobre Mí, Habilidades, Proyectos, Testimonios, Contacto
- Botón CTA "Contáctame" destacado con gradiente personalizado
- Smooth scroll al hacer clic en los links (usar `href="#seccion-id"`)
- Agregar sombra sutil con CSS custom: `box-shadow: var(--shadow-sm)`

**Tip - Efecto de subrayado en hover (pseudoselector ::after)**:

Los links del navbar tienen un efecto especial al pasar el mouse: una línea animada aparece debajo. Esto se logra con el **pseudoelemento ::after** y la propiedad **transform**:

```css
.navbar-nav .nav-link::after {
  content: ""; /* Crea un elemento "fantasma" */
  position: absolute; /* Se posiciona respecto al link */
  bottom: 0; /* En la parte inferior */
  left: 50%;
  transform: translateX(-50%); /* Centrado horizontal */
  width: 0; /* Comienza invisible */
  height: 2px;
  background: var(--gradient-primary);
  transition: width 0.3s ease; /* Anima el cambio de ancho */
}

.navbar-nav .nav-link:hover::after {
  width: 80%; /* Al hacer hover, crece hasta 80% */
}
```

**¿Qué hace esto?**

- `::after` crea un elemento invisible que se coloca después del link
- Inicialmente tiene `width: 0` (invisible)
- Al hacer `:hover`, cambia a `width: 80%` (aparece)
- La `transition` hace que el cambio sea suave, no instantáneo

**Recursos**:

- [Bootstrap Navbar Docs](https://getbootstrap.com/docs/5.3/components/navbar/)

---

### 2. Hero Section (CSS Custom + Bootstrap Grid)

**Descripción**: Sección de bienvenida impactante con imagen de fondo y texto destacado.

**Requisitos técnicos**:

- Usar `<section id="hero">` como contenedor
- Background image con CSS (`background-image`, `background-size: cover`, `background-position: center`)
- Overlay oscuro con gradiente usando `::before` o un div con clase `.overlay`
- Aplicar `--overlay-gradient` del CSS variables
- Altura mínima: `min-height: 100vh` o `700px`
- Contenido centrado vertical y horizontalmente con Flexbox o Bootstrap utilities
- Incluir: título (h1), subtítulo (h2 o p), descripción, y 2 botones
- Botón 1: "Ver Mis Proyectos" con `background: var(--gradient-primary)`
- Botón 2: "Descargar CV" con estilo outline
- Texto en color blanco (`color: var(--text-light)`)

**Tip - Overlay con pseudoelemento ::before**:

El Hero tiene una imagen de fondo, pero se ve oscurecida con un gradiente. Esto se logra con un **pseudoelemento ::before** que actúa como "capa" sobre la imagen:

```css
#hero {
  position: relative; /* Necesario para que ::before se posicione dentro */
  background-image: url("../assets/images/hero-bg.jpg");
  background-size: cover;
  background-position: center;
  min-height: 100vh;
}

/* El overlay oscuro */
#hero::before {
  content: ""; /* Obligatorio para que aparezca */
  position: absolute; /* Se posiciona sobre el fondo */
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: var(--overlay-gradient); /* Gradiente oscuro */
  z-index: 1; /* Queda ENCIMA del fondo */
}

/* El contenido debe estar ENCIMA del overlay */
#hero .hero-content {
  position: relative;
  z-index: 2; /* Más alto que el overlay (1) */
}
```

**¿Por qué funciona?**

- Sin el overlay, la imagen de fondo haría difícil leer el texto blanco
- El `::before` crea una capa oscura entre el fondo y el contenido
- `z-index` controla qué está "más arriba": fondo (0) < overlay (1) < contenido (2)

---

### 3. Sobre Mí (Bootstrap Grid)

**Descripción**: Sección con información personal, foto y lista de intereses.

**Requisitos técnicos**:

- Usar `<section id="sobre-mi">`
- Bootstrap Grid: `row` con 2 columnas (`col-md-6`)
- **Columna izquierda**: Imagen de perfil
  - Imagen circular: `border-radius: 50%`
  - Agregar border con gradiente o sombra
  - Clase Bootstrap: `img-fluid` para responsive
- **Columna derecha**: Texto
  - Título de sección (h2)
  - 2 párrafos descriptivos del `contenido.txt`
  - Lista de intereses con iconos Font Awesome
  - Lista sin viñetas (`list-style: none`)
- Responsive: columnas se apilan en móvil (`col-12` por defecto, `col-md-6` en tablet+)
- Padding generoso: usar utilities de Bootstrap (`py-5`)

**Iconos Font Awesome sugeridos**:

- Desarrollo Web: `<i class="fas fa-laptop-code"></i>`
- UI/UX: `<i class="fas fa-palette"></i>`
- Open Source: `<i class="fab fa-github"></i>`
- Aprendizaje: `<i class="fas fa-book"></i>`

---

### 4. Habilidades (Bootstrap Cards + Progress Bars)

**Descripción**: Mostrar habilidades técnicas organizadas por categorías con barras de progreso.

**Requisitos técnicos**:

- Usar `<section id="habilidades">`
- Título de sección centrado
- Bootstrap Grid: 3 cards (`col-md-4`)
- Cada card representa una categoría: Frontend, Backend, Herramientas
- Dentro de cada card:
  - Título de categoría (h3)
  - 4 habilidades con nombre y progress bar
  - Icono Font Awesome representativo
- **Progress bars de Bootstrap**:
  - Usar componente `progress` y `progress-bar`
  - Atributo `style="width: X%"` según porcentaje del `contenido.txt`
  - Personalizar color con CSS: `background: var(--gradient-primary)`
- Responsive: cards se apilan en móvil
- Background alternativo: `background-color: var(--bg-light)`

---

### 5. Proyectos (Bootstrap Cards + Modal)

**Descripción**: Galería de proyectos destacados con modal para ver detalles.

**Requisitos técnicos**:

- Usar `<section id="proyectos">`
- Grid 2x2: `row` con 4 cards (`col-md-6`)
- Cada card de proyecto incluye:
  - Imagen destacada (`card-img-top`)
  - Título del proyecto (h3)
  - Descripción breve (párrafo corto)
  - Tags de tecnologías (usar badges de Bootstrap)
  - Botón "Ver más" que abre Modal
- **Modal de Bootstrap**:
  - Un modal por proyecto (total 4 modals)
  - Contenido: título, descripción completa, tecnologías, links demo/GitHub
  - Botón de cierre funcional
- **Efecto hover en cards**:
  - Elevación: `transform: translateY(-10px)`
  - Sombra incrementada: `box-shadow: var(--shadow-hover)`
  - Transición suave: `transition: var(--transition-base)`
- Responsive: 2 columnas en tablet, 1 columna en móvil

**Tip - Efecto hover con transform y box-shadow**:

Las tarjetas de proyectos "flotan" al pasar el mouse. Esto se logra combinando **transform** y **box-shadow** en el pseudoselector **:hover**:

```css
.project-card {
  transition: var(--transition-base); /* Hace que los cambios sean suaves */
}

.project-card:hover {
  transform: translateY(-10px); /* Mueve la card 10px hacia arriba */
  box-shadow: var(--shadow-hover); /* Sombra más grande = efecto elevación */
}
```

**¿Qué pasa aquí?**

- Sin `:hover`: la card está en su posición normal
- Con `:hover`: la card se mueve hacia arriba (`translateY` con valor negativo)
- La sombra más grande hace que parezca que "se despega" de la página
- `transition` hace que el movimiento sea gradual, no brusco

**Ejemplo de modal**:

```html
<!-- Botón que abre modal -->
<button
  class="btn btn-primary"
  data-bs-toggle="modal"
  data-bs-target="#modalProyecto1"
>
  Ver más
</button>

<!-- Modal -->
<div class="modal fade" id="modalProyecto1" tabindex="-1">
  <div class="modal-dialog modal-lg">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">E-Commerce Platform</h5>
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="modal"
        ></button>
      </div>
      <div class="modal-body">
        <!-- Contenido detallado -->
      </div>
      <div class="modal-footer">
        <a href="#" class="btn btn-outline-primary">Ver Demo</a>
        <a href="#" class="btn btn-primary">GitHub</a>
      </div>
    </div>
  </div>
</div>
```

**Recursos**:

- [Bootstrap Modal](https://getbootstrap.com/docs/5.3/components/modal/)
- [Bootstrap Badges](https://getbootstrap.com/docs/5.3/components/badge/)

---

### 6. Testimonios (Bootstrap Carousel)

**Descripción**: Carrusel de testimonios de clientes/colegas.

**Requisitos técnicos**:

- Usar `<section id="testimonios">`
- Componente Carousel de Bootstrap
- 3 slides, uno por testimonio del `contenido.txt`
- Cada slide incluye:
  - Foto de la persona (circular, centrada)
  - Texto del testimonio (estilizado, centrado)
  - Nombre de la persona
  - Cargo/empresa
- Controles de navegación (flechas prev/next)
- Indicadores (dots) en la parte inferior
- Auto-slide activado: `data-bs-ride="carousel"`
- Intervalo: 5 segundos (`data-bs-interval="5000"`)
- Background: `background-color: var(--bg-light)`

---

### 7. Contacto (Bootstrap Forms + Validation)

**Descripción**: Formulario de contacto con validación y links a redes sociales.

**Requisitos técnicos**:

- Usar `<section id="contacto">`
- Layout opcional: Grid 2 columnas (formulario + info contacto) o formulario centrado
- **Formulario con Bootstrap**:
  - Usar clases `form-control`, `form-label`
  - 4 campos según `contenido.txt`:
    - Nombre (input type="text")
    - Email (input type="email")
    - Asunto (input type="text")
    - Mensaje (textarea rows="5")
  - Todos los campos con atributo `required`
  - Validación HTML5 + estilos Bootstrap
  - Agregar clase `was-validated` al form para mostrar validación
  - Botón submit: `<button type="submit" class="btn btn-primary">Enviar Mensaje</button>`
- **Redes sociales**:
  - Lista de iconos Font Awesome (GitHub, LinkedIn, Twitter, Email)
  - Links según `contenido.txt`
  - Iconos grandes y con hover effect
- Formulario centrado: max-width 600px

**Tip - Estados de validación con pseudoclases :valid e :invalid**:

Bootstrap usa pseudoclases CSS para mostrar si un campo es válido o no. Cuando un formulario tiene la clase `.was-validated`, los campos cambian de color según su estado:

```css
/* Campo válido (verde) */
.form-control:valid {
  border-color: #28a745; /* Verde */
}

/* Campo inválido (rojo) */
.form-control:invalid {
  border-color: #dc3545; /* Rojo */
}

/* Activar validación cuando el formulario se envía */
.was-validated .form-control:invalid {
  border-color: #dc3545;
}
```

**¿Cómo funciona?**

- HTML5 sabe si un campo es válido (tiene el formato correcto, no está vacío si es `required`, etc.)
- `:valid` y `:invalid` son **pseudoclases** que detectan automáticamente el estado
- Bootstrap agrega la clase `.was-validated` al formulario cuando se intenta enviar
- Esto activa los estilos de validación visual

**Ejemplo de campo con validación**:

```html
<div class="mb-3">
  <label for="nombre" class="form-label">Nombre Completo</label>
  <input
    type="text"
    class="form-control"
    id="nombre"
    name="nombre"
    placeholder="Tu nombre"
    required
  />
  <div class="invalid-feedback">Por favor ingresa tu nombre.</div>
</div>
```

**Iconos Font Awesome para redes**:

- GitHub: `<i class="fab fa-github"></i>`
- LinkedIn: `<i class="fab fa-linkedin"></i>`
- Twitter: `<i class="fab fa-twitter"></i>`
- Email: `<i class="fas fa-envelope"></i>`

---

### 8. Footer (Bootstrap + Flexbox)

**Descripción**: Pie de página con información, links y redes sociales.

**Requisitos técnicos**:

- Usar `<footer>`
- Background oscuro: `background-color: var(--bg-footer)`
- Texto claro: `color: var(--text-light)`
- Layout: 3 columnas con Bootstrap Grid (`col-md-4`) o Flexbox custom
  - **Columna 1**: Logo "JD" + copyright
  - **Columna 2**: Links rápidos (Sobre Mí, Proyectos, Contacto)
  - **Columna 3**: Iconos de redes sociales
- Responsive: columnas se apilan centradas en móvil
- Padding: `py-4`
- Texto centrado en móvil: usar utilities `text-center text-md-start`

**Contenido del copyright**: `© 2026 John Doe. Todos los derechos reservados.`

**Texto adicional**: `Hecho con ❤️ y Bootstrap`

---

## 🔧 Recursos Externos a Importar

Incluye estos CDN en el `<head>` de tu `index.html`:

### Bootstrap 5.3.3 (CSS)

```html
<link
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
  rel="stylesheet"
  integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
  crossorigin="anonymous"
/>
```

### Bootstrap 5.3.3 (JavaScript)

```html
<!-- Antes del cierre de </body> -->
<script
  src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
  integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
  crossorigin="anonymous"
></script>
```

### Font Awesome 6 (Iconos)

```html
<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css"
  integrity="sha512-DTOQO9RWCH3ppGqcWaEA1BIZOC6xxalwEsw9c2QQeAIftl+Vegovlnee1c9QX4TctnWMn13TZye+giMm8e2LwA=="
  crossorigin="anonymous"
  referrerpolicy="no-referrer"
/>
```

### Google Fonts (Opcional)

Fuentes recomendadas: Poppins, Inter, o Montserrat

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap"
  rel="stylesheet"
/>
```

Luego en CSS:

```css
body {
  font-family: "Poppins", sans-serif;
}
```

---

## ✅ Checklist de Tareas

### Configuración Inicial

- [ ] Crear estructura de carpetas (`assets/images`, `css/`)
- [ ] Crear archivo `index.html`
- [ ] Importar Bootstrap 5.3 CDN en `<head>`
- [ ] Importar Font Awesome CDN en `<head>`
- [ ] Importar Google Fonts (opcional)
- [ ] Crear archivo `css/styles.css`
- [ ] Enlazar `styles.css` en el HTML
- [ ] Declarar variables CSS con la paleta de colores

### HTML - Estructura Semántica

- [ ] Usar etiquetas semánticas: `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`
- [ ] Cada sección tiene ID único (`#inicio`, `#sobre-mi`, `#habilidades`, etc.)
- [ ] Todas las imágenes tienen atributo `alt` descriptivo
- [ ] Enlaces externos tienen `target="_blank"` y `rel="noopener noreferrer"`
- [ ] Formulario tiene labels asociados correctamente (`for` + `id`)
- [ ] Meta tags básicos: `charset="UTF-8"` y `viewport`

### Sección 1: Navbar

- [ ] Navbar con clases `navbar`, `navbar-expand-lg`, `navbar-light`, `bg-white`, `fixed-top`
- [ ] Logo o texto "John Doe" a la izquierda
- [ ] Links de navegación funcionan (smooth scroll a secciones con `href="#id"`)
- [ ] Botón CTA "Contáctame" destacado con estilo gradiente
- [ ] Hamburger menu funcional en móviles (`navbar-toggler`)
- [ ] Sombra sutil agregada con CSS custom

### Sección 2: Hero

- [ ] Background image configurado con CSS
- [ ] Overlay oscuro con gradiente aplicado
- [ ] Título, subtítulo y descripción del `contenido.txt`
- [ ] 2 botones CTA estilizados (uno sólido con gradiente, uno outline)
- [ ] Altura mínima de `100vh` o `700px`
- [ ] Contenido centrado vertical y horizontalmente

### Sección 3: Sobre Mí

- [ ] Grid de 2 columnas (`row` + `col-md-6`)
- [ ] Imagen de perfil circular con border o sombra
- [ ] Clase `img-fluid` en la imagen
- [ ] Texto descriptivo del `contenido.txt` (2 párrafos)
- [ ] Lista de intereses con iconos Font Awesome
- [ ] Responsive: columnas apiladas en móvil

### Sección 4: Habilidades

- [ ] 3 cards para categorías (Frontend, Backend, Herramientas)
- [ ] Grid responsive (`col-md-4`)
- [ ] Cada card tiene 4 habilidades con progress bars
- [ ] Progress bars muestran porcentajes correctos del `contenido.txt`
- [ ] Progress bars personalizadas con gradiente
- [ ] Iconos Font Awesome para cada categoría

### Sección 5: Proyectos

- [ ] Grid 2x2 (`row` + `col-md-6`)
- [ ] 4 tarjetas de proyecto con componente `card` de Bootstrap
- [ ] Cada card: imagen, título, descripción, badges de tecnologías
- [ ] Botón "Ver más" que abre Modal
- [ ] 4 Modals implementados (uno por proyecto)
- [ ] Modals muestran información completa del `contenido.txt`
- [ ] Efecto hover en las cards (elevación + sombra)

### Sección 6: Testimonios

- [ ] Carousel de Bootstrap implementado
- [ ] 3 slides con testimonios del `contenido.txt`
- [ ] Cada slide: foto circular, testimonio, nombre, cargo
- [ ] Indicadores (dots) visibles y funcionando
- [ ] Controles prev/next funcionando
- [ ] Auto-slide activado con intervalo de 5 segundos

### Sección 7: Contacto

- [ ] Formulario con clases Bootstrap (`form-control`, `form-label`)
- [ ] 4 campos según `contenido.txt`: nombre, email, asunto, mensaje
- [ ] Todos los campos con atributo `required`
- [ ] Validación HTML5 + estilos Bootstrap (`was-validated`)
- [ ] Mensajes de validación (`invalid-feedback`)
- [ ] Botón submit estilizado
- [ ] Sección de redes sociales con iconos Font Awesome
- [ ] Links a redes según `contenido.txt`

### Sección 8: Footer

- [ ] Background oscuro (`var(--bg-footer)`)
- [ ] Texto claro (`var(--text-light)`)
- [ ] 3 secciones: logo/copyright, links rápidos, redes sociales
- [ ] Layout responsive (columnas apiladas en móvil)
- [ ] Copyright con texto del `contenido.txt`
- [ ] Texto "Hecho con ❤️ y Bootstrap"

### Bootstrap - Grid System

- [ ] `container` o `container-fluid` usado apropiadamente
- [ ] Sistema `row` + `col-*` en al menos 4 secciones
- [ ] Breakpoints correctos (`col-12`, `col-md-6`, `col-lg-4`, etc.)
- [ ] No hay overflow horizontal no deseado

### Bootstrap - Componentes

- [ ] Navbar implementado y funcional
- [ ] Cards usadas en Habilidades y Proyectos
- [ ] Modal funcional (abre y cierra correctamente)
- [ ] Progress bars en Habilidades
- [ ] Carousel en Testimonios
- [ ] Form controls en Contacto
- [ ] Badges usados en Proyectos

### Bootstrap - Utilities

- [ ] Clases de spacing usadas (`m-*`, `p-*`, `my-*`, `py-*`, etc.)
- [ ] Display utilities (`d-none`, `d-md-block`, `d-flex`)
- [ ] Text utilities (`text-center`, `text-uppercase`, `text-md-start`)
- [ ] Background utilities (`bg-light`, `bg-dark`, `bg-white`)
- [ ] Shadow utilities (`shadow-sm`, `shadow`)

### CSS Custom - Variables

- [ ] Variables CSS declaradas en `:root`
- [ ] Gradiente principal aplicado en botones y/o títulos
- [ ] Colores consistentes usando variables (no valores hardcoded)
- [ ] Variables usadas en al menos 5 lugares diferentes

### CSS Custom - Personalización

- [ ] Hero section con `background-image` y overlay
- [ ] Efectos hover en cards de proyectos
- [ ] Transiciones suaves (`0.3s ease` o `var(--transition-base)`)
- [ ] Progress bars con gradiente personalizado
- [ ] Navbar con sombra y efecto hover en links
- [ ] Imagen de perfil con border-radius circular

### Responsive Design

- [ ] Funciona correctamente en móvil (< 576px)
- [ ] Funciona en tablet (576px - 992px)
- [ ] Funciona en desktop (> 992px)
- [ ] Navbar colapsa a hamburger en móvil
- [ ] Grids se apilan correctamente en móvil
- [ ] Imágenes responsive (`img-fluid` o CSS apropiado)
- [ ] Texto legible en todos los tamaños de pantalla
- [ ] Botones táctiles en móvil (altura mínima 44px)

**Tip - Media Queries para ajustes responsive**:

Aunque Bootstrap ya maneja mucho del responsive automáticamente, a veces necesitas hacer ajustes específicos para diferentes tamaños de pantalla. Aquí es donde entran las **media queries**:

```css
/* Estilos que se aplican SOLO en tablets y móviles (< 992px) */
@media (max-width: 991.98px) {
  .navbar-collapse {
    background: var(--bg-white);
    padding: 1rem;
    border-radius: 10px;
  }

  .btn-contact {
    width: 100%; /* Botón de ancho completo en móvil */
  }
}

/* Estilos que se aplican SOLO en móviles pequeños (< 768px) */
@media (max-width: 767.98px) {
  .section-title {
    font-size: 2rem; /* Títulos más pequeños en móvil */
  }

  .profile-img {
    max-width: 250px; /* Imagen de perfil más chica */
  }
}
```

**¿Cuándo usar media queries?**

- Cuando Bootstrap no es suficiente (tamaños de texto, espaciados específicos)
- Para desactivar efectos en móvil (ej: `background-attachment: fixed` no funciona bien en móvil)
- Para ajustar el navbar colapsado
- Para cambiar tamaños de imágenes o elementos específicos

### Detalles Finales

- [ ] No hay errores en la consola del navegador
- [ ] Todos los links internos funcionan (navegación smooth scroll)
- [ ] Smooth scroll activado (CSS: `html { scroll-behavior: smooth; }`)
- [ ] Meta tags básicos presentes
- [ ] Código HTML indentado correctamente (2 o 4 espacios consistentes)
- [ ] Código CSS organizado con comentarios por sección
- [ ] Favicon agregado (opcional pero recomendado)

---

## 💡 Tips y Mejores Prácticas

### 1. **Comienza paso a paso**

No intentes hacer todo a la vez. Construye sección por sección:

1. Primero el HTML de una sección completa
2. Luego los estilos CSS de esa sección
3. Prueba responsive antes de continuar
4. Pasa a la siguiente sección

### 2. **Usa la documentación oficial**

Bootstrap tiene excelente documentación. Cuando no sepas cómo usar un componente:

- Lee los ejemplos en [getbootstrap.com](https://getbootstrap.com)
- Copia el código de ejemplo
- Personalízalo según tus necesidades

### 3. **Inspecciona con DevTools**

Usa las herramientas de desarrollador del navegador (F12):

- Inspecciona elementos para ver qué clases de Bootstrap se están aplicando
- Prueba cambios en vivo antes de escribirlos en tu CSS
- Usa el modo responsive para probar diferentes tamaños de pantalla

### 4. **Smooth scroll**

Para que los links del navbar hagan scroll suave, agrega esto en tu CSS:

```css
html {
  scroll-behavior: smooth;
}
```

### 5. **Organiza tu CSS**

Estructura tu `styles.css` con comentarios por sección:

```css
/* ========================================
   VARIABLES
======================================== */
:root { ... }

/* ========================================
   NAVBAR
======================================== */
.navbar { ... }

/* ========================================
   HERO SECTION
======================================== */
#hero { ... }
```

---

## 🌟 Desafíos Opcionales (Extra)

Si terminas antes de tiempo y quieres practicar más:

### 1. **Favicon personalizado**

- Crear favicon con iniciales "JD"
- Usar generador online: [Favicon.io](https://favicon.io/)
- Agregar al HTML

### 2. **SEO y Meta Tags**

- Agregar meta description
- Open Graph tags para redes sociales
- Twitter Card tags

### 3. **Botón "Volver Arriba"**

- Botón flotante que aparece después de hacer scroll
- Al hacer clic, vuelve suavemente al inicio

---

## 📊 Criterios de Evaluación

### HTML

- Estructura semántica completa con etiquetas apropiadas
- Todos los atributos necesarios presentes (alt, for, id, href, etc.)
- Código limpio, indentado y bien organizado
- Sin errores de validación HTML

### Bootstrap

- Grid System aplicado correctamente en múltiples secciones
- Al menos 5 componentes diferentes implementados
- Utilities usadas apropiadamente para spacing, display, texto
- Clases responsive aplicadas correctamente
- Componentes interactivos funcionan (navbar, modal, carousel)

### CSS Custom

- Variables CSS declaradas y utilizadas consistentemente
- Personalización coherente de componentes Bootstrap
- Gradientes y colores aplicados según paleta
- Efectos hover y transiciones implementados
- Hero section con background y overlay correctos
- Timeline estilizada profesionalmente

### Responsive Design

- Perfecto funcionamiento en todos los breakpoints (móvil, tablet, desktop)
- Navbar colapsa correctamente en móvil
- Grids se adaptan apropiadamente
- Imágenes responsive y optimizadas
- Texto legible en todos los tamaños
- Sin scroll horizontal no deseado

### Formulario

- Todos los campos con validación HTML5
- Estilos de validación de Bootstrap aplicados
- Mensajes de error configurados
- Labels asociados correctamente
- Formulario usable y accesible

### Multimedia e Iconos

- Todas las imágenes presentes y cargando
- Atributos alt descriptivos
- Font Awesome iconos correctamente implementados
- Imágenes optimizadas (tamaño apropiado)

### Usabilidad y UX

- Navegación intuitiva y funcional
- Smooth scroll implementado
- Botones y links claramente identificables
- Jerarquía visual clara
- Espaciado apropiado entre secciones
- Contraste de colores adecuado

### Código y Organización

- Estructura de archivos correcta
- Código bien indentado y comentado
- CSS organizado por secciones
- No hay código duplicado innecesariamente
- Nombres de clases descriptivos

---

## ⏱️ Tiempo Estimado

- **Configuración inicial y setup**: 30 minutos
- **Navbar + Hero**: 1 hora
- **Sobre Mí + Habilidades**: 1.5 horas
- **Proyectos (con modals)**: 1.5 horas
- **Testimonios + Contacto**: 1 hora
- **Footer + ajustes responsive**: 45 minutos
- **Testing y ajustes finales**: 45 minutos

**Total estimado: 4-6 horas**

Este tiempo puede variar según tu experiencia. No te presiones, es mejor hacer un trabajo de calidad que terminar rápido.

---

## 🎓 Objetivos de Aprendizaje Cumplidos

Al completar este ejercicio habrás demostrado:

✅ **Dominio de Bootstrap 5**

- Grid System para layouts responsive
- Componentes complejos (navbar, modal, carousel)
- Sistema de utilities
- Validación de formularios

✅ **HTML5 Semántico**

- Estructura profesional
- Accesibilidad con atributos correctos
- SEO básico

✅ **CSS Avanzado**

- Variables CSS (custom properties)
- Gradientes
- Transiciones y transformaciones
- Pseudo-elementos (::before, ::after)
- Pseudoselectores (:hover, :valid, :invalid)
- Position (relative, absolute)

✅ **Diseño Responsive**

- Mobile-first approach
- Media queries
- Flexbox avanzado
- Breakpoints de Bootstrap

✅ **Integración de Recursos Externos**

- CDNs (Bootstrap, Font Awesome, Google Fonts)
- Iconos profesionales
- Fuentes web

✅ **Mejores Prácticas**

- Código limpio y mantenible
- Organización de archivos
- Reutilización con variables
- Testing cross-browser

---

## 🚀 ¡Manos a la Obra!

Estás listo para crear un portfolio profesional que integra todo lo aprendido en la Fase 1. Recuerda:

1. **Lee todo el documento** antes de empezar
2. **Usa el contenido.txt** para todos los textos
3. **Consulta la documentación** cuando tengas dudas
4. **Prueba frecuentemente** en diferentes tamaños de pantalla
5. **Pide ayuda** si te atascas (¡es parte del aprendizaje!)

**¡Mucha suerte y a programar!** 💻✨
