---
title: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme
description: projenize kod oluşturmak ve eklemek için Visual Studio Office geliştirme araçlarını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0f3a543d99b5b701256f1f738d4d79721f96cc5f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025504"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>İzlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme
  bu izlenecek yol, biçimlendirmeyi değiştirmek için Microsoft Office Excel çalışma sayfasındaki onay kutularını kullanmanın temellerini gösterir. projenize kod oluşturmak ve eklemek için Visual Studio Office geliştirme araçları 'nı kullanacaksınız. sonucu tamamlanmış bir örnek olarak görmek için, [Office geliştirme örneklerinde ve izlenecek yollarda](../vsto/office-development-samples-and-walkthroughs.md)Excel denetimleri örneğine bakın.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Çalışma sayfasına metin ve denetimler ekleyin.

- Bir seçenek belirlendiğinde metni biçimlendirin.

- Projenizi test edin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 bu adımda, Visual Studio kullanarak bir Excel çalışma kitabı projesi oluşturacaksınız.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Excel biçimlendirmelerimin** adıyla Excel bir çalışma kitabı projesi oluşturun. **Yeni belge oluştur** ' un seçili olduğundan emin olun. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **Excel biçimlendirme** projesini **Çözüm Gezgini** ekler.

## <a name="add-text-and-controls-to-the-worksheet"></a>Çalışma sayfasına metin ve denetimler ekleme
 Bu izlenecek yol için, <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> denetimde üç denetim ve bazı metinler gerekecektir <xref:Microsoft.Office.Tools.Excel.NamedRange> .

### <a name="to-add-three-check-boxes"></a>Üç onay kutusu eklemek için

1. çalışma kitabının Visual Studio tasarımcısında açık olduğunu ve açık olduğunu doğrulayın `Sheet1` .

2. **Araç kutusu**' nun **ortak denetimler** sekmesinden, bir <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> denetimi **Sheet1** içindeki **B2** hücresine veya yakınında sürükleyin.

3. **Görünüm** menüsünde **Özellikler** penceresi ' ni seçin.

4. **CheckBox1** öğesinin **Özellikler** penceresinin nesne adı liste kutusunda göründüğünden emin olun ve aşağıdaki özellikleri değiştirin:

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Applybold yazı tipi**|
    |**Metin**|**Kalın**|

5. **B4** hücresinde veya yakınında bir ikinci onay kutusu sürükleyin ve aşağıdaki özellikleri değiştirin:

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**applyItalicFont**|
    |**Metin**|**İtalik**|

6. **B6** hücresinde veya yakınında bir üçüncü onay kutusu sürükleyin ve aşağıdaki özellikleri değiştirin:

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Applyunderlineyazı tipi**|
    |**Metin**|**Altçizgi**|

7. **CTRL** tuşunu basılı tutarken üç onay kutusu denetimini seçin.

8. Excel biçim sekmesinin düzenleme grubunda **hizala**' ya ve ardından **sola hizala**' ya tıklayın.

     Üç onay kutusu denetimi, seçtiğiniz ilk denetimin konumunda sol tarafta hizalanır.

     Sonra, <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasına bir denetim sürükleyin.

    > [!NOTE]
    > Ayrıca, <xref:Microsoft.Office.Tools.Excel.NamedRange> **ad** kutusuna **TextFont** yazarak da denetim ekleyebilirsiniz.

#### <a name="to-add-text-to-a-namedrange-control"></a>NamedRange denetimine metin eklemek için

1. araç kutusunun **Excel denetimleri** sekmesinden bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi **B9** hücresine sürükleyin.

2. **$B $9** ' nin düzenlenebilir metin kutusunda göründüğünü ve **B9** hücresinin seçildiğini doğrulayın. Aksi takdirde, seçmek için hücre **B9** ' a tıklayın.

3. **Tamam**'a tıklayın.

4. **B9** hücresi adlı bir Aralık haline gelir `NamedRange1` .

    Çalışma sayfasında görünür bir gösterge yoktur, ancak `NamedRange1` **B9** hücresi seçildiğinde **ad kutusunda** (sol taraftaki çalışma sayfasının hemen üzerinde) görünür.

5. **NamedRange1** 'in **Özellikler** penceresinin nesne adı liste kutusunda göründüğünden emin olun ve aşağıdaki özellikleri değiştirin:

   |Özellik|Değer|
   |--------------|-----------|
   |**Ad**|**textFont**|
   |**Value2**|**Bu metnin biçimlendirmesini değiştirmek için bir onay kutusuna tıklayın.**|

   Sonra, bir seçenek belirlendiğinde metni biçimlendirmek için kodu yazın.

## <a name="format-the-text-when-an-option-is-selected"></a>Bir seçenek belirlendiğinde metni biçimlendirin
 Bu bölümde, Kullanıcı bir biçimlendirme seçeneği seçtiğinde, çalışma sayfasındaki metnin biçiminin değiştirildiği şekilde kod yazacaksınız.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Bir onay kutusu seçildiğinde biçimlendirmeyi değiştirmek için

1. **Sayfa1** öğesine sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.

2. Aşağıdaki kodu <xref:System.Windows.Forms.Control.Click> onay kutusunun olay işleyicisine ekleyin `applyBoldFont` :

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet7":::

3. Aşağıdaki kodu <xref:System.Windows.Forms.Control.Click> onay kutusunun olay işleyicisine ekleyin `applyItalicFont` :

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet8":::

4. Aşağıdaki kodu <xref:System.Windows.Forms.Control.Click> onay kutusunun olay işleyicisine ekleyin `applyUnderlineFont` :

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet9":::

5. C# ' ta, aşağıda gösterildiği gibi onay kutuları için olay işleyicileri eklemeniz gerekir <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> . olay işleyicileri oluşturma hakkında bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık, bir onay kutusunu seçtiğinizde veya temizlediğinizde metnin doğru biçimlendirildiğinden emin olmak için çalışma kitabınızı test edebilirsiniz.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Onay kutusunu seçin veya temizleyin.

3. Metnin doğru biçimlendirildiğinden emin olun.

## <a name="next-steps"></a>Sonraki adımlar
 bu izlenecek yol, Excel çalışma sayfalarında onay kutularını ve biçimlendirme metnini kullanmanın temellerini gösterir. Daha sonra gelebilecek bazı görevler şunlardır:

- Projeyi dağıtma. daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Bir metin kutusunu doldurmak için düğme kullanma. Daha fazla bilgi için bkz. [Izlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin kutusu görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
