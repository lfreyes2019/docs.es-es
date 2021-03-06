---
title: Contenedores, imágenes y registros de Docker
description: Ciclo de vida de aplicaciones de Docker en contenedor con la plataforma y las herramientas de Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: af235280c985d20f9e6a2ee6096edbe6c3aad63a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53142754"
---
# <a name="docker-containers-images-and-registries"></a>Contenedores, imágenes y registros de Docker

Cuando se usa Docker, cree una aplicación o el servicio y el paquete y sus dependencias en una imagen de contenedor. Una imagen es una representación estática de la aplicación o el servicio y de su configuración y las dependencias.

Para ejecutar la aplicación o el servicio, se crea una instancia de la imagen de la aplicación para crear un contenedor, que se ejecutará en el host de Docker. Inicialmente, los contenedores se prueban en un entorno de desarrollo o un PC.

Almacenar imágenes en un registro, que actúa como una biblioteca de imágenes. Necesita un registro cuando se implementa en orquestadores de producción. Docker mantiene un registro público a través de [Docker Hub](https://hub.docker.com/); otros proveedores ofrecen registros para distintas colecciones de imágenes. Como alternativa, las empresas pueden tener un registro privado local para sus propias imágenes de Docker.

Figura 1-4 se muestra cómo se relacionan las imágenes y los registros de Docker a otros componentes. También se muestran las diversas ofertas de registro de los proveedores.

![](./media/image4.png)

Figura 1-4: Taxonomía de términos de Docker y conceptos

Al colocar imágenes en un registro, puede almacenar fragmentos de la aplicación estáticos e inmutables, incluidas todas sus dependencias en un nivel de marco. , A continuación, puede versión e implementar imágenes en varios entornos y, por tanto, proporcionar una unidad de implementación coherente.

Registros de imágenes privados, hospedadas en local o en la nube, se recomiendan para las situaciones siguientes:

-   Las imágenes no deben compartirse públicamente por motivos de confidencialidad.

-   Quiere tener una latencia de red mínima entre las imágenes y el entorno de implementación elegido. Por ejemplo, si su entorno de producción es Azure, probablemente desee almacenar las imágenes en Azure Container Registry para que la latencia de red sea mínima. De forma similar, si el entorno de producción es local, puede tener un registro de confianza de Docker local disponible dentro de la misma red local.

>[!div class="step-by-step"]
>[Anterior](docker-terminology.md)
>[Siguiente](Docker-application-lifecycle/index.md)