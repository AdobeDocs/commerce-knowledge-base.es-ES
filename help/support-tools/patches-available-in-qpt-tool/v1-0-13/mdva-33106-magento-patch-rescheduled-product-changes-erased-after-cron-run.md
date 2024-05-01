---
title: "Parche MDVA-33106: los cambios de producto reprogramados se borran tras la ejecución de Cron"
description: El parche MDVA-33106 corrige el problema en el que los cambios reprogramados del producto se borran después del cron
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Parche MDVA-33106: los cambios de producto reprogramados se borran tras la ejecución de cron

El parche MDVA-33106 corrige el problema en el que los cambios reprogramados del producto se borran después del cron

```bash
bin/magento cron:run
```

se ejecuta el comando. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 está instalado. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. En Commerce Admin, vaya a **Catálogo** > **Productos** y haga clic en editar. Observe el **Precio** por ejemplo, *9,99*.
1. Clic **Programar nueva actualización** y rellene los detalles:
   * El nombre de la actualización no importa.
   * Establezca una fecha en el futuro, +1 año para la fecha de inicio y la fecha de finalización.
   * Establecer precio en *1,99*.
   * Guardar cambios.
1. Vaya al panel Ensayo de contenido y seleccione la vista de cuadrícula para ver si la coincidencia programada anterior.
1. Seleccione la acción de edición junto a la actualización programada. Los datos deben seguir coincidiendo con lo anterior.
1. Cambie la fecha programada por algo más cerca. En lugar de +1 año a partir de ahora, cámbielo a + 1 semana o + 1 mes.
1. Guarde los cambios y compruebe si las fechas se actualizan en el panel de ensayo.
1. Espere a que se ejecute un trabajo cron.
1. Vuelva a hacer clic en Editar en el cambio programado y compruebe el precio.

<u>Resultados esperados</u>:

El precio es de 1,99.

<u>Resultados reales</u>:

El precio es de 9,99.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
