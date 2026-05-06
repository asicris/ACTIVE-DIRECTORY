# Contribuír a este Proxecto

Gracias por estar interesado en contribuír a esta documentación sobre Active Directory!

## Configuración Local

### Requisitos Previos
- Python 3.8 ou superior
- pip (administrador de paquetes de Python)
- Git

### Instalación

1. **Clona o repositorio:**
```bash
git clone https://github.com/asicris/ACTIVE-DIRECTORY.git
cd ACTIVE-DIRECTORY
```

2. **Crea un entorno virtual (opcional pero recomendado):**
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

3. **Instala as dependencias:**
```bash
pip install -r requirements.txt
```

## Traballo Local

### Compilar e Visualizar Localmente

Para ver a documentación no teu navegador mentres traballas:

```bash
mkdocs serve
```

Despois accede a `http://localhost:8000` no teu navegador.

### Compilar o Site

Para xenerar o site estático:

```bash
mkdocs build
```

Isto crea un directorio `site/` coa documentación compilada.

## Estrutura do Proxecto

```
.
├── docs/                    # Documentación en Markdown
│   ├── index.md            # Páxina de inicio
│   ├── 00_*.md             # Documentos numerados
│   └── images/             # Imaxes
├── mkdocs.yml              # Configuración de MkDocs
├── requirements.txt        # Dependencias de Python
├── README.md               # Este arquivo
└── .github/
    └── workflows/
        └── deploy.yml      # Despliegue automático en GitHub Pages
```

## Editando Documentación

### Crear un Novo Documento

1. Crea un novo arquivo `.md` en `docs/` cun nome descritivo
2. Engade o documento ao `mkdocs.yml` en la sección de navegación (nav)
3. Usa o formato Markdown estándar

### Guía de Estilo

- **Idioma:** Galego
- **Encabezados:** Usa `#` para títulos principais, `##`, `###`, etc. para subseccións
- **Énfase:** Usa `**negra**` e `*itálica*`
- **Código:** Usa `` `código en liña` `` e bloques ` ``` ` para código multilínea
- **Ligas:** `[texto](arquivo.md)` para arquivos locais, `[texto](https://url)` para URLs externas
- **Listas:** Usa `-` ou `*` para listas sen orden, `1.` para listas ordenadas

### Exemplo de Documento

```markdown
# Título do Documento

## Subsección 1

Descrición con **énfase**.

### Subsección 1.1

Código en liña: `comando`.

Bloque de código:
\`\`\`bash
#!/bin/bash
echo "Hola"
\`\`\`

## Subsección 2

- Elemento 1
- Elemento 2
  - Subelemento 2.1

## Ligas

- [Outro documento](outro_documento.md)
- [Sitio externo](https://exemplo.com)
```

## Enviar Cambios

1. **Crea unha rama:**
```bash
git checkout -b feature/tu-rama
```

2. **Fai os cambios e comproba que se ven ben:**
```bash
mkdocs serve
```

3. **Commit dos cambios:**
```bash
git add .
git commit -m "Descripción clara dos cambios"
```

4. **Sube a rama:**
```bash
git push origin feature/tu-rama
```

5. **Abre un Pull Request** en GitHub

## Despliegue

O despliegue en GitHub Pages é automático cando se fai push á rama `main` ou `master`. O fluxo de traballo en `.github/workflows/deploy.yml` encárgase de:

1. Instalar as dependencias
2. Compilar a documentación con MkDocs
3. Desplegar o sitio en GitHub Pages

## Preguntas?

Se tes preguntas ou necesitas axuda, abre unha **issue** no repositorio.

---

Grazas pola túa contribución!
