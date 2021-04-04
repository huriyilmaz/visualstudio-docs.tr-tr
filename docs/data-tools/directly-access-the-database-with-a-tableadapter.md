---
title: Bir TableAdapter ile veritabanına doğrudan erişme
description: Doğrudan veritabanındaki verileri işlemek için INSERT, Update ve DELETE gibi yöntemleri kullanarak bir TableAdapter ile veritabanına doğrudan erişin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30248632eacde07cfcc94213aeeb75ecac8dcf70
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215922"
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

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>Kayıtları doğrudan bir veritabanında güncelleştirmek için

- `Update`Her sütun için yeni ve orijinal değerlerini parametre olarak geçirerek TableAdapter metodunu çağırın.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>Kayıtları doğrudan veritabanından silmek için

- `Delete`Her bir sütunun değerlerini metodun parametreleri olarak geçirerek TableAdapter metodunu çağırın `Delete` . Aşağıdaki yordam `Region` bir örnek olarak Northwind veritabanındaki tabloyu kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
