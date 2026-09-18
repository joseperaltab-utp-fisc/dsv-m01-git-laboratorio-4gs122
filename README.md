# DSV — Laboratorio de Control de Versiones · Grupo 4GS122

Repositorio base del **Laboratorio 1** del Módulo I de la asignatura
**Desarrollo de Software V** (8400), Licenciatura en Desarrollo y Gestión de
Software — Universidad Tecnológica de Panamá, Centro Regional de Veraguas.

Contiene un mini-sitio: un índice con el portafolio del curso y una página de
perfil por estudiante. Cada participante agrega la suya trabajando en su propia
rama y proponiendo la integración mediante un Pull Request.

---

## Estructura del proyecto

```text
dsv-m01-git-laboratorio/
├── README.md
├── .gitignore
└── site/
    ├── index.html                              Índice del portafolio
    ├── assets/
    │   ├── css/
    │   │   ├── style.css                       Estilos del índice (en uso)
    │   │   └── style-paleta-organizacional.css Variante con la paleta institucional
    │   └── img/
    │       ├── logo-utp.svg
    │       └── logo-fisc.svg
    └── alumnos/
        ├── apellidos-nombre/                   PLANTILLA — no la edites, cópiala
        │   ├── about-apellidos-nombre.html
        │   └── assets/
        │       ├── css/
        │       │   └── about-apellidos-nombre.css
        │       └── img/
        │           ├── foto-apellidos-nombre-160.webp
        │           ├── foto-apellidos-nombre-320.webp
        │           ├── foto-apellidos-nombre-480.webp
        │           └── foto-apellidos-nombre-640.webp
        └── gomez-valeria/                      EJEMPLO resuelto — consúltalo
            ├── about-gomez-valeria.html
            └── assets/
                ├── css/
                │   └── about-gomez-valeria.css
                └── img/
                    └── foto-gomez-valeria-{160,320,480,640}.webp
```

### Dos carpetas que no debes tocar

- **`apellidos-nombre/`** es la plantilla. Cópiala completa y renómbrala con tus
  datos; no la edites ni la borres, porque la usan los demás.
- **`gomez-valeria/`** es un ejemplo ya resuelto. Míralo cuando tengas dudas
  sobre cómo debe quedar el resultado.

### Sobre los dos archivos CSS del índice

`site/index.html` enlaza `style.css`, que usa una paleta azul.
`style-paleta-organizacional.css` es la misma hoja adaptada a los colores
institucionales. Ambas definen las mismas variables, así que se pueden
intercambiar cambiando una sola línea en el `<head>` del índice.

---

## Cómo trabajar en este repositorio

El procedimiento completo, paso a paso, está en la guía del **Laboratorio 1**.
Este resumen sirve como referencia rápida una vez que ya la leíste.

```bash
# 1. Clonar
git clone https://github.com/joseperaltab-utp-fisc/dsv-m01-git-laboratorio-4gs122.git
cd dsv-m01-git-laboratorio-4gs122

# 2. Crear tu rama
git switch -c feature/perfil-apellidos-nombre

# 3. Copiar la plantilla y renombrarla con tus datos
#    (ver la guía del laboratorio para la lista exacta de archivos)

# 4. Confirmar por partes
git add site/alumnos/apellidos-nombre/
git commit -m "feat: agregar pagina de perfil de Apellidos Nombre"

git add site/index.html
git commit -m "feat: enlazar el perfil de Apellidos Nombre en el indice"

# 5. Publicar y abrir el Pull Request
git push -u origin feature/perfil-apellidos-nombre
```

### Convención de nombres de rama

`tipo/descripcion-en-minusculas-con-guiones`

| Regla | Correcto | Incorrecto |
| --- | --- | --- |
| Todo en minúsculas | `feature/perfil-perez-juan` | `Feature/PerfilPerezJuan` |
| Guiones, nunca espacios ni puntos | `feature/perfil-perez-juan` | `feature/perfil-juan.perez` |
| Sin tildes ni eñes | `fix/pagina-cirugia` | `fix/página-cirugía` |
| Con prefijo que declara el propósito | `docs/manual-usuario` | `manual-usuario` |

Prefijos del curso: `feature`, `fix`, `docs`, `hotfix`.

La barra no crea carpetas reales, pero GitHub agrupa visualmente las ramas por
prefijo, lo que facilita ordenar el trabajo del equipo.

### Convención de mensajes de commit

`tipo: descripción en imperativo, minúscula, sin punto final`

Tipos en uso: `feat`, `fix`, `style`, `docs`, `refactor`, `chore`.

---

## Dónde va tu enlace en el índice

Dentro de `site/index.html`, la lista de estudiantes empieza con un comentario
que marca el punto de inserción:

```html
<ol class="lista-estudiantes">
  <!-- INSERTA TU ENLACE AQUÍ, COMO PRIMER ELEMENTO DE LA LISTA -->
  <li>
    <a class="enlace-estudiante" href="./alumnos/gomez-valeria/about-gomez-valeria.html">
      Valeria Gómez
    </a>
  </li>
  ...
</ol>
```

**Inserta tu bloque `<li>` inmediatamente después de ese comentario, como primer
elemento de la lista.** No lo pongas al final ni en medio.

Esto es deliberado: al hacerlo todos en el mismo punto, se produce un conflicto
de fusión cuando el trabajo de dos personas se encuentra. Resolverlo forma parte
de los objetivos del laboratorio, y el criterio C3 de la asignatura lo evalúa.

---

## Recomendaciones para la fotografía de perfil

La plantilla usa `srcset` con cuatro tamaños para que la imagen se vea nítida en
cualquier pantalla. Debes generar los cuatro.

**Tamaños a exportar:** 160, 320, 480 y 640 píxeles de lado. La imagen se muestra
como un círculo de 160 px; los tamaños mayores cubren las pantallas de alta
densidad.

**Encuadre.** Parte de una imagen cuadrada (1:1) y deja aire alrededor del sujeto:

| Zona | Margen sugerido |
| --- | --- |
| Sobre el cabello | 8–12 % de la altura |
| A cada lado de la cabeza | 12–15 % |
| Hombros y pecho | 20–28 % |

La cara debe ocupar entre el 60 % y el 70 % del diámetro del círculo, centrada
ligeramente por encima del centro. Ese encuadre deja ver el polo y, si entra, el
logotipo bordado.

**Formato.** WebP con calidad 80, que es lo que espera la plantilla. Fondo neutro
y buena iluminación; evita texturas ruidosas.

**Nombres de archivo.** Respeta exactamente el patrón, porque el `srcset` de la
plantilla los busca por nombre:

```text
foto-apellidos-nombre-160.webp
foto-apellidos-nombre-320.webp
foto-apellidos-nombre-480.webp
foto-apellidos-nombre-640.webp
```

**HTML sugerido (con srcset)** 

```html
<!-- file: site/alumnos/apellidos-nombre/about-apellidos-nombre.html -->
<figure class="perfil">
  <img
    src="./assets/img/foto-apellidos-nombre-320.webp"
    srcset="
      ./assets/img/foto-apellidos-nombre-160.webp 160w,
      ./assets/img/foto-apellidos-nombre-320.webp 320w,
      ./assets/img/foto-apellidos-nombre-480.webp 480w,
      ./assets/img/foto-apellidos-nombre-640.webp 640w
    "
    />

```
---

## Archivos ignorados

El `.gitignore` de la raíz excluye la configuración del editor, los espacios de
trabajo de VS Code y los archivos que genera el sistema operativo. No lo edites
para agregar tus propios archivos: si algo tuyo no debe versionarse, consúltalo
primero.

---

## Licencia y uso

Material docente de la asignatura Desarrollo de Software V.
Las fotografías de perfil pertenecen a cada estudiante y se publican con su
consentimiento para uso académico dentro del curso.
