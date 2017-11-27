---
title: "Método ICorDebugModuleDebugEvent::GetModule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64564b1af76ae3ce578155c7c40f0c4a4bd2c890
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="25eca-102">Método ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="25eca-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="25eca-103">Obtém o módulo mesclado apenas carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="25eca-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25eca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25eca-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25eca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25eca-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="25eca-106">[out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo mesclado que apenas foi carregado e descarregado.</span><span class="sxs-lookup"><span data-stu-id="25eca-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25eca-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="25eca-107">Remarks</span></span>  
 <span data-ttu-id="25eca-108">Você pode chamar o [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método para determinar se o módulo foi carregado e descarregado.</span><span class="sxs-lookup"><span data-stu-id="25eca-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25eca-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="25eca-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25eca-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25eca-110">Requirements</span></span>  
 <span data-ttu-id="25eca-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25eca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25eca-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25eca-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25eca-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25eca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25eca-114">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25eca-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25eca-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25eca-115">See Also</span></span>  
 [<span data-ttu-id="25eca-116">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="25eca-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [<span data-ttu-id="25eca-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="25eca-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)