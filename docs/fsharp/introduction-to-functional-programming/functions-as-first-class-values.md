---
title: Funciones como valores de primera clase (F#)
description: "Obtenga información acerca de cómo se elevan funciones al estado de primera clase en el lenguaje de programación de F #."
keywords: "visual f#, f#, programación funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="fdd77-104">Funciones como valores de primera clase</span><span class="sxs-lookup"><span data-stu-id="fdd77-104">Functions as First-Class Values</span></span>

<span data-ttu-id="fdd77-105">Los lenguajes de programación funcional se caracterizan principalmente por tratar las funciones como valores de primera clase.</span><span class="sxs-lookup"><span data-stu-id="fdd77-105">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="fdd77-106">El usuario podrá hacer con las funciones todo lo que se puede hacer con los valores de los otros tipos integrados y, además, con un esfuerzo comparable.</span><span class="sxs-lookup"><span data-stu-id="fdd77-106">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="fdd77-107">Entre los criterios más comunes para determinar si los valores son de primera clase se encuentran los siguientes:</span><span class="sxs-lookup"><span data-stu-id="fdd77-107">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="fdd77-108">¿Puede enlazar funciones a los identificadores de?</span><span class="sxs-lookup"><span data-stu-id="fdd77-108">Can you bind functions to identifiers?</span></span> <span data-ttu-id="fdd77-109">¿Es decir, puede que les dé nombres?</span><span class="sxs-lookup"><span data-stu-id="fdd77-109">That is, can you give them names?</span></span>

- <span data-ttu-id="fdd77-110">¿Puede almacenar las funciones en las estructuras de datos, como en una lista?</span><span class="sxs-lookup"><span data-stu-id="fdd77-110">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="fdd77-111">¿Puede pasar una función como argumento en una llamada de función?</span><span class="sxs-lookup"><span data-stu-id="fdd77-111">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="fdd77-112">¿Puede devolver una función de una llamada de función?</span><span class="sxs-lookup"><span data-stu-id="fdd77-112">Can you return a function from a function call?</span></span>

<span data-ttu-id="fdd77-113">Los dos últimos criterios definen lo que se conoce como *operaciones de orden superior* o *funciones de orden superior*.</span><span class="sxs-lookup"><span data-stu-id="fdd77-113">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="fdd77-114">Las funciones de orden superior aceptan otras funciones como argumentos y devuelven funciones como valores de llamadas de función.</span><span class="sxs-lookup"><span data-stu-id="fdd77-114">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="fdd77-115">Estas operaciones son compatibles con los principales pilares de la programación funcional, a saber, las funciones de asignación y la composición de funciones.</span><span class="sxs-lookup"><span data-stu-id="fdd77-115">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="fdd77-116">Asignar un nombre al valor</span><span class="sxs-lookup"><span data-stu-id="fdd77-116">Give the Value a Name</span></span>

<span data-ttu-id="fdd77-117">Si una función es un valor de primera clase, debe ser posible asignarle un nombre al igual que en el caso de enteros, cadenas y otros tipos integrados.</span><span class="sxs-lookup"><span data-stu-id="fdd77-117">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="fdd77-118">En la programación funcional, esto se denomina "enlazar un identificador a un valor".</span><span class="sxs-lookup"><span data-stu-id="fdd77-118">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="fdd77-119">F # utiliza [ `let` enlaces](../language-reference/functions/let-bindings.md) para enlazar nombres a valores: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-119">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="fdd77-120">En el código siguiente, se muestran dos ejemplos:</span><span class="sxs-lookup"><span data-stu-id="fdd77-120">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="fdd77-121">La asignación de un nombre a una función es así de sencilla.</span><span class="sxs-lookup"><span data-stu-id="fdd77-121">You can name a function just as easily.</span></span> <span data-ttu-id="fdd77-122">En el ejemplo siguiente se define una función denominada `squareIt` por el identificador de enlace `squareIt` a la [expresión lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-122">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="fdd77-123">La función `squareIt` tiene un parámetro, `n`, y devuelve el cuadrado de ese parámetro.</span><span class="sxs-lookup"><span data-stu-id="fdd77-123">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="fdd77-124">F# proporciona la siguiente sintaxis más concisa para lograr el mismo resultado.</span><span class="sxs-lookup"><span data-stu-id="fdd77-124">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="fdd77-125">En los siguientes ejemplos, se usa principalmente el primer estilo, `let <function-name> = <lambda-expression>`, para recalcar las similitudes entre la declaración de funciones y la declaración de otros tipos de valores.</span><span class="sxs-lookup"><span data-stu-id="fdd77-125">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="fdd77-126">Sin embargo, todas las funciones con nombre también se pueden escribir mediante la sintaxis concisa.</span><span class="sxs-lookup"><span data-stu-id="fdd77-126">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="fdd77-127">Algunos de los ejemplos se han escrito de ambas formas.</span><span class="sxs-lookup"><span data-stu-id="fdd77-127">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="fdd77-128">Almacenar el valor en una estructura de datos</span><span class="sxs-lookup"><span data-stu-id="fdd77-128">Store the Value in a Data Structure</span></span>

<span data-ttu-id="fdd77-129">Un valor de primera clase puede almacenarse en una estructura de datos.</span><span class="sxs-lookup"><span data-stu-id="fdd77-129">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="fdd77-130">En el siguiente código, se muestran ejemplos en los se almacenan los valores en listas y tuplas.</span><span class="sxs-lookup"><span data-stu-id="fdd77-130">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="fdd77-131">Para comprobar que un nombre de función almacenado en una tupla se evalúa realmente como una función, en el siguiente ejemplo se usan los operadores `fst` y `snd` para extraer los dos primeros elementos de la tupla `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-131">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="fdd77-132">El primer elemento de la tupla es `squareIt` y el segundo elemento es `num`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-132">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="fdd77-133">En un ejemplo anterior, se ha enlazado el identificador `num` al entero 10, un argumento válido para la función `squareIt`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-133">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="fdd77-134">La segunda expresión aplica el primer elemento de la tupla al segundo elemento de la tupla: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-134">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="fdd77-135">De forma similar, al igual que en el caso del identificador `num` y el entero 10, el identificador `squareIt` y la expresión lambda `fun n -> n * n` puede usarse indistintamente.</span><span class="sxs-lookup"><span data-stu-id="fdd77-135">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="fdd77-136">Pasar el valor como un argumento</span><span class="sxs-lookup"><span data-stu-id="fdd77-136">Pass the Value as an Argument</span></span>

<span data-ttu-id="fdd77-137">Si un lenguaje trata un valor como un valor de primera clase, se puede pasar dicho valor como argumento de una función.</span><span class="sxs-lookup"><span data-stu-id="fdd77-137">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="fdd77-138">Por ejemplo, los enteros y cadenas se suelen pasar como argumentos.</span><span class="sxs-lookup"><span data-stu-id="fdd77-138">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="fdd77-139">En el siguiente código, se muestran enteros y cadenas que se pasan como argumentos en F#.</span><span class="sxs-lookup"><span data-stu-id="fdd77-139">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="fdd77-140">Si una función es un valor de primera clase, dicha función también debe poder pasarse como un argumento.</span><span class="sxs-lookup"><span data-stu-id="fdd77-140">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="fdd77-141">Recuerde que esta es la primera característica de las funciones de orden superior.</span><span class="sxs-lookup"><span data-stu-id="fdd77-141">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="fdd77-142">En el siguiente ejemplo, la función `applyIt` tiene dos parámetros, `op` y `arg`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-142">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="fdd77-143">Si envía una función con un parámetro a `op` y un argumento apropiado para la función a `arg`, la función devolverá el resultado de aplicar `op` a `arg`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-143">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="fdd77-144">En el siguiente ejemplo, el argumento de función y el argumento entero se envían de la misma manera: por su nombre.</span><span class="sxs-lookup"><span data-stu-id="fdd77-144">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="fdd77-145">La capacidad para enviar una función como un argumento a otra función subyace a las abstracciones comunes en los lenguajes de programación funcional, como las operaciones de asignación o de filtrado.</span><span class="sxs-lookup"><span data-stu-id="fdd77-145">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="fdd77-146">Por ejemplo, una operación de asignación es una función de orden superior que captura el cálculo compartido por funciones que recorren una lista, realizan alguna operación con cada elemento y, a continuación, devuelven una lista con los resultados.</span><span class="sxs-lookup"><span data-stu-id="fdd77-146">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="fdd77-147">Quizás se desee incrementar cada elemento de una lista de enteros, elevar cada elemento al cuadrado o cambiar a mayúsculas cada uno de los elementos de una lista de cadenas.</span><span class="sxs-lookup"><span data-stu-id="fdd77-147">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="fdd77-148">La parte del cálculo propensa a errores es el proceso recursivo que recorre la lista y compila una lista de los resultados que se van a devolver.</span><span class="sxs-lookup"><span data-stu-id="fdd77-148">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="fdd77-149">Dicha parte se captura en la función de asignación.</span><span class="sxs-lookup"><span data-stu-id="fdd77-149">That part is captured in the mapping function.</span></span> <span data-ttu-id="fdd77-150">Lo único que hay que escribir para una aplicación concreta es la función que se desea aplicar a cada uno de los elementos de la lista (sumar, elevar al cuadrado, cambiar mayúscula a minúscula o viceversa).</span><span class="sxs-lookup"><span data-stu-id="fdd77-150">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="fdd77-151">Dicha función se envía como argumento a la función de asignación, de la misma manera que se envía `squareIt` a `applyIt` en el ejemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="fdd77-151">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="fdd77-152">F # proporciona métodos de asignación para la mayoría de los tipos de colección, incluidos [enumera](../language-reference/lists.md), [matrices](../language-reference/arrays.md), y [secuencias](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="fdd77-152">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="fdd77-153">En los siguientes ejemplos, se utilizan listas.</span><span class="sxs-lookup"><span data-stu-id="fdd77-153">The following examples use lists.</span></span> <span data-ttu-id="fdd77-154">La sintaxis es `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-154">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="fdd77-155">Para obtener más información, consulte [muestra](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="fdd77-155">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="fdd77-156">Devolver el valor de una llamada de función</span><span class="sxs-lookup"><span data-stu-id="fdd77-156">Return the Value from a Function Call</span></span>

<span data-ttu-id="fdd77-157">Por último, si un lenguaje trata una función como valor de primera clase, dicha función debe poder devolverse como valor de una llamada de función, al igual que en el caso de otros tipos como enteros y cadenas.</span><span class="sxs-lookup"><span data-stu-id="fdd77-157">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="fdd77-158">Las siguientes llamadas de función devuelven enteros y los muestran.</span><span class="sxs-lookup"><span data-stu-id="fdd77-158">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="fdd77-159">La siguiente llamada de función devuelve una cadena.</span><span class="sxs-lookup"><span data-stu-id="fdd77-159">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="fdd77-160">La siguiente llamada de función, declarada en el propio código, devuelve un valor booleano.</span><span class="sxs-lookup"><span data-stu-id="fdd77-160">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="fdd77-161">El valor mostrado es `True`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-161">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="fdd77-162">La capacidad para devolver una función como valor de una llamada de función es la segunda característica de las funciones de orden superior.</span><span class="sxs-lookup"><span data-stu-id="fdd77-162">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="fdd77-163">En el siguiente ejemplo, `checkFor` se define como una función que toma un argumento, `item`, y devuelve una nueva función como su valor.</span><span class="sxs-lookup"><span data-stu-id="fdd77-163">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="fdd77-164">La función devuelta toma una lista como argumento, `lst`, y busca `item` en `lst`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-164">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="fdd77-165">Si encuentra `item`, la función devuelve `true`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-165">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="fdd77-166">Si no encuentra `item`, la función devuelve `false`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-166">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="fdd77-167">Como se muestra en la sección anterior, el código siguiente utiliza una función de la lista, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), para buscar en la lista.</span><span class="sxs-lookup"><span data-stu-id="fdd77-167">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="fdd77-168">En el siguiente código, se utiliza `checkFor` para crear una función que toma un argumento (una lista) y busca el número 7 en la lista.</span><span class="sxs-lookup"><span data-stu-id="fdd77-168">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="fdd77-169">En el siguiente ejemplo, se utiliza el estatus de primera clase de las funciones en F# para declarar una función, `compose`, que devuelve una composición de dos argumentos de función.</span><span class="sxs-lookup"><span data-stu-id="fdd77-169">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="fdd77-170">Para obtener una versión más corta, vea la siguiente sección, "Funciones currificadas".</span><span class="sxs-lookup"><span data-stu-id="fdd77-170">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="fdd77-171">En el siguiente código, se envían dos funciones como argumentos a `compose` y las dos toman un solo argumento del mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="fdd77-171">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="fdd77-172">El valor devuelto es una nueva función que es una composición de los dos argumentos de función.</span><span class="sxs-lookup"><span data-stu-id="fdd77-172">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="fdd77-173">F# proporciona dos operadores, `<<` y `>>`, que realizan la composición de funciones.</span><span class="sxs-lookup"><span data-stu-id="fdd77-173">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="fdd77-174">Por ejemplo, `let squareAndDouble2 = doubleIt << squareIt` equivale a `let squareAndDouble = compose doubleIt squareIt` del ejemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="fdd77-174">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="fdd77-175">En el siguiente ejemplo de cómo devolver una función como valor de una llamada de función, se crea un simple juego de adivinanzas.</span><span class="sxs-lookup"><span data-stu-id="fdd77-175">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="fdd77-176">Para crear un juego, llame a `makeGame` y envíe para `target` el valor que el usuario debe adivinar.</span><span class="sxs-lookup"><span data-stu-id="fdd77-176">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="fdd77-177">El valor devuelto de la función `makeGame` es una función que toma un argumento (la adivinanza) y notifica si el usuario ha respondido correctamente a la adivinanza.</span><span class="sxs-lookup"><span data-stu-id="fdd77-177">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="fdd77-178">El siguiente código llama a `makeGame`, enviando el valor `7` para `target`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-178">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="fdd77-179">El identificador `playGame` está enlazado a la expresión lambda devuelta.</span><span class="sxs-lookup"><span data-stu-id="fdd77-179">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="fdd77-180">Por consiguiente, `playGame` es una función que toma como único argumento un valor de `guess`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-180">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="fdd77-181">Funciones currificadas</span><span class="sxs-lookup"><span data-stu-id="fdd77-181">Curried Functions</span></span>

<span data-ttu-id="fdd77-182">Muchos de los ejemplos en la sección anterior pueden escribirse más concisa aprovechando las ventajas de la parte implícita *currificación* en declaraciones de función de F #.</span><span class="sxs-lookup"><span data-stu-id="fdd77-182">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="fdd77-183">La currificación es un proceso que consiste en transformar una función con varios parámetros en una serie de funciones incrustadas, cada una de las cuales tiene un solo parámetro.</span><span class="sxs-lookup"><span data-stu-id="fdd77-183">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="fdd77-184">En F#, las funciones con más de un parámetro se currifican de manera inherente.</span><span class="sxs-lookup"><span data-stu-id="fdd77-184">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="fdd77-185">Por ejemplo, la función `compose` que aparece en la sección anterior se puede escribir de manera concisa con tres parámetros, tal y como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="fdd77-185">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="fdd77-186">Sin embargo, el resultado es una función con un parámetro que devuelve una función con un parámetro que, a su vez, devuelve otra función con un parámetro, tal y como se muestra en `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-186">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="fdd77-187">El acceso a esta función puede realizarse de varias maneras.</span><span class="sxs-lookup"><span data-stu-id="fdd77-187">You can access this function in several ways.</span></span> <span data-ttu-id="fdd77-188">En cada uno de los siguientes ejemplos, se devuelve y se muestra el número 18.</span><span class="sxs-lookup"><span data-stu-id="fdd77-188">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="fdd77-189">Se puede reemplazar `compose4` con `compose4curried` en cualquiera de los ejemplos.</span><span class="sxs-lookup"><span data-stu-id="fdd77-189">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="fdd77-190">Para comprobar que la función se ejecuta igual que antes, recurre de nuevo a los casos de prueba originales.</span><span class="sxs-lookup"><span data-stu-id="fdd77-190">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="fdd77-191">La currificación se puede restringir agrupando los parámetros en tuplas.</span><span class="sxs-lookup"><span data-stu-id="fdd77-191">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="fdd77-192">Para obtener más información, vea "Modelos de parámetros" en [parámetros y argumentos](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="fdd77-192">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="fdd77-193">En el siguiente ejemplo, se utiliza la currificación implícita para escribir una versión más corta de `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-193">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="fdd77-194">Los detalles referentes a cómo `makeGame` construye y devuelve la función `game` son menos explícitos en este formato, pero se pueden usar los casos de prueba originales para comprobar que el resultado es el mismo.</span><span class="sxs-lookup"><span data-stu-id="fdd77-194">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="fdd77-195">Para obtener más información sobre la currificación, vea "Aplicación parcial de argumentos" en [funciones](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="fdd77-195">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="fdd77-196">El identificador y la definición de función pueden usarse indistintamente</span><span class="sxs-lookup"><span data-stu-id="fdd77-196">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="fdd77-197">El nombre de variable `num` de los ejemplos anteriores se evalúa como el entero 10, y no es de extrañar que el entero 10 sea también válido en los casos en los que `num` es válido.</span><span class="sxs-lookup"><span data-stu-id="fdd77-197">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="fdd77-198">Lo mismo se aplica a los identificadores de las funciones y sus valores: siempre que se pueda usar el nombre de la función, se podrá usar la expresión lamdba enlazada al mismo.</span><span class="sxs-lookup"><span data-stu-id="fdd77-198">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="fdd77-199">En el siguiente ejemplo, se define una función `Boolean` denominada `isNegative` y, a continuación, se usan indistintamente el nombre y la definición de la función.</span><span class="sxs-lookup"><span data-stu-id="fdd77-199">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="fdd77-200">En los tres ejemplos siguientes, se devuelve y se muestra `False`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-200">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="fdd77-201">Para ir incluso un poco más lejos, reemplace `applyIt` por el valor al que está enlazada la función `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="fdd77-201">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="fdd77-202">Las funciones son valores de primera clase en F#</span><span class="sxs-lookup"><span data-stu-id="fdd77-202">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="fdd77-203">En los ejemplos que figuran en las secciones anteriores, se muestra que las funciones en F# cumplen los criterios de valores de primera clase:</span><span class="sxs-lookup"><span data-stu-id="fdd77-203">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="fdd77-204">Se puede enlazar un identificador a una definición de función.</span><span class="sxs-lookup"><span data-stu-id="fdd77-204">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="fdd77-205">Se puede almacenar una función en una estructura de datos.</span><span class="sxs-lookup"><span data-stu-id="fdd77-205">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="fdd77-206">Se puede pasar una función como argumento.</span><span class="sxs-lookup"><span data-stu-id="fdd77-206">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="fdd77-207">Se puede devolver una función como valor de una llamada de función.</span><span class="sxs-lookup"><span data-stu-id="fdd77-207">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="fdd77-208">Para obtener más información sobre F #, vea el [referencia del lenguaje F #](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="fdd77-208">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="fdd77-209">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fdd77-209">Example</span></span>

### <a name="description"></a><span data-ttu-id="fdd77-210">Descripción</span><span class="sxs-lookup"><span data-stu-id="fdd77-210">Description</span></span>

<span data-ttu-id="fdd77-211">El código siguiente contiene todos los ejemplos de este tema.</span><span class="sxs-lookup"><span data-stu-id="fdd77-211">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="fdd77-212">Código</span><span class="sxs-lookup"><span data-stu-id="fdd77-212">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="fdd77-213">Vea también</span><span class="sxs-lookup"><span data-stu-id="fdd77-213">See Also</span></span>

[<span data-ttu-id="fdd77-214">Listas</span><span class="sxs-lookup"><span data-stu-id="fdd77-214">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="fdd77-215">Tuplas</span><span class="sxs-lookup"><span data-stu-id="fdd77-215">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="fdd77-216">Funciones</span><span class="sxs-lookup"><span data-stu-id="fdd77-216">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="fdd77-217">`let`Enlaces</span><span class="sxs-lookup"><span data-stu-id="fdd77-217">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="fdd77-218">Expresiones lambda: La `fun` (palabra clave)</span><span class="sxs-lookup"><span data-stu-id="fdd77-218">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)