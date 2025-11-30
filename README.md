# 🦅 **Descripción del Reto: "Infiltración al Servidor Raptor"**

### 📜 Resumen del Reto

Los estudiantes actuarán como auditores de seguridad (pentesters) en la red local. Su misión es localizar un servidor furtivo, identificar sus servicios ocultos y vulnerar su acceso remoto utilizando herramientas de enumeración y fuerza bruta (**Nmap** y **Hydra**).

### 🎯 Objetivo del Escenario

El **Servidor Raptor** ha sido endurecido por el administrador para resistir ataques básicos. Sus características de defensa son:

1.  **Sigilo:** El servicio SSH no se encuentra en el puerto estándar (`22`).
    
2.  **Defensa Activa:** El servidor cuenta con un sistema de prevención de intrusos (IPS/Fail2Ban) que **bloqueará tu dirección IP por 10 minutos** si detecta múltiples intentos de contraseña fallidos en poco tiempo.
    
3.  **Señuelos:** Existen puertos y usuarios falsos diseñados para hacer perder tiempo al atacante.
    

**La condición de victoria es:**

1.  Encontrar el puerto SSH real.
    
2.  Obtener las credenciales correctas (Usuario y Contraseña) sin ser bloqueado.
    
3.  Acceder vía SSH y **crear un archivo de texto** en el directorio raíz (`~`) con tu nombre completo como evidencia.
    
4.  **Reiniciar el servidor** para expulsar a cualquier otro rival que esté intentando entrar.
    

----------

### 🕵️ Información de Inteligencia (Pistas)

-   **Objetivo:** Un servidor activo dentro del rango de red `192.168.X.X` (Escanea tu red local).
    
-   **Posibles Usuarios:** Inteligencia ha interceptado una lista de posibles usuarios activos:
    
    -   `root`, `admin`, `titulacion`, `test`, `usuario`.
        
    -   _Nota: Algunos usuarios pueden ser señuelos o estar deshabilitados._
        
-   **Contraseña:** Se sabe que la contraseña es débil y se encuentra dentro del **Diccionario del Reto** proporcionado por el profesor.
    

----------

### 🛠️ Tareas a Completar (Paso a Paso)

1.  Descubrimiento de Host (Reconocimiento):
    
    Utiliza nmap para escanear la red y encontrar la dirección IP del Servidor Raptor.
    
2.  Escaneo de Puertos y Servicios:
    
    Realiza un escaneo completo de puertos (-p-) para encontrar dónde está escondido el servicio SSH.
    
    -   _Cuidado: No te distraigas con los puertos trampa._
        
3.  Ataque de Fuerza Bruta (Explotación):
    
    Utiliza Hydra para descubrir la contraseña válida.
    
    -   **⚠️ IMPORTANTE:** Debido al sistema de bloqueo, debes ser preciso. Configura tu ataque cuidadosamente o usa un diccionario reducido y tiempos de espera adecuados para no ser baneado por el firewall.
        
4.  Evidencia de Compromiso (Post-Explotación):
    
    Conéctate al servidor y ejecuta el siguiente comando (sustituyendo con tus datos):
    

    
    ```Bash
    echo "HACKED BY: [TU NOMBRE COMPLETO]" > ~/pwned.txt
    
    ```
    
5.  Finalizar el Reto (King of the Hill):
    
    Una vez creada la evidencia, ejecuta:
    
    
    
    ```Bash
    sudo reboot
    
    ```
    
    Esto finalizará el reto, cortará las conexiones de tus compañeros y validará tu victoria.
    

----------

### ⚠️ Reglas de Enfrentamiento

-   Si tu IP es bloqueada, deberás esperar **10 minutos** para volver a intentarlo.
    
-   No está permitido realizar ataques de Denegación de Servicio (DoS).
    
-   Gana el primero que logre reiniciar el servidor dejando su archivo de evidencia guardado.
