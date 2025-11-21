# Parcial – CI/CD

Este proyecto implementa un pipeline de Integración Continua (CI) utilizando **GitHub Actions** y soporte para ejecución local mediante **nektos/act**.  
Incluye:

- Linter obligatorio (Checkstyle para Java).
- Pruebas automatizadas con JUnit.
- Reporte de cobertura con JaCoCo.
- Validación de umbral mínimo de cobertura.
- Build del proyecto.
- Ejecución local con act para simular GitHub Actions.

---

## 🚀 ¿Cómo funciona el pipeline?

El workflow principal está ubicado en:
```.github/workflows/ci-quality.yml```

Este pipeline se ejecuta automáticamente en:

- Cada `push` a la rama `main`
- Cada `pull_request` contra `main`

### Etapas del pipeline

1. **Checkout del repositorio**
2. **Linter (Checkstyle)**  
   Valida que el código Java cumpla reglas básicas de estilo.
3. **Pruebas automatizadas (JUnit)**
4. **Reporte de cobertura (JaCoCo)**
5. **Validación del umbral mínimo de cobertura**  
   El pipeline fallará si es inferior al valor configurado (por ejemplo ≥ 90%).
6. **Build del proyecto**
7. **Construcción y validación con Docker** (si aplica)

Si cualquier etapa falla, el pipeline se detiene inmediatamente.

---

## 🛠️ Requisitos del proyecto

- Java 17  
- Maven 3.9.x  
- Docker (solo si se usa act o el job de Docker)

---

## 📊 Linter utilizado

El proyecto utiliza:

Checkstyle (via Super-Linter)
La configuración del linter se encuentra en:
```.github/linters/checkstyle.xml```


---

## 🧪 Ejecución local con act

Este proyecto se puede ejecutar localmente mediante **nektos/act**, que permite simular GitHub Actions.

### ¿Qué es act?

**Act** es una herramienta que ejecuta localmente los workflows de GitHub Actions utilizando contenedores Docker.  
Permite probar el pipeline sin necesidad de hacer push al repositorio.

### Requisitos

- Docker instalado y corriendo
- act instalado (`brew install act`, `choco install act-cli`, o binario directo)

### Comando para ejecutar el pipeline completo
```act push```

### Para ejecutar solo el job del linter:
```act -j lint```


### Para ejecutar pruebas y cobertura:
```act -j test```