---
title: Amortización de las integraciones de pagos de Core Adobe Commerce
description: Debido a la Directiva sobre servicios de pago PSD 2 (consulte los detalles sobre [Directiva sobre servicios de pago](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html?lang=es) en nuestra guía del usuario) y a la continua evolución de muchas API, varias integraciones de pagos principales de Adobe Commerce corren el riesgo de quedar obsoletas y dejar de ser compatibles con la seguridad en el futuro. Con este fin, muchas integraciones de pago básicas han quedado o quedarán obsoletas en breve, y recomendamos la transición a sus correspondientes extensiones de Commerce Marketplace. Lea el resto del artículo siguiente para revisar los casos recientes de desaprobación de las integraciones de pagos. Cada uno de los vínculos **Status** se encuentra en nuestra guía del usuario. **Las integraciones siguientes se eliminarán de la versión 2.4.0 de Adobe Commerce y quedarán obsoletas en las versiones 2.3.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Amortización de las integraciones de pagos de Core Adobe Commerce

Debido al PSD de la Directiva sobre servicios de pago2 (consulte los detalles sobre la [Directiva sobre servicios de pago](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html?lang=es) en nuestra guía del usuario) y a la continua evolución de muchas API, varias integraciones de pagos principales de Adobe Commerce corren el riesgo de quedar obsoletas y dejar de ser compatibles con la seguridad en el futuro. Con este fin, muchas integraciones de pago básicas han quedado o quedarán obsoletas en breve, y recomendamos la transición a sus correspondientes extensiones de Commerce Marketplace. Lea el resto del artículo siguiente para revisar los casos recientes de desaprobación de las integraciones de pagos. Cada uno de los vínculos **Status** se encuentra en nuestra guía del usuario. **Las integraciones siguientes se eliminarán de la versión 2.4.0 de Adobe Commerce y quedarán obsoletas de las versiones 2.3.**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>Integración de métodos de pago</strong></td>
<td style="width: 226.364px;"><strong>Estado</strong></td>
<td style="width: 226.364px;"><strong>Recomendación de Adobe Commerce 2.X</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=es#recommended-solutions">Obsoleto desde la versión 2.3.5</a><br>2.4.0: se eliminará por completo</td>
<td style="width: 226.364px;">Pregunte a su proveedor de pagos qué solución recomienda para cumplir con los requisitos de PSD2.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=es#recommended-solutions">Obsoleto desde la versión 2.3.4</a><br>2.4.0: se eliminará por completo</td>
<td style="width: 226.364px;">En su lugar, use la <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">extensión oficial</a> del Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (Direct Post)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=es#recommended-solutions">Obsoleto desde la versión 2.3.1</a><br>2.4.0: se eliminará por completo</td>
<td style="width: 226.364px;">En su lugar, use la <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">extensión oficial</a> del Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">CyberSource</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=es#recommended-solutions">Obsoleto desde la versión 2.3.3</a><br>2.4.0: se eliminará por completo</td>
<td style="width: 226.364px;">En su lugar, use la <a href="https://marketplace.magento.com/cybersource-global-payment-management.html">extensión oficial</a> del Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=es#recommended-solutions">Obsoleto desde la versión 2.3.3</a><br>2.4.0: se eliminará por completo</td>
<td style="width: 226.364px;">Pregunte a su proveedor de pagos qué solución recomienda para cumplir con los requisitos de PSD2.</td>
</tr>
</tbody>
</table>

**Tenga en cuenta que la integración del método de pago principal de PayPal no quedará obsoleta ni se eliminará y seguirá siendo compatible con todas las versiones de 2.3.x y 2.4.x.**

## Cómo mantener sus pagos seguros en adelante

Para todas las implementaciones de Adobe Commerce y Magento Open Source que aún utilizan integraciones de pago obsoletas, siga las recomendaciones a continuación para asegurarse de que los pagos de sus clientes sean seguros, de que no se rechacen pagos y para prepararse para la actualización a Adobe Commerce 2.4.0:

* Instale y configure la extensión oficial del método de pago desde [Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043) tal como se menciona en la tabla anterior.
* Deshabilite las integraciones de pago en desuso en Administración (establezca la opción de configuración **Enabled** en *No* ) para que ya no se muestren en la tienda como opciones de pago. Asegúrese de que todos los pedidos nuevos se paguen a través de la integración de la extensión en su lugar.
* Debido a que la nueva integración de Commerce Marketplace no podrá procesar las transacciones de pago realizadas mediante una integración de pago obsoleta, recomendamos utilizar ambos métodos de pago durante un periodo en paralelo; pero solo para la finalización de transacciones ya registradas y posibles reembolsos. Para ello, mantenga desactivado el método de pago obsoleto, pero deje rellenados todos los campos de configuración.
