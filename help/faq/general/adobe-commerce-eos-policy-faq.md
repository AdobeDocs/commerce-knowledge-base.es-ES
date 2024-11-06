---
title: Preguntas frecuentes sobre el fin de la asistencia del software Adobe Commerce
description: Las siguientes preguntas frecuentes están pensadas para ayudar a los comerciantes, desarrolladores y socios a comprender las implicaciones de la fecha de fin de soporte (EOS) publicada por Adobe Commerce para las versiones afectadas de Adobe Commerce.
exl-id: ec147307-46eb-4a3a-8572-a014b091c58a
feature: Best Practices, Compliance, Console
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 0%

---

# Preguntas frecuentes sobre el fin de la asistencia del software Adobe Commerce

Las siguientes preguntas frecuentes están pensadas para ayudar a los comerciantes, desarrolladores y socios a comprender las implicaciones de la fecha de fin de soporte (EOS) publicada por Adobe Commerce para las versiones afectadas de Adobe Commerce.

## Disposiciones generales

### ¿Dónde puedo encontrar las fechas de soporte de software para todas las versiones de Adobe Commerce?

Puede encontrar la directiva de ciclo de vida del software de Adobe Commerce y las fechas de compatibilidad con el software en la [Directiva de ciclo de vida del software de Adobe Commerce](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf). También publicamos fechas de fin de soporte (EOS) en nuestra [página de documentación para desarrolladores](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions).

### ¿Qué significa cuando el Adobe deja de ser compatible con una versión del software de Adobe Commerce?

Cuando Adobe finalice el soporte para una versión de su software de Adobe Commerce, puede esperar lo siguiente:

* Adobe Commerce ya no creará más cambios de producto para esa versión (incluidos cambios funcionales, de calidad, de seguridad y de conformidad con PCI).
* Las solicitudes de extracción de la comunidad ya no se aceptarán ni fusionarán para la versión EOS. Se eliminarán las extensiones del Commerce Marketplace que solo sean compatibles con versiones no compatibles de Adobe Commerce.
* Se eliminará la documentación en línea de las versiones no compatibles (por ejemplo, los materiales de documentación para desarrolladores).
* Los tickets de asistencia enviados después de la finalización de la compatibilidad con una versión de Adobe Commerce no se resolverán (a continuación se proporcionan más detalles de asistencia técnica).

### ¿Cuáles son las implicaciones para los comerciantes que utilizan software de Adobe Commerce no compatible?

Se recomienda encarecidamente utilizar únicamente software compatible.

Si decide seguir utilizando software que ha finalizado la asistencia técnica, ya no recibirá actualizaciones importantes del producto ni soporte técnico, que a menudo incluye las actualizaciones de seguridad más recientes. El uso de software no compatible puede afectar a las siguientes áreas:

**Proporcionar experiencias de compra seguras:**

* Necesitará gastar recursos para evaluar y emplear proveedores de terceros para proporcionar soporte de seguridad, correcciones y actualizaciones.
* Una vez que una versión del software de Adobe Commerce ya no sea compatible, esa versión ya no es [compatible con PCI](https://www.pcisecuritystandards.org/pci_security/maintaining_payment_security). Cuando esto sucede, usted puede estar sujeto a multas, la eliminación de la capacidad de procesamiento de la tarjeta de crédito, u otras sanciones como resultado.
* Dado que la mayoría de las vulnerabilidades tienden a dirigirse a instalaciones que no están actualizadas con las últimas actualizaciones de seguridad, recomendamos siempre que los comerciantes mantengan su software actualizado e instalen actualizaciones de seguridad en cuanto estén disponibles. Depende del comerciante mantener su tienda en línea segura con las garantías y controles de seguridad adecuados para proteger su sitio web y los datos personales de sus clientes. Una de las mejores maneras de hacerlo es tener instalados los parches, las correcciones y las actualizaciones de software más recientes, y monitorizar continuamente su sitio y Admin Console para detectar actividades inusuales.

**Funcionamiento eficiente y eficaz**

* A medida que las versiones de software de Adobe Commerce no son compatibles, hay un grupo cada vez menor de desarrolladores y socios disponibles y capaces de proporcionar soporte para versiones obsoletas a medida que orientan sus operaciones a tecnologías más nuevas. Generalmente, el resultado es que la cantidad y calidad del talento para el mantenimiento del software disminuye, mientras que el costo de mantenimiento del software aumenta.
* En el caso de software Adobe Commerce no compatible, las tecnologías de periféricos y las dependencias también pueden alcanzar su propio final de vida útil (por ejemplo, PHP, MYSQL, REDIS, SOLR). Esto hace que sea cada vez más difícil administrar y mantener un sitio seguro y compatible.
* Los desarrolladores de extensiones también están aumentando su enfoque en las últimas tecnologías y plataformas compatibles. Como resultado, es posible que no sigan manteniendo las extensiones para versiones no compatibles de Adobe Commerce.
* El uso de versiones no compatibles del software de Adobe Commerce a menudo conduce a gastar más dinero y recursos en mantener una plataforma antigua, en lugar de aplicar esos recursos a la innovación y el crecimiento continuos del negocio.

**Creciendo agresivamente**

* El Adobe sigue invirtiendo en nuevas tecnologías y capacidades. Al mantener el software actualizado, puede aprovechar las nuevas tecnologías y capacidades que pueden ayudar a su empresa a operar de forma más estratégica y crecer aún más rápido.

### ¿Cuáles son algunos ejemplos de cómo los comerciantes pueden beneficiarse de las nuevas tecnologías al mantenerse al día con su software de Adobe Commerce?

Existen varias formas en las que se beneficia significativamente de mantenerse actualizado con el software de Adobe Commerce:

* Además de mantener su plataforma actualizada con las últimas protecciones de seguridad, incluida la compatibilidad con PCI, la actualización a una versión compatible puede proporcionar mejoras en rendimiento y escalabilidad, lo que le proporciona acceso a las últimas innovaciones.
* Adobe Commerce 2.4.4, el próximo 12 de abril de 2022, supone un nuevo paso adelante en las capacidades de comercio, el rendimiento y la protección. Establece la base para los próximos años de innovación en Adobes y ayuda con la resiliencia comercial y empresarial. Construida sobre la versión más reciente de PHP 8.1, la última versión permite a los comerciantes a futuras pruebas de sus negocios de comercio digital con:
   * Acceso más rápido a funciones innovadoras como servicios SaaS, como Recommendations de productos, servicios de pago y Live Search
   * Mantenimiento y actualizaciones más sencillas y rentables
   * Flexibilidad continua para personalizar y satisfacer necesidades empresariales únicas
   * Incrementos significativos en rendimiento y escalabilidad
   * Mejor experiencia de desarrollador y mejores herramientas para monitorizar el estado de la plataforma

### ¿Qué debo hacer para evitar problemas de fin de soporte de software?

Su plataforma de comercio es un sistema comercial importante para su empresa y mantenerse al día y al día es una inversión continua crítica en el negocio. Las últimas actualizaciones tecnológicas y de seguridad para tu tienda digital son importantes en muchos niveles y pueden ayudar a mejorar las innovaciones y el crecimiento.

La migración a la versión más reciente del software de Adobe Commerce puede tardar cierto tiempo y recursos en ejecutarse correctamente. Una práctica recomendada es planificar con la mayor antelación posible a la fecha de finalización de la asistencia para garantizar que dispone del tiempo y los recursos adecuados para lograr sus objetivos estratégicos dentro del calendario y el presupuesto. Para ayudarle con la próxima actualización, Adobe ha publicado la [Guía de actualización 2.4](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) que incluye las prácticas recomendadas y los pasos técnicos que debe seguir, así como las herramientas y los recursos que debe utilizar al realizar la actualización.

Otra consideración importante es reservar recursos para desarrolladores y socios lo antes posible. El tiempo y los recursos del socio se suelen reservar mucho antes de la fecha de finalización de la asistencia, lo que da como resultado una cantidad significativamente menor de recursos para ayudar con los proyectos de migración. Se recomienda que tenga un plan móvil de tres años que analice anualmente como mínimo y que se asegure de que el próximo año esté planificado y presupuestado. Utilice [el calendario de versiones del Adobe](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) para realizar un seguimiento de las fechas de las versiones.

### ¿Puedo utilizar un proveedor de servicios de terceros para la asistencia de software cuando la asistencia de Adobe Commerce cese?

Sí, puede buscar empresas de seguridad, desarrolladores o socios que proporcionen soporte para versiones no compatibles de Adobe Commerce. Será su responsabilidad evaluar a estos proveedores, volver a certificar el cumplimiento según sea necesario e identificar y resolver las amenazas de seguridad en curso que puedan afectar a su negocio y a sus clientes.

### Tengo una licencia para Adobe Commerce que se extiende más allá de la fecha de fin de soporte o de esa versión. ¿Adobe seguirá proporcionando soporte de software para mi versión no compatible durante toda la vida de mi licencia si elijo no pasarme a una versión compatible?

La licencia de Adobe Commerce le otorga el derecho de acceder a las versiones de Adobe Commerce disponibles en general y utilizarlas, incluido el acceso a ellas y el uso de versiones no compatibles. Independientemente de si la versión del software es compatible, es necesario que siga actualizándose con las tarifas de licencia actuales para seguir accediendo y utilizando el software de Adobe Commerce. Esto finaliza cuando finaliza el contrato de Adobe Commerce.

Una licencia de Adobe Commerce no proporciona soporte de software para las versiones que han alcanzado y pasado la fecha de fin de soporte. Es importante destacar que, si permanece en un software no compatible, tendrá que gestionar y pagar sus propios parches de seguridad y volver a certificar la conformidad con PCI, y probablemente asumirá riesgos y responsabilidades de seguridad adicionales.

### ¿Se &quot;apaga&quot; una versión de software cuando llega y pasa la fecha de fin de soporte?

No, el software de Adobe Commerce no se &quot;apaga&quot; una vez que se llega a la fecha de fin de soporte o se pasa. Su licencia sigue siendo válida incluso para software de Adobe Commerce no admitido, siempre y cuando su cuenta esté al día, sin embargo, usted será responsable de la certificación de conformidad con PCI y ya no podrá presentar vales de soporte. Lo más importante es que ya no recibirás parches de seguridad que te ayuden a proteger tu tienda digital.

### ¿Puedo seguir utilizando el software de Adobe Commerce una vez que mi licencia haya caducado?

Una vez caducada la licencia de Adobe Commerce, debe dejar de utilizar el software de Adobe Commerce y eliminar todas las versiones de dicho software. Siempre que su cuenta esté al día, la licencia de Adobe Commerce le otorga el derecho de acceder a las versiones de Adobe Commerce disponibles en general y utilizarlas.

## Disposiciones técnicas

### ¿Seguirán funcionando los vales de soporte que se hayan abierto ANTES de la fecha de finalización de la compatibilidad de una versión de software para resolver el problema incluso después de que haya pasado la fecha de finalización de la compatibilidad?

Sí, los vales de soporte abiertos antes de la fecha de finalización de la compatibilidad de una versión de software se seguirán trabajando y resolviendo incluso si ha pasado la fecha de finalización de la compatibilidad para esa versión de software. Sin embargo, la resolución de los tickets de asistencia puede depender de si la resolución depende de componentes fuera del control de Adobe Commerce (por ejemplo, PHP, jQuery, etc.) que han caducado o han llegado al final de la asistencia. En estos casos, el vale de soporte se puede resolver indicándole que actualice a la última versión.

### Si abro un ticket para una versión de software en la que el soporte de software finaliza pronto, ¿Adobe dará prioridad a esos tickets para que se resuelvan antes de que finalice la fecha de soporte?

No, el Adobe no vuelve a priorizar los tickets de asistencia en función de la fecha de finalización de la asistencia de esas versiones de software. Los tickets de soporte se abordan en función de algoritmos internos derivados del motivo de contacto del ticket, el entorno y el impacto comercial.

### Para los tickets de asistencia abiertos ANTES de que finalice la fecha de asistencia, ¿existe una alerta para recordar a los comerciantes la próxima finalización de la asistencia?

No, no hay alertas de recordatorio que notifiquen a los usuarios de tickets de asistencia las próximas fechas de fin de soporte. Es responsabilidad del usuario que abre el ticket saber las fechas de finalización de la compatibilidad para la versión de Adobe Commerce en la que se encuentran, que se encuentra en nuestra [política de ciclo de vida del software de Adobe Commerce](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

### Si se abre un ticket de asistencia para una versión de software DESPUÉS de la fecha de finalización de la asistencia para esa versión, ¿se seguirá trabajando en la resolución?

No, Adobe Commerce no funcionará para resolver los vales de soporte que se abrieron después de la fecha de finalización de soporte para esa versión de software.
