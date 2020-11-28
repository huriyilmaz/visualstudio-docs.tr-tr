---
title: Mevcut bir SharePoint sitesinden öğeleri içeri aktarma | Microsoft Docs
description: SharePoint çözüm paketini Içeri aktar proje şablonunu kullanarak mevcut bir SharePoint sitesinden öğeleri içeri aktarın, böylece öğeleri yeni bir SharePoint çözümünde yeniden kullanabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ef77fb280021fcfb701a677bc9ce17ec26e39516
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304518"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Mevcut bir SharePoint sitesinden öğeleri içeri aktar
  Içeri aktarma SharePoint çözüm paketi proje şablonu, yeni bir SharePoint çözümündeki mevcut SharePoint sitelerinden içerik türleri ve alanlar gibi öğeleri yeniden kullanmanıza olanak sağlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Çoğu içeri aktarılan çözümü değişiklik yapmadan çalıştırabilmenize karşın, özellikle de herhangi bir öğeyi içe aktardıktan sonra değiştirirseniz dikkate alınması gereken bazı kısıtlamalar ve sorunlar vardır.

> [!NOTE]
> Yeniden kullanılabilir iş akışlarını içeri aktarmak için, yeniden kullanılabilir Iş akışı proje şablonunu Içeri aktarın. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)]Yeniden [kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md).

## <a name="supported-sharepoint-solutions"></a>Desteklenen SharePoint çözümleri
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , ve içinde oluşturulan çözümlerin içeri aktarılmasını tam olarak destekler [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , aşağıdaki uygulamalarda oluşturulan çözümlerin içeri aktarılmasını desteklemez:

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  Genellikle bu uygulamalar tarafından oluşturulan çözümleri başarılı bir şekilde içeri aktarabilirsiniz, ancak bu işlev sınanmamıştır ve desteklenmez.

## <a name="item-import-restrictions"></a>Öğe içeri aktarma kısıtlamaları
 Birçok SharePoint öğesi var olan bir *. wsp* dosyasından içeri aktarılabilir, ancak aşağıdaki öğeler desteklenmez ve değişikliklerin doğru şekilde çalışması gerekebilir:

- BDC varlıkları

- Kod iş akışı ilişkilendirme öğeleri

- Kod iş akışları

- Görsel Web bölümleri (. ascx)

- Web Hizmetleri (*. asmx*)

- İçerik türü bağlamaları

- Olay alıcıları

- Liste tanımları (şablonlar)

- Site tanımları

  Veya ' den bir çözümü dışarı [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] aktardığınızda [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , bu öğeler otomatik olarak *. wsp* dosyasından çıkarılır. Ancak, desteklenmeyen araçlardan oluşturulan diğer *. wsp* dosyaları bu öğeleri içerebilir. (Bu konunun önceki kısımlarında "desteklenen SharePoint çözümleri" bölümüne bakın.)

## <a name="what-happens-when-you-import-a-solution"></a>Bir çözümü içeri aktardığınızda ne olur?
 SharePoint çözüm paketini Içeri aktar şablonunu içeren bir çözümü içeri aktardığınızda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] *. wsp* dosyasının tüm içeriğini kopyalar ve içeri aktarılan öğeler ve bunların dosyaları arasında mümkün olduğunca çok sayıda ilişkilendirmeyi ve başvuruyu uzlaştırmaya çalışır.

 Tüm içeri aktarılan öğeler **Çözüm Gezgini** içindeki ilgili klasörlere kopyalar. Örneğin, içerik türleri klasör **içerik türleri** altında görünür ve liste örnekleri **liste örnekleri** altında görünür. İçeri aktarılan bir öğeyle ilişkili dosyalar da öğenin klasörüne kopyalanır. Örneğin, içeri aktarılan bir liste örneği modüller, formlar ve ASPX sayfalarını içerir.

### <a name="dependent-items"></a>Bağımlı öğeler
 SharePoint çözüm paketini Içeri aktarma Sihirbazı ' nda bir öğe seçerseniz ancak bağımlı öğeler ' i seçerseniz, bir ileti kutusu, içeri aktarmadan önce bağımlı öğelerin de seçili olması gerektiğini bildirir.

### <a name="what-are-features"></a>Özellikler nelerdir?
 SharePoint Designer kullanıcıları Çözüm Gezgini ' de içeri aktarılan çözümlerde *Özellikler* olarak adlandırılan beklenmeyen dosyaları görebilir **.** Özellikler SharePoint Designer çözümünde var olsa da, bunlar görünümden gizleniyor. Özellikler artık ' de görünür [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Özellikler, SharePoint öğeleri için kapsayıcılardır. Her bir özellik, içerdiği içerik türleri ve liste tanımları gibi her öğe için bir başvuru tutar. Çözümünüzü içeri aktardığınızda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tüm içeri aktarılan öğelerin özelliklerini ayarlar ve dosyalar için özellik-öğe ilişkilerini sürdürme girişimleri. Başvuruları çözülemeyen dosyalar **diğer Içeri aktarılan dosyalar** klasörüne konur.

 Özellikler hakkında daha fazla bilgi için bkz. [SharePoint çözümlerini geliştirme](../sharepoint/developing-sharepoint-solutions.md) ve [özelliklerle çalışma](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

### <a name="handle-special-cases"></a>Özel durumları işle
 Bazı durumlarda, Visual Studio bir öğeyi bağımlı dosyalarla mutabık hale alamaz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Çözemeyebilir tüm dosyalar, **Içeri aktarılan diğer dosyaların** klasörü altında görünür. Bunlara ek olarak, **DeploymentType** özellikleri **NoDeployment** olarak ayarlanır, böylece çözümle birlikte dağıtılmazlar.

 Örneğin, liste tanımı ExpenseForms 'u içeri aktarırsanız, bu ada sahip bir liste tanımı, *Elements.xml* ve *Schema.xml* dosyaları ile birlikte **Çözüm Gezgini** **liste tanımları** klasörü altında görüntülenir. Ancak, ilişkili ASPX ve HTML formları, **diğer Içeri aktarılan dosyalar** klasörü altında **ExpenseForms** adlı bir klasöre yerleştirilebilir. İçeri aktarmayı gerçekleştirmek için, bu dosyaları **Çözüm Gezgini** ' deki ExpenseForms liste tanımı altında taşıyın ve **NoDeployment** öğesinden **ElementFile** öğesine her bir dosya için **DeploymentType** özelliğini değiştirin.

 Olay alıcılarını içeri aktarırken, *Elements.xml* dosyası doğru konuma kopyalanır, ancak çözümü çözümle birlikte dağıtabilmesi için derlemeyi çözüm paketine el ile eklemeniz gerekir. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] Bunun nasıl yapılacağı, bkz. [nasıl yapılır: ek derlemeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 İş akışları içeri aktarılırken, InfoPath formları **diğer Içeri aktarılan dosyalar** klasörüne kopyalanır. *. Wsp* dosyası bir Web şablonu içeriyorsa, **Çözüm Gezgini** başlangıç sayfası olarak ayarlanır.

## <a name="import-fields-and-property-bags"></a>İçeri aktarma alanları ve özellik paketleri
 Birden çok alan içeren bir çözümü içeri aktardığınızda, tüm ayrı alan tanımları, **Çözüm Gezgini** **olarak adlandırılan bir** düğüm altında tek bir *Elements.xml* dosyasında birleştirilir. Benzer şekilde, tüm özellik paketi girdileri, **PropertyBag** adlı bir düğüm altında bir *Elements.xml* dosyasında birleştirilir.

 SharePoint 'teki alanlar, metin, Boolean veya arama gibi belirtilen bir veri türünün sütunlarıdır. Daha fazla bilgi için bkz. [Yapı bloğu: sütunlar ve alan türleri](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)). Özellik paketleri SharePoint 'teki nesnelere, bir gruptan SharePoint sitesindeki bir listeye özellikler eklemenize olanak tanır. Özellik paketleri, özellik adları ve değerlerinin karma tablosu olarak uygulanır. Daha fazla bilgi için bkz. [SharePoint yapılandırması](/previous-versions/msp-n-p/ff647766(v=pandp.10)) veya [SharePoint özellik paketi ayarlarını](https://archive.codeplex.com/?p=pbs)yönetme.

## <a name="delete-items-in-the-project"></a>Projedeki öğeleri silme
 SharePoint Çözümlerinde birçok öğenin bir veya daha fazla bağımlı öğesi vardır. Örneğin, liste örnekleri içerik türlerine ve içerik türlerine göre değişir. Bir SharePoint çözümünü içeri aktardıktan sonra, çözümü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dağıtmaya çalışana kadar çözümde bir öğe silerseniz ancak bağımlı öğeleri değil, herhangi bir başvuru sorunu bildirimi yapmaz. Örneğin, içeri aktarılan bir çözümün bir içerik türüne bağımlı bir liste örneği varsa ve bu içerik türünü silerseniz, dağıtımda bir hata oluşabilir. Bu hata, bağımlı öğe SharePoint sunucusunda yoksa oluşur. Benzer şekilde, silinen bir öğenin ilgili bir özellik paketi de varsa, bu özellik paketi girişlerini **propertybag** *Elements.xml* dosyasından silin. Bu nedenle, içeri aktarılan bir çözümden herhangi bir öğeyi siler ve dağıtım hataları alırsanız, herhangi bir bağımlı öğenin da silinip silinmediğini denetleyin.

## <a name="restore-missing-feature-attributes"></a>Eksik özellik özniteliklerini geri yükleme
 Çözümleri içeri aktarırken, içeri aktarılan özellik bildiriminde bazı isteğe bağlı özellik öznitelikleri atlanır. Bu öznitelikleri yeni özellik dosyasına geri yüklemek istiyorsanız, özgün özellik dosyasını yeni özellik bildirimiyle karşılaştırarak eksik öznitelikleri tanımlayabilir ve [nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)konusundaki yönergeleri izleyin.

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Dağıtım çakışması algılaması yerleşik liste örneklerinde gerçekleştirilmez
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] yerleşik liste örneklerinde (SharePoint ile birlikte gelen varsayılan liste örnekleri) dağıtım çakışması algılamayı gerçekleştirmez. SharePoint 'teki yerleşik liste örneklerinin üzerine yazılmasını önlemek için çakışma algılama işlemi yapılmaz. Yerleşik liste örnekleri hala dağıtılır veya güncellenir, ancak hiçbir şekilde silinmez veya üzerine yazılmaz. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint paketleme ve dağıtım sorunlarını giderin](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="import-sharepoint-server-2010-workflows"></a>SharePoint Server 2010 iş akışlarını içeri aktarma
 İçinde oluşturulan bir iş akışını içeri aktarırsanız [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , dağıttıktan sonra düzgün çalışmaz. İş akışı, bazı derlemeler eksik olduğundan ve iş  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] akışları Şu anda iş akışı çözümlerinde desteklenmeyen InfoPath formları içerdiğinden, iş akışı düzgün çalışmaz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Ancak, içeri aktarılan [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] iş akışları, derlemeler için başvurular ekleme [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] ve InfoPath formlarını yeniden bağlama gibi bazı öğeler düzeltildikten sonra düzgün şekilde çalışabilir. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint Server 2010 Iş akışları Içeri aktarılıyor](/sharepoint/dev/).

## <a name="item-name-character-limit"></a>Öğe adı karakter sınırı
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , yol da dahil olmak üzere proje ve proje öğesi adları için 260 toplam karakter sınırına sahiptir. Bir çözümü içeri aktarırken, bir öğe adı bu sınırı aşarsa, şu hatayı alırsınız:

 **Belirtilen yol, dosya adı veya her ikisi çok uzun. Tam dosya adı 260 karakterden az olmalıdır ve dizin adı 248 karakterden az olmalıdır.**

 Bu hatayı aldığınızda, öğe oluşturulmaz. Bu sorun çoğu zaman içeri aktarılan modüllerle oluşur. Bu sorundan kaçınmak için şunları yapın:

- Projeniz için **Yeni Proje Ekle** iletişim kutusuna girdiğiniz kısa adları kullanın.

- Yolu kısaltmak için, bir konumda kök klasöre yakın bir yerde oluşturun.

## <a name="the-sharepointproductversion-attribute"></a>SharePointProductVersion özniteliği
 Veya gibi SharePoint 'in önceki bir sürümünde oluşturulmuş bir çözümü içeri aktarırsanız [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] , paket bildirimindeki SharePointProductVersion öznitelik değerini 12,0 olarak değiştirin veya tüm Içeri aktarılan Web sayfalarına bir betik Yöneticisi denetimi ekleyin ve sharepointproductversion 'ı 14,0 olarak bırakın. Aksi takdirde, içeri aktarılan Web formları SharePoint 'te görüntülenmez.

### <a name="background"></a>Arka plan
 Ve içindeki çözümler [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] , [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] SharePointProductVersion adlı bir özniteliği içerir. SharePoint, çözüm için tasarlanan SharePoint sürümünü belirlemekte bu özniteliği paket bildirimlerinde kullanır. İki geçerli değer 12,0 ve 14,0 ' dir. 12,0 değeri, öğenin veya için tasarlandığını belirtir [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] ; 14,0 değeri öğenin veya için tasarlandığını gösterir [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 ASPX sayfalarını işlerken gelişmiş güvenlik için [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] Tüm aspx veya ana sayfaların bir betik Yöneticisi denetimi içermesini gerektirir. Betik Yöneticisi hakkında daha fazla bilgi için bkz. [ScriptManager denetimine genel bakış](/previous-versions/bb398863(v=vs.140)). Komut dosyası Yöneticisi denetimi ve ' de kullanılamadığından, bir veya ' a [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] yükseltilen herhangi bir [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] sayfaya eklenmelidir [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] . Standart ana sayfa kullanan ASPX sayfaları, zaten standart ana sayfaya eklenmiş olduğundan bir betik Yöneticisi denetimi gerektirmez. Ancak, bir ana sayfa kullanmayan veya özel ana sayfa kullanan ASPX sayfaları, veya içinde çalışmak için bir betik denetimi eklememelidir [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] Tüm yeni projelerin SharePointProductVersion özniteliği 14,0 olarak ayarlandığı için bir veya projesini içeri aktardığınızda bir betik Yöneticisi denetiminin yokluğu bir sorun olabilir. Bir Web formu olan yükseltilen bir projeyi bir betik Yöneticisi olmadan dağıtırsanız, form SharePoint 'te görüntülenmez.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: mevcut bir SharePoint sitesinden öğeleri Içeri aktarma](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [İzlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio 'ya aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
