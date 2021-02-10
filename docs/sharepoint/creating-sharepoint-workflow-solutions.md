---
title: SharePoint Iş akışı çözümleri oluşturma | Microsoft Docs
description: SharePoint Web sitelerindeki belgelerin yaşam döngüsünü ve liste öğelerini yöneten özel iş akışları oluşturmak için araçları kullanarak SharePoint iş akışı çözümleri oluşturun.
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
ms.workload:
- office
ms.openlocfilehash: 28a5bc44b0f6fa04d32c574e9772369709736ddd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949083"
---
# <a name="create-sharepoint-workflow-solutions"></a>SharePoint iş akışı çözümleri oluşturma

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir SharePoint Web sitesindeki belgelerin yaşam döngüsünü ve liste öğelerini yöneten özel iş akışları oluşturmanıza yardımcı olacak araçlar sağlar. Belirtilen öğeler bir tasarımcı, etkinlik denetimleri kümesi ve gerekli derleme başvuruları içerir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca, iş akışlarını oluşturmaya ve yapılandırmaya yardımcı olması için **SharePoint Özelleştirme Sihirbazı**'nı da içerir.

SharePoint hakkında daha fazla bilgi için bkz. [Microsoft SharePoint ürünleri ve teknolojileri](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>SharePoint 'te iş akışları
 Bir SharePoint kitaplığına veya listesine bir iş akışı eklediğinizde, kitaplıktaki veya listedeki tüm öğelerde bir iş işlemini zorunlu kılabilirsiniz. Bir iş akışı, sistem veya kullanıcıların her öğe üzerinde gerçekleştirmesi gereken eylemleri (düzenlenecek öğeyi gönderme ve gözden geçirilmesi gibi) açıklar. *Etkinlik* olarak bilinen bu eylemler, iş akışının yapı taşlarıdır.

 ' De SharePoint iş akışları oluşturabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve bunları bir SharePoint Web sitesine dağıtabilirsiniz. Bir iş akışı SharePoint 'e dağıtıldıktan sonra, bunu bir kitaplık veya liste ile ilişkilendirirsiniz. Daha sonra otomatik olarak, bir işlem veya el ile bir kullanıcı tarafından başlatılabilir. İş akışı işlemi hakkında daha fazla bilgi için bkz. [Visual Studio kullanarak SharePoint iş akışlarını geliştirme](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Özel SharePoint iş akışları oluşturma
 Şu iki SharePoint iş akışı projesi kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] : **sıralı iş akışı** ve **durum makinesi iş akışı**.

 *Sıralı bir iş akışı* , bir dizi adımı temsil eder. Adımlar, son etkinlik tamamlanana kadar bir sonraki bir kez gerçekleştirilir. Sıralı iş akışları her zaman yürütmesinde tamamen sıralıdır. Dış olayları alabilecekleri ve paralel Logic akışları içerebildiğinden, yürütmenin tam sırası farklılık gösterebilir. Aşağıdaki çizimde sıralı bir iş akışı örneği gösterilmektedir.

 ![Sıralı Iş akışı](../sharepoint/media/sp-sequential.png "Sıralı Iş akışı")

 Bir *durum makinesi iş akışı* bir durumlar, geçişler ve eylemler kümesini temsil eder. Durum makinesi iş akışındaki adımlar zaman uyumsuz olarak yürütülür. Bu, bunlardan sonra bir tane gerçekleştirilmeyeceği anlamına gelir, bunun yerine eylemler ve durumlar tarafından tetiklenir. Bir durum başlangıç durumu olarak atanır ve sonra bir olaya bağlı olarak başka bir duruma geçiş yapılır. Durum makinesi, iş akışının sonunu belirleyen son bir duruma sahip olabilir. Aşağıdaki diyagramda bir durum makinesi iş akışı örneği gösterilmektedir.

 ![Durum makinesi Iş akışı](../sharepoint/media/sp-state.png "Durum makinesi Iş akışı")

 İş akışı türleri hakkında daha fazla bilgi için bkz. [Iş akışı türleri](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Sihirbazı kullanma
 İçinde bir SharePoint iş akışı projesi oluşturduğunuzda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , önce **SharePoint Özelleştirme Sihirbazı**'nda ayarlarını belirtirsiniz. Sihirbaz bu ayarları **Çözüm Gezgini** bir proje oluşturmak için kullanır. Bu proje, bir kod dosyası, iş akışını dağıtmak için kullanılan birkaç dosya ve özel bir SharePoint iş akışı oluşturmak için gereken derlemelere başvurular içerir.

 İş akışını oluşturduktan sonra, Özellikler penceresi özelliklerini değiştirebilirsiniz. İş akışı özelliklerinin çoğu doğrudan Özellikler penceresi değiştirilebilse de, bazıları değerlerini değiştirmek için üç nokta düğmesini (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) tıklamanızı gerektirir. Bu düğme **SharePoint Özelleştirme Sihirbazı 'nı** yeniden başlatır. Özellik değeri değiştirildikten sonra, **son** düğmesini seçerek bunları sonlandırın.

> [!NOTE]
> **Iş akışı türü** özelliği salt okunurdur ve değiştirilemez. İş akışı türünü değiştirmek isterseniz, başka bir iş akışı oluşturmanız gerekir.

## <a name="design-a-sharepoint-workflow"></a>SharePoint iş akışı tasarlama
 İş işlemindeki tüm adımları tanımladıktan sonra, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint iş akışını tasarlamak için iş akışı tasarımcısını kullanın. Tasarımcıyı açmak için **Çözüm Gezgini** içinde Workflow1.cs veya Workflow1. vb öğesine çift tıklayın veya bu dosyalardan herhangi biri için kısayol menüsünü açın ve **Aç** öğesini seçin.

### <a name="activities"></a>Etkinlikler
 Bir iş akışı tasarlamak için, **araç kutusundan** tasarımcı 'daki bir *iş akışı çizelgesine* etkinlik ekleyin. Bir iş akışı zamanlaması, etkinlik sırasını, gerçekleştirilmesi gereken sırada içerir.

 İki tür etkinlik vardır:

- *Basit etkinlikler* , "1 gün için gecikme" veya "Web Hizmeti Başlat" gibi tek bir iş birimi gerçekleştirir.

- *Bileşik etkinlikler* diğer etkinlikleri içerir; Örneğin, koşullu bir etkinlik iki dal içerebilir.

  **Araç kutusunda** her iki etkinlik türü de mevcuttur.

  Etkinliklerin özellikleri, yöntemleri ve olayları olabilir. Bir etkinliğin özelliklerini ayarlamak için **Özellikler** penceresini kullanın.

  Özel bir etkinlik da oluşturabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: özel site iş akışı etkinliği oluşturma](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Etkinlikler **araç kutusu**'ndaki aşağıdaki sekmelerde düzenlenmiştir:

- **SharePoint Iş akışı**

- **Windows Workflow v 3.0**

- **Windows Workflow v 3.5**

  Tüm temel iş akışı etkinlikleri SharePoint tarafından desteklenmez. Daha fazla bilgi için bkz. [Windows SharePoint hizmetlerine genel bakış Için Iş akışı etkinlikleri](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>SharePoint iş akışı etkinlikleri
 **SharePoint Iş akışı** sekmeleri ' de kullanım için özel etkinlikler içerir [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] . Bu etkinlikler belge yaşam döngüsü iş akışlarının geliştirilmesini basitleştirir ve kolaylaştırır. **SharePoint Iş akışı** sekmesinde listelenen etkinlikler hakkında daha fazla bilgi için bkz. [Windows SharePoint Services Için Iş akışı etkinlikleri genel bakış](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Windows iş akışı etkinlikleri
 **Windows Iş akışı** sekmeleri tarafından sunulan etkinlikleri içerir [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] . Bu etkinlikleri, herhangi bir tür Windows iş akışı uygulamasının iş akışı zamanlamalarını oluşturmak için kullanabilirsiniz.

 **Windows Iş akışları** sekmesinde listelenen etkinlikler hakkında daha fazla bilgi için bkz. [Windows Workflow Foundation etkinlikleri](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Windows Workflow Foundation hakkında daha fazla bilgi için bkz. [Windows Workflow Foundation genel bakış](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Tasarımcıda etkinliklerle çalışma
 İş akışı zamanlamanız, Windows Iş akışı etkinlikleri ve SharePoint Iş akışı etkinliklerinin bir birleşimini içerebilir.

 Tasarımcı, etkinlikleri doğru bir şekilde konumlandırmanıza ve yapılandırmanıza yardımcı olacak görsel ipuçları görüntüler. Bir etkinliği iş akışı zamanlaması üzerine sürüklediğinizde veya kopyaladığınızda Tasarımcı, iş akışındaki bu etkinlik için geçerli konumları gösteren yeşil artı işareti (+) simgelerini görüntüler. Bir etkinliği geçerli olmadığı bir konuma yerleştirebilirsiniz. Örneğin, bir Send etkinliğini bir dinleme etkinlik dalında ilk etkinlik olarak konumlandıramezsiniz. Daha fazla bilgi için bkz. [SharePoint Designer Geliştirici Merkezi](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>İş akışı sırasında bilgi toplama
 İş akışında önceden tanımlanmış zamanlarda kullanıcılardan bilgi toplamak isteyebilirsiniz. Formları veya öğe özelliklerini kullanarak bilgi toplayabilirsiniz.

### <a name="forms"></a>Formlar
 Formlar, sorular içeren iletişim kutularına benzer ve kullanıcıların yanıt vermesi için yollar sağlar.

 Bir iş akışında kullanılabilen dört tür form vardır:

- Kaldırma

- Başlatmak

- Değişiklik

- Görev

  Bunlar, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ilişkilendirme ve başlatma formları için öğe şablonları içerir. *İlişki formu* örneği, iş akışını yükleyen yöneticinin bir gider iş akışı için harcama limiti gibi iş akışıyla ilişkili parametreleri girmelerini sağlayan bir örnektir. Bir *başlatma formu* örneği, bir gider iş akışının kullanıcısına iş akışına harcadıkları miktarı girebilmenizi sağlayan bir örnektir. Bu tür formlar hakkında daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Öğe özellikleri
 Ayrıca, SharePoint kitaplığındaki veya listesindeki bir öğenin özelliklerini kullanarak kullanıcılardan bilgi toplayabilirsiniz. Ana kod dosyası (Workflow1.cs veya Workflow1. vb), adlı Microsoft. SharePoint. Workflow. SPWorkflowActivationProperties. WorkflowProperties sınıfının bir örneğini bildirir `workflowProperties` . `workflowProperties`Kod içindeki kitaplığın veya listenin özelliklerine erişmek için nesnesini kullanın. Bir örnek için bkz. [Izlenecek yol: SharePoint iş akışı çözümü oluşturma ve hata ayıklama](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>SharePoint iş akışı şablonunda hata ayıklama
 SharePoint iş akışı projesinde hata ayıkladığınızda, diğer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Web tabanlı projelerde hata ayıklaması yapabilirsiniz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Hata ayıklayıcıyı başlattığınızda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **SharePoint Özelleştirme Sihirbazı** 'nda belirttiğiniz ayarları kullanarak uygun SharePoint Web sitesini açın ve iş akışı şablonunu uygun kitaplık veya listeyle otomatik olarak ilişkilendirin. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcıyı [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] *w3wp.exe* adlı işleme iliştirir.

 İş akışını test etmek için el ile başlatmanız gerekir. Daha fazla bilgi için [SharePoint Çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md)konusunun "hata ayıklama iş akışları" bölümüne bakın. Web uygulaması hata ayıklaması hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bkz. [hata ayıklama Web uygulamaları ve betiği](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>SharePoint iş akışı şablonu dağıtma
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint iş akışı projeleri, tıpkı diğer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projeleri gibi dağıtılır. Daha fazla bilgi için bkz. [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Genel yeniden kullanılabilir iş akışlarını içeri aktar
 SharePoint Designer, siteye özgü yeniden kullanılabilir iş akışları oluşturmanın yanı sıra, herhangi bir SharePoint sitesi tarafından kullanılabilecek iş akışları olan *küresel olarak yeniden kullanılabilir iş akışları* oluşturmanıza olanak sağlar. ' Deki yeniden kullanılabilir yeniden kullanılabilir Iş akışı projesi, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] genel olarak kullanılabilir iş akışlarını içeri aktarmaz Ancak, genel olarak yeniden kullanılabilir bir iş akışını yeniden kullanılabilir bir iş akışına dönüştürmek ya da iş akışını Dönüştürülmeyen bir bildirim temelli iş akışı olarak içeri aktarmak için SharePoint Designer 'ı kullanabilirsiniz. Daha fazla bilgi için bkz. [mevcut bir SharePoint sitesinden öğeleri Içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: SharePoint iş akışı çözümü oluşturma ve hatalarını ayıklama](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Basit bir iş akışı oluşturma ve hata ayıklama yoluyla adım adım size yol gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[İzlenecek yol: ilişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Ilişkilendirme ve başlatma formlarıyla eksiksiz bir tam özellikli iş akışı oluşturmak için adım adım size yol gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[İzlenecek yol: bir uygulama sayfasını bir iş akışına ekleme](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Konu başlığı altında derlemeler: iş akışına girilen verileri raporlayan ek bir *. aspx* uygulama sayfası ekleyerek [ilişkilendirme ve başlatma formları Ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) .|
|[İzlenecek yol: özel site iş akışı etkinliği oluşturma](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|İki temel görevin nasıl gerçekleştirileceğini gösterir: site düzeyinde iş akışı oluşturma ve özel bir iş akışı etkinliği oluşturma.|
|[İzlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio 'ya aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint Designer 2010 ' de oluşturulan yeniden kullanılabilir bildirim temelli iş akışlarının bir SharePoint projesine nasıl içe aktarılacağını gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint çözümlerini derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)