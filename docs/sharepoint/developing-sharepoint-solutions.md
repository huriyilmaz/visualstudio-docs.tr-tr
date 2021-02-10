---
title: SharePoint çözümlerini geliştirme | Microsoft Docs
description: SharePoint çözümleri geliştirin. Bir SharePoint projesinin öğelerini öğrenin. SharePoint projesi ve proje öğesi özelliklerini anlayın.
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
ms.openlocfilehash: 2f085f5679db2c5c4a1e3cf0cc8d7bbf7cad58eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948844"
---
# <a name="develop-sharepoint-solutions"></a>SharePoint çözümleri geliştirme
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint siteleri ve site öğeleri oluşturmak için içinde çeşitli SharePoint proje türü şablonları mevcuttur. Kullanılabilir proje türlerinin bir listesi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md). Aşağıda bir SharePoint projesinin öğelerinin ve özelliklerinin açıklaması verilmiştir.

 SharePoint 2013 ve SharePoint eklentileri hakkında daha fazla bilgi için bkz. [sharepoint 2013](https://www.microsoft.com/microsoft-365/previous-versions/microsoft-sharepoint-2013) ve [derleme SharePoint eklentileri](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

## <a name="elements-of-a-sharepoint-project"></a>Bir SharePoint projesinin öğeleri
 SharePoint projesi altındaki düğümler, *SharePoint öğeleri* olarak bilinir. SharePoint öğeleri, yapılandırma dosyaları,. aspx formları ve daha fazlası gibi *SharePoint öğe dosyaları* olarak adlandırılan bir veya daha fazla alt dosya da içerebilir [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] .

 Proje öğesi dosyaları ile doldurulmuş proje şablonları kullanarak proje oluşturmak yerine boş **Proje** şablonunu kullanarak boş bir SharePoint projesi oluşturabilir ve ardından proje öğelerini el ile ekleyebilirsiniz. SharePoint projeleri Ayrıca isteğe bağlı olarak bir veya daha fazla özellik dosyası (SharePoint 'te etkinleştirme için) ve projenin dağıtılacağı bir paket dosyası içerebilir.

### <a name="special-nodes"></a>Özel düğümler
 Her SharePoint projesi, yeniden adlandırılamayan, silinemeyen, kesilen, kopyalanamayan veya projeden sürüklenebilen iki düğüm içerir. Bu düğümler aşağıdaki gibidir:

- Özellikler
- Paket

  Proje için hiçbir özellik veya paket tanımlanmasa bile her iki düğüm de her zaman tüm SharePoint projelerinde görünür.

#### <a name="features-node"></a>Özellikler düğümü
 **Özellikler** düğümü bir veya daha fazla SharePoint proje özelliği içerir. Bir özellik, SharePoint uzantılarının bir kapsayıcısıdır. Bir özellik SharePoint Server 'a dağıtıldıktan sonra site tanımlarına eklenebilir veya SharePoint sitelerindeki SharePoint yöneticileri tarafından tek tek etkinleştirilebilir. Daha fazla bilgi için bkz. [özelliklerle çalışma](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

 Bir SharePoint projesine içerik türü veya liste örneği gibi bir öğe eklediğinizde, **Özellikler** düğümündeki bir özelliğe eklenir. Öğenin kapsamı, yeni veya var olan bir özelliğe eklenip eklenmeyeceğini belirler. Yeni öğe, var olan bir özellikle aynı kapsama sahipse, bu özelliğe eklenir. Aksi takdirde, öğe yeni bir özelliğe eklenir.

 Bir özelliği el ile eklemek için özellik düğümünün kısayol menüsünde **Özellik Ekle** komutunu yürütün. Özellik tasarımcısını kullanarak bir özelliğin içeriğini görüntüleyebilir veya değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint 'ı özelleştirme özelliği](../sharepoint/how-to-customize-a-sharepoint-feature.md).

 Bir özellik bir SharePoint projesine eklendiğinde, bu özellik *x*. feature adlı bir düğüm olarak **Çözüm Gezgini** görüntülenir, burada *x* benzersiz bir sayıdır. Bir özellik SharePoint sunucusuna dağıtıldıktan sonra, SharePoint Yöneticisi onu etkinleştirebilir ve SharePoint site kullanıcıları tarafından kullanılabilir hale getirir.

#### <a name="package-node"></a>Paket düğümü
 **Paket** düğümü, SharePoint projesi için dağıtım mekanizması görevi gören tek bir dosya içerir. Bu dosya, *çözüm paketi* olarak bilinir. CAB tabanlı bir. WSP uzantısı. Çözüm paketi, SharePoint siteleri için uygulanan ve tek tek etkinleştirebileceğiniz veya devre dışı bırakabilen bir dizi özellik, site tanımı ve derleme içeren dağıtılabilir, yeniden kullanılabilir bir dosyadır. **Paket** düğümü her zaman paket için bir tanım dosyası olan Package. wspdef adlı bir dosya içerir [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . SharePoint çalıştıran sunucuya bir paket dağıtıldıktan sonra, SharePoint Yöneticisi onu yükleyebilir ve özelliklerini etkinleştirebilir.

 Paket Tasarımcısı ' nda paket düğümüne çift tıklayarak veya kısayol menüsünü açıp **Aç**' ı seçerek paketin içeriğini görüntüleyebilir veya değiştirebilirsiniz. Daha fazla bilgi için bkz. [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md).

## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint projesi ve proje öğesi özellikleri
 Diğer projeler gibi SharePoint projeleri, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Özellikler penceresi ve Özellikler sayfasındaki özellikleri görüntüler. Görüntülenen özellikler Seçili düğüme göre değişir.

 **Çözüm Gezgini** bir SharePoint projesi, proje öğesi veya proje öğesi dosya düğümü seçildiğinde, aşağıdaki özellikler Özellikler penceresi veya Özellikler sayfasında görünür:

### <a name="project-properties"></a>Proje özellikleri

|Özellik Adı|Description|
|-------------------|-----------------|
|Etkin dağıtım yapılandırması|Dağıtım sırasında gerçekleştirilen adımların serisini belirtir. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|
|Bütünleştirilmiş kod dağıtım hedefi|*SharePoint uygulama derlemelerinin* nerede olduğunu belirler. Geçerli bütünleştirilmiş kod konumu değerleri *GlobalAssemblyCache* (varsayılan) veya *WebApplication*.<br /><br /> *Korumalı çözüm* özelliği **true** olarak ayarlandıysa, bu özellik devre dışı bırakılır.|
|Hata ayıklamadan sonra otomatik olarak geri çek|Dağıtılan çözümün ' de hata ayıklama modunda, uygulamayı çalıştırdıktan sonra otomatik olarak SharePoint 'ten geri çekme yapıp kullanmadığını belirtir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Seçildiğinde, çözüm hata ayıkladıktan sonra, IDE Tasarım görünümüne geri gittiğinde çözüm geri çeker. Bu, kaldırıldığında çözüm geri çekmez. Daha fazla bilgi için bkz. [geri çekiliyor a Solution](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14)).|
|Yapılandırma Düzenle|Proje için kullanılacak dağıtım yapılandırmasını belirtir. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) ve [SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|
|Silverlight hata ayıklamasını etkinleştir (betik hata ayıklaması yerine)|Seçildiğinde, Silverlight hata ayıklayıcı hata ayıklama işlemine ekler. Kaldırıldığında, betik hata ayıklayıcısı hata ayıklama işlemine ekler. Daha fazla bilgi için bkz. [Silverlight hata ayıklamasına genel bakış](/previous-versions/windows/).|
|Derlemeyi pakete ekle|Proje derlemesinin derleme zamanında paketlenip paketlenmediğini belirtir.|
|Dağıtım sonrası komut satırı|SharePoint çözümünü dağıttıktan sonra çalıştırılacak komutları belirtir. Bu satır, tüm Batch komutlarının yanı sıra MSBuild değişkenlerinin çözümlenmesini de destekler. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım komutlarını ayarlama](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Dağıtım öncesi komut satırı|SharePoint çözümünü dağıtmadan önce çalıştırılacak komutları belirtir. Bu satır, tüm Batch komutlarının yanı sıra MSBuild değişkenlerinin çözümlenmesini de destekler. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım komutlarını ayarlama](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Proje Dosyası|Derleme, yapılandırma ve proje hakkında diğer bilgileri içeren dosyanın adı.|
|Proje klasörü|Sistemdeki proje dosyasının konumu. (Salt okunur.)|
|Korumalı çözüm|Projenin, *Kullanıcı tarafından oluşturulan çözüm* olarak da bilinen bir *Korumalı çözüm* olarak dağıtılıp dağıtılmayacağını belirtir. Korumalı çözümlerin güvenilir olması gerekmez. **Doğru** değeri, projenin bir korumalı çözüm olarak dağıtıldığı anlamına gelir, **yanlış** değeri projenin bir Grup çözümü olarak dağıtıldığı anlamına gelir. Daha fazla bilgi için bkz. korumalı [çözüm konuları](../sharepoint/sandboxed-solution-considerations.md) ve [korumalı ve Grup çözümleri arasındaki farklar](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|
|Site URL 'SI|[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]Bu proje için hedef siteyi belirtir.|
|Başlangıç öğesi|Projedeki çalıştırılacak ilk öğeyi belirtir.|

 Bir SharePoint öğe dosyası (örneğin, bir iş akışı veya özellikler düğümündeki bir özellik) seçtiğinizde, aşağıdaki özellikler Özellikler penceresi görüntülenir:

### <a name="project-item-properties"></a>Proje öğesi özellikleri

|Özellik Adı|Description|
|-------------------|-----------------|
|Dağıtıma Çakışma Çözümlemesi|Özellikleri sunucuda zaten olan bir öğeyle aynı olan bir proje öğesi dağıtıldığında gerçekleştirilecek eylemi belirtir. Daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtım sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|
|Özellik özellikleri|SharePoint 'e dağıtırken bir özelliğe eklenen bir değer kümesini (anahtar/değer çiftleri olarak saklanır) belirtir. Özellik dağıtıldıktan sonra, kodunuzda özellik değerlerine erişebilirsiniz. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Özellik alıcısı|Bir proje öğesinin içeren özelliği için belirli olaylar gerçekleştiğinde yürütülen kodu sağlar. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Klasör adı|SharePoint proje öğesi klasörünün adı.|
|Proje çıktısı başvuruları|Proje öğesinin çalıştırması gereken bir derleme gibi bir bağımlılığı belirtir. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Güvenli denetim girdileri|Güvenilmeyen kullanıcıların düzenleyebilmesi için güvenli olan denetimleri belirtir. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Proje öğesi dosya özellikleri

|Özellik Adı|Description|
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
|[Visual Studio 'da SharePoint geliştirme &#40;URL Seçicisi iletişim kutusu&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Projenizdeki veya yerel SharePoint sunucusundaki kaynaklara yol başvuruları eklemek için kullanabileceğiniz bir iletişim kutusu tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio 'da SharePoint geliştirme &#40;kullanmaya başlama&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Sunucu Gezgini kullanarak SharePoint bağlantılarına gözatın](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint çözümlerini derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
