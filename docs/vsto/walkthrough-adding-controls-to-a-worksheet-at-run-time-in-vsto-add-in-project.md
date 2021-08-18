---
title: VSTO eklenti projesindeki çalışma sayfasına denetimler ekleme
description: Kullanıcıların çalışma sayfasına bir düğme, NamedRange ve ListObject eklemesini sağlamak için şeridi nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d8706772526682c8856cedf5881ee0cd3f75dc76
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032153"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>izlenecek yol: VSTO eklentisi projesinde çalışma zamanında çalışma sayfasına denetimler ekleme
  bir Excel VSTO eklentisi kullanarak herhangi bir açık çalışma sayfasına denetim ekleyebilirsiniz. Bu izlenecek yol, kullanıcıların <xref:Microsoft.Office.Tools.Excel.Controls.Button> çalışma sayfasına bir, a ve bir eklemek Için şerit 'in nasıl kullanılacağını gösterir <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> . bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

 **Uygulama hedefi:** bu konudaki bilgiler, Excel için VSTO eklenti projelerine yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma sayfasına denetim eklemek için bir kullanıcı arabirimi (UI) sağlama.

- Çalışma sayfasına denetimler ekleme.

- Çalışma sayfasından denetimler kaldırılıyor.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>yeni bir Excel VSTO eklenti projesi oluşturma
 bir Excel VSTO eklenti projesi oluşturarak başlayın.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>yeni bir Excel VSTO eklenti projesi oluşturmak için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **exceldynamiccontrols** adlı bir Excel VSTO eklenti projesi oluşturun. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** derlemesine bir başvuru ekleyin. bu izlenecek yolda daha sonra çalışma sayfasına bir Windows Forms denetimi eklemek için bu başvuru gerekir.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Çalışma sayfasına denetim eklemek için bir kullanıcı arabirimi sağlama
 Excel şeridine özel bir sekme ekleyin. Kullanıcılar, çalışma sayfasına denetim eklemek için sekmedeki onay kutularını seçebilir.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Çalışma sayfasına denetim eklemek için bir kullanıcı arabirimi sağlamak için

1. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin ve ardından **Ekle**' ye tıklayın.

     Şerit tasarımcısında **Ribbon1. cs** veya **Ribbon1. vb** adlı bir dosya açılır ve varsayılan bir sekme ve grup görüntüler.

3. **araç kutusunun** **Office şerit denetimleri** sekmesinden **group1** üzerine bir CheckBox denetimi sürükleyin.

4. Seçmek için **CheckBox1** öğesine tıklayın.

5. **Özellikler** penceresinde, aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Düğme**|
    |**Etiketle**|**Düğme**|

6. **Group1** öğesine ikinci bir onay kutusu ekleyin ve ardından aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**NamedRange**|
    |**Etiketle**|**NamedRange**|

7. **Group1** öğesine üçüncü onay kutusu ekleyin ve ardından aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Veriyi**|
    |**Etiketle**|**Veriyi**|

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Yönetilen denetimler yalnızca kapsayıcı olarak davranan ana bilgisayar öğelerine eklenebilir. VSTO eklenti projeleri herhangi bir açık çalışma kitabıyla birlikte çalıştığından, VSTO eklenti çalışma sayfasını bir konak öğesine dönüştürür veya denetimi eklemeden önce var olan bir konak öğesini alır. <xref:Microsoft.Office.Tools.Excel.Worksheet>Açık çalışma sayfasına dayalı bir konak öğesi oluşturmak için her denetimin Click olay işleyicisine kod ekleyin. Sonra, <xref:Microsoft.Office.Tools.Excel.Controls.Button> <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasındaki geçerli seçime bir, a ve a ekleyin.

### <a name="to-add-controls-to-a-worksheet"></a>Çalışma sayfasına denetim eklemek için

1. Şerit Tasarımcısı ' nda, **düğmesine** çift tıklayın.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> **Düğme** onay kutusunun olay işleyicisi kod düzenleyicisinde açılır.

2. `Button_Click`Olay işleyicisini aşağıdaki kodla değiştirin.

     Bu kod, `GetVstoObject` çalışma kitabındaki ilk çalışma sayfasını temsil eden bir konak öğesini almak için yöntemini kullanır ve ardından <xref:Microsoft.Office.Tools.Excel.Controls.Button> Şu anda seçili olan hücreye bir denetim ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet2":::

3. **Çözüm Gezgini** içinde *Ribbon1. cs* veya *Ribbon1. vb* öğesini seçin.

4. **Görünüm** menüsünde **Tasarımcı**' ya tıklayın.

5. Şerit tasarımcısında, **NamedRange**' e çift tıklayın.

6. `NamedRange_Click`Olay işleyicisini aşağıdaki kodla değiştirin.

     Bu kod, `GetVstoObject` çalışma kitabındaki ilk çalışma sayfasını temsil eden bir konak öğesini almak için yöntemini kullanır ve ardından <xref:Microsoft.Office.Tools.Excel.NamedRange> Şu anda seçili olan hücre veya hücreler için bir denetim tanımlar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet3":::

7. Şerit tasarımcısında **ListObject**' e çift tıklayın.

8. `ListObject_Click`Olay işleyicisini aşağıdaki kodla değiştirin.

     Bu kod, `GetVstoObject` çalışma kitabındaki ilk çalışma sayfasını temsil eden bir konak öğesini almak için yöntemini kullanır ve ardından <xref:Microsoft.Office.Tools.Excel.ListObject> Şu anda seçili olan hücre veya hücreler için bir tanımlar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet4":::

9. Aşağıdaki deyimlerini Şerit kod dosyasının en üstüne ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet1":::

## <a name="remove-controls-from-the-worksheet"></a>Çalışma sayfasından denetimleri kaldırma
 Çalışma sayfası kaydedilip kapatıldığında denetimler kalıcı olmaz. çalışma sayfası kaydedilmeden önce oluşturulan tüm Windows Forms denetimlerini program aracılığıyla kaldırmalı veya çalışma kitabı yeniden açıldığında yalnızca denetimin bir anahattı görünür. <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>oluşturulan konak öğesinin denetimler koleksiyonundan Windows Forms denetimlerini kaldıran olaya kod ekleyin. daha fazla bilgi için bkz. [Office belgelerinde dinamik denetimleri kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

### <a name="to-remove-controls-from-the-worksheet"></a>Çalışma sayfasından denetimleri kaldırmak için

1. **Çözüm Gezgini**, *ThisAddIn. cs* veya *ThisAddIn. vb* öğesini seçin.

2. **Görünüm** menüsünde **kod**' a tıklayın.

3. Sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Bu kod çalışma kitabındaki ilk çalışma sayfasını alır ve sonra `HasVstoObject` çalışma sayfasında oluşturulmuş bir çalışma sayfası nesnesi olup olmadığını denetlemek için yöntemini kullanır. Oluşturulan çalışma sayfası nesnesinin denetimleri varsa, kod bu çalışma sayfası nesnesini alır ve denetim koleksiyonu aracılığıyla dolaşır, denetimleri kaldırır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet6":::

4. C# ' de, olay için bir olay işleyicisi oluşturmanız gerekir <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> . Bu kodu `ThisAddIn_Startup` yöntemine yerleştirebilirsiniz. olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md). `ThisAddIn_Startup` yöntemini aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet5":::

## <a name="test-the-solution"></a>Çözümü test etme
 Şeritteki özel bir sekmeden seçerek çalışma sayfasına denetimler ekleyin. Çalışma sayfasını kaydettiğinizde, bu denetimler kaldırılır.

### <a name="to-test-the-solution"></a>Çözümü test etmek için.

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Sheet1 ' deki herhangi bir hücreyi seçin.

3. **Eklentiler** sekmesine tıklayın.

4. **Grup1** grubunda **düğme**' ye tıklayın.

     Seçili hücrede bir düğme görünür.

5. Sayfa1 'de farklı bir hücre seçin.

6. **Grup1** grubunda, **NamedRange**' e tıklayın.

     Adlandırılmış bir Aralık seçili hücre için tanımlandı.

7. Sayfa1 'de bir hücre serisi seçin.

8. **Grup1** grubunda **ListObject**' e tıklayın.

     Seçili hücreler için bir liste nesnesi eklenir.

9. Çalışma sayfasını kaydedin.

     Sayfa1'e eklenen denetimler artık görünmez.

## <a name="next-steps"></a>Sonraki adımlar
 Eklenti projelerinde denetimler hakkında daha Excel VSTO bu konudan öğrenebilirsiniz:

- Denetimleri bir çalışma sayfasına kaydetme hakkında bilgi edinmek için Excel VSTO örnek ve izlenecek yollar sayfasındaki Office Ek [Dinamik Denetimler Örneği'ne bakın.](../vsto/office-development-samples-and-walkthroughs.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Excel çözümleri](../vsto/excel-solutions.md)
- [Windows belgelere genel bakış Office form denetimleri](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [ListObject denetimi](../vsto/listobject-control.md)
