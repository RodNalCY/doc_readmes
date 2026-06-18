## Configuración de Servidor de Pruebas en Red Local (LAN)

Para probar la aplicación desde otros dispositivos (como móviles o tablets) conectados a la misma red local (LAN), sigue detalladamente estos pasos:

### 1. Definir una Dirección IP Estática
Para evitar que tu dirección IP cambie y los dispositivos pierdan conexión, configura una IP estática en los ajustes de red de tu equipo:
- **En Windows**:
  1. Abre **Configuración** > **Red e Internet** > **Propiedades** de tu red activa (Wi-Fi o Ethernet).
  2. En **Asignación de IP**, haz clic en **Editar**.
  3. Cambia a **Manual**, activa **IPv4** e ingresa:
     - **IP**: Tu dirección IP fija (ej. `192.168.100.170`).
     - **Máscara de subred**: Generalmente `255.255.255.0`.
     - **Puerta de enlace**: La IP de tu router (ej. `192.168.100.1`).
     - **DNS**: Puedes usar los de Google (`8.8.8.8` y `8.8.4.4`).

### 2. Desactivar/Activar el Firewall Temporalmente
Para pruebas locales rápidas, el Firewall de Windows podría bloquear el tráfico entrante a los puertos de desarrollo.
- **Desactivar**: Desactiva temporalmente el Firewall de Windows Defender en redes privadas.
- **Activar**: **[IMPORTANTE]** No olvides reactivar el Firewall una vez concluidas tus pruebas de red local para asegurar tu equipo.

### 3. Ejecutar el Servidor Backend (Laravel)
Dirígete a la consola de tu backend en Laravel y arranca el servidor vinculándolo a la interfaz general `0.0.0.0` para que acepte conexiones de toda la red:
```bash
php artisan serve --host=0.0.0.0 --port=8000
```

### 4. Configurar el Environment en Angular
Modifica tu archivo `src/environments/environments.ts` para que apunte a la IP de tu servidor backend en lugar de `localhost`:
```typescript
export const environments = {
  // ...
  app_urls: {
    api: 'http://192.168.100.170:8000/api', // IP estática configurada en el paso 1
  },
  // ...
};
```

#### 4.1. Configurar el Environment en Vue.js
En caso de estar configurando el frontend de Vue.js, define en el archivo `.env` la ruta de tu API backend usando tu dirección IP estática:
```env
VITE_API_URL=http://192.168.100.170/api/
VITE_API_URL_IMAGE=http://192.168.100.170:8000/
```

### 5. Ejecutar el Servidor Frontend (Angular)
Inicia tu aplicación Angular vinculándola también al host de red local `0.0.0.0` (por defecto se habilitará en el puerto `4200`):
```bash
npx ng serve --host 0.0.0.0
```

#### 5.1. Ejecutar el Servidor Frontend (Vue.js)
En caso de usar Vue.js, ejecuta el siguiente comando para levantar el servidor en el puerto `3000` y permitir el acceso en la red local:
```bash
npx vite --host 0.0.0.0 --port 3000
```

### 6. Conexión desde otros Dispositivos
1. Asegúrate de que el otro dispositivo (móvil, tablet u otra PC) esté en la **misma red Wi-Fi/local** que tu computadora.
2. Abre el navegador del dispositivo e ingresa la dirección IP de tu frontend y su respectivo puerto según el framework:
   - **Para Angular**:
     ```
     http://192.168.100.170:4200/
     ```
   - **Para Vue.js**:
     ```
     http://192.168.100.170:3000/
     ```

