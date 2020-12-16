---
title: 'İzlenecek yol: Windows formu kullanarak veri toplama'
description: Microsoft Excel için belge düzeyi özelleştirmesindeki bir Windows formu açın, kullanıcıdan bilgi toplayın ve bu bilgileri bir çalışma sayfası hücresine yazın.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58d6f58f732d4a52aade6ff3678842900f1c29cd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527163"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>İzlenecek yol: Windows formu kullanarak veri toplama
  Bu izlenecek yol, Excel Microsoft Office için belge düzeyi özelleştirmede bir Windows formu açmayı, kullanıcıdan bilgi toplamayı ve bu bilgileri bir çalışma sayfası hücresine yazmayı gösterir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Bu izlenecek yol, Excel için belge düzeyindeki bir projeyi özellikle kullanıyor olsa da, izlenecek yol tarafından gösterilen kavramlar diğer Office projeleri için geçerlidir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Yeni proje oluşturma
 İlk adım bir Excel çalışma kitabı projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Winforminput** adlı bir Excel çalışma kitabı projesi oluşturun ve sihirbazda **Yeni belge oluştur** ' u seçin. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **Çözüm Gezgini** **Winforminput** projesini ekler.

## <a name="add-a-namedrange-control-to-the-worksheet"></a>Çalışma sayfasına NamedRange denetimi ekleme

### <a name="to-add-a-named-range-to-sheet1"></a>Sayfa1 'e adlandırılmış bir Aralık eklemek için

1. **A1** hücresini seçin `Sheet1` .

2. **Ad** kutusuna **forminput** yazın.

     **Ad** kutusu, formül çubuğunun solunda, çalışma sayfasının yalnızca **bir** sütununda bulunur.

3.  **Enter** tuşuna basın.

     <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** hücresine bir denetim eklenir. Çalışma sayfasında görünür bir işaret yoktur, ancak **Forminput** , **ad** kutusunda (sağ taraftaki çalışma sayfasının hemen üzerinde) ve **a1** hücresi seçildiğinde **Özellikler** penceresinde görünür.

## <a name="add-a-windows-form-to-the-project"></a>Projeye bir Windows formu ekleme
 Kullanıcıdan bilgi istemek için bir Windows formu oluşturun.

### <a name="to-add-a-windows-form"></a>Windows formu eklemek için

1. **Çözüm Gezgini**, **Winforminput** projesini seçin.

2. **Proje** menüsünde **Windows formu Ekle**' ye tıklayın.

3. **GetInputString. vb** veya **GetInputString.cs** formunu adlandırın ve ardından **Ekle**' ye tıklayın.

    Yeni form tasarımcıda açılır.

4. Forma bir <xref:System.Windows.Forms.TextBox> ve ekleyin <xref:System.Windows.Forms.Button> .

5. Düğmeyi seçin, **Özellikler** penceresinde özellik **metnini** bulun ve metni **Tamam**' a değiştirin.

   Ardından, `ThisWorkbook.vb` `ThisWorkbook.cs` kullanıcının bilgilerini toplamak için veya ' ye kod ekleyin.

## <a name="display-the-windows-form-and-collecting-information"></a>Windows formunu görüntüleme ve bilgileri toplama
 Windows form 'un bir örneğini oluşturun `GetInputString` ve görüntüleyin ve sonra kullanıcının bilgilerini çalışma sayfasındaki bir hücreye yazın.

#### <a name="to-display-the-form-and-collect-information"></a>Formu görüntüleme ve bilgileri toplama

1. **Çözüm Gezgini**' de **ThisWorkbook. vb** veya **ThisWorkbook.cs** öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. <xref:Microsoft.Office.Tools.Excel.Workbook.Open>Olay işleyicisinde `ThisWorkbook` , form için bir değişken bildirmek `GetInputString` ve sonra formu göstermek için aşağıdaki kodu ekleyin.

   > [!NOTE]
   > C# ' de, aşağıdaki olayda gösterildiği gibi bir olay işleyicisi eklemeniz gerekir <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> . Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]

3. Adlandırılmış bir aralığa metin yazan adlı bir yöntem oluşturun `WriteStringToCell` . Bu yöntem formdan çağrılır ve kullanıcının girişi, <xref:Microsoft.Office.Tools.Excel.NamedRange> `formInput` **a1** hücresinde, denetime geçirilir.

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]

   Sonra, düğmenin Click olayını işlemek için forma kod ekleyin.

## <a name="send-information-to-the-worksheet"></a>Çalışma sayfasına bilgi gönderin

### <a name="to-send-information-to-the-worksheet"></a>Çalışma sayfasına bilgi göndermek için

1. **Çözüm Gezgini**'de **GetInputString** öğesine sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

2. Düğme olay işleyicisi eklenmiş olarak kod dosyasını açmak için düğmeye çift tıklayın <xref:System.Windows.Forms.Control.Click> .

3. Metin kutusundan girişi almak için olay işleyicisine kod ekleyin, bunu işleve gönderin `WriteStringToCell` ve sonra formu kapatın.

     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]

## <a name="test"></a>Test etme
 Artık projeyi çalıştırabilirsiniz. Windows formu görünür ve giriş çalışma sayfasında görünür.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Windows form 'un göründüğünü onaylayın.

3. Metin kutusuna **Merhaba Dünya** yazın ve ardından **Tamam**' a tıklayın.

4. **Merhaba Dünya** çalışma sayfasının **a1** hücresinde göründüğünü onaylayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yol, bir Windows formu gösterme ve bir çalışma sayfasına veri geçirme temellerini gösterir. Gerçekleştirmek isteyebileceğiniz diğer görevler şunlardır:

- Excel çalışma kitabı veya Word belgesi üzerinde Windows Forms denetimleri kullanın. Daha fazla bilgi için bkz. [Office belgelerindeki Windows Forms denetimleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Bir Microsoft Office uygulamasının Kullanıcı arabirimini belge düzeyi özelleştirmesindeki veya VSTO eklentiden değiştirin. Daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
