---
title: 'Nasıl yapılır: işlem kullanarak verileri kaydetme'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfb03944743609d20d14f6104e5fadd529a5cfa6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641306"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Nasıl yapılır: işlem kullanarak verileri kaydetme

@No__t_0 ad alanını kullanarak bir işleme veri kaydedersiniz. Sizin için otomatik olarak yönetilen bir işleme katılmak üzere <xref:System.Transactions.TransactionScope> nesnesini kullanın.

Projeler *System. Transactions* derlemesine bir başvuru ile oluşturulmaz, bu nedenle işlemleri kullanan projelere el ile bir başvuru eklemeniz gerekir.

Bir işlemi uygulamanın en kolay yolu, bir `using` bildiriminde <xref:System.Transactions.TransactionScope> nesnesini örnekleyekullanmaktır. (Daha fazla bilgi için bkz. [using deyimleri](/dotnet/visual-basic/language-reference/statements/using-statement)ve [using deyimleri](/dotnet/csharp/language-reference/keywords/using-statement).) @No__t_2 bildiriminde çalışan kod işleme katılır.

İşlemi yürütmek için, using bloğundaki son bildiri olarak <xref:System.Transactions.TransactionScope.Complete%2A> yöntemini çağırın.

İşlemi geri almak için <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi çağrılmadan önce bir özel durum oluşturun.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>System. Transactions. dll dosyasına bir başvuru eklemek için

1. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.

2. **.Net** sekmesinde (SQL Server projeler için**SQL Server** sekmesinde), **System. Transactions**' ı seçin ve ardından **Tamam**' ı seçin.

     *System. Transactions. dll* öğesine bir başvuru projeye eklenir.

## <a name="to-save-data-in-a-transaction"></a>Verileri bir işlem içinde kaydetmek için

- İşlemi içeren using deyimindeki verileri kaydetmek için kod ekleyin. Aşağıdaki kod, bir using ifadesinde bir <xref:System.Transactions.TransactionScope> nesnesinin nasıl oluşturulduğunu ve örneklendirilendirilecek:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [İzlenecek yol: Bir işlemde veri kaydetme](../data-tools/save-data-in-a-transaction.md)