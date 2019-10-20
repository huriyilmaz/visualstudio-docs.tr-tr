---
title: İşlem kullanarak verileri kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652828"
---
# <a name="save-data-by-using-a-transaction"></a>Bir işlemi kullanarak veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 ad alanını kullanarak bir işleme veri kaydedersiniz. Sizin için otomatik olarak yönetilen bir işleme katılmak üzere <xref:System.Transactions.TransactionScope> nesnesini kullanın.

 Projeler System. Transactions derlemesine bir başvuru ile oluşturulmaz, bu nedenle işlemleri kullanan projelere el ile bir başvuru eklemeniz gerekir.

> [!NOTE]
> @No__t_0 ad alanı Windows 2000 veya sonraki sürümlerde desteklenir.

 Bir işlemi uygulamanın en kolay yolu, bir `using` bildiriminde <xref:System.Transactions.TransactionScope> nesnesini örnekleyekullanmaktır. (Daha fazla bilgi için bkz. [using deyimleri](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)ve [using deyimleri](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) @No__t_2 bildiriminde çalışan kod işleme katılır.

 İşlemi yürütmek için, using bloğundaki son bildiri olarak <xref:System.Transactions.TransactionScope.Complete%2A> yöntemini çağırın.

 İşlemi geri almak için <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi çağrılmadan önce bir özel durum oluşturun.

 Daha fazla bilgi için bkz. [verileri bir Işlemde kaydetme](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>System. Transactions dll dosyasına bir başvuru eklemek için

1. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.

2. **.Net** sekmesinde (SQL Server projeler için**SQL Server** sekmesinde), **System. Transactions**' ı seçin ve ardından **Tamam**' ı seçin.

     System. Transactions. dll öğesine bir başvuru projeye eklenir.

### <a name="to-save-data-in-a-transaction"></a>Verileri bir işlem içinde kaydetmek için

- İşlemi içeren using deyimindeki verileri kaydetmek için kod ekleyin. Aşağıdaki kod, bir using ifadesinde bir <xref:System.Transactions.TransactionScope> nesnesinin nasıl oluşturulduğunu ve örneklendirilendirilecek:

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
