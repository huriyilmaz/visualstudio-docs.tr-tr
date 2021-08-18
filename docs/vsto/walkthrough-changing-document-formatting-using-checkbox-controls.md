---
title: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme
description: metin biçimlendirmesini değiştirmek için Microsoft Word için belge düzeyi özelleştirmesindeki Windows Forms denetimlerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e9f280b2e8db25788e89bdb66d9ec5455c7a1efe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032062"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>İzlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme
  bu izlenecek yol, metin biçimlendirmesini değiştirmek için Microsoft Office Word için belge düzeyi özelleştirmesinde Windows Forms denetimlerinin nasıl kullanılacağını gösterir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Belge düzeyi projedeki belgeye tasarım zamanında metin ve denetim ekleme.

- Bir seçenek belirlendiğinde metni biçimlendirme.

  sonucu tamamlanmış bir örnek olarak görmek için [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)' da Word denetimleri örneğine bakın.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word belgesi projesi oluşturmaktır.

### <a name="create-a-new-project"></a>Yeni proje oluşturma

1. **Word Biçimme** adlı bir Word belgesi projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin.

     daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio yeni word belgesini tasarımcıda açar ve **word biçimlendirme** projesini **Çözüm Gezgini** ekler.

## <a name="add-text-and-controls-to-the-word-document"></a>Word belgesine metin ve denetimler ekleme
 Bu izlenecek yol için, Word belgesine üç onay kutusu ve bir denetimdeki bazı metinler ekleyin <xref:Microsoft.Office.Tools.Word.Bookmark> . Onay kutuları kullanıcıya metni biçimlendirmek için seçenekler sunar.

### <a name="add-three-check-boxes"></a>Üç onay kutusu Ekle

1. belgenin Visual Studio tasarımcısında açık olduğunu doğrulayın.

2. **Araç kutusunun** **ortak denetimler** sekmesinden, ilk <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> denetimi belgeye sürükleyin.

3. **Özellikler** penceresinde, aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Applybold yazı tipi**|
    |**Metin**|**Kalın**|

4. Ekleme noktasını ilk onay kutusunun altına taşımak için **ENTER** tuşuna basın.

5. Belgeye onay kutusunun altındaki ikinci onay kutusunu ekleyin `ApplyBoldFont` ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**applyItalicFont**|
    |**Metin**|**İtalik**|

6. İkinci onay kutusunun altına ekleme noktasını taşımak için **ENTER** tuşuna basın.

7. Belgeye onay kutusunun altına üçüncü onay kutusu ekleyin `ApplyItalicFont` ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Applyunderlineyazı tipi**|
    |**Metin**|**Altçizgi**|

### <a name="add-text-and-a-bookmark-control"></a>Metin ve yer Işareti denetimi ekleme

1. Ekleme noktasını onay kutusu denetimlerinin altına taşıyın ve aşağıdaki metni yazın:

    **Bu metnin biçimlendirmesini değiştirmek için bir onay kutusuna tıklayın.**

2. **Araç kutusunun** **Word denetimleri** sekmesinden <xref:Microsoft.Office.Tools.Word.Bookmark> belgeye bir denetim sürükleyin.

    **Yer Işareti denetimi Ekle** iletişim kutusu görünür.

3. Belgeye eklediğiniz metni seçin ve **Tamam**' a tıklayın.

    <xref:Microsoft.Office.Tools.Word.Bookmark>Belgedeki seçili metne **Bookmark1** adlı bir denetim eklenir.

4. **Özellikler** penceresinde **(Name)** özelliğinin değerini **fontText** olarak değiştirin.

   Sonra, bir onay kutusu işaretlendiğinde veya temizlendiğinde metni biçimlendirmek için kodu yazın.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Onay kutusu işaretlendiğinde veya temizlendiğinde metni biçimlendirin
 Kullanıcı bir biçimlendirme seçeneği seçerse belgedeki metnin biçimini değiştirin.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Onay kutusu seçildiğinde biçimlendirmeyi Değiştir

1. Çözüm Gezgini ' ye sağ tıklayın `ThisDocument` ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın. 

2. Yalnızca C# için, **ThisDocument** sınıfına aşağıdaki sabitleri ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet2":::

3. <xref:System.Windows.Forms.Control.Click>Onay kutusunun olay işleyicisine aşağıdaki kodu ekleyin `applyBoldFont` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet3":::

4. <xref:System.Windows.Forms.Control.Click>Onay kutusunun olay işleyicisine aşağıdaki kodu ekleyin `applyItalicFont` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet4":::

5. <xref:System.Windows.Forms.Control.Click>Onay kutusunun olay işleyicisine aşağıdaki kodu ekleyin `applyUnderlineFont` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet5":::

6. C# dilinde, olaya metin kutuları için olay işleyicileri eklemeniz gerekir <xref:Microsoft.Office.Tools.Word.Document.Startup> . olay işleyicilerini oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: olay işleyicileri oluşturma Office projelerinde](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık, bir onay kutusunu seçtiğinizde veya temizlediğinizde metnin doğru biçimlendirildiğinden emin olmak için belgenizi test edebilirsiniz.

### <a name="test-your-document"></a>Belgenizi test etme

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Onay kutusunu seçin veya temizleyin.

3. Metnin doğru biçimlendirildiğinden emin olun.

## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuzda, onay kutularını kullanma ve Word belgelerindeki metin biçimlendirmeyi programlama yoluyla değiştirme temelleri gösterilmektedir. Daha sonra gelebilecek bazı görevler şunlardır:

- Bir metin kutusunu doldurmak için düğme kullanın. Daha fazla bilgi için bkz. [Izlenecek yol: bir düğme kullanarak bir belgedeki metin kutusunda metni görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Grafik stillerini seçmek için radyo düğmelerini kullanma. Daha fazla bilgi için bkz. [Izlenecek yol: radyo düğmelerini kullanarak bir belgedeki grafiği güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
