---
title: Método SqlStreamChars.Write (Char [], Int32, Int32) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: dd9bb691f6d07f4875d684eef76d6329667003af
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221913"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>Método SqlStreamChars.Write (Char [], Int32, Int32)

Cuando se invalida en una clase derivada, escribe una secuencia de caracteres en la secuencia actual y avanza la posición actual dentro de la secuencia según el número de caracteres escritos. El ensamblado que contiene este método tiene una relación de confianza con SQLAccess.dll. Está pensado para su uso con SQL Server. Para otras bases de datos, utilice el mecanismo de hospedaje proporcionado por esa base de datos.

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parámetros

`buffer`  
Para escribir una matriz de char.

`offset`  
Un desplazamiento con respecto al origen.

`count`  
El número de caracteres que se escribirá en la secuencia actual.

## <a name="remarks"></a>Comentarios

> [!WARNING]
> El `SqlStreamChars.Write` método es privado y no está pensado para usarse directamente en el código.
>
> Microsoft no admite el uso de este campo en una aplicación de producción bajo ninguna circunstancia.

## <a name="requirements"></a>Requisitos

**Espacio de nombres:** <xref:System.Data.SqlTypes>

**Ensamblado:** System.Data (en System.Data.dll)

**Versiones de .NET framework:** Disponible desde la versión 2.0.