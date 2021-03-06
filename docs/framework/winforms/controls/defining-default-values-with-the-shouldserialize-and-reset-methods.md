---
title: Definindo valores padrão com o ShouldSerialize e os métodos de redefinição
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: 8d7645e8de5edee711c30bbe7edde8ba7b5b1dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529786"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definindo valores padrão com o ShouldSerialize e os métodos de redefinição
`ShouldSerialize` e `Reset` são métodos opcionais que você pode fornecer para uma propriedade, caso ela não tenha um valor padrão simples. Se a propriedade tem um valor padrão simples, você deve aplicar o <xref:System.ComponentModel.DefaultValueAttribute> e forneça o valor padrão para o construtor de classe de atributo em vez disso. Qualquer um desses mecanismos habilita os recursos a seguir no designer:  
  
-   A propriedade fornecerá uma indicação visual no navegador de propriedades se tiver sido modificado de seu valor padrão.  
  
-   O usuário pode clicar com o botão direito do mouse na propriedade e escolher **Redefinir** para restaurar a propriedade para o valor padrão.  
  
-   O designer gera um código mais eficiente.  
  
    > [!NOTE]
    >  A aplicar a <xref:System.ComponentModel.DefaultValueAttribute> ou forneça `Reset` *PropertyName* e `ShouldSerialize` *PropertyName* métodos. Não use os dois.  
  
 O método `Reset`*PropertyName* define uma propriedade para o valor padrão, conforme mostrado no seguinte fragmento de código.  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  Se uma propriedade não tem um `Reset` método, não é marcado com um <xref:System.ComponentModel.DefaultValueAttribute>e não tem um valor padrão fornecido na sua declaração, o `Reset` opção para essa propriedade está desabilitada no menu de atalho a **propriedades** janela do Designer de formulários do Windows no Visual Studio.  
  
 Os designers de como o Visual Studio usam o `ShouldSerialize` *PropertyName* método para verificar se uma propriedade foi alterado do valor padrão e escrever código em somente-se o formulário uma propriedade é alterado, permitindo, assim, um código mais eficiente geração. Por exemplo:  
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 Segue um exemplo de código completo.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 Nesse caso, mesmo quando o valor da variável particular acessados pelo `MyFont` é de propriedade `null`, o navegador de propriedade não exibir `null`; em vez disso, ele exibe o <xref:System.Windows.Forms.Control.Font%2A> propriedade do pai, se não for `null`, ou o padrão <xref:System.Windows.Forms.Control.Font%2A> valor definido em <xref:System.Windows.Forms.Control>. Portanto, o valor padrão para `MyFont` não pode simplesmente ser definida e um <xref:System.ComponentModel.DefaultValueAttribute> não pode ser aplicado a esta propriedade. Em vez disso, os métodos `ShouldSerialize` e `Reset` devem ser implementados para a propriedade `MyFont`.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades em controles do Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Definindo uma propriedade](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [Eventos alterados por propriedade](../../../../docs/framework/winforms/controls/property-changed-events.md)
