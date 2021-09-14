---
title: N Katmanlı bir veri kümesine doğrulama ekleme
description: Veri kümesinde n katmanlı bir veri kümesine doğrulama Visual Studio. Tek tek sütunlarda veya tam satırlarda yapılan değişiklikleri doğrulama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6d9774b45743b57941d08903375d29b663b64192
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631617"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>N Katmanlı bir veri kümesine doğrulama ekleme
N katmanlı bir çözüme ayrılmış bir veri kümesine doğrulama eklemek temelde tek dosyalı bir veri kümesine (tek bir projede veri kümesi) doğrulama eklemekle aynıdır. Veriler üzerinde doğrulama gerçekleştirmek için önerilen konum, veri tablosu <xref:System.Data.DataTable.ColumnChanging> ve/veya <xref:System.Data.DataTable.RowChanging> olayları sırasındadır.

Veri kümesi, veri kümesinde veri tablolarının sütun ve satır değiştirme olaylarına kullanıcı kodu eklerini sağlayan kısmi sınıflar oluşturma işlevi sağlar. N katmanlı bir çözümde bir veri kümesine kod ekleme hakkında daha fazla bilgi için bkz. N katmanlı uygulamalarda veri kümelerine kod ekleme ve [n](../data-tools/add-code-to-datasets-in-n-tier-applications.md)katmanlı uygulamalarda [TableAdapter'lara kod ekleme.](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Kısmi sınıflar hakkında daha fazla bilgi için bkz. [Nasıl yapılacaklar: Sınıfı](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) kısmi sınıflara (Sınıf Tasarımcısı) veya Kısmi sınıflar ve [yöntemlere bölme.](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)

> [!NOTE]
> Veri kümelerini TableAdapter'lardan ayırarak **(DataSet Project** özelliğini ayarerek), projede mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut kısmi veri kümesi sınıfları, veri kümesi projesine el ile taşınmalısınız.

> [!NOTE]
> Veri kümesi Tasarımcısı, ve olayları için C# içinde otomatik olarak olay işleyicileri <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> oluşturmaz. El ile bir olay işleyicisi oluşturmanız ve olay işleyicisini temel alınan olayla bağlamalısınız. Aşağıdaki yordamlar hem Visual Basic hem de C# içinde gerekli olay Visual Basic işleyicileri oluşturma hakkında bilgi sağlar.

## <a name="validate-changes-to-individual-columns"></a>Tek tek sütunlarda yapılan değişiklikleri doğrulama
Olayı işerek tek tek sütunlarda değerleri <xref:System.Data.DataTable.ColumnChanging> doğrulama. Bir <xref:System.Data.DataTable.ColumnChanging> sütundaki değer değiştirildiğinde olay ortaya çıkar. işlevinde istenen sütuna <xref:System.Data.DataTable.ColumnChanging> çift tıklayarak olay için bir olay işleyicisi **Veri Kümesi Tasarımcısı.**

Bir sütuna ilk kez çift tıklarken tasarımcı, olay için bir olay <xref:System.Data.DataTable.ColumnChanging> işleyicisi üretir. Belirli `If...Then` bir sütunu test alan bir deyimi de oluşturulur. Örneğin, Northwind Orders tablosunda **RequiredDate sütununa** çift tıklarken aşağıdaki kod oluşturulur:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> C# projelerinde, Veri Kümesi Tasarımcısı kümesi ve veri kümesinde tek tek tablolar için kısmi sınıflar oluşturur. Bu Veri Kümesi Tasarımcısı, C# içinde ve olayları için otomatik olarak olay <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> işleyici Visual Basic leri oluşturmaz. C# projelerinde, olayı işlemek için el ile bir yöntem oluşturmalı ve yöntemi temel alınan olayla bağlamalısınız. Aşağıdaki yordam hem Visual Basic hem de C# içinde gerekli olay işleyicilerini oluşturma adımlarını sağlar.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Tek tek sütun değerlerine yapılan değişiklikler sırasında doğrulama eklemek için

1. veri kümesinde *.xsd* dosyasına çift tıklayarak veri **Çözüm Gezgini.** Daha fazla bilgi için [bkz. Adım adım kılavuz:](walkthrough-creating-a-dataset-with-the-dataset-designer.md)veri kümesi oluşturma Veri Kümesi Tasarımcısı.

2. Doğrulamak istediğiniz sütuna çift tıklayın. Bu eylem olay <xref:System.Data.DataTable.ColumnChanging> işleyicisini oluşturur.

    > [!NOTE]
    > Bu Veri Kümesi Tasarımcısı C# olayı için otomatik olarak bir olay işleyicisi oluşturmaz. C# ile olayı işlemek için gereken kod sonraki bölümde yer almaktadır. `SampleColumnChangingEvent` oluşturulur ve ardından yönteminde <xref:System.Data.DataTable.ColumnChanging> olayına <xref:System.Data.DataTable.EndInit%2A> bağlandı.

3. Uygulama gereksinimlerinizi `e.ProposedValue` karşılayacak verileri içerdiğini doğrulamak için kod ekleyin. Önerilen değer kabul edilemezse, sütunu hata içerdiğini belirtecek şekilde ayarlayın.

     Aşağıdaki kod örneği, **Quantity** sütununda 0'dan büyük bir değer olduğunu doğrular. **Quantity değeri** 0'dan küçük veya ona eşitse sütun bir hataya ayarlanır. Quantity `Else` değeri 0'dan **büyükse yan** tümcesi hatayı temizler. Sütun değiştiren olay işleyicisinde yer alan kod aşağıdakine benzer:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Satırların tamamlarında yapılan değişiklikleri doğrulama
Olayı işerek satırların tamamdaki değerleri <xref:System.Data.DataTable.RowChanging> doğrular. Olay, <xref:System.Data.DataTable.RowChanging> tüm sütunlarda değerler işlendikleri zaman ortaya çıkar. Bir sütundaki değer başka <xref:System.Data.DataTable.RowChanging> bir sütundaki değere bağlı olduğunda olayda doğrulanması gerekir. Örneğin, Northwind'de Orders tablosunda OrderDate ve RequiredDate'i göz önünde bulundurabilirsiniz.

Siparişler girilirken doğrulama, OrderDate üzerinde veya öncesinde bir RequiredDate ile sipariş girilemeden emin olur. Bu örnekte hem RequiredDate hem de OrderDate sütunlarının değerleri karşılaştırıldı. Bu nedenle tek bir sütun değişikliğinin doğru olması mantıklı değildir.

tablo başlığı çubuğundaki tablo adına çift tıklayarak olay için bir olay <xref:System.Data.DataTable.RowChanging> işleyicisi **Veri Kümesi Tasarımcısı.**

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Tam satırlarda yapılan değişiklikler sırasında doğrulama eklemek için

1. veri kümesinde *.xsd* dosyasına çift tıklayarak veri **Çözüm Gezgini.** Daha fazla bilgi için [bkz. Adım adım kılavuz:](walkthrough-creating-a-dataset-with-the-dataset-designer.md)veri kümesi oluşturma Veri Kümesi Tasarımcısı.

2. Tasarımcıdaki veri tablosu başlık çubuğuna çift tıklayın.

     Olay işleyicisi ile kısmi `RowChanging` bir sınıf oluşturulur ve Kod Düzenleyicisi'nde açılır.

    > [!NOTE]
    > Bu Veri Kümesi Tasarımcısı, C# projelerinde olay için otomatik <xref:System.Data.DataTable.RowChanging> olarak bir olay işleyicisi oluşturmaz. Olayı işlemek ve kodu çalıştırmak için bir yöntem oluşturmanız ve ardından olayı tablonun başlatma <xref:System.Data.DataTable.RowChanging> yönteminde bağlayabilirsiniz.

3. Kısmi sınıf bildiriminin içine kullanıcı kodu ekleyin.

4. Aşağıdaki kod, olay sırasında doğrulamak için kullanıcı kodunun nereye ekli olduğunu <xref:System.Data.DataTable.RowChanging> gösterir. C# örneği, olay işleyicisi yöntemini olayına bağlayacak kodu da `OrdersRowChanging` içerir.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [N Katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [Adım adım kılavuz: N Katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Veri kümelerini doğrulama](../data-tools/validate-data-in-datasets.md)
