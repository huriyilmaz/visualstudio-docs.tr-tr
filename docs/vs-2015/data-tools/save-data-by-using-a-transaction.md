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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652828"
---
# <a name="save-data-by-using-a-transaction"></a>Bir işlemi kullanarak veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlemde verileri, <xref:System.Transactions> ad alanını kullanarak kaydedersiniz. <xref:System.Transactions.TransactionScope>Sizin için otomatik olarak yönetilen bir işleme katılmak için nesnesini kullanın.

 Projeler System. Transactions derlemesine bir başvuru ile oluşturulmaz, bu nedenle işlemleri kullanan projelere el ile bir başvuru eklemeniz gerekir.

> [!NOTE]
> <xref:System.Transactions>Ad alanı Windows 2000 veya sonraki sürümlerde desteklenir.

 Bir işlemi uygulamanın en kolay yolu, <xref:System.Transactions.TransactionScope> bir ifadede bir nesne örnekkullanmaktır `using` . (Daha fazla bilgi için bkz. [using deyimleri](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)ve [using deyimleri](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Bildiriminde çalışan kod, `using` işleme katılır.

 İşlemi yürütmek için, <xref:System.Transactions.TransactionScope.Complete%2A> using bloğundaki son ifade olarak yöntemi çağırın.

 İşlemi geri almak için yöntemini çağırmadan önce bir özel durum oluşturun <xref:System.Transactions.TransactionScope.Complete%2A> .

 Daha fazla bilgi için bkz. [verileri bir Işlemde kaydetme](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>System. Transactions dll dosyasına bir başvuru eklemek için

1. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.

2. **.Net** sekmesinde (SQL Server projeler için**SQL Server** sekmesinde), **System. Transactions**' ı seçin ve ardından **Tamam**' ı seçin.

     Projeye System.Transactions.dll bir başvuru eklenir.

### <a name="to-save-data-in-a-transaction"></a>Verileri bir işlem içinde kaydetmek için

- İşlemi içeren using deyimindeki verileri kaydetmek için kod ekleyin. Aşağıdaki kod, using deyimindeki bir nesnenin nasıl oluşturulacağını ve örneklendirilecek <xref:System.Transactions.TransactionScope> :

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
