---
title: SharePoint Çözümleri | Microsoft Docs
description: Yeni SharePoint geliştirin. Bir proje için SharePoint bilmek. Proje SharePoint proje öğesi özelliklerini anlama.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 1998cad37c5fa5f8eecb6a1a7ea34154105662b3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625311"
---
# <a name="develop-sharepoint-solutions"></a>Yeni SharePoint geliştirme

  'SharePoint site ve site öğeleri oluşturmak için çeşitli [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint proje türü şablonları kullanılabilir. Kullanılabilir proje türlerinin listesi için bkz. [SharePoint proje ve proje öğesi şablonları.](../sharepoint/sharepoint-project-and-project-item-templates.md) Aşağıda, bir SharePoint projesinin öğelerinin ve özelliklerinin açıklaması ve bulunmaktadır.

 Eklenti ekleme hakkında SharePoint için [bkz. Derleme SharePoint eklentileri.](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)

## <a name="elements-of-a-sharepoint-project"></a>SharePoint projesinin öğeleri

 Bir projedeki düğümler SharePoint öğeleri olarak SharePoint *bilinir.* SharePoint, yapılandırma dosyaları, .aspx formları ve daha fazlası *gibi* SharePoint öğe dosyaları olarak adlandırılan bir veya daha fazla alt [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] dosya da içerebilir.

 Proje öğesi dosyalarıyla doldurulmuş proje şablonlarını kullanarak proje oluşturmak yerine  Boş Project şablonunu kullanarak boş bir SharePoint proje oluşturabilir ve ardından proje öğelerini el ile ekleyebilirsiniz. SharePoint, isteğe bağlı olarak bir veya daha fazla özellik dosyası (SharePoint'de etkinleştirme için) ve projenin dağıtılamayacak bir paket dosyası içerebilir.

### <a name="special-nodes"></a>Özel düğümler

 Her SharePoint proje yeniden adlandırılamayacak, silinemez, kesemez, kopyalanamaz veya projeden sürüklenemez iki düğüm içerir. Bu düğümler aşağıdaki gibidir:

- Özellikler
- Paket

  Proje için hiçbir özellik veya paket SharePoint bile her iki düğüm de her zaman tüm projelerde görünür.

#### <a name="features-node"></a>Özellikler düğümü

 Özellikler **düğümü,** bir veya daha fazla SharePoint özellik içerir. Özellik, bir uzantı kapsayıcısıdır ve SharePoint. Bir özellik bir SharePoint sunucusuna dağıtıldıktan sonra, site tanımlarında yer alan veya sitelerde SharePoint yöneticiler tarafından tek SharePoint etkinleştirilebilir. Daha fazla bilgi için [bkz. Özelliklerle Çalışma.](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14))

 Bir SharePoint projesine içerik türü veya liste örneği gibi bir öğe eklerken, bu öğe Özellikler düğümünde bir **özele** eklenir. Öğenin kapsamı, öğenin yeni bir özelle mi yoksa var olan bir özelle mi ekli olduğunu belirler. Yeni öğe mevcut bir özellikle aynı kapsamına sahipse, söz konusu özele eklenir. Aksi takdirde, öğe yeni bir özellik eklenir.

 Bir özelliği el ile eklemek için özellik **düğümünün** kısayol menüsünde Özellik Ekle komutunu yürütün. Özellik Tasarımcısı'ı kullanarak bir özelliğin içeriğini görüntülebilirsiniz veya değiştirebilirsiniz. Daha fazla bilgi için [bkz. Nasıl SharePoint özelleştirme.](../sharepoint/how-to-customize-a-sharepoint-feature.md)

 Bir özellik bir SharePoint projesine eklendiğinde, Çözüm Gezgini x'in benzersiz bir sayı olduğu Varsayılan Özellik  *x*.feature adıyla bir düğüm olarak görünür.  SharePoint Server'a bir özellik dağıtıldıktan sonra, SharePoint yöneticisi özelliği etkinleştirerek site kullanıcılarının SharePoint hale SharePoint olabilir.

#### <a name="package-node"></a>Paket düğümü

 Paket **düğümü,** proje için dağıtım mekanizması olarak görev yapan tek bir SharePoint içerir. Çözüm paketi olarak bilinen *bu dosya,*.CAB tabanlıdır. WSP uzantısı. Çözüm paketi, SharePoint siteleri için geçerli olan ve tek tek etkinleştirebilir veya devre dışı bırakabilecek özellikler, site tanımları ve derlemeler içeren dağıtılabilir, yeniden kullanılabilir bir dosyadır. Paket **düğümü** ayrıca her zaman paket için bir tanım dosyası olan Package.wspdef adlı [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bir dosya içerir. Paket, SharePoint çalıştıran sunucuya dağıtıldıktan sonra, SharePoint yöneticisi paketi yükleyebilir ve özelliklerini etkinleştirebilirsiniz.

 Paket Tasarımcısı'nda paket düğümüne çift tıklayarak veya kısayol menüsünü açıp Aç'ı seçerek paketin içeriğini ekleyebilirsiniz veya **değiştirebilirsiniz.** Daha fazla bilgi için [bkz. SharePoint paketleri oluşturma.](../sharepoint/creating-sharepoint-solution-packages.md)

## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint proje ve proje öğesi özelliklerini değiştirme

 SharePoint projelerde olduğu gibi, özellikler de Özellikler penceresi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sayfasında görüntülenir. Görüntülenen özellikler, seçilen düğüme bağlıdır.

 Bir SharePoint proje, proje öğesi veya proje öğesi dosya düğümü **Çözüm Gezgini,** aşağıdaki özellikler Özellikler penceresi sayfasında görünür:

### <a name="project-properties"></a>Proje özellikleri

|Özellik Adı|Description|
|-------------------|-----------------|
|Etkin Dağıtım Yapılandırması|Dağıtım sırasında gerçekleştirilen adım serisini belirtir. Daha fazla bilgi için, [bkz. How to: Edit a SharePoint deployment configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|
|Derleme Dağıtım Hedefi|Uygulama *derlemelerinin SharePoint olduğunu* belirler. Geçerli derleme konumu değerleri *GlobalAssemblyCache* (varsayılan) veya *WebApplication'dır.*<br /><br /> Korumalı *Çözüm özelliği true* olarak **ayarlanırsa** bu özellik devre dışı bırakılır.|
|Hata ayıklamadan sonra otomatik geri alma|Uygulama içinde hata ayıklama modunda çalıştırıldıktan sonra dağıtılan çözümün SharePoint otomatik olarak geri çekip çekmey olmadığını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belirtir. Seçildiğinde, IDE hata ayıklamadan sonra tasarım görünümüne geri geldiğinde çözüm geri çekiliyor. Temizlenin, çözüm geri çekmez. Daha fazla bilgi için [bkz. Çözümü Geri Alma.](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14))|
|Yapılandırmaları Düzenle|Proje için kullanmak üzere dağıtım yapılandırmasını belirtir. Daha fazla bilgi için [bkz. Nasıl SharePoint:](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) Dağıtım yapılandırmasını düzenleme ve Çözüm paketlerini [dağıtma, yayımlama SharePoint yükseltme.](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)|
|Silverlight Hata Ayıklamayı Etkinleştirme (Betik hata ayıklaması yerine)|Silverlight hata ayıklayıcısı seçildiğinde hata ayıklama sürecine iliştirer. Betik hata ayıklayıcısı temiz olduğunda hata ayıklama sürecine iliştirer. Daha fazla bilgi için bkz. [Silverlight Hata Ayıklamaya Genel Bakış.](/previous-versions/windows/)|
|Derlemeyi Pakete Dahil Etmek|Proje derlemenin derleme zamanında paketli olup olmadığını belirtir.|
|Dağıtım Sonrası Komut Satırı|SharePoint çözümünün dağıtımı sonrasında çalıştıracak SharePoint belirtir. Bu satır, tüm batch komutlarının yanı sıra tüm MSBuild destekler. Daha fazla bilgi için, [bkz. How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Dağıtım Öncesi Komut Satırı|SharePoint çözümünü dağıtmadan önce çalıştıracak SharePoint belirtir. Bu satır, tüm batch komutlarının yanı sıra tüm MSBuild destekler. Daha fazla bilgi için, [bkz. How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Proje Dosyası|Derleme, yapılandırma ve proje hakkında diğer bilgileri içeren dosyanın adı.|
|Project Klasör|Proje dosyasının sistem üzerinde konumu. (Salt okunur.)|
|Korumalı Çözüm|Projenin, kullanıcı tarafından oluşturulan bir çözüm olarak da bilinen korumalı *alanlı* bir çözüm olarak *dağıtıp dağıtılamayacaklarını belirtir.* Korumalı alan çözümlerinin güvenilir olması şart değildir. **true değeri,** projenin korumalı alanlı çözüm olarak dağıtılacağı, **false** değeri ise projenin grup çözümü olarak dağıtılacağı anlamına gelir. Daha fazla bilgi için [bkz. Korumalı Alanlı](../sharepoint/sandboxed-solution-considerations.md) Çözüm Konuları ve [Korumalı Alan ve Grup Çözümleri Arasındaki Farklar.](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)|
|Site URL'si|Bu proje [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] için hedef sitenin belirtir.|
|Başlangıç Öğesi|Çalıştıracak projede ilk öğeyi belirtir.|

 Yeni bir SharePoint dosyası (örneğin, bir iş akışı veya Özellikler düğümünde bir özellik) seçerseniz, aşağıdaki özellikler Özellikler penceresi:

### <a name="project-item-properties"></a>Project özellikleri

|Özellik Adı|Description|
|-------------------|-----------------|
|Dağıtıma Çakışma Çözümlemesi|Özellikleri sunucu üzerinde zaten bulunan bir öğenin özellikleriyle aynı olan bir proje öğesini dağıtırken uz eklenecek eylemi belirtir. Daha fazla bilgi için [bkz. Paketleme SharePoint Dağıtım sorunlarını giderme.](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)|
|Özellik Özellikleri|Özel bir özelle birlikte dağıtan bir değer kümesi (anahtar/değer çiftleri olarak depolanır) SharePoint. Özellik dağıtıldıktan sonra kodundaki özellik değerlerine erişebilirsiniz. Daha fazla bilgi için, [bkz. Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Özellik Alıcısı|Bir proje öğesinin içeren özelliğinde belirli olaylar oluştuğunda yürütülen kod sağlar. Daha fazla bilgi için, [bkz. Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Klasör Adı|Proje öğesi SharePoint adı.|
|Project Çıkış Başvuruları|Proje öğenizin çalışması gereken bir derleme gibi bir bağımlılığı belirtir. Daha fazla bilgi için, [bkz. Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Kasa Denetim Girişleri|Güvenilmeyen kullanıcıların düzenlemesi için güvenli olan denetimleri belirtir. Daha fazla bilgi için, [bkz. Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Project öğe dosyası özellikleri

|Özellik Adı|Description|
|-------------------|-----------------|
|Derleme Eylemi|Dosyanın derleme ve dağıtım işlemleriyle nasıl ilişkili olduğunu belirtir. Daha fazla bilgi için bkz. [Dosya Özellikleri.](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))|
|Çıkış Dizinine Kopyalama|Kaynak dosyanın Çıkış dizinine kopyalanır olup olmadığını belirtir. Aşağıdaki değerlerden biri olabilir:<br /><br /> -   *Kopyalama*<br />-   *Her zaman kopyala*<br />-   *Daha yeni ise kopyala*<br /><br /> Daha fazla bilgi için bkz. [Dosya Özellikleri.](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))|
|Özel Araç|Varsa, dosyayı tasarım zamanında dönüştüren ve dönüştürmenin çıkışını başka bir dosyaya koyan bir aracın adını belirtir. Örneğin, bir veri kümesi (. [!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)] ) dosyası varsayılan özel bir araç içerir. Daha fazla bilgi için bkz. [Dosya Özellikleri.](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))|
|Özel Araç Ad Alanı|Özel aracın çıkışını kopyalanan ad alanı. Daha fazla bilgi için bkz. [Dosya Özellikleri.](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))|
|Dağıtım Konumu|SharePoint sunucusundaki dosyanın tam yolu. Bu yol, Dağıtım Kök ve Dağıtım Yolu alt özelliklerinden oluşur.|
|Dağıtım Yolu|dosyanın İş Akışı1 gibi SharePoint Sunucusu dosyasındaki göreli \\ yolu. Dosyanın tam yolu, Dağıtım Yolu değeri Dağıtım Kök  değerinin sonuna bir *oluşturularak* oluşturulur.<br /><br /> Dağıtım Türü özelliği için *RootFile* değerinin  seçimi Dağıtım Kökü özelliğini olarak değiştirir ve \Workflow1 tam yolu  \<SharePointRoot> \\ ile \<SharePointRoot> \\ sonuçlanır. Daha fazla bilgi için, [bkz. Packaging and Deploying SharePoint Solutions](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|
|Dağıtım Kökü|Dize. Dosyanın SharePoint Server'a dağıtılacağı kök klasör. Örneğin, \<SharePointRoot> \Template\Features \\ \<FeatureName> \\ .<br /><br /> Dağıtım Kökü *özelliğinin değeri* Dağıtım Türü *ayarı tarafından* belirlenir.|
|Dağıtım Türü|Dosyanın Dağıtım Kök değerini belirleyen *dağıtım türü.* Aşağıdaki değerlerden biri olabilir:<br /><br /> NoDeployment: *\<no value>*<br /><br /> ElementManifest: *\<SharePointRoot> \Template\Features \\ \<FeatureName>*\\<br /><br /> ElementFile: *\<SharePointRoot> \Template\Features \\ \<FeatureName> \\*<br /><br /> TemplateFile: *\<SharePointRoot> \Template \\*<br /><br /> RootFile: *\<SharePointRoot>\\*<br /><br /> GlobalResource: *\<SharePointRoot> \Resources \\*<br /><br /> ClassResource: *\<ClassResourcePath>\\*<br /><br /> Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|Dosya Adı|Öğe dosyası için dosyanın veya klasörün adı.|
|Tam Yol|Öğenin dosyasının konumu. (Salt okunur.)|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[SharePoint Projesi ve Proje Öğesi Şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md)|içinde SharePoint proje ve proje öğesi şablonlarını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açıklar.|
|[Nasıl yapılır: Bir SharePoint Projesine Öğeler Ekleme](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Bir SharePoint projesine yeni veya [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mevcut öğelerin nasıl ek SharePoint açıklar.|
|[Adım adım kılavuz: Site sütunu, içerik türü ve liste oluşturma SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Müşteri alanı, içerik türü, liste tanımı ve liste örneği oluşturma konusunda size adım adım yol sağlar.|
|[Nasıl: Olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)|Adım adım kılavuz: Site sütunu, içerik türü ve uygulama listesi oluşturma içinde oluşturulan proje için olay [alıcısının nasıl SharePoint.](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|
|[İş SharePoint çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)|İş akışı ilişkilendirme formları ve iş akışı başlatma formları içeren iş akışı projelerinin nasıl oluşturulacaklarını açıklar.|
|[SharePoint için sayfalar oluşturma](../sharepoint/creating-pages-for-sharepoint.md)|Uygulama sayfaları, site sayfaları, ana sayfalar ve uygulama sayfaları için sayfa düzenleri gibi sayfaları nasıl oluşturabilirsiniz SharePoint.|
|[SharePoint için web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)|Kullanıcıların bir tarayıcı kullanarak site sayfalarının içeriğini, görünümünü ve davranışını doğrudan değiştirmesini SharePoint denetimler eklemeyi açıklar.|
|[Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Uygulama sayfaları tarafından tüketilen kullanıcı denetimlerinin ve uygulama sayfalarında çalıştır Web Bölümleri kullanıcı denetimlerinin nasıl SharePoint.|
|[İş verilerini iş verileriyle SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Web hizmetlerinden ve arka uç sunucu uygulamalarından gelen verilerin bir web uygulamasıyla nasıl tümleştir SharePoint açıklar.|
|[SharePoint için site tanımları oluşturma](../sharepoint/creating-site-definitions-for-sharepoint.md)|Site tanımları oluşturma: site oluşturmak için kullanılan şablonlar SharePoint açıklar.|
|[Mevcut bir SharePoint Sitesinden Öğeleri İçeri Aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|mevcut bir sitedeki içerik türleri ve modüller gibi öğelerin bir SharePoint projesinde nasıl [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] içeri SharePoint açıklar.|
|[Çözüme Dosyaları Dahil Etmek için Modül Kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Projenizin dosyalarını SharePoint sitenize dağıtmak için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modüllerin nasıl SharePoint açıklar.|
|[SharePoint kullanarak bağlantılara göz Sunucu Gezgini](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Web siteleri kullanarak yerel SharePoint göz atma Sunucu Gezgini.|
|[Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Güvenli denetim girişleri, proje çıkış başvuruları ve özellik özellikleri gibi projeler için paketleme ve dağıtım bilgileri sağlamak üzere proje öğesi özelliklerinin nasıl kullanılası açık bir şekilde açık bir şekilde anlattır.|
|[Nasıl: Eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Kaynaklara daha kolay erişim sağlamak için eşlenen klasörlerin projenize nasıl SharePoint açıklar.|
|[Korumalı alanlı çözümde dikkat edilmesi gerekenler](../sharepoint/sandboxed-solution-considerations.md)|Korumalı alan çözümleriyle ilişkili sorunları açıklar.|
|[SharePoint Çözümleri için Güvenlik](../sharepoint/security-for-sharepoint-solutions.md)|içinde çözüm geliştirmek için güvenlikle ilgili SharePoint konuları [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açıklar.|
|[Visual Studio SharePoint geliştirme &#40;URL seçicisi iletişim kutusu&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|projenizdeki kaynaklara veya yerel SharePoint sunucusuna yol başvuruları eklemek için kullanabileceğiniz bir iletişim kutusu tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio &#40;SharePoint geliştirmeye başlayın&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Sunucu Gezgini kullanarak SharePoint bağlantılara gözatamazsınız](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint çözümleri oluşturun ve hata ayıklayın](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
