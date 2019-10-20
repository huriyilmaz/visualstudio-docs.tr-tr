---
title: Veritabanına doğrudan TableAdapter ile erişin | Microsoft Docs
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657370"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bir TableAdapter ile veritabanına doğrudan erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0, `UpdateCommand` ve `DeleteCommand` ek olarak, TableAdapters doğrudan veritabanına karşı çalıştırılabilen yöntemlerle oluşturulur. Bu Yöntemler (`TableAdapter.Insert`, `TableAdapter.Update` ve `TableAdapter.Delete`) doğrudan veritabanındaki verileri işlemek için çağrılabilir.

 Bu doğrudan yöntemleri oluşturmak istemiyorsanız, TableAdapter 'ın `GenerateDbDirectMethods` özelliğini **Özellikler** penceresinde `false` olarak ayarlayın. TableAdapter 'ın ana sorgusuna ek olarak bir TableAdapter 'a herhangi bir sorgu eklenirse, bu DbDirect yöntemlerini üretmeyin tek başına sorgulardır.

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdoğrudan bir veritabanına
 Gerçekleştirmeyi denediğiniz görevi gerçekleştiren TableAdapter DbDirect yöntemini çağırın.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Yeni kayıtları doğrudan bir veritabanına eklemek için

- Her bir sütunun değerlerini parametre olarak geçirerek TableAdapter 'ın `Insert` yöntemini çağırın. Aşağıdaki yordam bir örnek olarak Northwind database'teki `Region` tablosunu kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>Kayıtları doğrudan bir veritabanında güncelleştirmek için

- TableAdapter 'ın `Update` yöntemini çağırın, her sütun için yeni ve orijinal değerlerini parametre olarak geçirerek.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>Kayıtları doğrudan veritabanından silmek için

- Her bir sütunun değerlerini `Delete` yönteminin parametreleri olarak geçirerek TableAdapter 'ın `Delete` yöntemini çağırın. Aşağıdaki yordam bir örnek olarak Northwind database'teki `Region` tablosunu kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>Ayrıca Bkz.
 [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
