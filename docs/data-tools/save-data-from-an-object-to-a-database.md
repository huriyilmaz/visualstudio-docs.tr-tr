---
title: Verileri bir nesneden veritabanına kaydetme
description: DataSet araçlarını kullanarak bir nesneden veritabanına veri Visual Studio. Yeni kayıtları kaydetme, mevcut kayıtları güncelleştirme ve mevcut kayıtları silme hakkında bilgi alın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 96e296be3bb5e591f3da9699fe15371659dddfc0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631202"
---
# <a name="save-data-from-an-object-to-a-database"></a>Verileri bir nesneden veritabanına kaydetme

Nesnenizin değerlerini TableAdapter'ın DBDirect yöntemlerinden (örneğin, ) birilerine aktararak nesnelerdeki verileri veritabanına `TableAdapter.Insert` kaydedebilirsiniz. Daha fazla bilgi için bkz. [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Bir nesne koleksiyonundan veri kaydetmek için, nesne koleksiyonunda döngü oluşturun (örneğin, for-next döngüsü) ve TableAdapter'ın yöntemlerinden birini kullanarak her nesnenin değerlerini veritabanına `DBDirect` gönderin.

Varsayılan `DBDirect` olarak, yöntemler doğrudan veritabanına karşı çalıştırılan bir TableAdapter üzerinde oluşturulur. Bu yöntemler doğrudan çağrılsa da, veya nesnelerinin bir veritabanına güncelleştirme göndermek için değişiklikleri muadele <xref:System.Data.DataSet> <xref:System.Data.DataTable> etmelerini gerektirmez.

> [!NOTE]
> TableAdapter yapılandırıyorken, ana sorgunun oluşturulacak yöntemler için `DBDirect` yeterli bilgi sağlaması gerekir. Örneğin, TableAdapter tanımlı birincil anahtar sütununa sahip bir tablodaki verileri sorgulayacak şekilde yapılandırılmışsa, yöntem `DBDirect` oluşturmaz.

|TableAdapter DBDirect yöntemi|Description|
| - |-----------------|
|`TableAdapter.Insert`|Veritabanına yeni kayıtlar ekler ve tek tek sütun değerlerini yöntem parametreleri olarak geçmenize olanak sağlar.|
|`TableAdapter.Update`|Veritabanındaki mevcut kayıtları güncelleştirme. yöntemi, `Update` yöntem parametreleri olarak özgün ve yeni sütun değerlerini alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler de bu kaydı güncelleştirmek için kullanılır.<br /><br /> yöntemi ayrıca , , veya s dizilerini yöntem parametreleri olarak alarak bir veri kümesinde yapılan değişiklikleri veritabanına geri almak `TableAdapter.Update` <xref:System.Data.DataSet> için de <xref:System.Data.DataTable> <xref:System.Data.DataRow> <xref:System.Data.DataRow> kullanılır.|
|`TableAdapter.Delete`|Yöntem parametresi olarak geçirilen özgün sütun değerlerini temel alarak veritabanındaki mevcut kayıtları siler.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Bir nesneden veritabanına yeni kayıtlar kaydetmek için

- Değerleri yöntemine aktararak kayıtları `TableAdapter.Insert` oluşturun.

     Aşağıdaki örnek, nesnesinde yer alan değerleri `Customers` yöntemine aktararak tabloda yeni `currentCustomer` bir müşteri kaydı `TableAdapter.Insert` oluşturur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Var olan kayıtları bir nesneden veritabanına güncelleştirmek için

- yöntemini çağırarak, kaydı güncelleştirmek için yeni değerleri ve kaydı bulmak için özgün değerleri `TableAdapter.Update` geçerek kayıtları değiştirebilirsiniz.

    > [!NOTE]
    > Nesnenizin yöntemine geçmesi için özgün değerleri sürdürmesi `Update` gerekir. Bu örnek, özgün değerleri depolamak `orig` için bir ön eke sahip özellikleri kullanır.

     Aşağıdaki örnek, nesnesinde yeni ve `Customers` özgün değerleri yöntemine geçerek tablodaki mevcut `Customer` bir kaydı `TableAdapter.Update` güncelleştirir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet24":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet24":::

## <a name="to-delete-existing-records-from-a-database"></a>Veritabanındaki mevcut kayıtları silmek için

- yöntemini çağırarak ve `TableAdapter.Delete` kaydı bulmak için özgün değerleri geçerek kayıtları silin.

    > [!NOTE]
    > Nesnenizin yöntemine geçmesi için özgün değerleri sürdürmesi `Delete` gerekir. Bu örnek, özgün değerleri depolamak `orig` için bir ön eke sahip özellikleri kullanır.

     Aşağıdaki örnek, nesnesinde özgün değerleri `Customers` yöntemine geçerek tablodaki `Customer` bir kaydı `TableAdapter.Delete` siler.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet25":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet25":::

## <a name="net-security"></a>.NET güvenliği

Veritabanındaki tabloda seçili , veya işlemini `INSERT` `UPDATE` gerçekleştirme izniniz `DELETE` olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
