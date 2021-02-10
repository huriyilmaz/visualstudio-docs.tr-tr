---
title: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme
description: Visual Studio 'da Office geliştirme araçlarını kullanarak projenize kod oluşturma ve bunları ekleme hakkında bilgi edinin.
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
ms.workload:
- office
ms.openlocfilehash: 908660693abce2f2adf07d98e7f2a451a8f3c8e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956600"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>İzlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme
  Bu izlenecek yol, biçimlendirmeyi değiştirmek için Microsoft Office Excel çalışma sayfasındaki onay kutularını kullanmanın temellerini gösterir. Visual Studio 'da Office geliştirme araçları 'nı kullanarak projenize kod oluşturmanız ve kod eklemeniz gerekir. Sonucu tamamlanmış bir örnek olarak görmek için bkz. [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md): Excel denetimleri örneği.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Çalışma sayfasına metin ve denetimler ekleyin.

- Bir seçenek belirlendiğinde metni biçimlendirin.

- Projenizi test edin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 Bu adımda, Visual Studio 'Yu kullanarak bir Excel çalışma kitabı projesi oluşturacaksınız.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Excel Biçimme** adında bir Excel çalışma kitabı projesi oluşturun. **Yeni belge oluştur** ' un seçili olduğundan emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **Excel biçimlendirme** projesini **Çözüm Gezgini** ekler.

## <a name="add-text-and-controls-to-the-worksheet"></a>Çalışma sayfasına metin ve denetimler ekleme
 Bu izlenecek yol için, <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> denetimde üç denetim ve bazı metinler gerekecektir <xref:Microsoft.Office.Tools.Excel.NamedRange> .

### <a name="to-add-three-check-boxes"></a>Üç onay kutusu eklemek için

1. Çalışma kitabının Visual Studio tasarımcısında açık olduğunu ve açık olduğunu doğrulayın `Sheet1` .

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

8. Excel 'deki biçim grubunun düzenleme grubunda **Hizala**' ya ve ardından **Sola Hizala**' ya tıklayın.

     Üç onay kutusu denetimi, seçtiğiniz ilk denetimin konumunda sol tarafta hizalanır.

     Sonra, <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasına bir denetim sürükleyin.

    > [!NOTE]
    > Ayrıca, <xref:Microsoft.Office.Tools.Excel.NamedRange> **ad** kutusuna **TextFont** yazarak da denetim ekleyebilirsiniz.

#### <a name="to-add-text-to-a-namedrange-control"></a>NamedRange denetimine metin eklemek için

1. Araç kutusunun **Excel denetimleri** sekmesinden bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi **B9** hücresine sürükleyin.

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

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. Aşağıdaki kodu <xref:System.Windows.Forms.Control.Click> onay kutusunun olay işleyicisine ekleyin `applyItalicFont` :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. Aşağıdaki kodu <xref:System.Windows.Forms.Control.Click> onay kutusunun olay işleyicisine ekleyin `applyUnderlineFont` :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. C# ' ta, aşağıda gösterildiği gibi onay kutuları için olay işleyicileri eklemeniz gerekir <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> . Olay işleyicileri oluşturma hakkında bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık, bir onay kutusunu seçtiğinizde veya temizlediğinizde metnin doğru biçimlendirildiğinden emin olmak için çalışma kitabınızı test edebilirsiniz.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Onay kutusunu seçin veya temizleyin.

3. Metnin doğru biçimlendirildiğinden emin olun.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yol, Excel çalışma sayfalarındaki onay kutularını ve biçimlendirme metnini kullanmanın temellerini gösterir. Daha sonra gelebilecek bazı görevler şunlardır:

- Projeyi dağıtma. Daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Bir metin kutusunu doldurmak için düğme kullanma. Daha fazla bilgi için bkz. [Izlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin kutusu görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
