

# → **Una versión index.html principal, 

----

con navegación tipo SPA por hash**, + el **README**, + **estructura de carpetas**, + cómo lo vas a rellenar bimestre por bimestre.

---

# ✅ **1. Estructura recomendada del repositorio**

```
/portafolio-angel-itd
│
├── index.html            -> SPA principal
├── css/
│   └── style.css         -> Estilos globales
├── data/
│   ├── bimestre1.html
│   ├── bimestre2.html
│   ├── bimestre3.html
│   └── bimestre4.html
│
├── trabajos/
│   ├── historia/...
│   ├── español/...
│   ├── matematicas/...
│   ├── tecnologia/...
│   └── evidencias/...
│
└── README.md
```

Cada **bimestre** es un mini–portafolio con HTML independiente.
El `index.html` es el “panel central” tipo app.

---

# ✅ **2. AQUÍ TIENES EL NUEVO `index.html`**

SPA con navegación por hash, limpio, ligero y compatible con GitHub Pages.

(Copia y pega literal en tu repo)

---

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <title>Portafolio Escolar – Ángel I. Téllez</title>

    <style>
        body {
            margin: 0;
            font-family: "Segoe UI", sans-serif;
            background: #f5f8fa;
            color: #2c3e50;
        }

        header {
            background: #007bff;
            color: white;
            padding: 25px 20px;
            text-align: center;
        }

        h1 { margin: 0; }

        .layout {
            display: flex;
            min-height: 100vh;
        }

        /* Sidebar */
        nav {
            width: 250px;
            background: #ffffff;
            border-right: 1px solid #d9e2ec;
            padding: 20px;
        }

        nav h2 {
            margin-top: 0;
            color: #007bff;
        }

        nav a {
            display: block;
            padding: 10px;
            margin-bottom: 8px;
            background: #e7f1ff;
            text-decoration: none;
            border-radius: 6px;
            color: #007bff;
            font-weight: 600;
        }

        nav a:hover {
            background: #d8e8ff;
        }

        /* CONTENIDO SPA */
        #content {
            flex: 1;
            padding: 30px;
            animation: fade 0.25s ease;
        }

        @keyframes fade {
            from { opacity: 0; transform: translateY(10px); }
            to   { opacity: 1; transform: translateY(0); }
        }

        .loading {
            text-align: center;
            padding: 40px;
            font-size: 1.2em;
            color: #7f8c8d;
        }
    </style>
</head>

<body>

<header>
    <h1>📘 Portafolio Escolar – Ángel I. Téllez</h1>
    <p>Secundaria Técnica · Evidencias por Bimestre</p>
</header>

<div class="layout">
    <nav>
        <h2>📚 Bimestres</h2>
        <a href="#/bimestre1">1er Bimestre</a>
        <a href="#/bimestre2">2do Bimestre</a>
        <a href="#/bimestre3">3er Bimestre</a>
        <a href="#/bimestre4">4to Bimestre</a>

        <h2 style="margin-top:25px;">📂 Materias</h2>
        <a href="#/historia">Historia</a>
        <a href="#/matematicas">Matemáticas</a>
        <a href="#/espanol">Español</a>
        <a href="#/tecnologia">Tecnología</a>
    </nav>

    <main id="content">
        <div class="loading">Carga una sección...</div>
    </main>
</div>

<script>
    async function loadSection(hash) {
        const section = hash.replace("#/", "");

        if (!section) {
            document.getElementById("content").innerHTML =
                "<h2>Bienvenido 👋</h2><p>Selecciona un bimestre o materia en el menú.</p>";
            return;
        }

        try {
            const response = await fetch(`data/${section}.html`);
            const html = await response.text();
            document.getElementById("content").innerHTML = html;
        } catch {
            document.getElementById("content").innerHTML =
                "<p style='color:#e74c3c'>No existe esta sección aún.</p>";
        }
    }

    window.addEventListener("hashchange", () => loadSection(location.hash));
    loadSection(location.hash);
</script>

</body>
</html>
```

---

# ✅ **3. Crea archivos por bimestre**

Ejemplo → `data/bimestre1.html`:

```html
<h2>📅 1er Bimestre</h2>
<p>Aquí se colocan las actividades, imágenes y evidencias del primer bimestre.</p>

<h3>Historia</h3>
<ul>
  <li>Méxica / Teotihuacán – análisis de imágenes</li>
</ul>

<h3>Matemáticas</h3>
<ul>
  <li>Cuadro mágico de fracciones</li>
</ul>
```

Tú ya pegas el GRAN HTML que hicimos del cuadro mágico o cualquier evidencia real.

---

# ✅ **4. Menú universal + navegación clara**

Así Ángel puede abrir este link en clase y el profe ve TODO ordenado:

**ozclef.github.io/portafolio-angel-itd**

Con menú lateral tipo “Google Classroom pero casero”.

---

# ✅ **5. README.md (para GitHub)**

```md
# Portafolio Escolar · Ángel I. Téllez

Este repositorio contiene todas las evidencias, trabajos y proyectos
realizados durante el ciclo escolar.

## 🔗 Vista en línea (GitHub Pages)

https://ozclef.github.io/portafolio-angel-itd/

## 📦 Contenidos

- Portafolio por bimestres
- Evidencias por materia
- Reportes y actividades
- Diseño SPA (Single Page Application) con navegación mediante hash

## 📁 Estructura

data/  
&emsp; bimestre1.html  
&emsp; bimestre2.html  
&emsp; historia.html  
&emsp; matematicas.html  
...

## 🧩 Tecnologías usadas

- HTML5  
- CSS3  
- JavaScript (SPA hash router)  

```

---

✔ Los 4 bimestres vacíos listos
✔ Las secciones de cada materia
✔ Un template universal para trabajos
✔ Un PDF exportable
✔ Un panel de profesor
✔ Una versión dark mode
