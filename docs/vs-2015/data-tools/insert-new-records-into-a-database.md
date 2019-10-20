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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651554"
---
# <a name="insert-new-records-into-a-database"></a>Veritabanına yeni kayıtlar ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yeni kayıtları bir veritabanına eklemek için, `TableAdapter.Update` yöntemini veya TableAdapter 'ın DBDirect yöntemlerinden birini (özellikle `TableAdapter.Insert` yöntemi) kullanabilirsiniz.

 Uygulamanız TableAdapters kullanmıyorsa, veritabanınızdaki yeni kayıtları eklemek için komut nesnelerini (örneğin, <xref:System.Data.SqlClient.SqlCommand>) kullanabilirsiniz.

 Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa, `TableAdapter.Update` yöntemini kullanın. @No__t_0 yöntemi tüm değişiklikleri (güncelleştirmeler, ekler ve siler) veritabanına gönderir.

 Uygulamanız verileri depolamak için nesneler kullanıyorsa veya veritabanında yeni kayıtlar oluşturmak için daha ayrıntılı bir denetim istiyorsanız, `TableAdapter.Insert` yöntemini kullanın.

 TableAdapter ' ın bir `Insert` yöntemi yoksa, TableAdapter saklı yordamları kullanacak şekilde yapılandırıldığı veya `GenerateDBDirectMethods` özelliği `false` olarak ayarlandığı anlamına gelir. TableAdapter 'ın `GenerateDBDirectMethods` özelliğini Veri Kümesi Tasarımcısı içinden `true` olarak ayarlamayı deneyin ve ardından veri kümesini kaydedin. Bu, TableAdapter 'ı yeniden oluşturacak. TableAdapter 'ın bir `Insert` yöntemi yoksa, tablo muhtemelen tek tek satırları ayırt etmek için yeterli şema bilgisi sağlamaz (örneğin, tabloda birincil anahtar kümesi olmayabilir).

## <a name="insert-new-records-by-using-tableadapters"></a>TableAdapters kullanarak yeni kayıtlar ekleme
 TableAdapters, uygulamanızın gereksinimlerine bağlı olarak yeni kayıtları bir veritabanına eklemek için farklı yollar sunar.

 Uygulamanız verileri depolamak için veri kümeleri kullanıyorsa, veri kümesindeki istenen <xref:System.Data.DataTable> yeni kayıtlar ekleyebilir ve sonra `TableAdapter.Update` yöntemini çağırabilirsiniz. @No__t_0 yöntemi, <xref:System.Data.DataTable> tüm değişiklikleri veritabanına gönderir (değiştirilen ve silinen kayıtlar dahil).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter. Update yöntemini kullanarak bir veritabanına yeni kayıtlar eklemek için

1. Yeni bir <xref:System.Data.DataRow> oluşturup <xref:System.Data.DataTable.Rows%2A> koleksiyonuna ekleyerek istenen <xref:System.Data.DataTable> yeni kayıtlar ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: DataTable 'A satır ekleme](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Yeni satırlar <xref:System.Data.DataTable> eklendikten sonra, `TableAdapter.Update` yöntemini çağırın. Tüm <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>s dizisini veya tek bir <xref:System.Data.DataRow> geçirerek güncelleştirilecek veri miktarını denetleyebilirsiniz.

    Aşağıdaki kod, bir <xref:System.Data.DataTable> yeni bir kaydın nasıl ekleneceğini ve sonra yeni satırı veritabanına kaydetmek için `TableAdapter.Update` metodunu çağırılacağını gösterir. (Bu örnek, Northwind veritabanındaki `Region` tablosunu kullanır.)

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Uygulamanız verileri depolamak için nesneler kullanıyorsa, doğrudan veritabanında yeni satırlar oluşturmak için `TableAdapter.Insert` yöntemini kullanabilirsiniz. @No__t_0 yöntemi her bir sütunun parametre olarak ayrı değerlerini kabul eder. Yöntemi çağırmak, veritabanına geçirilen parametre değerleriyle yeni bir kayıt ekler.

   Aşağıdaki yordam bir örnek olarak Northwind veritabanındaki `Region` tablosunu kullanır.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter. Insert metodunu kullanarak bir veritabanına yeni kayıtlar eklemek için

- Her bir sütunun değerlerini parametre olarak geçirerek TableAdapter 'ın `Insert` yöntemini çağırın.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Komut nesnelerini kullanarak yeni kayıtlar ekleme
 Aşağıdaki örnek, komut nesnelerini kullanarak doğrudan bir veritabanına yeni kayıtlar ekler.

 Aşağıdaki yordam bir örnek olarak Northwind veritabanındaki `Region` tablosunu kullanır.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Komut nesnelerini kullanarak bir veritabanına yeni kayıtlar eklemek için

- Yeni bir komut nesnesi oluşturun ve ardından `Connection`, `CommandType` ve `CommandText` özelliklerini ayarlayın.

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği
 Bağlanmaya çalıştığınız veritabanına erişiminizin yanı sıra, istenen tabloya ekleme yapma iznini de yapmanız gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
