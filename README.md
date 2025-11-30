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
💀 **OPERACIÓN RAPTOR: La Ruleta Rusa Digital**
  **DESCRIPCIÓN:**

⚠️ **ALERTA DE INTELIGENCIA** ⚠️

He interceptado 31 paquetes de datos distintos (`diccionario_usuarios_X.txt` y `diccionario_passwords_X.txt`). Cada uno de ustedes recibirá un par de archivos **ÚNICO y DIFERENTE** al de sus compañeros.

Aquí es donde empieza el juego mental:

🎲 **El Factor Suerte (Tu Peor Enemigo):** Los archivos han sido desordenados aleatoriamente.

-   En el **Archivo #7**, la contraseña correcta podría estar en la **línea 3**. (Nivel: Fácil)
    
-   En el **Archivo #24**, la contraseña correcta podría estar en la **línea 98**. (Nivel: Pesadilla)
    

🚫 **La Trampa del Servidor:** El servidor Raptor tiene un sistema de defensa activo (**Fail2Ban**) que **bloqueará tu IP por 1 HORA si fallas 5 veces seguidas**.

Si te tocó un archivo con la contraseña al final y lanzas tu ataque a máxima velocidad... **serás eliminado automáticamente antes de encontrar la clave.**

💀 **REGLAS DE SUPERVIVENCIA:**

1.  **NO COPIES A TU VECINO:** Su archivo es diferente. Si él entra en 10 segundos, es porque tuvo suerte. Si tú intentas ir a su velocidad con un archivo difícil, el Firewall te detectará.
    
2.  **Velocidad vs. Estrategia:** ¿Te arriesgarás a lanzar Hydra rápido confiando en tu suerte? ¿O configurarás retardos para ir lento y seguro, aunque te tome más tiempo?
    
3.  **Analiza tu munición:** Antes de disparar, abre tus archivos de texto. A veces el ojo humano es más rápido que la fuerza bruta.
    

**Tu misión:** Identificar cuál de las 31 combinaciones te tocó, vulnerar el puerto XXXX y dejar tu marca antes de que el servidor te expulse.

> _"No es solo hackear. Es saber si hoy la suerte está de tu lado."_
> _"Tomen un archivo al azar, no hay devoluciones"_


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