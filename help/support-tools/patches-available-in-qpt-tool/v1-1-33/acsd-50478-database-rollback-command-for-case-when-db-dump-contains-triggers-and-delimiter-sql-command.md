---
title: "ACSD-50478: Problema de JS para la acción de reversión en la cuadrícula de copias de seguridad y el comando de reversión de base de datos"
description: Aplique el parche ACSD-50478 para corregir el problema de JS para la acción de reversión en la cuadrícula de copias de seguridad y el comando de reversión de la base de datos para un caso en el que el volcado de la base de datos contenga déclencheur y un comando SQL *delimiter*.
exl-id: 8b516705-29be-462e-b3ec-3a339b6e8006
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-50478: problema de JS para la acción de reversión en la cuadrícula de copias de seguridad y el comando de reversión de base de datos

El parche ACSD-50478 corrige el problema de JS para la acción de reversión en la cuadrícula de copias de seguridad y el comando de reversión de la base de datos para un caso en el que el volcado de la base de datos contiene déclencheur y un *delimitador* Comando SQL. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. El ID del parche es ACSD-50478. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Problema de JS para la acción de reversión en la cuadrícula Copias de seguridad y el comando de reversión de la base de datos para un caso en el que el volcado de la base de datos contiene déclencheur y un *delimitador* Comando SQL.

<u>Pasos a seguir</u>:

1. Establecer indizadores en [!UICONTROL Update on Schedule] modo para que los déclencheur se creen en la base de datos.
1. Habilite la funcionalidad de copia de seguridad desde la línea de comandos:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Ir a **Sistema** > **Herramientas** > **Copias de seguridad** y generar una copia de seguridad de BD.
1. Abra la consola del explorador y verá el siguiente error:

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Intente importar la base de datos desde la línea de comandos:

   `bin/magento setup:rollback --db-file="<filename>"`

1. Aparece el siguiente error:

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Resultados esperados</u>:

La restauración de la base de datos se realiza correctamente desde la línea de comandos y desde el administrador.

<u>Resultados reales</u>:

Ha observado los errores mencionados en los pasos 4 y 6.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
