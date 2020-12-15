---
title: Düğmeye metin kutusunda metin kutusu kullanarak metni görüntüleme
description: Microsoft Word için belge düzeyi özelleştirmesindeki düğmeleri ve metin kutularını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1cda1fe3e7430ff30dcc3b3921eb2bcd4d31b699
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522745"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>İzlenecek yol: düğme kullanarak bir belgedeki metin kutusunda metin görüntüleme
  Bu izlenecek yol, Microsoft Office Word için belge düzeyi özelleştirmesinde düğmelerin ve metin kutularının nasıl kullanılacağını gösterir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Belge düzeyindeki bir projede Word belgesine tasarım zamanında denetimler ekleme.

- Düğmeye tıklandığında metin kutusunu doldurma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **My Word düğmesini** kullanarak bir Word belgesi projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Word belgesini açar ve **Çözüm Gezgini** Için **My Word düğme** projesini ekler.

## <a name="add-controls-to-the-word-document"></a>Word belgesine denetim ekleme
 Kullanıcı arabirimi denetimleri, Word belgesindeki bir düğmeden ve metin kutusundan oluşur.

### <a name="to-add-a-button-and-a-text-box"></a>Bir düğme ve metin kutusu eklemek için

1. Belgenin Visual Studio tasarımcısında açık olduğunu doğrulayın.

2. **Araç kutusunun** **ortak denetimler** sekmesinden <xref:Microsoft.Office.Tools.Word.Controls.TextBox> belgeye bir denetim sürükleyin.

   > [!NOTE]
   > Word 'de denetimler varsayılan olarak metin ile satır içinde bırakılır. Word 'deki Seçenekler iletişim kutusunun **düzenleme** sekmesinde varsayılan **seçeneği** değiştirilerek denetimlerin ve şekil nesnelerinin eklenme şeklini değiştirebilirsiniz.

3. **Görünüm** menüsünde **Özellikler penceresi**' ne tıklayın.

4. **Özellikler** penceresi açılan kutusunda **textBox1** ' i bulun ve metin kutusunun Name özelliğini **metinadı** olarak değiştirin. 

5. Bir **düğme** denetimini belgeye sürükleyin ve aşağıdaki özellikleri değiştirin.

   |Özellik|Değer|
   |--------------|-----------|
   |**Ad**|**InsertText**|
   |**Metin**|**Metin ekle**|

   Artık düğme tıklandığında çalıştırılacak kodu yazabilirsiniz.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Düğmeye tıklandığında metin kutusunu doldur
 Kullanıcı düğmeye her tıkladığında **Merhaba Dünya!** metin kutusuna eklenir.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Düğmeye tıklandığında metin kutusuna yazmak için

1. **Çözüm Gezgini**' de, **ThisDocument**' e sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.

2. Aşağıdaki kodu <xref:System.Windows.Forms.Control.Click> düğmenin olay işleyicisine ekleyin.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. C# ' de, olaya düğme için bir olay işleyicisi eklemeniz gerekir <xref:Microsoft.Office.Tools.Word.Document.Startup> . Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Uygulamayı test etme
 Artık Merhaba Dünya iletinin olduğundan emin olmak için belgenizi test edebilirsiniz **!** düğmeye tıkladığınızda metin kutusunda görünür.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Düğmesine tıklayın.

3. Merhaba Dünya doğrulayın **!** metin kutusunda görünür.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yol, Word belgelerindeki düğmeleri ve metin kutularını kullanmanın temellerini gösterir. Daha sonra gelebilecek bazı görevler şunlardır:

- Biçimlendirmeyi değiştirmek için Birleşik giriş kutusu kullanma. Daha fazla bilgi için bkz. [Izlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Grafik stillerini seçmek için radyo düğmelerini kullanma. Daha fazla bilgi için bkz. [Izlenecek yol: radyo düğmelerini kullanarak bir belgedeki grafiği güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
