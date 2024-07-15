---
title: Diagnóstico de discrepancias de ingresos de Google eCommerce
description: '''Este artículo proporciona soluciones para discrepancias entre Google y Magento Business Intelligence (MBI). El seguimiento del comercio electrónico de Google potencia tanto su cuenta de Google Analytics como sus paneles de MBI, pero hace que muchos clientes nos pregunten: ¿Deberían ambas herramientas informar de la misma cantidad de **pedidos** e **ingresos"**?'
exl-id: b2e43e70-d234-4338-ae81-fa401416be5a
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Diagnóstico de discrepancias de ingresos de Google eCommerce

Este artículo proporciona soluciones para las discrepancias entre Google y Magento Business Intelligence (MBI). El seguimiento del comercio electrónico de Google potencia tanto su cuenta de Google Analytics como sus paneles de MBI, pero hace que muchos clientes nos pregunten: ¿Deberían ambas herramientas informar de la misma cantidad de **pedidos** e **ingresos**?

En nuestra experiencia, la respuesta es &quot;no&quot; en casi todos los casos. Esto se debe a que el seguimiento de Google eCommerce obtiene la información del pedido durante un evento de clic en el botón del sitio web, lo que omite muchos atributos de pedido registrados posteriormente en la base de datos, desde pedidos no registrados hasta cancelaciones o reembolsos posteriores.

Sabemos que una discrepancia entre Google y MBI puede causar incertidumbre para usted y su equipo. Queremos ayudarle a comprender la diferencia entre estos dos números, lo que podría revelar ajustes que se deben realizar en su cuenta o base de datos de Google.

## ¿Por qué GA informa de **menos** ingresos que mi base de datos?

Cuando los Google Analytics informan de forma insuficiente de los pedidos y los ingresos, esto indica que no está capturando todos los pedidos que se realizan en el sitio. Como sabe que los datos de la base de datos son el número definitivo, puede realizar algunos pasos para intentar determinar la causa raíz y posiblemente ayudar a Google a capturar más información.

* No siempre ha tenido habilitado el seguimiento del comercio electrónico de Google. Intente ver un período más reciente y más pequeño.
* El seguimiento de comercio electrónico de Google no está configurado para capturar compras de ciertos navegadores, sistemas operativos o dispositivos.
* El evento de clics asociado con el seguimiento de su Google eCommerce no realiza un seguimiento correcto de los impuestos, el envío u otros cargos por encima del total del pedido.
* La marca de tiempo de la base de datos está en una zona horaria diferente a la de los Google Analytics.
* Las personas pueden visitar el sitio a través de ventanas de incógnito o con las cookies desactivadas.

## ¿Por qué GA informa de **más** ingresos que mi base de datos?

Hemos descubierto que es más común que los Google Analytics informen en exceso de pedidos e ingresos en comparación con una base de datos de comercio electrónico. Esto no siempre es algo malo. Su base de datos es el registro definitivo de transacciones realizadas en su sitio web y hay varias razones por las que Google podría estar informando alto incluso cuando lo ha configurado perfectamente:

* El seguimiento del comercio electrónico captura los clics en botones duplicados y solo se registra como un único pedido en la base de datos.
* Tiene un número elevado de pedidos cancelados, reembolsados o fraudulentos, lo que es un cambio de estado que se produce después de que eCommerce rastree los datos.
* Las métricas **Ingresos** y **Pedidos** excluyen deliberadamente pedidos internos o de prueba, que Google no puede diferenciar.
* Los pedidos no se pueden realizar en la base de datos en determinadas circunstancias.
* El seguimiento de comercio electrónico de Google no tiene en cuenta los cupones y descuentos del pedido.
* La marca de tiempo de la base de datos está en una zona horaria diferente a la de los Google Analytics.

Recuerde, aunque Google genere un número mayor que el de la base de datos, es probable que aún falten algunos pedidos por los motivos detallados en la sección anterior.

## Resolución de problemas

* Cree un clon de su métrica **Ingresos** sin filtros que restrinjan el resultado. Los filtros Pedidos que contamos o Clientes que contamos son importantes, pero Google no tiene un filtro equivalente.
* Auditar un período reciente pequeño, como un lapso de unas pocas horas a principios de esta semana.
* Una vez configurado el seguimiento del comercio electrónico de Google en MBI, utilice Filtro o Agrupar por para auditar un único Source, Medium o Campaign. A continuación, haga lo mismo en Google. Una fuente con menos tráfico/ingresos será mejor, ya que es como tener menos margen de error.
