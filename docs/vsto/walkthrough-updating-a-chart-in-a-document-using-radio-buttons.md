---
title: 'Adım adım kılavuz: Radyo düğmelerini kullanarak belgede bir grafiği güncelleştirme'
description: Kullanıcılara belge üzerinde grafik stilleri seçme seçeneği vermek üzere Microsoft Word düzeyi özelleştirmede radyo düğmelerini nasıl kullanabileceğinizi öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725541"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Adım adım kılavuz: Radyo düğmelerini kullanarak belgede bir grafiği güncelleştirme
  Bu kılavuzda, kullanıcılara belge üzerinde grafik stilleri seçme seçeneği vermek için Microsoft Office Word'e belge düzeyi özelleştirmede radyo düğmelerini nasıl kullanabileceğiniz açıklanır.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Tasarım zamanında belge düzeyi projesinde belgeye grafik ekleme.

- Radyo düğmelerini kullanıcı denetimine ekleyerek gruplama.

- Bir seçenek seçildiğinde grafik stilini değiştirme.

  Sonucu tamamlanmış bir örnek olarak görmek için, geliştirme örnekleri ve izlenecek [yollar Office Word Denetimleri Örneği'ne bakın.](../vsto/office-development-samples-and-walkthroughs.md)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word Belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. Grafiğim Seçenekleri adıyla bir **Word Belgesi projesi oluşturun.** Sihirbazda Yeni belge **oluştur'a tıklayın.** Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio word belgesini tasarımcıda açar ve Grafiğim Seçenekleri projesini **Çözüm Gezgini.** 

## <a name="add-a-chart-to-the-document"></a>Belgeye grafik ekleme

### <a name="to-add-a-chart"></a>Grafik eklemek için

1. Visual Studio tasarımcısında barındırılan Word belgesinde, Şerit'te Ekle **sekmesine** tıklayın.

2. Metin **grubunda** Nesne Ekle açılan **düğmesine ve** ardından Nesne'ye **tıklayın.**

     Nesne **iletişim** kutusu açılır.

3. Yeni Oluştur **sekmesindeki** Nesne türü **listesinde** Microsoft Graph **Grafiği'ne ve** ardından Tamam'a **tıklayın.**

     Ekleme noktasında belgeye bir grafik eklenir ve Bazı varsayılan **verilerle** Birlikte Veri Sayfası penceresi görüntülenir.

4. Grafikte **varsayılan değerleri** kabul etmek için Veri Sayfası penceresini kapatın ve odağı grafikten başka bir yere taşımak için belgenin içine tıklayın.

5. Grafiği sağ tıklatın ve ardından Nesneyi **Biçimlendir'e tıklayın.**

6. Nesneyi Biçimlendir **iletişim** kutusunun Düzen **sekmesinde Kare'yi** seçin ve **Tamam'a** **tıklayın.**

## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi ekleme
 Belge üzerindeki radyo düğmeleri varsayılan olarak birbirini dışlar. Kullanıcı denetimine ekleyerek ve ardından seçimi denetlemeye kod yazarak düzgün çalışmasını sebilirsiniz.

### <a name="to-add-a-user-control"></a>Kullanıcı denetimi eklemek için

1. içinde **Grafiğim Seçenekleri** projesini **Çözüm Gezgini.**

2. Yeni **Project** **Ekle'ye tıklayın.**

3. Yeni Öğe **Ekle iletişim kutusunda** Kullanıcı Denetimi'ne **tıklayın,** **denetime ChartOptions adını ve Ekle'ye** **tıklayın.**

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Kullanıcı Windows Form denetimleri eklemek için

1. Kullanıcı denetimi tasarımcıda görünmüyorsa, grafikte **ChartOptions'a** **çift Çözüm Gezgini.**

2. Araç **Kutusunun Ortak** Denetimler **sekmesinden,** ilk **Radyo Düğmesi** denetimlerini kullanıcı denetimine sürükleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**columnChart**|
    |**Metin**|**Sütun Grafiği**|

3. Kullanıcı **denetimine ikinci** bir Radyo Düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**barChart**|
    |**Metin**|**Çubuk Grafik**|

4. Kullanıcı **denetimine üçüncü bir** Radyo Düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**lineChart**|
    |**Metin**|**Çizgi Grafik**|

5. Kullanıcı **denetimine dördüncü** bir Radyo Düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**areaBlockChart**|
    |**Metin**|**Alan Blok Grafiği**|

## <a name="add-references"></a>Başvuru ekleme
 Bir belgedeki kullanıcı denetiminden chart'a erişmek için projenizin derlemesi için `Microsoft.Office.Interop.Graph` bir başvuruya sahipsiniz.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Microsoft'a başvuru eklemek için. Office. Birlikte çalış -abilir -lik. Graph derlemesi

1. Giriş menüsünde **Project** Ekle'ye **tıklayın.**

     Başvuru **Ekle iletişim** kutusu görüntülenir.

2. **.NET sekmesinde** **Microsoft.Office. Birlikte çalış -abilir -lik. Graph** ve **Tamam'a tıklayın.** Derlemenin 14.0.0.0 sürümünü seçin.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Radyo düğmesi seçildiğinde grafik stilini değiştirme
 Düğmelerin düzgün çalışması için kullanıcı denetiminde bir genel olay oluşturun, seçim türünü ayarlamak için bir özellik ekleyin ve radyo düğmelerinin her biri için bir `CheckedChanged` yordam oluşturun.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Kullanıcı denetiminde olay ve özellik oluşturmak için

1. Bu **Çözüm Gezgini,** kullanıcı denetimine sağ tıklayın ve ardından Kodu **Görüntüle'ye tıklayın.**

2. sınıfına bir olay `SelectionChanged` ve özelliği oluşturmak için kod `Selection` `ChartOptions` ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet9":::

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Radyo düğmelerinin CheckedChange olaylarını işlemek için

1. Radyo düğmesinin olay `CheckedChanged` işleyicisinde grafik `areaBlockChart` türünü ayarlayın ve ardından olayı yükseltin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet10":::

2. Radyo düğmesinin olay `CheckedChanged` işleyicisinde grafik `barChart` türünü ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet11":::

3. Radyo düğmesinin olay `CheckedChanged` işleyicisinde grafik `columnChart` türünü ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet12":::

4. Radyo düğmesinin olay `CheckedChanged` işleyicisinde grafik `lineChart` türünü ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet13":::

5. C# içinde radyo düğmeleri için olay işleyicileri eklemeniz gerekir. Kodu oluşturucuya, `ChartOptions` çağrısının altına `InitializeComponent` ekebilirsiniz. Olay işleyicileri oluşturma hakkında daha fazla bilgi için, [bkz. How to: Create Event Handlers in Office Projelerinde](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet14":::

## <a name="add-the-user-control-to-the-document"></a>Belgeye Kullanıcı denetimi ekleme
 Çözümü derlemek için yeni kullanıcı denetimi Araç Kutusuna otomatik **olarak eklenir.** Ardından denetimi Araç Kutusundan **belgenize** sürükleyebilirsiniz.

### <a name="to-add-the-user-control-your-document"></a>Belgenizi kullanıcı denetimine eklemek için

1. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     **ChartOptions kullanıcı** denetimi Araç Kutusuna **eklenir.**

2. Içinde **Çözüm Gezgini** **ThisDocument.vb veya ThisDocument.cs'ye** sağ **tıklayın** ve ardından Öğesini **Görünüm Tasarımcısı.**

3. Denetimi `ChartOptions` Araç **Kutusundan belgeye** sürükleyin.

     Özellikler **penceresinde,** az önce belgeye ekley istediğiniz denetimi olarak  `ChartOptions1` değiştirin.

## <a name="change-the-chart-type"></a>Grafik türünü değiştirme
 Grafik türünü kullanıcı denetiminde seçilen seçen şekilde değiştirmek için bir olay işleyicisi oluşturun.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Belgede görüntülenen grafiğin türünü değiştirmek için

1. Aşağıdaki olay işleyicisini sınıfına `ThisDocument` ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet15":::

2. C# içinde, kullanıcı denetimi için olay işleyicisi eklemeniz <xref:Microsoft.Office.Tools.Word.Document.Startup> gerekir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet16":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık radyo düğmesini seçerek grafik stilinin doğru güncelleştirilmiş olduğundan emin olmak için belgenizi test edin.

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
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Belgelerde Windows Forms denetimlerinin Office sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
