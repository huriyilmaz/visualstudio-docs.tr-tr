---
title: Çalışma zamanında VSTO eklenti projesindeki çalışma sayfasına denetimler ekleme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5bf2610ca1f3f3767082bf50953f821d37d1af2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253904"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>İzlenecek yol: çalışma zamanında VSTO eklenti projesindeki çalışma sayfasına denetimler ekleme
  Excel VSTO eklentisini kullanarak, herhangi bir açık çalışma sayfasına denetim ekleyebilirsiniz. Bu izlenecek yol, kullanıcıların <xref:Microsoft.Office.Tools.Excel.Controls.Button> çalışma sayfasına bir, a ve bir eklemek Için şerit 'in nasıl kullanılacağını gösterir <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> . Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

 **Uygulama hedefi:** Bu konudaki bilgiler Excel için VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma sayfasına denetim eklemek için bir kullanıcı arabirimi (UI) sağlama.

- Çalışma sayfasına denetimler ekleme.

- Çalışma sayfasından denetimler kaldırılıyor.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>Yeni bir Excel VSTO eklentisi projesi oluşturma
 Bir Excel VSTO eklentisi projesi oluşturarak başlayın.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Yeni bir Excel VSTO eklentisi projesi oluşturmak için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **Exceldynamiccontrols**ADLı bir Excel VSTO eklenti projesi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** derlemesine bir başvuru ekleyin. Bu izlenecek yolda daha sonra çalışma sayfasına bir Windows Forms denetimi eklemek için bu başvuru gerekir.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Çalışma sayfasına denetim eklemek için bir kullanıcı arabirimi sağlama
 Excel şeridine özel bir sekme ekleyin. Kullanıcılar, çalışma sayfasına denetim eklemek için sekmedeki onay kutularını seçebilir.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Çalışma sayfasına denetim eklemek için bir kullanıcı arabirimi sağlamak için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin ve ardından **Ekle**' ye tıklayın.

     Şerit tasarımcısında **Ribbon1.cs** veya **Ribbon1. vb** adlı bir dosya açılır ve varsayılan bir sekme ve grup görüntüler.

3. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden **Group1**üzerine bir CheckBox denetimi sürükleyin.

4. Seçmek için **CheckBox1** öğesine tıklayın.

5. **Özellikler** penceresinde, aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Düğme**|
    |**Etiketle**|**Düğme**|

6. **Group1**öğesine ikinci bir onay kutusu ekleyin ve ardından aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**NamedRange**|
    |**Etiketle**|**NamedRange**|

7. **Group1**öğesine üçüncü onay kutusu ekleyin ve ardından aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Veriyi**|
    |**Etiketle**|**Veriyi**|

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Yönetilen denetimler yalnızca kapsayıcı olarak davranan ana bilgisayar öğelerine eklenebilir. VSTO eklentisi projeleri herhangi bir açık çalışma kitabıyla çalıştığı için, VSTO eklentisi çalışma sayfasını bir konak öğesine dönüştürür veya denetimi eklemeden önce var olan bir konak öğesini alır. <xref:Microsoft.Office.Tools.Excel.Worksheet>Açık çalışma sayfasına dayalı bir konak öğesi oluşturmak için her denetimin Click olay işleyicisine kod ekleyin. Sonra, <xref:Microsoft.Office.Tools.Excel.Controls.Button> <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasındaki geçerli seçime bir, a ve a ekleyin.

### <a name="to-add-controls-to-a-worksheet"></a>Çalışma sayfasına denetim eklemek için

1. Şerit Tasarımcısı ' nda, **düğmesine**çift tıklayın.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> **Düğme** onay kutusunun olay işleyicisi kod düzenleyicisinde açılır.

2. `Button_Click`Olay işleyicisini aşağıdaki kodla değiştirin.

     Bu kod, `GetVstoObject` çalışma kitabındaki ilk çalışma sayfasını temsil eden bir konak öğesini almak için yöntemini kullanır ve ardından <xref:Microsoft.Office.Tools.Excel.Controls.Button> Şu anda seçili olan hücreye bir denetim ekler.

     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]

3. **Çözüm Gezgini**' de *Ribbon1.cs* veya *Ribbon1. vb*' yi seçin.

4. **Görünüm** menüsünde **Tasarımcı**' ya tıklayın.

5. Şerit tasarımcısında, **NamedRange**' e çift tıklayın.

6. `NamedRange_Click`Olay işleyicisini aşağıdaki kodla değiştirin.

     Bu kod, `GetVstoObject` çalışma kitabındaki ilk çalışma sayfasını temsil eden bir konak öğesini almak için yöntemini kullanır ve ardından <xref:Microsoft.Office.Tools.Excel.NamedRange> Şu anda seçili olan hücre veya hücreler için bir denetim tanımlar.

     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]

7. Şerit tasarımcısında **ListObject**' e çift tıklayın.

8. `ListObject_Click`Olay işleyicisini aşağıdaki kodla değiştirin.

     Bu kod, `GetVstoObject` çalışma kitabındaki ilk çalışma sayfasını temsil eden bir konak öğesini almak için yöntemini kullanır ve ardından <xref:Microsoft.Office.Tools.Excel.ListObject> Şu anda seçili olan hücre veya hücreler için bir tanımlar.

     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]

9. Aşağıdaki deyimlerini Şerit kod dosyasının en üstüne ekleyin.

     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]

## <a name="remove-controls-from-the-worksheet"></a>Çalışma sayfasından denetimleri kaldırma
 Çalışma sayfası kaydedilip kapatıldığında denetimler kalıcı olmaz. Çalışma sayfası kaydedilmeden önce oluşturulan tüm Windows Forms denetimlerini program aracılığıyla kaldırmalı veya çalışma kitabı yeniden açıldığında yalnızca denetimin bir anahattı görünür. <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>Oluşturulan konak öğesinin denetimler koleksiyonundan Windows Forms denetimlerini kaldıran olaya kod ekleyin. Daha fazla bilgi için bkz. [Dinamik denetimleri Office belgelerinde kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

### <a name="to-remove-controls-from-the-worksheet"></a>Çalışma sayfasından denetimleri kaldırmak için

1. **Çözüm Gezgini**' de *ThisAddIn.cs* veya *ThisAddIn. vb*öğesini seçin.

2. **Görünüm** menüsünde **kod**' a tıklayın.

3. Sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Bu kod çalışma kitabındaki ilk çalışma sayfasını alır ve sonra `HasVstoObject` çalışma sayfasında oluşturulmuş bir çalışma sayfası nesnesi olup olmadığını denetlemek için yöntemini kullanır. Oluşturulan çalışma sayfası nesnesinin denetimleri varsa, kod bu çalışma sayfası nesnesini alır ve denetim koleksiyonu aracılığıyla dolaşır, denetimleri kaldırır.

     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]

4. C# ' de, olay için bir olay işleyicisi oluşturmanız gerekir <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> . Bu kodu `ThisAddIn_Startup` yöntemine yerleştirebilirsiniz. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md). `ThisAddIn_Startup` yöntemini aşağıdaki kodla değiştirin.

     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]

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

     Seçili hücreler için bir liste nesnesi eklendi.

9. Çalışma sayfasını kaydedin.

     Sheet1 'e eklediğiniz denetimler artık görünmez.

## <a name="next-steps"></a>Sonraki adımlar
 Bu konudaki Excel VSTO eklenti projelerinde denetimler hakkında daha fazla bilgi edinebilirsiniz:

- Denetimlerin çalışma sayfasına nasıl kaydedileceği hakkında bilgi edinmek için bkz. [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)KONUMUNDAKI Excel VSTO eklentisi dinamik denetimleri örneği.

## <a name="see-also"></a>Ayrıca bkz.
- [Excel çözümleri](../vsto/excel-solutions.md)
- [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [ListObject denetimi](../vsto/listobject-control.md)
