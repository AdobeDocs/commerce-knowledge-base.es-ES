---
title: Actualización de directiva de ciclo vital de ticket de soporte de Adobe Commerce
description: Este artículo proporciona información sobre la actualización de la directiva de ciclo vital del vale de soporte de Adobe Commerce.
exl-id: c3fbcb4a-107f-48b3-afed-b9a0c5d0425c
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Actualización de directiva de ciclo vital de ticket de soporte de Adobe Commerce

Este artículo proporciona información sobre la actualización de la directiva de ciclo vital del vale de soporte de Adobe Commerce.

La siguiente tabla ilustra los escenarios actualizados. Puede encontrar detalles para cada escenario en la sección siguiente.

<table>
 <tbody>
 <tr>
 <td class="wysiwyg-text-align-center"> </td>
 <td class="wysiwyg-text-align-center"><strong>Estado del ticket</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Días para "Resolver"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Días para "Cerrado"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Tiempo de notificación</strong></td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>El ingeniero proporciona la solución</strong></td>
 <td class="wysiwyg-text-align-center">"Esperando su respuesta"</td>
 <td class="wysiwyg-text-align-center">3</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Días 3 y 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Esperando información del cliente</strong></td>
 <td class="wysiwyg-text-align-center">"Esperando su respuesta"</td>
 <td class="wysiwyg-text-align-center">N/D</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Días 1, 3 y 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>El cliente establece en "Resuelto" o solicita al ingeniero que establezca en "Resuelto"</strong></td>
 <td class="wysiwyg-text-align-center">"Resuelto"</td>
 <td class="wysiwyg-text-align-center">Inmediato</td>
 <td class="wysiwyg-text-align-center">1</td>
 <td class="wysiwyg-text-align-center">Día 1</td>
 </tr>
 </tbody>
 </table>

## Escenarios en detalle

### Cuando un ingeniero proporciona una solución

1. Una vez que se proporciona una solución a un cliente, el ingeniero establece el estado del ticket en &quot;Esperando su respuesta&quot;.
1. Si no hay respuesta del cliente durante 3 días después de cambiar el estado a &quot;Esperando su respuesta&quot;, el ticket se mueve a &quot;Resuelto&quot; y se notifica al cliente.
1. Si no hay respuesta del cliente durante 6 días después de cambiar el estado a &quot;Esperando su respuesta&quot;, el ticket se cierra y se notifica al cliente.

### Cuando se requiera información adicional de un cliente

1. Si se requiere una actualización del cliente, el ingeniero establece el ticket en &quot;Esperando su respuesta&quot;.
1. Las notificaciones se envían al cliente el día 1 y 3 solicitando el seguimiento del cliente.
1. Si no hay respuesta del cliente durante 6 días después de cambiar el estado a &quot;Esperando su respuesta&quot;, el ticket se cierra y se notifica al cliente.

### Ticket establecido como &quot;Resuelto&quot; por un cliente

Cuando un cliente establece un ticket como &quot;Resuelto&quot;, se cierra en un día y se notifica al cliente.

### El cliente ordena al servicio de asistencia que cierre el ticket

Cuando un cliente indica al Soporte de Adobe Commerce que cierre el ticket, se cierra en un día y se notifica al cliente.

## Lectura relacionada

* [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
* [El vínculo &quot;Enviar un ticket&quot; no se muestra en la página de inicio del Centro de ayuda de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#no-submit-link)
* [Formulario de envío de tickets: el comerciante no se muestra en la lista desplegable Organización](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)
