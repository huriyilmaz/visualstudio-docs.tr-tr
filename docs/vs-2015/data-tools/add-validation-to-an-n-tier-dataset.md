---
title: N katmanlı veri kümesine doğrulama ekleme | Microsoft Docs
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
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b03f1e85140d62d84ae7c706a9bfee6a7c515abb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673048"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>N Katmanlı bir veri kümesine doğrulama ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N katmanlı bir çözüme ayrılmış bir veri kümesine doğrulama eklemek, temelde tek bir dosya veri kümesine (tek bir projede bir veri kümesi) doğrulama ekleme ile aynıdır. Veriler üzerinde doğrulama gerçekleştirmek için önerilen konum, <xref:System.Data.DataTable.ColumnChanging> bir veri tablosunun ve/veya <xref:System.Data.DataTable.RowChanging> olaylarının sayısıdır.

Veri kümesi Tasarımcısı, veri kümesindeki veri tablolarının sütun ve satır değiştirme olaylarına Kullanıcı kodu ekleyebileceğiniz kısmi sınıflar oluşturma işlevlerini sağlar. N katmanlı bir çözümde bir veri kümesine kod ekleme hakkında daha fazla bilgi için, bkz. [n katmanlı uygulamalardaki veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md)ve [n katmanlı uygulamalarda TableAdapters 'e kod](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)ekleme. Kısmi sınıflar hakkında daha fazla bilgi için bkz. [nasıl yapılır: sınıfı kısmi sınıflara bölme (sınıf Tasarımcısı)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) veya [kısmi sınıflar ve Yöntemler](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

> [!NOTE]
> Veri kümelerini TableAdapters 'dan ayırdığınızda ( **DataSet projesi** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

> [!NOTE]
> Veri Kümesi Tasarımcısı, ve olayları Için C# ' de otomatik olarak olay işleyicileri <xref:System.Data.DataTable.ColumnChanging> oluşturmaz <xref:System.Data.DataTable.RowChanging> . El ile bir olay işleyicisi oluşturmanız ve olay işleyicisini temeldeki olaya yedeklemeniz gerekir. Aşağıdaki yordamlar, hem Visual Basic hem de C# ' de gerekli olay işleyicilerinin nasıl oluşturulacağını açıklamaktadır.

## <a name="validatechanges-to-individual-columns"></a>Her sütuna yönelik ValidateChanges
 Olayı işleyerek sütunları ayrı sütunlarda doğrulayın <xref:System.Data.DataTable.ColumnChanging> . <xref:System.Data.DataTable.ColumnChanging>Olay, sütundaki bir değer değiştirildiğinde tetiklenir. <xref:System.Data.DataTable.ColumnChanging>Veri kümesinde istenen sütuna çift tıklayarak olay için bir olay işleyicisi oluşturun.

 Bir sütuna ilk kez çift tıkladığınızda, tasarımcı olay için bir olay işleyicisi oluşturur <xref:System.Data.DataTable.ColumnChanging> . `If…Then`Belirli bir sütun için testler de oluşturulur. Örneğin, Northwind Orders tablosundaki RequiredDate sütununu çift tıklattığınızda aşağıdaki kod oluşturulur:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> C# projelerinde Veri Kümesi Tasarımcısı, veri kümesindeki yalnızca veri kümesi ve tek tablolar için kısmi sınıflar oluşturur. Veri Kümesi Tasarımcısı, <xref:System.Data.DataTable.ColumnChanging> C# ' deki ve olayları için Visual Basic gibi olay işleyicilerini otomatik olarak oluşturmaz <xref:System.Data.DataTable.RowChanging> . C# projelerinde, olayı işlemek için el ile bir yöntem oluşturmanız ve yöntemi temel alınan olaya yedeklemeniz gerekir. Aşağıdaki yordam, hem Visual Basic hem de C# içinde gerekli olay işleyicilerini oluşturma adımlarını sağlar.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Tek tek sütun değerlerine değişiklikler sırasında doğrulama eklemek için

1. **Çözüm Gezgini**içindeki **. xsd** dosyasını çift tıklayarak tasarımcıda veri kümesini açın. Daha fazla bilgi için bkz. [nasıl yapılır: veri kümesi Tasarımcısı veri kümesini açma](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Doğrulamak istediğiniz sütuna çift tıklayın. Bu eylem <xref:System.Data.DataTable.ColumnChanging> olay işleyicisini oluşturur.

    > [!NOTE]
    > Veri Kümesi Tasarımcısı, C# olayı için otomatik olarak bir olay işleyici oluşturmaz. C# ' de olayı işlemek için gerekli olan kod bir sonraki bölüme dahildir. `SampleColumnChangingEvent` oluşturulur ve sonra <xref:System.Data.DataTable.ColumnChanging> yöntemdeki olaya bağlanır <xref:System.Data.DataTable.EndInit%2A> .

3. `e.ProposedValue`Uygulamanızın gereksinimlerini karşılayan veriler içerdiğini doğrulamak için kod ekleyin. Önerilen değer kabul edilemez ise, sütunu bir hata içerdiğini belirtecek şekilde ayarlayın.

     Aşağıdaki kod örneği, **Quantity** sütununun 0 ' dan fazla içerdiğini doğrular. **Quantity** 0 ' dan küçük veya eşitse, sütun bir hata olarak ayarlanır. `Else` **Quantity** 0 ' dan fazla ise yan tümce hatayı temizler. Sütun değiştirme olay işleyicisindeki kodun aşağıdakine benzer olması gerekir:

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
    // C#
    // Add this code to the DataTable
    // partial class.

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

## <a name="validatechanges-to-whole-rows"></a>Tüm satırlarda ValidateChanges
 Olayı işleyerek tüm satırlardaki değerleri doğrulayın <xref:System.Data.DataTable.RowChanging> . <xref:System.Data.DataTable.RowChanging>Olay, tüm sütunlardaki değerler işlendiği zaman tetiklenir. <xref:System.Data.DataTable.RowChanging>Bir sütundaki değer başka bir sütundaki değere dayanıyorsa olayda doğrulanması gerekir. Örneğin, Northwind 'deki Orders tablosunda OrderDate ve RequiredDate ' i göz önünde bulundurun.

 Siparişler girildiğinde, doğrulama işlemi OrderDate tarihinde veya bu tarihten önce olan bir RequiredDate ile bir siparişin girilmediğinden emin olur. Bu örnekte, hem RequiredDate hem de OrderDate sütunlarının değerlerinin karşılaştırılması gerekir, bu nedenle tek bir sütun değişikliğinin doğrulanması anlamlı değildir.

 <xref:System.Data.DataTable.RowChanging>Tablonun başlık çubuğundaki tablo adına çift tıklayarak olay için bir olay işleyicisi oluşturun.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Tüm satırlarda değişiklikler sırasında doğrulama eklemek için

1. **Çözüm Gezgini**içindeki **. xsd** dosyasını çift tıklayarak tasarımcıda veri kümesini açın. Daha fazla bilgi için bkz. [nasıl yapılır: veri kümesi Tasarımcısı veri kümesini açma](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Tasarımcıda veri tablosunun başlık çubuğuna çift tıklayın.

     Kısmi bir sınıf, `RowChanging` olay işleyicisiyle oluşturulur ve kod düzenleyicisinde açılır.

    > [!NOTE]
    > Veri Kümesi Tasarımcısı, C# projelerindeki olay için otomatik olarak bir olay işleyici oluşturmaz <xref:System.Data.DataTable.RowChanging> . Olayı işlemek için bir yöntem oluşturmanız <xref:System.Data.DataTable.RowChanging> ve olayı tablonun başlatma yönteminde bağlamak için kodu çalıştırmanız gerekir.

3. Kısmi sınıf bildiriminin içine Kullanıcı kodu ekleyin.

4. Aşağıdaki kod, Visual Basic olay sırasında doğrulanacak kullanıcı kodunun nereye ekleneceğini gösterir <xref:System.Data.DataTable.RowChanging> :

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

5. Aşağıdaki kod, `RowChanging` olay işleyicisinin nasıl oluşturulacağını ve C# için olay sırasında doğrulanacak kullanıcı kodunun nereye ekleneceğini göstermektedir <xref:System.Data.DataTable.RowChanging> :

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

## <a name="see-also"></a>Ayrıca Bkz.
 [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md) [Izlenecek yol: n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md)
