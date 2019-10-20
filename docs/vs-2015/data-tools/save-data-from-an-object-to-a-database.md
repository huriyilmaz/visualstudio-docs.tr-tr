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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607452"
---
# <a name="save-data-from-an-object-to-a-database"></a>Verileri bir nesneden veritabanına kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nesneleri, nesne içindeki verileri TableAdapter 'ın DBDirect metotlarından birine geçirerek bir veritabanına kaydedebilirsiniz (örneğin, `TableAdapter.Insert`).

 Bir nesne koleksiyonundan verileri kaydetmek için, nesne koleksiyonu boyunca (örneğin, bir for-Next döngüsü) döngü yapın ve TableAdapter DBDirect yöntemlerinden birini kullanarak her bir nesne için değerleri veritabanına gönderin.

 Varsayılan olarak, DBDirect yöntemleri doğrudan veritabanına karşı çalıştırılabilen bir TableAdapter üzerinde oluşturulur. Bu yöntemler doğrudan çağrılabilir ve bir veritabanına güncelleştirme göndermek için <xref:System.Data.DataSet> ya da <xref:System.Data.DataTable> nesnelerin değişikliklere göre mutabık kılınmaması gerekmez.

> [!NOTE]
> Bir TableAdapter yapılandırırken, ana sorgunun, DBDirect yöntemlerinin oluşturulması için yeterli bilgi sağlaması gerekir. Örneğin, bir TableAdapter birincil anahtar sütunu tanımlanmış olmayan bir tablodan verileri sorgulamak üzere yapılandırıldıysa, DBDirect yöntemleri oluşturmaz.

|TableAdapter DBDirect yöntemi|Açıklama|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Veritabanına yeni kayıtlar ekler ve bağımsız sütun değerlerini Yöntem parametreleri olarak geçirmenize olanak sağlar.|
|`TableAdapter.Update`|Bir veritabanındaki mevcut kayıtları güncelleştirir. @No__t_0 yöntemi, özgün ve yeni sütun değerlerini Yöntem parametreleri olarak alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler bu kaydı güncelleştirmek için kullanılır.<br /><br /> @No__t_0 yöntemi, bir veri kümesindeki değişiklikleri bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> veya bir dizi <xref:System.Data.DataRow>s yöntem parametresi olarak bir veritabanına yeniden karşılaştırmak için de kullanılır.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen özgün sütun değerlerini temel alarak veritabanından varolan kayıtları siler.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Bir nesneden yeni kayıtları bir veritabanına kaydetmek için

- Değerleri `TableAdapter.Insert` yöntemine geçirerek kayıtları oluşturun.

     Aşağıdaki örnek, `currentCustomer` nesnesindeki değerleri `TableAdapter.Insert` yöntemine geçirerek `Customers` tabloda yeni bir müşteri kaydı oluşturur.

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Varolan kayıtları bir nesneden bir veritabanına güncelleştirmek için

- @No__t_0 yöntemini çağırarak, kaydı güncelleştirmek için yeni değerleri geçirerek ve kaydı bulmak için özgün değerleri geçirerek kayıtları değiştirin.

    > [!NOTE]
    > Nesnenizin `Update` yöntemine geçebilmesi için özgün değerleri tutması gerekir. Bu örnek, özgün değerleri depolamak için `orig` önekiyle birlikte özellikleri kullanır.

     Aşağıdaki örnek, `Customer` nesnesindeki yeni ve özgün değerleri `TableAdapter.Update` yöntemine geçirerek `Customers` tablodaki var olan bir kaydı güncelleştirir.

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Varolan kayıtları bir veritabanından silmek için

- @No__t_0 yöntemini çağırarak ve kaydı bulmak için özgün değerleri geçirerek kayıtları silin.

    > [!NOTE]
    > Nesnenizin `Delete` yöntemine geçebilmesi için özgün değerleri tutması gerekir. Bu örnek, özgün değerleri depolamak için `orig` önekiyle birlikte özellikleri kullanır.

     Aşağıdaki örnek, `Customer` nesnesindeki özgün değerleri `TableAdapter.Delete` yöntemine geçirerek `Customers` tablosundan bir kaydı siler.

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği
 Veritabanındaki tabloda seçili ekleme, GÜNCELLEŞTIRME veya SILME işlemleri gerçekleştirmek için izninizin olması gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
