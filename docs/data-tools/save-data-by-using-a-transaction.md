---
title: 'Nasıl yapılır: işlem kullanarak verileri kaydetme'
description: Visual Studio veri kümesi araçlarıyla bir işlem kullanarak nasıl veri kaydedileceğini inceleyin. System. Transactions ad alanını kullanarak bir işleme veri kaydedersiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5acc25ecb9a370317170d6d419a931414a7dee11ed0b4bcf1c1b4442248d109a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346914"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Nasıl yapılır: işlem kullanarak verileri kaydetme

Bir işlemde verileri, <xref:System.Transactions> ad alanını kullanarak kaydedersiniz. <xref:System.Transactions.TransactionScope>Sizin için otomatik olarak yönetilen bir işleme katılmak için nesnesini kullanın.

Projeler *System. Transactions* derlemesine bir başvuru ile oluşturulmaz, bu nedenle işlemleri kullanan projelere el ile bir başvuru eklemeniz gerekir.

Bir işlemi uygulamanın en kolay yolu, <xref:System.Transactions.TransactionScope> bir ifadede bir nesne örnekkullanmaktır `using` . (Daha fazla bilgi için bkz. [using deyimleri](/dotnet/visual-basic/language-reference/statements/using-statement)ve [using deyimleri](/dotnet/csharp/language-reference/keywords/using-statement).) Bildiriminde çalışan kod, `using` işleme katılır.

İşlemi yürütmek için, <xref:System.Transactions.TransactionScope.Complete%2A> using bloğundaki son ifade olarak yöntemi çağırın.

İşlemi geri almak için yöntemini çağırmadan önce bir özel durum oluşturun <xref:System.Transactions.TransactionScope.Complete%2A> .

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>System.Transactions.dll bir başvuru eklemek için

1. **Project** menüsünde **başvuru ekle**' yi seçin.

2. **.net** sekmesinde (SQL Server projeler için **SQL Server** sekmesinde), **System. Transactions**' ı seçin ve ardından **tamam**' ı seçin.

     Projeye *System.Transactions.dll* bir başvuru eklenir.

## <a name="to-save-data-in-a-transaction"></a>Verileri bir işlem içinde kaydetmek için

- İşlemi içeren using deyimindeki verileri kaydetmek için kod ekleyin. Aşağıdaki kod, using deyimindeki bir nesnenin nasıl oluşturulacağını ve örneklendirilecek <xref:System.Transactions.TransactionScope> :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet11":::

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [İzlenecek yol: Bir işlemde veri kaydetme](../data-tools/save-data-in-a-transaction.md)
