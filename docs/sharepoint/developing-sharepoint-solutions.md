---
title: SharePoint Çözümleri geliştirme | Microsoft Docs
description: SharePoint çözümleri geliştirme. SharePoint projesinin öğelerini bilmek. SharePoint proje ve proje öğesi özelliklerini anlama.
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
ms.workload:
- office
ms.openlocfilehash: f839f4148054b4e10a7fc1703aa8f03549bdbf36
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112904"
---
# <a name="develop-sharepoint-solutions"></a>SharePoint çözümleri geliştirme

  Içinde SharePoint siteleri ve site öğeleri oluşturmak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] için çeşitli SharePoint proje türü şablonları kullanılabilir. Kullanılabilir proje türlerinin listesi için bkz. [SharePoint proje ve proje öğesi şablonları.](../sharepoint/sharepoint-project-and-project-item-templates.md) Aşağıda, bir SharePoint projesinin öğelerinin ve özelliklerinin bir açıklaması ve ardından ve ardından yer alan açıklama ve bilgiler yer a açıklamadır.

 SharePoint eklentileri hakkında bilgi için [bkz. SharePoint eklentilerini derleme.](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)

## <a name="elements-of-a-sharepoint-project"></a>SharePoint projesinin öğeleri

 Bir SharePoint projesi altındaki düğümler, *SharePoint öğeleri olarak bilinir.* SharePoint öğeleri, yapılandırma dosyaları, .aspx formları ve daha fazlası gibi *SharePoint* öğe dosyaları olarak adlandırılan bir veya daha fazla alt [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] dosya da içerebilir.

 Proje öğesi dosyalarıyla doldurulmuş proje şablonlarını kullanarak proje oluşturmak yerine  Boş Proje şablonunu kullanarak boş bir SharePoint projesi oluşturabilir ve ardından proje öğelerini el ile ekleyebilirsiniz. SharePoint projeleri ayrıca isteğe bağlı olarak bir veya daha fazla özellik dosyası (SharePoint'te etkinleştirme için) ve projenin dağıtıla bir paket dosyası içerebilir.

### <a name="special-nodes"></a>Özel düğümler

 Her SharePoint projesi yeniden adlandırılamaz, silinemez, kesemez, kopyalanamaz veya projeden sürüklenemez iki düğüm içerir. Bu düğümler aşağıdaki gibidir:

- Özellikler
- Paket

  Proje için hiçbir özellik veya paket tanımlanmamış olsa bile her iki düğüm de her zaman tüm SharePoint projelerinde görünür.

#### <a name="features-node"></a>Özellikler düğümü

 Özellikler **düğümü** bir veya daha fazla SharePoint proje özelliği içerir. Özellik, SharePoint için uzantıların bir kapsayıcısıdır. Bir özellik SharePoint sunucusuna dağıtıldıktan sonra, site tanımlarında yer alan veya SharePoint sitelerinin SharePoint yöneticileri tarafından tek tek etkinleştirilebilir. Daha fazla bilgi için [bkz. Özelliklerle Çalışma.](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14))

 Bir SharePoint projesine içerik türü veya liste örneği gibi bir öğe eklerken, bu öğe Özellikler düğümünde bir **özele eklenir.** Öğenin kapsamı, öğenin yeni bir özelle mi yoksa var olan bir özelle mi ekli olduğunu belirler. Yeni öğe mevcut bir özellikle aynı kapsamına sahipse, bu özele eklenir. Aksi takdirde, öğe yeni bir özellik eklenir.

 Bir özelliği el ile eklemek için özellik **düğümünün** kısayol menüsünde Özellik Ekle komutunu yürütün. Özellik Tasarımcısı'ı kullanarak bir özelliğin içeriğini görüntülebilirsiniz veya değiştirebilirsiniz. Daha fazla bilgi için [bkz. Nasıl: SharePoint özelliğini özelleştirme.](../sharepoint/how-to-customize-a-sharepoint-feature.md)

 Bir SharePoint projesine bir özellik eklendiğinde, Çözüm Gezgini **x'in** benzersiz bir sayı olduğu Özellik *x*.feature varsayılan adına sahip bir *düğüm* olarak görünür. Bir özellik SharePoint Server'a dağıtıldıktan sonra, SharePoint yöneticisi etkinleştirerek SharePoint sitesi kullanıcıları tarafından kullanılabilir hale kullanılabilir.

#### <a name="package-node"></a>Paket düğümü

 Paket **düğümü,** SharePoint projesi için dağıtım mekanizması olarak görev yapan tek bir dosya içerir. Çözüm paketi olarak bilinen *bu dosya,*.CAB tabanlıdır. WSP uzantısı. Çözüm paketi, SharePoint siteleri için geçerli olan ve tek tek etkinleştirebilir veya devre dışı bırakabilecek bir dizi özellik, site tanımı ve derleme içeren dağıtılabilir, yeniden kullanılabilir bir dosyadır. Paket **düğümü** ayrıca her zaman paket için bir tanım dosyası olan Package.wspdef adlı [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bir dosya içerir. SharePoint çalıştıran sunucuya bir paket dağıtıldıktan sonra, SharePoint yöneticisi paketi yükleyebilir ve özelliklerini etkinleştirebilirsiniz.

 Paket Tasarımcısı'nda paket düğümüne çift tıklayarak veya kısayol menüsünü açıp Aç'ı seçerek paketin içeriğini ekleyebilirsiniz veya **değiştirebilirsiniz.** Daha fazla bilgi için [bkz. SharePoint çözüm paketleri oluşturma.](../sharepoint/creating-sharepoint-solution-packages.md)

## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint proje ve proje öğesi özellikleri

 SharePoint projeleri, diğer projelerde olduğu gibi, özellikleri Özellikler penceresi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sayfasında görüntüler. Görüntülenen özellikler, seçilen düğüme bağlıdır.

 bir SharePoint projesi, proje öğesi veya proje öğesi dosya düğümü **Çözüm Gezgini,** aşağıdaki özellikler Özellikler penceresi sayfasında görünür:

### <a name="project-properties"></a>Proje özellikleri

|Özellik Adı|Açıklama|
|-------------------|-----------------|
|Etkin Dağıtım Yapılandırması|Dağıtım sırasında gerçekleştirilen adım serisini belirtir. Daha fazla bilgi için, [bkz. How to: Edit a SharePoint deployment configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|
|Derleme Dağıtım Hedefi|SharePoint uygulama *derlemelerinin nerede olduğunu* belirler. Geçerli derleme konumu değerleri *GlobalAssemblyCache* (varsayılan) veya *WebApplication'dır.*<br /><br /> Korumalı *Çözüm özelliği true* olarak **ayarlanırsa** bu özellik devre dışı bırakılır.|
|Hata ayıklamadan sonra otomatik geri alma|Uygulamayı içinde hata ayıklama modunda çalıştırıldıktan sonra dağıtılan çözümün SharePoint'den otomatik olarak geri çekip çekmey olmadığını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belirtir. Seçildiğinde, IDE hata ayıklamadan sonra tasarım görünümüne geri geldiğinde çözüm geri çekiliyor. Temizlenin, çözüm geri çekmez. Daha fazla bilgi için [bkz. Çözümü Geri Alma.](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14))|
|Yapılandırmaları Düzenle|Proje için kullanmak üzere dağıtım yapılandırmasını belirtir. Daha fazla bilgi için [bkz. Nasıl kullanılır: SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) dağıtım yapılandırmasını düzenleme ve SharePoint çözüm paketlerini [dağıtma, yayımlama ve yükseltme.](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)|
|Silverlight Hata Ayıklamayı Etkinleştirme (Betik hata ayıklaması yerine)|Silverlight hata ayıklayıcısı seçildiğinde hata ayıklama sürecine iliştirer. Betik hata ayıklayıcısı temiz olduğunda hata ayıklama sürecine iliştirer. Daha fazla bilgi için bkz. [Silverlight Hata Ayıklamaya Genel Bakış.](/previous-versions/windows/)|
|Derlemeyi Pakete Dahil Etmek|Proje derlemenin derleme zamanında paketli olup olmadığını belirtir.|
|Dağıtım Sonrası Komut Satırı|SharePoint çözümünü dağıtarak çalıştıracak komutları belirtir. Bu satır, MSBuild değişkenlerinin çözünürlüğüne ek olarak tüm batch komutlarını destekler. Daha fazla bilgi için, [bkz. How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Dağıtım Öncesi Komut Satırı|SharePoint çözümünü dağıtmadan önce çalıştıracak komutları belirtir. Bu satır, MSBuild değişkenlerinin çözünürlüğüne ek olarak tüm batch komutlarını destekler. Daha fazla bilgi için, [bkz. How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Proje Dosyası|Derleme, yapılandırma ve proje hakkında diğer bilgileri içeren dosyanın adı.|
|Proje Klasörü|Proje dosyasının sistem üzerinde konumu. (Salt okunur.)|
|Korumalı Çözüm|Projenin, kullanıcı tarafından oluşturulan bir çözüm olarak da bilinen *korumalı alan çözümü* olarak *dağıtılacak olup olmadığını belirtir.* Korumalı alan çözümlerinin güvenilir olması şart değildir. **true değeri,** projenin korumalı alanlı çözüm olarak dağıtılacağı, **false** değeri ise projenin grup çözümü olarak dağıtılacağı anlamına gelir. Daha fazla bilgi için [bkz. Korumalı Alanlı](../sharepoint/sandboxed-solution-considerations.md) Çözüm Konuları ve [Korumalı Alan ve Grup Çözümleri Arasındaki Farklar.](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)|
|Site URL'si|Bu proje [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] için hedef sitenin belirtir.|
|Başlangıç Öğesi|Çalıştıracak projede ilk öğeyi belirtir.|

 Bir SharePoint öğe dosyası (örneğin, bir iş akışı veya Özellikler düğümünde bir özellik) seçtiğiniz zaman, aşağıdaki özellikler Özellikler penceresi:

### <a name="project-item-properties"></a>Proje öğesi özellikleri

|Özellik Adı|Açıklama|
|-------------------|-----------------|
|Dağıtıma Çakışma Çözümlemesi|Özellikleri sunucu üzerinde zaten bulunan bir öğenin özellikleriyle aynı olan bir proje öğesini dağıtırken uz eklenecek eylemi belirtir. Daha fazla bilgi için [bkz. SharePoint Paketleme ve Dağıtım Sorunlarını Giderme.](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)|
|Özellik Özellikleri|SharePoint 'e dağıtırken bir özelliğe eklenen bir değer kümesini (anahtar/değer çiftleri olarak saklanır) belirtir. Özellik dağıtıldıktan sonra, kodunuzda özellik değerlerine erişebilirsiniz. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Özellik alıcısı|Bir proje öğesinin içeren özelliği için belirli olaylar gerçekleştiğinde yürütülen kodu sağlar. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Klasör adı|SharePoint proje öğesi klasörünün adı.|
|Proje çıktısı başvuruları|Proje öğesinin çalıştırması gereken bir derleme gibi bir bağımlılığı belirtir. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Güvenli denetim girdileri|Güvenilmeyen kullanıcıların düzenleyebilmesi için güvenli olan denetimleri belirtir. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Proje öğesi dosya özellikleri

|Özellik Adı|Açıklama|
|-------------------|-----------------|
|Derleme eylemi|Dosyanın derleme ve dağıtım işlemleriyle ilişkisini belirtir. Daha fazla bilgi için bkz. [dosya özellikleri](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Çıkış dizinine Kopyala|Kaynak dosyaların çıkış dizinine kopyalanıp kopyalanmayacağını belirtir. Aşağıdaki değerlerden biri olabilir:<br /><br /> -   *Kopyalamayın*<br />-   *Her zaman Kopyala*<br />-   *Daha yeniyse kopyala*<br /><br /> Daha fazla bilgi için bkz. [dosya özellikleri](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Özel araç|Varsa, dosyayı tasarım zamanında dönüştüren ve dönüşümün çıkışını başka bir dosyaya yerleştiren bir aracın adını belirtir. Örneğin, bir veri kümesi (. [!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)] ) dosyası varsayılan bir özel araca sahiptir. Daha fazla bilgi için bkz. [dosya özellikleri](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Özel araç ad alanı|Özel aracın çıktısının kopyalandığı ad alanı. Daha fazla bilgi için bkz. [dosya özellikleri](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Dağıtım Konumu|SharePoint sunucusundaki dosyanın tam yolu. Bu yol, dağıtım kökü ve dağıtım yolu alt özelliklerinden oluşur.|
|Dağıtım yolu|SharePoint Server dosyasındaki dosyanın Workflow1 gibi göreli yolu \\ . Dosyanın tam yolu, dağıtım *yolu* değeri *dağıtım kök* değerinin sonuna bitişerek oluşturulur.<br /><br /> *Dağıtım türü* özelliği Için bir *RootFile* değeri seçildiğinde, *dağıtım kök* özelliği, \<SharePointRoot> \\ tam olarak \<SharePointRoot> \workflow1 yoluna neden olacak şekilde değişir \\ . Daha fazla bilgi için bkz. [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|
|Dağıtım kökü|Dize. SharePoint sunucusunda dosyanın dağıtıldığı kök klasör. Örneğin, \<SharePointRoot> \Template\features \\ \<FeatureName> \\ .<br /><br /> *Dağıtım kök* özelliğinin değeri, *dağıtım türü* ayarı tarafından belirlenir.|
|Dağıtım türü|Dosyanın dağıtım türü, *dağıtım kök* değerini belirler. Aşağıdaki değerlerden biri olabilir:<br /><br /> NoDeployment: *\<no value>*<br /><br /> ElementManifest: *\<SharePointRoot> \Template\features \\ \<FeatureName>*\\<br /><br /> ElementFile: *\<SharePointRoot> \Template\özellikler \\ \<FeatureName> \\*<br /><br /> TemplateFile: *\<SharePointRoot> \ şablon \\*<br /><br /> RootFile: *\<SharePointRoot>\\*<br /><br /> GlobalResource: *\<SharePointRoot> \Resources \\*<br /><br /> ClassResource: *\<ClassResourcePath>\\*<br /><br /> Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|Dosya Adı|Öğe dosyası için dosya veya klasörün adı.|
|Tam Yol|Öğe için dosyanın konumu. (Salt okunur.)|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[SharePoint Projesi ve Proje Öğesi Şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md)|İçinde kullanabileceğiniz SharePoint projesi ve proje öğesi şablonlarını açıklar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Nasıl yapılır: Bir SharePoint Projesine Öğeler Ekleme](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Yeni veya var olan öğelerin bir SharePoint projesine nasıl ekleneceğini açıklar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[İzlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Müşteri alanı, içerik türü, liste tanımı ve liste örneği oluşturma konusunda size adım adım yol gösterir.|
|[Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)|[Izlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)bölümünde oluşturulan proje için bir olay alıcısının nasıl ekleneceğini açıklar.|
|[SharePoint iş akışı çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)|İş akışı ilişkilendirme formları ve iş akışı başlatma formları içeren iş akışı projelerinin nasıl oluşturulacağını açıklar.|
|[SharePoint için sayfa oluşturma](../sharepoint/creating-pages-for-sharepoint.md)|SharePoint için uygulama sayfaları, site sayfaları, ana sayfalar ve sayfa düzenleri gibi sayfaları nasıl oluşturabileceğiniz açıklanmaktadır.|
|[SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)|Kullanıcıların SharePoint site sayfalarının içeriğini, görünümünü ve davranışını bir tarayıcı kullanarak doğrudan değiştirmesini sağlayan denetimlerin nasıl ekleneceğini açıklar.|
|[Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|SharePoint 'te çalışan uygulama sayfaları ve Web Bölümleri tarafından tüketilen kullanıcı denetimlerinin nasıl oluşturulacağını açıklar.|
|[İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)|Web Hizmetleri ve arka uç sunucu uygulamalarındaki verilerin bir SharePoint uygulamasına nasıl tümleştirileceğini açıklar.|
|[SharePoint için site tanımları oluşturma](../sharepoint/creating-site-definitions-for-sharepoint.md)|Site tanımlarının nasıl oluşturulduğunu açıklar: SharePoint siteleri oluşturmak için kullanılan şablonlar.|
|[Mevcut bir SharePoint Sitesinden Öğeleri İçeri Aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Mevcut bir SharePoint sitesinden bir SharePoint projesine içerik türleri ve modüller gibi öğelerin nasıl içeri aktarılacağını açıklar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Çözüme Dosyaları Dahil Etmek için Modül Kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Projenizden SharePoint sitesine dosya dağıtmak için modüllerin nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Sunucu Gezgini kullanarak SharePoint bağlantılarına gözatın](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Sunucu Gezgini kullanarak yerel SharePoint sitelerine nasıl gözatabileceğinizi açıklar.|
|[Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Proje öğesi özelliklerinin, güvenli denetim girişleri, proje çıktı başvuruları ve özellik özellikleri gibi projeler için paketleme ve dağıtım bilgilerini sağlamak üzere nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md)|SharePoint kaynaklarına daha kolay erişim sağlamak için eşlenmiş klasörlerin projenize nasıl eklenebileceğinizi açıklar.|
|[Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md)|Korumalı çözümlerle ilişkili sorunları açıklar.|
|[SharePoint Çözümleri için Güvenlik](../sharepoint/security-for-sharepoint-solutions.md)|' De SharePoint çözümleri geliştirmeye yönelik güvenlik konuları açıklanmaktadır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Visual Studio&#41;'de SharePoint &#40;URL seçici iletişim Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Projenizin veya yerel SharePoint sunucusundaki kaynaklara yol başvuruları eklemek için kullanabileceğiniz bir iletişim kutusunu açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanmaya başlayın &#40;sharepoint geliştirme Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Sunucu Gezgini kullanarak SharePoint bağlantılarına göz atma](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint çözümlerini derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint çözümlerini paketle ve dağıt](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
