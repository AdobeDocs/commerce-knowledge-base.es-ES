---
title: Contraseñas de administrador guardadas como texto sin formato en el registro de acciones
description: Este artículo proporciona una corrección para el caso de que un administrador de Commerce cree un nuevo usuario con privilegios de administrador y la contraseña se guarde como texto sin formato en la tabla de base de datos magento_logging_event_changes.
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Contraseñas de administrador guardadas como texto sin formato en el registro de acciones

Este artículo proporciona una corrección cuando un administrador de Commerce crea un nuevo usuario con privilegios de administrador y la contraseña se guarda como texto sin formato en la `magento_logging_event_changes` tabla de base de datos.

Para solucionar este problema de seguridad, instale la actualización de seguridad de Adobe Commerce 2.0.16 y 2.1.9. Después de aplicar la actualización de seguridad, las contraseñas se cifran y no aparecen como texto sin formato.

## Versiones afectadas {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce local 2.X.X
* Adobe Commerce en infraestructura en la nube 2.X.X

## Problema {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Cuando un administrador de Commerce existente crea un nuevo usuario con privilegios de administrador mediante **Sistema** > **Permisos** > **Todos los usuarios** > **Añadir nuevo usuario**, la contraseña (introducida como confirmación) se guarda como texto sin formato en la `magento_logging_event_changes` tabla de base de datos.

### Pasos a seguir: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Inicie sesión como administrador y cree un nuevo usuario navegando a esta ruta: **Sistema** > Permisos > **Todos los usuarios**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Luego haga clic en **Añadir nuevo usuario** página. Proporcione la contraseña de administrador actual cuando se le solicite.
1. Vaya a la **Sistema** > **Registro de acciones** > **Informe** y busque la última entrada de registro.
1. Puede ver la contraseña actual, ni cifrada ni con hash.

## Solución {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

Instalación del [Actualización de seguridad de Adobe Commerce 2.0.16 y 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) corrige este problema.

Después de instalar la actualización de seguridad, la contraseña se cifra y no aparece en texto sin formato en `magento_logging_event_changes` tabla.

## Más información {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

[Página de actualización de seguridad de Adobe Commerce 2.0.16 y 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) en nuestro centro de seguridad.

[Actualización de la aplicación y los componentes de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) en nuestra documentación para desarrolladores.
