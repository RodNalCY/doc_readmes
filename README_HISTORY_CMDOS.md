## 🛠️ Activar el seguimiento de programas recientes en Windows

Sigue estos pasos para habilitar la opción de mostrar programas recientemente utilizados en el menú Inicio:

1. **Abrir el editor del registro**:
   - Presiona `Windows + R` para abrir el cuadro de diálogo **Ejecutar**.
   - También puedes ir al botón **Inicio** y buscar `"Ejecutar"`.
   - En el cuadro, escribe `regedit` y presiona **Enter**.

2. **Navegar a la clave del registro**:
   - En el Editor del Registro, dirígete a la siguiente ruta:

     ```
     HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced
     ```

3. **Modificar el valor**:
   - En el panel derecho, localiza la entrada llamada `Start_TrackProgs`.
   - Haz doble clic sobre ella.
   - Cambia el valor a `1` y haz clic en **Aceptar**.

4. **Reiniciar el equipo**:
   - Para que los cambios surtan efecto, reinicia tu PC.
---

## 📜 Ver historial de comandos ejecutados

Para consultar el historial de comandos en tu terminal, puedes usar el siguiente comando en la ruta de tu proyecto:

```bash
D:\laragon\www\crm_elsol> doskey /history