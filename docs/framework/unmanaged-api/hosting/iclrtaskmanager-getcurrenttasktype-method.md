---
title: Método ICLRTaskManager::GetCurrentTaskType
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51c103fb38dd97ec076096037932925e31280f02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437710"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a>Método ICLRTaskManager::GetCurrentTaskType
Obtém o tipo de tarefa que está em execução atualmente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pTaskType`  
 [out] Um ponteiro para um valor de [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeração que indica o tipo de tarefa que está sendo executado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
