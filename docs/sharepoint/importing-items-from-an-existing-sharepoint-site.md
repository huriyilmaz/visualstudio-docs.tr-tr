---
title: mevcut bir SharePoint sitesinden öğeleri içeri aktarma | Microsoft Docs
description: mevcut bir SharePoint sitesinden öğeleri içeri aktarma SharePoint çözüm paketi proje şablonuyla içeri aktarın, böylece öğeleri yeni bir SharePoint çözümünde yeniden kullanabilirsiniz.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 752e65412cc7ee7b3179f47ecd27caaf4e088822
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726753"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>mevcut bir SharePoint sitesinden öğeleri içeri aktar
  içeri aktarma SharePoint çözüm paketi proje şablonu, yeni bir SharePoint çözümünde mevcut SharePoint sitelerinden içerik türleri ve alanlar gibi öğeleri yeniden kullanmanıza olanak tanır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Çoğu içeri aktarılan çözümü değişiklik yapmadan çalıştırabilmenize karşın, özellikle de herhangi bir öğeyi içe aktardıktan sonra değiştirirseniz dikkate alınması gereken bazı kısıtlamalar ve sorunlar vardır.

> [!NOTE]
> Yeniden kullanılabilir iş akışlarını içeri aktarmak için, yeniden kullanılabilir Iş akışı proje şablonunu Içeri aktarın. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)]Yeniden [kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md).

## <a name="supported-sharepoint-solutions"></a>desteklenen SharePoint çözümleri
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , ve içinde oluşturulan çözümlerin içeri aktarılmasını tam olarak destekler [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , aşağıdaki uygulamalarda oluşturulan çözümlerin içeri aktarılmasını desteklemez:

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint tasarımcısı 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  Genellikle bu uygulamalar tarafından oluşturulan çözümleri başarılı bir şekilde içeri aktarabilirsiniz, ancak bu işlev sınanmamıştır ve desteklenmez.

## <a name="item-import-restrictions"></a>Öğe içeri aktarma kısıtlamaları
 birçok SharePoint öğesi var olan bir *. wsp* dosyasından içeri aktarılabilir, ancak aşağıdaki öğeler desteklenmez ve değişikliklerin doğru şekilde çalışması gerekebilir:

- BDC varlıkları

- Kod iş akışı ilişkilendirme öğeleri

- Kod iş akışları

- Görsel Web bölümleri (. ascx)

- Web Hizmetleri (*. asmx*)

- İçerik türü bağlamaları

- Olay alıcıları

- Liste tanımları (şablonlar)

- Site tanımları

  Veya ' den bir çözümü dışarı [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] aktardığınızda [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , bu öğeler otomatik olarak *. wsp* dosyasından çıkarılır. Ancak, desteklenmeyen araçlardan oluşturulan diğer *. wsp* dosyaları bu öğeleri içerebilir. (bu konunun önceki kısımlarında "desteklenen SharePoint çözümleri" bölümüne bakın.)

## <a name="what-happens-when-you-import-a-solution"></a>Bir çözümü içeri aktardığınızda ne olur?
 içeri aktarma SharePoint çözüm paketi şablonuyla bir çözümü içeri aktardığınızda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] *. wsp* dosyasının tüm içeriğini kopyalar ve içeri aktarılan öğeler ve bunların dosyaları arasında çok sayıda ilişkilendirmeyi ve başvuruyu mümkün olduğunca korur.

 Tüm içeri aktarılan öğeler **Çözüm Gezgini** içindeki ilgili klasörlere kopyalar. Örneğin, içerik türleri klasör **içerik türleri** altında görünür ve liste örnekleri **liste örnekleri** altında görünür. İçeri aktarılan bir öğeyle ilişkili dosyalar da öğenin klasörüne kopyalanır. Örneğin, içeri aktarılan bir liste örneği modüller, formlar ve ASPX sayfalarını içerir.

### <a name="dependent-items"></a>Bağımlı öğeler
 içeri aktarma SharePoint çözüm paketi sihirbazı ' nda bir öğe seçerseniz ancak bağımlı öğeleri yoksa, bir ileti kutusu, içeri aktarmadan önce bağımlı öğelerin de seçilmesi gerektiğini bildirir.

### <a name="what-are-features"></a>Özellikler nelerdir?
 SharePoint Tasarımcı kullanıcıları Çözüm Gezgini ' de içeri aktarılan çözümlerde, *Özellikler* olarak adlandırılan beklenmeyen dosyaları görebilir **.** SharePoint tasarımcı çözümünde özellikler var olsa da, bunlar görünümden gizleniyor. Özellikler artık ' de görünür [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 özellikler SharePoint öğeleri için kapsayıcılardır. Her bir özellik, içerdiği içerik türleri ve liste tanımları gibi her öğe için bir başvuru tutar. Çözümünüzü içeri aktardığınızda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tüm içeri aktarılan öğelerin özelliklerini ayarlar ve dosyalar için özellik-öğe ilişkilerini sürdürme girişimleri. Başvuruları çözülemeyen dosyalar **diğer Içeri aktarılan dosyalar** klasörüne konur.

 özellikler hakkında daha fazla bilgi için bkz. [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md) ve [özelliklerle çalışma](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

### <a name="handle-special-cases"></a>Özel durumları işle
 bazı durumlarda Visual Studio bir öğeyi bağımlı dosyalarla mutabık kılınamaz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Çözemeyebilir tüm dosyalar, **Içeri aktarılan diğer dosyaların** klasörü altında görünür. Bunlara ek olarak, **DeploymentType** özellikleri **NoDeployment** olarak ayarlanır, böylece çözümle birlikte dağıtılmazlar.

 Örneğin, liste tanımı ExpenseForms 'u içeri aktarırsanız, bu ada sahip bir liste tanımı, *Elements.xml* ve *Schema.xml* dosyaları ile birlikte **Çözüm Gezgini** **liste tanımları** klasörü altında görüntülenir. Ancak, ilişkili ASPX ve HTML formları, **diğer Içeri aktarılan dosyalar** klasörü altında **ExpenseForms** adlı bir klasöre yerleştirilebilir. İçeri aktarmayı gerçekleştirmek için, bu dosyaları **Çözüm Gezgini** ' deki ExpenseForms liste tanımı altında taşıyın ve **NoDeployment** öğesinden **ElementFile** öğesine her bir dosya için **DeploymentType** özelliğini değiştirin.

 Olay alıcılarını içeri aktarırken, *Elements.xml* dosyası doğru konuma kopyalanır, ancak çözümü çözümle birlikte dağıtabilmesi için derlemeyi çözüm paketine el ile eklemeniz gerekir. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] Bunun nasıl yapılacağı, bkz. [nasıl yapılır: ek derlemeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 İş akışları içeri aktarılırken, InfoPath formları **diğer Içeri aktarılan dosyalar** klasörüne kopyalanır. *. Wsp* dosyası bir Web şablonu içeriyorsa, **Çözüm Gezgini** başlangıç sayfası olarak ayarlanır.

## <a name="import-fields-and-property-bags"></a>İçeri aktarma alanları ve özellik paketleri
 Birden çok alan içeren bir çözümü içeri aktardığınızda, tüm ayrı alan tanımları, **Çözüm Gezgini** **olarak adlandırılan bir** düğüm altında tek bir *Elements.xml* dosyasında birleştirilir. Benzer şekilde, tüm özellik paketi girdileri, **PropertyBag** adlı bir düğüm altında bir *Elements.xml* dosyasında birleştirilir.

 SharePoint alanlar, metin, Boolean veya arama gibi belirtilen bir veri türünün sütunlarıdır. Daha fazla bilgi için bkz. [Yapı bloğu: sütunlar ve alan türleri](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)). özellik paketleri SharePoint, bir gruptaki her şey SharePoint sitesindeki bir listeye özellikler eklemenize olanak tanır. Özellik paketleri, özellik adları ve değerlerinin karma tablosu olarak uygulanır. daha fazla bilgi için bkz. [SharePoint yapılandırmayı yönetme](/previous-versions/msp-n-p/ff647766(v=pandp.10)) veya [özellik paketi Ayarlar SharePoint](https://archive.codeplex.com/?p=pbs).

## <a name="delete-items-in-the-project"></a>Projedeki öğeleri silme
 SharePoint çözümlerinde çoğu öğenin bir veya daha fazla bağımlı öğesi vardır. Örneğin, liste örnekleri içerik türlerine ve içerik türlerine göre değişir. bir SharePoint çözümünü içeri aktardıktan sonra, çözümü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dağıtmaya çalışana kadar çözümde bir öğe silerseniz ancak bağımlı öğeleri değil, herhangi bir başvuru sorunu hakkında sizi bilgilendirmez. Örneğin, içeri aktarılan bir çözümün bir içerik türüne bağımlı bir liste örneği varsa ve bu içerik türünü silerseniz, dağıtımda bir hata oluşabilir. SharePoint sunucuda bağımlı öğe yoksa hata oluşur. Benzer şekilde, silinen bir öğenin ilgili bir özellik paketi de varsa, bu özellik paketi girişlerini **propertybag** *Elements.xml* dosyasından silin. Bu nedenle, içeri aktarılan bir çözümden herhangi bir öğeyi siler ve dağıtım hataları alırsanız, herhangi bir bağımlı öğenin da silinip silinmediğini denetleyin.

## <a name="restore-missing-feature-attributes"></a>Eksik özellik özniteliklerini geri yükleme
 Çözümleri içeri aktarırken, içeri aktarılan özellik bildiriminde bazı isteğe bağlı özellik öznitelikleri atlanır. bu öznitelikleri yeni özellik dosyasına geri yüklemek istiyorsanız, özgün özellik dosyasını yeni özellik bildirimi ile karşılaştırarak eksik öznitelikleri tanımlayabilir ve [nasıl yapılır: özelleştirme SharePoint özelliği](../sharepoint/how-to-customize-a-sharepoint-feature.md)konusundaki yönergeleri izleyin.

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Dağıtım çakışması algılaması yerleşik liste örneklerinde gerçekleştirilmez
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]yerleşik liste örneklerinde (yani, SharePoint gelen varsayılan liste örneklerinde) dağıtım çakışması algılamayı gerçekleştirmez. SharePoint üzerindeki yerleşik liste örneklerinin üzerine yazılmasını önlemek için çakışma algılama işlemi yapılmaz. Yerleşik liste örnekleri hala dağıtılır veya güncellenir, ancak hiçbir şekilde silinmez veya üzerine yazılmaz. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][paketleme ve dağıtım SharePoint sorun giderin](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="import-sharepoint-server-2010-workflows"></a>SharePoint Server 2010 iş akışlarını içeri aktarma
 İçinde oluşturulan bir iş akışını içeri aktarırsanız [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , dağıttıktan sonra düzgün çalışmaz. İş akışı, bazı derlemeler eksik olduğundan ve iş  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] akışları Şu anda iş akışı çözümlerinde desteklenmeyen InfoPath formları içerdiğinden, iş akışı düzgün çalışmaz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Ancak, içeri aktarılan [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] iş akışları, derlemeler için başvurular ekleme [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] ve InfoPath formlarını yeniden bağlama gibi bazı öğeler düzeltildikten sonra düzgün şekilde çalışabilir. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint Server 2010 iş akışları içeri aktarılıyor](/sharepoint/dev/).

## <a name="item-name-character-limit"></a>Öğe adı karakter sınırı
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , yol da dahil olmak üzere proje ve proje öğesi adları için 260 toplam karakter sınırına sahiptir. Bir çözümü içeri aktarırken, bir öğe adı bu sınırı aşarsa, şu hatayı alırsınız:

 **Belirtilen yol, dosya adı veya her ikisi çok uzun. Tam dosya adı 260 karakterden az olmalıdır ve dizin adı 248 karakterden az olmalıdır.**

 Bu hatayı aldığınızda, öğe oluşturulmaz. Bu sorun çoğu zaman içeri aktarılan modüllerle oluşur. Bu sorundan kaçınmak için şunları yapın:

- **yeni Project ekle** iletişim kutusuna girdiğinizde projeniz için kısa adlar kullanın.

- Yolu kısaltmak için, bir konumda kök klasöre yakın bir yerde oluşturun.

## <a name="the-sharepointproductversion-attribute"></a>SharePointProductVersion özniteliği
 ya da gibi SharePoint önceki bir sürümünde oluşturulmuş bir çözümü içeri aktarırsanız [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] , paket bildirimindeki sharepointproductversion öznitelik değerini 12,0 olarak değiştirin veya tüm içeri aktarılan Web sayfalarına bir betik yöneticisi denetimi ekleyin ve sharepointproductversion öğesini 14,0 olarak bırakın. Aksi halde, içeri aktarılan Web formları SharePoint görüntülenmez.

### <a name="background"></a>Arka Plan
 Ve içindeki çözümler [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] , [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] SharePointProductVersion adlı bir özniteliği içerir. SharePoint, çözüm için tasarlanan SharePoint sürümünü öğrenmek için bu özniteliği paket bildirimlerinde kullanır. İki geçerli değer 12,0 ve 14,0 ' dir. 12,0 değeri, öğenin veya için tasarlandığını belirtir [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] ; 14,0 değeri öğenin veya için tasarlandığını gösterir [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 ASPX sayfalarını işleme sırasında gelişmiş güvenlik için ve tüm ASPX veya ana sayfaların bir [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] betik yöneticisi denetimi içermesi gerekir. Betik yöneticisi hakkında daha fazla bilgi için bkz. [ScriptManager Denetimine Genel Bakış.](/previous-versions/bb398863(v=vs.140)) betik yöneticisi denetimi ve içinde kullanılabilir olduğundan, veya sürümüne yükseltilen [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] herhangi bir veya sayfaya bir tane [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] eklenmiştir. Standart ana sayfa kullanan ASPX sayfaları için betik yöneticisi denetimi gerekli değildir çünkü standart ana sayfaya zaten bir tane eklenir. Ancak, bir ana sayfa kullanmayan veya özel bir ana sayfa kullanan ASPX sayfalarının veya içinde çalışması için bir betik denetimi eklemesi [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] gerekir.

 Tüm yeni projelerin [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] SharePointProductVersion özniteliği 14.0 olarak ayarlanmış olduğundan, bir veya projesini içine aktarıyorken betik yöneticisi denetimi olmaması sorun [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] olabilir. Betik yöneticisi olmadan Web formu olan yükseltilmiş bir projeyi dağıtırsanız, form bir web SharePoint.

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: Mevcut bir siteden öğeleri SharePoint aktarma](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [Adım adım kılavuz: SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Nasıl olur: Bir SharePoint projesine mevcut bir BDC SharePoint ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
