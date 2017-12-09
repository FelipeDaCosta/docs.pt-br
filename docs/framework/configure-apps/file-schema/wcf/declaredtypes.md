---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80a2959395cf8f10ae8c5bc2ccd47ea97ffdaa30
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdeclaredtypesgt"></a>&lt;declaredTypes&gt;
Contém de tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa durante a desserialização.  
  
 Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
                <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Adiciona tipos que exigem tipos conhecidos.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Exemplo  
 O código XML a seguir mostra tipos declarados e tipos conhecidos adicionados a um `DataContractSerializer` elemento. O exemplo mostra três tipos que está sendo adicionados. A primeira é um tipo personalizado chamado "Orders" que usa um tipo conhecido chamado "Item". O segundo declarado de tipo é um <xref:System.Collections.Generic.List%601> que usa `Item` como um tipo conhecido. Finalmente a terceira declarado de tipo é um <xref:System.Collections.Generic.Dictionary%602>. O <xref:System.Collections.Generic.Dictionary%602> tipo de classe é um tipo genérico, com parâmetros de tipo de dois. A primeira representa a chave e a segunda representa o valor. O exemplo a seguir adiciona um <xref:System.Collections.Generic.List%601> do segundo tipo (valor) à lista de tipos conhecidos. Você deve usar o `index` atributo para especificar o parâmetro de tipo para usar o tipo conhecido. Nesse caso, o tipo de valor é indicado pelo índice de atributo definido como "1" (a coleção é baseado em zero).  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [Tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)