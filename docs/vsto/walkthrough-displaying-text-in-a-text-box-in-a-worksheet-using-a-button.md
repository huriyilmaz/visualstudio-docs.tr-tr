---
title: Düğme kullanarak çalışma sayfasındaki metin kutusu içinde metni görüntüle
description: Microsoft Excel çalışma sayfalarında düğme ve metin kutusu kullanmayla ilgili temel bilgileri öğrenin. Visual Studio 'da Office geliştirme araçları 'nı kullanarak da Excel projeleri oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1209bf903f5a5b9c0005d9ba4ba6a891752aedd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827792"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>İzlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme
  Bu izlenecek yol, Excel çalışma sayfalarında düğme ve metin Microsoft Office kutusu kullanmanın temel bilgilerini ve Visual Studio 'da Office geliştirme araçları 'nı kullanarak Excel projeleri oluşturmayı gösterir. Sonucu tamamlanmış bir örnek olarak görmek için bkz. [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md): Excel denetimleri örneği.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Çalışma sayfasına denetimler ekleme.

- Düğmeye tıklandığında bir metin kutusunu doldurun.

- Projenizi test edin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 Bu adımda, Visual Studio kullanarak bir Excel çalışma kitabı projesi oluşturacaksınız.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Excel 'i Adlandır **düğmesini** kullanarak bir Excel çalışma kitabı projesi oluşturun. **Yeni belge oluştur** ' un seçili olduğundan emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **Excel düğme** projesini **Çözüm Gezgini** ekler.

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Bu kılavuzda, ilk çalışma sayfasında bir düğmeye ve bir metin kutusuna ihtiyacınız olacaktır.

### <a name="to-add-a-button-and-a-text-box"></a>Bir düğme ve metin kutusu eklemek için

1. **Excel Button.xlsx** çalışma kitabının, Visual Studio tasarımcısında `Sheet1` görüntülendiğini doğrulayın.

2. Araç kutusunun **ortak denetimler** sekmesinden bir <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> öğesine sürükleyin `Sheet1` .

3. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

4. **Özellikler** penceresi açılır kutusunda **textBox1** ' in göründüğünden emin olun ve metin kutusunun **Name özelliğini metinadı** olarak değiştirin. 

5. Bir **düğme** denetimini üzerine sürükleyin `Sheet1` ve aşağıdaki özellikleri değiştirin:

   |Özellik|Değer|
   |--------------|-----------|
   |**Ad**|**InsertText**|
   |**Metin**|**Metin ekle**|

   Şimdi düğme tıklandığında çalıştırılacak kodu yazın.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Düğmeye tıklandığında metin kutusunu doldur
 Kullanıcı düğmeyi her tıkladığında **Merhaba Dünya!** metin kutusuna eklenir.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Düğmeye tıklandığında metin kutusuna yazmak için

1. **Çözüm Gezgini**, **Sheet1**' e sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.

2. Aşağıdaki kodu <xref:System.Windows.Forms.Control.Click> düğmenin olay işleyicisine ekleyin:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet11":::

3. C# ' de, <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> olaya aşağıda gösterildiği gibi bir olay işleyicisi eklemeniz gerekir. Olay işleyicileri oluşturma hakkında bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet12":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık Merhaba Dünya ileti olduğundan emin olmak için çalışma kitabınızı test edebilirsiniz **!** düğmeye tıkladığınızda metin kutusunda görünür.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Düğmesine tıklayın.

3. Merhaba Dünya doğrulayın **!** metin kutusunda görünür.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yol, Excel çalışma sayfalarında düğme ve metin kutusu kullanmanın temellerini gösterir. Daha sonra gelebilecek bazı görevler şunlardır:

- Projeyi dağıtma. Daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

- Biçimlendirmeyi değiştirmek için onay kutuları kullanma. Daha fazla bilgi için bkz. [Izlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
- [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
