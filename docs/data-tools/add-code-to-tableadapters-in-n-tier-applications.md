---
title: N katmanlı uygulamalarda TableAdapter’lara kod ekleme
description: N katmanlı uygulamalarda tablo bağdaştırıcılara kod ekleme. TableAdapter için kısmi bir sınıf dosyası oluşturun ve buna kod ekleyin (DatasetName.DataSet.Designer yerine).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 55b6a64953944bacd8fcda73a9edeab00a99afc5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067214"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>N katmanlı uygulamalarda TableAdapter’lara kod ekleme
TableAdapter için kısmi bir sınıf dosyası oluşturarak ve buna kod ekleyerek *(DatasetName.DataSet.Designer* dosyasına kod eklemek yerine) TableAdapter işlevselliğini genişletebilirsiniz. Kısmi sınıflar, belirli bir sınıfın birden çok fiziksel dosya arasında bölünmesi için kodu etkinleştirir. Daha fazla bilgi için [bkz. Kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) [veya kısmi (Tür)](/dotnet/csharp/language-reference/keywords/partial-type).

TableAdapter tanımlayan kod, veri kümesinde TableAdapter üzerinde yapılan her değişiklikte oluşturulur. Bu kod, TableAdapter'ın yapılandırmasını değiştiren herhangi bir sihirbazın çalıştırı sırasında değişiklikler yapılırken de oluşturulur. TableAdapter'ın yeniden oluşturulması sırasında kodunuzun silinmesini önlemek için TableAdapter'ın kısmi sınıf dosyasına kod ekleyin.

Varsayılan olarak, veri kümesi ile TableAdapter kodunu ayırarak her projede ayrı bir sınıf dosyası elde edilen sonuç olur. Özgün projede TableAdapter kodunu içeren *DatasetName.Designer.vb* (veya *DatasetName.Designer.cs*) adlı bir dosya vardır. **Dataset Project** özelliğinde belirlenen projede, veri kümesi kodunu içeren *DatasetName.DataSet.Designer.vb* (veya *DatasetName.DataSet.Designer.cs)* adlı bir dosya vardır.

> [!NOTE]
> Veri kümelerini ve TableAdapter'ları ayırarak **(DataSet Project** özelliğini ayarerek), projede mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut kısmi veri kümesi sınıfları, veri kümesi projesine el ile taşınmalısınız.

> [!NOTE]
> Veri kümesi, doğrulama gerektiğinde oluşturma ve <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> olay işleyicileri için işlevsellik sağlar. Daha fazla bilgi için [bkz. N katmanlı veri kümesine doğrulama ekleme.](../data-tools/add-validation-to-an-n-tier-dataset.md)

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N katmanlı bir uygulamada TableAdapter'a kullanıcı kodu eklemek için

1. *.xsd dosyasını içeren projeyi* bulun.

2. *.xsd dosyasına çift* tıklar ve **Veri Kümesi Tasarımcısı.**

3. Kod eklemek istediğiniz TableAdapter'a sağ tıklayın ve Ardından Kodu **Görüntüle'yi seçin.**

     Kısmi bir sınıf oluşturulur ve Kod Düzenleyicisi'nde açılır.

4. Kısmi sınıf bildiriminin içine kod ekleyin.

5. Aşağıdaki örnek, içinde kodun nereye `CustomersTableAdapter` ekli olduğunu `NorthwindDataSet` gösterir:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [N Katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [N katmanlı uygulamalarda veri kümelere kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [Hiyerarşik güncelleştirmeye genel bakış](hierarchical-update.md)
