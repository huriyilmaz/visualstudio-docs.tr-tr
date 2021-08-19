---
title: güncelleştirme Excel veya Word projesi .NET Framework 4,5 'e geçirildi
description: belirli özellikleri kullanan bir Excel veya Word projeniz olduğunda, hedef framework .NET Framework 4 ' e veya üzeri olarak değiştirilirse kodunuzu değiştirmelisiniz.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c79d0361d1cfad2615d83bb2a8d66733f0516f3b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046327"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-45"></a>.NET Framework 4,5 'e geçiş yaptığınız Excel ve Word projelerini güncelleştirme
  aşağıdaki özelliklerden herhangi birini kullanan bir Excel veya Word projeniz varsa, hedef framework veya daha yeni olarak değiştirilirse kodunuzu değiştirmeniz gerekir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] :

- [GetVstoObject ve HasVstoObject yöntemleri](#GetVstoObject)

- [Belge düzeyi projelerinde oluşturulan sınıflar](#generatedclasses)

- [Windows Belgelerde form denetimleri](#winforms)

- [Word içerik denetimi olayları](#ccevents)

- [OLEObject ve OLEControl sınıfları](#ole)

- [Controls. Item (nesne) özelliği](#itemproperty)

- [CollectionBase 'den türetilen Koleksiyonlar](#collections)

  ayrıca, `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` veya sonraki bir sürüme yeniden hedeflenmiş Excel projelerindeki sınıfa başvuruları da kaldırmalısınız [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Visual Studio, bu özniteliği veya sınıf başvurusunu sizin için kaldırmaz.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Excel projelerinden ExcelLocale1033 özniteliğini kaldırma
 , `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` veya üstünü hedefleyen çözümler için kullanılan Office çalışma zamanına yönelik Visual Studio 2010 araçlarının bölümünden kaldırılmıştır [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . ve sonrasındaki ortak dil çalışma zamanı (CLR) [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] her zaman Excel nesne modeline 1033 yerel ayar kimliğini geçirir ve bu davranışı devre dışı bırakmak için artık bu özniteliği kullanamazsınız. daha fazla bilgi için bkz. [Excel çözümlerin genelleştirme ve yerelleştirilmesi](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>ExcelLocale1033Attribute 'yi kaldırmak için

1. proje Visual Studio açıkken **Çözüm Gezgini** açın.

2. **özellikler** düğümü (C# için) veya **Project** düğümü altında (Visual Basic için), assemblyınfo kod dosyasına çift tıklayarak kodu düzenleyici 'de açın.

    > [!NOTE]
    > Visual Basic projelerinde, assemblyınfo kod dosyasını görmek için **Çözüm Gezgini** **tüm dosyaları göster** düğmesini tıklamalısınız.

3. Öğesini bulun `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` ve dosyadan kaldırın ya da not edin.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy sınıfına bir başvuruyu kaldırma
 Microsoft Office sistem için Microsoft Visual Studio 2005 araçları kullanılarak oluşturulan projeler, sınıfını kullanarak Excel nesnesini örnekleyebilirsiniz <xref:Microsoft.Office.Interop.Excel.Application> `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` . bu sınıf, veya daha sonra hedeflenen çözümler için kullanılan Office çalışma zamanına yönelik Visual Studio 2010 araçlarının bölümünden kaldırılmıştır [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Bu nedenle, bu sınıfa başvuran kod satırını kaldırmanız veya bir açıklama satırı oluşturmanız gerekir.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy sınıfına başvuruyu kaldırmak için

1. projeyi Visual Studio açın ve **Çözüm Gezgini** açın.

2. **Çözüm Gezgini**' de, *thisaddın. cs* (C# için) veya *thisaddın. vb* (Visual Basic için) kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

3. Kod düzenleyicisinde, `VSTO generated code` bölgesinde aşağıdaki kod satırını kaldırın veya yorum yapın.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="update-code-that-uses-the-getvstoobject-and-hasvstoobject-methods"></a><a name="GetVstoObject"></a> GetVstoObject ve HasVstoObject yöntemlerini kullanan kodu güncelleştirme
 .NET Framework 3,5 ' i hedefleyen projelerde, `GetVstoObject` veya `HasVstoObject` yöntemleri projenizdeki aşağıdaki yerel nesnelerden birinde uzantı yöntemleri olarak kullanılabilir: <xref:Microsoft.Office.Interop.Word.Document> , <xref:Microsoft.Office.Interop.Excel.Workbook> , <xref:Microsoft.Office.Interop.Excel.Worksheet> veya <xref:Microsoft.Office.Interop.Excel.ListObject> . Bu yöntemleri çağırdığınızda bir parametre geçirmeniz gerekmez. aşağıdaki kod örneği, .NET Framework 3,5 ' i hedefleyen bir Word VSTO eklentisi içinde GetVstoObject yönteminin nasıl kullanılacağını gösterir.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya sonraki bir sürümü hedefleyen projelerde, aşağıdaki yöntemlerden biriyle bu yöntemlere erişmek için kodunuzu değiştirmeniz gerekir:

- Bu yöntemlere <xref:Microsoft.Office.Interop.Word.Document> ,, <xref:Microsoft.Office.Interop.Excel.Workbook> <xref:Microsoft.Office.Interop.Excel.Worksheet> veya nesnelerinde uzantı yöntemleri olarak erişmeye devam edebilirsiniz <xref:Microsoft.Office.Interop.Excel.ListObject> . Ancak artık özelliği tarafından döndürülen nesneyi `Globals.Factory` Bu yöntemlere geçirmeniz gerekir.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Alternatif olarak, bu yöntemlere özelliği tarafından döndürülen nesne üzerinde erişebilirsiniz `Globals.Factory` . Bu yöntemlere bu şekilde eriştiğinizde, genişletmek istediğiniz yerel nesneyi yöntemine geçirmeniz gerekir.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  daha fazla bilgi için bkz. [çalışma zamanında VSTO eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="update-code-that-uses-instances-of-the-generated-classes-in-document-level-projects"></a><a name="generatedclasses"></a> Belge düzeyi projelerde oluşturulan sınıfların örneklerini kullanan kodu güncelleştirme
 .NET Framework 3,5 ' i hedefleyen belge düzeyi projelerde, projelerdeki oluşturulan sınıflar içinde aşağıdaki sınıflardan türetilir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] :

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheet>

  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yukarıda listelenen türler sınıflar yerine arayüzlerdir. Veya sonrasını hedefleyen projelerde oluşturulan sınıflar [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , içindeki aşağıdaki yeni sınıflardan türetilir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] :

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Projenizdeki kod, tarafından türetilen temel sınıf olarak oluşturulan sınıflardan birinin bir örneğine başvuruyorsa, kodu değiştirmeniz gerekir.

  örneğin, .NET Framework 3,5 ' i hedefleyen Excel bir çalışma kitabı projesinde, projenizde oluşturulan `Sheet` *n* sınıflarının örnekleri üzerinde bazı çalışmalar gerçekleştiren bir yardımcı yönteminiz olabilir.

```vb
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)
    ' Do something to the worksheet object.
End Sub
```

```csharp
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)
{
    // Do something to the worksheet object.
}
```

 Projeyi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümüne yeniden hedeflemeniz durumunda kodunuzda aşağıdaki değişikliklerden birini yapmalısınız:

- `DoSomethingToSheet` <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> Projenizdeki bir nesnenin özelliğini geçirmek için yöntemini çağıran herhangi bir kodu değiştirin <xref:Microsoft.Office.Tools.Excel.WorksheetBase> . Bu özellik bir <xref:Microsoft.Office.Tools.Excel.Worksheet> nesne döndürür.

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- `DoSomethingToSheet`Yöntem parametresini, bunun yerine bir nesne beklediği şekilde değiştirin <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .

    ```vb
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)
        ' Do something to the worksheet object.
    End Sub
    ```

    ```csharp
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)
    {
        // Do something to the worksheet object.
    }
    ```

## <a name="update-code-that-uses-windows-forms-controls-on-documents"></a><a name="winforms"></a>belgelerde Windows Forms denetimleri kullanan kodu güncelleştirme
 ya da ad alanı için bir **using** (C#) ya da **ımports** (Visual Basic) ifadesini, <xref:Microsoft.Office.Tools.Excel> <xref:Microsoft.Office.Tools.Word> belge veya çalışma sayfasına programlı bir şekilde Windows Forms denetimleri eklemek için denetimler özelliğini kullanan herhangi bir kod dosyasının en üstüne eklemeniz gerekir.

 .NET Framework 3,5 ' i hedefleyen projelerde, Windows Forms denetimleri (yöntemi gibi) ekleyen yöntemler `AddButton` <xref:Microsoft.Office.Tools.Excel.ControlCollection> ve <xref:Microsoft.Office.Tools.Word.ControlCollection> sınıflarında tanımlanmıştır.

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, bu yöntemler denetimler özelliğinde kullanılabilen genişletme yöntemleridir. Bu uzantı yöntemlerini kullanmak için, yöntemlerini kullandığınız kod dosyası  veya  <xref:Microsoft.Office.Tools.Excel> <xref:Microsoft.Office.Tools.Word> ad alanı için bir using veya Imports bildirimine sahip olmalıdır. Bu ifade, veya daha sonra hedeflenen yeni projelerde otomatik olarak oluşturulur [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . ancak, bu ifade .NET Framework 3,5 ' i hedefleyen projelerde otomatik olarak eklenmez, bu nedenle projeyi yeniden hedeflediğinizde eklemeniz gerekir.

 daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-handles-word-content-control-events"></a><a name="ccevents"></a> Word içerik denetimi olaylarını işleyen kodu güncelleştirme
 .NET Framework 3,5 ' i hedefleyen projelerde, Word içerik denetimlerinin olayları genel temsilci tarafından işlenir <xref:System.EventHandler%601> . [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, bu olaylar diğer temsilciler tarafından işlenir.

 Aşağıdaki tabloda, Word içerik denetim olayları ve bunlarla veya daha sonra hedeflenen projelerde ilişkili temsilciler listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

|Olay|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Ve sonraki projelerde kullanılacak temsilci|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="update-code-that-uses-the-oleobject-and-olecontrol-classes"></a><a name="ole"></a> OLEObject ve OLEControl sınıfları kullanan kodu güncelleştirme
 .NET Framework 3,5 ' i hedefleyen projelerde, ve sınıflarını kullanarak bir belgeye veya çalışma sayfasına özel denetimler (örneğin, Windows Forms kullanıcı denetimleri) ekleyebilirsiniz `Microsoft.Office.Tools.Excel.OLEObject` `Microsoft.Office.Tools.Word.OLEControl` .

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, bu sınıflar <xref:Microsoft.Office.Tools.Excel.ControlSite> ve arabirimleri ile değiştirilmiştir <xref:Microsoft.Office.Tools.Word.ControlSite> . Bunun yerine öğesine ve öğesine başvuran kodu değiştirmeniz gerekir `Microsoft.Office.Tools.Excel.OLEObject` `Microsoft.Office.Tools.Word.OLEControl` <xref:Microsoft.Office.Tools.Excel.ControlSite> <xref:Microsoft.Office.Tools.Word.ControlSite> . yeni adlar dışında, bu denetimler .NET Framework 3,5 ' i hedefleyen projelerde yaptıkları gibi davranır.

 daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-the-controlsitemobject-property"></a><a name="itemproperty"></a> Controls. Item (Object) özelliğini kullanan kodu güncelleştirme
 .NET Framework 3,5 ' i hedefleyen projelerde, Microsoft.Office.Tools.Word.Document öğesinin ıtem (Object) özelliğini kullanabilirsiniz. `Microsoft.Office.Tools.Excel.Worksheet.Controls`Bir belge veya çalışma sayfasının belirtilen denetime sahip olup olmadığını belirleme denetimleri veya koleksiyonu.

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, öğe (nesne) özelliği bu koleksiyonlardan kaldırılmıştır. Bir belge veya çalışma sayfasının belirtilen denetimi içerip içermediğini anlamak için, veya koleksiyonunun Contains (System. Object) yöntemini kullanın <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> .

 belge ve çalışma sayfalarının denetimler koleksiyonu hakkında daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-collections-that-derive-from-collectionbase"></a><a name="collections"></a> CollectionBase 'den türetilen koleksiyonları kullanan kodu güncelleştirme
 .NET Framework 3,5 ' i hedefleyen projelerde,, ve gibi sınıfından türetilmiş çeşitli koleksiyon türleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:System.Collections.CollectionBase> `Microsoft.Office.Tools.SmartTagCollection` `Microsoft.Office.Tools.Excel.ControlCollection` `Microsoft.Office.Tools.Word.ControlCollection` .

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, bu koleksiyon türleri artık öğesinden türetilmeyen arabirimlerdir <xref:System.Collections.CollectionBase> . Bazı üyeler,, ve gibi bu koleksiyon türlerinde artık kullanılamaz <xref:System.Collections.CollectionBase.Capacity%2A> <xref:System.Collections.CollectionBase.List%2A> <xref:System.Collections.CollectionBase.InnerList%2A> .

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [İçerik denetimleri](../vsto/content-controls.md)
- [Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
