---
title: Preguntas más frecuentes sobre la directiva de ciclo vital actualizada para las versiones de Adobe Commerce
description: '"Adobe Commerce proporciona correcciones de calidad para una versión menor durante un mínimo de 12 meses a partir de la fecha de disponibilidad general de la próxima versión menor del software. La manera en que proporcionamos correcciones de calidad durante este período está cambiando:'''
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 0%

---

# Preguntas más frecuentes sobre la directiva de ciclo vital actualizada para las versiones de Adobe Commerce

## ¿Qué está cambiando?

Adobe Commerce proporciona correcciones de calidad para una versión menor durante un mínimo de 12 meses a partir de la fecha de disponibilidad general de la próxima versión menor del software. La forma en que proporcionamos correcciones de calidad durante este período está cambiando:

* **Directiva anterior:** Actualmente las correcciones de calidad a la línea anterior que se encuentra en la ventana EOS de 12 meses se entregan a través de nuestra versión trimestral de parches, por lo tanto, haciendo que los parches trimestrales sean una combinación de seguridad + calidad.
* **Nueva directiva:** A partir de 2.4 como línea de versión secundaria más actual, las revisiones de la versión de la línea compatible anterior (2.3) pasarán a ser de solo seguridad. Seguiremos ofreciendo correcciones de calidad para la línea compatible anterior durante los 12 meses posteriores al lanzamiento de una versión menor (como 2.4) y las nuevas líneas de versión secundarias subsiguientes; pero estarán disponibles a través de la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) y se centrarán únicamente en los problemas críticos.

## ¿Cuándo entra en vigor esta política?

Adobe Commerce 2.3.6 está programado para lanzarse el 15 de octubre de 2020 y es el último parche para Adobe Commerce 2.3 que incluirá calidad y seguridad. Después de 2.3.6, la línea 2.3.x pasará a ser de solo seguridad y los problemas de calidad críticos para 2.3 se podrán solucionar mediante QPT.

>[!NOTE]
>
>La única vez que lanzaremos una versión completa de 2.3 es si necesitamos mantener la conformidad con nuestra pila de tecnología, como para PHP o Elasticsearch. Esto está ocurriendo en el segundo trimestre de 2021 con una actualización obligatoria de PHP 7.4, incrementaremos la línea a 2.3.7. Para obtener más información, consulte la [compatibilidad de PHP 7.4 con la línea de la versión Adobe Commerce 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) publicación DevBlog.

## ¿Qué es una versión de solo seguridad?

Las versiones solo de seguridad contienen correcciones de seguridad únicamente y no se ha corregido la calidad. Sin embargo, tenga en cuenta que nuestras versiones de solo seguridad pueden incluir correcciones rápidas específicas cuando las consideremos absolutamente críticas para ejecutar Adobe Commerce.

## ¿Seguirá habiendo una versión de solo seguridad para la última línea (a partir de la publicación, 2.4)?

Adobe también seguirá teniendo versiones de solo seguridad para la línea de versiones más reciente. El proceso para estos se describe en [Presentación de la nueva publicación de parches de solo seguridad](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) publicación DevBlog.

## ¿Qué es la herramienta Parches de calidad?

Consulte el artículo [Herramienta de parches de calidad lanzada: una nueva herramienta para aplicar parches de calidad de forma automática](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.

## ¿Quién debe considerar la posibilidad de utilizar esta nueva directiva?

La nueva política pretende crear vías para que los comerciantes planifiquen estratégicamente los costes anuales de desarrollo de Adobe Commerce, permitiéndoles mantener la seguridad y la calidad crítica durante estos ciclos estratégicos. También puede ser utilizado por los comerciantes que se preocupan por la seguridad sobre todo lo demás y están generalmente contentos con la estabilidad de la línea más antigua, apoyada. A los comerciantes les puede resultar más fácil planificar y presupuestar estas actualizaciones, ya que serán más predecibles.

## ¿Deben los comerciantes seguir actualizándose a la línea más reciente?

En última instancia, todos los comerciantes deben priorizar la planificación para adoptar la última línea de Adobe Commerce de forma oportuna. La nueva línea Security Only y la herramienta QPT no pretenden sustituir a la hoja de ruta estratégica de actualización para los comerciantes, sino que ofrecen flexibilidad a los comerciantes para planificar su hoja de ruta de actualización y un medio para reaccionar rápidamente a los problemas de seguridad y calidad sin tener que implementar una actualización completa.

## ¿Cómo obtendré correcciones de calidad en versiones menores compatibles que no sean la última línea?

Las correcciones estarán disponibles a través de la [herramienta Parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).

## ¿Cómo obtendré correcciones de calidad en la última línea?

La línea actual tendrá calidad como parte de la actualización trimestral. Entre versiones, si se pone en contacto con el servicio de asistencia para obtener una corrección en la línea más reciente, se suministrará a través de QPT. A continuación, una vez que actualice a la versión que tenga esa corrección, se aplicará mediante el parche trimestral.

## ¿Qué tipo de problemas de calidad se solucionarán en versiones menores compatibles que no sean la última línea?

Solo los problemas de calidad importantes que rompan los flujos principales se solucionarán en la línea anterior (2.3) y se entregarán a través de QPT.

## ¿Alguna corrección de calidad formará parte de la versión trimestral en versiones menores compatibles que no sean la última línea?

Sí, como parte de la línea de solo seguridad, lanzamos lo que el Adobe llama &quot;correcciones rápidas&quot; a esa línea; se trata de problemas muy críticos que afectan a la aplicación de Adobe Commerce.

## ¿Se ofrecerán al mismo tiempo mejoras de seguridad y QPT?

La línea de solo seguridad seguirá el calendario de versiones trimestrales y se lanzará con la nomenclatura -p1. Ejemplo 2.3.6-p1. La calidad se lanzará ad hoc a medida que se descubran y corrijan problemas de calidad, y estarán disponibles a través de QPT.

## Si tengo un problema de calidad que no se resolverá en versiones menores compatibles que no sean la última línea o QPT, ¿qué puedo hacer?

La línea anterior es solo de seguridad, lo que significa que el principal beneficio es mantenerse seguro. Solo los parches para problemas importantes que rompan los flujos principales estarán disponibles a través de QPT.

Los problemas que no afecten a los flujos principales o que tengan soluciones alternativas solo se solucionarán en la línea más reciente. El Adobe anima a aquellos que desean correcciones críticas y no críticas a pasar a la línea más reciente.

## ¿Las actualizaciones serán más costosas o difíciles para los comerciantes si permanecen en la línea de solo seguridad hasta que llegue al final de la asistencia de seguridad?

En teoría, deberían ser iguales en costo para el Comerciante en términos de horas de desarrollo, siempre y cuando no hayan adoptado un gran número de Parches de Calidad. Si un comerciante descubre que necesita o quiere más de un puñado de parches a través de la herramienta QPT, se recomienda que dé prioridad a la actualización a la última versión de Adobe Commerce. La adopción de un gran número de parches de calidad, en lugar de actualizar a la versión actual de Adobe Commerce, puede aumentar los costes de desarrollo y las complejidades de la actualización una vez que la línea de solo seguridad llega al final de la asistencia.

## ¿Por qué debería limitar la cantidad de parches de calidad entregados a través de QPT?

Al aplicar muchas correcciones de calidad individuales, puede hacer que el código de Adobe Commerce sea más complejo. La complejidad añadida podría provocar cambios impredecibles al actualizar a la línea de versión más reciente. Es por eso que recomendamos usar QPT con moderación y solo para las correcciones más críticas.

## ¿Qué sucede con el cumplimiento de las pilas de tecnología?

Durante la vida útil de una línea de lanzamiento habrá actualizaciones a varias pilas de tecnología, como PHP o Elasticsearch, que deberán actualizarse para seguir cumpliendo con las normas. Daremos la mayor notificación posible a nuestros comerciantes de que estos están llegando.

Nota: En el segundo trimestre de 2021, tendremos que actualizar PHP y Redis en la línea 2.3.x para seguir cumpliendo con las normas. Esto hará que la línea aumente a 2.3.7. Para obtener más información, consulte la [compatibilidad de PHP 7.4 con la línea de la versión Adobe Commerce 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) publicación DevBlog.
