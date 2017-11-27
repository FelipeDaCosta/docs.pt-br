---
title: Usando um pincel de gradiente para preencher formas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a1c4ab7c2ee6f7164b6158dcb4ca4721be12650
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="aca55-102">Usando um pincel de gradiente para preencher formas</span><span class="sxs-lookup"><span data-stu-id="aca55-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="aca55-103">Você pode usar um pincel de gradiente para preencher uma forma com uma cor que muda gradualmente.</span><span class="sxs-lookup"><span data-stu-id="aca55-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="aca55-104">Por exemplo, é possível usar um gradiente horizontal para preencher uma forma com uma cor que muda gradualmente à medida que você move da borda esquerda da forma para a borda direita.</span><span class="sxs-lookup"><span data-stu-id="aca55-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="aca55-105">Imagine um retângulo com uma borda esquerda preta (representada pelos componentes vermelho, verde e azul 0, 0, 0) e uma borda direita vermelha (representada por 255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="aca55-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="aca55-106">Se o retângulo tem 256 pixels de largura, o componente vermelho de um determinado pixel será maior do que o componente vermelho do pixel à esquerda.</span><span class="sxs-lookup"><span data-stu-id="aca55-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="aca55-107">O pixel mais à esquerda em uma linha tem componentes de cor (0, 0, 0), o segundo pixel tem (1, 0, 0), o terceiro pixel tem (2, 0, 0) e assim por diante, até chegar ao pixel mais à direita, que tem componentes de cor (255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="aca55-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="aca55-108">Esses valores de cor interpolados compõem o gradiente de cores.</span><span class="sxs-lookup"><span data-stu-id="aca55-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="aca55-109">Um gradiente linear muda de cor ao mover na horizontal, vertical ou em paralelo para uma linha inclinada especificada.</span><span class="sxs-lookup"><span data-stu-id="aca55-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="aca55-110">Um gradiente de demarcador muda de cor ao mover sobre o interior e o limite de um demarcador.</span><span class="sxs-lookup"><span data-stu-id="aca55-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="aca55-111">É possível personalizar gradientes de demarcador para obter uma grande variedade de efeitos.</span><span class="sxs-lookup"><span data-stu-id="aca55-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="aca55-112">A ilustração a seguir mostra um retângulo preenchido com um pincel gradiente linear e uma elipse preenchida com um pincel gradiente de demarcador.</span><span class="sxs-lookup"><span data-stu-id="aca55-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="aca55-113">![Gradiente](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="aca55-113">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aca55-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="aca55-114">In This Section</span></span>  
 [<span data-ttu-id="aca55-115">Como Criar um Gradiente Linear</span><span class="sxs-lookup"><span data-stu-id="aca55-115">How to: Create a Linear Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="aca55-116">Mostra como criar um gradiente linear usando a <xref:System.Drawing.Drawing2D.LinearGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="aca55-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="aca55-117">Como Criar um Gradiente de Caminho</span><span class="sxs-lookup"><span data-stu-id="aca55-117">How to: Create a Path Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 <span data-ttu-id="aca55-118">Descreve como criar um gradiente de caminho usando o <xref:System.Drawing.Drawing2D.PathGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="aca55-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="aca55-119">Como Aplicar Correção Gama a um Gradiente</span><span class="sxs-lookup"><span data-stu-id="aca55-119">How to: Apply Gamma Correction to a Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="aca55-120">Explica como usar correção gama com um pincel de gradiente.</span><span class="sxs-lookup"><span data-stu-id="aca55-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aca55-121">Referência</span><span class="sxs-lookup"><span data-stu-id="aca55-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="aca55-122">Contém uma descrição dessa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="aca55-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="aca55-123">Contém uma descrição dessa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="aca55-123">Contains a description of this class and has links to all of its members.</span></span>