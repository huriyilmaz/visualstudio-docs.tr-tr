---
title: TableAdapter kullanarak verileri güncelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b54aeb91ea873b23b1e68731e40542df04fcbd01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648120"
---
# <a name="update-data-by-using-a-tableadapter"></a>TableAdapter kullanarak verileri güncelleştirme

Veri kümenizdeki veriler değiştirildikten ve doğrulandıktan sonra, bir [TableAdapter](../data-tools/create-and-configure-tableadapters.md)'ın `Update` yöntemini çağırarak güncelleştirilmiş verileri bir veritabanına geri gönderebilirsiniz. @No__t_0 yöntemi tek bir veri tablosunu güncelleştirir ve tablodaki her bir veri satırının <xref:System.Data.DataRow.RowState%2A> göre doğru komutu (INSERT, UPDATE veya DELETE) çalıştırır. Bir veri kümesinde ilgili tablolar olduğunda Visual Studio, güncelleştirmeleri yapmak için kullandığınız bir TableAdapterManager sınıfı oluşturur. TableAdapterManager sınıfı, güncelleştirmelerin veritabanında tanımlanan yabancı anahtar kısıtlamalarına göre doğru sırada yapılmasını sağlar. Veriye dayalı denetimleri kullandığınızda, veri bağlama mimarisi tableAdapterManager adlı TableAdapterManager sınıfının bir üye değişkenini oluşturur.

> [!NOTE]
> Bir veri kaynağını bir veri kümesinin içeriğiyle güncelleştirmeyi denediğinizde, hata alabilirsiniz. Hataları önlemek için, bağdaştırıcının `Update` yöntemini çağıran kodu bir `try` / `catch` bloğu içine koymanızı öneririz.

Bir veri kaynağını güncelleştirmeye yönelik tam yordam, iş ihtiyaçlarına bağlı olarak farklılık gösterebilir, ancak aşağıdaki adımları içerir:

1. Bağdaştırıcının `Update` yöntemini bir `try` / `catch` bloğunda çağırın.

2. Bir özel durum yakalanmışsa, hataya neden olan veri satırını bulun.

3. Veri satırındaki sorunu uzlaştırır (veya mümkünse, Kullanıcı tarafından değişiklik için geçersiz satırı sunarak) ve güncelleştirmeyi yeniden deneyin (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Verileri bir veritabanına kaydetme

TableAdapter 'ın `Update` yöntemini çağırın. Veritabanına yazılacak değerleri içeren veri tablosunun adını geçirin.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>TableAdapter kullanarak bir veritabanını güncelleştirmek için

- TableAdapter 'ın `Update` yöntemini bir `try` / `catch` bloğuna iliştirin. Aşağıdaki örnek, bir `try` / `catch` bloğunun içinden `NorthwindDataSet` `Customers` tablonun içeriğini nasıl güncelleşkullanabileceğinizi gösterir.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)