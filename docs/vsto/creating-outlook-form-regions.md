---
title: Outlook form bölgeleri oluşturma
description: Form bölgelerini daha kolay tasarlamak, geliştirmek ve hata ayıklamak üzere Microsoft Outlook formlarını özelleştirmek için form bölgelerini nasıl kullanabileceğinizi öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3273c02416cac54dfd244ba4f163fb5d726413c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847968"
---
# <a name="create-outlook-form-regions"></a>Outlook form bölgeleri oluşturma
  Form bölgelerini Microsoft Office Outlook formlarını özelleştirmek için kullanabilirsiniz. Visual Studio, form bölgelerini tasarlamanıza, geliştirmenize ve hata ayıklamanıza daha kolay bir şekilde gelişmiş araçlar sağlar.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:

- [Form bölgelerini kullanmanın avantajları](#Enhance)

- [Projenize Outlook form bölgesi ekleme](#Adding)

- [Form bölgesi tasarımcısını kullanma](#UsingFormRegionDesigner)

- [Outlook 'ta tasarlanan form bölgesi kullanma](#UsingFormRegionDesignedOutlook)

- [Form bölgesine özel kod ekleme](#AddingCustomCode)

- [Projeyi derleme](#Building)

- [Form bölgesinde hata ayıklama](#Debugging)

- [Form bölgesi dağıtma](#Deploying)

## <a name="advantages-of-using-form-regions"></a><a name="Enhance"></a> Form bölgelerini kullanmanın avantajları
 Form bölgeleri geleneksel Outlook Forms geliştirmesi üzerinde birçok geliştirme sunar:

- Herhangi bir standart formun varsayılan sayfasını özelleştirin.

- Herhangi bir standart forma en fazla 12 ek sayfa ekleyin.

- Herhangi bir standart formu değiştirin veya geliştirin.

- Okuma bölmesinde ve Inspector 'da özel kullanıcı arabirimini görüntüleyin.

  Daha fazla bilgi için bkz. [form sayfalarını ve form bölgelerini özelleştirme](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).

## <a name="add-an-outlook-form-region-to-your-project"></a><a name="Adding"></a> Projenize Outlook form bölgesi ekleme
 Yeni bir form bölgesi tasarlamak veya Outlook 'ta tasarlanan form bölgesini içeri aktarmak için **Yeni Outlook form bölgesi** Sihirbazı 'nı kullanabilirsiniz. Ayrıca, başka bir Outlook VSTO eklenti projesinde kullandığınız bir form bölgeniz varsa, varolan form bölgenizi yeniden kullanabilirsiniz.

### <a name="create-a-new-form-region-by-using-the-wizard"></a><a name="CreatingFormRegion"></a> Sihirbazı kullanarak yeni bir form bölgesi oluşturma
 Form bölgesi oluşturmak için Outlook VSTO eklentisi projesine bir **Outlook form bölgesi** öğesi ekleyin. Bu, **Yeni Outlook form bölgesi** Sihirbazı 'nı başlatır.

 Yeni bir form bölgesi tasarlamak veya Outlook 'ta tasarlanan form bölgesini içeri aktarmak isteyip istemediğinizi belirtmek için Sihirbazı kullanın. Yeni bir form bölgesi tasarlama hakkında daha fazla bilgi için bkz. [form bölgesi tasarımcısını kullanma](#UsingFormRegionDesigner). Outlook 'ta tasarlanan form bölgesini kullanma hakkında daha fazla bilgi için bkz. [Outlook 'ta tasarlanan form bölgesini Içeri aktarma](#UsingFormRegionDesignedOutlook).

 Oluşturmak istediğiniz form bölgesi türünü belirtmek için Sihirbazı kullanın. Aşağıdaki tabloda her form bölge türü açıklanmaktadır.

|Bölge türü|Açıklama|
|-----------------|-----------------|
|Bağımsız|Form bölgesini Outlook formunda yeni bir sayfa olarak ekler.|
|Boşluğuna bitişik alanda|Form bölgesini Outlook formunun varsayılan sayfasının altına ekler.|
|Değiştirme|Form bölgesini bir Outlook formunun varsayılan sayfasının yerini alan yeni bir sayfa olarak ekler.|
|Tümünü Değiştir|Outlook formunun tamamını form bölgesiyle değiştirir.|

 Ayrıca, görüntüleme koşullarını belirtmek ve genişletilecek form türünü seçmek için Sihirbazı da kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Sihirbazda yaptığınız seçimler diğer sihirbaz sayfalarında bulunan seçenekleri etkiler. Örneğin, **Yeni Outlook form bölgesi oluştur** sayfasında **bitişik** veya **ayrı** seçeneğini belirlerseniz **başlık** ve **Açıklama** alanları, **açıklayıcı açıklayıcı metinde kullanılamaz ve görüntüleme tercihleri sayfasını seçin** . Bunun nedeni Outlook 'un bitişik veya ayrı bir form bölgesi görüntülediğinde bu alanları kullanmamalıdır.

#### <a name="form-region-files"></a>Form bölgesi dosyaları
 **Yeni Outlook form bölgesi** Sihirbazı 'nı tamamladığınızda, Visual Studio projenize otomatik olarak aşağıdaki dosyaları ekler:

- Form bölgesi kod dosyası. Bu dosya, **Yeni öğe Ekle** Iletişim kutusunda **Outlook form bölgesi** öğesi için belirttiğiniz ada sahiptir. Bu dosyaya form bölgesi olaylarını işlemek için kod ekleyin.

- Form bölgesi Tasarımcısı kod dosyası. Bu dosya, form bölgesi Tasarımcısı tarafından oluşturulan kodu içerir ve doğrudan düzenlenmemelidir.

- Outlook form depolama (*. ofs*) dosyası.

    > [!NOTE]
    > Bu dosya yalnızca Outlook 'ta tasarlanan bir form bölgesini içeri aktarırsanız projeye eklenir.

#### <a name="form-region-factory-class"></a>Form bölgesi fabrikası sınıfı
 Form bölgesi kod dosyası, arabirimini uygulayan kısmi bir sınıf içerir <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> . Bu form bölgesi fabrikası sınıfıdır. Form bölgesi fabrikası sınıfı, form bölgesinin yeni örneklerini oluşturmaktan sorumludur.

 **Form bölgesi fabrikası** bölgesini genişleterek bu sınıfı bulabilirsiniz.

 **Yeni Outlook form bölgesi** Sihirbazı bu sınıfa, form bölgesinin iç adını ve form bölgesini görüntüleyen ileti sınıflarını belirten öznitelikler ekler. Dosya projeye eklendikten sonra bu öznitelikleri el ile değiştirebilirsiniz.

 Form bölgesi fabrikası sınıfının çoğu form bölgesi tasarımcı dosyasında uygulanır. Ancak `FormRegionInitializing` olay işleyicisi, form bölgesi kod dosyasında gösterilir. Bu olay işleyicisini Outlook 'un form bölgesini görüntülemesi gerekip gerekmediğini belirtmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [tanıtıcı form bölgesi olayları](#HandlingFormRegionEvents).

### <a name="add-an-existing-form-region-to-your-project"></a><a name="AddingExistingFormRegion"></a> Projenize var olan bir form bölgesi ekleme
 Başka bir Outlook projesinde kullandığınız bir Outlook form bölgeniz varsa, **var olan öğe Ekle** iletişim kutusunu kullanarak GEÇERLI Outlook VSTO eklenti projenizde onu yeniden kullanabilirsiniz.

 Varolan form bölgesinin bir kod dosyası (*. vb* veya *. cs*) olması gerekir; **mevcut öğe Ekle** iletişim kutusunu kullanarak Outlook form depolama (*. ofs*) dosyalarını ekleyemezsiniz. Ancak, bir Outlook Form Depolama dosyasını içeri aktararak yeni bir form bölgesi oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

## <a name="use-the-form-region-designer"></a><a name="UsingFormRegionDesigner"></a> Form bölgesi tasarımcısını kullanma
 Form bölgesi Tasarımcısı, form bölgesinin yerleşimini ve görünümünü tasarlamanıza yardımcı olur. Yönetilen denetimleri tasarımcının yüzeyine sürükleyebilirsiniz, Denetim ' e çift tıklayarak olay işleyicilerini açabilir ve **Özellikler** penceresinde özellikleri ayarlayabilirsiniz.

> [!NOTE]
> Form bölgesinin, **Özellikler** penceresindeki **bildirim** düğümünün altında Outlook 'ta görünme biçimini etkileyen özellikleri bulabilirsiniz.

 Form bölgesi Tasarımcısı yalnızca **Yeni Outlook form bölgesi** sihirbazının **form bölgesini nasıl oluşturmak Istediğinizi seçin** sayfasında **Yeni bir form bölgesi Tasarla** ' yı seçerseniz kullanılabilir.

 Form bölgesi tasarımcısını açmak için üç yol vardır:

- **Çözüm Gezgini**, form bölgesi kod dosyasına çift tıklayın.

- **Çözüm Gezgini**, form bölgesi kod dosyasına sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

- **Çözüm Gezgini**, form bölgesi kod dosyasını seçin ve ardından **Görünüm** menüsünde **Tasarımcı**' ya tıklayın.

  Form bölgesi Tasarımcısı yalnızca yönetilen denetimleri destekler. Yerel Outlook denetimleri ekleyemezsiniz.

## <a name="import-a-form-region-designed-in-outlook"></a><a name="UsingFormRegionDesignedOutlook"></a> Outlook 'ta tasarlanan form bölgesini içeri aktarma
 Outlook 'ta tasarladığınızda, form bölgesine yerel Outlook denetimleri ekleyebilirsiniz. Yerel Outlook denetimleri, tasarım zamanında Outlook verilerine bağlamanıza olanak tanır. Ancak, form bölgesi tasarımcısını kullanarak yönetilen denetimler ekleyebilir veya form bölgesinin tasarımını değiştirebilirsiniz.

 **Yeni Outlook form bölgesi** Sihirbazı 'nı kullanarak form bölgelerini BIR Outlook VSTO eklentisi projesine aktarabilirsiniz. **Form bölgesini nasıl oluşturmak Istediğinizi seçin** sayfasında **Outlook form depolama (. ofs) dosyasını içeri aktar**' ı seçin. Daha sonra bir Outlook form depolama dosyası (*. ofs*) dosyasının konumuna gidebilirsiniz. (Outlook, form bölgelerini *. ofs* dosyaları olarak kaydeder.)

 **Yeni Outlook form bölgesi** Sihirbazı *. ofs* dosyasını proje dizinine kopyalar ve form bölgesi tasarımcı dosyasına denetim başvuruları ekler. Daha sonra form bölgesi kod dosyasında denetim olaylarını işleyebilirsiniz.

 Visual Basic projesindeki olayları işlemek için, kod düzenleyicisinin en üstündeki Yöntem adı listesinden bir olay seçin.

 Bir C# projesindeki olayları işlemek için yöntemindeki olayları denetlemek için abone olun <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> . Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma &#40;C&#35; programlama kılavuzu&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).

 Form bölgesi fabrikası sınıfının yönteminde form bölgesi özelliklerini değiştirebilirsiniz `InitializeManifest` .

> [!NOTE]
> Form bölgesini içeri aktarmak için, geliştirme bilgisayarına yüklediğiniz aynı Outlook sürümünü hedefleyen bir projede çalışmanız gerekir. Örneğin, Outlook 2010 yüklüyse, form bölgesinin içe aktarılması yalnızca bir projede çalışır ve **outlook 2010 eklenti** projesi şablonu kullanılarak oluşturulmuştur.

### <a name="update-an-imported-form-regions-design"></a>İçeri aktarılan form bölgesinin tasarımını güncelleştirme
 Form bölgesindeki denetimleri ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Bunu yapmadan önce, form bölgesi kod dosyasına eklediğiniz kodu yedekleyin. Ardından, Outlook 'ta *. ofs* dosyasını açın, form bölgesini değiştirin ve değişiklikleri kaydedin. Değiştirilen *. ofs* dosyasını içeri aktarmak Için **Yeni Outlook form bölgesi** Sihirbazı 'nı kullanın. Kodunuzu daha sonra yeni form bölgesi kod dosyasına yapıştırabilirsiniz.

## <a name="add-custom-code-to-a-form-region"></a><a name="AddingCustomCode"></a> Form bölgesine özel kod ekleme
 <xref:Microsoft.Office.Tools.Outlook>Ad alanı, form bölgesini, form bölgesini görüntüleyen Outlook öğesini ve diğer yararlı öğeleri temsil eden sınıflara erişmenizi sağlar. **Outlook form bölgesi** öğesi, projedeki bu derlemeye otomatik olarak bir başvuru ekler ve form bölgesi kod dosyasının en üstüne uygun **using** veya **Imports** ifadesini ekler.

 `Microsoft.Office.Interop.Outlook`Outlook programlama görevlerinin çoğunu gerçekleştirmek için ad alanındaki sınıfları, yöntemleri ve özellikleri kullanabilirsiniz. Outlook nesne modeli hakkında daha fazla bilgi için bkz. [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md). Outlook nesne modelini kullanan tipik görev örnekleri için bkz. [Outlook çözümleri](../vsto/outlook-solutions.md).

### <a name="handle-form-region-events"></a><a name="HandlingFormRegionEvents"></a> Form bölgesi olaylarını işle
 **Outlook form bölgesi** öğesi, aşağıdaki üç olay işleyicisini form bölgesi kod dosyasına otomatik olarak ekler.

|Olay|Açıklama|
|-----------|-----------------|
|Formregionbaşlatılıyor|Form bölgesi başlatılmadan önce oluşur. Outlook 'un form bölgesini görüntülemesi gerekip gerekmediğini öğrenmek için bu olay işleyicisindeki koşulları kontrol edebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Outlook 'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|
|Bir Formregiongösteriliyor|Form bölgesinin bir örneği oluşturulduktan sonra, ancak form bölgesi görüntülenmeden önce oluşur.|
|FormRegionClosed|Form bölgesi kapatılmadan önce gerçekleşir.|

## <a name="build-the-project"></a><a name="Building"></a> Projeyi derleme
 Form bölgesi içeren bir Outlook VSTO eklentisi projesi oluşturduğunuzda, Visual Studio kayıt defterine aşağıdaki bilgileri ekler:

- Bir veya daha fazla form bölgesi ile ilişkili her ileti sınıfı için bir anahtar.

- Her form bölgesi için bir giriş ve Outlook VSTO eklentisinin adını temsil eden ilişkili bir değer.

  Outlook, form bölgelerini yüklemek için bu bilgileri kullanır.

## <a name="debug-a-form-region"></a><a name="Debugging"></a> Form bölgesinde hata ayıklama
 Form bölgesi içeren bir Outlook VSTO eklentisinin hatalarını, diğer projelerde hata ayıklaması yaptığınız gibi ayıklayabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Hata ayıklayıcıyı başlattığınızda, Visual Studio otomatik olarak Outlook 'u başlatır.

 Form bölgesini görüntülemek için uygun Outlook öğesini açmanız gerekir. Örneğin, bir bitişik form bölgesi bir posta öğesinin altına eklendiğinde, bir posta öğesi açın.

## <a name="deploy-a-form-region"></a><a name="Deploying"></a> Form bölgesi dağıtma
 Form bölgeleri, ilişkili Outlook VSTO eklentisi ile otomatik olarak dağıtılır. Bu nedenle, bir form bölgesini dağıtmak için özel bir görev gerçekleştirmeniz gerekmez. VSTO Eklentilerini dağıtma hakkında daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)|Form bölgelerinizi iyileştirebilmenizi ve olası sorunları önlemenize yardımcı olabilecek bilgiler sağlar.|
|[Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|**Yeni Outlook form bölgesi** Sihirbazı 'nı kullanarak standart veya özel Microsoft Office Outlook formunu genişletmek için form bölgesi oluşturmayı gösterir.|
|[Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Form bölgesini her bir öğenin ileti sınıfıyla ilişkilendirerek, hangi Microsoft Office Outlook öğelerinin form bölgesi görüntülemesi gerektiğini belirtmeyi açıklar.|
|[İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)|Bir kişi öğesinin Inspector penceresinde yeni bir sayfa olarak görünen özel bir form bölgesinin nasıl tasarlanacağını gösterir.|
|[İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Outlook Microsoft Office bir form bölgesinin nasıl tasarlanacağını ve ardından **Yeni Outlook form bölgesi** Sihirbazı 'nı kullanarak form bölgesini BIR Outlook VSTO eklentisi projesine aktarmayı gösterir.|
|[Çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md)|Bir form bölgesindeki denetimleri göstermek, gizlemek veya değiştirmek için nasıl kod yazılacağını ve kullanıcıların sınıfı kullanarak projenizdeki diğer alanlardan kodu çalıştırmasına olanak tanır `Globals` .|
|[Nasıl yapılır: Outlook 'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Microsoft Office Outlook 'un belirli bir öğe için form bölgesi görüntülemesini nasıl önleyegösterdiğini gösterir.|
|Form bölgesinin göründüğü Outlook öğesine nasıl erişmekte olduğunu gösterir.|
|[Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)|Kullanıcıların bir Outlook öğesine yanıt vermesini nasıl sağladığını açıklar.|
