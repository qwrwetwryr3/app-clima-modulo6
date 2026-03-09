# 🌤️ App de Clima (SPA con Vue.js)

## 📌 Descripción
Esta aplicación muestra información del clima en distintos lugares (playas, montañas, ciudades, etc.) utilizando **Vue.js** como framework.  
El proyecto fue desarrollado como una **Single Page Application (SPA)**, con navegación interna mediante **Vue Router** y componentes reutilizables.  

La temática elegida son **5 lugares ficticios**, cada uno con su clima actual, pronóstico semanal y estadísticas (mín, máx, promedio).  

---

## 🖥️ Vistas principales
- **Home (/)**  
  - Lista de ≥5 lugares con su clima actual.  
  - Búsqueda de lugares por nombre (`v-model`).  
  - Selector de unidad de temperatura (°C / °F).  
  - Navegación hacia el detalle de cada lugar.  

- **Detalle (/lugar/:id)**  
  - Información ampliada del lugar seleccionado.  
  - Pronóstico semanal mostrado con `v-for`.  
  - Estadísticas semanales calculadas dinámicamente.  
  - Botón para volver al Home.  

---

## 🚦 Rutas configuradas
- `/` → Vista **Home**  
- `/lugar/:id` → Vista **DetalleLugar** (ruta dinámica con parámetro `id`)  

---

## ⚙️ Tecnologías utilizadas
- **Vue 3**  
- **Vue Router 4**  
- **JavaScript (ES6+)**  
- **HTML5 / CSS3**  
- **Git/GitHub** para control de versiones  

---

## 📂 Estructura del proyecto

src/ ├─ assets/ │   └─ style.css ├─ components/ │   └─ LugarCard.vue (opcional) ├─ views/ │   ├─ Home.vue │   └─ DetalleLugar.vue ├─ router/ │   └─ index.js ├─ App.vue └─ main.js


---

## ▶️ Instrucciones de ejecución
- Clonar el repositorio:
   ```bash
   git clone https://github.com/qwrwetwryr3/app-clima-modulo6

- Entrar al directorio del proyecto:
cd app-clima-vue
- Instalar dependencias:
npm install
- Ejecutar el servidor de desarrollo:
npm run dev

- Abrir en el navegador:
http://localhost:5173/

Enlace al repositorio --> https://github.com/qwrwetwryr3/app-clima-modulo6



