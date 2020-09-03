---
title: Bir nesneden bir veritabanına veri kaydetme | Microsoft Docs
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607452"
---
# <a name="save-data-from-an-object-to-a-database"></a>Verileri bir nesneden veritabanına kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nesneleri, nesne içindeki verileri TableAdapter 'ın DBDirect metotlarından birine geçirerek bir veritabanına kaydedebilirsiniz (örneğin, `TableAdapter.Insert` ).

 Bir nesne koleksiyonundan verileri kaydetmek için, nesne koleksiyonu boyunca (örneğin, bir for-Next döngüsü) döngü yapın ve TableAdapter DBDirect yöntemlerinden birini kullanarak her bir nesne için değerleri veritabanına gönderin.

 Varsayılan olarak, DBDirect yöntemleri doğrudan veritabanına karşı çalıştırılabilen bir TableAdapter üzerinde oluşturulur. Bu yöntemler doğrudan çağrılabilir ve <xref:System.Data.DataSet> <xref:System.Data.DataTable> bir veritabanına güncelleştirme göndermek için değişiklikleri mutabık kılma gerektirmez.

> [!NOTE]
> Bir TableAdapter yapılandırırken, ana sorgunun, DBDirect yöntemlerinin oluşturulması için yeterli bilgi sağlaması gerekir. Örneğin, bir TableAdapter birincil anahtar sütunu tanımlanmış olmayan bir tablodan verileri sorgulamak üzere yapılandırıldıysa, DBDirect yöntemleri oluşturmaz.

|TableAdapter DBDirect yöntemi|Açıklama|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Veritabanına yeni kayıtlar ekler ve bağımsız sütun değerlerini Yöntem parametreleri olarak geçirmenize olanak sağlar.|
|`TableAdapter.Update`|Bir veritabanındaki mevcut kayıtları güncelleştirir. `Update`Yöntemi, özgün ve yeni sütun değerlerini Yöntem parametreleri olarak alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler bu kaydı güncelleştirmek için kullanılır.<br /><br /> `TableAdapter.Update`Yöntemi, bir veri kümesindeki değişiklikleri <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> <xref:System.Data.DataRow> yöntem parametresi olarak bir,, veya dizisi alarak veritabanına geri mutabık kılmak için de kullanılır.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen özgün sütun değerlerini temel alarak veritabanından varolan kayıtları siler.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Bir nesneden yeni kayıtları bir veritabanına kaydetmek için

- Değerleri yöntemine geçirerek kayıtları oluşturun `TableAdapter.Insert` .

     Aşağıdaki örnek, `Customers` nesnesindeki değerleri yöntemine geçirerek tabloda yeni bir müşteri kaydı oluşturur `currentCustomer` `TableAdapter.Insert` .

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Varolan kayıtları bir nesneden bir veritabanına güncelleştirmek için

- `TableAdapter.Update`Yöntemi çağırarak, kaydı güncelleştirmek için yeni değerleri geçirerek ve kaydı bulmak için özgün değerleri geçirerek kayıtları değiştirin.

    > [!NOTE]
    > Nesneniz, yönteme geçirmek için özgün değerleri sürdürmeniz gerekir `Update` . Bu örnek `orig` , özgün değerleri depolamak için bir ön eki olan özellikleri kullanır.

     Aşağıdaki örnek, `Customers` nesnesi içindeki yeni ve orijinal değerlerini yöntemine geçirerek tablodaki var olan bir kaydı güncelleştirir `Customer` `TableAdapter.Update` .

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Varolan kayıtları bir veritabanından silmek için

- `TableAdapter.Delete`Metodu çağırarak ve kaydı bulmak için özgün değerleri geçirerek kayıtları silin.

    > [!NOTE]
    > Nesneniz, yönteme geçirmek için özgün değerleri sürdürmeniz gerekir `Delete` . Bu örnek `orig` , özgün değerleri depolamak için bir ön eki olan özellikleri kullanır.

     Aşağıdaki örnek, `Customers` nesnesindeki özgün değerleri yöntemine geçirerek tablodaki bir kaydı siler `Customer` `TableAdapter.Delete` .

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği
 Veritabanındaki tabloda seçili ekleme, GÜNCELLEŞTIRME veya SILME işlemleri gerçekleştirmek için izninizin olması gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
