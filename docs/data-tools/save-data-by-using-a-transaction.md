---
title: 'Nasıl kullanılır: İşlem kullanarak veri kaydetme'
description: Veri kümesinde DataSet araçlarıyla bir işlem kullanarak veri kaydetmeyi Visual Studio. System.Transactions ad alanını kullanarak bir işlemde veri kaydedebilirsiniz.
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
ms.openlocfilehash: 238c5e82a35db0f2fbc6627bd0bb09d3af8f070b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631226"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Nasıl kullanılır: İşlem kullanarak veri kaydetme

Ad alanını kullanarak bir işlemde veri <xref:System.Transactions> kaydedebilirsiniz. Sizin <xref:System.Transactions.TransactionScope> için otomatik olarak yönetilen bir işlemde katılmak için nesnesini kullanın.

Projeler *System.Transactions* derlemesi başvurusuyla oluşturulmaz, bu nedenle işlemleri kullanan projelere el ile başvuru eklemeniz gerekir.

İşlem uygulamanın en kolay yolu, deyiminde bir <xref:System.Transactions.TransactionScope> nesnenin örneğini `using` oluşturmadır. (Daha fazla bilgi için [bkz. Using deyimi](/dotnet/visual-basic/language-reference/statements/using-statement), ve [Using deyimi](/dotnet/csharp/language-reference/keywords/using-statement).) deyimi içinde çalışan `using` kod, işlemde yer almaktadır.

İşlem işlemek için using <xref:System.Transactions.TransactionScope.Complete%2A> bloğunda son deyim olarak yöntemini çağırma.

İşlem geri almak için yöntemini çağırmadan önce bir özel durum <xref:System.Transactions.TransactionScope.Complete%2A> oluşturur.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>System.Transactions.dll'a başvuru eklemek için

1. Yeni **Project** **Ekle'yi seçin.**

2. **.NET sekmesinde** **(** SQL Server projeleri için SQL Server sekmesi), **System.Transactions 'ı ve** ardından Tamam'ı **seçin.**

     Projeye *System.Transactions.dll* bir başvuru eklenir.

## <a name="to-save-data-in-a-transaction"></a>Bir işlemde veri kaydetmek için

- İşlem içeren using deyimine veri kaydetmek için kod ekleyin. Aşağıdaki kod, using deyiminde nesne oluşturma ve <xref:System.Transactions.TransactionScope> örneği oluşturma adımları gösterir:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet11":::

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [İzlenecek yol: Bir işlemde veri kaydetme](../data-tools/save-data-in-a-transaction.md)
