---
title: TableAdapter kullanarak verileri güncelleştirme
description: Veri kümesindeki verileri güncelleştirme. Bir TableAdapter 'ın Update yöntemini çağırarak verileri veritabanına geri gönderin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 38f804232dd633be82e328716312c9c8f1cf53e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036790"
---
# <a name="update-data-by-using-a-tableadapter"></a>TableAdapter kullanarak verileri güncelleştirme

Veri kümenizdeki veriler değiştirildikten ve doğrulandıktan sonra, `Update` bir [TableAdapter](../data-tools/create-and-configure-tableadapters.md)metodunu çağırarak güncelleştirilmiş verileri bir veritabanına geri gönderebilirsiniz. `Update`Yöntemi, tek bir veri tablosunu güncelleştirir ve tablodaki her bir veri satırının temelinde doğru komutu (INSERT, Update veya delete) çalıştırır <xref:System.Data.DataRow.RowState%2A> . bir veri kümesinde ilişkili tablolar olduğunda, Visual Studio güncelleştirmeleri yapmak için kullandığınız bir TableAdapterManager sınıfı oluşturur. TableAdapterManager sınıfı, güncelleştirmelerin veritabanında tanımlanan yabancı anahtar kısıtlamalarına göre doğru sırada yapılmasını sağlar. Veriye dayalı denetimleri kullandığınızda, veri bağlama mimarisi tableAdapterManager adlı TableAdapterManager sınıfının bir üye değişkenini oluşturur.

> [!NOTE]
> Bir veri kaynağını bir veri kümesinin içeriğiyle güncelleştirmeyi denediğinizde, hata alabilirsiniz. Hataları önlemek için, bağdaştırıcının yöntemini çağıran kodu `Update` bir blok içinde koymanız önerilir `try` / `catch` .

Bir veri kaynağını güncelleştirmeye yönelik tam yordam, iş ihtiyaçlarına bağlı olarak farklılık gösterebilir, ancak aşağıdaki adımları içerir:

1. `Update`Bir blokta bağdaştırıcının yöntemini çağırın `try` / `catch` .

2. Bir özel durum yakalanmışsa, hataya neden olan veri satırını bulun.

3. Veri satırındaki sorunu uzlaştırır (veya mümkünse, Kullanıcı tarafından değişiklik için geçersiz satırı sunarak) ve sonra güncelleştirmeyi yeniden deneyin ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="save-data-to-a-database"></a>Verileri bir veritabanına kaydetme

`Update`TableAdapter metodunu çağırın. Veritabanına yazılacak değerleri içeren veri tablosunun adını geçirin.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>TableAdapter kullanarak bir veritabanını güncelleştirmek için

- TableAdapter `Update` metodunu bir blokta çevrelemek `try` / `catch` . Aşağıdaki örnek, `Customers` içindeki tablosunun içeriğini `NorthwindDataSet` bir blok içinden nasıl güncelleşleyeceğinizi gösterir `try` / `catch` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet9":::

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
