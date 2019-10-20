---
title: N katmanlı uygulamalarda TableAdapters 'e kod ekleme | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673097"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>N katmanlı uygulamalarda TableAdapter’lara kod ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_1 için kısmi bir sınıf dosyası oluşturarak ve ona kod ekleyerek bir `TableAdapter` işlevselliğini genişletebilirsiniz ( *DataSetName*'e kod eklemek yerine). DataSet. Designer dosyası). Kısmi sınıflar, belirli bir sınıfın kodunu birden çok fiziksel dosyaya bölünecek şekilde etkinleştirir. Daha fazla bilgi için bkz. [kısmi](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) veya [kısmi (tür)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 @No__t_0 tanımlayan kod, `TableAdapter` her değişiklik yapıldığında oluşturulur. Bu kod ayrıca, `TableAdapter` yapılandırmasını değiştiren herhangi bir sihirbazın çalıştırılması sırasında değişiklik yapıldığında da oluşturulur. @No__t_0 yeniden oluşturma sırasında kodunuzun silinmesini engellemek için, `TableAdapter` kısmi sınıf dosyasına kod ekleyin.

 Varsayılan olarak, veri kümesini ve `TableAdapter` kodunu ayırdıktan sonra sonuç, her projedeki ayrı bir sınıf dosyasıdır. Özgün projenin *DataSetName*adlı bir dosyası vardır. Designer. vb (veya *DataSetName*. Designer.cs) `TableAdapter` kodu içerir. **DataSet projesi** özelliğinde belirtilen proje, *DataSetName*adlı bir dosya içerir. DataSet. Designer. vb (veya *DataSetName*. DataSet.Designer.cs) veri kümesi kodunu içerir.

> [!NOTE]
> Veri kümelerini ve `TableAdapter`s ayırdığınızda ( **DataSet proje** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

> [!NOTE]
> Veri kümesi Tasarımcısı, doğrulama gerektiğinde <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olay işleyicileri oluşturmak için işlevsellik sağlar. Daha fazla bilgi için bkz. [n katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N katmanlı bir uygulamadaki bir TableAdapter 'a Kullanıcı kodu eklemek için

1. . Xsd dosyasını (veri kümesi) içeren projeyi bulun.

2. Veri kümesini açmak için **. xsd** dosyasına çift tıklayın.

3. Kodu eklemek istediğiniz `TableAdapter` sağ tıklatın ve ardından**kodu görüntüle**' yi seçin.

     Kod düzenleyicisinde kısmi bir sınıf oluşturulur ve açılır.

4. Kısmi sınıf bildiriminin içine kod ekleyin.

5. Aşağıdaki örnek, `NorthwindDataSet` `CustomersTableAdapter` kodun nereye ekleneceğini gösterir:

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

## <a name="see-also"></a>Ayrıca Bkz.
 [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md) [n katmanlı uygulamalardaki veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [TableAdapterManager genel bakış](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) [hiyerarşik güncelleştirmesine genel bakış](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)