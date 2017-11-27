---
title: "Visão geral do controle divisor (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Splitter
helpviewer_keywords: Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e4602796a1a7740adb9a352d0a21fb6c2a58959d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="760e5-102">Visão geral do controle divisor (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="760e5-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="760e5-103">Embora <xref:System.Windows.Forms.SplitContainer> substitua e adicione funcionalidade ao controle <xref:System.Windows.Forms.Splitter> de versões anteriores, <xref:System.Windows.Forms.Splitter> é mantido para compatibilidade com versões anteriores e uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="760e5-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="760e5-104">Windows Forms <xref:System.Windows.Forms.Splitter> controles são usados para redimensionar controles encaixados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="760e5-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="760e5-105">O <xref:System.Windows.Forms.Splitter> controle é geralmente usado em formulários com controles que têm vários comprimentos de dados para apresentar, como o Windows Explorer, painéis cujos dados contêm informações de larguras diferentes em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="760e5-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="760e5-106">Trabalhando com o controle Splitter</span><span class="sxs-lookup"><span data-stu-id="760e5-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="760e5-107">Quando o usuário aponta o ponteiro do mouse na borda não encaixada de um controle que pode ser redimensionado por um controle splitter, o ponteiro muda de aparência para indicar que o controle pode ser redimensionado.</span><span class="sxs-lookup"><span data-stu-id="760e5-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="760e5-108">Com o controle Splitter, o usuário pode redimensionar o controle encaixado que esteja imediatamente antes dele.</span><span class="sxs-lookup"><span data-stu-id="760e5-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="760e5-109">Portanto, para permitir que o usuário redimensione um controle encaixado em tempo de execução, encaixe o controle a ser redimensionado em uma borda de um contêiner e, em seguida, encaixe um controle Splitter no mesmo lado do contêiner.</span><span class="sxs-lookup"><span data-stu-id="760e5-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="760e5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="760e5-110">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="760e5-111">Como encaixar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="760e5-111">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="760e5-112">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="760e5-112">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)