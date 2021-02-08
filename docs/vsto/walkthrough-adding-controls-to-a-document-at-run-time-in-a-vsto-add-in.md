---
title: VSTO eklentisinin çalışma zamanında belgeye denetim ekleme
description: Kullanıcıların bir düğmeye bir düğme sınıfı veya bir zengin Textcontentcontrol arabirimi eklemesini sağlamak için Şeriti nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3cc88b5ee48241a15a66144c992936b55fb2acf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838093"
---
# <a name="walkthrough-add-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>İzlenecek yol: bir VSTO eklentisinin çalışma zamanında belgeye denetim ekleme
  Bir VSTO eklentisi kullanarak herhangi bir açık Microsoft Office Word belgesine denetim ekleyebilirsiniz. Bu izlenecek yol, kullanıcıların bir <xref:Microsoft.Office.Tools.Word.Controls.Button> belgeye veya bir belge eklemesine olanak tanımak için şerit 'in nasıl kullanılacağını gösterir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .

 **Uygulama hedefi:** Bu konudaki bilgiler Word 2010 için VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Yeni bir Word VSTO eklentisi projesi oluşturuluyor.

- Belgeye denetim eklemek için bir kullanıcı arabirimi (UI) sağlama.

- Çalışma zamanında belgeye denetim ekleme.

- Denetimlerin belgeden kaldırılması.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-word-add-in-project"></a>Yeni bir Word eklentisi projesi oluştur
 Bir Word VSTO eklentisi projesi oluşturarak başlayın.

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Yeni bir Word VSTO eklentisi projesi oluşturmak için

1. Word için, **WordDynamicControls** ADLı bir VSTO eklenti projesi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** derlemesine bir başvuru ekleyin. Bu izlenecek yolda daha sonra belgeye Windows Forms bir denetim eklemek için bu başvuru gerekir.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Belgeye denetim eklemek için bir kullanıcı arabirimi sağlama
 Word 'deki Şerite özel bir sekme ekleyin. Kullanıcılar bir belgeye denetim eklemek için sekmedeki onay kutularını seçebilir.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Belgeye denetim eklemek için bir kullanıcı arabirimi sağlamak için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin.

3. Yeni şeridin adını **MyRibbon** olarak değiştirin ve **Ekle**' ye tıklayın.

    **MyRibbon.cs** veya **MyRibbon. vb** dosyası Şerit Tasarımcısı 'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4. Şerit tasarımcısında, **grup1** grubuna tıklayın.

5. **Özellikler** penceresinde, **grup1** Için **Label** özelliğini, **Denetimler Ekle** olarak değiştirin.

6. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden **Group1** üzerine bir **CheckBox** denetimi sürükleyin.

7. Seçmek için **CheckBox1** öğesine tıklayın.

8. **Özellikler** penceresinde, aşağıdaki özellikleri değiştirin.

   | Özellik | Değer |
   |-----------|-----------------------|
   | **Ad** | **addButtonCheckBox** |
   | **Etiketle** | **Düğme Ekle** |

9. **Group1** öğesine ikinci bir onay kutusu ekleyin ve ardından aşağıdaki özellikleri değiştirin.

   | Özellik | Değer |
   |-----------|---------------------------|
   | **Ad** | **addRichTextCheckBox** |
   | **Etiketle** | **Zengin metin denetimi ekleme** |

10. Şerit Tasarımcısı ' nda, **Ekle düğmesine** çift tıklayın.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> **Düğme Ekle** onay kutusunun olay işleyicisi kod düzenleyicisinde açılır.

11. Şerit Tasarımcısına dönün ve **zengin metin denetimi Ekle**' ye çift tıklayın.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> **Zengin metin denetimi Ekle** onay kutusunun olay Işleyicisi, kod düzenleyicisinde açılır.

    Bu izlenecek yolda daha sonra, etkin belgede denetim eklemek ve kaldırmak için bu olay işleyicilerine kod ekleyeceksiniz.

## <a name="add-and-remove-controls-on-the-active-document"></a>Etkin belgede denetim ekleme ve kaldırma
 VSTO eklenti kodunda, bir denetim ekleyebilmeniz için etkin belgeyi bir <xref:Microsoft.Office.Tools.Word.Document> *konak öğesine* dönüştürmeniz gerekir. Office çözümlerinde, yönetilen denetimler yalnızca, denetimler için kapsayıcılar olarak davranan konak öğelerine eklenebilir. VSTO eklenti projelerinde, konak öğeleri yöntemi kullanılarak çalışma zamanında oluşturulabilir `GetVstoObject` .

 `ThisAddIn`Etkin belgeyi eklemek veya kaldırmak için çağrılabilecek sınıfa Yöntemler ekleyin <xref:Microsoft.Office.Tools.Word.Controls.Button> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . Bu izlenecek yolda daha sonra <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Şeritteki onay kutularının olay işleyicilerinden bu yöntemleri çağıracaksınız.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Etkin belgede denetim ekleme ve kaldırma

1. **Çözüm Gezgini**, dosyayı kod düzenleyicisinde açmak için *ThisAddIn.cs* veya *ThisAddIn. vb* öğesine çift tıklayın.

2. Aşağıdaki kodu `ThisAddIn` sınıfına ekleyin. Bu kod, <xref:Microsoft.Office.Tools.Word.Controls.Button> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgeye eklenecek denetimleri temsil eden nesneler bildirir.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]

3. Sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Kullanıcı Şeritteki **Düğme Ekle** onay kutusuna tıkladığında, <xref:Microsoft.Office.Tools.Word.Controls.Button> onay kutusu seçiliyse, bu yöntem belgedeki geçerli seçime ekler veya <xref:Microsoft.Office.Tools.Word.Controls.Button> onay kutusunun işareti kaldırılmışsa kaldırır.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]

4. Sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Kullanıcı Şeritteki **zengin metin denetimi Ekle** onay kutusuna tıkladığında, <xref:Microsoft.Office.Tools.Word.RichTextContentControl> onay kutusu seçili olduğunda bu yöntem belgedeki geçerli seçime ekler veya <xref:Microsoft.Office.Tools.Word.RichTextContentControl> onay kutusunun işareti kaldırılmışsa kaldırır.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Belge kaydedildiğinde düğme denetimini kaldır
 Windows Forms denetimleri belge kaydedilip kapatıldığında kalıcı olmaz. Ancak, her denetim için bir ActiveX sarmalayıcı belgede kalır ve belge yeniden açıldığında bu sarmalayıcının kenarlığı son kullanıcılar tarafından görülebilir. VSTO eklentilerinde dinamik olarak oluşturulan Windows Forms denetimlerini temizlemek için birkaç yol vardır. Bu kılavuzda, belge kaydedildiğinde denetimi programlı bir şekilde kaldırırsınız <xref:Microsoft.Office.Tools.Word.Controls.Button> .

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Belge kaydedildiğinde düğme denetimini kaldırmak için

1. *ThisAddIn.cs* veya *ThisAddIn. vb* kod dosyasında sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Bu yöntem, olay için bir olay işleyicisidir <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Kaydedilen belgenin <xref:Microsoft.Office.Tools.Word.Document> kendisiyle ilişkili bir konak öğesi varsa, olay işleyicisi konak öğesini alır ve varsa <xref:Microsoft.Office.Tools.Word.Controls.Button> denetimi kaldırır.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]

2. C# ' de, olay işleyicisine aşağıdaki kodu ekleyin `ThisAddIn_Startup` . Olay işleyicisini olayla bağlamak Için C# dilinde bu kod gereklidir `Application_DocumentBeforeSave` <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Kullanıcı Şeritteki onay kutularına tıkladığında denetimleri Ekle ve Kaldır
 Son olarak, <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> belgeye denetim eklemek veya kaldırmak için şerit 'e eklediğiniz onay kutularının olay işleyicilerini değiştirin.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Kullanıcı Şeritteki onay kutularına tıkladığında denetim eklemek veya kaldırmak için

1. *MyRibbon.cs* veya *MyRibbon. vb* kod dosyasında, oluşturulan `addButtonCheckBox_Click` ve `addRichTextCheckBox_Click` olay işleyicilerini aşağıdaki kodla değiştirin. Bu kod, bu `ToggleButtonOnDocument` `ToggleRichTextControlOnDocument` `ThisAddIn` izlenecek yolda daha önce sınıfa eklediğiniz ve yöntemlerini çağırmak için bu olay işleyicilerini yeniden tanımlar.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]

## <a name="test-the-solution"></a>Çözümü test etme
 Şeritteki özel sekmeden seçerek belgeye denetimler ekleyin. Belgeyi kaydettiğinizde <xref:Microsoft.Office.Tools.Word.Controls.Button> denetim kaldırılır.

### <a name="to-test-the-solution"></a>Çözümü test etmek için.

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Etkin belgede, belgeye yeni boş paragraflar eklemek için birkaç kez **ENTER** tuşuna basın.

3. İlk paragrafı seçin.

4. **Eklentiler** sekmesine tıklayın.

5. **Denetimleri Ekle** grubunda, **Ekle düğmesine** tıklayın.

     İlk paragrafta bir düğme belirir.

6. Son paragrafı seçin.

7. **Denetimleri Ekle** grubunda **zengin metin denetimi Ekle**' ye tıklayın.

     Son paragrafa zengin metin içerik denetimi eklenir.

8. Belgeyi kaydedin.

     Düğme belgeden kaldırılır.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan VSTO Eklentilerindeki denetimler hakkında daha fazla bilgi edinebilirsiniz:

- Çalışma zamanında bir belgeye birçok farklı denetim türünün nasıl ekleneceğini ve belgeyi yeniden açtığınızda denetimleri yeniden oluşturmayı gösteren bir örnek için, bkz. [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md): Word Add-In dinamik denetimler örneği.

- Excel için VSTO eklentisini kullanarak çalışma sayfasına nasıl denetim ekleneceğini gösteren bir izlenecek yol için bkz. [Izlenecek yol: çalışma ZAMANıNDA VSTO eklenti projesindeki denetimleri ekleme](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Word çözümleri](../vsto/word-solutions.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office belgelerinde dinamik denetimleri kalıcı hale getirme](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
