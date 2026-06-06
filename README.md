# MCP Chat

MCP Chat es una aplicación de línea de comandos que permite chatear de forma interactiva con modelos de IA a través de la API de Anthropic. La aplicación soporta recuperación de documentos, comandos con prefijo y extensiones de herramientas mediante la arquitectura MCP (Model Control Protocol).

## Requisitos previos

- Python 3.9+
- API Key de Anthropic

## Configuración

### Paso 1: Configurar las variables de entorno

1. Crea o edita el archivo `.env` en la raíz del proyecto y verifica que las siguientes variables estén correctamente configuradas:

```
ANTHROPIC_API_KEY=""  # Ingresa tu clave secreta de Anthropic
```

### Paso 2: Instalar dependencias

#### Opción 1: Configuración con uv (Recomendado)

[uv](https://github.com/astral-sh/uv) es un instalador y resolvedor de paquetes Python muy rápido.

1. Instala uv si aún no lo tienes:

```bash
pip install uv
```

2. Crea y activa un entorno virtual:

```bash
uv venv
source .venv/bin/activate  # En Windows: .venv\Scripts\activate
```

3. Instala las dependencias:

```bash
uv pip install -e .
```

4. Ejecuta el proyecto:

```bash
uv run main.py
```

#### Opción 2: Configuración sin uv

1. Crea y activa un entorno virtual:

```bash
python -m venv .venv
source .venv/bin/activate  # En Windows: .venv\Scripts\activate
```

2. Instala las dependencias:

```bash
pip install anthropic python-dotenv prompt-toolkit "mcp[cli]==1.8.0"
```

3. Ejecuta el proyecto:

```bash
python main.py
```

## Uso

### Interacción básica

Escribe tu mensaje y presiona Enter para chatear con el modelo.

### Recuperación de documentos

Usa el símbolo @ seguido del ID del documento para incluir su contenido en tu consulta:

```
> Cuéntame sobre @deposicion.md
```

### Comandos

Usa el prefijo / para ejecutar comandos definidos en el servidor MCP:

```
> /resumir deposicion.md
```

Los comandos se autocompletarán al presionar Tab.

## Desarrollo

### Agregar nuevos documentos

Edita el archivo `mcp_server.py` para agregar nuevos documentos al diccionario `docs`.

### Implementar funcionalidades MCP

Para implementar completamente las funcionalidades MCP:

1. Completa los TODOs en `mcp_server.py`
2. Implementa la funcionalidad faltante en `mcp_client.py`

### Linting y verificación de tipos

No hay linting ni verificación de tipos implementados.
