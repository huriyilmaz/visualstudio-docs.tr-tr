---
title: Verileri bir nesneden veritabanına kaydetme
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 4afa0d376366b154501e1a0e4488af57b4448a32
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281662"
---
# <a name="save-data-from-an-object-to-a-database"></a>Verileri bir nesneden veritabanına kaydetme

Nesneleri, nesne içindeki verileri TableAdapter 'ın DBDirect metotlarından birine geçirerek bir veritabanına kaydedebilirsiniz (örneğin, `TableAdapter.Insert` ). Daha fazla bilgi için bkz. [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Bir nesne koleksiyonundan verileri kaydetmek için, nesne koleksiyonu boyunca (örneğin, bir for-Next döngüsü) döngü yapın ve TableAdapter yöntemlerinden birini kullanarak her bir nesne için değerleri veritabanına gönderin `DBDirect` .

Varsayılan olarak, `DBDirect` Yöntemler doğrudan veritabanına karşı çalıştırılabilen bir TableAdapter üzerinde oluşturulur. Bu yöntemler doğrudan çağrılabilir ve <xref:System.Data.DataSet> <xref:System.Data.DataTable> bir veritabanına güncelleştirme göndermek için değişiklikleri mutabık kılma gerektirmez.

> [!NOTE]
> Bir TableAdapter yapılandırırken, ana sorgunun oluşturulacak yöntemler için yeterli bilgi sağlaması gerekir `DBDirect` . Örneğin, bir TableAdapter birincil anahtar sütunu tanımlanmış olmayan bir tablodan verileri sorgulamak üzere yapılandırılmışsa, `DBDirect` Yöntem oluşturmaz.

|TableAdapter DBDirect yöntemi|Description|
| - |-----------------|
|`TableAdapter.Insert`|Veritabanına yeni kayıtlar ekler ve bağımsız sütun değerlerini Yöntem parametreleri olarak geçirmenize olanak sağlar.|
|`TableAdapter.Update`|Bir veritabanındaki mevcut kayıtları güncelleştirir. `Update`Yöntemi, özgün ve yeni sütun değerlerini Yöntem parametreleri olarak alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler bu kaydı güncelleştirmek için kullanılır.<br /><br /> `TableAdapter.Update`Yöntemi, bir veri kümesindeki değişiklikleri <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> <xref:System.Data.DataRow> yöntem parametresi olarak bir,, veya dizisi alarak veritabanına geri mutabık kılmak için de kullanılır.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen özgün sütun değerlerini temel alarak veritabanından varolan kayıtları siler.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Bir nesneden yeni kayıtları bir veritabanına kaydetmek için

- Değerleri yöntemine geçirerek kayıtları oluşturun `TableAdapter.Insert` .

     Aşağıdaki örnek, `Customers` nesnesindeki değerleri yöntemine geçirerek tabloda yeni bir müşteri kaydı oluşturur `currentCustomer` `TableAdapter.Insert` .

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Varolan kayıtları bir nesneden bir veritabanına güncelleştirmek için

- `TableAdapter.Update`Yöntemi çağırarak, kaydı güncelleştirmek için yeni değerleri geçirerek ve kaydı bulmak için özgün değerleri geçirerek kayıtları değiştirin.

    > [!NOTE]
    > Nesneniz, yönteme geçirmek için özgün değerleri sürdürmeniz gerekir `Update` . Bu örnek `orig` , özgün değerleri depolamak için bir ön eki olan özellikleri kullanır.

     Aşağıdaki örnek, `Customers` nesnesi içindeki yeni ve orijinal değerlerini yöntemine geçirerek tablodaki var olan bir kaydı güncelleştirir `Customer` `TableAdapter.Update` .

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Varolan kayıtları bir veritabanından silmek için

- `TableAdapter.Delete`Metodu çağırarak ve kaydı bulmak için özgün değerleri geçirerek kayıtları silin.

    > [!NOTE]
    > Nesneniz, yönteme geçirmek için özgün değerleri sürdürmeniz gerekir `Delete` . Bu örnek `orig` , özgün değerleri depolamak için bir ön eki olan özellikleri kullanır.

     Aşağıdaki örnek, `Customers` nesnesindeki özgün değerleri yöntemine geçirerek tablodaki bir kaydı siler `Customer` `TableAdapter.Delete` .

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>.NET güvenliği

`INSERT`Veritabanında seçili, veya öğesini gerçekleştirmek için izninizin olması gerekir `UPDATE` `DELETE` .

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
