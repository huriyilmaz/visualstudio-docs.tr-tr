---
title: SharePoint Proje ve Proje Kalemi Şablonları | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649220"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint proje ve proje öğesi şablonları
  Aşağıdaki bölümlerde kullanılabilir SharePoint proje ve proje öğesi şablonları ve bunların nasıl kullanıldığı açıklanmaktadır.

## <a name="project-and-project-item-templates-overview"></a>Proje ve proje öğesi şablonlarına genel bakış
 Visual Studio'da yeni bir SharePoint projesi oluşturduğunuzda, çözüme bir SharePoint projesi, proje türünün gerektirdiği tüm proje öğeleriyle birlikte eklenir. Örneğin, bir Silverlight Web Bölümü projesi oluşturursanız, Visual Studio, bu proje öğelerinin gerektirdiği tüm dosyalarla birlikte Görsel Web Bölümü proje öğesi ve Silverlight uygulaması proje öğesi içeren bir çözüm oluşturur. Proje öğesi şablonları, etkinlik alıcısı, site sütunu veya liste ekleme gibi varolan bir SharePoint projesine proje öğeleri eklemek için kullanılır.

 SharePoint temelleri hakkında daha fazla bilgi için Bkz. [SharePoint Vakfı Yapı Taşları.](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)) Gelişmiş kullanıcılar özel proje ve proje öğesi şablonları oluşturabilir. Daha fazla bilgi için [bkz.](../sharepoint/extending-the-sharepoint-project-system.md)

## <a name="project-templates"></a>Proje şablonları
 Aşağıda SharePoint proje şablonlarının bir listesi verilmiştir. Visual Studio'daki SharePoint proje şablonlarını Görüntülemek için, **Yeni Proje** iletişim kutusunda, **Visual C#** veya **Visual Basic**altında **SharePoint** düğümlerini genişletin ve ardından **2010'u**seçin.

### <a name="sharepoint-2010-project"></a>SharePoint 2010 projesi
 *SharePoint 2010 Projesi'nin* içeriği her SharePoint proje şablonuna dahildir. SharePoint 2010 Projesi şunları içerir:

- Bir proje dosyası.

- Proje özellikleri sayfası.

- Projedeki tüm derleme başvurularını listeleyen bir **Başvuru** klasörü.

- Özellikleri SharePoint sunucusuna dağıtmak için kullanılan *bir .feature* yapılandırma dosyası içeren Özellikler **klasörü.**

- Çözümü **Package** SharePoint'e dağıtmak için kullanılan *package.package* dosyası içeren paket klasörü.

- Gelişmiş güvenlik için derlemeyi güçlü bir adla imzalamak için kullanılan key.snk (güçlü ad anahtarı) dosyası.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight web bölümü
 *SharePoint 2010 Silverlight Web Part* projeleri, SharePoint için Silverlight uygulamalarını görüntüleyen web parçaları oluşturmanıza olanak tanır. Bu projeyi oluşturduğunuzda, projeye yeni bir Silverlight uygulaması ekleyip eklemeyin veya varolan bir uygulamaya başvurup başvurmayın belirtebilirsiniz. Daha fazla bilgi için bkz: SharePoint ve Walkthrough [için web parçaları oluştur: SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) [için OData'yı görüntüleyen bir Silverlight web parçası oluşturun.](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 görsel web bölümü
 *SharePoint 2010 Visual Web Part* projesi *elements.xml* tanım dosyası, bir **Web Bölümü** öğesi ve kullanıcı **denetimi** öğeiçerir. Görsel Stüdyo Araç Kutusu'ndan kullanıcı denetiminin yüzeyine denetimleri sürükleyerek veya kopyalayarak görsel web parçasının görünümünü tasarlayabilirsiniz. Daha fazla bilgi için bkz: Tasarımcı ve Yapı Bloğu [Kullanarak SharePoint web bölümü oluşturun:](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [Web Bölümleri.](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))

### <a name="import-sharepoint-2010-solution-package"></a>Import SharePoint 2010 çözüm paketi
 *SharePoint 2010 Çözüm Paketi* projelerini içe aktar, varolan sharepoint 2010 sitesinin tamamını veya bir kısmını, SharePoint çözümüne *(.wsp)* aktarılan bir dosyaya Visual Studio'ya aktarabilirsiniz. Visual Studio'ya alındıktan sonra öğelerini özelleştirebilir ve yeniden dağıtabilirsiniz. Daha fazla bilgi için, [varolan bir SharePoint sitesinden öğeleri alma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)konusuna bakın.

### <a name="import-reusable-sharepoint-2010-workflow"></a>Yeniden kullanılabilir SharePoint 2010 iş akışı alma
 *Yeniden Kullanılabilir SharePoint 2010 İş Akışı projelerini içe aktarın,* SharePoint Designer 2010'da oluşturulan yeniden kullanılabilir, bildirimsel iş akışını Visual Studio'ya aktarmanızı sağlar. İş akışı SharePoint sitesinden *.wsp* dosyası olarak dışa aktarılır. Visual Studio'ya alındıktan sonra özelleştirebilir, kod ekleyebilir ve ardından sharepoint sitesine dağıtabilirsiniz. Daha fazla bilgi için [Bkz. Walkthrough: Visual Studio'ya SharePoint Designer yeniden kullanılabilir iş akışı aktarın.](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)

## <a name="project-item-templates"></a>Proje öğesi şablonları
 Aşağıda SharePoint proje öğesi şablonlarının bir listesi verilmiştir. Proje öğesi şablonları, site sütunları, listeler ve içerik türleri gibi SharePoint işlevselliğini desteklemek için SharePoint çözümüne dosya ekler. Örneğin, çözümünüze bir site sütunu eklemek *Elements.xml* tanım dosyası içeren bir site sütunu projesi ekler. Görsel bir web parçası eklemek, *elements.xml* dosyası, kullanıcı denetim öğesi ve görsel web parçası öğesi içeren çözümünüze görsel bir web parçası projesi ekler.

 SharePoint proje öğesi şablonlarını görüntülemek **için, Solution**Explorer'da, SharePoint projesinin kısayol menüsünü açın ve ardından Ekle , Yeni **Öğe'yi**seçin. **New Item** **Visual C#** veya **Visual Basic**altında **SharePoint** düğümini genişletin ve ardından **2010'u**seçin.

### <a name="application-page-farm-solution-only"></a>Uygulama sayfası (yalnızca çiftlik çözümü)
 **Uygulama Sayfası (Yalnızca Farm Solution)** öğesi, [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] SharePoint sitesi için bir web sayfası tasarlamanızı sağlar. Uygulama sayfaları yalnızca çiftlik çözümlerinde kullanılabilir. Bu proje öğesini yalnızca çiftlik çözümlerine ekleyebilirsiniz. Daha fazla bilgi için [bkz: Uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md) ve [Uygulama _layouts Sayfa Türü.](/previous-versions/office/aa979604(v=office.14))

### <a name="business-data-connectivity-model-farm-solution-only"></a>İş veri bağlantısı modeli (yalnızca çiftlik çözümü)
 İş **Verileri Bağlantı Modeli (Yalnızca Farm Solution)** öğesi, iş verilerini SharePoint'e tümleştirmenize olanak tanır. İş verileri, Siebel ve Hizmet Reklamcılığı [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]Protokolü (SAP) gibi arka uç sunucu uygulamalarından gelebilir. İş veri bağlantısı modelleri yalnızca çiftlik çözümlerinde kullanılabilir. Bu proje öğesini yalnızca çiftlik çözümlerine ekleyebilirsiniz. Daha fazla bilgi için [bkz: BDC Modeli Oluşturma](../sharepoint/how-to-create-a-bdc-model.md), [Nasıl Kullanılır: Yerelleştirilmiş Adları, Özellikleri ve İzinleri Belirtmek için Kaynak Dosyasını Kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)ve [Yenilikler: İş Bağlantı Hizmetleri.](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14))

### <a name="content-type"></a>İçerik türü
 *İçerik Türü* öğeleri, belge, duyuru veya görev gibi varolan (temel) içerik türüne göre özel içerik türleri oluşturmanıza izin verir. Özel içerik türü, tanımladığınız tüm site sütunları (alanları) ile birlikte temel içerik türüyle aynı öznitelikleri ve alanları sağlar. Örneğin, SharePoint'te gelen temel Kişi içeriği türünü temel alan özel bir Kişi içeriği türü oluşturabilirsiniz. Varolan site sütunlarını değiştirerek veya temel içerik türüne zaten dahil olanlara daha fazla site sütunu ekleyerek içerik türünü özelleştirebilirsiniz.

> [!NOTE]
> SharePoint sınırlaması nedeniyle, kumlu çözüm içeriği türüne dayalı bir çiftlik çözümü içerik türü oluşturamazsınız.

 Daha fazla bilgi için [Bkz. Walkthrough: SharePoint ve](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) Building Block için bir site sütunu, içerik türü ve liste [oluşturun: İçerik Türü](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Boş öğe
 *Boş öğeler* genellikle Visual Studio'da proje veya proje öğesi şablonu bulunmayan SharePoint proje öğelerini tanımlamak için kullanılır. Projenize boş bir öğe eklediğinizde, EmptyElement[x]([x] benzersiz bir sayı\) nın oluşturulduğu bir düğüm oluşturulur. EmptyElement[x] *Elements.xml* adlı tek bir dosya içerir. [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] *Elements.xml'de*istenen öğeleri tanımlamak için ifadeleri kullanın.

### <a name="event-receiver"></a>Olay alıcısı
 *Olay alıcıları,* SharePoint sitesindeki bir öğenin listeye eklenmesi, bir web öğesinin silinmesi veya iş akışının başlatılması gibi öğelerin olaylarını işler. Olay alıcısı proje öğesi şablonu,

- Olayları listele

- Öğe olaylarını listele

- E-posta olaylarını listele

- Web etkinlikleri

- İş akışı olaylarını listele

  Olay alıcısı proje öğesi, **SharePoint Özelleştirme**Sihirbazı'nda projeyi oluştururken belirttiğiniz tüm olaylar için olay işleyicileri içeren tek bir sınıf dosyası içeren bir **Olay Alıcısı** klasörü oluşturur. Dosya, alan, öğe, liste, ek, web bölümleri ve iş akışları gibi öğeler eklendiğinde, güncellendiğinde, silindiğinde veya kaldırıldığında, olay alıcısı sınıfı SharePoint sitesinde oluşan olayları işleyebilir. Daha fazla bilgi için [bkz: Nasıl bir olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md) ve [Yapı Taşı: Olay Yönetimi.](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14))

### <a name="list"></a>Liste
 Liste, takvim veya görev listesi gibi yeniden kullanılabilir temel SharePoint listesi tanımının bir örneğidir. Çözüme bir liste ekledikten sonra, Liste Tasarımcısı listeye site sütunları eklemenize ve özel liste sütunları oluşturmanıza olanak tanır. Bu, içerik türlerinden site sütunlarını içerir. Listede görünecek sütunları belirleyen listenin *görünümünü* belirtebilirsiniz. Daha fazla bilgi için [Bkz. Walkthrough: SharePoint ve](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) Building Block için bir site sütunu, içerik türü ve liste [oluşturun: Listeler ve Belge Kitaplıkları.](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14))

### <a name="module"></a>Modül
 *Modüller* [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] (modüllerle karıştırılmamalıdır) görüntüler veya notlar gibi SharePoint sunucusuna dağıtmak istediğiniz dosyaları içerir. Modül proje öğesi bir **Modül** düğümü içerir. Modül düğümü iki proje öğesi şablonu içerir: modül için bir bildirim görevi gören bir XML tanım dosyası ve bir *sample.txt* dosyası, bir yer tutucu dosyası. Daha fazla bilgi için, Çözüme ve [Modüllere](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)) [Dosya Eklemek Için Modülleri Kullan'a](../sharepoint/using-modules-to-include-files-in-the-solution.md) bakın.

### <a name="sequential-workflow-farm-solution-only"></a>Sıralı iş akışı (yalnızca çiftlik çözümü)
 *Ardışık iş akışı,* son adım tamamlanana kadar sırayla gerçekleştirilen bir dizi iş mantığı adımıdır. Sıralı iş akışları, listeler ve belgeler gibi SharePoint öğelerini içeren işlemleri yönetmek için kullanılır. Site düzeyinde (genel) iş akışları veya liste düzeyinde (yerel) iş akışları oluşturabilir ve iş akışının otomatik olarak mı yoksa el ile mi başlatılmadığını seçebilirsiniz. Bu proje öğesi yalnızca çiftlik çözümlerinde kullanılabilir. Bu proje öğesini yalnızca çiftlik çözümlerine ekleyebilirsiniz. Daha fazla bilgi için bkz: [SharePoint iş akışı çözümleri oluştur](../sharepoint/creating-sharepoint-workflow-solutions.md), [SharePoint Server 2010'da İş Akışları](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))ve [Yenilikler: İş Akışı Geliştirmeleri](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Silverlight web parçası
 *Silverlight web parçası* proje öğeleri, SharePoint için Silverlight uygulamalarını görüntüleyen web parçaları oluşturmanıza olanak tanır. Bu proje öğesini çözümünüze eklediğinizde, yeni bir Silverlight uygulaması eklemeyi veya varolan bir uygulamaya daha sonra başvurup başvurmamayı seçebilirsiniz. Daha fazla bilgi için bkz: SharePoint ve Walkthrough [için web parçaları oluştur: SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) [için OData'yı görüntüleyen bir Silverlight web parçası oluşturun.](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)

### <a name="site-column"></a>Site sütunu
 *Alan*olarak da bilinen *bir site sütunu,* SharePoint projesine ekleyebileceğiniz en temel öğelerden biridir. Site sütunu, telefon numarası, metin yorumu veya kişi listesindeki bir ilgilinin şehir adı gibi bir veri türünü temsil eder. Daha fazla bilgi için bkz: SharePoint ve [Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)) [için site sütunları, içerik türleri ve listeler oluşturun.](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)

### <a name="site-definition-farm-solution-only"></a>Site tanımı (yalnızca çiftlik çözümü)
 *Site tanımı* proje öğeleri aşağıdaki dosyaları içeren bir site tanımı klasörü içerir:

- Varsayılan .aspx sayfası, site için varsayılan web sayfası olarak kullanılır.

- Sitenin bileşenlerini tanımlayan *onet.xml* dosyası.

- **Yeni SharePoint Site** sayfasının **Şablon Seçimi** bölümünde görünen site tanımı yapılandırmalarını belirten bir webtemp xml dosyası.

  Bir site tanımı ekledikten sonra, işlevselliği tanıtmak için kod ve dosya eklersiniz. Bu proje öğesi yalnızca çiftlik çözümlerinde kullanılabilir. Bu proje öğesini yalnızca çiftlik çözümlerine ekleyebilirsiniz. Daha fazla bilgi için [bkz.](../sharepoint/creating-site-definitions-for-sharepoint.md) [Site Definitions and Configurations](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14))

### <a name="state-machine-workflow-farm-solution-only"></a>Durum makine iş akışı (yalnızca çiftlik çözümü)
 *Durum makine iş akışı* iş mantığı durumları, geçişler ve eylemler kümesidir. Durum makine iş akışındaki adımlar sırayla gerçekleştirilmez; bunun yerine, eylemler ve durumlar tarafından tetiklenir. Sıralı iş akışı gibi, durum makine iş akışları da listeler ve belgeler gibi SharePoint öğeleriyle ilişkilidir. Bir kez daha, site düzeyinde (genel) iş akışları veya liste düzeyi (yerel) iş akışları oluşturabilirsiniz. Ayrıca, iş akışının otomatik olarak mı yoksa el ile mi başlatılmadığını da seçebilirsiniz. Bu proje öğesi yalnızca çiftlik çözümlerinde kullanılabilir. Bu proje öğesini yalnızca çiftlik çözümlerine ekleyebilirsiniz. Daha fazla bilgi için bkz: [SharePoint iş akışı çözümleri oluştur](../sharepoint/creating-sharepoint-workflow-solutions.md), [SharePoint Server 2010'da İş Akışları](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))ve [Yenilikler: İş Akışı Geliştirmeleri](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Kullanıcı denetimi (yalnızca çiftlik çözümü)
 *Kullanıcı denetimi,* diğer ASP.NET denetimleri ve SharePoint denetimleri ekleyebileceğiniz özel ve yeniden kullanılabilir bir denetimdir. Kullanıcı denetimi, SharePoint'te çalışan uygulama sayfalarına ve web bölümlerine eklenebilir. Bu proje öğesi yalnızca çiftlik çözümlerinde kullanılabilir. Bu proje öğesini yalnızca çiftlik çözümlerine ekleyebilirsiniz. Daha fazla bilgi için [bkz.](creating-reusable-controls-for-web-parts-or-application-pages.md)

### <a name="visual-web-part"></a>Görsel web bölümü
 *Görsel web bölümü* proje öğesi *elements.xml* tanım dosyası, bir **Web Bölümü** öğesi ve kullanıcı **denetimi** öğeiçerir. Görsel Stüdyo Araç Kutusu'ndan kullanıcı denetiminin yüzeyine denetimleri sürükleyerek veya kopyalayarak görsel web parçasının görünümünü tasarlayabilirsiniz. Daha fazla bilgi için bkz: Tasarımcı ve Yapı Bloğu [Kullanarak SharePoint web bölümü oluşturun:](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [Web Bölümleri.](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))

### <a name="web-part"></a>Web kısmı
 *Web bölümü,* Web Bölümü Sayfası adı verilen özel bir sayfa türü içinde çalışan sunucu tarafı denetimidir. Bunlar, SharePoint sitesinde görünen sayfaların yapı taşlarıdır. Web bölümü öğesi, SharePoint sitesi için bir web parçası tasarlamanızı sağlayan dosyalar sağlar. Daha fazla bilgi için [bkz: SharePoint web bölümü](../sharepoint/how-to-create-a-sharepoint-web-part.md) ve [Yapı Taşı oluşturma: Web Bölümleri.](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirin](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint Ürün ve Teknolojileri](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
