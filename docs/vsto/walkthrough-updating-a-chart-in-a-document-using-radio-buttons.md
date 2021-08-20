---
title: 'İzlenecek yol: radyo düğmelerini kullanarak bir belgedeki grafiği güncelleştirme'
description: kullanıcılara belgedeki grafik stillerini seçme seçeneğini sunmak için Microsoft Word için belge düzeyi özelleştirmesinde radyo düğmelerini nasıl kullanabileceğinizi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d95ab38581945c61000b3cfcca26ed1ba3fd2c5d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155416"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>İzlenecek yol: radyo düğmelerini kullanarak bir belgedeki grafiği güncelleştirme
  bu izlenecek yol, kullanıcılara belgedeki grafik stillerini seçme seçeneği sunmak üzere Microsoft Office Word için belge düzeyi özelleştirmesinde radyo düğmelerinin nasıl kullanılacağını gösterir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Belge düzeyindeki bir projede belgeye tasarım zamanında bir grafik ekleme.

- Radyo düğmelerini bir kullanıcı denetimine ekleyerek gruplandırma.

- Bir seçenek belirlendiğinde grafik stilini değiştirme.

  sonucu tamamlanmış bir örnek olarak görmek için [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)' da Word denetimleri örneğine bakın.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Grafiğim** adıyla bir Word belgesi projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio yeni Word belgesini tasarımcıda açar ve **grafik seçenekleri** projesini **Çözüm Gezgini** ekler.

## <a name="add-a-chart-to-the-document"></a>Belgeye grafik ekleme

### <a name="to-add-a-chart"></a>Grafik eklemek için

1. Visual Studio tasarımcısında barındırılan Word belgesinde, şeritte **ekle** sekmesine tıklayın.

2. **Metin** grubunda, **nesne Ekle** açılır düğmesine tıklayın ve **nesne**' ye tıklayın.

     **Nesne** iletişim kutusu açılır.

3. **yeni oluştur** sekmesinin **nesne türü** listesinde **grafik Microsoft Graph** seçin ve ardından **tamam**' a tıklayın.

     Ekleme noktasındaki belgeye bir grafik eklenir ve **veri sayfası** penceresi bazı varsayılan verilerle birlikte görüntülenir.

4. Grafikteki varsayılan değerleri kabul etmek için **veri sayfası** penceresini kapatın ve odağı grafikten uzağa taşımak için belgenin içine tıklayın.

5. Grafiğe sağ tıklayın ve sonra **nesne Biçimlendir**' e tıklayın.

6. **Nesne Biçimlendir** Iletişim kutusunun **Düzen** sekmesinde **kare** ' i seçin ve **Tamam**' ı tıklatın.

## <a name="add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi Ekle
 Belgedeki radyo düğmeleri varsayılan olarak birbirini dışlar. Bunları bir kullanıcı denetimine ekleyerek ve sonra seçimi denetlemek için kod yazarak doğru şekilde çalışır hale getirebilirsiniz.

### <a name="to-add-a-user-control"></a>Kullanıcı denetimi eklemek için

1. **Çözüm Gezgini** Içindeki **My Chart Options** projesini seçin.

2. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

3. **Yeni öğe Ekle** Iletişim kutusunda **Kullanıcı denetimi**' ne tıklayın, denetimi **ChartOptions olarak** adlandırın ve **Ekle**' ye tıklayın.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>kullanıcı denetimine Windows Form denetimleri eklemek için

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

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Microsoft 'a bir başvuru eklemek için. Office. Derlemesinde. Graph derlemesi

1. **Project** menüsünde **başvuru ekle**' ye tıklayın.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **.Net** sekmesinde, **Microsoft. Office ' yi seçin. Derlemesinde. Graph** **Tamam**' a tıklayın. Derlemenin 14.0.0.0 sürümünü seçin.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Bir radyo düğmesi seçildiğinde grafik stilini değiştirme
 Düğmelerin doğru çalışmasını sağlamak için Kullanıcı denetiminde genel bir olay oluşturun, seçim türünü ayarlamak için bir özellik ekleyin ve radyo düğmelerinin her birinin olayı için bir yordam oluşturun `CheckedChanged` .

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Kullanıcı denetiminde bir olay ve özellik oluşturmak için

1. **Çözüm Gezgini**, Kullanıcı denetimine sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

2. `SelectionChanged`Sınıfına bir olay ve özellik oluşturmak için kod ekleyin `Selection` `ChartOptions` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet9":::

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Radyo düğmelerinin CheckedChange olayını işlemek için

1. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `areaBlockChart` ve olayı yükseltin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet10":::

2. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `barChart` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet11":::

3. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `columnChart` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet12":::

4. `CheckedChanged`Radyo düğmesinin olay işleyicisinde grafik türünü ayarlayın `lineChart` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet13":::

5. C# dilinde radyo düğmeleri için olay işleyicileri eklemeniz gerekir. `ChartOptions`Öğesine çağrısının altında kodu oluşturucuya ekleyebilirsiniz `InitializeComponent` . olay işleyicileri oluşturma hakkında bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet14":::

## <a name="add-the-user-control-to-the-document"></a>Belgeye Kullanıcı denetimini ekleyin
 Çözümü oluşturduğunuzda, Yeni Kullanıcı denetimi **araç kutusuna** otomatik olarak eklenir. Daha sonra denetimi **araç kutusundan** belgenize sürükleyebilirsiniz.

### <a name="to-add-the-user-control-your-document"></a>Belgenize Kullanıcı denetimi eklemek için

1. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     **ChartOptions** Kullanıcı denetimi **araç kutusuna** eklenir.

2. **Çözüm Gezgini**' de **ThisDocument. vb** veya **ThisDocument. cs**' ye sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

3. `ChartOptions` **Araç kutusundaki** denetimi belgeye sürükleyin.

     **Özellikler** penceresinde, belgeye yeni eklediğiniz denetimi adlandırın `ChartOptions1` .

## <a name="change-the-chart-type"></a>Grafik türünü değiştirme
 Grafik türünü Kullanıcı denetiminde seçilen seçeneğe göre değiştirmek için bir olay işleyicisi oluşturun.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Belgede görüntülenen grafik türünü değiştirmek için

1. Aşağıdaki olay işleyicisini `ThisDocument` sınıfına ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet15":::

2. C# ' de, olaya Kullanıcı denetimi için bir olay işleyicisi eklemeniz gerekir <xref:Microsoft.Office.Tools.Word.Document.Startup> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet16":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık bir radyo düğmesini seçerek grafik stilinin doğru güncelleştirilmiş olduğundan emin olmak için belgenizi test edin.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Çeşitli radyo düğmelerini seçin.

3. Grafik stilinin seçime uygun şekilde değiştiklerini onaylayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bir sonraki görevlerden bazıları:

- Bir metin kutusunu doldurmak için düğme kullanma. Daha fazla bilgi için [bkz. Adım adım: Düğme kullanarak belge içinde metin görüntüleme.](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)

- Birleşik giriş kutusundan bir stil seçerek biçimlendirmeyi değiştirme. Daha fazla bilgi için [bkz. Adım adım: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme.](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Office örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Office Windows Form denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
