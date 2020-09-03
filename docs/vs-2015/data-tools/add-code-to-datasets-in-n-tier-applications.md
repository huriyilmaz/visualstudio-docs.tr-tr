---
title: N katmanlı uygulamalardaki veri kümelerine kod ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673110"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümelerine kod ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri kümesi için kısmi bir sınıf dosyası oluşturarak ve buna kod ekleyerek bir veri kümesinin işlevselliğini genişletebilirsiniz ( *DataSetName*'e kod eklemek yerine). DataSet. Designer dosyası). Kısmi sınıflar, belirli bir sınıfın kodunu birden çok fiziksel dosyaya bölünecek şekilde etkinleştirir. Daha fazla bilgi için bkz. [kısmi](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) veya [kısmi sınıflar ve Yöntemler](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

Veri kümesini tanımlayan kod, veri kümesi tanımında her değişiklik yapıldığında oluşturulur. Bu kod ayrıca, bir veri kümesinin yapılandırmasını değiştiren herhangi bir sihirbazın çalıştırılması sırasında değişiklikler yaptığınızda da oluşturulur. Bir veri kümesinin yeniden oluşturulması sırasında kodunuzun silinmesini engellemek için, veri kümesinin kısmi sınıf dosyasına kod ekleyin.

Varsayılan olarak, veri kümesini ve kodu ayırdıktan sonra `TableAdapter` sonuç, her projedeki ayrı bir sınıf dosyasıdır. Özgün projenin *DataSetName*adlı bir dosya vardır. Designer. vb (veya *DataSetName*. Designer.cs) `TableAdapter` kodu içerir. **DataSet proje** özelliğinde belirtilen projede, *DataSetName*adlı bir dosya bulunur. DataSet. Designer. vb (veya *DataSetName*. DataSet.Designer.cs). Bu dosya veri kümesi kodunu içerir.

> [!NOTE]
> Veri kümelerini ve `TableAdapter` öğeleri ( **veri kümesi proje** özelliğini ayarlayarak) ayırdığınızda, projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

> [!NOTE]
> Doğrulama kodunun eklenmesi gerektiğinde, veri kümesi Tasarımcısı, oluşturma <xref:System.Data.DataTable.ColumnChanging> ve olay işleyicileri için işlevsellik sağlar <xref:System.Data.DataTable.RowChanging> . Daha fazla bilgi için bkz. [n katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümelerine kod ekleme

1. . Xsd dosyasını (veri kümesi) içeren projeyi bulun.

2. Veri kümesini açmak için **. xsd** dosyasını seçin.

3. Kod eklemek istediğiniz veri tablosuna (başlık çubuğundaki tablo adı) sağ tıklayın ve ardından **kodu görüntüle**' yi seçin.

     Kod düzenleyicisinde kısmi bir sınıf oluşturulur ve açılır.

4. Kısmi sınıf bildiriminin içine kod ekleyin.

     Aşağıdaki örnek, NorthwindDataSet 'teki CustomersDataTable öğesine kod nereye ekleneceğini gösterir:

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

- [N Katmanlı Veri Uygulamalarına Genel Bakış](../data-tools/n-tier-data-applications-overview.md)
- [N katmanlı uygulamalarda TableAdapter’lara kod ekleme](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [TableAdapterManager genel bakış](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Hiyerarşik Güncelleştirmeye Genel Bakış](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)