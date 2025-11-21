# RESPUESTAS – Parcial de Calidad de Software Avanzado

## Parte 1 – Estrategia

### 1. Diferencia entre CI y CD

**Integración Continua (CI)**  
La CI consiste en revisar automáticamente el proyecto cada vez que alguien sube un cambio. Esto sirve para detectar errores rápido, como problemas de estilo, fallas en pruebas o cosas que podrían afectar el funcionamiento. La idea es mantener el proyecto en buen estado todo el tiempo.

**Despliegue Continuo (CD)**  
El CD se encarga de que el proyecto esté listo para usarse después de que pasa todas las revisiones. Esto incluye prepararlo, empaquetarlo y dejarlo listo para publicar. En algunos casos incluso se puede mandar a producción automáticamente. Su objetivo es que lo que está en el repositorio siempre pueda entregarse sin problemas.

---

### 2. Lenguaje, linter y herramienta de cobertura

- **Lenguaje:** Java  
  Es estable, fácil de integrar con pruebas y se usa ampliamente en cursos y proyectos.

- **Linter:** Checkstyle  
  Sirve para revisar que el código esté ordenado y siga reglas básicas. Ayuda a mantener un estilo consistente.

- **Cobertura:** JaCoCo  
  Permite saber qué partes del código están cubiertas por pruebas. Funciona bien con Maven y con JUnit.

---

### 3. Umbral mínimo de cobertura

El proyecto usa un mínimo de **90%** de cobertura.  
Este porcentaje ayuda a asegurar que casi todo el código esté probado y que el proyecto sea más confiable.

---

## Parte 2 – Workflow CI/CD

El archivo `.github/workflows/ci-quality.yml` ejecuta:

- Revisión del código con el linter  
- Pruebas automatizadas  
- Validación de cobertura  
- Construcción del proyecto  

Si algo falla, el pipeline se detiene inmediatamente para evitar errores más grandes.

---

## Parte 3 – Uso de nektos/act

**¿Qué es act?**  
Act permite ejecutar los workflows de GitHub Actions directamente en la computadora. Esto ayuda a probar el pipeline sin necesidad de subir cambios al repositorio cada vez.

**Requisitos:**  
- Docker  
- Act instalado  

**Comando para ejecutar todo el pipeline:**
```act push```


---

## Parte 4 – Validación y logs

### ¿Cómo identificar fallos del linter?

Cuando el linter detecta un problema, en los mensajes aparece algo como “error”, “falló” o que una regla no se cumplió.  
Básicamente, si ves que el linter muestra algún mensaje con error, significa que hay algo en el estilo del código que debe corregirse.

### ¿Cómo identificar fallos en las pruebas?

Si una prueba falla, los mensajes muestran palabras como “failure”, “error” o indican cuántas pruebas fallaron.  
Si aparece aunque sea una prueba fallida, significa que el pipeline no puede continuar.

### ¿Cómo identificar fallos de cobertura?

Cuando la cobertura es menor al porcentaje mínimo, aparece un mensaje avisando que el porcentaje no es suficiente.  
También se muestra cuánto fue el porcentaje real. Si está por debajo del valor esperado, el pipeline falla.

### Runs fallidos y exitosos

- Un run fallido muestra errores, advertencias o porcentajes bajos.  
- Un run exitoso muestra mensajes de éxito y que todas las etapas se completaron correctamente.

---

## Parte 5 – IA y Ética

### Métodos para detectar código generado por IA

1. **Analizar la forma en la que está escrito el código**  
   Muchas IAs escriben de forma muy ordenada y repetitiva. Cuando un código cambia mucho de estilo o parece demasiado perfecto, puede levantar sospechas.

2. **Comparar el estilo del estudiante con el del código**  
   Si el código no se parece al estilo de la persona (por cómo escribe o cómo estructura las cosas), se puede detectar que quizá no fue escrito por ella.

---

### Por qué no se puede asegurar al 100% el uso de IA

No existe una forma totalmente segura de saber si algo fue escrito por una persona o por una IA.  
Las herramientas solo pueden hacer estimaciones, porque tanto humanos como IA pueden imitarse entre sí. Por eso, no se puede garantizar con certeza.

---

### Políticas razonables para el uso de IA

- Permitir usar IA para aprender o aclarar dudas.  
- No permitir que la IA escriba el código que se entregará como trabajo.  
- Solicitar al estudiante que explique su código para demostrar que entiende lo que hizo.  
- Permitir usar IA en documentación si se menciona claramente que se utilizó.

---

