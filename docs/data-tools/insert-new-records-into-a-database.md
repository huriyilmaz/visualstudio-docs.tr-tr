---
title: Veritabanına yeni kayıtlar ekleme
description: TableAdapter. Update yöntemini, TableAdapter 'ın DBDirect yöntemlerinden birini veya komut nesnelerini kullanarak bir veritabanına yeni kayıtlar ekleyin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631292"
---
# <a name="insert-new-records-into-a-database"></a>Veritabanına yeni kayıtlar ekleme

Yeni kayıtları bir veritabanına eklemek için, `TableAdapter.Update` yöntemini veya TableAdapter DBDirect yöntemlerinden birini (özellikle `TableAdapter.Insert` yöntemi) kullanabilirsiniz. Daha fazla bilgi için bkz. [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Uygulamanız TableAdapters kullanmıyorsa,  <xref:System.Data.SqlClient.SqlCommand> veritabanınızdaki yeni kayıtları eklemek için komut nesnelerini (örneğin,) kullanabilirsiniz.

Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa `TableAdapter.Update` yöntemini kullanın. `Update`Yöntemi tüm değişiklikleri (güncelleştirmeler, ekler ve siler) veritabanına gönderir.

Uygulamanız verileri depolamak için nesneler kullanıyorsa veya veritabanında yeni kayıtlar oluşturmak için daha ayrıntılı bir denetim istiyorsanız `TableAdapter.Insert` yöntemini kullanın.

TableAdapter 'da bir yöntemi yoksa `Insert` , TableAdapter saklı yordamları kullanacak şekilde yapılandırıldığı veya `GenerateDBDirectMethods` özelliği olarak ayarlandığı anlamına gelir `false` . TableAdapter `GenerateDBDirectMethods` özelliğinin özelliğini veri kümesi Tasarımcısı içinden olarak ayarlamayı deneyin `true` ve ardından veri kümesini kaydedin. Bu, TableAdapter 'ı yeniden oluşturacak. TableAdapter `Insert` 'ın bir yöntemi yoksa, tablo muhtemelen tek tek satırları ayırt etmek için yeterli şema bilgisi sağlamaz (örneğin, tabloda birincil anahtar kümesi bulunmayabilir).

## <a name="insert-new-records-by-using-tableadapters"></a>TableAdapters kullanarak yeni kayıtlar ekleme

TableAdapters, uygulamanızın gereksinimlerine bağlı olarak yeni kayıtları bir veritabanına eklemek için farklı yollar sunar.

Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa, veri kümesinde istenen yeni kayıtları eklemek <xref:System.Data.DataTable> ve ardından yöntemini çağırmak yeterlidir `TableAdapter.Update` . `TableAdapter.Update`Yöntemi, içindeki tüm değişiklikleri veritabanına gönderir <xref:System.Data.DataTable> (değiştirilen ve silinen kayıtlar dahil).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter. Update yöntemini kullanarak bir veritabanına yeni kayıtlar eklemek için

1. <xref:System.Data.DataTable>Yeni bir oluşturup koleksiyona ekleyerek istenen yeni kayıtları ekleyin <xref:System.Data.DataRow> <xref:System.Data.DataTable.Rows%2A> .

2. Yeni satırlar öğesine eklendikten sonra <xref:System.Data.DataTable> `TableAdapter.Update` yöntemini çağırın. Güncelleştirilecek veri miktarını <xref:System.Data.DataSet> , bir, bir <xref:System.Data.DataTable> dizi <xref:System.Data.DataRow> veya tek bir olarak geçirerek kontrol edebilirsiniz <xref:System.Data.DataRow> .

   Aşağıdaki kod, bir öğesine nasıl yeni bir kayıt ekleneceğini gösterir <xref:System.Data.DataTable> ve ardından `TableAdapter.Update` yeni satırı veritabanına kaydetmek için yöntemini çağırır. (Bu örnek, `Region` Northwind veritabanındaki tablosunu kullanır.)

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb" id="Snippet14":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs" id="Snippet14":::

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter. Insert metodunu kullanarak bir veritabanına yeni kayıtlar eklemek için

Uygulamanız verileri depolamak için nesneleri kullanıyorsa, `TableAdapter.Insert` doğrudan veritabanında yeni satırlar oluşturmak için yöntemini kullanabilirsiniz. `Insert`Yöntemi her bir sütunun parametre olarak ayrı değerlerini kabul eder. Yöntemi çağırmak, veritabanına geçirilen parametre değerleriyle yeni bir kayıt ekler.

- TableAdapter `Insert` metodunu, her bir sütunun değerlerini parametre olarak geçirerek çağırın.

Aşağıdaki yordamda, `TableAdapter.Insert` satırları eklemek için yönteminin kullanılması gösterilmektedir. Bu örnek `Region` , Northwind veritabanındaki tabloya veri ekler.

> [!NOTE]
> Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

## <a name="insert-new-records-by-using-command-objects"></a>Komut nesnelerini kullanarak yeni kayıtlar ekleme

Komut nesnelerini kullanarak doğrudan bir veritabanına yeni kayıtlar ekleyebilirsiniz.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Komut nesnelerini kullanarak bir veritabanına yeni kayıtlar eklemek için

- Yeni bir komut nesnesi oluşturun ve sonra, `Connection` `CommandType` ve `CommandText` özelliklerini ayarlayın.

Aşağıdaki örnek, komut nesnesi kullanarak bir veritabanına kayıt eklemeyi gösterir. `Region`Northwind veritabanındaki tabloya veri ekler.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet16":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet16":::

## <a name="net-security"></a>.NET güvenliği

Bağlanmaya çalıştığınız veritabanına erişiminizin yanı sıra, istenen tabloya ekleme yapma iznini de yapmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
