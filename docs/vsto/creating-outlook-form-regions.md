---
title: Form Outlook bölgeleri oluşturma
description: Form bölgelerini tasarlamayı, geliştirmeyi ve hata ayıklamayı kolaylaştırmak Outlook Microsoft formlarını özelleştirmek için form bölgelerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 31c843d1d8a0a8a1ee06cbde33d9f229d0954d0914deb1dde912f50d2dbebfd3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226277"
---
# <a name="create-outlook-form-regions"></a>Form Outlook bölgeleri oluşturma
  Form bölgelerini kullanarak form formlarını Microsoft Office Outlook kullanabilirsiniz. Visual Studio form bölgelerini tasarlamayı, geliştirmeyi ve hata ayıklamayı kolaylaştıran gelişmiş araçlar sağlar.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:

- [Form bölgelerini kullanmanın avantajları](#Enhance)

- [Projenize Outlook form bölgesi ekleme](#Adding)

- [Form bölgesi tasarımcısını kullanma](#UsingFormRegionDesigner)

- [Form bölgesinde tasarlanmış bir form Outlook](#UsingFormRegionDesignedOutlook)

- [Form bölgesi için özel kod ekleme](#AddingCustomCode)

- [Projeyi derleme](#Building)

- [Form bölgesinde hata ayıklama](#Debugging)

- [Form bölgesi dağıtma](#Deploying)

## <a name="advantages-of-using-form-regions"></a><a name="Enhance"></a> Form bölgelerini kullanmanın avantajları
 Form bölgeleri, form geliştirmesi için geleneksel Outlook geliştirmeler sağlar:

- Herhangi bir standart formun varsayılan sayfasını özelleştirin.

- Herhangi bir standart forma en fazla 12 sayfa daha ekleyin.

- Herhangi bir standart formu değiştirin veya geliştirin.

- Okuma Bölmesinde ve Denetçiler'de özel kullanıcı arabirimini görüntüleyin.

  Daha fazla bilgi için [bkz. Form sayfalarını ve form bölgelerini özelleştirme.](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions)

## <a name="add-an-outlook-form-region-to-your-project"></a><a name="Adding"></a>Projenize Outlook form bölgesi ekleme
 Yeni bir form **bölgesi tasarlamak Outlook form bölgesi** tasarlamak veya yeni form bölgesinde tasarlanmış bir form bölgesi içeri aktarmak için Yeni Form Bölgesi sihirbazını Outlook. Ayrıca, Başka bir Eklenti projesinde kullanılan bir form Outlook VSTO, mevcut form bölgenizi yeniden kullanabilirsiniz.

### <a name="create-a-new-form-region-by-using-the-wizard"></a><a name="CreatingFormRegion"></a> Sihirbazı kullanarak yeni bir form bölgesi oluşturma
 Form bölgesi oluşturmak için bir Outlook **Form Bölgesi öğesini** bir Outlook VSTO projesine ekleyin. Bu, **Yeni Outlook Form Bölgesi sihirbazını** başlatır.

 Yeni bir form bölgesi tasarlamak mı yoksa yeni bir form bölgesinde tasarlanmış bir form bölgesi içeri aktarmayı mı Outlook. Yeni bir form bölgesi tasarlama hakkında daha fazla bilgi için [bkz. Form bölgesi tasarımcısını kullanma.](#UsingFormRegionDesigner) Veri kaynağında tasarlanmış bir form bölgesi kullanma hakkında daha fazla Outlook için [bkz.](#UsingFormRegionDesignedOutlook)Outlook.

 Oluşturmak istediğiniz form bölgesi türünü belirtmek için sihirbazı kullanın. Aşağıdaki tabloda her form bölgesi türü açıklandı.

|Bölge türü|Açıklama|
|-----------------|-----------------|
|Ayrı|Form bölgelerini yeni bir sayfa olarak yeni bir Outlook ekler.|
|Bitişik|Form bölgelerini bir form formunun Outlook altına ekler.|
|Değiştirme|Form bölgesi, form formunun varsayılan sayfasının yerine yeni bir sayfa Outlook ekler.|
|Hepsini değiştir|Form formunun Outlook form bölgesiyle değiştirir.|

 Sihirbazı, görüntüleme koşullarını belirtmek ve genişletilen form türünü seçmek için de kullanabilirsiniz. Daha fazla bilgi [için, bkz. How to: Add-in Outlook form bölgesi ekleme.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

 Sihirbazda yapılan seçimler, diğer sihirbaz sayfalarında kullanılabilen seçenekleri etkiler. Örneğin, Yeni Outlook  **Form** Bölgesi  Oluştur sayfasında Ekleme veya Ayırma'yi seçerse,  Açıklayıcı  metin girin ve görüntüleme tercihleri sayfanızı seçin sayfasında Başlık ve Açıklama alanları **kullanılamaz.** Bunun nedeni Outlook veya ayrı bir form bölgesi görüntülerken bu alanları kullanmamadır.

#### <a name="form-region-files"></a>Form bölgesi dosyaları
 Yeni Form Bölgesi **sihirbazını Outlook,** Visual Studio otomatik olarak aşağıdaki dosyaları projenize ekler:

- Form bölgesi kod dosyası. Bu dosya, Yeni Öğe Ekle iletişim kutusunda **Outlook Form** Bölgesi öğesi için **belirttiğiniz adı** içerir. Bu dosyaya form bölgesi olaylarını işlemek için kod ekleyin.

- Form bölgesi tasarımcısı kod dosyası. Bu dosya form bölgesi tasarımcısı tarafından oluşturulan kodu içerir ve doğrudan düzenlenemez.

- Bir Outlook Form Depolama (*.ofs*) dosyası.

    > [!NOTE]
    > Bu dosya yalnızca projesinde tasarlanmış bir form bölgesini içeri aktarıyorsanız projeye Outlook.

#### <a name="form-region-factory-class"></a>Form bölgesi fabrika sınıfı
 Form bölgesi kod dosyası arabirimi uygulayan kısmi bir sınıf <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> içerir. Bu, form bölgesi fabrika sınıfıdır. Form bölgesi fabrika sınıfı, form bölgesi için yeni örnekler oluşturmakla sorumludur.

 Form Bölgesi Fabrikası bölgesini genişleterek **bu sınıfı** bulabilirsiniz.

 Yeni **Outlook Form** Bölgesi sihirbazı, form bölgesi iç adını ve form bölgelerini görüntüleyen ileti sınıflarını belirten öznitelikleri bu sınıfa ekler. Dosya projeye eklendikten sonra bu öznitelikleri el ile değiştirebilirsiniz.

 Form bölgesi fabrika sınıfının çoğu form bölgesi tasarımcı dosyasında uygulanır. Ancak, `FormRegionInitializing` olay işleyicisi form bölgesi kod dosyasında ortaya çıkar. Bu olay işleyicisini, form Outlook görüntü Outlook belirtmek için kullanabilirsiniz. Daha fazla bilgi için [bkz. Form bölgesi olaylarını işleme.](#HandlingFormRegionEvents)

### <a name="add-an-existing-form-region-to-your-project"></a><a name="AddingExistingFormRegion"></a> Projenize mevcut bir form bölgesi ekleme
 Başka bir Outlook projesinde kullanılan bir Outlook form bölgeniz varsa, Mevcut Öğeyi Ekle iletişim kutusunu kullanarak Outlook VSTO Eklenti  projesinde yeniden kullanabilirsiniz.

 Var olan form bölgesinde bir kod dosyası (*.vb veya* *.cs) olması* gerekir; Var Olan Outlook Ekle Depolama kullanarak Form Depolama (*.ofs*) **dosyaları ek** olamaz. Ancak, bir form form dosyası içeri aktararak yeni bir form Outlook Depolama oluşturabilirsiniz. Daha fazla bilgi [için, bkz. How to: Add-in Outlook form bölgesi ekleme.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

## <a name="use-the-form-region-designer"></a><a name="UsingFormRegionDesigner"></a> Form bölgesi tasarımcısını kullanma
 Form bölgesi tasarımcısı, bir form bölgesi düzenini ve görünümünü tasarlamanıza yardımcı olur. Yönetilen denetimleri tasarımcının yüzeyine sürükleyip denetimlere çift tıklar, olay işleyicilerini açabilir ve Özellikler penceresinde özellikleri **ayarlayabilirsiniz.**

> [!NOTE]
> Özellikler penceresinde bildirim düğümünün altında form bölgesi Outlook **etkileyen** özellikler **bulabilirsiniz.**

 Form bölgesi tasarımcısı yalnızca Yeni  Form Bölgesi sihirbazının **Form** Bölgesi oluşturma form bölgesi oluşturma sayfasında Yeni Form Bölgesi **Tasarla'Outlook kullanılabilir.**

 Form bölgesi tasarımcısını açmanın üç yolu vardır:

- Bu **Çözüm Gezgini** form bölgesi kod dosyasına çift tıklayın.

- Bu **Çözüm Gezgini** form bölgesi kod dosyasına sağ tıklayın ve sonra Datele'ye **Görünüm Tasarımcısı.**

- Bu **Çözüm Gezgini** form bölgesi kod dosyasını seçin ve ardından  Görünüm menüsünde Tasarımcı'ya **tıklayın.**

  Form bölgesi tasarımcısı yalnızca yönetilen denetimleri destekler. Yerel denetimler Outlook ekamazsiniz.

## <a name="import-a-form-region-designed-in-outlook"></a><a name="UsingFormRegionDesignedOutlook"></a>Outlook'de tasarlanmış bir form bölgelerini içeri Outlook
 Tasarımını form Outlook, form Outlook yerel denetimler eklersiniz. Yerel Outlook denetimler, tasarım zamanında Outlook verilere bağlamaya olanak sağlar. Ancak, daha sonra yönetilen denetimler eklemek veya form bölgesi tasarımını değiştirmek için form bölgesi tasarımcısını kullanamazsiniz.

 Yeni Form Bölgesi sihirbazını kullanarak form Outlook VSTO eklenti **projesine Outlook aktarabilirsiniz.** Form **bölgelerini nasıl oluşturmak istediğinize** bakın sayfasında Bir form formu Outlook **(.ofs) Depolama'yi seçin.** Daha sonra bir Outlook Form dosyası (*.ofs*) Depolama konuma göz atabilirsiniz. (Outlook bölgeleri *.ofs dosyaları olarak kaydeder.)*

 Yeni **Outlook Form** Bölgesi *sihirbazı. ofs* dosyasını proje dizinine kopyalar ve form bölgesi tasarımcı dosyasına denetim başvuruları ekler. Ardından form bölgesi kod dosyasında denetim olaylarını işebilirsiniz.

 Bir Visual Basic projesinde olayları işlemek için Kod Düzenleyicisi'nin en üstünde yer alan yöntem adı listesinden bir olay seçin.

 Bir C# projesinde olayları işlemek için yönteminde olayları denetlemeye abone <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> olun. Daha fazla bilgi için bkz. C&#35; programlama kılavuzu &#40;ve [olaylara abone&#41;. ](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events)

 Form bölgesi fabrika sınıfının `InitializeManifest` yönteminde form bölgesi özelliklerini değiştirebilirsiniz.

> [!NOTE]
> Bir form bölgesini içeri aktaracaksanız, geliştirme bilgisayarına yüklemiş Outlook sürümünü hedef alan bir projede çalışıyor olun. Örneğin, Outlook 2010 yüklüyse, form bölgesi içeri aktarma işlemi yalnızca **Outlook 2010 Eklenti** proje şablonu kullanılarak oluşturulmuş bir projede çalışır.

### <a name="update-an-imported-form-regions-design"></a>İçe aktarılan form bölgesi tasarımını güncelleştirme
 Form bölgesindeki denetimleri ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Bunu yapmadan önce, form bölgesi kod dosyasına eklediğiniz kodu yedekleyin. ardından Outlook *. ofs* dosyasını açın, form bölgesini değiştirin ve değişiklikleri kaydedin. değiştirilen *. ofs* dosyasını içeri aktarmak için **yeni Outlook Form bölgesi** sihirbazı 'nı kullanın. Kodunuzu daha sonra yeni form bölgesi kod dosyasına yapıştırabilirsiniz.

## <a name="add-custom-code-to-a-form-region"></a><a name="AddingCustomCode"></a> Form bölgesine özel kod ekleme
 <xref:Microsoft.Office.Tools.Outlook>ad alanı, form bölgesini, form bölgesini görüntüleyen Outlook öğeyi ve diğer yararlı öğeleri temsil eden sınıflara erişmenizi sağlar. **Outlook form bölgesi** öğesi, projedeki bu derlemeye otomatik olarak bir başvuru ekler ve Form bölgesi kod dosyasının en üstüne uygun **using** veya **ımports** ifadesini ekler.

 `Microsoft.Office.Interop.Outlook`Outlook programlama görevlerinin çoğunu gerçekleştirmek için ad alanındaki sınıfları, yöntemleri ve özellikleri kullanabilirsiniz. Outlook nesne modeli hakkında daha fazla bilgi için bkz. [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md). Outlook nesne modelini kullanan tipik görev örnekleri için bkz. [Outlook çözümleri](../vsto/outlook-solutions.md).

### <a name="handle-form-region-events"></a><a name="HandlingFormRegionEvents"></a> Form bölgesi olaylarını işle
 **Outlook form bölgesi** öğesi, aşağıdaki üç olay işleyicisini Form bölgesi kod dosyasına otomatik olarak ekler.

|Olay|Açıklama|
|-----------|-----------------|
|Formregionbaşlatılıyor|Form bölgesi başlatılmadan önce oluşur. bu olay işleyicisindeki koşulları, Outlook form bölgesinin görüntülenip görüntülenmeyeceğini anlamak için denetleyebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: Outlook bir form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|
|Bir Formregiongösteriliyor|Form bölgesinin bir örneği oluşturulduktan sonra, ancak form bölgesi görüntülenmeden önce oluşur.|
|FormRegionClosed|Form bölgesi kapatılmadan önce gerçekleşir.|

## <a name="build-the-project"></a><a name="Building"></a> Projeyi derleme
 form bölgesi içeren bir Outlook VSTO eklenti projesi oluşturduğunuzda Visual Studio aşağıdaki bilgileri kayıt defterine ekler:

- Bir veya daha fazla form bölgesi ile ilişkili her ileti sınıfı için bir anahtar.

- her form bölgesi için bir giriş ve Outlook VSTO eklentisinin adını temsil eden ilişkili bir değer.

  Outlook, form bölgelerini yüklemek için bu bilgileri kullanır.

## <a name="debug-a-form-region"></a><a name="Debugging"></a> Form bölgesinde hata ayıklama
 bir form bölgesini içeren Outlook VSTO eklentisinin hatalarını ayıkladığınızda, tıpkı diğer projelerde hata ayıklaması yapabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]hata ayıklayıcıyı başlattığınızda, Outlook Visual Studio otomatik olarak başlatılır.

 form bölgesini görüntülemek için uygun Outlook öğesini açmanız gerekir. Örneğin, bir bitişik form bölgesi bir posta öğesinin altına eklendiğinde, bir posta öğesi açın.

## <a name="deploy-a-form-region"></a><a name="Deploying"></a> Form bölgesi dağıtma
 Form bölgeleri, ilişkili Outlook VSTO eklentisi ile otomatik olarak dağıtılır. Bu nedenle, bir form bölgesini dağıtmak için özel bir görev gerçekleştirmeniz gerekmez. VSTO eklentileri dağıtma hakkında daha fazla bilgi için bkz. [Deploy a Office solution](../vsto/deploying-an-office-solution.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)|Form bölgelerinizi iyileştirebilmenizi ve olası sorunları önlemenize yardımcı olabilecek bilgiler sağlar.|
|[nasıl yapılır: Outlook eklentisi projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|**yeni Outlook form bölgesi** sihirbazı 'nı kullanarak standart veya özel Microsoft Office Outlook formu genişletmek için form bölgesi oluşturmayı gösterir.|
|[form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|form bölgesini her bir öğenin ileti sınıfıyla ilişkilendirerek form bölgesini hangi Microsoft Office Outlook öğelerinin görüntülemesi gerektiğini belirtir.|
|[izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)|Bir kişi öğesinin Inspector penceresinde yeni bir sayfa olarak görünen özel bir form bölgesinin nasıl tasarlanacağını gösterir.|
|[İzlenecek yol: Outlook ' de tasarlanan form bölgesini Içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Microsoft Office Outlook bir form bölgesinin nasıl tasarlanacağını ve sonra **yeni Outlook form bölgesi** sihirbazı 'nı kullanarak form bölgesini bir Outlook VSTO eklentisi projesine aktarmayı gösterir.|
|[Çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md)|Bir form bölgesindeki denetimleri göstermek, gizlemek veya değiştirmek için nasıl kod yazılacağını ve kullanıcıların sınıfı kullanarak projenizdeki diğer alanlardan kodu çalıştırmasına olanak tanır `Globals` .|
|[nasıl yapılır: Outlook form bölgesi görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Microsoft Office Outlook belirli bir öğe için form bölgesi görüntülemesini nasıl önleyekullanabileceğinizi gösterir.|
|form bölgesinin göründüğü Outlook öğeye nasıl erişmekte olduğunu gösterir.|
|[Outlook form bölgelerinde özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)|kullanıcıların bir Outlook öğeye yanıt vermesini nasıl sağladığını açıklar.|
