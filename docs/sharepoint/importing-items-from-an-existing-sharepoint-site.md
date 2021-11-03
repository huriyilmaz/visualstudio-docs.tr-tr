---
title: Mevcut bir Site SharePoint'dan Öğeleri | Microsoft Docs
description: Öğeleri yeni bir çözümde yeniden SharePoint için İçeri Aktarma SharePoint Çözüm Paketi proje şablonuyla mevcut bir SharePoint aktarın.
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
ms.openlocfilehash: 7cf9f13ac7a45cd739c5248c68cfe0d7041a84c7
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127448"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Mevcut bir siteden öğeleri SharePoint alma
  İçeri Aktarma SharePoint Çözüm Paketi proje şablonu, mevcut sitelerden içerik türleri ve alanlar gibi öğeleri yeni bir SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözümde yeniden SharePoint sağlar. İçeri aktarılan çözümlerin çoğunu değişiklik yapmadan çalıştırabilirsiniz, ancak özellikle de öğeleri içeri aktardıktan sonra herhangi bir öğe değiştirirken dikkate alınacak bazı kısıtlamalar ve sorunlar vardır.

> [!NOTE]
> Yeniden kullanılabilir iş akışlarını içeri aktarma için Yeniden Kullanılabilir İş Akışını İçeri Aktar proje şablonunu kullanın. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri.](../sharepoint/guidelines-for-importing-reusable-workflows.md)

## <a name="supported-sharepoint-solutions"></a>Desteklenen SharePoint çözümleri
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] ve içinde oluşturulan çözümlerin içeri aktarmayı tam olarak [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] destekler.

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] aşağıdaki uygulamalarda oluşturulan çözümlerin içeri aktarılamalarını desteklemez:

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  Bu uygulamalar tarafından oluşturulan çözümleri genellikle başarıyla içeri aktarabilirsiniz, ancak bu işlevsellik test edilmemiştir ve desteklenmiyor.

## <a name="item-import-restrictions"></a>Öğe içeri aktarma kısıtlamaları
 Çoğu SharePoint mevcut *bir .wsp* dosyasından içe aktarılabilmiş olsa da, aşağıdaki öğeler desteklanmaz ve düzgün çalışması için değişiklikler yapılması gerekli olabilir:

- BDC varlıkları

- Kod iş akışı ilişkilendirme öğeleri

- Kod iş akışları

- Görsel Web bölümleri (.ascx)

- Web hizmetleri (*.asmx*)

- İçerik türü bağlamaları

- Olay alıcıları

- Tanımları (şablonlar) listele

- Site tanımları

  veya 'den bir çözümü [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] dışarı [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] aktarsanız, bu öğeler otomatik olarak *.wsp dosyasından hariç* tutulacaktır. Ancak desteklenmeyen araçlardan oluşturulan diğer *.wsp* dosyaları bu öğeleri içerebilir. (Bu konunun önceki SharePoint "Desteklenen Çözümler" başlığına bakın.)

## <a name="what-happens-when-you-import-a-solution"></a>Bir çözümü içeri aktarınca ne olur?
 SharePoint Çözüm Paketini İçeri Aktar şablonuyla bir çözümü içeri aktarıyorsanız, .wsp dosyasının tüm içeriğini kopyalar ve içeri aktarılan öğelerle dosyaları arasında mümkün olan en fazla ilişkilendirmeyi ve başvuruyı uzlaştırmaya ve korumaya [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çalışır. 

 İçe aktarılan tüm öğeler, içinde karşılık gelen **klasörlere Çözüm Gezgini.** Örneğin, içerik türleri klasörünün altında görünür **İçerik türleri ve** liste örnekleri, Örnekleri **listele altında görünür.** İçe aktarılan bir öğeyle ilişkili dosyalar da öğenin klasörüne kopyalanır. Örneğin, içe aktarılan bir liste örneği modüllerini, formlarını ve ASPX sayfalarını içerir.

### <a name="dependent-items"></a>Bağımlı öğeler
 SharePoint Çözüm Paketini İçeri Aktar sihirbazında bir öğe seçer ancak bağımlı öğeleri seçmezsiniz, bağımlı öğelerin içeri aktarmadan önce de seçili olması gerektiğini size bir ileti kutusu iletir.

### <a name="what-are-features"></a>Özellikler nedir?
 SharePoint Tasarımcı kullanıcıları, özellikler olarak adlandırılan beklenmeyen *dosyaları,* bu dosyalarda içe aktarılan **çözümlerinde Çözüm Gezgini.** SharePoint Designer çözümünde mevcut olsa da, bunlar görünümden gizlendi. Özellikler artık içinde görünür [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] durumdadır.

 Özellikler, SharePoint kapsayıcılarıdır. Her özellik, içerdiği içerik türleri ve liste tanımları gibi her öğeye bir başvuru tutar. Çözümlerinizi içeri aktararak içeri aktarılan tüm öğeler için özellikler ayarlar ve dosyalar için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] özellik-öğe ilişkilerini sürdürmeye çalışır. Başvuruları çözümlenemedi tüm dosyalar Diğer İçe Aktarılan **Dosyalar klasörüne** alınır.

 Özellikler hakkında daha fazla bilgi için [bkz. SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md) [ve Özelliklerle Çalışma.](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14))

### <a name="handle-special-cases"></a>Özel servis olaylarını işleme
 Bazı durumlarda, Visual Studio bağımlı dosyalarıyla uzlaştıramaz. Çözümlene [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir dosya, Diğer İçe Aktarılan Dosyalar **klasörünün altında görünür.** Ayrıca **DeploymentType özellikleri,** çözümle birlikte dağıtılamamaları için **NoDeployment** olarak ayarlanır.

 Örneğin ExpenseForms liste tanımını içeri aktarıyorsanız, Çözüm Gezgini'daki Liste  tanımları klasörünün altında bu adla bir liste tanımı,Elements.xmlveSchema.xml *görünür.*   Ancak, ilişkili ASPX ve HTML formları **ExpenseForms** adlı bir klasöre Diğer İçe **Aktarılan Dosyalar klasörünün altına** yerleştirilebilirsiniz. İçeri aktarma işlemini tamamlamak için, bu dosyaları Çözüm Gezgini ExpenseForms liste tanımı altında hareket **ettirin** ve **NoDeployment** olan her dosyanın **DeploymentType** özelliğini ElementFile olarak **değiştirebilirsiniz.**

 Olay alıcılarını içeri *aktarıyorsanız,Elements.xml* dosyası doğru konuma kopyalanır, ancak çözümüyle birlikte dağıtacak şekilde derlemeyi çözüm paketine el ile dahil edin. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)]bunu nasıl yapabilirim, bkz. Nasıl 2012: Ek [derlemeler ekleme ve kaldırma.](../sharepoint/how-to-add-and-remove-additional-assemblies.md)

 İş akışları içeri aktarılırken, InfoPath formları Diğer İçeri Aktarılan **Dosyalar klasörüne kopyalanır.** *.wsp dosyası* bir Web şablonu içeriyorsa, dosyanın başlangıç sayfası olarak **Çözüm Gezgini.**

## <a name="import-fields-and-property-bags"></a>Alanları ve özellik torbalarını içeri aktarma
 Birden çok alana sahip bir çözümü içeri aktarıyorsanız, ayrı alan tanımlarının hepsi, Alanlar adlı bir *düğüm altındaElements.xml* tek bir **Çözüm Gezgini** **birleştirilir.** Benzer şekilde, tüm özellik çantası girişleri PropertyBags *adlıElements.xml* altındaki bir dosyayla **birleştirilir.**

 Veri SharePoint metin, Boole veya arama gibi belirli bir veri türünün sütunlarıdır. Daha fazla bilgi için bkz. [Yapı Taşı: Sütunlar ve Alan Türleri.](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)) Özellik çantası, bir gruptan bir SharePoint sitedeki bir listeye kadar her şey için SharePoint sağlar. Özellik çantası, özellik adlarının ve değerlerinin karma tablosu olarak uygulanır. Daha fazla bilgi için [bkz. SharePoint Yapılandırması'SharePoint](/previous-versions/msp-n-p/ff647766(v=pandp.10)) [Property Bag Ayarlar.](https://www.codeproject.com/articles/43601/sharepoint-property-bag)

## <a name="delete-items-in-the-project"></a>Projedeki öğeleri silme
 Bu çözümdeki SharePoint bir veya daha fazla bağımlı öğeye sahiptir. Örneğin, liste örnekleri içerik türlerine, içerik türleri ise alanlara bağlıdır. Bir SharePoint çözümü içeri aktardıktan sonra, çözümü dağıtmayı denemeden önce çözümdeki bir öğeyi siler ancak bağımlı öğelerini silmeniz durumu size herhangi bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başvuru sorunu bildirmez. Örneğin, içe aktarılan bir çözümde içerik türüne bağlı bir liste örneği varsa ve bu içerik türünü silersiniz, dağıtımda bir hata oluşabilir. Bağımlı öğe, SharePoint sunucusunda yoksa hata oluşur. Benzer şekilde, silinmiş bir öğenin ilgili bir özellik çantası da varsa, bu özellik çantası girdilerini **PropertyBags dosya dosyasından** *Elements.xml* silin. Bu nedenle, içe aktarılan bir çözümden herhangi bir öğe siler ve dağıtım hataları elde edersiniz, bağımlı öğelerden herhangi biri de silinmesi gereksin mi kontrol edin.

## <a name="restore-missing-feature-attributes"></a>Eksik özellik özniteliklerini geri yükleme
 Çözümler içeri aktarılırken, içeri aktarılan özellik bildiriminden bazı isteğe bağlı özellik öznitelikleri atlanır. Bu öznitelikleri yeni özellik dosyasında geri yüklemek için özgün özellik dosyasını yeni özellik bildirimiyle karşılaştırarak eksik öznitelikleri bulun ve Nasıl yapılır: Bir özellik özelliğini özelleştirme konusunda verilen [SharePoint izleyin.](../sharepoint/how-to-customize-a-sharepoint-feature.md)

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Yerleşik liste örneklerde dağıtım çakışması algılaması gerçekleştiriliyor
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]yerleşik liste örneklerde dağıtım çakışması algılama gerçekleştirmez (diğer bir ifadeyle birlikte gelen varsayılan liste SharePoint). Çakışma algılama işlemi, yerleşik liste örneklerinin üzerine yazılmasından kaçınmak için SharePoint. Yerleşik liste örnekleri hala dağıtılır veya güncelleştirilir, ancak hiçbir zaman silinmez veya üzerine yazılmaz. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Paketleme SharePoint dağıtımıyla ilgili sorunları giderme.](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)

## <a name="import-sharepoint-server-2010-workflows"></a>SharePoint Server 2010 iş akışlarını içeri aktarma
 içinde oluşturulan bir iş akışını içeri [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] aktardısanız, dağıtınca düzgün çalışmaz. Bazı derlemeler eksik olduğundan ve iş akışları şu anda iş akışı çözümlerinde destek açmayan InfoPath formları içerdiği için iş  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] akışı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] düzgün çalışmıyor. Ancak, derlemelere başvuru ekleme ve InfoPath formlarını yeniden bağlama gibi bazı öğeler düzeltildikten sonra, içe aktarılan iş akışları düzgün şekilde [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] çalışmak için kullanılabilir. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint Server 2010 İş Akışlarını İçeri Aktarma.](/sharepoint/dev/)

## <a name="item-name-character-limit"></a>Öğe adı karakter sınırı
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , yol da dahil olmak üzere proje ve proje öğesi adları için toplam 260 karakterlik bir sınıra sahip. Bir çözümü içeri aktarıyorsanız, öğe adı bu sınırı aşarsa şu hatayı alırsınız:

 **Belirtilen yol, dosya adı veya her ikisi de çok uzun. Tam dosya adı 260 karakterden az olmalı ve dizin adı 248 karakterden küçük olmalıdır.**

 Bu hatayı alırsanız öğe oluşturulmaz. Bu sorun en çok içe aktarılan modüllerde oluşur. Bu sorunu önlemek için şunları yapın:

- Yeni Kaynak Ekle iletişim kutusuna projeniz için **kısa adlar Project** kullanın.

- Yolu kısaltmak için projeyi kök klasöre mümkün olduğunca yakın bir konumda oluşturun.

## <a name="the-sharepointproductversion-attribute"></a>SharePointProductVersion özniteliği
 veya gibi önceki bir SharePoint sürümünde oluşturulan bir çözümü içeri aktarıyorsanız, paket bildiriminde SharePointProductVersion öznitelik değerini 12.0 olarak değiştirebilir veya içeri aktarılan tüm Web sayfalarına bir betik yöneticisi denetimi ekler ve [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] SharePointProductVersion değerini 14.0 olarak bırakın. Aksi takdirde, içe aktarılan Web formları veri SharePoint.

### <a name="background"></a>Arka Plan
 ve içinde [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] çözümler [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] SharePointProductVersion adlı bir öznitelik içerir. SharePoint çözümün tasarlanma sürümünü belirlemek için paket bildirim SharePoint bu özniteliği kullanır. İki geçerli değer 12.0 ve 14.0'dır. 12.0 değeri, öğenin veya için tasarlanma durumuna [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] işaret ediyor; 14.0 değeri ise öğenin veya için tasarlanıyor olduğunu [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] gösterir.

 ASPX sayfalarını işleme sırasında gelişmiş güvenlik için ve tüm ASPX veya ana sayfaların bir [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] betik yöneticisi denetimi içermesi gerekir. Betik yöneticisi hakkında daha fazla bilgi için bkz. [ScriptManager Denetimine Genel Bakış.](/previous-versions/bb398863(v=vs.140)) betik yöneticisi denetimi ve içinde kullanılabilir olduğundan, veya sürümüne yükseltilen [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] herhangi bir veya sayfaya bir tane [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] eklenmiştir. Standart ana sayfa kullanan ASPX sayfaları için betik yöneticisi denetimi gerekli değildir çünkü standart ana sayfaya zaten bir tane eklenir. Ancak, bir ana sayfa kullanmayan veya özel bir ana sayfa kullanan ASPX sayfalarının veya içinde çalışması için bir betik denetimi eklemesi [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] gerekir.

 Tüm yeni projelerin [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] SharePointProductVersion özniteliği 14.0 olarak ayarlanmış olduğundan, bir veya projesini içine aktarıyorken betik yöneticisi denetimi olmaması sorun [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] olabilir. Betik yöneticisi olmadan Bir Web formu olan yükseltilmiş bir proje dağıtırsanız, form bir web SharePoint.

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: Mevcut bir siteden SharePoint içeri aktarma](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [Adım adım kılavuz: SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Nasıl olur: Bir SharePoint projesine mevcut bir BDC SharePoint ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
