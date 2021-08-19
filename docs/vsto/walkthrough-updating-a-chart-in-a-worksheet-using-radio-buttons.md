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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155388"
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
   | **Metin** | **Çubuk grafik** |

4. Kullanıcı denetimine üçüncü bir radyo düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.

   | Özellik | Değer |
   |----------|----------------|
   | **Ad** | **lineChart** |
   | **Metin** | **Çizgi grafik** |

5. Kullanıcı denetimine dördüncü radyo düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.

   |Özellik|Değer|
   |--------------|-----------|
   |**Ad**|**areaBlockChart**|
   |**Metin**|**Alan blok grafiği**|

   Sonra, bir radyo düğmesine tıklandığında Grafiği güncelleştirmek için kodu yazın.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Bir radyo düğmesi seçildiğinde grafik stilini değiştirme
 Artık grafik stilini değiştirmek için kodu ekleyebilirsiniz. Bunu yapmak için Kullanıcı denetiminde ortak bir olay oluşturun, seçim türünü ayarlamak için bir özellik ekleyin ve radyo düğmelerinin her birinin olayı için bir olay işleyicisi oluşturun `CheckedChanged` .

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Kullanıcı denetiminde bir olay ve özellik oluşturmak için

1. **Çözüm Gezgini**, Kullanıcı denetimine sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

2. `ChartOptions`Bir `SelectionChanged` olay ve özellik oluşturmak için sınıfa kod ekleyin `Selection` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet13":::

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Radyo düğmelerinin CheckedChanged olayını işlemek için

1. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `areaBlockChart` ve olayı yükseltin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet14":::

2. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `barChart` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet15":::

3. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `columnChart` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet16":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet16":::

4. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `lineChart` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet17":::

5. C# dilinde radyo düğmeleri için olay işleyicileri eklemeniz gerekir. `ChartOptions`Öğesine çağrısının altında kodu oluşturucuya ekleyebilirsiniz `InitializeComponent` . olay işleyicilerini oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: olay işleyicileri oluşturma Office projelerinde](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet18":::

## <a name="add-the-user-control-to-the-worksheet"></a>Çalışma sayfasına kullanıcı denetimini ekleme
 Çözümü oluşturduğunuzda, Yeni Kullanıcı denetimi **araç kutusuna** otomatik olarak eklenir. Daha sonra denetimi **araç kutusundan** çalışma sayfanıza sürükleyebilirsiniz.

### <a name="to-add-the-user-control-your-worksheet"></a>Çalışma sayfanıza Kullanıcı denetimi eklemek için

1. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     **ChartOptions** Kullanıcı denetimi **araç kutusuna** eklenir.

2. **Çözüm Gezgini**, **Sheet1. vb** veya **Sayfa1. cs**' ye sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

3. **Araç kutusundan** **ChartOptions** denetimini çalışma sayfasına sürükleyin.

     Adlı yeni bir denetim `my_Excel_Chart_ChartOptions1` projenize eklenir.

4. Denetimin adını **ChartOptions1** olarak değiştirin.

## <a name="change-the-chart-type"></a>Grafik türünü değiştirme
 Grafik türünü değiştirmek için, Kullanıcı denetiminde seçilen seçeneğe göre stili ayarlayan bir olay işleyicisi oluşturun.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Çalışma sayfasında görüntülenen grafik türünü değiştirmek için

1. Aşağıdaki olay işleyicisini `Sheet1` sınıfına ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet19":::

2. C# ' ta, aşağıda gösterildiği gibi, olaya Kullanıcı denetimi için bir olay işleyicisi eklemeniz gerekir <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> . olay işleyicilerini oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: olay işleyicileri oluşturma Office projelerinde](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet20":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Bir radyo düğmesini seçtiğinizde grafiğin doğru şekilde stillendirilmiş olduğunu doğrulamak için artık çalışma kitabınızı test edebilirsiniz.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Çeşitli radyo düğmeleri seçin.

3. Grafik stilinin seçimle eşleşecek şekilde değişiklik olduğunu onaylayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuzda, çalışma sayfalarında radyo düğmelerinin ve grafik stillerinin kullanımıyla ilgili temel bilgiler gösterilmektedir. Daha sonra gelebilecek bazı görevler şunlardır:

- Projeyi dağıtma. daha fazla bilgi için bkz. [Office çözüm dağıtma](../vsto/deploying-an-office-solution.md).

- Bir metin kutusunu doldurmak için düğme kullanma. Daha fazla bilgi için bkz. [Izlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin kutusu görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Onay kutularını kullanarak çalışma sayfasındaki biçimlendirmeyi değiştirme. Daha fazla bilgi için bkz. [Izlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
