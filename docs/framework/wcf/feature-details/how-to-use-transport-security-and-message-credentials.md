---
title: Como utilizar credenciais de mensagem e segurança de transporte
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
author: BrucePerlerMS
ms.openlocfilehash: 40fe7b1fa6a61b56d5dfdde75a92834f096a8be4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200401"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Como utilizar credenciais de mensagem e segurança de transporte
Proteger um serviço com credenciais de transporte e de mensagem usa o melhor dos modos de segurança de transporte e de mensagem no Windows Communication Foundation (WCF). Em suma, segurança de camada de transporte fornece integridade e confidencialidade, enquanto a segurança da camada de mensagem fornece uma variedade de credenciais que não são possíveis com os mecanismos de segurança de transporte estrito. Este tópico mostra as etapas básicas para a implementação de transporte com credenciais de mensagem usando o <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.NetTcpBinding> associações. Para obter mais informações sobre como definir o modo de segurança, consulte [como: definir o modo de segurança](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 Ao definir o modo de segurança para `TransportWithMessageCredential`, o transporte determina o mecanismo real que fornece a segurança de nível de transporte. Para HTTP, o mecanismo é Secure Sockets Layer (SSL) sobre HTTP (HTTPS); para TCP, é SSL sobre TCP ou Windows.  
  
 Se o transporte é HTTP (usando o <xref:System.ServiceModel.WSHttpBinding>), SSL sobre HTTP fornece a segurança de nível de transporte. Nesse caso, você deve configurar o computador que hospeda o serviço com um certificado SSL associado a uma porta, conforme mostrado neste tópico.  
  
 Se o transporte é TCP (usando o <xref:System.ServiceModel.NetTcpBinding>), por padrão a segurança de nível de transporte fornecida é de segurança do Windows ou SSL sobre TCP. Ao usar SSL sobre TCP, você deve especificar o certificado usando o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método, conforme mostrado neste tópico.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Para usar o WSHttpBinding com um certificado de segurança de transporte (no código)  
  
1.  Use a ferramenta de HttpCfg.exe para associar um certificado SSL para uma porta no computador. Para obter mais informações, consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  Criar uma instância do <xref:System.ServiceModel.WSHttpBinding> de classe e defina a <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> propriedade <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3.  Defina o <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> propriedade para um valor apropriado. (Para obter mais informações, consulte [selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.  
  
4.  Criar uma instância da <xref:System.Uri> classe com um endereço base apropriado. Observe que o endereço deve usar o esquema "HTTPS" e deve conter o nome real da máquina e o número da porta associado ao certificado SSL. (Como alternativa, você pode definir o endereço base na configuração).  
  
5.  Adicionar um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.  
  
6.  Criar a instância das <xref:System.ServiceModel.ServiceHost> e chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Para usar a NetTcpBinding com um certificado de segurança de transporte (no código)  
  
1.  Criar uma instância do <xref:System.ServiceModel.NetTcpBinding> de classe e defina a <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> propriedade <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Defina o <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> para um valor apropriado. O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.  
  
3.  Criar uma instância da <xref:System.Uri> classe com um endereço base apropriado. Observe que o endereço deve usar o esquema de "NET. TCP". (Como alternativa, você pode definir o endereço base na configuração).  
  
4.  Criar a instância da <xref:System.ServiceModel.ServiceHost> classe.  
  
5.  Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para definir explicitamente o certificado X.509 para o serviço.  
  
6.  Adicionar um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.  
  
7.  Chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Para usar a NetTcpBinding com Windows para segurança de transporte (no código)  
  
1.  Criar uma instância do <xref:System.ServiceModel.NetTcpBinding> de classe e defina a <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> propriedade <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Definir a segurança de transporte para usar o Windows, definindo o <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> para <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Observe que esse é o padrão).  
  
3.  Defina o <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> para um valor apropriado. O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.  
  
4.  Criar uma instância da <xref:System.Uri> classe com um endereço base apropriado. Observe que o endereço deve usar o esquema de "NET. TCP". (Como alternativa, você pode definir o endereço base na configuração).  
  
5.  Criar a instância da <xref:System.ServiceModel.ServiceHost> classe.  
  
6.  Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para definir explicitamente o certificado X.509 para o serviço.  
  
7.  Adicionar um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.  
  
8.  Chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Usando a configuração  
  
#### <a name="to-use-the-wshttpbinding"></a>Para usar o WSHttpBinding  
  
1.  Configure o computador com um certificado SSL associado a uma porta. (Para obter mais informações, consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). Não é necessário definir um <`transport`> valor do elemento com essa configuração.  
  
2.  Especifique o tipo de credencial de cliente para a segurança de nível de mensagem. O exemplo a seguir define o `clientCredentialType` atributo da <`message`> elemento `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Para usar a NetTcpBinding com um certificado para segurança de transporte  
  
1.  Para SSL sobre TCP, você deve especificar explicitamente o certificado no `<behaviors>` elemento. O exemplo a seguir especifica um certificado por seu emissor no local de armazenamento padrão (computador local e armazenamentos pessoais).  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Adicionar um [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) à seção de associações  
  
3.  Adicione um elemento de associação e defina o `name` de atributo para um valor apropriado.  
  
4.  Adicionar um <`security`> elemento e defina o `mode` atributo `TransportWithMessageCredential`.  
  
5.  Adicione um <`message>` elemento e defina o `clientCredentialType` de atributo para um valor apropriado.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Para usar a NetTcpBinding com Windows para segurança de transporte  
  
1.  Adicionar um [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) à seção de associações,  
  
2.  Adicione um <`binding`> elemento e defina o `name` de atributo para um valor apropriado.  
  
3.  Adicionar um <`security`> elemento e defina o `mode` atributo `TransportWithMessageCredential`.  
  
4.  Adicionar um <`transport`> elemento e defina o `clientCredentialType` atributo `Windows`.  
  
5.  Adicione um <`message`> elemento e defina o `clientCredentialType` de atributo para um valor apropriado. O código a seguir define o valor para um certificado.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Como definir o modo de segurança](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Protegendo serviços](../../../../docs/framework/wcf/securing-services.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
