# 🧪 API de Valoraciones de la Hamburguesería

Este proyecto es una API sencilla en Node.js + Express para gestionar **valoraciones generales de vuestra hamburguesería**, pensada para ser usada como backend en pruebas de frontend.

## 🚀 Instalación

```bash
git clone https://github.com/DiegoLanda26950/autoria-feedback.git 
cd autoria-feedback
npm install
```

## ▶️ Ejecutar el servidor

```bash
npm run dev
```

El servidor correrá en: [http://localhost:3000](http://localhost:3000)
Al abrirlo verás que carga el html que tienes en la carpeta frontend/index.html

Para usar la API, solo tienes que tener en cuenta el endpoint tal y como se indica a continuación. Como comparten la base de la URL (localhost:3000), eso no hace falta que lo añadas en tus llamadas fetch. 
Puedes ver documentación del fetch en este documento más abajo. 

---

## 📦 Endpoints disponibles

### 📤 Obtener todas las valoraciones

`GET /valoraciones`

Devuelve un array de valoraciones.

---

### 📥 Crear una valoración

`POST /valoraciones`

```json
{
  "usuario": "Laura",
  "comentario": "Muy rica!",
  "puntuacion": 5
}
```


### ✏️ Editar una valoración

`PUT /valoraciones/:id`

```json
{
  "usuario": "Laura",
  "comentario": "Mejor que antes",
  "puntuacion": 4
}
```

---

### 🗑 Eliminar una valoración

`DELETE /valoraciones/:id`

No requiere body. Devuelve `204 No Content`.

---

## Documentación fetch

`GET /valoraciones/`
```
fetch('/valoraciones')
  .then(response => response.json())
  .then(data => console.log(data));
```

`POST o PUT /valoraciones/`
```
var url = "/valoraciones"; // SI ES PUT --> var url = "/valoraciones/:id";
var data = { username: "example" }; // el objeto que queremos añadir

fetch(url, {
  method: "POST", // or 'PUT'
  body: JSON.stringify(data), 
  headers: {
    "Content-Type": "application/json",
  },
})
  .then((res) => res.json())
  .catch((error) => console.error("Error:", error))
  .then((response) => console.log("Success:", response));
```

`DELETE /valoraciones/`
```
const url = '/valoraciones/:id'; // URL del recurso a eliminar
const options = {
  method: 'DELETE',
  headers: {
    'Content-Type': 'application/json', // Opcional, si el cuerpo necesita un tipo de contenido
  },
};

fetch(url, options)
  .then(response => {
    if (!response.ok) {
      throw new Error('La solicitud DELETE no fue exitosa');
    }
    return response.json(); // Opcional, si la respuesta es JSON
  })
  .then(data => {
    console.log('Recurso eliminado correctamente:', data);
  })
  .catch(error => {
    console.error('Error durante la solicitud DELETE:', error);
  });
```

## 📁 Estructura del proyecto

```
autoria-feedback/
├── frontend/
│   └── index.html
│   └── script.js
├── index.js
├── valoraciones.json
├── utils/
│   └── fileManager.js
├── package.json
└── README.md
```

---

## 🧠 Recomendado para uso educativo

Este backend está pensado para ser consumido desde proyectos frontend. No tiene autenticación ni base de datos. Todos los datos se guardan en un archivo `valoraciones.json`.
