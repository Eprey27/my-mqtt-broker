# Message Queuing Telemetry Transport - MQTT

> MQTT, que significa "Message Queuing Telemetry Transport", es un protocolo de mensajería ligero diseñado para dispositivos de bajo ancho de banda, alta latencia o redes inestables. Fue desarrollado por IBM en la década de 1990 y se ha convertido en un estándar popular para la Internet de las Cosas (IoT) y otras aplicaciones donde se necesita un protocolo de mensajería eficiente.

Aquí hay algunas características clave de MQTT:

1. **Modelo Publish/Subscribe**: A diferencia del modelo tradicional de petición/respuesta, MQTT utiliza un modelo de publicación/suscripción. Los dispositivos (clientes) pueden suscribirse a temas y otros dispositivos pueden publicar mensajes en esos temas.

2. **Broker**: Un componente central en la arquitectura MQTT es el "broker". Es el intermediario que gestiona las suscripciones y las publicaciones de los clientes.

3. **QoS (Quality of Service)**: MQTT soporta diferentes niveles de QoS:
   - QoS 0: El mensaje se entrega como máximo una vez, y la entrega no está confirmada.
   - QoS 1: El mensaje se entrega al menos una vez, y se espera una confirmación.
   - QoS 2: El mensaje se entrega exactamente una vez mediante un proceso de intercambio de cuatro pasos.

4. **Retención de Mensajes**: Si se especifica, el último mensaje enviado a un tema puede ser retenido por el broker. Así, cualquier cliente que se suscriba más tarde a ese tema recibirá inmediatamente el mensaje retenido.

5. **Last Will and Testament (LWT)**: Es un mensaje que se especifica en el momento de la conexión. Si el broker detecta que un cliente se ha desconectado de forma inesperada, enviará automáticamente el mensaje LWT en nombre del cliente desconectado.

6. **Seguridad**: Aunque MQTT en sí mismo no define características avanzadas de seguridad, puede funcionar sobre conexiones TLS/SSL para cifrado y autenticación.

MQTT se utiliza en una variedad de aplicaciones, desde la automatización del hogar y la industria hasta la telemetría de vehículos y la monitorización del estado de la salud. Es especialmente popular en escenarios donde la eficiencia en términos de ancho de banda y recursos del dispositivo es crucial.

---

Si eres un desarrollador en C# que trabaja con .NET y estás interesado en MQTT, hay varias cosas que debes conocer y considerar. Aquí te presento una lista con algunos de los aspectos más relevantes:

1. **Bibliotecas y SDKs**:
   - **MQTTnet**: Es una de las bibliotecas MQTT más populares para .NET. Es de código abierto y ofrece una API asincrónica para trabajar con MQTT. Con esta biblioteca, puedes tanto publicar y suscribirte a mensajes como construir tu propio broker MQTT.

2. **Conceptos Básicos**:
   - Entender el modelo de **publicación/suscripción** de MQTT.
   - Conocer cómo funcionan los **topics** y cómo se estructuran.
   - Familiarizarse con los niveles de **QoS** y cuándo usar cada uno.
   - Aprender sobre la **retención de mensajes** y el **Last Will and Testament (LWT)**.

3. **Seguridad**:
   - Si bien MQTT en sí mismo es ligero y no prescribe mecanismos de seguridad específicos, es esencial implementar **TLS/SSL** cuando se transmiten datos sensibles o cuando se utiliza MQTT en producción.
   - Aprender a manejar la **autenticación y autorización** en MQTT, ya sea a nivel de broker o mediante complementos o soluciones personalizadas.

4. **Optimización**:
   - MQTT es eficiente, pero aún así es crucial saber cómo **estructurar los mensajes y los topics** para obtener el máximo rendimiento, especialmente si trabajas con dispositivos de IoT con recursos limitados.
   - Entender cómo las características de **QoS**, la retención de mensajes y otros aspectos pueden afectar el rendimiento y la eficiencia de la red.

5. **Integración**:
   - Puede que necesites integrar MQTT con otras soluciones o sistemas. Por ejemplo, si estás recopilando datos de sensores mediante MQTT, esos datos podrían necesitar ser almacenados en una base de datos o enviados a una API web. Conoce cómo hacer estas integraciones de manera eficaz en el ecosistema .NET.

6. **Pruebas y Monitorización**:
   - Asegúrate de probar tus implementaciones MQTT bajo diferentes condiciones de red y carga para garantizar su robustez.
   - Utiliza herramientas para monitorear el tráfico MQTT, lo que puede ayudarte a identificar y solucionar problemas.

7. **Mantente Actualizado**:
   - MQTT, como cualquier otra tecnología, evoluciona con el tiempo. Es crucial mantenerse al día con las últimas versiones del protocolo y las mejores prácticas asociadas.

Finalmente, te recomiendo empezar con pequeños proyectos para familiarizarte con MQTT en .NET. Puedes comenzar configurando un broker como Mosquitto, conectarte a él desde una aplicación .NET usando MQTTnet, y luego publicar y suscribirte a mensajes para ver cómo funciona todo en acción. ¡Buena suerte en tu aventura con MQTT!

---

¡Por supuesto! Aquí hay algunas ideas de proyectos pequeños para iniciarte en MQTT utilizando .NET:

1. **Monitor de Temperatura**:
   - Utiliza un sensor de temperatura (como el DHT11 o DHT22) conectado a un dispositivo como Raspberry Pi o Arduino.
   - Haz que el dispositivo publique lecturas de temperatura en un topic MQTT específico.
   - Crea una aplicación en .NET que se suscriba a ese topic y muestre las lecturas en tiempo real.

2. **Sistema de Alerta de Puerta**:
   - Coloca un sensor magnético en una puerta para detectar cuando se abre o cierra.
   - Publica el estado de la puerta (abierta/cerrada) en un topic MQTT.
   - Crea una aplicación .NET que se suscriba a este topic y envíe una notificación o alerta cuando el estado de la puerta cambie.

3. **Controlador de Luces Remoto**:
   - Conecta una lámpara o tira LED a un microcontrolador o dispositivo IoT.
   - Crea una aplicación .NET con una interfaz que permita al usuario encender/apagar la luz.
   - Cuando el usuario interactúa con la interfaz, la aplicación .NET publica un mensaje en un topic MQTT al que el dispositivo esté suscrito, y el dispositivo responde encendiendo o apagando la luz.

4. **Monitor de Consumo de Energía**:
   - Si tienes acceso a un medidor de energía inteligente que pueda enviar datos vía MQTT (o si puedes hacer uno), haz que publique el consumo en tiempo real.
   - Crea una aplicación .NET que visualice estos datos, tal vez incluso con gráficos en tiempo real.

5. **Chat Simple**:
   - Crea dos aplicaciones .NET: una para enviar mensajes y otra para recibirlos.
   - Utiliza MQTT para transmitir los mensajes entre las aplicaciones, emulando un chat simple.

6. **Sistema de Riego Automatizado**:
   - Utiliza un sensor de humedad del suelo y conecta una bomba de agua o válvula a un microcontrolador.
   - Cuando el sensor detecte que el suelo está demasiado seco, puede publicar un mensaje en un topic.
   - Una aplicación .NET que monitorea este topic puede enviar una alerta o incluso activar automáticamente el riego.

7. **Broker MQTT Personalizado**:
   - Usando la biblioteca MQTTnet en .NET, intenta crear tu propio broker MQTT básico.
   - Esto te dará una comprensión profunda de cómo funcionan las operaciones internas de MQTT.

Estos proyectos te proporcionarán una comprensión práctica de cómo funcionan las operaciones de publicación y suscripción en MQTT y cómo integrar dispositivos y aplicaciones en un sistema unificado. A medida que te familiarices con estos conceptos básicos, podrás ampliar tus proyectos o combinarlos de maneras interesantes. ¡Buena suerte!

---

# 6. **Sistema de Riego Automatizado**:

- Utiliza un sensor de humedad del suelo y conecta una bomba de agua o válvula a un microcontrolador.
- Cuando el sensor detecte que el suelo está demasiado seco, puede publicar un mensaje en un topic.
- Una aplicación .NET que monitorea este topic puede enviar una alerta o incluso activar automáticamente el riego.

El sistema de riego automatizado utilizando MQTT con un sensor de humedad y una bomba de agua puede tener múltiples componentes. Aquí, te daré un ejemplo simplificado en el que supondré que estás utilizando un microcontrolador (como un ESP8266 o ESP32 con soporte para MQTT) para el hardware, y una aplicación .NET para monitorear y controlar.

**1. Hardware (por ejemplo, usando un ESP8266 y el framework Arduino):**

```cpp
#include <WiFi.h>
#include <PubSubClient.h>

const char* ssid = "tu_SSID";
const char* password = "tu_PASSWORD";
const char* mqtt_server = "dirección_del_broker_MQTT";

WiFiClient espClient;
PubSubClient client(espClient);

const int soilSensorPin = A0; // Suponiendo que el sensor analógico está en A0
const int waterPumpPin = D1; // Conecta la bomba de agua aquí

void setup() {
  pinMode(soilSensorPin, INPUT);
  pinMode(waterPumpPin, OUTPUT);
  digitalWrite(waterPumpPin, LOW);

  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
  }

  client.setServer(mqtt_server, 1883);
  client.setCallback(callback);
}

void callback(char* topic, byte* message, unsigned int length) {
  String messageTemp;
  for (int i = 0; i < length; i++) {
    messageTemp += (char)message[i];
  }
  
  if (messageTemp == "ON") {
    digitalWrite(waterPumpPin, HIGH);
  }
  else if (messageTemp == "OFF") {
    digitalWrite(waterPumpPin, LOW);
  }
}

void loop() {
  if (!client.connected()) {
    while (!client.connected()) {
      if (client.connect("ESP8266Client")) {
        client.subscribe("home/garden/waterpump");
      }
    }
  }

  int soilMoistureValue = analogRead(soilSensorPin);
  client.publish("home/garden/soilmoisture", String(soilMoistureValue).c_str());

  delay(5000); // Publica cada 5 segundos
  client.loop();
}
```

**2. Aplicación .NET (usando la biblioteca MQTTnet):**

```csharp
using MQTTnet;
using MQTTnet.Client;
using MQTTnet.Client.Options;
using System;
using System.Text;
using System.Threading.Tasks;

class Program {
    static async Task Main(string[] args) {
        var factory = new MqttFactory();
        var mqttClient = factory.CreateMqttClient();
        var options = new MqttClientOptionsBuilder()
            .WithClientId("DotNetClient")
            .WithTcpServer("dirección_del_broker_MQTT")
            .Build();

        mqttClient.UseConnectedHandler(async e => {
            await mqttClient.SubscribeAsync(new MqttTopicFilterBuilder().WithTopic("home/garden/soilmoisture").Build());
        });

        mqttClient.UseApplicationMessageReceivedHandler(e => {
            string message = Encoding.UTF8.GetString(e.ApplicationMessage.Payload);
            int moistureValue = Convert.ToInt32(message);

            if (moistureValue < 500) { // Este valor es solo un ejemplo. Ajusta según tu sensor y necesidades.
                mqttClient.PublishAsync("home/garden/waterpump", "ON");
            } else {
                mqttClient.PublishAsync("home/garden/waterpump", "OFF");
            }
        });

        await mqttClient.ConnectAsync(options);
        Console.ReadLine(); 
    }
}
```

Estos ejemplos son bastante básicos y simplificados. Si estás construyendo una solución real, deberías considerar agregar manejo de errores, re-conexiones, seguridad (por ejemplo, autenticación MQTT y conexiones cifradas), entre otros. ¡Espero que esto te ayude a comenzar!

---

# 7. Broker MQTT Personalizado

- Usando la biblioteca MQTTnet en .NET, intenta crear tu propio broker MQTT básico.
- Esto te dará una comprensión profunda de cómo funcionan las operaciones internas de MQTT.

El ejemplo 7 trata sobre crear un broker MQTT personalizado usando la biblioteca MQTTnet en .NET. A continuación, te mostraré un ejemplo simplificado de cómo hacerlo.

1. **Instalar el paquete NuGet necesario**:

Primero, necesitas instalar el paquete NuGet de MQTTnet. Puedes hacerlo usando el Administrador de paquetes NuGet o la línea de comandos:

```bash
Install-Package MQTTnet
```

2. **Código del Broker MQTT Personalizado**:

```csharp
using MQTTnet;
using MQTTnet.Server;
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        var optionsBuilder = new MqttServerOptionsBuilder()
            .WithConnectionValidator(context =>
            {
                if (context.ClientId.Length < 10)
                {
                    context.ReasonCode = MqttConnectReasonCode.ClientIdentifierNotValid;
                    return;
                }

                if (context.Username != "myUser" || context.Password != "myPassword")
                {
                    context.ReasonCode = MqttConnectReasonCode.BadUserNameOrPassword;
                    return;
                }

                context.ReasonCode = MqttConnectReasonCode.Success;
            })
            .WithDefaultEndpointPort(1883);

        var mqttServer = new MqttFactory().CreateMqttServer();
        mqttServer.UseClientConnectedHandler(eventArgs =>
        {
            Console.WriteLine($"Cliente conectado: {eventArgs.ClientId}");
        });

        mqttServer.UseClientDisconnectedHandler(eventArgs =>
        {
            Console.WriteLine($"Cliente desconectado: {eventArgs.ClientId}");
        });

        await mqttServer.StartAsync(optionsBuilder.Build());

        Console.WriteLine("Broker MQTT iniciado. Presiona cualquier tecla para salir.");
        Console.ReadLine();

        await mqttServer.StopAsync();
    }
}
```

Este código crea un servidor MQTT básico que se ejecuta en el puerto 1883. La conexión se valida comprobando el tamaño del ClientId y también verificando un nombre de usuario y contraseña fijos. También hemos agregado manejadores para registrar cuando un cliente se conecta o desconecta.

Recuerda, este es un broker básico. En un escenario real, querrías agregar más características, configuraciones y seguridad, y posiblemente almacenar los mensajes, manejar la persistencia de las sesiones, entre otros.

Sin embargo, este ejemplo te da una idea de cómo iniciar y gestionar tu propio broker MQTT usando MQTTnet en .NET. ¡Espero que te sea útil para empezar!

---

# Casos de uso comunes de un MQTT service broker

Claro, los brokers MQTT desempeñan un papel fundamental en la arquitectura de IoT y otras aplicaciones de mensajería en tiempo real. A continuación, te detallaré algunos de los casos de uso más comunes para un broker MQTT:

1. **Internet de las Cosas (IoT)**:
    - **Dispositivos domésticos inteligentes**: Desde termostatos hasta luces, pasando por cerraduras inteligentes. Estos dispositivos pueden comunicarse entre sí y con aplicaciones centralizadas a través de un broker MQTT.
    - **Monitorización industrial**: Sensores en fábricas y plantas industriales pueden enviar datos a través de MQTT para monitoreo, alertas y análisis.
    - **Gestión de flotas**: Vehículos equipados con sensores y dispositivos GPS pueden enviar información en tiempo real a través de MQTT para rastreo, mantenimiento y análisis.

2. **Aplicaciones Móviles**:
    - **Notificaciones push**: Aunque existen servicios específicos para notificaciones push, MQTT puede ser una alternativa debido a su bajo consumo de batería y entrega en tiempo real.
    - **Chat en tiempo real**: MQTT puede ser usado para mensajería instantánea en aplicaciones de chat, especialmente donde la eficiencia y la entrega rápida son cruciales.

3. **Telemetría**:
    - **Drones**: Para enviar datos de posición, estado de la batería, y otros parámetros en tiempo real.
    - **Equipos médicos**: Dispositivos como monitores cardíacos y otros instrumentos médicos pueden usar MQTT para enviar datos en tiempo real.

4. **Sistemas de Seguridad**:
    - **Monitoreo de cámaras y sensores**: Las cámaras y sensores pueden enviar alertas y estados a través de MQTT.
    - **Sistemas de alarma**: Para comunicarse con centros de monitoreo y con aplicaciones móviles de los usuarios.

5. **Gestión de Energía y Utilidades**:
    - **Redes inteligentes**: Los dispositivos en una red eléctrica inteligente pueden comunicarse entre sí y con estaciones centrales a través de MQTT.
    - **Monitorización de recursos**: Como agua, gas y electricidad.

6. **Agricultura Inteligente**:
    - Sensores en el campo pueden enviar datos sobre humedad del suelo, condiciones climáticas, etc., para optimizar el riego y otras operaciones agrícolas.

7. **Retail**:
    - **Gestión de inventario**: Los sensores en estantes pueden comunicarse con sistemas centralizados para monitorear el stock.
    - **Publicidad y marketing en tiempo real**: Por ejemplo, enviar ofertas a dispositivos móviles de clientes basados en su ubicación en tiempo real dentro de una tienda.

8. **Logística**:
    - **Monitorización de condiciones de carga**: Como temperatura en contenedores refrigerados durante el transporte.
    - **Rastreo de paquetes**: Para enviar actualizaciones en tiempo real sobre la ubicación y el estado de los paquetes.

9. **Integración y Automatización de Sistemas**:
    - **Middleware**: MQTT puede actuar como un middleware para integrar diferentes sistemas que no se comunican directamente entre sí.
    - **Automatización de procesos empresariales**: Donde diferentes aplicaciones y dispositivos necesitan comunicarse en tiempo real.

10. **Investigación y Desarrollo**:
    - **Prototipos**: Gracias a su facilidad de uso y versatilidad, MQTT es comúnmente usado en prototipos y proyectos de investigación.

Dada la naturaleza liviana y eficiente de MQTT y su modelo de publicación/suscripción, es una excelente elección para casos de uso donde se requiere comunicación en tiempo real, especialmente en entornos donde el ancho de banda es limitado o es costoso, y donde los dispositivos pueden tener recursos limitados.

---

# características y capacidades clave de un service broker de MQTT

Para que un service broker de MQTT pueda atender eficientemente los casos de uso mencionados, necesita tener ciertas características y capacidades clave. A continuación, detallo algunas de las más importantes:

1. **Escalabilidad**:
    - **Alta Conexión Concurrente**: El broker debe ser capaz de manejar miles, si no millones, de conexiones concurrentes, especialmente en escenarios de IoT donde el número de dispositivos puede ser enorme.
    - **Escalabilidad Horizontal**: La capacidad de agregar más instancias del broker para manejar el aumento de la carga es esencial.

2. **Fiabilidad y Durabilidad**:
    - **Calidad de Servicio (QoS)**: Debe soportar los tres niveles de QoS de MQTT: 0 (sin confirmación), 1 (confirmación en el punto de entrega) y 2 (entrega exactamente una vez).
    - **Persistencia de Mensajes**: En el caso de desconexiones o problemas, el broker debe ser capaz de almacenar mensajes hasta que puedan ser entregados.
    - **Tolerancia a Fallos**: El broker debería ser resistente a fallos y tener capacidad de auto-recovery.

3. **Seguridad**:
    - **Autenticación y Autorización**: Capacidad para verificar la identidad de los clientes y determinar qué recursos o temas pueden acceder.
    - **Encriptación**: Soporte para conexiones seguras, generalmente a través de TLS/SSL.
    - **Aislamiento de Sesion**: Prevenir que un cliente pueda interceptar mensajes destinados a otro cliente.

4. **Flexibilidad y Extensibilidad**:
    - **Soporte de Plugins o Extensiones**: Esto permite al broker adaptarse a necesidades específicas o añadir funcionalidades adicionales.
    - **Interfaz API**: Para administración, monitoreo o integración con otros sistemas.

5. **Rendimiento**:
    - **Latencia Baja**: Esencial para aplicaciones en tiempo real.
    - **Optimización del Ancho de Banda**: Capacidad para minimizar el uso de datos, lo cual es crítico en redes limitadas o costosas.

6. **Retención y Almacenamiento**:
    - **Retención de Mensajes (Last Will and Testament)**: Un mensaje que el broker envía en nombre del cliente cuando este se desconecta inesperadamente.
    - **Almacenamiento Temporal**: Capacidad para almacenar mensajes de forma temporal para clientes que estén offline (con QoS 1 y 2).

7. **Monitoreo y Administración**:
    - **Logging**: Registrar actividades y transacciones para análisis y troubleshooting.
    - **Herramientas de Monitoreo**: Para supervisar la salud, el rendimiento y la actividad del broker en tiempo real.
    - **Alertas**: Notificaciones en caso de problemas o situaciones anómalas.

8. **Interoperabilidad**:
    - **Compatibilidad con Estándares**: Asegurarse de que el broker sea compatible con las especificaciones MQTT estándar para garantizar la interoperabilidad con diferentes clientes y dispositivos.
    - **Protocolo Bridging**: La capacidad de actuar como un puente entre diferentes protocolos de mensajería.

9. **Clustering y Balanceo de Carga**:
    - La capacidad de agrupar varios brokers y distribuir la carga entre ellos para mejorar la redundancia y el rendimiento.

10. **Limitación y Control de Carga**:
    - **Control de Tasa (Throttling)**: Limitar el número de mensajes por cliente o por tema para evitar la sobrecarga.
    - **Limitación de Clientes**: Poder establecer un límite máximo de conexiones.

Estas características garantizan que el broker MQTT pueda atender los diversos y complejos escenarios de los casos de uso mencionados, desde sistemas IoT a gran escala hasta aplicaciones en tiempo real que requieren alta disponibilidad, seguridad y rendimiento.
