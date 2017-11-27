---
title: "Processamento de transações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5248dd3a4da450e411dd5d9a7843df6c9263026e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-processing"></a><span data-ttu-id="9f786-102">Processamento de transações</span><span class="sxs-lookup"><span data-stu-id="9f786-102">Transaction Processing</span></span>
<span data-ttu-id="9f786-103">Ao comprar um livro de livrarias online, você troca money (na forma de crédito) de um livro.</span><span class="sxs-lookup"><span data-stu-id="9f786-103">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="9f786-104">Se o crédito é boa, uma série de operações relacionadas garante que você obtenha o livro e a livraria obtém seu dinheiro.</span><span class="sxs-lookup"><span data-stu-id="9f786-104">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="9f786-105">No entanto, se uma única operação na série falhar durante a troca, toda a troca falhará.</span><span class="sxs-lookup"><span data-stu-id="9f786-105">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="9f786-106">Você não obtiver o livro e a livraria não obter seu dinheiro.</span><span class="sxs-lookup"><span data-stu-id="9f786-106">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="9f786-107">A tecnologia responsável por fazer o intercâmbio equilibrado e previsível é chamada de processamento de transações.</span><span class="sxs-lookup"><span data-stu-id="9f786-107">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="9f786-108">As transações garantem que recursos orientados a dados não são permanentemente atualizados, a menos que todas as operações dentro da unidade transacional foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="9f786-108">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="9f786-109">Ao combinar um conjunto de operações relacionadas em uma unidade que completamente obtenha êxito ou falha completamente, você pode simplificar a recuperação de erro e tornar seu aplicativo mais confiável.</span><span class="sxs-lookup"><span data-stu-id="9f786-109">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="9f786-110">Sistemas de processamento de transação consistem em hardware e software que hospeda um aplicativo orientado a transações que executa as transações de rotina necessárias para conduzir os negócios.</span><span class="sxs-lookup"><span data-stu-id="9f786-110">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="9f786-111">Os exemplos incluem sistemas de gerenciamento de entrada de ordem de venda, reservas de viagens, folha de pagamento, registros de funcionários, produção e a remessa.</span><span class="sxs-lookup"><span data-stu-id="9f786-111">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="9f786-112">Esta seção fornece informações gerais sobre o processamento de transações e informações específicas sobre como escrever aplicativos transacionais e gerenciadores de recursos usando o Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f786-112">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f786-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9f786-113">In This Section</span></span>  
 <span data-ttu-id="9f786-114">[Transaction Fundamentals](../../../../docs/framework/data/transactions/transaction-fundamentals.md) (Conceitos básicos de transação)</span><span class="sxs-lookup"><span data-stu-id="9f786-114">[Transaction Fundamentals](../../../../docs/framework/data/transactions/transaction-fundamentals.md)</span></span>  
 <span data-ttu-id="9f786-115">Apresenta os termos e conceitos de processamento de transações básicas.</span><span class="sxs-lookup"><span data-stu-id="9f786-115">Introduces basic transaction processing terms and concepts.</span></span>  
  
 <span data-ttu-id="9f786-116">[Features Provided by System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) (Recursos fornecidos por System.Transactions)</span><span class="sxs-lookup"><span data-stu-id="9f786-116">[Features Provided by System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)</span></span>  
 <span data-ttu-id="9f786-117">Descreve como usar recursos do System. Transactions para escrever seu próprio aplicativo transacional.</span><span class="sxs-lookup"><span data-stu-id="9f786-117">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9f786-118">Referência</span><span class="sxs-lookup"><span data-stu-id="9f786-118">Reference</span></span>  
 <xref:System.Transactions>  
 <span data-ttu-id="9f786-119">Fornece classes que permitem que o seu código para participar de transações.</span><span class="sxs-lookup"><span data-stu-id="9f786-119">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="9f786-120">As classes de suportam a transações com vários participantes distribuídos, várias notificações de fase e inscrições duráveis.</span><span class="sxs-lookup"><span data-stu-id="9f786-120">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>