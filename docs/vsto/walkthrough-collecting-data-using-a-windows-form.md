---
title: 'izlenecek yol: Windows formu kullanarak veri toplama'
description: Microsoft Excel için belge düzeyi özelleştirmesindeki bir Windows formunu açın, kullanıcıdan bilgi toplayın ve bu bilgileri bir çalışma sayfası hücresine yazın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 422fe752d75caad04023da2306428a2e26e82afd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633777"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>izlenecek yol: Windows formu kullanarak veri toplama
  bu kılavuzda, Microsoft Office Excel için belge düzeyi özelleştirmesindeki bir Windows formunun nasıl açılacağı, kullanıcıdan bilgi toplamadan ve bu bilgilerin bir çalışma sayfası hücresine nasıl yazılacağı gösterilmektedir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 bu izlenecek yol, Excel için belge düzeyi bir proje kullansa da, izlenecek yol tarafından gösterilen kavramlar diğer Office projelerine uygulanabilir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Yeni proje oluşturma
 ilk adım Excel bir çalışma kitabı projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **winforminput** adında bir Excel çalışma kitabı projesi oluşturun ve sihirbazda **yeni belge oluştur** ' u seçin. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **wınforminput** projesini **Çözüm Gezgini** ekler.

## <a name="add-a-namedrange-control-to-the-worksheet"></a>Çalışma sayfasına NamedRange denetimi ekleme

### <a name="to-add-a-named-range-to-sheet1"></a>Sayfa1 'e adlandırılmış bir Aralık eklemek için

1. **A1** hücresini seçin `Sheet1` .

2. **Ad** kutusuna **forminput** yazın.

     **Ad** kutusu, formül çubuğunun solunda, çalışma sayfasının yalnızca **bir** sütununda bulunur.

3.  **Enter** tuşuna basın.

     <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** hücresine bir denetim eklenir. Çalışma sayfasında görünür bir işaret yoktur, ancak **Forminput** , **ad** kutusunda (sağ taraftaki çalışma sayfasının hemen üzerinde) ve **a1** hücresi seçildiğinde **Özellikler** penceresinde görünür.

## <a name="add-a-windows-form-to-the-project"></a>projeye Windows Form ekleme
 kullanıcıdan bilgi istemek için bir Windows formu oluşturun.

### <a name="to-add-a-windows-form"></a>Windows Form eklemek için

1. **Çözüm Gezgini**, **Winforminput** projesini seçin.

2. **Project** menüsünde, **Windows Form ekle**' ye tıklayın.

3. **GetInputString. vb** veya **GetInputString. cs** biçimini adlandırın ve ardından **Ekle**' ye tıklayın.

    Yeni form tasarımcıda açılır.

4. Forma bir <xref:System.Windows.Forms.TextBox> ve ekleyin <xref:System.Windows.Forms.Button> .

5. Düğmeyi seçin, **Özellikler** penceresinde özellik **metnini** bulun ve metni **Tamam**' a değiştirin.

   Ardından, `ThisWorkbook.vb` `ThisWorkbook.cs` kullanıcının bilgilerini toplamak için veya ' ye kod ekleyin.

## <a name="display-the-windows-form-and-collecting-information"></a>Windows formunu görüntüleme ve bilgileri toplama
 Windows formunun bir örneğini oluşturun `GetInputString` ve görüntüleyin ve sonra kullanıcının bilgilerini çalışma sayfasındaki bir hücreye yazın.

#### <a name="to-display-the-form-and-collect-information"></a>Formu görüntüleme ve bilgileri toplama

1. **Çözüm Gezgini**' de **ThisWorkbook. vb** veya **ThisWorkbook. cs** öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. <xref:Microsoft.Office.Tools.Excel.Workbook.Open>Olay işleyicisinde `ThisWorkbook` , form için bir değişken bildirmek `GetInputString` ve sonra formu göstermek için aşağıdaki kodu ekleyin.

   > [!NOTE]
   > C# ' de, aşağıdaki olayda gösterildiği gibi bir olay işleyicisi eklemeniz gerekir <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> . olay işleyicileri oluşturma hakkında bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

    :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb" id="Snippet1":::

3. Adlandırılmış bir aralığa metin yazan adlı bir yöntem oluşturun `WriteStringToCell` . Bu yöntem formdan çağrılır ve kullanıcının girişi, <xref:Microsoft.Office.Tools.Excel.NamedRange> `formInput` **a1** hücresinde, denetime geçirilir.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb" id="Snippet2":::

   Sonra, düğmenin Click olayını işlemek için forma kod ekleyin.

## <a name="send-information-to-the-worksheet"></a>Çalışma sayfasına bilgi gönderin

### <a name="to-send-information-to-the-worksheet"></a>Çalışma sayfasına bilgi göndermek için

1. **Çözüm Gezgini**'de **GetInputString** öğesine sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

2. Düğme olay işleyicisi eklenmiş olarak kod dosyasını açmak için düğmeye çift tıklayın <xref:System.Windows.Forms.Control.Click> .

3. Metin kutusundan girişi almak için olay işleyicisine kod ekleyin, bunu işleve gönderin `WriteStringToCell` ve sonra formu kapatın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb" id="Snippet3":::

## <a name="test"></a>Test etme
 Artık projeyi çalıştırabilirsiniz. Windows Form görüntülenir ve giriş sayfası çalışma sayfasında görünür.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Windows formunun göründüğünü onaylayın.

3. Metin kutusuna **Merhaba Dünya** yazın ve ardından **Tamam**' a tıklayın.

4. **Merhaba Dünya** çalışma sayfasının **a1** hücresinde göründüğünü onaylayın.

## <a name="next-steps"></a>Sonraki adımlar
 bu izlenecek yol, bir Windows formu gösterme ve bir çalışma sayfasına veri geçirme temellerini gösterir. Gerçekleştirmek isteyebileceğiniz diğer görevler şunlardır:

- bir Excel çalışma kitabında veya Word belgesinde Windows Forms denetimleri kullanın. daha fazla bilgi için bkz. [Office belgelere genel bakış Windows Forms denetimleri](../vsto/windows-forms-controls-on-office-documents-overview.md).

- bir Microsoft Office uygulamasının kullanıcı arabirimini belge düzeyi özelleştirmesindeki veya bir VSTO eklentiden değiştirin. daha fazla bilgi için bkz. [Office uı özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
