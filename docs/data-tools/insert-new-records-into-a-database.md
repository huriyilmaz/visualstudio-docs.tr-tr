---
title: Veritabanına yeni kayıtlar ekleme
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3a3830c9dd1921939ced3577b7bafa22772b49f6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586425"
---
# <a name="insert-new-records-into-a-database"></a>Veritabanına yeni kayıtlar ekleme

Yeni kayıtları bir veritabanına eklemek için, `TableAdapter.Update` yöntemini veya TableAdapter 'ın DBDirect yöntemlerinden birini (özellikle `TableAdapter.Insert` yöntemi) kullanabilirsiniz. Daha fazla bilgi için bkz. [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Uygulamanız TableAdapters kullanmıyorsa, veritabanınızdaki yeni kayıtları eklemek için komut nesnelerini (örneğin, <xref:System.Data.SqlClient.SqlCommand>) kullanabilirsiniz.

Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa, `TableAdapter.Update` yöntemini kullanın. `Update` yöntemi tüm değişiklikleri (güncelleştirmeler, ekler ve siler) veritabanına gönderir.

Uygulamanız verileri depolamak için nesneler kullanıyorsa veya veritabanında yeni kayıtlar oluşturmak için daha ayrıntılı bir denetim istiyorsanız, `TableAdapter.Insert` yöntemini kullanın.

TableAdapter ' ın bir `Insert` yöntemi yoksa, TableAdapter saklı yordamları kullanacak şekilde yapılandırıldığı veya `GenerateDBDirectMethods` özelliği `false`olarak ayarlandığı anlamına gelir. TableAdapter 'ın `GenerateDBDirectMethods` özelliğini **veri kümesi Tasarımcısı**içinden `true` olarak ayarlamayı deneyin ve ardından veri kümesini kaydedin. Bu, TableAdapter 'ı yeniden oluşturacak. TableAdapter 'ın bir `Insert` yöntemi yoksa, tablo muhtemelen tek tek satırları ayırt etmek için yeterli şema bilgisi sağlamaz (örneğin, tabloda birincil anahtar kümesi olmayabilir).

## <a name="insert-new-records-by-using-tableadapters"></a>TableAdapters kullanarak yeni kayıtlar ekleme

TableAdapters, uygulamanızın gereksinimlerine bağlı olarak yeni kayıtları bir veritabanına eklemek için farklı yollar sunar.

Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa, veri kümesindeki istenen <xref:System.Data.DataTable> yeni kayıtlar ekleyebilir ve sonra `TableAdapter.Update` yöntemini çağırabilirsiniz. `TableAdapter.Update` yöntemi, <xref:System.Data.DataTable> tüm değişiklikleri veritabanına gönderir (değiştirilen ve silinen kayıtlar dahil).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter. Update yöntemini kullanarak bir veritabanına yeni kayıtlar eklemek için

1. Yeni bir <xref:System.Data.DataRow> oluşturup <xref:System.Data.DataTable.Rows%2A> koleksiyonuna ekleyerek istenen <xref:System.Data.DataTable> yeni kayıtlar ekleyin.

2. Yeni satırlar <xref:System.Data.DataTable>eklendikten sonra, `TableAdapter.Update` yöntemini çağırın. <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>bir dizi veya tek bir <xref:System.Data.DataRow>geçirerek güncelleştirilecek veri miktarını kontrol edebilirsiniz.

   Aşağıdaki kod, bir <xref:System.Data.DataTable> yeni bir kaydın nasıl ekleneceğini ve sonra yeni satırı veritabanına kaydetmek için `TableAdapter.Update` metodunu çağırılacağını gösterir. (Bu örnek, Northwind veritabanındaki `Region` tablosunu kullanır.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter. Insert metodunu kullanarak bir veritabanına yeni kayıtlar eklemek için

Uygulamanız verileri depolamak için nesneler kullanıyorsa, doğrudan veritabanında yeni satırlar oluşturmak için `TableAdapter.Insert` yöntemini kullanabilirsiniz. `Insert` yöntemi her bir sütunun parametre olarak ayrı değerlerini kabul eder. Yöntemi çağırmak, veritabanına geçirilen parametre değerleriyle yeni bir kayıt ekler.

- Her bir sütunun değerlerini parametre olarak geçirerek TableAdapter 'ın `Insert` yöntemini çağırın.

Aşağıdaki yordamda, satırları eklemek için `TableAdapter.Insert` yönteminin kullanımı gösterilmektedir. Bu örnek, Northwind veritabanındaki `Region` tablosuna veri ekler.

> [!NOTE]
> Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Komut nesnelerini kullanarak yeni kayıtlar ekleme

Komut nesnelerini kullanarak doğrudan bir veritabanına yeni kayıtlar ekleyebilirsiniz.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Komut nesnelerini kullanarak bir veritabanına yeni kayıtlar eklemek için

- Yeni bir komut nesnesi oluşturun ve ardından `Connection`, `CommandType`ve `CommandText` özelliklerini ayarlayın.

Aşağıdaki örnek, komut nesnesi kullanarak bir veritabanına kayıt eklemeyi gösterir. Northwind veritabanındaki `Region` tablosuna veri ekler.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>.NET güvenliği

Bağlanmaya çalıştığınız veritabanına erişiminizin yanı sıra, istenen tabloya ekleme yapma iznini de yapmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
