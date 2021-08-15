---
title: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme
description: Projenize kod oluşturmak Office eklemek için Visual Studio geliştirme araçlarını nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: c51872c10e015f0e40332ae3d4c64c7182ab1e35e55386b6125323ed73608ecb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121296534"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Adım adım kılavuz: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme
  Bu kılavuzda, biçimlendirmeyi değiştirmek için çalışma sayfasındaki onay kutularını Microsoft Office Excel temel bilgiler yer almaktadır. Projenize kod Office eklemek için Visual Studio geliştirme araçlarını kullanır ve bu araçları kullanabilirsiniz. Sonucu tamamlanmış bir örnek olarak görmek için, geliştirme Excel ve [izlenecek yollar Office Denetimler Örneği'ne bakın.](../vsto/office-development-samples-and-walkthroughs.md)

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu kılavuzda şunları yapmayı öğrenirsiniz:

- Çalışma sayfasına metin ve denetim ekleme.

- Bir seçenek seçildiğinde metni biçimlendirin.

- Projenizi test etmek.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 Bu adımda, Visual Studio kullanarak Excel Workbook projesi Visual Studio.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. My Excel Formatting adıyla bir çalışma kitabı **Excel oluşturun.** Yeni belge **oluştur'ın seçili olduğundan** emin olun. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **My Excel Formatting** projesini **Çözüm Gezgini.**

## <a name="add-text-and-controls-to-the-worksheet"></a>Çalışma sayfasına metin ve denetim ekleme
 Bu kılavuz için bir denetimde üç <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> denetime ve bazı metinlere ihtiyacınız <xref:Microsoft.Office.Tools.Excel.NamedRange> vardır.

### <a name="to-add-three-check-boxes"></a>Üç onay kutusu eklemek için

1. Çalışma kitabının tasarımcıda açık olduğunu Visual Studio olduğunu `Sheet1` doğrulayın.

2. Araç Kutusunun **Ortak Denetimler** **sekmesinden,** bir denetimi Sayfa1'de B2 hücresine <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> **veya** yakın **bir hücreye sürükleyin.**

3. Görünüm menüsünde **Özellikler** penceresini **seçin.**

4. Özellikler penceresinin nesne adı listesi kutusunda **Checkbox1'in** görünür olduğundan **emin** olun ve aşağıdaki özellikleri değiştirin:

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**applyBoldFont**|
    |**Metin**|**Kalın**|

5. İkinci bir onay kutusunu B4 hücresine veya **yakınına sürükleyin** ve aşağıdaki özellikleri değiştirin:

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**applyYikFont**|
    |**Metin**|**İtalik**|

6. Üçüncü bir onay kutusunu B6 hücresine veya **yakınına sürükleyin** ve aşağıdaki özellikleri değiştirin:

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**applyUnderlineFont**|
    |**Metin**|**Altı çizili**|

7. Ctrl tuşunu basılı tutarak üç onay kutusu **denetimi de seçin.**

8. Excel'daki Biçim sekmesinin Düzenle Grubunda, Hizala'ya ve **ardından** Sola Hizala'ya **tıklayın.**

     Üç onay kutusu denetimi, sol tarafta, seçtiğiniz ilk denetimin konumunda hizalanır.

     Ardından, bir denetimi çalışma <xref:Microsoft.Office.Tools.Excel.NamedRange> sayfasına sürükleyin.

    > [!NOTE]
    > Name kutusuna <xref:Microsoft.Office.Tools.Excel.NamedRange> **textFont yazarak da** denetimi **ebilirsiniz.**

#### <a name="to-add-text-to-a-namedrange-control"></a>NamedRange denetimine metin eklemek için

1. Araç **Excel Denetimler** sekmesinden bir denetimi <xref:Microsoft.Office.Tools.Excel.NamedRange> **B9 hücresine sürükleyin.**

2. Düzenlenebilir **$B kutusunda 9 ABD** Doları'nın görüntülendiğinden ve **B9 hücrenin seçili olduğunu** doğrulayın. Yoksa, seçmek için **B9 hücresine** tıklayın.

3. **Tamam**'a tıklayın.

4. B9 **hücresi** adlı bir aralık haline `NamedRange1` gelir.

    Çalışma sayfasında görünür bir gösterge yoktur, ancak B9 hücresi seçildiğinde Ad kutusunda (sol tarafta çalışma sayfasının `NamedRange1` hemen üzerinde)  görünür. 

5. Özellikler penceresinin nesne adı listesi kutusunda **NamedRange1'in** görünür olduğundan **emin** olun ve aşağıdaki özellikleri değiştirin:

   |Özellik|Değer|
   |--------------|-----------|
   |**Ad**|**textFont**|
   |**Değer2**|**Bu metnin biçimlendirmesini değiştirmek için bir onay kutusuna tıklayın.**|

   Ardından, bir seçenek seçildiğinde metni biçimlendirmek için kodu yazın.

## <a name="format-the-text-when-an-option-is-selected"></a>Bir seçenek seçildiğinde metni biçimlendirme
 Bu bölümde, kullanıcı bir biçimlendirme seçeneğine sahip olduğunda çalışma sayfasındaki metnin biçiminin değişmesi için kod yazacaksiniz.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Onay kutusu seçildiğinde biçimlendirmeyi değiştirmek için

1. Sayfa1'e **sağ** tıklayın ve ardından kısayol **menüsünde Kodu** Görüntüle'ye tıklayın.

2. Onay kutusunun olay <xref:System.Windows.Forms.Control.Click> işleyicisi için aşağıdaki `applyBoldFont` kodu ekleyin:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet7":::

3. Onay kutusunun olay <xref:System.Windows.Forms.Control.Click> işleyicisi için aşağıdaki `applyItalicFont` kodu ekleyin:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet8":::

4. Onay kutusunun olay <xref:System.Windows.Forms.Control.Click> işleyicisi için aşağıdaki `applyUnderlineFont` kodu ekleyin:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet9":::

5. C# içinde, aşağıda gösterildiği gibi olay onay kutuları için olay <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> işleyicileri eklemeniz gerekir. Olay işleyicileri oluşturma hakkında daha fazla bilgi için [bkz. Nasıl oluşturulur: Office projelerinde olay işleyicileri oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık çalışma kitabınızı test etmek için bir onay kutusunu işaretle veya temizle seçeneğiyle metnin doğru biçimlendirilmiş olduğundan emin olun.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Onay kutusunu seçin veya temizleyin.

3. Metnin doğru biçimlendirilmiş olduğunu onaylayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuzda, çalışma sayfalarında onay kutularını kullanmanın ve metin biçimlendirmenin Excel yer almaktadır. Bir sonraki görevlerden bazıları:

- Projeyi dağıtma. Daha fazla bilgi için [bkz. Office kullanarak bir ClickOnce.](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- Bir metin kutusunu doldurmak için düğme kullanma. Daha fazla bilgi için [bkz. Adım adım: Düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme.](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Belgelerde Windows Forms denetimlerinin Office sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
