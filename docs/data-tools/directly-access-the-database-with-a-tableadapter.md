---
title: Bir TableAdapter ile veritabanına doğrudan erişme
description: Doğrudan veritabanındaki verileri işlemek için Ekleme, Güncelleştirme ve Silme gibi yöntemleri kullanarak TableAdapter ile veritabanına doğrudan erişin.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 18abf137354f6b5a752c217a68e7d70e74dd13fb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631413"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bir TableAdapter ile veritabanına doğrudan erişme

, ve `InsertCommand` `UpdateCommand` `DeleteCommand` ,TableAdapter'lara ek olarak, doğrudan veritabanına karşı çalıştırılan yöntemlerle oluşturulur. Verileri doğrudan veritabanında işlemek için bu yöntemleri ( `TableAdapter.Insert` `TableAdapter.Update` , ve ) `TableAdapter.Delete` çağırabilirsiniz.

Bu doğrudan yöntemleri oluşturmak istemiyorsanız, Özellikler penceresinde TableAdapter'ın `GenerateDbDirectMethods` `false` özelliğini  olarak ayarlayın. TableAdapter'ın ana sorgusuna ek olarak TableAdapter'a sorgu eklenirse, bunlar bu yöntemleri üretemeyen tek başına `DbDirect` sorgulardır.

## <a name="send-commands-directly-to-a-database"></a>Komutları doğrudan bir veritabanına gönderme

Gerçekleştirmeye çalıştığın görevi gerçekleştiren TableAdapter `DbDirect` yöntemini çağırma.

### <a name="to-insert-new-records-directly-into-a-database"></a>Yeni kayıtları doğrudan bir veritabanına eklemek için

- TableAdapter yöntemini `Insert` çağırarak her sütunun değerlerini parametre olarak geçirme. Aşağıdaki yordam `Region` northwind veritabanındaki tabloyu örnek olarak kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini seçin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>Doğrudan bir veritabanındaki kayıtları güncelleştirmek için

- TableAdapter yöntemini çağırarak her sütun için yeni ve `Update` özgün değerleri parametre olarak geçirme.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini seçin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>Kayıtları doğrudan bir veritabanından silmek için

- TableAdapter yöntemini `Delete` çağırarak her sütunun değerlerini yönteminin parametreleri olarak `Delete` geçirme. Aşağıdaki yordam `Region` northwind veritabanındaki tabloyu örnek olarak kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini seçin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
