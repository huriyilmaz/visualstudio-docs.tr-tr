---
title: Bir TableAdapter ile veritabanına doğrudan erişme
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 22d84e9b4beafd64cc629a295bcfa7f9f67afb6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282572"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bir TableAdapter ile veritabanına doğrudan erişme

, Ve ' a ek olarak, `InsertCommand` `UpdateCommand` `DeleteCommand` TableAdapters doğrudan veritabanına karşı çalıştırılabilen yöntemlerle oluşturulur. `TableAdapter.Insert` `TableAdapter.Update` `TableAdapter.Delete` Verileri doğrudan veritabanında işlemek için bu yöntemleri (, ve) çağırabilirsiniz.

Bu doğrudan yöntemleri oluşturmak istemiyorsanız, TableAdapter `GenerateDbDirectMethods` özelliğini `false` **Özellikler** penceresinde olarak ayarlayın. TableAdapter 'ın ana sorgusuna ek olarak bir TableAdapter 'a herhangi bir sorgu eklenirse, bu yöntemleri oluşturan tek başına sorgular vardır `DbDirect` .

## <a name="send-commands-directly-to-a-database"></a>Komutları doğrudan bir veritabanına gönder

`DbDirect`Gerçekleştirmeyi denediğiniz görevi gerçekleştiren TableAdapter metodunu çağırın.

### <a name="to-insert-new-records-directly-into-a-database"></a>Yeni kayıtları doğrudan bir veritabanına eklemek için

- TableAdapter `Insert` metodunu, her bir sütunun değerlerini parametre olarak geçirerek çağırın. Aşağıdaki yordam `Region` bir örnek olarak Northwind veritabanındaki tabloyu kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Kayıtları doğrudan bir veritabanında güncelleştirmek için

- `Update`Her sütun için yeni ve orijinal değerlerini parametre olarak geçirerek TableAdapter metodunu çağırın.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Kayıtları doğrudan veritabanından silmek için

- `Delete`Her bir sütunun değerlerini metodun parametreleri olarak geçirerek TableAdapter metodunu çağırın `Delete` . Aşağıdaki yordam `Region` bir örnek olarak Northwind veritabanındaki tabloyu kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
