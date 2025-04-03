# 📂 AGREGAR "ABRIR EN CMD" AL MENÚ CONTEXTUAL EN WINDOWS

## 🚀 PASOS RÁPIDOS

1. Abre el Editor del Registro de Windows:
   - Presiona `Win + R`, escribe `regedit` y presiona `Enter`.

2. Ve a la siguiente ruta en el registro:
   ```reg
   HKEY_CLASSES_ROOT\Directory\Background\shell

3. Crea una nueva clave llamada **Abrir en CMD**.

4. Dentro de **Abrir en CMD**, crea otra clave llamada **command**.

5. En **command**, edita el valor (Predeterminado) e ingresa:
   ```reg
   cmd.exe /k cd %V