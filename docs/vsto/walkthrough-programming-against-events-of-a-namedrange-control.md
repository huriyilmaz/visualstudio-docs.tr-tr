---
title: 'Adım adım kılavuz: NamedRange denetimi olaylarına karşı programla'
description: Office geliştirme araçlarını kullanarak Microsoft Excel çalışma sayfasına ve programlarına NamedRange denetimi Visual Studio.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8a6b5ca7d884fbece6795f63d668aa04a8ba6f80
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726097"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Adım adım kılavuz: NamedRange denetimi olaylarına karşı programla
  Bu kılavuzda, Microsoft Office Excel çalışma sayfasındaki geliştirme araçlarını kullanarak Microsoft Office Excel çalışma sayfasına <xref:Microsoft.Office.Tools.Excel.NamedRange> ve programlarına denetim Office nasıl Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu kılavuzda şunları yapmayı öğrenirsiniz:

- Çalışma sayfasına <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim ekleme.

- Denetim olaylarına <xref:Microsoft.Office.Tools.Excel.NamedRange> karşı programla.

- Projenizi test etmek.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 Bu adımda, Excel kullanarak Visual Studio.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. My Named Range Events Excel adlı bir **Çalışma Kitabı projesi oluşturun.** Yeni belge **oluştur'ın seçili olduğundan** emin olun. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve Adlandırılmış Aralık Olaylarım **projesini** **Çözüm Gezgini.**

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Çalışma sayfasına metin ve adlandırılmış aralık ekleme
 Konak denetimleri nesnelere Office, bunları belgenize yerel nesneyi eklerken olduğu gibi ekleyebilirsiniz. Örneğin, Ekle menüsünü açarak Excel üzerine gelin ve Tanımla'ya seçerek çalışma sayfasına bir çalışma <xref:Microsoft.Office.Tools.Excel.NamedRange> sayfası denetimi **ekleyebilirsiniz.**   Bir denetimi Araç <xref:Microsoft.Office.Tools.Excel.NamedRange> Kutusundan çalışma sayfasına **sürükleyerek de** ekleyebilirsiniz.

 Bu adımda, Araç Kutusunu kullanarak çalışma sayfasına iki adlandırılmış aralık denetimi **ekecek ve ardından** çalışma sayfasına metin eksersiniz.

### <a name="to-add-a-range-to-your-worksheet"></a>Çalışma sayfanıza aralık eklemek için

1. Adlandırılmış *Aralığım çalışma Events.xlsx* çalışma kitabının, Visual Studio açık olduğunu `Sheet1` doğrulayın.

2. Araç **kutusunun Excel Denetimler** sekmesinden, bir denetimi içinde <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1 hücresine** `Sheet1` sürükleyin.

     Add **NamedRange Control** iletişim kutusu görüntülenir.

3. Düzenlenebilir **$A kutusunda 1** ABD Doları'nın görüntülendiğinden ve **A1 hücresi seçildiğinden** emin olun. Yoksa, seçmek için **A1 hücresine** tıklayın.

4. **Tamam**'a tıklayın.

     A1 **hücresi** adlı bir aralık haline `namedRange1` gelir. Çalışma sayfasında görünür bir gösterge yoktur, ancak A1 hücresi seçildiğinde Ad kutusunda (sol tarafta çalışma sayfasının hemen üzerinde `namedRange1` bulunur) görünür.  

5. <xref:Microsoft.Office.Tools.Excel.NamedRange>B3 hücresine başka bir **denetim ekleyin.**

6. Düzenlenebilir **$B kutusunda 3** ABD Doları'nın görüntülendiğinden ve **B3 hücresi seçildiğinden** emin olun. Yoksa, seçmek için **B3 hücresine** tıklayın.

7. **Tamam**'a tıklayın.

     B3 **hücresi** adlı bir aralık haline `namedRange2` gelir.

### <a name="to-add-text-to-your-worksheet"></a>Çalışma sayfanıza metin eklemek için

1. **A1 Hücresi'ne** aşağıdaki metni yazın:

    **Bu bir NamedRange denetimi örneğidir.**

2. A3 **Hücresi'ne** (sol `namedRange2` tarafta) aşağıdaki metni yazın:

    **Olay:**

   Aşağıdaki bölümlerde , ve olaylarına yanıt olarak denetimin özelliklerini değiştiren ve içine metin ekleyen `namedRange2` `namedRange2` kod <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> yazacak. `namedRange1`

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>BeforeDoubleClick olayına yanıt vermek için kod ekleme

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>BeforeDoubleClick olayına göre NamedRange2 içine metin eklemek için

1. Bu **Çözüm Gezgini,** **Sayfa1.vb veya Sheet1.cs'ye** sağ tıklayın **ve** Kodu **Görüntüle'yi seçin.**

2. Olay işleyicisi `namedRange1_BeforeDoubleClick` aşağıdaki gibi görünüyor olacak şekilde kod ekleyin:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet24":::

3. C# içinde, aşağıdaki olayda gösterildiği gibi adlandırılmış aralık için olay işleyicileri <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> eklemeniz gerekir. Olay işleyicileri oluşturma hakkında daha fazla bilgi için [bkz. Nasıl oluşturulur: Office projelerinde olay işleyicileri oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet25":::

## <a name="add-code-to-respond-to-the-change-event"></a>Değişiklik olayına yanıt vermek için kod ekleme

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Change olayına göre namedRange2 içine metin eklemek için

1. Olay işleyicisi `NamedRange1_Change` aşağıdaki gibi görünüyor olacak şekilde kod ekleyin:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet26":::

    > [!NOTE]
    > Excel aralığındaki bir hücreye çift tıklarsanız düzenleme moduna girebilirsiniz. Metinde değişiklik olsa bile seçim aralığın dışına taşındığında bir <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> olay oluşur.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>SelectionChange olayına yanıt vermek için kod ekleme

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>SelectionChange olayına göre namedRange2 içine metin eklemek için

1. Olay **işleyicisini NamedRange1_SelectionChange** şekilde görünen kod ekleyin:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet27":::

    > [!NOTE]
    > Bir aralıkta bir hücreye çift Excel seçimin aralıkta hareket etmesine neden olduğundan, olay oluşmadan önce <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> bir olay oluşur.

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık çalışma kitabınızı test etmek için denetim olaylarını açıklayan metnin olaylar ıldığında başka bir adlandırılmış <xref:Microsoft.Office.Tools.Excel.NamedRange> araca ekli olduğunu doğrularsınız.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. İmlecinizi `namedRange1` içine yerleştirerek olayla ilgili metnin <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> ekli olduğunu ve çalışma sayfasına bir açıklama ekli olduğunu doğrulayın.

3. öğesinin içine `namedRange1` çift tıklayın ve olaylarla ilgili metnin içine <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> kırmızı italik metin ekli olduğunu `namedRange2` doğrulayın.

4. öğesinin dışına tıklayın ve metinde değişiklik yapılmış olsa bile düzenleme modundan çıkılıyorsa değişiklik olayı `namedRange1` oluştuğuna dikkat edin.

5. içindeki metni `namedRange1` değiştirme.

6. öğesinin dışına `namedRange1` tıklayın ve olayla ilgili metnin <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> içine mavi metin ile ekli olduğunu `namedRange2` doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuz, bir denetimin olaylarına karşı programlamanın temellerini <xref:Microsoft.Office.Tools.Excel.NamedRange> gösterir. Bir sonraki görev şu şekilde olabilir:

- Projeyi dağıtma. Daha fazla bilgi için [bkz. Bir Office dağıtma.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş Excel kullanarak nesneleri otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl olur: NamedRange denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-namedrange-controls.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Nasıllı: Projelerde olay Office oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md)
