---
title: Veritabanına yeni kayıtlar ekleme | Microsoft Docs
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651554"
---
# <a name="insert-new-records-into-a-database"></a>Veritabanına yeni kayıtlar ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yeni kayıtları bir veritabanına eklemek için, `TableAdapter.Update` yöntemini veya TableAdapter DBDirect yöntemlerinden birini (özellikle `TableAdapter.Insert` yöntemi) kullanabilirsiniz.

 Uygulamanız TableAdapters kullanmıyorsa,  <xref:System.Data.SqlClient.SqlCommand> veritabanınızdaki yeni kayıtları eklemek için komut nesnelerini (örneğin,) kullanabilirsiniz.

 Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa `TableAdapter.Update` yöntemini kullanın. `Update`Yöntemi tüm değişiklikleri (güncelleştirmeler, ekler ve siler) veritabanına gönderir.

 Uygulamanız verileri depolamak için nesneler kullanıyorsa veya veritabanında yeni kayıtlar oluşturmak için daha ayrıntılı bir denetim istiyorsanız `TableAdapter.Insert` yöntemini kullanın.

 TableAdapter 'da bir yöntemi yoksa `Insert` , TableAdapter saklı yordamları kullanacak şekilde yapılandırıldığı veya `GenerateDBDirectMethods` özelliği olarak ayarlandığı anlamına gelir `false` . TableAdapter `GenerateDBDirectMethods` özelliğinin özelliğini veri kümesi Tasarımcısı içinden olarak ayarlamayı deneyin `true` ve ardından veri kümesini kaydedin. Bu, TableAdapter 'ı yeniden oluşturacak. TableAdapter hala bir yönteme sahip değilse `Insert` , tablo muhtemelen tek tek satırları ayırt etmek için yeterli şema bilgisi sağlamaz (örneğin, tabloda birincil anahtar kümesi olmayabilir).

## <a name="insert-new-records-by-using-tableadapters"></a>TableAdapters kullanarak yeni kayıtlar ekleme
 TableAdapters, uygulamanızın gereksinimlerine bağlı olarak yeni kayıtları bir veritabanına eklemek için farklı yollar sunar.

 Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa, veri kümesinde istenen yeni kayıtları eklemek <xref:System.Data.DataTable> ve ardından yöntemini çağırmak yeterlidir `TableAdapter.Update` . `TableAdapter.Update`Yöntemi, içindeki tüm değişiklikleri veritabanına gönderir <xref:System.Data.DataTable> (değiştirilen ve silinen kayıtlar dahil).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter. Update yöntemini kullanarak bir veritabanına yeni kayıtlar eklemek için

1. <xref:System.Data.DataTable>Yeni bir oluşturup koleksiyona ekleyerek istenen yeni kayıtları ekleyin <xref:System.Data.DataRow> <xref:System.Data.DataTable.Rows%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: DataTable 'A satır ekleme](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Yeni satırlar öğesine eklendikten sonra <xref:System.Data.DataTable> `TableAdapter.Update` yöntemini çağırın. Güncelleştirilecek veri miktarını <xref:System.Data.DataSet> , bir, bir <xref:System.Data.DataTable> dizi <xref:System.Data.DataRow> veya tek bir olarak geçirerek kontrol edebilirsiniz <xref:System.Data.DataRow> .

    Aşağıdaki kod, bir öğesine nasıl yeni bir kayıt ekleneceğini gösterir <xref:System.Data.DataTable> ve ardından `TableAdapter.Update` yeni satırı veritabanına kaydetmek için yöntemini çağırır. (Bu örnek, `Region` Northwind veritabanındaki tablosunu kullanır.)

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Uygulamanız verileri depolamak için nesneleri kullanıyorsa, `TableAdapter.Insert` doğrudan veritabanında yeni satırlar oluşturmak için yöntemini kullanabilirsiniz. `Insert`Yöntemi her bir sütunun parametre olarak ayrı değerlerini kabul eder. Yöntemi çağırmak, veritabanına geçirilen parametre değerleriyle yeni bir kayıt ekler.

   Aşağıdaki yordam `Region` bir örnek olarak Northwind veritabanındaki tabloyu kullanır.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter. Insert metodunu kullanarak bir veritabanına yeni kayıtlar eklemek için

- TableAdapter `Insert` metodunu, her bir sütunun değerlerini parametre olarak geçirerek çağırın.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Komut nesnelerini kullanarak yeni kayıtlar ekleme
 Aşağıdaki örnek, komut nesnelerini kullanarak doğrudan bir veritabanına yeni kayıtlar ekler.

 Aşağıdaki yordam `Region` bir örnek olarak Northwind veritabanındaki tabloyu kullanır.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Komut nesnelerini kullanarak bir veritabanına yeni kayıtlar eklemek için

- Yeni bir komut nesnesi oluşturun ve sonra, `Connection` `CommandType` ve `CommandText` özelliklerini ayarlayın.

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği
 Bağlanmaya çalıştığınız veritabanına erişiminizin yanı sıra, istenen tabloya ekleme yapma iznini de yapmanız gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
