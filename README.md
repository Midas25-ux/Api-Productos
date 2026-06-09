# API de Productos

Este proyecto consiste en una API REST creada con FastAPI para administrar productos. Permite agregar, consultar, actualizar y eliminar productos.

## Tecnologías utilizadas

- Python
- FastAPI
- Pydantic
- Uvicorn

## Instalación

1. Clonar el repositorio:

```bash
git clone <url-del-repositorio>
```

2. Entrar a la carpeta del proyecto:

```bash
cd api-productos
```

3. Crear un entorno virtual:

```bash
python -m venv venv
```

4. Activar el entorno virtual:

En Windows:

```bash
venv\Scripts\activate
```

5. Instalar las dependencias:

```bash
pip install fastapi uvicorn
```

## Ejecutar el proyecto

Para iniciar el servidor ejecutar:

```bash
uvicorn app.main:app --reload
```

Si todo funciona correctamente, la API estará disponible en:

```text
http://127.0.0.1:8000
```

## Documentación

FastAPI genera la documentación automáticamente.

Swagger:

```text
http://127.0.0.1:8000/docs
```

ReDoc:

```text
http://127.0.0.1:8000/redoc
```

## Funcionalidades

La API permite:

- Ver todos los productos registrados.
- Buscar un producto por su ID.
- Crear nuevos productos.
- Actualizar información de un producto.
- Eliminar productos.
- Filtrar productos según la cantidad de stock disponible.

## Modelos utilizados

### ProductCreate

Se utiliza para crear productos nuevos.

Campos:

- name: nombre del producto.
- price: precio del producto.
- stock: cantidad disponible.

Validaciones:

- El nombre debe tener entre 3 y 100 caracteres.
- El precio debe ser mayor que 0.
- El stock no puede ser negativo.

### ProductUpdate

Se utiliza para actualizar un producto existente.

Incluye:

- id
- name
- price
- stock

### ProductResponse

Es el modelo que devuelve la API cuando se consulta un producto.

## Endpoints

### Obtener todos los productos

```http
GET /products
```

También se puede filtrar por stock:

```http
GET /products?min_stock=5
```

### Obtener un producto por ID

```http
GET /products/{product_id}
```

Ejemplo:

```http
GET /products/1
```

### Crear un producto

```http
POST /products
```

Ejemplo:

```json
{
  "name": "Mouse",
  "price": 50,
  "stock": 10
}
```

### Actualizar un producto

```http
PUT /products/{product_id}
```

Ejemplo:

```json
{
  "id": 1,
  "name": "Mouse Gamer",
  "price": 80,
  "stock": 15
}
```

### Eliminar un producto

```http
DELETE /products/{product_id}
```

## Códigos de respuesta

- 200: operación realizada correctamente.
- 201: producto creado correctamente.
- 204: producto eliminado correctamente.
- 404: producto no encontrado.
- 422: error en los datos enviados.

