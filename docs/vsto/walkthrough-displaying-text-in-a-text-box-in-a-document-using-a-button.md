---
title: Düğme kullanarak belgede metin kutusunda metin görüntüleme
description: Belge düzeyinde özelleştirmeler için düğmeleri ve metin kutularını nasıl kullanabileceğinizi Microsoft Word.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e86ff0baf55be711759cdae47304e2013483e40f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075586"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Adım adım kılavuz: Düğme kullanarak belge içinde metin kutusunda metin görüntüleme
  Bu kılavuzda, Word'de belge düzeyi özelleştirmede düğmelerin ve metin kutularının nasıl Microsoft Office göstereceğiz.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Tasarım zamanında belge düzeyi projesinde Word belgesine denetimler ekleme.

- Bir düğmeye tıkıldığında metin kutusunu doldurmak.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word Belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. Sözcüğüm Düğmesi adıyla bir **Word Belgesi projesi oluşturun.** Sihirbazda Yeni belge **oluştur'a tıklayın.**

     Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio yeni Word belgesini tasarımcıda açar ve My **Word Button** projesini **Çözüm Gezgini.**

## <a name="add-controls-to-the-word-document"></a>Word belgesine denetim ekleme
 Kullanıcı arabirimi denetimleri, Word belgesinde bir düğme ve bir metin kutusundan oluşur.

### <a name="to-add-a-button-and-a-text-box"></a>Düğme ve metin kutusu eklemek için

1. Belgenin tasarımcıda açık olduğunu Visual Studio.

2. Araç **Kutusunun Ortak** Denetimler **sekmesinden,** bir <xref:Microsoft.Office.Tools.Word.Controls.TextBox> denetimi belgeye sürükleyin.

   > [!NOTE]
   > Word'de denetimler varsayılan olarak metinle satır içinde bırakılır. Word'de Seçenekler iletişim kutusunun Düzenle sekmesindeki varsayılan değeri değiştirerek denetimlerin **ve** şekil **nesnelerinin eklenme** şeklini değiştirebilirsiniz.

3. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

4. Özellikler penceresi açılan **kutusunda** **TextBox1'i** bulun ve metin kutusunun **Name** özelliğini displayText olarak **değiştirin.**

5. Bir **Düğme denetimi** belgeye sürükleyin ve aşağıdaki özellikleri değiştirin.

   |Özellik|Değer|
   |--------------|-----------|
   |**Ad**|**insertText**|
   |**Metin**|**Metin Ekle**|

   Artık düğmeye tıkıldığında çalıştıracak kodu yazabilirsiniz.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Düğmeye tıkıldığında metin kutusunu doldurmak
 Kullanıcı düğmeye her tıkladığında **Merhaba Dünya!** metin kutusuna eklenir.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Düğmeye tıkıldığında metin kutusuna yazmak için

1. Bu **Çözüm Gezgini,** **ThisDocument'a sağ tıklayın** ve ardından kısayol menüsünde **Kodu** Görüntüle'ye tıklayın.

2. Düğmenin olay <xref:System.Windows.Forms.Control.Click> işleyicisi için aşağıdaki kodu ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet7":::

3. C# içinde, düğmeye olay için bir olay işleyicisi eklemeniz <xref:Microsoft.Office.Tools.Word.Document.Startup> gerekir. Olay işleyicileri oluşturma hakkında daha fazla bilgi için [bkz. Nasıl oluşturulur: Office projelerinde olay işleyicileri oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet8":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık iletinin doğru olduğundan emin olmak için belgenizi test **Merhaba Dünya!** düğmesine tıklarken metin kutusunda görünür.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Düğmesine tıklayın.

3. Bunu **onaylayın Merhaba Dünya!** metin kutusunda görünür.

## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuz, Word belgelerde düğmeleri ve metin kutularını kullanmanın temellerini gösterir. Bir sonraki görevlerden bazıları:

- Biçimlendirmeyi değiştirmek için birleşik giriş kutusu kullanma. Daha fazla bilgi için [bkz. Adım adım: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme.](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)

- Grafik stillerini seçmek için radyo düğmelerini kullanma. Daha fazla bilgi için, [bkz. Walkthrough: Update a chart in a](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)document using radio buttons .

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Belgelerde form Office genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Office örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Nasıl Windows: Windows Form denetimleri ekleme Office ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
