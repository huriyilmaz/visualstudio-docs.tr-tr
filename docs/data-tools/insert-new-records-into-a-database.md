---
title: Veritabanına yeni kayıtlar ekleme
description: TableAdapter'ın DBDirect yöntemlerinden biri olan TableAdapter.Update yöntemini veya komut nesnelerini kullanarak veritabanına yeni kayıtlar ekler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7b3fbea039c82210c135b26c918ca18c757816b5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113919"
---
# <a name="insert-new-records-into-a-database"></a>Veritabanına yeni kayıtlar ekleme

Veritabanına yeni kayıtlar eklemek için yöntemini veya `TableAdapter.Update` TableAdapter'ın DBDirect yöntemlerinden birini (özellikle yöntemi) `TableAdapter.Insert` kullanabilirsiniz. Daha fazla bilgi için bkz. [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Uygulamanız TableAdapter'ları kullanamasa, veritabanınıza yeni kayıtlar eklemek için komut nesnelerini (örneğin,  <xref:System.Data.SqlClient.SqlCommand> ) kullanabilirsiniz.

Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa yöntemini `TableAdapter.Update` kullanın. yöntemi `Update` tüm değişiklikleri (güncelleştirmeler, eklemeler ve silmeler) veritabanına gönderir.

Uygulamanız verileri depolamak için nesneler kullanıyorsa veya veritabanında yeni kayıtlar oluşturma üzerinde daha iyi denetim sahibi olmak için yöntemini `TableAdapter.Insert` kullanın.

TableAdapter'nizin bir yöntemi yoksa, TableAdapter saklı yordamları kullanmak üzere yapılandırılmış veya özelliği `Insert` `GenerateDBDirectMethods` olarak ayarlanmış `false` demektir. TableAdapter özelliğini Veri Kümesi Tasarımcısı içinde olarak `GenerateDBDirectMethods` `true` **ayarlamayı deneyin** ve ardından veri kümenizi kaydedin. TableAdapter yeniden oluşturulur. TableAdapter hala bir yöntemi yoksa, tablo büyük olasılıkla tek tek satırları ayırt etmek için yeterli şema bilgisi sağlamaz (örneğin, tabloda birincil anahtar kümesi `Insert` yoktur).

## <a name="insert-new-records-by-using-tableadapters"></a>TableAdapter'ları kullanarak yeni kayıtlar ekleme

TableAdapter'lar, uygulama gereksinimlerine bağlı olarak veritabanına yeni kayıtlar eklemek için farklı yollar sağlar.

Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa, veri kümesinde istenene yeni kayıtlar ekleyebilir ve <xref:System.Data.DataTable> ardından yöntemini `TableAdapter.Update` çağırabilirsiniz. yöntemi `TableAdapter.Update` veritabanındaki tüm değişiklikleri <xref:System.Data.DataTable> (değiştirilen ve silinen kayıtlar dahil) gönderir.

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter.Update yöntemini kullanarak veritabanına yeni kayıtlar eklemek için

1. Yeni bir oluşturarak ve <xref:System.Data.DataTable> koleksiyona ekleyerek <xref:System.Data.DataRow> istenene yeni kayıtlar <xref:System.Data.DataTable.Rows%2A> ekleyin.

2. 'ye yeni satırlar eklendikten <xref:System.Data.DataTable> sonra yöntemini `TableAdapter.Update` çağırma. Tüm , , bir dizi s veya tek bir ile geçerek güncelleştirilen veri miktarını <xref:System.Data.DataSet> <xref:System.Data.DataTable> kontrol altına <xref:System.Data.DataRow> <xref:System.Data.DataRow> aabilirsiniz.

   Aşağıdaki kod, yeni bir kayda nasıl yeni bir kayıt ekleyen ve sonra yeni satırı <xref:System.Data.DataTable> `TableAdapter.Update` veritabanına kaydetmek için yöntemini çağırmayı gösterir. (Bu örnekte `Region` Northwind veritabanındaki tablo kullanılır.)

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb" id="Snippet14":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs" id="Snippet14":::

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter.Insert yöntemini kullanarak veritabanına yeni kayıtlar eklemek için

Uygulamanız verileri depolamak için nesneleri kullanıyorsa, doğrudan veritabanında yeni `TableAdapter.Insert` satırlar oluşturmak için yöntemini kullanabilirsiniz. yöntemi, `Insert` her sütun için ayrı değerleri parametre olarak kabul eder. yönteminin çağrılsı, geçirilen parametre değerleriyle veritabanına yeni bir kayıt ekler.

- TableAdapter yöntemini `Insert` çağırarak her sütunun değerlerini parametre olarak geçirme.

Aşağıdaki yordamda, satır eklemek için `TableAdapter.Insert` yönteminin kullanımı gösterir. Bu `Region` örnek, Northwind veritabanındaki tabloya veri ekler.

> [!NOTE]
> Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini seçin.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

## <a name="insert-new-records-by-using-command-objects"></a>Komut nesnelerini kullanarak yeni kayıtlar ekleme

Komut nesnelerini kullanarak yeni kayıtları doğrudan bir veritabanına ebilirsiniz.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Komut nesnelerini kullanarak veritabanına yeni kayıtlar eklemek için

- Yeni bir komut nesnesi oluşturun ve ardından , `Connection` ve `CommandType` özelliklerini `CommandText` ayarlayın.

Aşağıdaki örnek, komut nesnesini kullanarak bir veritabanına kayıt eklemeyi gösterir. `Region`Northwind veritabanındaki tabloya veri ekler.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet16":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet16":::

## <a name="net-security"></a>.NET güvenliği

Bağlanmaya çalıştığınız veritabanına ve istenen tabloya eklemeler gerçekleştirme iznine sahipsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
