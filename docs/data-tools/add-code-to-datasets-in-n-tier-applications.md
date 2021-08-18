---
title: N katmanlı uygulamalarda Veri Kümelerine kod ekleme
description: Uygulama içinde n katmanlı uygulamalarda veri kümelere kod Visual Studio. Veri kümesi için kısmi bir sınıf dosyası oluşturun ve buna kod ekleyin (DatasetName.Dataset.Designer yerine).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7df5c2fd963ce628f146bde5b8df754866898b20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134834"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda Veri Kümelerine kod ekleme

Veri kümesi için kısmi bir sınıf dosyası oluşturarak ve buna kod ekleyerek *(DatasetName'e* kod eklemek yerine) veri kümesi işlevselliğini genişletebilirsiniz. Dataset.Designer dosyası). Kısmi sınıflar, belirli bir sınıfın birden çok fiziksel dosya arasında bölünmesi için kodu etkinleştirir. Daha fazla bilgi için [bkz. Kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) [veya Kısmi sınıflar ve yöntemleri.](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)

Veri kümesi tanımında her değişiklik (türü oluşturulan veri kümesinde) yapılan her değişiklikte bir veri kümesi tanımlayan kod oluşturulur. Bu kod, bir veri kümesi yapılandırmasını değiştiren herhangi bir sihirbazın çalıştırması sırasında değişiklik yaptığınız zaman da oluşturulur. Bir veri kümesi yeniden oluşturulurken kodunuzun silinmesini önlemek için, veri kümesi kısmi sınıf dosyasına kod ekleyin.

Varsayılan olarak, veri kümesi ile TableAdapter kodunu ayırarak her projede ayrı bir sınıf dosyası elde edilen sonuç olur. Özgün projede TableAdapter kodunu içeren *DatasetName.Designer.vb* (veya *DatasetName.Designer.cs*) adlı bir dosya vardır. **DataSet Project** özelliğinde belirlenen projede *DatasetName.DataSet.Designer.vb* (veya *DatasetName.DataSet.Designer.cs)* adlı bir dosya vardır. Bu dosya veri kümesi kodunu içerir.

> [!NOTE]
> DataSet'leri ve TableAdapter'ları ayırarak **(DataSet Project** özelliğini ayarerek), projede mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıfları, veri kümesi projesine el ile taşınmalısınız.

> [!NOTE]
> Doğrulama kodunun ekleniyor olması gerekirken, türü türe sahip veri kümesi oluşturma ve olay <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> işleyicileri için işlevsellik sağlar. Daha fazla bilgi için [bkz. N katmanlı veri kümesine doğrulama ekleme.](../data-tools/add-validation-to-an-n-tier-dataset.md)

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda DataSet'lere kod eklemek için

1. *.xsd dosyasını içeren projeyi* bulun.

2. Veri kümesi **açmak için .xsd** dosyasını seçin.

3. Kod eklemek istediğiniz veri tablosuna sağ tıklayın (başlık çubuğundaki tablo adı) ve ardından Kodu **Görüntüle'yi seçin.**

     Kısmi bir sınıf oluşturulur ve Kod Düzenleyicisi'nde açılır.

4. Kısmi sınıf bildiriminin içine kod ekleyin.

     Aşağıdaki örnek, NorthwindDataSet'te CustomersDataTable'a nereye kod eklen bir değer olduğunu gösterir:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [N Katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [N katmanlı uygulamalarda TableAdapter’lara kod ekleme](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [Hiyerarşik güncelleştirmeye genel bakış](hierarchical-update.md)
- [Visual Studio'de DataSet araçları](../data-tools/dataset-tools-in-visual-studio.md)
