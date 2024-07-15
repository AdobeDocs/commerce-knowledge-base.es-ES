---
title: Buscar tablas MySQL grandes
description: '"Para identificar las tablas grandes, conéctese a la base de datos como se describe en el artículo [Conectarse a la base de datos](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) y ejecute el siguiente comando, donde "project_id" es su ID de proyecto en la nube:"'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Buscar tablas MySQL grandes

Para identificar las tablas grandes, conéctese a la base de datos como se describe en el artículo [Conectarse a la base de datos](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) y ejecute el siguiente comando, donde `project_id` es su Id. de proyecto en la nube:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Esto mostraría la lista completa de tablas y su tamaño. Puede ir a través de la lista e identificar qué tablas requieren atención debido al gran tamaño.
