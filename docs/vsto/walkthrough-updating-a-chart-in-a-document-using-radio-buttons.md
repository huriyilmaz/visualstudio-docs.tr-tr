---
title: 'İzlenecek yol: radyo düğmelerini kullanarak bir belgedeki grafiği güncelleştirme'
description: Kullanıcılara belgedeki grafik stillerini seçme seçeneği sunmak üzere Microsoft Word için belge düzeyi özelleştirmesinde radyo düğmelerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0db8cd113983231ee45252fec8fb47e3a7b75b7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937335"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>İzlenecek yol: radyo düğmelerini kullanarak bir belgedeki grafiği güncelleştirme
  Bu izlenecek yol, kullanıcılara belgedeki grafik stillerini seçme seçeneği sunmak üzere Microsoft Office Word için belge düzeyi özelleştirmesinde radyo düğmelerinin nasıl kullanılacağını gösterir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Belge düzeyindeki bir projede belgeye tasarım zamanında bir grafik ekleme.

- Radyo düğmelerini bir kullanıcı denetimine ekleyerek gruplandırma.

- Bir seçenek belirlendiğinde grafik stilini değiştirme.

  Sonucu tamamlanmış bir örnek olarak görmek için bkz. [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)Içindeki Word denetimleri örneği.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Grafiğim** adıyla bir Word belgesi projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Word belgesini açar ve **Çözüm Gezgini** Için **My Chart Options** projesini ekler.

## <a name="add-a-chart-to-the-document"></a>Belgeye grafik ekleme

### <a name="to-add-a-chart"></a>Grafik eklemek için

1. Visual Studio tasarımcısında barındırılan Word belgesinde, şeritte **Ekle** sekmesine tıklayın.

2. **Metin** grubunda, **nesne Ekle** açılır düğmesine tıklayın ve **nesne**' ye tıklayın.

     **Nesne** iletişim kutusu açılır.

3. **Yeni oluştur** sekmesinin **nesne türü** listesinde **grafik Microsoft Graph** seçin ve ardından **Tamam**' a tıklayın.

     Ekleme noktasındaki belgeye bir grafik eklenir ve **veri sayfası** penceresi bazı varsayılan verilerle birlikte görüntülenir.

4. Grafikteki varsayılan değerleri kabul etmek için **veri sayfası** penceresini kapatın ve odağı grafikten uzağa taşımak için belgenin içine tıklayın.

5. Grafiğe sağ tıklayın ve sonra **nesne Biçimlendir**' e tıklayın.

6. **Nesne Biçimlendir** Iletişim kutusunun **Düzen** sekmesinde **kare** ' i seçin ve **Tamam**' ı tıklatın.

## <a name="add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi Ekle
 Belgedeki radyo düğmeleri varsayılan olarak birbirini dışlar. Bunları bir kullanıcı denetimine ekleyerek ve sonra seçimi denetlemek için kod yazarak doğru şekilde çalışır hale getirebilirsiniz.

### <a name="to-add-a-user-control"></a>Kullanıcı denetimi eklemek için

1. **Çözüm Gezgini** Içindeki **My Chart Options** projesini seçin.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** Iletişim kutusunda **Kullanıcı denetimi**' ne tıklayın, denetimi **ChartOptions olarak** adlandırın ve **Ekle**' ye tıklayın.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Kullanıcı denetimine Windows form denetimleri eklemek için

1. Kullanıcı denetimi tasarımcıda görünmüyorsa, **Çözüm Gezgini**' de **ChartOptions** ' a çift tıklayın.

2. **Araç kutusunun** **ortak denetimler** sekmesinden, ilk **radyo düğmesi** denetimini Kullanıcı denetimine sürükleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**columnChart**|
    |**Metin**|**Sütun grafiği**|

3. Kullanıcı denetimine ikinci bir **radyo düğmesi** ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**barChart**|
    |**Metin**|**Çubuk grafik**|

4. Kullanıcı denetimine üçüncü bir **radyo düğmesi** ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**lineChart**|
    |**Metin**|**Çizgi grafik**|

5. Kullanıcı denetimine dördüncü **radyo düğmesi** ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**areaBlockChart**|
    |**Metin**|**Alan blok grafiği**|

## <a name="add-references"></a>Başvuru Ekle
 Bir belgedeki Kullanıcı denetiminden grafiğe erişmek için, projenizdeki derlemeye bir başvurunuz olması gerekir `Microsoft.Office.Interop.Graph` .

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Microsoft. Office. Interop. Graph derlemesine bir başvuru eklemek için

1. **Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **.Net** sekmesinde, **Microsoft. Office. Interop. Graph** ' i seçin ve **Tamam**' a tıklayın. Derlemenin 14.0.0.0 sürümünü seçin.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Bir radyo düğmesi seçildiğinde grafik stilini değiştirme
 Düğmelerin doğru çalışmasını sağlamak için Kullanıcı denetiminde genel bir olay oluşturun, seçim türünü ayarlamak için bir özellik ekleyin ve radyo düğmelerinin her birinin olayı için bir yordam oluşturun `CheckedChanged` .

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Kullanıcı denetiminde bir olay ve özellik oluşturmak için

1. **Çözüm Gezgini**, Kullanıcı denetimine sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

2. `SelectionChanged`Sınıfına bir olay ve özellik oluşturmak için kod ekleyin `Selection` `ChartOptions` .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Radyo düğmelerinin CheckedChange olayını işlemek için

1. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `areaBlockChart` ve olayı yükseltin.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]

2. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `barChart` .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]

3. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `columnChart` .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]

4. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `lineChart` .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]

5. C# dilinde radyo düğmeleri için olay işleyicileri eklemeniz gerekir. `ChartOptions`Öğesine çağrısının altında kodu oluşturucuya ekleyebilirsiniz `InitializeComponent` . Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]

## <a name="add-the-user-control-to-the-document"></a>Belgeye Kullanıcı denetimini ekleyin
 Çözümü oluşturduğunuzda, Yeni Kullanıcı denetimi **araç kutusuna** otomatik olarak eklenir. Daha sonra denetimi **araç kutusundan** belgenize sürükleyebilirsiniz.

### <a name="to-add-the-user-control-your-document"></a>Belgenize Kullanıcı denetimi eklemek için

1. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     **ChartOptions** Kullanıcı denetimi **araç kutusuna** eklenir.

2. **Çözüm Gezgini**, **ThisDocument. vb** veya **ThisDocument.cs** öğesine sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

3. `ChartOptions` **Araç kutusundaki** denetimi belgeye sürükleyin.

     **Özellikler** penceresinde, belgeye yeni eklediğiniz denetimi adlandırın `ChartOptions1` .

## <a name="change-the-chart-type"></a>Grafik türünü değiştirme
 Grafik türünü Kullanıcı denetiminde seçilen seçeneğe göre değiştirmek için bir olay işleyicisi oluşturun.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Belgede görüntülenen grafik türünü değiştirmek için

1. Aşağıdaki olay işleyicisini `ThisDocument` sınıfına ekleyin.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]

2. C# ' de, olaya Kullanıcı denetimi için bir olay işleyicisi eklemeniz gerekir <xref:Microsoft.Office.Tools.Word.Document.Startup> .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık bir radyo düğmesini seçtiğinizde grafik stilinin doğru şekilde güncelleştirildiğinden emin olmak için belgenizi test edebilirsiniz.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Çeşitli radyo düğmeleri seçin.

3. Grafik stilinin seçimle eşleşecek şekilde değişiklik olduğunu onaylayın.

## <a name="next-steps"></a>Sonraki adımlar
 Daha sonra gelebilecek bazı görevler şunlardır:

- Bir metin kutusunu doldurmak için düğme kullanma. Daha fazla bilgi için bkz. [Izlenecek yol: bir düğme kullanarak bir belgedeki metin kutusunda metni görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Birleşik giriş kutusundan bir stil seçerek biçimlendirmeyi değiştirin. Daha fazla bilgi için bkz. [Izlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
