---
title: Radyo düğmelerini kullanarak çalışma sayfasındaki grafiği güncelleştirme
description: kullanıcılara seçenekler arasında hızlı bir şekilde geçiş yapmak için bir yol sağlamak üzere Microsoft Excel çalışma sayfasında radyo düğmelerinin kullanımıyla ilgili temel bilgileri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4edf0813fcbcd9b7013b85bcf251da9a47beb78a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725531"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>İzlenecek Yol: Radyo Düğmelerini Kullanarak Çalışma Sayfasında Grafik Güncelleme
  bu izlenecek yol, kullanıcıya seçenekler arasında hızlı bir şekilde geçiş yapmak için bir yol sağlamak üzere Microsoft Office Excel çalışma sayfasındaki radyo düğmelerinin kullanımıyla ilgili temel bilgileri gösterir. Bu durumda, Seçenekler grafiğin stilini değiştirir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 sonucu tamamlanmış bir örnek olarak görmek için, [Office geliştirme örneklerinde ve izlenecek yollarda](../vsto/office-development-samples-and-walkthroughs.md)Excel denetimleri örneğine bakın.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir çalışma sayfasına radyo düğmeleri grubu ekleme.

- Bir seçenek belirlendiğinde grafik stilini değiştirme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="add-a-chart-to-a-worksheet"></a>Çalışma sayfasına grafik ekleme
 var olan bir çalışma kitabını özelleştiren Excel bir çalışma kitabı projesi oluşturabilirsiniz. bu kılavuzda, bir çalışma kitabına bir grafik ekleyecek ve ardından bu çalışma kitabını yeni bir Excel çözümünde kullanacaksınız. Bu izlenecek yolda veri kaynağı, **grafik Için veri** adlı bir çalışma sayfasıdır.

### <a name="to-add-the-data"></a>Verileri eklemek için

1. Microsoft Excel’i açın.

2. **Sheet3** sekmesine sağ tıklayın ve sonra kısayol menüsünde **Yeniden Adlandır** ' a tıklayın.

3. **Grafik için sayfayı veri** olarak yeniden adlandırın.

4. Aşağıdaki verileri, A4 hücresi sol üst köşesinden ve sağ alt köşedeki E8 **grafik Için verilere** ekleyin.

   |Bölge/çeyrek|Ç1|Ç2|Ç3|Ç4|
   |-|--------|--------|--------|--------|
   |Batı|500|550|550|600|
   |Doğu|600|625|675|700|
   |Kuzey|450|470|490|510|
   |Güney|800|750|775|790|

   Sonra, verileri göstermek için ilk çalışma sayfasına bir grafik ekleyin.

### <a name="to-add-a-chart-in-excel"></a>Excel bir grafik eklemek için

1. **Ekle** sekmesinde, **grafikler** grubunda, **sütun**' a ve ardından **Tüm grafik türleri**' ne tıklayın.

2. **Grafik Ekle** Iletişim kutusunda **Tamam**' a tıklayın.

3. **Tasarım** sekmesinde, **veri** grubunda, **veri Seç**' e tıklayın.

4. **Veri kaynağı seç** iletişim kutusunda, **ChartData Range** kutusuna tıklayın ve varsayılan seçimi kaldırın.

5. **Grafik verileri** sayfasında, sol üst köşede yer alan ve sağ alt köşedeki E8 için a4 içeren hücre bloğunu seçin.

6. **Veri kaynağı seç** Iletişim kutusunda **Tamam**' a tıklayın.

7. Sağ üst köşedeki **E2** hücresi ile hizalanacak şekilde grafiği yeniden konumlandırın.

8. Dosyanızı C sürücüsüne kaydedin ve **ExcelChart.xlsx** adlandırın.

9. Çıkış Excel.

## <a name="create-a-new-project"></a>Yeni proje oluşturma
 bu adımda, **excelchart** çalışma kitabını temel alan bir Excel çalışma kitabı projesi oluşturacaksınız.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Excel grafiğim** adına sahip bir Excel çalışma kitabı projesi oluşturun. Sihirbazda, **var olan bir belgeyi Kopyala**' yı seçin.

     daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Gözden geçirme düğmesine tıklayın** ve bu kılavuzda daha önce oluşturduğunuz çalışma kitabına gidin.

3. **Tamam**'a tıklayın.

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **Excel grafik** projesini **Çözüm Gezgini** ekler.

## <a name="set-properties-of-the-chart"></a>Grafiğin özelliklerini ayarla
 var olan bir çalışma kitabını kullanan yeni bir Excel çalışma kitabı projesi oluşturduğunuzda, konak denetimleri, çalışma kitabındaki tüm adlandırılmış aralıklar, liste nesneleri ve grafikler için otomatik olarak oluşturulur. <xref:Microsoft.Office.Tools.Excel.Chart>Denetimin adını **Özellikler** penceresini kullanarak değiştirebilirsiniz.

### <a name="to-change-the-name-of-the-chart-control"></a>Grafik denetiminin adını değiştirmek için

1. <xref:Microsoft.Office.Tools.Excel.Chart>Tasarımcıda denetimi seçin ve **Özellikler** penceresinde aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Veri grafiği**|
    |**HasLegend**|**yanlýþ**|

## <a name="add-controls"></a>Denetim Ekle
 Bu çalışma sayfası, kullanıcılara grafik stilini hızlı bir şekilde değiştirmek için bir yol sağlamak üzere radyo düğmelerini kullanır. Ancak radyo düğmelerinin dışlamalı olması gerekir — tek bir düğme seçildiğinde, grupta başka hiçbir düğme de aynı anda seçilebilir. Bu davranış, çalışma sayfasına çeşitli radyo düğmeleri eklediğinizde varsayılan olarak gerçekleşmez.

 Bu davranışı eklemenin bir yolu, bir kullanıcı denetimindeki radyo düğmelerini gruplamak, kodunuzu kullanıcı denetiminin arkasına yazmak ve sonra Kullanıcı denetimini çalışma sayfasına eklemektir.

### <a name="to-add-a-user-control"></a>Kullanıcı denetimi eklemek için

1. **Çözüm Gezgini** **Excel grafik projem** ' i seçin.

2. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

3. **Yeni öğe Ekle** Iletişim kutusunda **Kullanıcı denetimi**' ne tıklayın, denetimi **ChartOptions olarak** adlandırın ve **Ekle**' ye tıklayın.

### <a name="to-add-radio-buttons-to-the-user-control"></a>Kullanıcı denetimine radyo düğmeleri eklemek için

1. Kullanıcı denetimi tasarımcıda görünmüyorsa, **Çözüm Gezgini**' de **ChartOptions** ' a çift tıklayın.

2. **Araç kutusunun** **ortak denetimler** sekmesinden, bir **radyo düğmesi** denetimini Kullanıcı denetimine sürükleyin ve aşağıdaki özellikleri değiştirin.

   | Özellik | Değer |
   |----------|------------------|
   | **Ad** | **columnChart** |
   | **Metin** | **Sütun grafiği** |

3. Kullanıcı denetimine ikinci bir radyo düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.

   | Özellik | Değer |
   |----------|---------------|
   | **Ad** | **barChart** |
   | **Metin** | **Çubuk Grafik** |

4. Kullanıcı denetimine üçüncü bir radyo düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.

   | Özellik | Değer |
   |----------|----------------|
   | **Ad** | **lineChart** |
   | **Metin** | **Çizgi Grafik** |

5. Kullanıcı denetimine dördüncü bir radyo düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.

   |Özellik|Değer|
   |--------------|-----------|
   |**Ad**|**areaBlockChart**|
   |**Metin**|**Alan Blok Grafiği**|

   Ardından, radyo düğmesine tıkıldığında grafiği güncelleştirmek için kodu yazın.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Radyo düğmesi seçildiğinde grafik stilini değiştirme
 Artık grafik stilini değiştirmek için kodu ekleyebilirsiniz. Bunu yapmak için, kullanıcı denetiminde genel bir olay oluşturun, seçim türünü ayarlamak için bir özellik ekleyin ve radyo düğmelerinin her biri için bir olay `CheckedChanged` işleyicisi oluşturun.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Kullanıcı denetiminde olay ve özellik oluşturmak için

1. Bu **Çözüm Gezgini,** kullanıcı denetimine sağ tıklayın ve ardından Kodu **Görüntüle'ye tıklayın.**

2. Bir olay ve `ChartOptions` özelliği oluşturmak için `SelectionChanged` sınıfına kod `Selection` ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet13":::

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Radyo düğmelerinin CheckedChanged olaylarını işlemek için

1. Radyo düğmesinin olay `CheckedChanged` işleyicisinde grafik `areaBlockChart` türünü ayarlayın ve ardından olayı yükseltin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet14":::

2. Radyo düğmesinin olay `CheckedChanged` işleyicisinde grafik `barChart` türünü ayarlayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet15":::

3. Radyo düğmesinin olay `CheckedChanged` işleyicisinde grafik `columnChart` türünü ayarlayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet16":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet16":::

4. Radyo düğmesinin olay `CheckedChanged` işleyicisinde grafik `lineChart` türünü ayarlayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet17":::

5. C# içinde radyo düğmeleri için olay işleyicileri eklemeniz gerekir. Kodu oluşturucuya, `ChartOptions` çağrısının altına `InitializeComponent` ekebilirsiniz. Olay işleyicilerinin nasıl oluşturulacakları hakkında bilgi için [bkz. Nasıl 2014' Office projelerinde olay işleyicileri oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet18":::

## <a name="add-the-user-control-to-the-worksheet"></a>Çalışma sayfasına kullanıcı denetimi ekleme
 Çözümü derlemek için yeni kullanıcı denetimi Araç Kutusuna otomatik **olarak eklenir.** Ardından denetimi Araç Kutusundan çalışma **sayfanıza** sürükleyebilirsiniz.

### <a name="to-add-the-user-control-your-worksheet"></a>Kullanıcı denetimi eklemek için çalışma sayfanız

1. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     **ChartOptions kullanıcı** denetimi Araç Kutusuna **eklenir.**

2. Bu **Çözüm Gezgini,** Sayfa1.vb veya **Sheet1.cs'ye** sağ tıklayın ve sonra Datele'ye **Görünüm Tasarımcısı.** 

3. **ChartOptions denetimi** araç **kutusundan çalışma** sayfasına sürükleyin.

     Projenize adlı `my_Excel_Chart_ChartOptions1` yeni bir denetim eklenir.

4. Denetimin adını **ChartOptions1 olarak değiştirir.**

## <a name="change-the-chart-type"></a>Grafik türünü değiştirme
 Grafik türünü değiştirmek için, stili kullanıcı denetiminde seçilen seçen bir olay işleyicisi oluşturun.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Çalışma sayfasında görüntülenen grafiğin türünü değiştirmek için

1. Aşağıdaki olay işleyicisini sınıfına `Sheet1` ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet19":::

2. C# içinde, aşağıda gösterildiği gibi kullanıcı denetimi için olay işleyicisi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> eklemeniz gerekir. Olay işleyicilerinin nasıl oluşturulacakları hakkında bilgi için [bkz. Nasıl 2014' Office projelerinde olay işleyicileri oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet20":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık bir radyo düğmesini seçerek grafiğin düzgün stile sahip olduğunu doğrulamak için çalışma kitabınızı test edin.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Çeşitli radyo düğmelerini seçin.

3. Grafik stilinin seçime uygun şekilde değiştiklerini onaylayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuz, çalışma sayfalarında radyo düğmelerini ve grafik stillerini kullanmanın temellerini gösterir. Bir sonraki görevlerden bazıları:

- Projeyi dağıtma. Daha fazla bilgi için [bkz. Bir Office dağıtma.](../vsto/deploying-an-office-solution.md)

- Bir metin kutusunu doldurmak için düğme kullanma. Daha fazla bilgi için [bkz. Adım adım: Düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme.](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)

- Onay kutularını kullanarak çalışma sayfasındaki biçimlendirmeyi değiştirme. Daha fazla bilgi için [bkz. Kılavuz: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme.](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
