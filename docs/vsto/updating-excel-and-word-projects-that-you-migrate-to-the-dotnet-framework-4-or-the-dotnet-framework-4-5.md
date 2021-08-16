---
title: .NET Framework 4.5'e geçirilen Excel veya Word projesini güncelleştirme
description: Belirli özellikleri kullanan bir Excel veya Word projeniz olduğunda, hedef çerçeve .NET Framework 4 veya sonraki bir Excel olarak değiştirilirse kodunuzu değiştirmeniz gerekir.
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
ms.openlocfilehash: df1295eb07a086504129d281c0c050679bf9b856a392cb03dabbf638d8c6a38d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121285029"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-45"></a>Excel 4.5'e geçirilen .NET Framework Word projelerini güncelleştirme
  Aşağıdaki özelliklerden herhangi birini Excel word veya Word projeniz varsa, hedef çerçeve veya sonraki bir ile değiştirilirse kodunuzu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] değiştirmeniz gerekir:

- [GetVstoObject ve HasVstoObject yöntemleri](#GetVstoObject)

- [Belge düzeyi projelerinde oluşturulan sınıflar](#generatedclasses)

- [Windows Belgeler üzerinde form denetimleri](#winforms)

- [Word içerik denetimi olayları](#ccevents)

- [OLEObject ve OLEControl sınıfları](#ole)

- [Controls.Item(Object) özelliği](#itemproperty)

- [CollectionBase'den türeyen koleksiyonlar](#collections)

  Ayrıca veya sonraki bir ya da sonraki bir ya da sonraki bir Excel için yeniden hedefli projelerden sınıfına ve `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` başvurularını [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] kaldırmanız gerekir. Visual Studio, bu özniteliği veya sınıf başvurularını sizin için kaldırmaz.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>ExcelLocale1033 özniteliğini projelerden Excel kaldırma
 , veya sonraki bir sürümü hedef alan çözümler için kullanılan Visual Studio 2010 Office çalışma zamanı için bölümünün `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] kısmından kaldırılmıştır. ve sonraki işletim gruplarında ortak dil çalışma zamanı (CLR) her zaman yerel kimlik 1033'ü Excel nesne modeline iletir ve bu davranışı devre dışı bırakmak için artık bu özniteliği [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] kullanamazsiniz. Daha fazla bilgi için [bkz. Genelleştirme ve yerelleştirme Excel.](../vsto/globalization-and-localization-of-excel-solutions.md)

### <a name="to-remove-the-excellocale1033attribute"></a>ExcelLocale1033Attribute'unu kaldırmak için

1. Proje Visual Studio açıkken **Çözüm Gezgini.**

2. Özellikler **düğümü** (C# için) veya **My Project** düğümünün (Visual Basic için) altında AssemblyInfo kod dosyasına çift tıklar ve kod düzenleyicisinde açın.

    > [!NOTE]
    > Bu Visual Basic, AssemblyInfo kod dosyasını **görmek** için Çözüm Gezgini Dosyaları **Göster** düğmesine tıklamanız gerekir.

3. dosyasını `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` bulun ve dosyadan kaldırın veya açıklamaya çıkarın.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy sınıfına başvuru kaldırma
 Microsoft Office System için Microsoft Visual Studio 2005 Araçları kullanılarak oluşturulan projeler sınıfını kullanarak Excel <xref:Microsoft.Office.Interop.Excel.Application> nesnesinin örneğini `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` oluşturur. Bu sınıf, veya sonrakini hedef alan çözümler için kullanılan Office için Visual Studio 2010 Araçları'nın [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] kısmından kaldırılmıştır. Bu nedenle, bu sınıfa başvurulan kod satırlarını kaldırmanız veya açıklama satırınız gerekir.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy sınıfı başvurularını kaldırmak için

1. Projeyi Visual Studio açın ve sonra da **Çözüm Gezgini.**

2. Bu **Çözüm Gezgini** *ThisAddin.cs* (C#için) veya *ThisAddin.vb* (Visual Basic için) kısayol menüsünü açın ve ardından Kodu **Görüntüle'yi seçin.**

3. Kod Düzenleyicisi'nde, `VSTO generated code` bölgede aşağıdaki kod satırı kaldırın veya açıklama satırı yapın.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="update-code-that-uses-the-getvstoobject-and-hasvstoobject-methods"></a><a name="GetVstoObject"></a> GetVstoObject ve HasVstoObject yöntemlerini kullanan kodu güncelleştirme
 .NET Framework 3.5'i hedef alan projelerde veya yöntemleri, projenizin şu yerel nesnelerinden biri üzerinde uzantı yöntemleri olarak `GetVstoObject` `HasVstoObject` kullanılabilir: <xref:Microsoft.Office.Interop.Word.Document> , , <xref:Microsoft.Office.Interop.Excel.Workbook> veya <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.ListObject> . Bu yöntemleri çağırarak parametre geçmeniz gerekli değildir. Aşağıdaki kod örneği, 3.5'i hedefleyen bir Word VSTO Eklentisinde GetVstoObject yönteminin nasıl .NET Framework göstermektedir.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonrakini hedef alan projelerde, aşağıdaki yöntemlerden birini kullanarak bu yöntemlere erişmek için kodunuzu değiştirmeniz gerekir:

- Bu yöntemlere yine de , , veya nesnelerini genişletme <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Workbook> yöntemleri olarak <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.ListObject> erişebilirsiniz. Ancak şimdi özelliği tarafından döndürülen nesneyi bu `Globals.Factory` yöntemlere iletirsiniz.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Alternatif olarak, özelliği tarafından döndürülen nesnede bu yöntemlere `Globals.Factory` erişebilirsiniz. Bu yöntemlere bu şekilde erişin, yöntemine genişletmek istediğiniz yerel nesneyi geçmeniz gerekir.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="update-code-that-uses-instances-of-the-generated-classes-in-document-level-projects"></a><a name="generatedclasses"></a> Belge düzeyi projelerinde oluşturulan sınıfların örneklerini kullanan kodu güncelleştirme
 .NET Framework 3.5'i hedef alan belge düzeyi projelerde, projelerde oluşturulan sınıflar içinde aşağıdaki sınıflardan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] türetmektedir:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheet>

  veya üzerini [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] hedef alan projelerde, yukarıda listelenen [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] türler sınıflar yerine arabirimleridir. veya sonraki bir sonrakini hedef alan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] projelerde oluşturulan sınıflar içinde aşağıdaki yeni sınıflardan türetir: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Projenizin kodu, oluşturulan sınıflardan birinin örneğine türetilen temel sınıf olarak başvurursa, kodu değiştirmeniz gerekir.

  Örneğin, .NET Framework 3.5'i hedef alan bir Excel Çalışma Kitabı projesinde, projenizin oluşturulan n sınıfı örnekleri üzerinde bazı işler gerçekleştiren bir yardımcı `Sheet` *yönteminiz* olabilir.

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

 Projeyi veya sonraki bir tarihine yeniden [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] hedefleyebilirsiniz, kodunda aşağıdaki değişikliklerden birini gerçekleştirin:

- Projenize bir nesnenin `DoSomethingToSheet` özelliğini geçmek için yöntemini <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> çağıran herhangi bir kodu <xref:Microsoft.Office.Tools.Excel.WorksheetBase> değiştirme. Bu özellik bir nesnesi <xref:Microsoft.Office.Tools.Excel.Worksheet> döndürür.

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- Bunun yerine `DoSomethingToSheet` yöntem parametresini bir nesnesi beklemek <xref:Microsoft.Office.Tools.Excel.WorksheetBase> için değiştirme.

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

## <a name="update-code-that-uses-windows-forms-controls-on-documents"></a><a name="winforms"></a>Belgelerde Formlar Windows kullanan kodu güncelleştirme
 Belgeye **veya** çalışma sayfasına program aracılığıyla Windows Forms denetimleri eklemek için Controls özelliğini kullanan herhangi bir kod dosyasının en üstüne veya ad alanı için using (C#) veya **Imports** <xref:Microsoft.Office.Tools.Excel> (Visual Basic) deyimi eklemeniz <xref:Microsoft.Office.Tools.Word> gerekir.

 .NET Framework 3.5'i hedef alan projelerde, Windows Forms denetimleri (yöntemi gibi) ek olarak ve `AddButton` <xref:Microsoft.Office.Tools.Excel.ControlCollection> sınıflarında <xref:Microsoft.Office.Tools.Word.ControlCollection> tanımlanır.

 veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonrakini hedef alan projelerde bu yöntemler, Denetimler özelliğinde kullanılabilen uzantı yöntemleridir. Bu uzantı yöntemlerini kullanmak için, yöntemleri kullanmakta olan kod dosyasında veya ad alanı için **bir using** veya **Imports** deyimi <xref:Microsoft.Office.Tools.Excel> <xref:Microsoft.Office.Tools.Word> bulunacaktır. Bu deyim, veya sonrakini hedef alan yeni projelerde otomatik [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] olarak oluşturulur. Ancak, bu deyim 3.5'i .NET Framework projelere otomatik olarak eklenmez, bu nedenle projeyi yeniden hedefleyene kadar bunu eklemeniz gerekir.

 Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="update-code-that-handles-word-content-control-events"></a><a name="ccevents"></a> Word içerik denetimi olaylarını işen kodu güncelleştirme
 .NET Framework 3.5'i hedef alan projelerde, Word içerik denetimlerinin olayları genel temsilci tarafından <xref:System.EventHandler%601> dolar. veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonrakini hedef alan projelerde bu olaylar diğer temsilciler tarafından ele alınan olaylardır.

 Aşağıdaki tabloda, Word içerik denetimi olayları ve veya sonrakini hedef alan projelerde onlarla ilişkili [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] temsilciler liste almaktadır.

|Olay|Ve sonraki projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] kullanmak üzere temsilci seç|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="update-code-that-uses-the-oleobject-and-olecontrol-classes"></a><a name="ole"></a> OLEObject ve OLEControl sınıflarını kullanan kodu güncelleştirme
 .NET Framework 3.5'i hedef alan projelerde, ve sınıflarını kullanarak bir belgeye veya çalışma sayfasına özel denetimler (Windows Forms kullanıcı denetimleri gibi) `Microsoft.Office.Tools.Excel.OLEObject` `Microsoft.Office.Tools.Word.OLEControl` ekleyebilirsiniz.

 veya sonrakini [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] hedef alan projelerde, bu sınıflar ve <xref:Microsoft.Office.Tools.Excel.ControlSite> arabirimleri <xref:Microsoft.Office.Tools.Word.ControlSite> ile değiştirilmiştir. ve yerine ve ifadelerini ifade etmek `Microsoft.Office.Tools.Excel.OLEObject` `Microsoft.Office.Tools.Word.OLEControl` için kodu değiştirmeniz <xref:Microsoft.Office.Tools.Excel.ControlSite> <xref:Microsoft.Office.Tools.Word.ControlSite> gerekir. Yeni adlar dışında, bu denetimler 3.5'i hedef alan projelerde .NET Framework davranır.

 Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="update-code-that-uses-the-controlsitemobject-property"></a><a name="itemproperty"></a> Controls.Item(Object) özelliğini kullanan kodu güncelleştirme
 .NET Framework 3.5'i hedef alan projelerde, Microsoft.Office.Tools.Word.Document öğesinin Item(Object) özelliğini kullanabilirsiniz. Bir belgenin `Microsoft.Office.Tools.Excel.Worksheet.Controls` veya çalışma sayfasının belirli bir denetime sahip olup olmadığını belirlemek için denetimler veya koleksiyon.

 veya sonrakini [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] hedef alan projelerde Item(Object) özelliği bu koleksiyonlardan kaldırılmıştır. Bir belgenin veya çalışma sayfasının belirtilen bir denetimi içerdiğini belirlemek için veya koleksiyonunun Contains(System.Object) <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> yöntemini kullanın.

 Belgelerin ve çalışma sayfalarının Denetimler koleksiyonu hakkında daha fazla bilgi için bkz. Çalışma zamanında [Office belgelere denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="update-code-that-uses-collections-that-derive-from-collectionbase"></a><a name="collections"></a> CollectionBase'den türeten koleksiyonları kullanan kodu güncelleştirme
 .NET Framework 3.5'i hedef alan projelerde, içinde çeşitli koleksiyon türleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:System.Collections.CollectionBase> `Microsoft.Office.Tools.SmartTagCollection` sınıfından türetildi, örneğin `Microsoft.Office.Tools.Excel.ControlCollection` , ve `Microsoft.Office.Tools.Word.ControlCollection` .

 veya sonraki bir sonrakini hedef alan projelerde, bu koleksiyon türleri artık [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 'den türet yapmayan arabirimlerdir. <xref:System.Collections.CollectionBase> Bazı üyeler artık , ve gibi bu koleksiyon türlerinde <xref:System.Collections.CollectionBase.Capacity%2A> <xref:System.Collections.CollectionBase.List%2A> <xref:System.Collections.CollectionBase.InnerList%2A> kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini 4 veya .NET Framework'a geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [İçerik denetimleri](../vsto/content-controls.md)
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
