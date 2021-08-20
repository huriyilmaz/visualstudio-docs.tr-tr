---
title: SharePoint iş akışı çözümleri oluşturma | Microsoft Docs
description: SharePoint web sitelerindeki belge yaşam döngüsünü ve liste öğelerini yöneten özel iş akışları oluşturmak için araçları kullanarak SharePoint iş akışı çözümleri oluşturun.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149461"
---
# <a name="create-sharepoint-workflow-solutions"></a>SharePoint iş akışı çözümleri oluşturma

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint Web sitesindeki belgelerin yaşam döngüsünü ve liste öğelerini yöneten özel iş akışları oluşturmanıza yardımcı olacak araçlar sağlar. Belirtilen öğeler bir tasarımcı, etkinlik denetimleri kümesi ve gerekli derleme başvuruları içerir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ayrıca, iş akışlarını oluşturmaya ve yapılandırmaya yardımcı olması için **SharePoint özelleştirme sihirbazını** da içerir.

SharePoint hakkında daha fazla bilgi için bkz. [Microsoft SharePoint ürünleri ve teknolojileri](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>SharePoint iş akışları
 bir SharePoint kitaplığına veya listesine bir iş akışı eklediğinizde, kitaplıktaki veya listedeki tüm öğelerde bir iş işlemini zorunlu kılabilirsiniz. Bir iş akışı, sistem veya kullanıcıların her öğe üzerinde gerçekleştirmesi gereken eylemleri (düzenlenecek öğeyi gönderme ve gözden geçirilmesi gibi) açıklar. *Etkinlik* olarak bilinen bu eylemler, iş akışının yapı taşlarıdır.

 içinde SharePoint iş akışları oluşturabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve bunları SharePoint bir Web sitesine dağıtabilirsiniz. SharePoint bir iş akışı dağıtıldıktan sonra, bunu bir kitaplık veya liste ile ilişkilendirirsiniz. Daha sonra otomatik olarak, bir işlem veya el ile bir kullanıcı tarafından başlatılabilir. iş akışı işlemi hakkında daha fazla bilgi için bkz. [Visual Studio kullanarak SharePoint iş akışları geliştirme](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>özel SharePoint iş akışları oluşturma
 iki SharePoint iş akışı projesi şu şekilde sunulmaktadır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] : **sıralı iş akışı** ve **durum makinesi iş akışı**.

 *Sıralı bir iş akışı* , bir dizi adımı temsil eder. Adımlar, son etkinlik tamamlanana kadar bir sonraki bir kez gerçekleştirilir. Sıralı iş akışları her zaman yürütmesinde tamamen sıralıdır. Dış olayları alabilecekleri ve paralel Logic akışları içerebildiğinden, yürütmenin tam sırası farklılık gösterebilir. Aşağıdaki çizimde sıralı bir iş akışı örneği gösterilmektedir.

 ![Sıralı Iş akışı](../sharepoint/media/sp-sequential.png "Sıralı İş Akışı")

 Bir *durum makinesi iş akışı* bir durumlar, geçişler ve eylemler kümesini temsil eder. Durum makinesi iş akışındaki adımlar zaman uyumsuz olarak yürütülür. Bu, bunlardan sonra bir tane gerçekleştirilmeyeceği anlamına gelir, bunun yerine eylemler ve durumlar tarafından tetiklenir. Bir durum başlangıç durumu olarak atanır ve sonra bir olaya bağlı olarak başka bir duruma geçiş yapılır. Durum makinesi, iş akışının sonunu belirleyen son bir duruma sahip olabilir. Aşağıdaki diyagramda bir durum makinesi iş akışı örneği gösterilmektedir.

 ![Durum makinesi Iş akışı](../sharepoint/media/sp-state.png "Durum Makinesi İş Akışı")

 İş akışı türleri hakkında daha fazla bilgi için bkz. [Iş akışı türleri](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Sihirbazı kullanma
 içinde bir SharePoint iş akışı projesi oluşturduğunuzda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , önce **SharePoint özelleştirme sihirbazında** ayarlarını belirtirsiniz. Sihirbaz bu ayarları **Çözüm Gezgini** bir proje oluşturmak için kullanır. bu proje, bir kod dosyası, iş akışını dağıtmak için kullanılan birkaç dosya ve özel bir SharePoint iş akışı oluşturmak için gereken derlemelere başvurular içerir.

 İş akışını oluşturduktan sonra, Özellikler penceresi özelliklerini değiştirebilirsiniz. iş akışı özelliklerinin çoğu doğrudan Özellikler penceresi değiştirilebilse de, bazıları değerlerini değiştirmek için üç nokta düğmesini (![ASP.NET Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")) tıklamanızı gerektirir. bu düğme **SharePoint özelleştirme sihirbazı**'nı yeniden başlatır. Özellik değeri değiştirildikten sonra, **son** düğmesini seçerek bunları sonlandırın.

> [!NOTE]
> **Iş akışı türü** özelliği salt okunurdur ve değiştirilemez. İş akışı türünü değiştirmek isterseniz, başka bir iş akışı oluşturmanız gerekir.

## <a name="design-a-sharepoint-workflow"></a>SharePoint iş akışı tasarlama
 iş işlemindeki tüm adımları tanımladıktan sonra, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint iş akışını tasarlamak için iş akışı tasarımcısını kullanın. Tasarımcıyı açmak için **Çözüm Gezgini** içinde Workflow1. cs veya Workflow1. vb öğesine çift tıklayın veya bu dosyalardan herhangi biri için kısayol menüsünü açın ve **Aç** öğesini seçin.

### <a name="activities"></a>Etkinlikler
 Bir iş akışı tasarlamak için, **araç kutusundan** tasarımcı 'daki bir *iş akışı çizelgesine* etkinlik ekleyin. Bir iş akışı zamanlaması, etkinlik sırasını, gerçekleştirilmesi gereken sırada içerir.

 İki tür etkinlik vardır:

- *Basit etkinlikler* , "1 gün için gecikme" veya "Web Hizmeti Başlat" gibi tek bir iş birimi gerçekleştirir.

- *Bileşik etkinlikler* diğer etkinlikleri içerir; Örneğin, koşullu bir etkinlik iki dal içerebilir.

  **Araç kutusunda** her iki etkinlik türü de mevcuttur.

  Etkinliklerin özellikleri, yöntemleri ve olayları olabilir. Bir etkinliğin özelliklerini ayarlamak için **Özellikler** penceresini kullanın.

  Özel bir etkinlik da oluşturabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: özel site iş akışı etkinliği oluşturma](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Etkinlikler **araç kutusu**'ndaki aşağıdaki sekmelerde düzenlenmiştir:

- **SharePoint Akışıyla**

- **Windows İş akışı v 3.0**

- **Windows İş akışı v 3.5**

  Tüm temel iş akışı etkinlikleri SharePoint tarafından desteklenmez. daha fazla bilgi için bkz. [Windows SharePoint Services genel bakış için iş akışı etkinlikleri](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>SharePoint iş akışı etkinlikleri
 **SharePoint iş akışı** sekmeleri ' de kullanım için özel etkinlikler içerir [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] . Bu etkinlikler belge yaşam döngüsü iş akışlarının geliştirilmesini basitleştirir ve kolaylaştırır. **SharePoint iş akışı** sekmesinde listelenen etkinlikler hakkında daha fazla bilgi için bkz. [Windows SharePoint Services genel bakış için iş akışı etkinlikleri](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Windows iş akışı etkinlikleri
 **Windows iş akışı** sekmeleri tarafından sunulan etkinlikleri içerir [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] . bu etkinlikleri, her türlü Windows iş akışı uygulamasının iş akışı zamanlamalarını oluşturmak için kullanabilirsiniz.

 **Windows iş akışları** sekmesinde listelenen etkinlikler hakkında daha fazla bilgi için, bkz. [Windows Workflow Foundation etkinlikler](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Windows Workflow Foundation hakkında daha fazla bilgi için bkz. [Windows Workflow Foundation genel bakış](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Tasarımcıda etkinliklerle çalışma
 iş akışı zamanlamanız, Windows iş akışı etkinliklerinin bir birleşimini ve SharePoint iş akışı etkinliklerini içerebilir.

 Tasarımcı, etkinlikleri doğru bir şekilde konumlandırmanıza ve yapılandırmanıza yardımcı olacak görsel ipuçları görüntüler. Bir etkinliği iş akışı zamanlaması üzerine sürüklediğinizde veya kopyaladığınızda Tasarımcı, iş akışındaki bu etkinlik için geçerli konumları gösteren yeşil artı işareti (+) simgelerini görüntüler. Bir etkinliği geçerli olmadığı bir konuma yerleştirebilirsiniz. Örneğin, bir Send etkinliğini bir dinleme etkinlik dalında ilk etkinlik olarak konumlandıramezsiniz. daha fazla bilgi için bkz. [SharePoint tasarımcı geliştirici merkezi](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>İş akışı sırasında bilgi toplama
 İş akışında önceden tanımlanmış zamanlarda kullanıcılardan bilgi toplamak isteyebilirsiniz. Formları veya öğe özelliklerini kullanarak bilgi toplayabilirsiniz.

### <a name="forms"></a>Formlar
 Formlar, sorular içeren iletişim kutularına benzer ve kullanıcıların yanıt vermesi için yollar sağlar.

 Bir iş akışında kullanılabilen dört tür form vardır:

- Kaldırma

- Başlatmak

- Değişiklik

- Görev

  Bunlar, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ilişkilendirme ve başlatma formları için öğe şablonları içerir. *İlişki formu* örneği, iş akışını yükleyen yöneticinin bir gider iş akışı için harcama limiti gibi iş akışıyla ilişkili parametreleri girmelerini sağlayan bir örnektir. Bir *başlatma formu* örneği, bir gider iş akışının kullanıcısına iş akışına harcadıkları miktarı girebilmenizi sağlayan bir örnektir. bu form türleri hakkında daha fazla bilgi için bkz. [SharePoint proje ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Öğe özellikleri
 ayrıca, SharePoint kitaplığı veya listesindeki bir öğenin özelliklerini kullanarak kullanıcılardan bilgi toplayabilirsiniz. Ana kod dosyası (Workflow1. cs veya Workflow1. vb), Microsoft 'un bir örneğini bildirir. SharePoint. Workflow. SPWorkflowActivationProperties. WorkflowProperties sınıfı adlı `workflowProperties` . `workflowProperties`Kod içindeki kitaplığın veya listenin özelliklerine erişmek için nesnesini kullanın. bir örnek için bkz. [izlenecek yol: SharePoint iş akışı çözümü oluşturma ve hatalarını ayıklama](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>SharePoint iş akışı şablonunda hata ayıklama
 SharePoint iş akışı projesinde hata ayıkladığınızda diğer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Web tabanlı projelerde hata ayıklaması yapabilirsiniz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]hata ayıklayıcıyı başlattığınızda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uygun SharePoint Web sitesini açmak için **SharePoint özelleştirme sihirbazında** belirttiğiniz ayarları kullanır ve iş akışı şablonunu uygun kitaplık veya liste ile otomatik olarak ilişkilendirir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcıyı [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] *w3wp.exe* adlı işleme iliştirir.

 İş akışını test etmek için el ile başlatmanız gerekir. Daha fazla bilgi için Hata Ayıklama ve Çözümler'de "İş Akışlarında [Hata Ayıklama" SharePoint bakın.](../sharepoint/debugging-sharepoint-solutions.md) Web uygulamasında hata ayıklama hakkında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] daha fazla bilgi için bkz. Web uygulamalarında ve [betikte hata ayıklama.](../debugger/how-to-enable-debugging-for-aspnet-applications.md)

## <a name="deploy-a-sharepoint-workflow-template"></a>İş akışı SharePoint dağıtma
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint iş akışı projeleri diğer iş akışı projeleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] gibi SharePoint dağıtır. Daha fazla bilgi için [bkz. Paket ve Dağıtım SharePoint.](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

## <a name="import-globally-reusable-workflows"></a>Genel olarak yeniden kullanılabilir iş akışlarını içeri aktarma
 SharePoint Designer, siteye özgü yeniden kullanılabilir iş akışları oluşturmaya ek olarak, herhangi bir site tarafından kullanılmaktadır iş akışları olan *genel* olarak yeniden kullanılabilir iş SharePoint sağlar. 'de Yeniden Kullanılabilir İş Akışını İçeri Aktar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projesi şu anda genel olarak yeniden kullanılabilir iş akışlarını içeri aktarmaz. Ancak, genel olarak yeniden SharePoint iş akışını yeniden kullanılabilir bir iş akışına dönüştürmek için SharePoint Designer'ı kullanabilir veya iş akışını, dönüştürülemeyen bildirimsiz bir iş akışı olarak içeri aktarabilirsiniz. Daha fazla bilgi için [bkz. Mevcut bir sitedeki öğeleri SharePoint.](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Adım adım kılavuz: İş akışı çözümü SharePoint oluşturma ve hata ayıklama](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Basit bir iş akışı oluşturma ve hata ayıklama konusunda size adım adım yol [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sağlar.|
|[Adım adım kılavuz: İlişki ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|İlişkileme ve Başlatma formlarını tamamlayan daha tam özellikli bir iş akışı oluşturmaya adım [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adım yol sağlar.|
|[Adım adım kılavuz: İş akışına uygulama sayfası ekleme](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Konu başlığında [derlemeler:](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) İş akışına girilen veriler üzerinde rapor oluşturan ek *bir .aspx* uygulama sayfası ekleyerek ilişkilendirme ve başlatma formlarına sahip bir iş akışı oluşturun.|
|[Adım adım kılavuz: Özel site iş akışı etkinliği oluşturma](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|İki önemli görevi nasıl gerçekleştireceklerini gösterir: site düzeyinde iş akışı oluşturma ve özel bir iş akışı etkinliği oluşturma.|
|[Adım adım kılavuz: SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint Designer 2010'da oluşturulan yeniden kullanılabilir bildirimli iş akışlarını bir SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Çözüm oluşturma ve SharePoint ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)