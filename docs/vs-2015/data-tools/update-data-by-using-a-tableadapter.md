---
title: TableAdapter kullanarak verileri güncelleştirme | Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602328"
---
# <a name="update-data-by-using-a-tableadapter"></a>TableAdapter kullanarak verileri güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri kümenizdeki veriler değiştirildikten ve doğrulandıktan sonra, bir TableAdapter 'ın `Update` yöntemini çağırarak güncelleştirilmiş verileri bir veritabanıya geri gönderebilirsiniz. @No__t_0 yöntemi tek bir veri tablosunu güncelleştirir ve tablodaki her bir veri satırının <xref:System.Data.DataRow.RowState%2A> göre doğru komutu (INSERT, UPDATE veya DELETE) çalıştırır. Bir veri kümesinde ilgili tablolar olduğunda Visual Studio, güncelleştirmeleri yapmak için kullandığınız bir TableAdapterManager sınıfı oluşturur. TableAdapterManager sınıfı, güncelleştirmelerin veritabanında tanımlanan yabancı anahtar kısıtlamalarına göre doğru sırada yapılmasını sağlar. Veriye dayalı denetimleri kullandığınızda, veri bağlama mimarisi tableAdapterManager adlı TableAdapterManager sınıfının bir üye değişkenini oluşturur. Daha fazla bilgi için bkz. [Hiyerarşik Güncelleştirmeye Genel Bakış](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).

> [!NOTE]
> Bir veri kaynağını bir veri kümesinin içeriğiyle güncelleştirmeyi denediğinizde, hata alabilirsiniz. Hataları önlemek için, bağdaştırıcının `Update` yöntemini çağıran kodu bir `try` / `catch` bloğu içine koymanızı öneririz.

 Bir veri kaynağını güncelleştirmeye yönelik tam yordam, iş ihtiyaçlarına bağlı olarak farklılık gösterebilir, ancak aşağıdaki adımları içerir:

1. Bağdaştırıcının `Update` yöntemini bir `try` / `catch` bloğunda çağırın.

2. Bir özel durum yakalanmışsa, hataya neden olan veri satırını bulun. Daha fazla bilgi için bkz. [nasıl yapılır: hata Içeren satırları bulma](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).

3. Veri satırındaki sorunu uzlaştırır (veya mümkünse, Kullanıcı tarafından değişiklik için geçersiz satırı sunarak) ve güncelleştirmeyi yeniden deneyin (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="savedata-to-a-database"></a>Bir veritabanına SaveData
 TableAdapter 'ın `Update` yöntemini çağırın. Veritabanına yazılacak değerleri içeren veri tablosunun adını geçirin.

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>TableAdapter kullanarak bir veritabanını güncelleştirmek için

- TableAdapter 'ın `Update` yöntemini bir `try` / `catch` bloğuna iliştirin. Aşağıdaki örnek, bir `try` / `catch` bloğunun içinden `NorthwindDataSet` `Customers` tablonun içeriğini nasıl güncelleşkullanabileceğinizi gösterir.

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
