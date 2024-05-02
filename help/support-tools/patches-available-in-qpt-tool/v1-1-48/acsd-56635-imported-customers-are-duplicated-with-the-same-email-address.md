---
title: '"ACSD-56635: Los clientes importados se duplican cuando el uso compartido de cuentas se establece en [!DNL Global]'''
description: Aplique el parche ACSD-56635 para solucionar el problema de Adobe Commerce en el que el cliente importado se duplica con la misma dirección de correo electrónico cuando la importación se utiliza con el uso compartido de cuentas establecido en [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: 86d752c9c2791ef19960876afafe24fefe5d29ed
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: los clientes importados se duplican con la misma dirección de correo electrónico cuando el uso compartido de cuentas se establece en [!DNL Global]

El parche ACSD-56635 corrige el problema en el que el cliente importado se duplica con la misma dirección de correo electrónico cuando la importación se utiliza con el uso compartido de cuentas establecido en [!DNL Global]. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. El ID del parche es ACSD-56635. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes importados se duplican con la misma dirección de correo electrónico cuando el uso compartido de cuentas se establece en [!DNL Global].

<u>Pasos a seguir</u>:

1. En Adobe Commerce (2.4: desarrollo de b2b) **[!UICONTROL Admin]**, acceso **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Configure las variables *[!UICONTROL Share Customer Accounts]* configurando en *[!DNL Global]*.
1. Crear varios sitios web y tiendas:

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Cree un nuevo cliente en *sitio web principal* de administrador con dirección de correo electrónico utilizada como <adb@yormail.com>.
1. En **[!UICONTROL Admin]**, vaya a **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Seleccionar **[!UICONTROL Customer Entity Type]** as *[!UICONTROL Customers Main File]*.
1. Utilice la misma dirección de correo electrónico que <adb@yormail.com> en otro sitio web, por ejemplo, ws1. Consulte el archivo CSV de ejemplo customer.csv, que aparece a continuación.
1. Complete la importación para ver el nuevo usuario creado en *ws1* con la misma dirección de correo electrónico.

contenido de customer.csv:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Resultados esperados</u>:

Se actualiza el cliente importado con la misma dirección de correo electrónico en lugar de duplicarlo.

<u>Resultados reales</u>:

Los clientes duplicados se crean con la misma dirección de correo electrónico al utilizar la importación de clientes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
