---
title: Mevcut bir SharePoint sitesinden öğeleri içeri aktarma | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 820e7c6f2ac7ea3e65e2156f33464bec96fce091
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982577"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Mevcut bir SharePoint sitesinden öğeleri içeri aktar
  SharePoint çözüm paketi Içeri aktarma projesi şablonu, yeni bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint çözümünde mevcut SharePoint sitelerinden içerik türleri ve alanlar gibi öğeleri yeniden kullanmanıza olanak sağlar. Çoğu içeri aktarılan çözümü değişiklik yapmadan çalıştırabilmenize karşın, özellikle de herhangi bir öğeyi içe aktardıktan sonra değiştirirseniz dikkate alınması gereken bazı kısıtlamalar ve sorunlar vardır.

> [!NOTE]
> Yeniden kullanılabilir iş akışlarını içeri aktarmak için, yeniden kullanılabilir Iş akışı proje şablonunu Içeri aktarın. yeniden [kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md)[!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)].

## <a name="supported-sharepoint-solutions"></a>Desteklenen SharePoint çözümleri
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]oluşturulan çözümlerin içeri aktarılmasını tam olarak destekler.

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], aşağıdaki uygulamalarda oluşturulan çözümlerin içeri aktarılmasını desteklemez:

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

- Web Hizmetleri ( *. asmx*)

- İçerik türü bağlamaları

- Olay alıcıları

- Liste tanımları (şablonlar)

- Site tanımları

  [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] veya [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]bir çözümü dışarı aktardığınızda, bu öğeler otomatik olarak *. wsp* dosyasından çıkarılır. Ancak, desteklenmeyen araçlardan oluşturulan diğer *. wsp* dosyaları bu öğeleri içerebilir. (Bu konunun önceki kısımlarında "desteklenen SharePoint çözümleri" bölümüne bakın.)

## <a name="what-happens-when-you-import-a-solution"></a>Bir çözümü içeri aktardığınızda ne olur?
 Içeri aktarma SharePoint çözüm paketi şablonuyla bir çözümü içeri aktardığınızda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] *. wsp* dosyasının tüm içeriğini kopyalar ve içeri aktarılan öğeler ve bunların dosyaları arasında çok sayıda ilişkilendirmeyi ve başvuruyu aynı şekilde tutmaya çalışır üç.

 Tüm içeri aktarılan öğeler **Çözüm Gezgini**içindeki ilgili klasörlere kopyalar. Örneğin, içerik türleri klasör **içerik türleri** altında görünür ve liste örnekleri **liste örnekleri**altında görünür. İçeri aktarılan bir öğeyle ilişkili dosyalar da öğenin klasörüne kopyalanır. Örneğin, içeri aktarılan bir liste örneği modüller, formlar ve ASPX sayfalarını içerir.

### <a name="dependent-items"></a>Bağımlı öğeler
 SharePoint çözüm paketini Içeri aktarma Sihirbazı ' nda bir öğe seçerseniz ancak bağımlı öğeler ' i seçerseniz, bir ileti kutusu, içeri aktarmadan önce bağımlı öğelerin de seçili olması gerektiğini bildirir.

### <a name="what-are-features"></a>Özellikler nelerdir?
 SharePoint Designer kullanıcıları Çözüm Gezgini ' de içeri aktarılan çözümlerde *Özellikler*olarak adlandırılan beklenmeyen dosyaları görebilir **.** Özellikler SharePoint Designer çözümünde var olsa da, bunlar görünümden gizleniyor. Özellikler artık [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]görünür.

 Özellikler, SharePoint öğeleri için kapsayıcılardır. Her bir özellik, içerdiği içerik türleri ve liste tanımları gibi her öğe için bir başvuru tutar. Çözümünüzü içeri aktardığınızda, tüm içeri aktarılan öğelerin özelliklerini ayarlar ve dosyalar için özellik-öğe ilişkilerini sürdürme girişimleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Başvuruları çözülemeyen dosyalar **diğer Içeri aktarılan dosyalar** klasörüne konur.

 Özellikler hakkında daha fazla bilgi için bkz. [SharePoint çözümlerini geliştirme](../sharepoint/developing-sharepoint-solutions.md) ve [özelliklerle çalışma](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

### <a name="handle-special-cases"></a>Özel durumları işle
 Bazı durumlarda, Visual Studio bir öğeyi bağımlı dosyalarla mutabık hale alamaz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözemeyebilir tüm dosyalar, **Içeri aktarılan diğer dosyaların**klasörü altında görünür. Bunlara ek olarak, **DeploymentType** özellikleri **NoDeployment** olarak ayarlanır, böylece çözümle birlikte dağıtılmazlar.

 Örneğin, liste tanımı ExpenseForms 'u içeri aktarırsanız, bu ada sahip bir liste tanımı, *öğeleri. xml* ve *Schema. xml* dosyaları Ile birlikte **Çözüm Gezgini** içindeki **liste tanımları** klasörü altında görüntülenir. Ancak, ilişkili ASPX ve HTML formları, **diğer Içeri aktarılan dosyalar** klasörü altında **ExpenseForms** adlı bir klasöre yerleştirilebilir. İçeri aktarmayı gerçekleştirmek için, bu dosyaları **Çözüm Gezgini** ' deki ExpenseForms liste tanımı altında taşıyın ve **NoDeployment** öğesinden **ElementFile**öğesine her bir dosya için **DeploymentType** özelliğini değiştirin.

 Olay alıcılarını içeri aktarırken, *Elements. xml* dosyası doğru konuma kopyalanır, ancak çözümle birlikte dağıtım için derlemeyi çözüm paketine el ile eklemeniz gerekir. Bunun nasıl yapılacağını [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)], bkz. [nasıl yapılır: ek derlemeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 İş akışları içeri aktarılırken, InfoPath formları **diğer Içeri aktarılan dosyalar** klasörüne kopyalanır. *. Wsp* dosyası bir Web şablonu içeriyorsa, **Çözüm Gezgini**başlangıç sayfası olarak ayarlanır.

## <a name="import-fields-and-property-bags"></a>İçeri aktarma alanları ve özellik paketleri
 Birden çok alan içeren bir çözümü içeri aktardığınızda, tüm ayrı alan tanımları **Çözüm Gezgini** **alanları**içindeki bir düğüm altında tek bir *öğeler. xml* dosyasında birleştirilir. Benzer şekilde, tüm özellik paketi girdileri, **PropertyBag**adlı bir düğüm altında bulunan bir *Elements. xml* dosyasında birleştirilir.

 SharePoint 'teki alanlar, metin, Boolean veya arama gibi belirtilen bir veri türünün sütunlarıdır. Daha fazla bilgi için bkz. [Yapı bloğu: sütunlar ve alan türleri](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)). Özellik paketleri SharePoint 'teki nesnelere, bir gruptan SharePoint sitesindeki bir listeye özellikler eklemenize olanak tanır. Özellik paketleri, özellik adları ve değerlerinin karma tablosu olarak uygulanır. Daha fazla bilgi için bkz. [SharePoint yapılandırması](/previous-versions/msp-n-p/ff647766(v=pandp.10)) veya [SharePoint özellik paketi ayarlarını](https://archive.codeplex.com/?p=pbs)yönetme.

## <a name="delete-items-in-the-project"></a>Projedeki öğeleri silme
 SharePoint Çözümlerinde birçok öğenin bir veya daha fazla bağımlı öğesi vardır. Örneğin, liste örnekleri içerik türlerine ve içerik türlerine göre değişir. Bir SharePoint çözümünü içeri aktardıktan sonra, çözümü dağıtmaya çalışana kadar çözümdeki bir öğeyi silmeniz durumunda değil, çözüm sorunlarından haberdar değildir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Örneğin, içeri aktarılan bir çözümün bir içerik türüne bağımlı bir liste örneği varsa ve bu içerik türünü silerseniz, dağıtımda bir hata oluşabilir. Bu hata, bağımlı öğe SharePoint sunucusunda yoksa oluşur. Benzer şekilde, silinen bir öğenin ilgili bir özellik paketi de varsa, bu özellik paketi girdilerini **propertytorler** *Elements. xml* dosyasından silin. Bu nedenle, içeri aktarılan bir çözümden herhangi bir öğeyi siler ve dağıtım hataları alırsanız, herhangi bir bağımlı öğenin da silinip silinmediğini denetleyin.

## <a name="restore-missing-feature-attributes"></a>Eksik özellik özniteliklerini geri yükleme
 Çözümleri içeri aktarırken, içeri aktarılan özellik bildiriminde bazı isteğe bağlı özellik öznitelikleri atlanır. Bu öznitelikleri yeni özellik dosyasına geri yüklemek istiyorsanız, özgün özellik dosyasını yeni özellik bildirimiyle karşılaştırarak eksik öznitelikleri tanımlayabilir ve [nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)konusundaki yönergeleri izleyin.

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Dağıtım çakışması algılaması yerleşik liste örneklerinde gerçekleştirilmez
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], yerleşik liste örneklerinde (SharePoint ile birlikte gelen varsayılan liste örnekleri) dağıtım çakışması algılamayı gerçekleştirmez. SharePoint 'teki yerleşik liste örneklerinin üzerine yazılmasını önlemek için çakışma algılama işlemi yapılmaz. Yerleşik liste örnekleri hala dağıtılır veya güncellenir, ancak hiçbir şekilde silinmez veya üzerine yazılmaz. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint paketleme ve dağıtım sorunlarını giderin](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="import-sharepoint-server-2010-workflows"></a>SharePoint Server 2010 iş akışlarını içeri aktarma
 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]oluşturulan bir iş akışını içeri aktarırsanız, dağıttıktan sonra düzgün çalışmaz. Bazı derlemeler olmadığından ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] iş akışları, şu anda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı çözümlerinde desteklenmeyen InfoPath formları içerdiğinden iş akışı düzgün çalışmaz. Ancak, içeri aktarılan [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] iş akışları, [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] derlemelerine başvuru ekleme ve InfoPath formlarını yeniden bağlama gibi bazı öğeleri düzelttikten sonra düzgün şekilde çalışabilir. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint Server 2010 Iş akışlarını Içeri aktarma](/sharepoint/dev/).

## <a name="item-name-character-limit"></a>Öğe adı karakter sınırı
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], proje ve proje öğesi adları için yol dahil 260 toplam karakter sınırı vardır. Bir çözümü içeri aktarırken, bir öğe adı bu sınırı aşarsa, şu hatayı alırsınız:

 **Belirtilen yol, dosya adı veya her ikisi çok uzun. Tam dosya adı 260 karakterden az olmalıdır ve dizin adı 248 karakterden az olmalıdır.**

 Bu hatayı aldığınızda, öğe oluşturulmaz. Bu sorun çoğu zaman içeri aktarılan modüllerle oluşur. Bu sorundan kaçınmak için şunları yapın:

- Projeniz için **Yeni Proje Ekle** iletişim kutusuna girdiğiniz kısa adları kullanın.

- Yolu kısaltmak için, bir konumda kök klasöre yakın bir yerde oluşturun.

## <a name="the-sharepointproductversion-attribute"></a>SharePointProductVersion özniteliği
 SharePoint 'in daha önceki bir sürümünde oluşturulan [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] veya [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]gibi bir çözümü içeri aktarırsanız, paket bildirimindeki SharePointProductVersion öznitelik değerini 12,0 olarak değiştirin ya da tüm içeri aktarılan Web sayfalarına bir betik Yöneticisi denetimi ekleyin ve şu komutu bırakın SharePointProductVersion 14,0 olarak ayarlanmıştır. Aksi takdirde, içeri aktarılan Web formları SharePoint 'te görüntülenmez.

### <a name="background"></a>Arka Plan
 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] çözümleri, SharePointProductVersion adlı bir öznitelik içerir. SharePoint, çözüm için tasarlanan SharePoint sürümünü belirlemekte bu özniteliği paket bildirimlerinde kullanır. İki geçerli değer 12,0 ve 14,0 ' dir. 12,0 değeri, öğenin [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] veya [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]için tasarlandığını belirtir; 14,0 değeri, öğenin [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] veya [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]için tasarlandığını gösterir.

 ASPX sayfalarını işlerken gelişmiş güvenlik için, [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] tüm ASPX veya ana sayfaların bir betik Yöneticisi denetimi içermesini gerektirir. Betik Yöneticisi hakkında daha fazla bilgi için bkz. [ScriptManager denetimine genel bakış](/previous-versions/bb398863(v=vs.140)). Betik Yöneticisi denetimi [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ve [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]' de kullanılamadığından, bir [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] veya [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] sayfasına [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] veya [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]yükseltilmelidir. Standart ana sayfa kullanan ASPX sayfaları, zaten standart ana sayfaya eklenmiş olduğundan bir betik Yöneticisi denetimi gerektirmez. Ancak, ana sayfa kullanmayan veya özel ana sayfa kullanan ASPX sayfaları [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] veya [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]çalışmak için bir betik denetimi eklememelidir.

 Tüm yeni projelerin SharePointProductVersion özniteliği 14,0 olarak ayarlandığından, bir [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] veya [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] projesini [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]aktardığınızda bir betik Yöneticisi denetiminin yokluğu bir sorun olabilir. Bir Web formu olan yükseltilen bir projeyi bir betik Yöneticisi olmadan dağıtırsanız, form SharePoint 'te görüntülenmez.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: mevcut bir SharePoint sitesinden öğeleri Içeri aktarma](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [İzlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio 'ya aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
