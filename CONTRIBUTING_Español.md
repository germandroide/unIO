Licensed under the Creative Commons Attribution-NoDerivatives 4.0 International License (CC BY-ND 4.0).
# Guía de Contribución para el Proyecto unIO

¡Gracias por tu interés en contribuir al desarrollo del léxico de unIO! Tu participación es valiosa para hacer crecer esta Lengua Auxiliar Internacional inclusiva.

Esta guía te ayudará a entender cómo proponer nuevo vocabulario (raíces y derivados) de manera que sea coherente con los principios y la estructura de unIO.

## Antes de Empezar: Conoce unIO

Es fundamental que comprendas los principios básicos de unIO antes de proponer nuevo léxico. Por favor, asegúrate de haber:

1.  **Leído y comprendido la [Especificación de unIO V1.0](./unio_specification_v1.0.pdf)**. Presta especial atención a:
    *   **Sección 2: Fonología y Ortografía (V5.0):** El alfabeto de 20 letras, la correspondencia unívoca letra-sonido (z=/θ/, x=/tʃ/, j=/j/, r=/ɾ/, g=/g/), y la acentuación en la penúltima sílaba.
    *   **Sección 4: Morfología:** La invariabilidad de las raíces, el sistema regular de afijos (-s, -e, -ad, -it, -ika, -abli, mal-, re-, etc.).
    *   **Sección 1 y 5: Principios y Filosofía Léxica:** Simplicidad, regularidad, neutralidad y el enfoque mixto (a priori/internacional adaptado), **dando prioridad siempre a la derivación/composición interna antes de crear nuevas raíces**.
2.  **Explorado el Léxico Existente:** Revisa tanto la Especificación V1.0 como el contenido actual de la carpeta [`lexicon/`](./lexicon) en este repositorio para evitar proponer palabras que ya existen o conceptos que se pueden formar fácilmente con derivación.

## Cómo Proponer Nuevo Léxico (Flujo de Trabajo)

Utilizamos el flujo estándar de GitHub con Pull Requests (PRs):

1.  **Fork:** Haz un "Fork" de este repositorio a tu propia cuenta de GitHub.
2.  **Clonar (Opcional, para trabajo local):** Clona tu fork a tu máquina local si prefieres trabajar allí: `git clone https://github.com/TU_USUARIO/TU_REPOSITORIO_FORK.git`
3.  **Crear una Rama (Branch):** Crea una nueva rama descriptiva para tus cambios desde la rama `main`. Ej: `git checkout -b anadir-vocabulario-medico` o `feature/medical-terms`.
4.  **Añadir/Editar Entradas Léxicas:**
    *   Navega a la carpeta `lexicon/` y elige la subcarpeta temática adecuada (ej. `general/`, `scientific/`, `medical/`). Si crees que se necesita una nueva categoría, puedes proponerla creando una nueva carpeta.
    *   Edita el archivo `.yaml` existente en esa carpeta (o crea uno si es una categoría nueva) para añadir tu(s) nueva(s) entrada(s) léxica(s). **DEBES seguir estrictamente el formato YAML especificado abajo.**
5.  **Confirmar Cambios (Commit):** Guarda tus cambios con un mensaje claro y conciso. Ej: `git add lexicon/medical/words.yaml && git commit -m "Add root 'kor' for heart and related terms"`.
6.  **Empujar Cambios (Push):** Sube tu rama a tu fork en GitHub: `git push origin nombre-de-tu-rama`.
7.  **Crear un Pull Request (PR):** Ve a tu fork en GitHub. Verás un botón para crear un "Pull Request" desde tu nueva rama hacia la rama `main` del repositorio original de unIO.
    *   **Describe tu PR:** En la descripción del PR, explica claramente qué palabras has añadido, por qué son necesarias, y cómo respetan los principios fonológicos y morfológicos de unIO. Si usaste IA, menciona brevemente cómo.

## Formato Obligatorio para Entradas Léxicas (YAML)

Todas las entradas nuevas deben añadirse a los archivos `.yaml` dentro de las carpetas de `lexicon/` usando la siguiente estructura por cada palabra/raíz:

```yaml
- root: [la_raiz_unio]         # La palabra raíz en unIO (obligatorio)
  pos: [tipo_gramatical]       # Parte de la oración (n, v, adj, adv, prep, conj, part, interj) (obligatorio)
  definitions:
    es: "[definición_es]"     # Definición concisa en español (obligatorio)
    # en: "[definición_en]"   # (Opcional) Definición en inglés
    # unio: "[definición_unio]" # (Opcional) Definición corta usando unIO simple
  etymology: "[origen_logica]"  # Origen etimológico o razón lógica de la forma (obligatorio - ej. "Lat. corpus", "Comp.: labor+lok", "A priori, similar a X", "Adapt. Intl.")
  plural: "[forma_plural]"      # Solo para nombres (n), si aplica (ej. doms)
  examples:                    # Al menos un ejemplo (recomendado)
    - unio: "[frase_ejemplo_unio]"
      es: "[traduccion_ejemplo_es]"
    # - unio: "[otro_ejemplo_unio]"
    #   es: "[otro_ejemplo_es]"
  derivatives:                 # Lista opcional de derivados directos ya definidos o propuestos aquí
    - root: "[raiz_derivada]"
      pos: "[pos_derivada]"
      definition_es: "[def_derivada_es]"
  tags: [tag1, tag2, ...]      # Etiquetas opcionales para categorización (ej. basic, science, medical, abstract, concrete)
