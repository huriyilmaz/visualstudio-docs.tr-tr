---
title: Verileri bir nesneden veritabanına kaydetme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 509910730d4da095b6db622212716a8f958495d7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586269"
---
# <a name="save-data-from-an-object-to-a-database"></a>Verileri bir nesneden veritabanına kaydetme

Nesneleri, nesne içindeki verileri TableAdapter 'ın DBDirect metotlarından birine geçirerek bir veritabanına kaydedebilirsiniz (örneğin, `TableAdapter.Insert`). Daha fazla bilgi için bkz. [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Bir nesne koleksiyonundan verileri kaydetmek için, nesne koleksiyonu boyunca (örneğin, bir for-Next döngüsü) döngü yapın ve TableAdapter 'ın `DBDirect` yöntemlerinden birini kullanarak her bir nesne için değerleri veritabanına gönderin.

Varsayılan olarak, doğrudan veritabanına karşı çalıştırılabilen bir TableAdapter üzerinde `DBDirect` Yöntemler oluşturulur. Bu yöntemler doğrudan çağrılabilir ve bir veritabanına güncelleştirme göndermek için <xref:System.Data.DataSet> ya da <xref:System.Data.DataTable> nesnelerin değişikliklere göre mutabık kılınmaması gerekmez.

> [!NOTE]
> Bir TableAdapter yapılandırırken, ana sorgu `DBDirect` yöntemlerinin oluşturulması için yeterli bilgi sağlamalıdır. Örneğin, bir TableAdapter birincil anahtar sütunu tanımlanmış olmayan bir tablodan verileri sorgulamak üzere yapılandırılmışsa, `DBDirect` Yöntemler oluşturmaz.

|TableAdapter DBDirect yöntemi|Açıklama|
| - |-----------------|
|`TableAdapter.Insert`|Veritabanına yeni kayıtlar ekler ve bağımsız sütun değerlerini Yöntem parametreleri olarak geçirmenize olanak sağlar.|
|`TableAdapter.Update`|Mevcut veritabanındaki kayıtları güncelleştirir. `Update` yöntemi, özgün ve yeni sütun değerlerini Yöntem parametreleri olarak alır. Orijinal değerleri özgün kaydı bulmak için kullanılır ve bu kaydı güncelleştirmek için yeni değerler kullanılır.<br /><br /> `TableAdapter.Update` yöntemi, bir veri kümesindeki değişiklikleri bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>veya bir dizi <xref:System.Data.DataRow>yöntem parametresi olarak geçirerek veritabanına geri dönmek için de kullanılır.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen var olan kayıtların özgün sütun değerlerine göre veritabanından siler.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Bir nesneden yeni kayıtları bir veritabanına kaydetmek için

- Değerleri `TableAdapter.Insert` yöntemine geçirerek kayıtları oluşturun.

     Aşağıdaki örnek, `currentCustomer` nesnesindeki değerleri `TableAdapter.Insert` yöntemine geçirerek `Customers` tabloda yeni bir müşteri kaydı oluşturur.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Varolan kayıtları bir nesneden bir veritabanına güncelleştirmek için

- `TableAdapter.Update` yöntemini çağırarak, kaydı güncelleştirmek için yeni değerleri geçirerek ve kaydı bulmak için özgün değerleri geçirerek kayıtları değiştirin.

    > [!NOTE]
    > Nesnenizin `Update` yöntemine geçebilmesi için özgün değerleri tutması gerekir. Bu örnek, özgün değerleri depolamak için `orig` önekiyle birlikte özellikleri kullanır.

     Aşağıdaki örnek, `Customer` nesnesindeki yeni ve özgün değerleri `TableAdapter.Update` yöntemine geçirerek `Customers` tablodaki var olan bir kaydı güncelleştirir.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Varolan kayıtları bir veritabanından silmek için

- `TableAdapter.Delete` yöntemini çağırarak ve kaydı bulmak için özgün değerleri geçirerek kayıtları silin.

    > [!NOTE]
    > Nesnenizin `Delete` yöntemine geçebilmesi için özgün değerleri tutması gerekir. Bu örnek, özgün değerleri depolamak için `orig` önekiyle birlikte özellikleri kullanır.

     Aşağıdaki örnek, `Customer` nesnesindeki özgün değerleri `TableAdapter.Delete` yöntemine geçirerek `Customers` tablosundan bir kaydı siler.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>.NET güvenliği

Veritabanındaki tabloda seçili `INSERT`, `UPDATE`veya `DELETE` gerçekleştirmek için izninizin olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
