---
title: Interface ICLRErrorReportingManager
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf9e04ed1d3a68fed120c4c13ad992af1f777244
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433790"
---
# <a name="iclrerrorreportingmanager-interface"></a>Interface ICLRErrorReportingManager
Fornece métodos que permitem que o host configurar os despejos de pilha personalizado para o relatório de erros.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Especifica a configuração de despejos de pilha personalizado para o relatório de erros.|  
|[Método EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Limpa a configuração de despejo de pilha personalizado foi definida por uma chamada anterior para `BeginCustomDump`.|  
|[Método GetBucketParametersForCurrentException](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Obtém o bucket Watson para a exceção atual no thread de chamada.|  
  
## <a name="remarks"></a>Comentários  
 O `BeginCustomDump` método define a configuração de despejo de pilha personalizado. O `EndCustomDump` método limpa a configuração de despejo de pilha personalizado e libera qualquer estado associado. Ele deve ser chamado após a conclusão do despejo personalizado.  
  
> [!IMPORTANT]
>  Falha ao chamar `EndCustomDump` faz com que a memória vazem.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
