---
title: 'Mitigação: serviços WCF e autenticação de certificado'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f05dfab89fa5f811769687c467b2186745ecd5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388931"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Mitigação: serviços WCF e autenticação de certificado
O .NET Framework 4.6 adiciona o TLS 1.1 e o TLS 1.2 à lista padrão de protocolos SSL do WCF. Quando os computadores cliente e servidor têm o .NET Framework 4.6 ou posteriores instalados, o TLS 1.2 é usado para negociação.  
  
## <a name="impact"></a>Impacto  
 O TLS 1.2 não dá suporte à autenticação do certificado MD5. Consequentemente, se um cliente usar um certificado SSL que use MD5 para o algoritmo de hash, o cliente WCF falhará ao se conectar ao serviço WCF. Para saber mais, confira [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md) (Mitigação: serviços WCF e autenticação de certificado).  
  
## <a name="mitigation"></a>Redução  
 Você pode contornar esse problema para que um cliente WCF possa se conectar a um servidor WCF seguindo um destes procedimentos:  
  
-   Atualize o certificado para não usar o algoritmo MD5. Esta é a solução recomendada.  
  
-   Se a associação não tiver sido configurada dinamicamente no código-fonte, atualize o arquivo de configuração de aplicativo para usar o TLS 1.1 ou uma versão anterior do protocolo. Isso permite que você continue usando um certificado com o algoritmo de hash MD5.  
  
    > [!CAUTION]
    >  Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.  
  
     O arquivo de configuração que se segue demonstra isso:  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding>  
                        <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                            <transport clientCredentialType="None|Windows|Certificate"  
                                                protectionLevel="None|Sign|EncryptAndSign"  
                                                sslProtocols="Ssl3|Tls1|Tls11">  
                            </transport>  
                        </security>  
                    </binding>  
                </netTcpBinding>  
            </bindings>  
        </system.ServiceModel>  
    </configuration>  
    ```  
  
-   Se a associação foi configurada dinamicamente no código-fonte, atualize a propriedade <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> para usar o TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) ou uma versão anterior do protocolo no código-fonte.  
  
    > [!CAUTION]
    >  Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
