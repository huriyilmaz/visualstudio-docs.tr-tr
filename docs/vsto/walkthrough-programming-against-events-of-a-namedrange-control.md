---
title: 'İzlenecek yol: NamedRange denetimi olaylarına karşı programlama'
description: Visual Studio 'da Office geliştirme araçları 'nı kullanarak Microsoft Excel çalışma sayfasına ve programına yönelik olarak bir NamedRange denetimini nasıl ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec1c670867fae277a3c3c8290cd34d0d4be7ddf3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824971"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>İzlenecek yol: NamedRange denetimi olaylarına karşı programlama
  Bu izlenecek yol <xref:Microsoft.Office.Tools.Excel.NamedRange> , Visual Studio 'Da Office geliştirme araçları 'nı kullanarak Microsoft Office Excel çalışma sayfasına ve programına yönelik bir denetimin nasıl ekleneceğini gösterir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- <xref:Microsoft.Office.Tools.Excel.NamedRange>Çalışma sayfasına bir denetim ekleyin.

- <xref:Microsoft.Office.Tools.Excel.NamedRange>Denetim olaylarına karşı program.

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

1. **Adlandırılmış Aralık olaylarım** adlı bir Excel çalışma kitabı projesi oluşturun. **Yeni belge oluştur** ' un seçili olduğundan emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **Çözüm Gezgini** **Adlandırılmış Aralık olayları** projesini ekler.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Çalışma sayfasına metin ve adlandırılmış aralıklar ekleme
 Konak denetimleri genişletilmiş Office nesneleri olduğundan, bunları belgenize yerel nesneyi ekleyeceğiniz şekilde ekleyebilirsiniz. Örneğin, <xref:Microsoft.Office.Tools.Excel.NamedRange> **Ekle** menüsünü açıp **ad**' ın üzerine gelip **Tanımla**' yı seçerek bir çalışma sayfasına Excel denetimi ekleyebilirsiniz. Ayrıca, <xref:Microsoft.Office.Tools.Excel.NamedRange> **araç kutusundan** çalışma sayfasına sürükleyerek bir denetim ekleyebilirsiniz.

 Bu adımda, **araç kutusunu** kullanarak çalışma sayfasına iki adlandırılmış aralık denetimi ekleyecek ve ardından çalışma sayfasına metin ekleyeceksiniz.

### <a name="to-add-a-range-to-your-worksheet"></a>Çalışma sayfanıza bir Aralık eklemek için

1. *Adlandırılmış aralık Events.xlsx* çalışma kitabının, Visual Studio tasarımcısında görüntülenmiş olarak açık olduğunu doğrulayın `Sheet1` .

2. Araç kutusunun **Excel denetimleri** sekmesinden, <xref:Microsoft.Office.Tools.Excel.NamedRange> içindeki **a1** hücresine bir denetim sürükleyin `Sheet1` .

     **NamedRange denetimi Ekle** iletişim kutusu görünür.

3. **$A $1** ' nin düzenlenebilir metin kutusunda göründüğünü ve **a1** hücresinin seçildiğini doğrulayın. Aksi takdirde, seçmek için **a1** hücresini tıklatın.

4. **Tamam**'a tıklayın.

     **A1** hücresi adlı bir aralığa dönüşür `namedRange1` . Çalışma sayfasında görünür bir gösterge yoktur, ancak `namedRange1` **a1** hücresi seçildiğinde **ad** kutusunda (sol taraftaki çalışma sayfasının hemen üzerinde bulunur) görünür.

5. <xref:Microsoft.Office.Tools.Excel.NamedRange> **B3** hücresine başka bir denetim ekleyin.

6. **$B $3** ' nin düzenlenebilir metin kutusunda göründüğünü ve **B3** hücresinin seçildiğini doğrulayın. Aksi takdirde, seçmek için hücre **B3** ' e tıklayın.

7. **Tamam**'a tıklayın.

     **B3** hücresi adlı bir aralığa dönüşür `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Çalışma sayfanıza metin eklemek için

1. **A1** hücresinde aşağıdaki metni yazın:

    **Bu, NamedRange denetimine bir örnektir.**

2. **A3** hücresinde (soluna `namedRange2` ) aşağıdaki metni yazın:

    **Olayları**

   Aşağıdaki bölümlerde, içine metin ekleyen `namedRange2` ve, `namedRange2` ve olaylarına yanıt olarak denetimin özelliklerini değiştiren bir kod yazacaksınız <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>BeforeDoubleClick olayına yanıt vermek için kod ekleme

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>BeforeDoubleClick olayına göre NamedRange2 içine metin eklemek için

1. **Çözüm Gezgini**, **Sheet1. vb** veya **Sheet1. cs** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.

2. Olay işleyicisinin aşağıdakine benzer şekilde kod ekleyin `namedRange1_BeforeDoubleClick` :

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet24":::

3. C# ' de, aşağıdaki olayda gösterildiği gibi, adlandırılmış aralığa yönelik olay işleyicileri eklemeniz gerekir <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> . Olay işleyicileri oluşturma hakkında bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet25":::

## <a name="add-code-to-respond-to-the-change-event"></a>Değişiklik olayına yanıt vermek için kod ekleme

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Değişiklik olayına göre namedRange2 içine metin eklemek için

1. Olay işleyicisinin aşağıdakine benzer şekilde kod ekleyin `NamedRange1_Change` :

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet26":::

    > [!NOTE]
    > Excel aralığındaki bir hücreye çift tıklamak düzenleme moduna girdiğinde, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> metinde değişiklik yapılmasa bile seçim aralığın dışına taşındığında bir olay oluşur.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>SelectionChange olayına yanıt vermek için kod ekleme

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>SelectionChange olayına göre namedRange2 içine metin eklemek için

1. **NamedRange1_SelectionChange** olay işleyicisinin aşağıdaki gibi görünmesi için kod ekleyin:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet27":::

    > [!NOTE]
    > Excel aralığındaki bir hücreye çift tıklamak seçimin aralığa taşınmasına neden olduğundan, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> olay gerçekleşmeden önce bir olay oluşur <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> .

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık, bir denetimin olaylarını açıklayan metnin, <xref:Microsoft.Office.Tools.Excel.NamedRange> Olaylar oluşturulduğunda başka bir adlandırılmış aralığa eklendiğini doğrulamak için çalışma kitabınızı test edebilirsiniz.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. İmlecinizi içine yerleştirin `namedRange1` ve olayla ilgili metnin <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> eklendiğini ve çalışma sayfasına bir yorum eklendiğini doğrulayın.

3. İçine çift tıklayın `namedRange1` ve olaylar ile ilgili metnin <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> içinde kırmızı italik metinle eklendiğini doğrulayın `namedRange2` .

4. Dışında ' `namedRange1` e tıklayın ve metinde değişiklik yapılmasa bile düzenleme modundan çıkarken değişiklik olayının gerçekleşeceğini unutmayın.

5. İçindeki metni değiştirin `namedRange1` .

6. Dışında ' `namedRange1` e tıklayın ve olayla ilgili metnin <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> mavi metinle birlikte eklendiğini doğrulayın `namedRange2` .

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yol, bir denetimin olaylarına karşı programlama temellerini gösterir <xref:Microsoft.Office.Tools.Excel.NamedRange> . Daha sonra gelebilecek bir görev aşağıda verilmiştir:

- Projeyi dağıtma. Daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md)
