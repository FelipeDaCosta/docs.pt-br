---
title: Método ISymUnmanagedWriter::Initialize
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44046560f4f788c4a7d695ff18c9c01740fea35a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428029"
---
# <a name="isymunmanagedwriterinitialize-method"></a>Método ISymUnmanagedWriter::Initialize
Define a interface do emissor de metadados com a qual este gravador será associado e define o nome do arquivo de saída que serão gravados os símbolos de depuração.  
  
 Esse método pode ser chamado apenas uma vez, e ele deve ser chamado antes de quaisquer outros métodos de gravador. Alguns gravadores podem exigir um nome de arquivo. No entanto, você sempre pode passar um nome de arquivo para esse método sem qualquer efeito negativo no gravadores que não usam o nome do arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `emitter`  
 [in] Um ponteiro para a interface do emissor de metadados.  
  
 `filename`  
 [in] O nome do arquivo no qual os símbolos de depuração são gravados. Se um nome de arquivo for especificado para um gravador que não use nomes de arquivo, esse parâmetro será ignorado.  
  
 `pIStream`  
 [in] Se especificado, o gravador de símbolo emitirá os símbolos para o determinado <xref:System.Runtime.InteropServices.ComTypes.IStream> em vez de no arquivo especificado no `filename` parâmetro. O parâmetro `pIStream` é opcional.  
  
 `fFullBuild`  
 [in] `true` quando se trata de uma recriação completa; `false` quando se trata de uma compilação incremental.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Método Initialize2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
