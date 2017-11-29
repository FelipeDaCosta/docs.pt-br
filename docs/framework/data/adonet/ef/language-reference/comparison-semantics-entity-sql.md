---
title: "Semântica de comparação (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1fd1c21fc4f156bfe7a5abf9f76bd341e2d0f10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-semantics-entity-sql"></a>Semântica de comparação (Entity SQL)
Executar alguns dos seguintes operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] envolve a comparação de instâncias do tipo:  
  
## <a name="explicit-comparison"></a>Comparação explícita  
 Operações de igualdade:  
  
-   =  
  
-   !=  
  
 Ordenando operações:  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 Operações de nulidade:  
  
-   É NULO  
  
-   NÃO É NULO  
  
## <a name="explicit-distinction"></a>Distinção explícita  
 Distinção de igualdade:  
  
-   DISTINCT  
  
-   GROUP BY  
  
 Classificação a distinção:  
  
-   ORDENAR POR  
  
## <a name="implicit-distinction"></a>Distinção implícita  
 Definir operações e predicados (igualdade):  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   OVERLAPS  
  
 Predicados de item (igual):  
  
-   IN  
  
## <a name="supported-combinations"></a>Combinações suportados  
 A tabela a seguir mostra todas as combinações suportados operadores de comparação para cada tipo do tipo:  
  
|**Tipo**|**=**<br /><br /> **!=**|**AGRUPAR POR**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **SE CRUZAM**<br /><br /> **EXCETO**<br /><br /> **DEFINIR**<br /><br /> **SOBREPOSIÇÕES**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDENAR POR**|**É NULO**<br /><br /> **NÃO É NULO**|  
|-|-|-|-|-|-|-|-|  
|Tipo de entidade|REF<sup>1</sup>|Todas as propriedades<sup>2</sup>|Todas as propriedades<sup>2</sup>|Todas as propriedades<sup>2</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|REF<sup>1</sup>|  
|Tipo complexo|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|  
|Row|Todas as propriedades<sup>4</sup>|Todas as propriedades<sup>4</sup>|Todas as propriedades<sup>4</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Todas as propriedades<sup>4</sup>|Lançar<sup>3</sup>|  
|Tipo primitivo|Específica do provedor|Específica do provedor|Específica do provedor|Específica do provedor|Específica do provedor|Específica do provedor|Específica do provedor|  
|Multiset|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|  
|Ref|Sim<sup>5</sup>|Sim<sup>5</sup>|Sim<sup>5</sup>|Sim<sup>5</sup>|Throw|Throw|Sim<sup>5</sup>|  
|Associação<br /><br /> tipo|Lançar<sup>3</sup>|Throw|Throw|Throw|Lançar<sup>3</sup>|Lançar<sup>3</sup>|Lançar<sup>3</sup>|  
  
 <sup>1</sup>as referências das instâncias do tipo de entidade fornecido implicitamente são comparadas, conforme mostrado no exemplo a seguir:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Uma instância de entidade não pode ser comparado a uma referência explícita. Se isso for tentada, uma exceção é lançada. Por exemplo, a seguinte consulta irá acionar uma exceção:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>propriedades de tipos complexos são esticadas antes de serem enviados para o armazenamento, para que se tornem comparável (contanto que todas as suas propriedades são comparáveis). Consulte também <sup>4.</sup>  
  
 <sup>3</sup>o Entity Framework runtime detecta o caso de suporte e lança uma exceção significativa sem envolver o provedor/armazenamento.  
  
 <sup>4</sup>é feita uma tentativa de comparar todas as propriedades. Se houver uma propriedade que é de um tipo não comparável, como texto, o ntext, ou imagem, uma exceção de servidor pode ser lançada.  
  
 <sup>5</sup>todos os elementos individuais de referências são comparados (Isso inclui o nome do conjunto de entidade e todas as propriedades de chave do tipo de entidade).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)