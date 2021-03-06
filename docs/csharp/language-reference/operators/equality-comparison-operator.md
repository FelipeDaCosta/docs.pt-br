---
title: Operador == (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: d9d7dcf3b38939e681fb51d6c674151cee78b3d0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43779151"
---
# <a name="-operator-c-reference"></a>Operador == (Referência de C#)
Para tipos de valor predefinidos, o operador de igualdade (`==`) retornará true se os valores dos seus operandos forem iguais; caso contrário, `false`. Para tipos de referência diferentes de [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md), o `==` retornará `true` se seus dois operandos se referirem ao mesmo objeto. Para o tipo `string`, o `==` compara os valores das cadeias de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Os tipos de valor definidos pelo usuário podem sobrecarregar o operador `==` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Os tipos de referência definidos pelo usuário também podem fazer isso, embora o `==` se comporte, por padrão, conforme descrito acima para os tipos de referência predefinidos e definidos pelo usuário. Se `==` estiver sobrecarregado, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) também deverá estar sobrecarregado. As operações em tipos integrais geralmente são permitidas na enumeração.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
