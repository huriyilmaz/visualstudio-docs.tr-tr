---
title: İş akışı SharePoint çözümleri oluşturma | Microsoft Docs
description: Web SharePoint ve liste öğelerinin yaşam döngüsünü yöneten özel iş akışları oluşturmak için araçları kullanarak iş akışı SharePoint oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ba44e9c128cafec7223e5a90b0aa2d37cab6f8e2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635646"
---
# <a name="create-sharepoint-workflow-solutions"></a>İş SharePoint çözümleri oluşturma

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Web sitesinde belgelerin ve liste öğelerinin yaşam döngüsünü yöneten özel iş akışları oluşturmanıza yardımcı SharePoint sağlar. Sağlanan öğeler arasında tasarımcı, etkinlik denetimleri kümesi ve gerekli derleme başvuruları yer almaktadır. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ayrıca, iş **SharePoint oluşturmanıza ve** yapılandırmanıza yardımcı olmak için Özelleştirme Sihirbazı'nı içerir.

Daha fazla bilgi SharePoint için [bkz. Microsoft SharePoint Ürünleri ve Teknolojileri.](/sharepoint/dev/)

## <a name="workflows-in-sharepoint"></a>SharePoint'de iş SharePoint
 Bir iş akışını bir SharePoint kitaplığına veya listesine eklerken, kitaplık veya listedeki tüm öğelere bir iş süreci zorlar. Bir iş akışı, sistemin veya kullanıcıların her öğe üzerinde gerçekleştirmesi gereken, düzenlenemez ve gözden geçirile bir öğe gönderme gibi eylemleri açıklar. Etkinlikler olarak bilinen *bu eylemler,* iş akışının yapı taşlarıdır.

 içinde iş SharePoint oluşturabilir ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bunları bir web sitesine SharePoint dağıtabilirsiniz. Bir iş akışı SharePoint sonra bir kitaplık veya listeyle ilişkilendirilz. Daha sonra otomatik olarak, bir işlem tarafından veya bir kullanıcı tarafından el ile başlatılabilir. İş akışı işlemi hakkında daha fazla bilgi için [bkz. SharePoint kullanarak iş Visual Studio.](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio)

## <a name="create-custom-sharepoint-workflows"></a>Özel iş SharePoint oluşturma
 İki SharePoint iş akışı projelerini kullanabilirsiniz: Sıralı İş [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Akışı** ve Durum Makinesi **İş Akışı.**

 Sıralı *iş akışı* bir dizi adımı temsil eder. Son etkinlik tamamlanana kadar adımlar tek tek gerçekleştirilir. Sıralı iş akışları her zaman yürütme sırasında kesin olarak sıralıdır. Dış olayları alaları ve paralel mantık akışları içermeleri nedeniyle tam yürütme sırası farklılık gösterebilir. Aşağıdaki çizimde sıralı iş akışı örneği gösterilmiştir.

 ![Sıralı İş Akışı](../sharepoint/media/sp-sequential.png "Sıralı Iş akışı")

 Durum *makinesi iş akışı* bir dizi durumu, geçişi ve eylemi temsil eder. Bir durum makinesi iş akışında adımlar zaman uyumsuz olarak yürütülür. Başka bir anlama gelir ki bunlar her zaman bire bir gerçekleştirilecek değil, bunun yerine eylemler ve durumlarla tetiklenir. Bir durum başlangıç durumu olarak atanır ve ardından bir olayı temel alarak başka bir duruma geçiş yapılır. Durum makinesi, iş akışının sonunu belirleyen son bir durumuna sahip olabilir. Aşağıdaki diyagramda durum makinesi iş akışının bir örneği gösterildi.

 ![Durum Makinesi İş Akışı](../sharepoint/media/sp-state.png "Durum makinesi Iş akışı")

 İş akışı türleri hakkında daha fazla bilgi için bkz. [İş Akışı Türleri.](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14))

### <a name="use-the-wizard"></a>Sihirbazı kullanma
 'de bir SharePoint iş akışı projesi sanız, önce özelleştirme özelleştirme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **sihirbazında SharePoint belirtirsiniz.** Sihirbaz, içinde bir proje oluşturmak için bu **ayarları Çözüm Gezgini.** Bu proje bir kod dosyası, iş akışını dağıtmak için kullanılan birkaç dosya ve özel bir iş akışı oluşturmak için gereken derlemelere SharePoint içerir.

 İş akışını oluşturduk sonra, iş akışının özelliklerini Özellikler penceresi. Çoğu iş akışı özelliği doğrudan Özellikler penceresi olsa da, bazıları değerlerini değiştirmek için bir üç nokta düğmesine (![ASP.NET Mobil](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")Tasarımcı üç nokta ) tıklamanızı gerektirir. Bu düğme, Özelleştirme **Sihirbazı'SharePoint yeniden başlatır.** Özellik değeri değiştikten sonra son olarak **Son** düğmesini seçin.

> [!NOTE]
> İş **Akışı Türü** özelliği salt okunur ve değiştirilemez. İş akışı türünü değiştirmek için başka bir iş akışı oluşturmanız gerekir.

## <a name="design-a-sharepoint-workflow"></a>İş akışı SharePoint tasarlama
 İş sürecindeki tüm adımları tanımlayarak iş akışı tasarımcısını kullanarak iş [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] akışınızı SharePoint. Tasarımcıyı açmak için, Çözüm Gezgini'de Workflow1.cs veya Workflow1.vb'ye çift tıklayın veya bu dosyalardan herhangi biri için kısayol menüsünü açıp Aç'ı **seçin.**

### <a name="activities"></a>Etkinlikler
 bir iş akışı tasarlamak için Araç Kutusundan **tasarımcıda** bir iş *akışı zaman çizelgesine* etkinlikler ekleyin. İş akışı zamanlaması, gerçekleştirilecekleri sırayla etkinliklerin sırasını içerir.

 İki tür etkinlik vardır:

- *Basit etkinlikler,* "1 günlük gecikme" veya "Web hizmetini başlatma" gibi tek bir iş birimini gerçekleştirmektedir.

- *Bileşik etkinlikler diğer* etkinlikleri içerir; Örneğin, bir koşullu etkinlik iki dal içerebilir.

  Her iki etkinlik türü de Araç Kutusunda **mevcuttur.**

  Etkinlikler özelliklere, yöntemlere ve olaylara sahip olabilir. Bir **etkinliğin** özelliklerini ayarlamak için Özellikler penceresini kullanın.

  Özel bir etkinlik de oluşturabilirsiniz. Daha fazla bilgi için [bkz. Adım adım: Özel bir site iş akışı etkinliği oluşturma.](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)

  Etkinlikler Araç Kutusu'nda aşağıdaki **sekmelerde düzenlenmiştir:**

- **SharePoint Iş akışı**

- **Windows İş akışı v3.0**

- **Windows İş akışı v3.5**

  Tüm temel iş akışı etkinlikleri, iş akışı SharePoint. Daha fazla bilgi için bkz. [genel bakış için Windows SharePoint Services Etkinlikleri.](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))

#### <a name="sharepoint-workflow-activities"></a>SharePoint iş akışı etkinliklerini kullanma
 İş **SharePoint sekmeleri** içinde kullanım için özel etkinlikler [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] içerir. Bu etkinlikler belge yaşam döngüsü iş akışlarının geliştirilmesini basitleştirir ve kolaylaştırır. SharePoint İş Akışı sekmesinde listelenen etkinlikler **hakkında daha fazla bilgi** için bkz. Windows SharePoint Services Genel [Bakış.](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))

#### <a name="windows-workflow-activities"></a>Windows iş akışı etkinlikleri
 İş **Windows sekmeleri** tarafından sağlanan etkinlikleri [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] içerir. Bu etkinlikleri kullanarak her türlü iş akışı uygulaması için iş akışı Windows oluşturabilirsiniz.

 İş Akışları sekmesinde listelenen etkinlikler hakkında daha fazla **Windows** için [bkz. Windows Workflow Foundation Etkinlikleri.](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)) Windows Workflow Foundation hakkında daha fazla bilgi için [bkz. Windows Workflow Foundation'a Genel Bakış.](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90))

### <a name="work-with-activities-in-the-designer"></a>Tasarımcıda etkinliklerle çalışma
 İş akışı zamanlamanız, İş Akışı etkinliklerinin Windows bir birleşimini ve SharePoint etkinliklerini içerebilir.

 Tasarımcı, etkinlikleri doğru şekilde konumlandırmanıza ve yapılandırmanıza yardımcı olacak görsel ipuçları görüntüler. Bir etkinliği iş akışı zamanlaması üzerine sürükler veya kopyalarsanız tasarımcı, iş akışında bu etkinlik için geçerli konumları gösteren yeşil artı işareti (+) simgeleri görüntüler. Bir etkinliği geçerli olmayacak bir konuma konumamazsiniz. Örneğin, Bir Gönderme etkinliğini Dinleme etkinliği dallarında ilk etkinlik olarak konumlayayamazsiniz. Daha fazla bilgi için [bkz. SharePoint Tasarımcısı Geliştirici Merkezi.](https://developer.microsoft.com/office/docs)

## <a name="collect-information-during-the-workflow"></a>İş akışı sırasında bilgi toplama
 İş akışında önceden tanımlanmış zamanlarda kullanıcılardan bilgi toplamak iyi olabilir. Form veya öğe özelliklerini kullanarak bilgi toplayabilirsiniz.

### <a name="forms"></a>Formlar
 Formlar, sorular içeren ve kullanıcıların yanıt verme yolları sağlayan iletişim kutularına benzer.

 Bir iş akışında 4 tür form kullanılabilir:

- Derneği

- Başlatma

- Değişiklik

- Görev

  Bunların arasında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ilişkilendirme ve başlatan formlar için öğe şablonları yer almaktadır. İlişki oluşturma formuna *örnek olarak,* iş akışını yükleyerek yöneticinin iş akışıyla ilgili parametreler (harcama iş akışı için harcama limiti gibi) girmesini sağlayan bir form vardır. Başlatma formuna *örnek olarak,* bir gider iş akışının kullanıcılarının iş akışına harcanan tutarı girmelerini sağlayan bir form ve bir örnektir. Bu tür formlar hakkında daha fazla bilgi için [bkz. SharePoint proje ve proje öğesi şablonları.](../sharepoint/sharepoint-project-and-project-item-templates.md)

### <a name="item-properties"></a>Öğe özellikleri
 Kullanıcılardan bilgi toplamak için kitaplıkta veya listede yer alan bir öğenin SharePoint da toplayabilirsiniz. Ana kod dosyası (Workflow1.cs veya Workflow1.vb) Microsoft'un bir örneğini belirtir. SharePoint. adlı Workflow.SPWorkflowActivationProperties.WorkflowProperties `workflowProperties` sınıfı. Kodda `workflowProperties` kitaplığın veya listenin özelliklerine erişmek için nesnesini kullanın. Bir örnek için [bkz. Adım adım: İş akışı çözümü için SharePoint ve hata ayıklama.](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)

## <a name="debug-a-sharepoint-workflow-template"></a>İş akışı SharePoint hata ayıklama
 Bir iş akışı SharePoint diğer Web tabanlı projelerde hata ayıklamayla aynı şekilde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıkabilirsiniz. Hata ayıklayıcıyı başlatırken, uygun SharePoint Web sitesini açmak ve iş akışı şablonunu uygun kitaplık veya listeyle otomatik olarak ilişkilendirmek için SharePoint Özelleştirme Sihirbazı'nda belirttiğiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayarları kullanır.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ayrıca hata [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayıklayıcısınıw3wp.exe[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] *adlı işlemew3wp.exe.*

 İş akışını test etmek için el ile başlatmanız gerekir. daha fazla bilgi için, [hata ayıklama SharePoint çözümlerinde](../sharepoint/debugging-sharepoint-solutions.md)"hata ayıklama iş akışları" bölümüne bakın. Web uygulaması hata ayıklaması hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bkz. [hata ayıklama Web uygulamaları ve betiği](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>SharePoint iş akışı şablonu dağıtma
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint iş akışı projeleri diğer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projeler gibi dağıtılır. daha fazla bilgi için bkz. [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Genel yeniden kullanılabilir iş akışlarını içeri aktar
 SharePoint tasarımcı, siteye özgü yeniden kullanılabilir iş akışları oluşturmanın yanı sıra, herhangi bir SharePoint sitesi tarafından kullanılabilecek iş akışları olan *küresel olarak yeniden kullanılabilir iş akışları* oluşturmanıza olanak sağlar. ' Deki yeniden kullanılabilir yeniden kullanılabilir Iş akışı projesi, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] genel olarak kullanılabilir iş akışlarını içeri aktarmaz ancak, genel olarak yeniden kullanılabilir bir iş akışını yeniden kullanılabilir bir iş akışına dönüştürmek ya da iş akışını dönüştürülmeyen bir bildirim temelli iş akışı olarak içeri aktarmak için SharePoint tasarımcısını kullanabilirsiniz. daha fazla bilgi için bkz. [mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[izlenecek yol: SharePoint iş akışı çözümü oluşturma ve hatalarını ayıklama](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Basit bir iş akışı oluşturma ve hata ayıklama yoluyla adım adım size yol gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[İzlenecek yol: ilişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Ilişkilendirme ve başlatma formlarıyla eksiksiz bir tam özellikli iş akışı oluşturmak için adım adım size yol gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[İzlenecek yol: bir uygulama sayfasını bir iş akışına ekleme](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Konu başlığı altında derlemeler: iş akışına girilen verileri raporlayan ek bir *. aspx* uygulama sayfası ekleyerek [ilişkilendirme ve başlatma formları Ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) .|
|[İzlenecek yol: özel site iş akışı etkinliği oluşturma](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|İki temel görevin nasıl gerçekleştirileceğini gösterir: site düzeyinde iş akışı oluşturma ve özel bir iş akışı etkinliği oluşturma.|
|[izlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio içine aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint tasarımcısı 2010 ' de oluşturulan yeniden kullanılabilir bildirim temelli iş akışlarının bir SharePoint projesine nasıl içe aktarılacağını gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint çözümleri oluşturun ve hata ayıklayın](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)