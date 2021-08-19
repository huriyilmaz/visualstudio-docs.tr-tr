---
title: SharePoint Project Ve Project ŞablonLarını | Microsoft Docs
description: Kullanılabilir proje ve proje SharePoint şablonlarının açıklamalarını ve bunların nasıl kullanıldıklarını gözden geçirme.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2949bf27910f90cee2e109e64d0d6741439806fc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115570"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint proje ve proje öğesi şablonlarını kullanma
  Aşağıdaki bölümlerde proje ve SharePoint şablonlarını ve bunların nasıl kullanıldıklarını açıklar.

## <a name="project-and-project-item-templates-overview"></a>Project ve proje öğesi şablonlarına genel bakış
 Visual Studio'SharePoint yeni bir SharePoint projesi, bu proje türü için gereken tüm proje öğeleriyle birlikte çözüme eklenir. Örneğin, bir Silverlight Web Bölümü projesi oluşturursanız, Visual Studio Görsel Web Bölümü proje öğesini ve bir Silverlight uygulaması proje öğesini ve bu proje öğeleri için gereken tüm dosyaları içeren bir çözüm oluşturur. Project öğe şablonları, olay alıcısı, site sütunu veya liste ekleme gibi SharePoint proje öğeleri eklemek için kullanılır.

 Temel bilgiler hakkında SharePoint için bkz. [SharePoint Foundation Yapı Taşları.](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)) İleri düzey kullanıcılar özel proje ve proje öğesi şablonları oluşturabilir. Daha fazla bilgi için [bkz. SharePoint proje sistemini genişletme.](../sharepoint/extending-the-sharepoint-project-system.md)

## <a name="project-templates"></a>Project şablonları
 Aşağıda, proje şablonlarının SharePoint listesi ve ardından yer almaktadır. SharePoint proje şablonlarını Visual Studio için, Yeni **Project** iletişim kutusunda **Visual C#** veya **Visual Basic** altındaki SharePoint düğümünü genişletin ve  **ardından 2010'a tıklayın.**

### <a name="sharepoint-2010-project"></a>SharePoint 2010 projesi
 *SharePoint 2010* Project her proje şablonuna SharePoint dahil edilir. 2010 SharePoint bir Project içerir:

- Proje dosyası.

- Proje özellikleri sayfası.

- Projedeki tüm derleme başvurularını listeleye bir **References** klasörü.

- Özellikleri **sunucuya** dağıtmak için *kullanılan bir .feature* yapılandırma dosyası içeren özellikler SharePoint klasörü.

- Çözümü **SharePoint'a** dağıtmak için kullanılan *Package.package* dosyasını içeren bir Package SharePoint.

- Gelişmiş güvenlik için derlemeyi güçlü bir adla imzalamak için kullanılan bir key.snk (strong-name key) dosyası.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight web bölümü
 *SharePoint 2010 Silverlight Web Bölümü* projeleri, Silverlight uygulamalarının görüntü SharePoint web bölümleri oluşturmanızı sağlar. Bu projeyi 7.000.000'e 000.000'e kadar olan bir proje için yeni bir Silverlight uygulaması eklemek veya mevcut bir uygulamaya başvuru yapmak için belirtebilirsiniz. Daha fazla bilgi için [bkz. SharePoint için web](../sharepoint/creating-web-parts-for-sharepoint.md) bölümleri oluşturma ve adım adım kılavuz: SharePoint için OData görüntüleyen [bir Silverlight web bölümü oluşturma.](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 görsel web bölümü
 Bir *SharePoint 2010 Visual Web* Bölümü projesi bir *Elements.xml* tanım dosyası, **bir Web** Bölümü öğesi ve bir Kullanıcı Denetimi **öğesi** içerir. Visual Studio Toolbox'tan kullanıcı denetimi yüzeyine sürükleyerek veya kopyalayıp görsel web bölümü görünümünü tasarabilirsiniz. Daha fazla bilgi için, [bkz. How to: Create a SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) web part by Using a Designer and [Building Block: Web Bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>2010 SharePoint paketini içeri aktarma
 *SharePoint 2010* Çözüm Paketi projelerini içeri aktarın, mevcut SharePoint 2010 sitenin bir kısmını veya bir kısmını bir SharePoint çözümü (*.wsp*) dosyasına aktararak Visual Studio. Uygulama içine Visual Studio sonra öğelerini özelleştirilebilir ve yeniden yalıtabilirsiniz. Daha fazla bilgi için [bkz. Mevcut bir sitedeki öğeleri SharePoint.](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)

### <a name="import-reusable-sharepoint-2010-workflow"></a>Yeniden kullanılabilir iş SharePoint 2010 iş akışını içeri aktarma
 *Yeniden Kullanılabilir SharePoint 2010* İş Akışı projelerini içeri aktarma, SharePoint Designer 2010'da oluşturulan yeniden kullanılabilir, bildirime açık bir iş akışını Visual Studio. İş akışı, SharePoint *bir .wsp dosyası olarak dışarı* aktarıldı. Sanal Visual Studio sonra özelleştirilebilir, içine kod ekleyebilir ve daha sonra bir SharePoint dağıtabilirsiniz. Daha fazla bilgi için [bkz. Adım adım: SharePoint Tasarımcısı](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)yeniden kullanılabilir iş akışını Visual Studio.

## <a name="project-item-templates"></a>Project öğe şablonları
 Aşağıda, proje öğesi SharePoint listesi ve ardından yer almaktadır. Project şablonları site sütunları, SharePoint ve içerik türleri gibi SharePoint işlevlerini desteklemek için SharePoint çözümüne dosya ekler. Örneğin çözümünüze bir site sütunu eklemek, bir site tanımı dosyası içeren bir *siteElements.xml* ekler. Görsel web bölümü eklemek çözümünüze birElements.xmldosyası, kullanıcı denetim öğesi ve görsel web bölümü öğesi içeren bir görsel web bölümü projesi ekler. 

 Proje öğesi SharePoint görüntülemek için, **Çözüm Gezgini'da** bir SharePoint projesinin kısayol menüsünü açın ve Ekle **,** Yeni Öğe'yi **seçin.** Visual **C# SharePoint** altındaki  Visual Basic **düğümünü genişletin ve** ardından **2010'ı seçin.**

### <a name="application-page-farm-solution-only"></a>Uygulama sayfası (yalnızca grup çözümü)
 Uygulama **Sayfası (Yalnızca Grup Çözümü)** öğesi, bir web sitesi için [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] bir web SharePoint sağlar. Uygulama sayfaları yalnızca grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca grup çözümlerine eklersiniz. Daha fazla bilgi için, [bkz. How to: Create an application page](../sharepoint/how-to-create-an-application-page.md) and Application _layouts Page [Type](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>İş verileri bağlantı modeli (yalnızca grup çözümü)
 İş **Verileri Bağlantı Modeli (Yalnızca Grup Çözümü)** öğesi, iş verilerini iş verileriyle SharePoint. İş verileri, , Siebel ve Hizmet Reklam Protokolü [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] (SAP) gibi arka uç sunucu uygulamalarından gelebilir. İş verileri bağlantı modelleri yalnızca grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca grup çözümlerine eklersiniz. Daha fazla bilgi için, bkz. Nasıl [kullanılır: BDC Modeli Oluşturma,](../sharepoint/how-to-create-a-bdc-model.md) [Nasıl kullanılır:](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)Yerelleştirilmiş Adları, Özellikleri ve İzinleri Belirtmek için Kaynak Dosyası Kullanma ve [What's New: Business Connectivity Services](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>İçerik türü
 *İçerik Türü* öğeleri belge, duyuru veya görev gibi mevcut (temel) içerik türünü temel alan özel içerik türleri oluşturmanıza izin sağlar. Özel içerik türü, temel içerik türüyle aynı öznitelikleri ve alanları tanımladığınız tüm site sütunlarıyla (alanlar) birlikte sağlar. Örneğin, bir kişi ile birlikte gelen temel Kişi içerik türünü temel alan özel bir Kişi içerik SharePoint. Mevcut site sütunlarını değiştirerek veya temel içerik türüne zaten dahil edilenlere daha fazla site sütunu ekleyerek içerik türünü özelleştirebilirsiniz.

> [!NOTE]
> Bir SharePoint nedeniyle korumalı alanlı çözüm içerik türünü temel alan bir grup çözümü içerik türü oluşturamazsiniz.

 Daha fazla bilgi için bkz. Adım [adım: Site sütunu,](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) içerik türü ve SharePoint listesi oluşturma [ve Yapı Taşı: İçerik Türü.](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14))

### <a name="empty-element"></a>Boş öğe
 *Boş öğeler* genellikle bir proje veya SharePoint şablonu olmayan proje öğelerini tanımlamak için Visual Studio. Projenize boş bir öğe eklerken EmptyElement[x](burada [x] adlı bir düğüm benzersiz bir \) sayı oluşturulur. EmptyElement[x],Elements.xml *adlı tek bir dosya içerir.* içinde [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istenen öğeleri tanımlamak için deyimlerini *Elements.xml.*

### <a name="event-receiver"></a>Olay alıcısı
 *Olay alıcıları,* bir SharePoint bir öğenin listeye ekleniyor, bir web öğesi silindiğinde veya bir iş akışı başlatıldı. Olay alıcısı proje öğesi şablonu

- Olayları listele

- Öğe olaylarını listele

- E-posta olaylarını listele

- Web olayları

- İş akışı olaylarını listele

  Olay alıcısı proje  öğesi, SharePoint Özelleştirme Sihirbazı'nda projeyi oluşturulduğunda belirttiğiniz tüm olaylar için olay işleyicileri içeren tek sınıflı bir **dosya ile bir Olay Alıcısı klasörü oluşturur.** Olay alıcısı sınıfı, SharePoint, alanlar, öğeler, listeler, ekler, web bölümleri ve iş akışları eklendiklerinde, güncelleştirildiğinde, silindiğinde veya kaldırıldığı zaman SharePoint sitesinde oluşan olayları işebilir. Daha fazla bilgi için, [bkz. How to: Create an event receiver](../sharepoint/how-to-create-an-event-receiver.md) and Building [Block: Event Handling](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>Liste
 Liste, takvim veya görev listesi gibi yeniden SharePoint bir temel veri listesi tanımı örneğidir. Çözüme bir liste ekledikten sonra Liste Tasarımcısı, listeye site sütunları eklemenize ve özel liste sütunları oluşturmanıza olanak sağlar. Buna içerik türlerinden site sütunları dahildir. Listede görünecek *sütunları* belirleyen liste görünümünü belirtebilirsiniz. Daha fazla bilgi için bkz. Adım [adım:](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) Site sütunu, içerik türü ve SharePoint listesi [oluşturma: Listeler ve Belge Kitaplıkları.](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14))

### <a name="module"></a>Modül
 *Modüller* (modüllerle karıştırılmamalıdır) görüntüler veya notlar gibi SharePoint sunucuya [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] dağıtmak istediğiniz dosyaları içerir. Modül proje öğesi bir Modül **düğümü** içerir. Modül düğümü iki proje öğesi şablonu içerir: modül için bildirim olarak hareket eder bir XML tanım dosyası vesample.txt *dosyası* yer tutucu dosyası. Daha fazla bilgi için [bkz. Çözüm ve Modüllere Dosya](../sharepoint/using-modules-to-include-files-in-the-solution.md) Eklemek için [Modülleri Kullanma.](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14))

### <a name="sequential-workflow-farm-solution-only"></a>Sıralı iş akışı (yalnızca grup çözümü)
 Sıralı *iş akışı,* son adım tamamlanana kadar sırayla gerçekleştirilen bir dizi iş mantığı adımıdır. Sıralı iş akışları, listeler ve belgeler gibi SharePoint işlemleri yönetmek için kullanılır. Site düzeyinde (genel) iş akışları veya liste düzeyi (yerel) iş akışları oluşturabilir ve bir iş akışının otomatik olarak mı yoksa el ile mi başlatılası seçebilirsiniz. Bu proje öğesi yalnızca grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca grup çözümlerine eklersiniz. Daha fazla bilgi için, [bkz. SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)iş akışı çözümleri oluşturma, [SharePoint Server 2010'da](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))İş Akışları ve [What's New: Workflow Improvements](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Silverlight web bölümü
 *Silverlight web bölümü* proje öğeleri, Silverlight uygulamalarının görüntü SharePoint web bölümleri oluşturmanıza olanak sağlar. Bu proje öğesini çözümünüze eklerken, yeni bir Silverlight uygulaması eklemeyi veya daha sonra var olan bir uygulamaya başvurup başvurulmaycagını seçebilirsiniz. Daha fazla bilgi için [bkz. SharePoint için web](../sharepoint/creating-web-parts-for-sharepoint.md) bölümleri oluşturma ve adım adım kılavuz: SharePoint için OData görüntüleyen [bir Silverlight web bölümü oluşturma.](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)

### <a name="site-column"></a>Site sütunu
 Alan olarak da bilinen *bir site* *sütunu,* bir site projesine ekleyebilirsiniz en temel öğelerden SharePoint olur. Site sütunu telefon numarası, metin açıklaması veya kişi listesinde bir kişinin şehir adı gibi bir veri türünü temsil eder. Daha fazla bilgi için, [bkz. Create site columns, content types, and lists for SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) and [Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Site tanımı (yalnızca grup çözümü)
 *Site tanımı* proje öğeleri, aşağıdaki dosyaları içeren bir site tanımı klasörü içerir:

- Sitenin varsayılan web sayfası olarak kullanılan varsayılan .aspx sayfası.

- Sitenin *onet.xml* tanımlayan bir dosya.

- Yeni Web Sitesi sayfasının Şablon Seçimi bölümünde görünen site  tanımı yapılandırmalarını belirten bir webtemp xml **SharePoint dosyası.**

  Bir site tanımı ekledikten sonra işlevleri tanıtmak için kod ve dosyalar eklersiniz. Bu proje öğesi yalnızca grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca grup çözümlerine eklersiniz. Daha fazla bilgi için, [bkz. Create site definitions for SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) and [Site Definitions and Configurations](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Durum makinesi iş akışı (yalnızca grup çözümü)
 Durum *makinesi iş akışı* bir dizi iş mantığı durumu, geçişi ve eylemidir. Durum makinesi iş akışında adımlar sırasıyla gerçekleştirlanmaz; bunun yerine, eylemler ve durumlarla tetiklenirler. Sıralı bir iş akışı gibi durum makinesi iş akışları da listeler SharePoint belgeler gibi iş akışlarıyla ilişkilendirilmektedir. Bir kez daha site düzeyi (genel) iş akışları veya liste düzeyi (yerel) iş akışları oluşturabilirsiniz. Bir iş akışının otomatik olarak mı yoksa el ile mi başlatılamayacaklarını da seçebilirsiniz. Bu proje öğesi yalnızca grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca grup çözümlerine eklersiniz. Daha fazla bilgi için [bkz. SharePoint iş akışı](../sharepoint/creating-sharepoint-workflow-solutions.md)çözümleri oluşturma, [SharePoint Server 2010'da](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))İş Akışları ve [What's New: Workflow Improvements](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Kullanıcı denetimi (yalnızca grup çözümü)
 Kullanıcı *denetimi,* diğer denetimler ve denetimler için diğer ASP.NET, yeniden SharePoint denetimdir. Kullanıcı denetimi, uygulama sayfalarına ve web bölümlerine SharePoint. Bu proje öğesi yalnızca grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca grup çözümlerine eklersiniz. Daha fazla bilgi için, [bkz. Creating Reusable Controls for Web Bölümleri or Application Pages](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Görsel web bölümü
 Görsel *web bölümü proje* öğesi,Elements.xmldosyası, Web Bölümü öğesi **ve** Kullanıcı Denetimi **öğesi** içerir.  Visual Studio Toolbox'tan kullanıcı denetimi yüzeyine sürükleyerek veya kopyalayıp görsel web parçasının görünümünü tasarabilirsiniz. Daha fazla bilgi için, [bkz. How to: Create a SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) web part by Using a Designer and [Building Block: Web Bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web kısmı
 Web *bölümü,* Web Bölümü Sayfası adlı özel bir sayfa türü içinde çalışan bir sunucu tarafı denetimidir. Bunlar, bir sitenin bir yerinde görünen sayfaların SharePoint yapı taşlarıdır. Web bölümü öğesi, bir web sitesi için web bölümü tasarlamaya olanak SharePoint sağlar. Daha fazla bilgi için, [bkz. How to: Create a SharePoint web part and](../sharepoint/how-to-create-a-sharepoint-web-part.md) Building [Block: Web Bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint Ürünler ve Teknolojiler](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
