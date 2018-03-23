---
title: -refout (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6075b92efd1eec9797fca248e97a325bd5df4bb
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/23/2018
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="9e577-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e577-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="9e577-103">La opción **-refout** especifica una ruta de archivo donde el ensamblado de referencia debe mostrarse.</span><span class="sxs-lookup"><span data-stu-id="9e577-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="9e577-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9e577-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="9e577-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="9e577-105">Arguments</span></span>

 <span data-ttu-id="9e577-106">`filepath` La ruta de acceso y el nombre del ensamblado de referencia.</span><span class="sxs-lookup"><span data-stu-id="9e577-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="9e577-107">Debe estar en una subcarpeta del ensamblado principal.</span><span class="sxs-lookup"><span data-stu-id="9e577-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="9e577-108">La convención recomendada (que se usa por MSBuild) es colocar el ensamblado de referencia en una subcarpeta "ref/" con relación al ensamblado principal.</span><span class="sxs-lookup"><span data-stu-id="9e577-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="9e577-109">Todas las carpetas de `filepath` debe existir; el compilador no los crea.</span><span class="sxs-lookup"><span data-stu-id="9e577-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="9e577-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="9e577-110">Remarks</span></span>

<span data-ttu-id="9e577-111">Visual Basic admite la `-refout` conmutador a partir de la versión 15.3.</span><span class="sxs-lookup"><span data-stu-id="9e577-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="9e577-112">Ensamblados de referencia son solo metadatos ensamblados que contienen metadatos pero ningún código de implementación.</span><span class="sxs-lookup"><span data-stu-id="9e577-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="9e577-113">Incluyen información de los tipos y miembros para todo excepto los tipos anónimos.</span><span class="sxs-lookup"><span data-stu-id="9e577-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="9e577-114">Los cuerpos de método se reemplazan con una sola `throw null` instrucción.</span><span class="sxs-lookup"><span data-stu-id="9e577-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="9e577-115">La razón para usar `throw null` cuerpos de método (en contraposición a ningún cuerpos) es para que pueda ejecutar y pasar (, por tanto, validar la integridad de los metadatos) PEVerify.</span><span class="sxs-lookup"><span data-stu-id="9e577-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="9e577-116">Ensamblados de referencia incluyen un nivel de ensamblado [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atributo.</span><span class="sxs-lookup"><span data-stu-id="9e577-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="9e577-117">Este atributo puede especificarse en el origen (por lo tanto, el compilador no necesitará sintetizarlo).</span><span class="sxs-lookup"><span data-stu-id="9e577-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="9e577-118">Debido a este atributo, rechazan tiempos de ejecución cargar los ensamblados de referencia para la ejecución (pero todavía se pueden cargar en un contexto de solo reflexión).</span><span class="sxs-lookup"><span data-stu-id="9e577-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="9e577-119">Herramientas que se reflejan en los ensamblados deben asegurarse de que se cargan los ensamblados de referencia como de solo reflexión; en caso contrario, el runtime produce una <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="9e577-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="9e577-120">Las opciones `-refout` y [`-refonly`](refonly-compiler-option.md) son mutuamente excluyentes.</span><span class="sxs-lookup"><span data-stu-id="9e577-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e577-121">Vea también</span><span class="sxs-lookup"><span data-stu-id="9e577-121">See Also</span></span>
<span data-ttu-id="9e577-122">[-refonly](refonly-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="9e577-122">[-refonly](refonly-compiler-option.md) </span></span>  
[<span data-ttu-id="9e577-123">Compilador de línea de comandos de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e577-123">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="9e577-124">Líneas de comandos de compilación de ejemplo</span><span class="sxs-lookup"><span data-stu-id="9e577-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)  
