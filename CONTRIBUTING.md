# Cómo contribuir a los proyectos de b24cloud

¡Gracias por tu interés en contribuir a los proyectos de la organización **b24cloud**! Este documento describe cómo puedes participar y colaborar en nuestros repositorios.

---

## 📌 Antes de empezar

1. **Lee el [Código de Conducta](CODE_OF_CONDUCT.md)**. Esperamos que todos los contribuyentes y colaboradores respeten estos principios.
2. **Revisa los temas abiertos** (issues y pull requests) para evitar duplicar trabajo.
3. **Asegúrate de que tu contribución se alinee con los objetivos del proyecto**.

---

## 🔒 Visibilidad de repositorios

**Todos los repositorios nuevos deben crearse como `private` por defecto.**

- Nunca crear un repositorio con visibilidad pública sin autorización explícita del mantenedor.
- Al crear un repositorio mediante herramienta, API o agente, usar siempre `private: true`.
- Cualquier excepción debe estar documentada y aprobada expresamente.

---

## 🛠️ Cómo contribuir

### 🔹 Reportar problemas (Issues)

Si encuentras un **bug** o tienes una **solicitud de mejora**, abre un nuevo issue en el repositorio correspondiente:

1. Ve a la pestaña **Issues** del repositorio.
2. Haz clic en **New Issue**.
3. Selecciona el **template** adecuado (bug report, feature request, etc.).
4. Rellena los detalles solicitados y envía el issue.

> **Nota:** Si no hay un template específico, describe el problema de manera clara y concisa, incluyendo:
> - Pasos para reproducir el error.
> - Comportamiento esperado vs. comportamiento real.
> - Entorno (sistema operativo, versión de software, etc.).

---

### 🔹 Proponer cambios (Pull Requests)

Si quieres contribuir con código, sigue estos pasos:

1. **Haz un fork** del repositorio.
2. **Clona tu fork** en tu máquina local:
   ```bash
   git clone https://github.com/tu-usuario/nombre-repositorio.git
   cd nombre-repositorio
   ```
3. **Crea una rama** para tu cambio:
   ```bash
   git checkout -b nombre-de-tu-rama
   ```
4. **Realiza tus cambios** y haz commits con mensajes descriptivos:
   ```bash
   git add .
   git commit -m "Descripción clara de los cambios"
   ```
5. **Empuja los cambios** a tu fork:
   ```bash
   git push origin nombre-de-tu-rama
   ```
6. **Abre un Pull Request (PR)** desde tu fork al repositorio original:
   - Ve a **Pull Requests** > **New Pull Request**.
   - Selecciona tu rama y compara los cambios.
   - Rellena el template del PR y envíalo.

> **Requisitos para el PR:**
> - Debe pasar todas las pruebas automatizadas (CI/CD).
> - Debe incluir pruebas unitarias si aplica.
> - Debe seguir el estilo de código del proyecto.
> - Debe tener una descripción clara y justificación de los cambios.

---

### 🔹 Mejoras de documentación

Si encuentras errores en la documentación o quieres mejorarla:

1. Haz un fork del repositorio.
2. Edita los archivos de documentación (generalmente en `README.md`, `docs/`, o archivos `.md` en el repositorio).
3. Sigue los pasos anteriores para enviar un PR.

---

## 📝 Estilo de commits

Mantén tus commits **claros y descriptivos**. Usa el formato:

```
<tipo>(<alcance>): <descripción>

<cuerpo opcional>
```

Ejemplos:

- `feat(api): añade endpoint para obtener usuarios`
- `fix(ui): corrige visualización de botones en móvil`
- `docs(readme): actualiza guía de instalación`
- `chore(deps): actualiza dependencias a versiones estables`

---

## 🔍 Revisión de código

Todos los PRs pasan por un proceso de revisión:
- Un **miembro del equipo** revisará tu PR.
- Si hay comentarios o cambios solicitados, debes actualizar tu PR.
- Una vez aprobado, un mantenedor hará merge del PR.

---

## 🌟 Reconocimiento

¡Todas las contribuciones son bienvenidas! Los contribuyentes más activos pueden ser reconocidos como **colaboradores oficiales** de la organización.

---

## 🆘 ¿Necesitas ayuda?

Si tienes dudas o necesitas orientación:
- Revisa los **Issues** abiertos en el repositorio.
- Contacta al equipo en [soporte@b24cloud.com](mailto:soporte@b24cloud.com).
- Únete a nuestro [canal de Discord](https://discord.gg/b24cloud) (si aplica).

---

## 📜 Licencia

Al contribuir, aceptas que tu código se publique bajo la **licencia del proyecto** (generalmente MIT o Apache 2.0).

---

¡Gracias por ser parte de la comunidad **b24cloud**!
