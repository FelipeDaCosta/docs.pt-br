---
title: Eventos (F#)
description: "Saiba como F # eventos permitem que você associe a ações do usuário, que são importantes na programação de GUI de chamadas de função."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 28b588f2-0c9e-4c0d-babf-901ed934638a
ms.openlocfilehash: 43ff52134093acbd670d48ea83d40f1e9eb377c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="events"></a><span data-ttu-id="4a906-104">Eventos</span><span class="sxs-lookup"><span data-stu-id="4a906-104">Events</span></span>

> [!NOTE]
<span data-ttu-id="4a906-105">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="4a906-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="4a906-106">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="4a906-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="4a906-107">Eventos permitem que você associe chamadas de função a ações de usuário e são importantes na programação da GUI.</span><span class="sxs-lookup"><span data-stu-id="4a906-107">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="4a906-108">Os eventos também podem ser disparados por seus aplicativos ou pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="4a906-108">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="4a906-109">Tratando eventos</span><span class="sxs-lookup"><span data-stu-id="4a906-109">Handling Events</span></span>
<span data-ttu-id="4a906-110">Quando você usa uma biblioteca de GUI como o Windows Forms ou o Windows Presentation Foundation (WPF), grande parte do código em seu aplicativo é executado em resposta a eventos que são predefinidos pela biblioteca.</span><span class="sxs-lookup"><span data-stu-id="4a906-110">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="4a906-111">Esses eventos predefinidos são membros de classes da GUI como formulários e controles.</span><span class="sxs-lookup"><span data-stu-id="4a906-111">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="4a906-112">Você pode adicionar comportamento personalizado a um evento preexistente, como o clique de botão, ao fazer referência ao evento de interesse nomeado específico (por exemplo, o evento `Click` da classe `Form`) e invocar o método `Add` como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a906-112">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="4a906-113">Se você executar isso do F# Interativo, omita a chamada a `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span><span class="sxs-lookup"><span data-stu-id="4a906-113">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="4a906-114">O tipo do método `Add` é `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="4a906-114">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="4a906-115">Portanto, o método do manipulador de eventos assume um parâmetro, normalmente os argumentos de evento, e retorna `unit`.</span><span class="sxs-lookup"><span data-stu-id="4a906-115">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="4a906-116">O exemplo anterior mostra o manipulador de eventos como uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="4a906-116">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="4a906-117">O manipulador de eventos também pode ser um valor de função como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a906-117">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="4a906-118">O exemplo de código a seguir também mostra o uso de parâmetros do manipulador de eventos que fornecem informações específicas para o tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="4a906-118">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="4a906-119">Para um evento `MouseMove`, o sistema passa um objeto `System.Windows.Forms.MouseEventArgs` que contém a posição `X` e `Y` do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4a906-119">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a><span data-ttu-id="4a906-120">Criando eventos personalizados</span><span class="sxs-lookup"><span data-stu-id="4a906-120">Creating Custom Events</span></span>
<span data-ttu-id="4a906-121">F # eventos são representados por F # [evento](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) de classe que implementa o [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span><span class="sxs-lookup"><span data-stu-id="4a906-121">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="4a906-122">`IEvent`é uma interface que combina a funcionalidade de duas interfaces, `System.IObservable<'T>` e [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span><span class="sxs-lookup"><span data-stu-id="4a906-122">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="4a906-123">Portanto, `Event`s têm funcionalidade equivalente de delegados em outras linguagens, além da funcionalidade adicional de `IObservable` o que significa que os eventos de F# oferecem suporte à filtragem de eventos e ao uso de funções de primeira classe de F# e expressões lambda como manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="4a906-123">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="4a906-124">Essa funcionalidade é fornecida no [módulo eventos](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span><span class="sxs-lookup"><span data-stu-id="4a906-124">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="4a906-125">Para criar um evento em uma classe que atue como qualquer outro evento do .NET Framework, adicione à classe uma associação `let` que defina um `Event` como um campo em uma classe.</span><span class="sxs-lookup"><span data-stu-id="4a906-125">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="4a906-126">Você pode especificar o tipo de argumento de evento desejado como o argumento de tipo ou deixá-lo em branco e fazer com que o compilador deduza o tipo apropriado.</span><span class="sxs-lookup"><span data-stu-id="4a906-126">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="4a906-127">Você também deve definir um membro de evento que exponha o evento como um evento de CLI.</span><span class="sxs-lookup"><span data-stu-id="4a906-127">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="4a906-128">Esse membro deve ter o [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) atributo.</span><span class="sxs-lookup"><span data-stu-id="4a906-128">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="4a906-129">Ela é declarada como uma propriedade e sua implementação é apenas uma chamada para o [publicar](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) propriedade do evento.</span><span class="sxs-lookup"><span data-stu-id="4a906-129">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="4a906-130">Os usuários de sua classe podem usar o método `Add` do evento publicado para adicionar um manipulador.</span><span class="sxs-lookup"><span data-stu-id="4a906-130">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="4a906-131">O argumento para o método `Add` pode ser uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="4a906-131">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="4a906-132">Você pode usar a propriedade `Trigger` do evento para gerar o evento, passando os argumentos à função do manipulador.</span><span class="sxs-lookup"><span data-stu-id="4a906-132">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="4a906-133">O exemplo de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="4a906-133">The following code example illustrates this.</span></span> <span data-ttu-id="4a906-134">Neste exemplo, o argumento do tipo inferido para o evento é uma tupla que representa os argumentos para a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="4a906-134">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="4a906-135">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="4a906-135">The output is as follows.</span></span>

```
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="4a906-136">A funcionalidade adicional fornecida pelo módulo `Event` está ilustrada aqui.</span><span class="sxs-lookup"><span data-stu-id="4a906-136">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="4a906-137">O exemplo de código a seguir ilustra o uso básico de `Event.create` para criar um evento e um método de gatilho, adicionar dois manipuladores de eventos na forma de expressões lambda e disparar o evento para executar ambas as expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="4a906-137">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="4a906-138">A saída do código anterior está a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a906-138">The output of the previous code is as follows.</span></span>

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="4a906-139">Processando fluxos de eventos</span><span class="sxs-lookup"><span data-stu-id="4a906-139">Processing Event Streams</span></span>
<span data-ttu-id="4a906-140">Em vez de apenas adicionar um manipulador de eventos para um evento usando o [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) função, você pode usar as funções no `Event` módulo para processo fluxos de eventos por meios altamente personalizados.</span><span class="sxs-lookup"><span data-stu-id="4a906-140">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="4a906-141">Para fazer isso, use a barra vertical e o sinal maior que (`|>`) junto com o evento como o primeiro valor em uma série de chamadas de função e funções do módulo `Event` como chamadas de função subsequentes.</span><span class="sxs-lookup"><span data-stu-id="4a906-141">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="4a906-142">O exemplo de código a seguir mostra como configurar um evento em que o manipulador é chamado apenas em determinadas condições.</span><span class="sxs-lookup"><span data-stu-id="4a906-142">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="4a906-143">O [módulo Observable](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contém funções semelhantes que operam em objetos observáveis.</span><span class="sxs-lookup"><span data-stu-id="4a906-143">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="4a906-144">Objetos observáveis são semelhantes a eventos, mas apenas assinam eventos ativamente se eles mesmos estiverem sendo assinados.</span><span class="sxs-lookup"><span data-stu-id="4a906-144">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>


## <a name="implementing-an-interface-event"></a><span data-ttu-id="4a906-145">Implementando um evento de interface</span><span class="sxs-lookup"><span data-stu-id="4a906-145">Implementing an Interface Event</span></span>
<span data-ttu-id="4a906-146">À medida em que desenvolve componentes de interface do usuário, você frequentemente começa ao criar um novo formulário ou um novo controle que herde de um formulário ou controle existente.</span><span class="sxs-lookup"><span data-stu-id="4a906-146">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="4a906-147">Eventos são frequentemente definidos em uma interface e, nesse caso, você deve implementar a interface para implementar o evento.</span><span class="sxs-lookup"><span data-stu-id="4a906-147">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="4a906-148">A interface `System.ComponentModel.INotifyPropertyChanged` define um único evento `System.ComponentModel.INotifyPropertyChanged.PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="4a906-148">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="4a906-149">O código a seguir ilustra como implementar o evento que essa interface herdada definiu:</span><span class="sxs-lookup"><span data-stu-id="4a906-149">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish


    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

<span data-ttu-id="4a906-150">Se você desejar conectar o evento no construtor, o código será um pouco mais complicado porque a conexão do evento deverá estar em um bloco `then` em um construtor adicional como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4a906-150">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")


    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)


// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a><span data-ttu-id="4a906-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a906-151">See Also</span></span>
[<span data-ttu-id="4a906-152">Membros</span><span class="sxs-lookup"><span data-stu-id="4a906-152">Members</span></span>](index.md)

[<span data-ttu-id="4a906-153">Manipulando e acionando eventos</span><span class="sxs-lookup"><span data-stu-id="4a906-153">Handling and Raising Events</span></span>](https://msdn.microsoft.com/library/edzehd2t.aspx)

[<span data-ttu-id="4a906-154">Expressões lambda: A `fun` palavra-chave</span><span class="sxs-lookup"><span data-stu-id="4a906-154">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)

[<span data-ttu-id="4a906-155">Módulo Control. Event</span><span class="sxs-lookup"><span data-stu-id="4a906-155">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[<span data-ttu-id="4a906-156">Control. Event &#60;' T &#62; Classe</span><span class="sxs-lookup"><span data-stu-id="4a906-156">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[<span data-ttu-id="4a906-157">Control. Event &#60;' Delegado ' Args &#62; Classe</span><span class="sxs-lookup"><span data-stu-id="4a906-157">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)