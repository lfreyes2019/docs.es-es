---
title: Opciones de F# Interactive
description: "Obtenga información acerca de las opciones de línea de comandos compatibles con F # Interactive, fsi.exe."
keywords: "visual f#, f#, programación funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9f3e39b-ce6c-41ff-991f-0625f46441ae
ms.openlocfilehash: a9b36a12aa9ffcfa26ea50d72d018a25f5f65243
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="f-interactive-options"></a><span data-ttu-id="b83cc-104">Opciones de F# Interactive</span><span class="sxs-lookup"><span data-stu-id="b83cc-104">F# Interactive Options</span></span>

> [!NOTE]
<span data-ttu-id="b83cc-105">En este artículo actualmente solo se describe la experiencia para Windows.</span><span class="sxs-lookup"><span data-stu-id="b83cc-105">This article currently describes the experience for Windows only.</span></span>  <span data-ttu-id="b83cc-106">Se reescribirá.</span><span class="sxs-lookup"><span data-stu-id="b83cc-106">It will be rewritten.</span></span>

<span data-ttu-id="b83cc-107">En este tema se describe las opciones de línea de comandos compatibles con F # Interactive, `fsi.exe`.</span><span class="sxs-lookup"><span data-stu-id="b83cc-107">This topic describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="b83cc-108">F # Interactive acepta muchas de las mismas opciones de línea de comandos que el compilador de F #, pero también acepta algunas opciones adicionales.</span><span class="sxs-lookup"><span data-stu-id="b83cc-108">F# Interactive accepts many of the same command line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="using-f-interactive-for-scripting"></a><span data-ttu-id="b83cc-109">Uso de F # Interactive para secuencias de comandos</span><span class="sxs-lookup"><span data-stu-id="b83cc-109">Using F# Interactive for Scripting</span></span>
<span data-ttu-id="b83cc-110">F # Interactive, `fsi.exe`, se puede iniciar de forma interactiva, o se puede iniciar desde la línea de comandos para ejecutar un script.</span><span class="sxs-lookup"><span data-stu-id="b83cc-110">F# Interactive, `fsi.exe`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="b83cc-111">La sintaxis de línea de comandos es</span><span class="sxs-lookup"><span data-stu-id="b83cc-111">The command line syntax is</span></span>

```
> fsi.exe [options] [ script-file [arguments] ]
```

<span data-ttu-id="b83cc-112">La extensión de archivo para archivos de script de F # es `.fsx`.</span><span class="sxs-lookup"><span data-stu-id="b83cc-112">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="b83cc-113">Tabla de opciones de F # Interactive</span><span class="sxs-lookup"><span data-stu-id="b83cc-113">Table of F# Interactive Options</span></span>
<span data-ttu-id="b83cc-114">En la tabla siguiente se resume las opciones admitidas por F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="b83cc-114">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="b83cc-115">Puede establecer estas opciones en la línea de comandos o mediante el IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b83cc-115">You can set these options on the command-line or through the Visual Studio IDE.</span></span> <span data-ttu-id="b83cc-116">Para establecer estas opciones en el IDE de Visual Studio, abra el **herramientas** menú, seleccione **opciones...** , a continuación, expanda el **herramientas de F #** nodo y seleccione **F # Interactive**.</span><span class="sxs-lookup"><span data-stu-id="b83cc-116">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options...**, then expand the **F# Tools** node and select **F# Interactive**.</span></span>

<span data-ttu-id="b83cc-117">Si aparecen listas de argumentos de la opción de F # Interactive, elementos de lista están separados por punto y coma (`;`).</span><span class="sxs-lookup"><span data-stu-id="b83cc-117">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="b83cc-118">Opción</span><span class="sxs-lookup"><span data-stu-id="b83cc-118">Option</span></span>|<span data-ttu-id="b83cc-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="b83cc-119">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="b83cc-120">Se utiliza para indicar a F # Interactive que debe tratar los argumentos restantes como argumentos de línea de comandos para el programa en F # o el script que puede tener acceso en el código mediante el uso de la lista **fsi.CommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="b83cc-120">Used to instruct F# Interactive to treat remaining arguments as command line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="b83cc-121">**--comprobar**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-121">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="b83cc-122">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-123">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-123">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-124">**--la página de códigos:&lt;int&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-124">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="b83cc-125">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-125">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-126">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-126">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-127">**--crossoptimize**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-127">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="b83cc-128">Habilitar o deshabilitar las optimizaciones entre módulos.</span><span class="sxs-lookup"><span data-stu-id="b83cc-128">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="b83cc-129">**--depurar**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-129">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="b83cc-130">**--depurar:**[**completa**&#124; **pdbonly**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-130">**--debug:**[**full**&#124;**pdbonly**]</span></span><br /><br /><span data-ttu-id="b83cc-131">**-g**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-131">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="b83cc-132">**-g:**[**completa**&#124; **pdbonly**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-132">**-g:**[**full**&#124;**pdbonly**]</span></span>|<span data-ttu-id="b83cc-133">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-133">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-134">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-134">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-135">**--definir:&lt;cadena&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-135">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="b83cc-136">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-136">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-137">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-137">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-138">**--exec**</span><span class="sxs-lookup"><span data-stu-id="b83cc-138">**--exec**</span></span>|<span data-ttu-id="b83cc-139">Indica a F # interactive se cierre después de cargar los archivos o ejecutar el archivo de script proporcionado en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="b83cc-139">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="b83cc-140">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="b83cc-140">**--fullpaths**</span></span>|<span data-ttu-id="b83cc-141">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-141">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-142">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-142">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-143">**--gui**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-143">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="b83cc-144">Habilita o deshabilita el bucle de eventos de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b83cc-144">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="b83cc-145">El valor predeterminado está habilitado.</span><span class="sxs-lookup"><span data-stu-id="b83cc-145">The default is enabled.</span></span>|
|<span data-ttu-id="b83cc-146">**--Ayuda**</span><span class="sxs-lookup"><span data-stu-id="b83cc-146">**--help**</span></span><br /><br /><span data-ttu-id="b83cc-147">**-?**</span><span class="sxs-lookup"><span data-stu-id="b83cc-147">**-?**</span></span>|<span data-ttu-id="b83cc-148">Se usa para mostrar la sintaxis de línea de comandos y una breve descripción de cada opción.</span><span class="sxs-lookup"><span data-stu-id="b83cc-148">Used to display the command line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="b83cc-149">**--lib:&lt;lista de carpetas&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-149">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="b83cc-150">**-I:&lt;lista de carpetas&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-150">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="b83cc-151">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-151">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-152">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-152">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-153">**--cargar:&lt;nombre de archivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-153">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="b83cc-154">Compila el código de origen especificado en el inicio y carga las construcciones de F # compiladas en la sesión.</span><span class="sxs-lookup"><span data-stu-id="b83cc-154">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span> <span data-ttu-id="b83cc-155">Si el origen de destino contiene directivas de secuencias de comandos como **#use** o **#load**, a continuación, debe usar **--utilizar** o **#use** en lugar de **--cargar** o **#load**.</span><span class="sxs-lookup"><span data-stu-id="b83cc-155">If the target source contains scripting directives such as **#use** or **#load**, then you must use **--use** or **#use** instead of **--load** or **#load**.</span></span>|
|<span data-ttu-id="b83cc-156">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="b83cc-156">**--mlcompatibility**</span></span>|<span data-ttu-id="b83cc-157">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-157">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-158">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-158">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-159">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="b83cc-159">**--noframework**</span></span>|<span data-ttu-id="b83cc-160">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-160">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-161">Para obtener más información, vea [opciones del compilador](../../language-reference/compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="b83cc-161">For more information, see [Compiler Options](../../language-reference/compiler-options.md)</span></span>|
|<span data-ttu-id="b83cc-162">**nologo:**</span><span class="sxs-lookup"><span data-stu-id="b83cc-162">**--nologo**</span></span>|<span data-ttu-id="b83cc-163">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-163">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-164">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-164">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-165">**--nowarn:&lt;lista de advertencias&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-165">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="b83cc-166">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-166">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-167">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-167">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-168">**--optimizar**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-168">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="b83cc-169">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-169">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-170">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-170">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-171">**--silencioso**</span><span class="sxs-lookup"><span data-stu-id="b83cc-171">**--quiet**</span></span>|<span data-ttu-id="b83cc-172">Suprimir la salida de F # Interactive a la **stdout** secuencia.</span><span class="sxs-lookup"><span data-stu-id="b83cc-172">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="b83cc-173">**--cotizaciones de depuración**</span><span class="sxs-lookup"><span data-stu-id="b83cc-173">**--quotations-debug**</span></span>|<span data-ttu-id="b83cc-174">Especifica que se debería emitir la información de depuración adicional para las expresiones que se derivan de literales de expresión de código delimitada de F # y reflejan las definiciones.</span><span class="sxs-lookup"><span data-stu-id="b83cc-174">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="b83cc-175">La información de depuración se agrega a los atributos personalizados de un nodo de árbol de expresión de F #.</span><span class="sxs-lookup"><span data-stu-id="b83cc-175">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="b83cc-176">Vea [expresiones de código delimitadas](../../language-reference/code-quotations.md) y [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span><span class="sxs-lookup"><span data-stu-id="b83cc-176">See [Code Quotations](../../language-reference/code-quotations.md) and [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span></span>|
|<span data-ttu-id="b83cc-177">**--readline**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-177">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="b83cc-178">Habilitar o deshabilitar la finalización con tabulación en modo interactivo.</span><span class="sxs-lookup"><span data-stu-id="b83cc-178">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="b83cc-179">**--referencia:&lt;nombre de archivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-179">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="b83cc-180">**-r:&lt;nombre de archivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-180">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="b83cc-181">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-181">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-182">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-182">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-183">**--tailcalls**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-183">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="b83cc-184">Habilitar o deshabilitar el uso de la instrucción de IL final, lo que hace que el marco de pila para reutilizarse en funciones recursivas de cola.</span><span class="sxs-lookup"><span data-stu-id="b83cc-184">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="b83cc-185">Esta opción está habilitada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="b83cc-185">This option is enabled by default.</span></span>|
|<span data-ttu-id="b83cc-186">**--utilizar:&lt;nombre de archivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-186">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="b83cc-187">Indica al intérprete que utilice el archivo especificado en el inicio como entrada inicial.</span><span class="sxs-lookup"><span data-stu-id="b83cc-187">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="b83cc-188">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="b83cc-188">**--utf8output**</span></span>|<span data-ttu-id="b83cc-189">Igual que la opción del compilador fsc.exe.</span><span class="sxs-lookup"><span data-stu-id="b83cc-189">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="b83cc-190">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-190">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-191">**--Advertir:&lt;nivel de advertencia&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-191">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="b83cc-192">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-192">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-193">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-193">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-194">**--warnaserror**[**+**&#124; **-**]</span><span class="sxs-lookup"><span data-stu-id="b83cc-194">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="b83cc-195">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-195">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-196">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-196">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|
|<span data-ttu-id="b83cc-197">**--warnaserror**[**+**&#124; **-** ]:**&lt;int-list&gt;**</span><span class="sxs-lookup"><span data-stu-id="b83cc-197">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="b83cc-198">Igual que el **fsc.exe** opción del compilador.</span><span class="sxs-lookup"><span data-stu-id="b83cc-198">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="b83cc-199">Para obtener más información, consulte [Opciones del compilador](../../language-reference/compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-199">For more information, see [Compiler Options](../../language-reference/compiler-options.md).</span></span>|

## <a name="related-topics"></a><span data-ttu-id="b83cc-200">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="b83cc-200">Related Topics</span></span>

|<span data-ttu-id="b83cc-201">Título</span><span class="sxs-lookup"><span data-stu-id="b83cc-201">Title</span></span>|<span data-ttu-id="b83cc-202">Descripción</span><span class="sxs-lookup"><span data-stu-id="b83cc-202">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="b83cc-203">Opciones del compilador</span><span class="sxs-lookup"><span data-stu-id="b83cc-203">Compiler Options</span></span>](../../language-reference/compiler-options.md)|<span data-ttu-id="b83cc-204">Describe las opciones de línea de comandos disponibles para el compilador de F #, **fsc.exe**.</span><span class="sxs-lookup"><span data-stu-id="b83cc-204">Describes command line options available for the F# compiler, **fsc.exe**.</span></span>|