---
title: Outlook form bölgeleri oluşturma
description: form bölgelerini daha kolay tasarlamak, geliştirmek ve hatalarını ayıklamak üzere Microsoft Outlook formlarını özelleştirmek için form bölgelerini nasıl kullanabileceğinizi öğrenin.
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
# <a name="create-outlook-form-regions"></a>Outlook form bölgeleri oluşturma
  form bölgelerini, Microsoft Office Outlook formlarını özelleştirmek için kullanabilirsiniz. Visual Studio, form bölgelerini tasarlamanıza, geliştirmenize ve hata ayıklamanıza daha kolay hale getirmek için gelişmiş araçlar sağlar.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:

- [Form bölgelerini kullanmanın avantajları](#Enhance)

- [projenize Outlook form bölgesi ekleme](#Adding)

- [Form bölgesi tasarımcısını kullanma](#UsingFormRegionDesigner)

- [Outlook 'da tasarlanan bir form bölgesi kullanın](#UsingFormRegionDesignedOutlook)

- [Form bölgesine özel kod ekleme](#AddingCustomCode)

- [Projeyi derleme](#Building)

- [Form bölgesinde hata ayıklama](#Debugging)

- [Form bölgesi dağıtma](#Deploying)

## <a name="advantages-of-using-form-regions"></a><a name="Enhance"></a> Form bölgelerini kullanmanın avantajları
 form bölgeleri geleneksel Outlook formları geliştirmesi üzerinde birçok geliştirme sunar:

- Herhangi bir standart formun varsayılan sayfasını özelleştirin.

- Herhangi bir standart forma en fazla 12 ek sayfa ekleyin.

- Herhangi bir standart formu değiştirin veya geliştirin.

- Okuma bölmesinde ve Inspector 'da özel kullanıcı arabirimini görüntüleyin.

  Daha fazla bilgi için bkz. [form sayfalarını ve form bölgelerini özelleştirme](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).

## <a name="add-an-outlook-form-region-to-your-project"></a><a name="Adding"></a>projenize Outlook form bölgesi ekleme
 yeni bir form bölgesi tasarlamak veya Outlook tasarlanan form bölgesini içeri aktarmak için **yeni Outlook form bölgesi** sihirbazını kullanabilirsiniz. ayrıca, başka bir Outlook VSTO eklenti projesinde kullandığınız bir form bölgeniz varsa, varolan form bölgenizi yeniden kullanabilirsiniz.

### <a name="create-a-new-form-region-by-using-the-wizard"></a><a name="CreatingFormRegion"></a> Sihirbazı kullanarak yeni bir form bölgesi oluşturma
 form bölgesi oluşturmak için bir Outlook VSTO eklenti projesine bir **Outlook form bölgesi** öğesi ekleyin. **yeni Outlook Form bölgesi** sihirbazı başlatılır.

 Yeni bir form bölgesi tasarlamak veya Outlook olarak tasarlanan form bölgesini içeri aktarmak isteyip istemediğinizi belirtmek için Sihirbazı kullanın. Yeni bir form bölgesi tasarlama hakkında daha fazla bilgi için bkz. [form bölgesi tasarımcısını kullanma](#UsingFormRegionDesigner). Outlook ' de tasarlanan form bölgesini kullanma hakkında daha fazla bilgi için, bkz. [Outlook tasarlanan form bölgesini içeri aktarma](#UsingFormRegionDesignedOutlook).

 Oluşturmak istediğiniz form bölgesi türünü belirtmek için Sihirbazı kullanın. Aşağıdaki tabloda her form bölge türü açıklanmaktadır.

|Bölge türü|Açıklama|
|-----------------|-----------------|
|Bağımsız|form bölgesini Outlook formunda yeni bir sayfa olarak ekler.|
|Boşluğuna bitişik alanda|form bölgesini Outlook formun varsayılan sayfasının altına ekler.|
|Değiştirme|form bölgesini, bir Outlook formunun varsayılan sayfasının yerini alan yeni bir sayfa olarak ekler.|
|Tümünü Değiştir|tüm Outlook formunu form bölgesiyle değiştirir.|

 Ayrıca, görüntüleme koşullarını belirtmek ve genişletilecek form türünü seçmek için Sihirbazı da kullanabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Sihirbazda yaptığınız seçimler diğer sihirbaz sayfalarında bulunan seçenekleri etkiler. örneğin, **yeni bir Outlook Form bölgesi oluştur** sayfasında **bitişik** veya **ayrı** seçeneğini belirlerseniz **başlık** ve **açıklama** alanları **açıklayıcı açıklayıcı metin içinde kullanılamaz ve görüntüleme tercihleri sayfasını seçin** . bunun nedeni, Outlook bitişik veya ayrı bir form bölgesi görüntülediğinde bu alanları kullanmaz.

#### <a name="form-region-files"></a>Form bölgesi dosyaları
 **yeni Outlook Form bölgesi** sihirbazı 'nı tamamladığınızda, Visual Studio otomatik olarak aşağıdaki dosyaları projenize ekler:

- Form bölgesi kod dosyası. bu dosya, **yeni öğe ekle** iletişim kutusunda **Outlook Form bölgesi** öğesi için belirttiğiniz ada sahiptir. Bu dosyaya form bölgesi olaylarını işlemek için kod ekleyin.

- Form bölgesi Tasarımcısı kod dosyası. Bu dosya, form bölgesi Tasarımcısı tarafından oluşturulan kodu içerir ve doğrudan düzenlenmemelidir.

- Outlook Form Depolama (*. ofs*) dosyası.

    > [!NOTE]
    > Bu dosya yalnızca Outlook ' de tasarlanan bir form bölgesini içeri aktarırsanız projeye eklenir.

#### <a name="form-region-factory-class"></a>Form bölgesi fabrikası sınıfı
 Form bölgesi kod dosyası, arabirimini uygulayan kısmi bir sınıf içerir <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> . Bu form bölgesi fabrikası sınıfıdır. Form bölgesi fabrikası sınıfı, form bölgesinin yeni örneklerini oluşturmaktan sorumludur.

 **Form bölgesi fabrikası** bölgesini genişleterek bu sınıfı bulabilirsiniz.

 **yeni Outlook form bölgesi** sihirbazı bu sınıfa, form bölgesinin iç adını ve form bölgesini görüntüleyen ileti sınıflarını belirten öznitelikler ekler. Dosya projeye eklendikten sonra bu öznitelikleri el ile değiştirebilirsiniz.

 Form bölgesi fabrikası sınıfının çoğu form bölgesi tasarımcı dosyasında uygulanır. Ancak `FormRegionInitializing` olay işleyicisi, form bölgesi kod dosyasında gösterilir. bu olay işleyicisini, Outlook form bölgesinin görüntülenip görüntülenmeyeceğini belirtmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [tanıtıcı form bölgesi olayları](#HandlingFormRegionEvents).

### <a name="add-an-existing-form-region-to-your-project"></a><a name="AddingExistingFormRegion"></a> Projenize var olan bir form bölgesi ekleme
 başka bir Outlook projesinde kullandığınız bir Outlook form bölgeniz varsa, **varolan öğe ekle** iletişim kutusunu kullanarak mevcut Outlook VSTO eklenti projenizde onu yeniden kullanabilirsiniz.

 Varolan form bölgesinin bir kod dosyası (*. vb* veya *. cs*) olması gerekir; **varolan öğe ekle** iletişim kutusunu kullanarak Outlook Form Depolama (*. ofs*) dosyaları ekleyemezsiniz. ancak, bir Outlook form Depolama dosyasını içeri aktararak yeni bir form bölgesi oluşturabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

## <a name="use-the-form-region-designer"></a><a name="UsingFormRegionDesigner"></a> Form bölgesi tasarımcısını kullanma
 Form bölgesi Tasarımcısı, form bölgesinin yerleşimini ve görünümünü tasarlamanıza yardımcı olur. Yönetilen denetimleri tasarımcının yüzeyine sürükleyebilirsiniz, Denetim ' e çift tıklayarak olay işleyicilerini açabilir ve **Özellikler** penceresinde özellikleri ayarlayabilirsiniz.

> [!NOTE]
> form bölgesinin, **özellikler** penceresindeki **bildirim** düğümünün altında Outlook görünme biçimini etkileyen özellikleri bulabilirsiniz.

 form bölgesi tasarımcısı yalnızca **yeni Outlook form bölgesi** sihirbazının **form bölgesini nasıl oluşturmak istediğinizi seçin** sayfasında **yeni bir form bölgesi tasarla** ' yı seçerseniz kullanılabilir.

 Form bölgesi tasarımcısını açmak için üç yol vardır:

- **Çözüm Gezgini**, form bölgesi kod dosyasına çift tıklayın.

- **Çözüm Gezgini**, form bölgesi kod dosyasına sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

- **Çözüm Gezgini**, form bölgesi kod dosyasını seçin ve ardından **Görünüm** menüsünde **Tasarımcı**' ya tıklayın.

  Form bölgesi Tasarımcısı yalnızca yönetilen denetimleri destekler. yerel Outlook denetimleri ekleyemezsiniz.

## <a name="import-a-form-region-designed-in-outlook"></a><a name="UsingFormRegionDesignedOutlook"></a>Outlook 'da tasarlanan form bölgesini içeri aktarma
 Outlook içinde tasarladığınızda, form bölgesine yerel Outlook denetimleri ekleyebilirsiniz. yerel Outlook denetimleri, tasarım zamanında Outlook verileri bağlamanıza olanak tanır. Ancak, form bölgesi tasarımcısını kullanarak yönetilen denetimler ekleyebilir veya form bölgesinin tasarımını değiştirebilirsiniz.

 **yeni Outlook form bölgesi** sihirbazı 'nı kullanarak form bölgelerini bir Outlook VSTO eklenti projesine aktarabilirsiniz. **form bölgesini nasıl oluşturmak istediğinizi seçin** sayfasında **Outlook form Depolama (. ofs) dosyasını içeri aktar**' ı seçin. daha sonra bir Outlook Form Depolama dosya (*. ofs*) dosyasının konumuna gidebilirsiniz. (Outlook form bölgelerini *. ofs* dosyaları olarak kaydeder.)

 **yeni Outlook form bölgesi** sihirbazı *. ofs* dosyasını proje dizinine kopyalar ve Form bölgesi tasarımcı dosyasına denetim başvuruları ekler. Daha sonra form bölgesi kod dosyasında denetim olaylarını işleyebilirsiniz.

 Visual Basic projesindeki olayları işlemek için, kod düzenleyicisinin en üstündeki yöntem adı listesinden bir olay seçin.

 Bir C# projesindeki olayları işlemek için yöntemindeki olayları denetlemek için abone olun <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> . Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma &#40;C&#35; programlama kılavuzu&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).

 Form bölgesi fabrikası sınıfının yönteminde form bölgesi özelliklerini değiştirebilirsiniz `InitializeManifest` .

> [!NOTE]
> form bölgesini içeri aktarmak için, geliştirme bilgisayarına yüklediğiniz Outlook aynı sürümünü hedefleyen bir projede çalışmanız gerekir. örneğin, Outlook 2010 yüklüyse, form bölgesinin içeri aktarılması yalnızca bir projede çalışır ve **Outlook 2010 eklenti** projesi şablonu kullanılarak oluşturulmuştur.

### <a name="update-an-imported-form-regions-design"></a>İçeri aktarılan form bölgesinin tasarımını güncelleştirme
 Form bölgesinde denetim ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Bunu yapmadan önce, form bölgesi kod dosyasına ekley istediğiniz kodu geri kaydedin. Ardından *.ofs dosyasını dosyanın* Outlook form bölgesinde değişiklik yapın ve değişiklikleri kaydedin. Değiştirilen **.ofs Outlook içeri** almak için Yeni Form Bölgesi *sihirbazını* kullanın. Ardından kodunuzu yeni form bölgesi kod dosyasına yapıştırabilirsiniz.

## <a name="add-custom-code-to-a-form-region"></a><a name="AddingCustomCode"></a> Form bölgesi için özel kod ekleme
 Ad <xref:Microsoft.Office.Tools.Outlook> alanı size form bölgelerini, form bölgelerini görüntüleyen Outlook ve diğer yararlı öğeleri temsil eden sınıflara erişim sağlar. Form **Outlook öğesi,** projedeki bu derlemeye otomatik olarak bir başvuru ekler ve form bölgesi kod dosyasının en üstüne uygun **using** veya **Imports** deyimini ekler.

 Programlama görevlerinizin çoğunu gerçekleştirmek için ad alanı içinde sınıfları, yöntemleri ve `Microsoft.Office.Interop.Outlook` özellikleri Outlook kullanabilirsiniz. Nesne modeli oluşturma hakkında daha Outlook için bkz. [Outlook modeline genel bakış.](../vsto/outlook-object-model-overview.md) Outlook nesne modelini kullanan tipik görevler için bkz. [Outlook.](../vsto/outlook-solutions.md).

### <a name="handle-form-region-events"></a><a name="HandlingFormRegionEvents"></a> Form bölgesi olaylarını işleme
 Form **Outlook öğesi,** form bölgesi kod dosyasına aşağıdaki üç olay işleyicisini otomatik olarak ekler.

|Olay|Açıklama|
|-----------|-----------------|
|FormRegionInitializing|Form bölgesi başlatılmadan önce gerçekleşir. Bu olay işleyicisinde koşulları kontrol edip form Outlook olup olmadığını tespit edin. Daha fazla bilgi için [bkz. Nasıl Outlook form bölgesi görüntülemesini engelleme.](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|
|FormRegionShowing|Form bölgesi örneği oluşturulduktan sonra ancak form bölgesi görüntülendiğinde gerçekleşir.|
|FormRegionClosed|Form bölgesi kapatılana kadar gerçekleşir.|

## <a name="build-the-project"></a><a name="Building"></a> Projeyi oluşturma
 Form bölgesi içeren Outlook VSTO bir Eklenti projesi derlemeniz Visual Studio kayıt defterine aşağıdaki bilgileri ekler:

- Bir veya daha fazla form bölgesiyle ilişkili her ileti sınıfı için bir anahtar.

- Her form bölgesi için bir giriş ve eklentinin adını temsil eden ilişkili Outlook VSTO.

  Outlook form bölgelerini yüklemek için bu bilgileri kullanır.

## <a name="debug-a-form-region"></a><a name="Debugging"></a> Form bölgesinde hata ayıklama
 Form bölgesi içeren Outlook VSTO diğer projelerde olduğu gibi bir eklentide hata [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayıkabilirsiniz. Hata ayıklayıcıyı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatırken, Visual Studio otomatik olarak Outlook.

 Form bölgelerini görüntülemek için uygun form Outlook açabilirsiniz. Örneğin, bir posta öğesinin altına bir bitişik form bölgesi eklenirse, bir posta öğesi açın.

## <a name="deploy-a-form-region"></a><a name="Deploying"></a> Form bölgesi dağıtma
 Form bölgeleri, ilişkili Outlook VSTO otomatik olarak dağıtılır. Bu nedenle, bir form bölgesi dağıtmak için herhangi bir özel görev gerçekleştirmeniz gerekli değildir. Eklentilerini dağıtma hakkında daha fazla VSTO için bkz. [Bir Office dağıtma.](../vsto/deploying-an-office-solution.md)

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Form bölgelerini Outlook yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)|Form bölgelerinizi iyileştirmenize ve olası sorunlardan kaçınmanıza yardımcı olacak bilgiler sağlar.|
|[Nasıl yapılanlar: Eklenti projesine Outlook bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Yeni Form Bölgesi sihirbazını kullanarak standart veya özel bir form Microsoft Office Outlook bir form bölgesi **Outlook nasıl oluşturabilirsiniz?**|
|[Form bölgelerini bir form Outlook ile ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Form bölgesi ile her Microsoft Office Outlook ileti sınıfıyla iletinin nasıl bir form bölgesi görüntüle görüntüleycegerek hangi öğelerin form bölgesi görüntüleyenileşimlerini açıklar.|
|[Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)|Bir kişi öğesinin Denetçi penceresinde yeni sayfa olarak görünen özel bir form bölgesi tasarlamayı gösterir.|
|[Adım adım kılavuz: Veri kaynağında tasarlanmış bir form Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Yeni Form Bölgesi sihirbazını kullanarak Microsoft Office Outlook form bölgesi tasarlamayı ve ardından form Outlook VSTO eklenti projesine aktarma **Outlook yı** gösterir.|
|[Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md)|Form bölgesinde denetimleri göstermek, gizlemek veya değiştirmek ve kullanıcıların sınıfını kullanarak projenizin diğer alanlarından kodu çalıştırmalarını sağlamak için nasıl kod yazacaklarını `Globals` açıklar.|
|[Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Belirli bir öğe Microsoft Office Outlook bir form bölgesi görüntülemesini önlemeyi gösterir.|
|Form bölgesi görünen Outlook öğeye nasıl erişileni gösterir.|
|[Form bölgelerinde Outlook eylemler](../vsto/custom-actions-in-outlook-form-regions.md)|Kullanıcıların bir öğeye yanıt vermesine nasıl olanak Outlook açıklar.|
