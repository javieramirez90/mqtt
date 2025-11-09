# Guión Detallado del Video - MQTT Equipo 08

**Duración total:** 10-15 minutos
**Formato:** Video continuo sin cortes

---

## 📋 CHECKLIST PRE-GRABACIÓN

### Preparación Técnica
- [ ] HiveMQ Cloud configurado y funcionando
- [ ] Todos tienen las credenciales en `config.py`
- [ ] `requirements.txt` instalado en todos los equipos
- [ ] Código probado y funcionando correctamente
- [ ] Apps móviles instaladas y configuradas
- [ ] Presentación de diapositivas lista

### Preparación del Video
- [ ] Buena iluminación para las cámaras
- [ ] Micrófono funcionando correctamente
- [ ] Software de grabación de pantalla listo
- [ ] Todos saben sus líneas y timing
- [ ] Hacer prueba completa antes de grabar

---

## 🎬 SECCIÓN 1: INTRODUCCIÓN (2 minutos)

### Toma 1: Presentación del Equipo
**[CÁMARA ABIERTA - TODOS VISIBLES EN PANTALLA]**

**Integrante 1:**
> "¡Buenas tardes! Bienvenidos a nuestra demostración del protocolo MQTT para Internet de las Cosas. Somos el Equipo 08."

**Integrante 2:**
> "Mi nombre es [NOMBRE COMPLETO], matrícula [MATRÍCULA]. En esta demostración estaré a cargo de mostrar el funcionamiento de los subscribers y explicar la teoría del protocolo MQTT."

**Integrante 3:**
> "Yo soy [NOMBRE COMPLETO], matrícula [MATRÍCULA]. Mi rol será coordinar la demostración práctica y mostrar la comunicación entre múltiples dispositivos en tiempo real."

**Integrante 1:**
> "Y yo soy [NOMBRE COMPLETO], matrícula [MATRÍCULA]. Me encargué de configurar el broker en HiveMQ Cloud y desarrollar los publishers para nuestra demostración."

**Integrante 1:**
> "Hoy vamos a demostrar cómo MQTT permite la comunicación eficiente entre dispositivos IoT usando un broker en la nube. Veremos publishers, subscribers y el broker trabajando juntos en tiempo real. ¡Comencemos!"

---

## 🎬 SECCIÓN 2: EXPLICACIÓN TEÓRICA (3-4 minutos)

### Toma 2: ¿Qué es MQTT?
**[COMPARTIR PANTALLA - PRESENTACIÓN]**

**Integrante 2:**
> "MQTT significa Message Queuing Telemetry Transport. Es un protocolo de mensajería ligero diseñado específicamente para Internet de las Cosas."

**[DIAPOSITIVA 1: Características de MQTT]**

**Integrante 2:**
> "Las características principales de MQTT son:
> - Es extremadamente ligero, usa muy poco ancho de banda
> - Diseñado para dispositivos con recursos limitados
> - Funciona bien en conexiones inestables o de baja latencia
> - Ideal para sensores, actuadores y dispositivos embebidos"

### Toma 3: Componentes del Sistema
**[DIAPOSITIVA 2: Arquitectura MQTT]**

**Integrante 1:**
> "La arquitectura de MQTT se basa en tres componentes principales:"

**Integrante 1:**
> "Primero, los **Publishers** o publicadores. Son dispositivos o aplicaciones que generan datos y los envían a temas específicos, que llamamos 'topics'. Por ejemplo, un sensor de temperatura que publica sus lecturas."

**Integrante 2:**
> "Segundo, los **Subscribers** o suscriptores. Son dispositivos que reciben mensajes de los topics a los que están suscritos. Pueden suscribirse a uno o múltiples topics según sus necesidades."

**Integrante 3:**
> "Y tercero, el **Broker** o intermediario. Es el corazón del sistema MQTT. Recibe todos los mensajes de los publishers y los distribuye a los subscribers correspondientes. En nuestra demo usamos HiveMQ Cloud como broker."

### Toma 4: Modelo Publish/Subscribe
**[DIAPOSITIVA 3: Diagrama de Flujo]**

**Integrante 2:**
> "El modelo publish/subscribe funciona así:"

**[Mostrar animación o diagrama]**

**Integrante 2:**
> "1. El publisher envía un mensaje a un topic específico, por ejemplo 'temperatura/cocina'
> 2. El broker recibe ese mensaje
> 3. El broker identifica qué subscribers están suscritos a ese topic
> 4. El broker envía el mensaje a todos los subscribers interesados"

**Integrante 1:**
> "Lo interesante es que publishers y subscribers no se conocen entre sí. Están completamente desacoplados, lo que permite escalabilidad y flexibilidad."

### Toma 5: Topics y QoS
**[DIAPOSITIVA 4: Topics y Quality of Service]**

**Integrante 3:**
> "Los topics en MQTT funcionan como canales de comunicación. Se organizan jerárquicamente usando el símbolo '/', por ejemplo: 'casa/cocina/temperatura'"

**Integrante 3:**
> "MQTT también ofrece tres niveles de Quality of Service o QoS:
> - QoS 0: El mensaje se envía una vez, sin confirmación
> - QoS 1: El mensaje se entrega al menos una vez (el que usaremos)
> - QoS 2: El mensaje se entrega exactamente una vez"

**Integrante 2:**
> "Para nuestra demostración usaremos QoS 1, que balancea confiabilidad y eficiencia. Ahora veamos cómo configuramos todo esto en la práctica."

---

## 🎬 SECCIÓN 3: CONFIGURACIÓN (2 minutos)

### Toma 6: Dashboard de HiveMQ
**[COMPARTIR PANTALLA - HiveMQ Dashboard]**

**Integrante 1:**
> "Para nuestra demostración utilizamos HiveMQ Cloud, que es una solución profesional de broker MQTT con un tier gratuito perfecto para pruebas y proyectos educativos."

**[Navegar por el dashboard]**

**Integrante 1:**
> "Aquí pueden ver nuestro cluster 'equipo08-mqtt'. Está alojado en la región US East y está activo, como indica el punto verde."

**[Mostrar la sección de Access Management]**

**Integrante 1:**
> "Configuramos credenciales de acceso con usuario y contraseña para asegurar que solo dispositivos autorizados puedan conectarse."

**[Mostrar Overview]**

**Integrante 1:**
> "El dashboard nos muestra la URL de conexión del broker y el puerto 8883, que usa TLS para conexiones seguras. Esta información es la que compartimos con todo el equipo para conectar nuestros dispositivos."

### Toma 7: Código y Topics
**[COMPARTIR PANTALLA - VS Code con config.py]**

**Integrante 1:**
> "En nuestro archivo de configuración tenemos las credenciales del broker y los topics que usaremos para la demostración:"

**Integrante 1:**
> "- 'equipo08/sensor/temperatura' para datos de sensores
> - 'equipo08/alertas' para notificaciones importantes
> - 'equipo08/chat' para mensajes entre dispositivos"

**Integrante 2:**
> "Todos nuestros dispositivos usan la misma configuración, lo que facilita la comunicación. Ahora veamos esto en acción."

---

## 🎬 SECCIÓN 4: DEMOSTRACIÓN EN VIVO (5-6 minutos)

### Toma 8: Iniciar Publisher Automático
**[PANTALLA DIVIDIDA - Terminal de Integrante 1]**

**Integrante 1:**
> "Voy a iniciar nuestro publisher automático que simula un sensor de temperatura."

```bash
python publisher.py
```

**[Esperar a ver la conexión]**

**Integrante 1:**
> "Como pueden ver, el script se conectó exitosamente al broker HiveMQ y está comenzando a publicar datos de temperatura y humedad cada 5 segundos."

**[Dejar corriendo, mostrar 2-3 mensajes publicándose]**

**Integrante 1:**
> "Aquí vemos temperatura de 24.5 grados, humedad del 55%... Los datos se están enviando al topic 'equipo08/sensor/temperatura' con QoS 1."

### Toma 9: Subscriber en Python
**[MOSTRAR PANTALLA DE Integrante 2 - Terminal]**

**Integrante 2:**
> "Ahora voy a iniciar mi subscriber en Python que está escuchando todos los topics del equipo."

```bash
python subscriber.py
```

**[Esperar a la conexión]**

**Integrante 2:**
> "Perfecto, estoy conectado y suscrito a los topics. Como pueden ver..."

**[Esperar a que llegue un mensaje del publisher]**

**Integrante 2:**
> "¡Aquí está! Estoy recibiendo los datos de temperatura en tiempo real. El mensaje incluye timestamp, temperatura de 25.3 grados, humedad... Todo en formato JSON."

**[Dejar que se reciban 2-3 mensajes]**

### Toma 10: App Móvil
**[MOSTRAR PANTALLA DE Integrante 3 - Celular/Emulador]**

**Integrante 3:**
> "Y yo tengo configurada la app IoT MQTT Panel en mi dispositivo móvil, también conectado al mismo broker."

**[Mostrar la app conectándose]**

**Integrante 3:**
> "Pueden ver que también estoy recibiendo los mismos datos de temperatura. Esto demuestra la versatilidad de MQTT: un mismo mensaje llega a múltiples tipos de dispositivos simultáneamente."

**[Mostrar el panel actualizándose con los datos]**

**Integrante 3:**
> "La temperatura se actualiza automáticamente cada 5 segundos. Tengo un gauge visual que me muestra el valor actual."

### Toma 11: Demostrar Alertas
**[VOLVER A PANTALLA DE Integrante 1]**

**Integrante 1:**
> "Nuestro publisher también está programado para detectar temperaturas críticas. Vean qué pasa cuando la temperatura sube de 28 grados..."

**[Esperar a que se genere una alerta automáticamente]**

**Integrante 1:**
> "¡Alerta! El sistema detectó temperatura alta de 28.7 grados y automáticamente publicó un mensaje al topic de alertas."

**[CAMBIAR A PANTALLA DE Integrante 2]**

**Integrante 2:**
> "Y aquí en mi subscriber veo la alerta llegando en el topic 'equipo08/alertas' con nivel WARNING. El sistema es capaz de separar datos normales de alertas usando diferentes topics."

### Toma 12: Publisher Interactivo
**[MOSTRAR PANTALLA DE Integrante 3]**

**Integrante 3:**
> "Ahora voy a demostrar la comunicación bidireccional. Voy a usar el publisher interactivo para enviar mensajes personalizados."

```bash
python publisher_interactivo.py
```

**Integrante 3:**
> "Estoy conectado. Voy a escribir un mensaje al chat..."

**[Escribir]**
```
Mensaje: ¡Hola desde el publisher de [Nombre]!
```

**[CAMBIAR A PANTALLA DE Integrante 2]**

**Integrante 2:**
> "¡Lo recibí! Aquí veo el mensaje de [Nombre] con su timestamp. Esto podría usarse para comunicación entre dispositivos IoT en tiempo real."

### Toma 13: Cambiar Topics en Vivo
**[VOLVER A INTEGRANTE 3]**

**Integrante 3:**
> "Puedo cambiar de topic dinámicamente. Voy a cambiar al topic de alertas..."

```
Mensaje: /topic equipo08/alertas
```

**Integrante 3:**
> "Y ahora envío una alerta manual..."

```
Mensaje: Sistema de prueba funcionando correctamente
```

**[MOSTRAR APP MÓVIL O SUBSCRIBER]**

**Integrante 2:**
> "Perfecto, la alerta llegó al topic correcto. Todos los subscribers suscritos a 'equipo08/alertas' reciben el mensaje."

### Toma 14: Wildcard Subscription
**[MOSTRAR TERMINAL DE Integrante 2]**

**Integrante 2:**
> "Una característica poderosa de MQTT son los wildcards. Mi subscriber está suscrito a 'equipo08/#', donde el símbolo '#' significa 'todos los sub-topics'."

**Integrante 2:**
> "Esto significa que recibo mensajes de todos los topics que empiecen con 'equipo08/', ya sea temperatura, alertas, chat, o cualquier otro que se cree."

**Integrante 1:**
> "Esto es muy útil en aplicaciones reales. Por ejemplo, un dashboard central podría suscribirse a 'casa/#' para recibir datos de todos los sensores de la casa."

### Toma 15: Demostrar Persistencia de Suscripciones
**[MOSTRAR PANTALLA DIVIDIDA]**

**Integrante 3:**
> "Ahora voy a demostrar algo interesante. Voy a detener mi subscriber temporalmente..."

**[Cerrar subscriber]**

**Integrante 1:**
> "Mientras tanto, el publisher sigue enviando datos..."

**[Mostrar publisher enviando 2-3 mensajes]**

**Integrante 3:**
> "Y ahora vuelvo a conectar mi subscriber..."

**[Reiniciar subscriber]**

**Integrante 3:**
> "Con QoS 1, el broker mantuvo los mensajes recientes y ahora los recibo al reconectarme. Esto asegura que no se pierdan datos importantes aunque haya desconexiones temporales."

---

## 🎬 SECCIÓN 5: VENTAJAS Y CASOS DE USO (1-2 minutos)

### Toma 16: Resumen de Ventajas
**[CÁMARA ABIERTA O COMPARTIR DIAPOSITIVA]**

**Integrante 2:**
> "Como hemos visto en la demostración, MQTT ofrece varias ventajas importantes:"

**Integrante 2:**
> "**Desacoplamiento**: Los publishers y subscribers no necesitan conocerse ni estar activos al mismo tiempo. El broker actúa como intermediario."

**Integrante 1:**
> "**Escalabilidad**: Un solo mensaje puede llegar a múltiples subscribers sin esfuerzo adicional del publisher. Podríamos tener 10, 100 o 1000 dispositivos escuchando."

**Integrante 3:**
> "**Eficiencia**: El protocolo es muy ligero, usa mínimo ancho de banda. Perfecto para sensores con batería o conexiones limitadas."

**Integrante 2:**
> "**Confiabilidad**: Con QoS 1 y 2, tenemos garantías de entrega incluso en redes inestables. El broker maneja reconexiones automáticamente."

### Toma 17: Casos de Uso Reales
**[COMPARTIR DIAPOSITIVA CON EJEMPLOS]**

**Integrante 1:**
> "MQTT se usa extensivamente en aplicaciones reales de IoT:"

**Integrante 1:**
> "- **Smart Home**: Termostatos, luces, cámaras, sensores de puertas comunicándose entre sí
> - **Industrial IoT**: Monitoreo de maquinaria, alertas de mantenimiento, control de procesos
> - **Agricultura**: Sensores de humedad de suelo, automatización de riego
> - **Salud**: Dispositivos médicos wearables enviando datos vitales a hospitales
> - **Automotriz**: Vehículos conectados enviando telemetría y recibiendo actualizaciones"

**Integrante 3:**
> "Empresas como Facebook Messenger, Amazon AWS IoT y sistemas de smart cities usan MQTT para manejar millones de dispositivos conectados."

---

## 🎬 SECCIÓN 6: CONCLUSIONES (2 minutos)

### Toma 18: Conclusiones Individuales
**[CÁMARA ABIERTA - TODOS VISIBLES]**

**Integrante 3:**
> "En conclusión, MQTT es un protocolo fundamental para Internet de las Cosas que permite comunicación eficiente y confiable entre dispositivos."

**Integrante 2:**
> "El modelo publish/subscribe con broker intermediario ofrece un desacoplamiento que facilita el desarrollo y escalamiento de sistemas IoT complejos."

**Integrante 1:**
> "Servicios como HiveMQ Cloud hacen muy accesible implementar soluciones profesionales, incluso para proyectos educativos o startups que están comenzando."

**Integrante 2:**
> "Lo que más me impresionó fue la facilidad de uso. Con pocas líneas de código en Python pudimos crear un sistema distribuido que funciona en múltiples dispositivos y plataformas."

**Integrante 3:**
> "Y la flexibilidad de los topics permite organizar la información de manera jerárquica y lógica, facilitando el mantenimiento del sistema."

**Integrante 1:**
> "Esta tecnología está transformando industrias completas, desde manufactura hasta agricultura, permitiendo tomar decisiones en tiempo real basadas en datos de sensores."

### Toma 19: Cierre
**[TODOS MIRANDO A CÁMARA]**

**Integrante 1:**
> "Esperamos que esta demostración haya sido clara y útil para entender las capacidades de MQTT."

**Integrante 2:**
> "Todo nuestro código está disponible y documentado para que puedan replicar y experimentar con MQTT."

**Integrante 3:**
> "Les animamos a explorar más sobre este protocolo y las infinitas posibilidades que ofrece para IoT."

**TODOS:**
> "¡Gracias por su atención!"

**[FIN DEL VIDEO]**

---

## 📝 NOTAS DE PRODUCCIÓN

### Timing Sugerido
- Introducción: 0:00 - 2:00
- Teoría: 2:00 - 6:00
- Configuración: 6:00 - 8:00
- Demo: 8:00 - 14:00
- Conclusiones: 14:00 - 16:00

### Checklist Final de Edición
- [ ] Buena calidad de audio en todas las secciones
- [ ] Transiciones suaves entre tomas
- [ ] Pantallas compartidas legibles
- [ ] Todos los integrantes tienen tiempo similar en cámara
- [ ] Demostración fluye sin cortes visibles
- [ ] Música de fondo suave (opcional)
- [ ] Captions para términos técnicos importantes
- [ ] Exportar en 1080p mínimo
- [ ] Duración entre 10-15 minutos

### Consejos para la Grabación
1. **Hacer prueba completa** antes de la grabación final
2. **Tener agua** cerca para todos
3. **Cerrar notificaciones** en todos los dispositivos
4. **Usar auriculares** para evitar eco
5. **Iluminación natural** o ring light
6. **Fondo limpio** y profesional
7. **Probar todos los códigos** 30 minutos antes
8. **Tener backup** de los scripts por si algo falla

### Qué Mostrar en Pantalla
- Dashboard de HiveMQ con métricas
- Código ejecutándose en terminales
- Mensajes llegando en tiempo real
- App móvil actualizándose
- Diapositivas claras y profesionales

### Qué Evitar
- ❌ Cortes bruscos
- ❌ Largos silencios
- ❌ Pantallas con información sensible (contraseñas completas)
- ❌ Errores sin resolver en pantalla
- ❌ Jerga técnica sin explicar

### Plan B por si Algo Falla
- Tener mensajes pre-publicados con MQTT Retain flag
- Grabaciones de pantalla de backup
- Script de prueba simple que siempre funcione
- HiveMQ tiene Web Client incorporado como backup
