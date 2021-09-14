---
title: SharePoint Project ve Project öğe şablonları | Microsoft Docs
description: kullanılabilir SharePoint proje ve proje öğesi şablonlarının açıklamalarını ve bunların nasıl kullanıldığını gözden geçirin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636833"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint projesi ve proje öğesi şablonları
  aşağıdaki bölümlerde, kullanılabilir SharePoint projesi ve proje öğesi şablonları ve bunların nasıl kullanıldığı açıklanır.

## <a name="project-and-project-item-templates-overview"></a>Project ve proje öğesi şablonlarına genel bakış
 Visual Studio yeni bir SharePoint projesi oluşturduğunuzda, bu proje türü için gereken tüm proje öğeleriyle birlikte çözüme bir SharePoint projesi eklenir. örneğin, bir silverlight web bölümü projesi oluşturursanız Visual Studio, bir Visual Web bölümü proje öğesi ve bir silverlight uygulaması proje öğesi içeren bir çözüm oluşturur ve bu proje öğeleri için gereken tüm dosyaları içerir. Project öğe şablonları, bir olay alıcısı, site sütunu veya liste ekleme gibi var olan bir SharePoint projesine proje öğeleri eklemek için kullanılır.

 SharePoint temelleri hakkında daha fazla bilgi için bkz. [SharePoint Foundation yapı taşları](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Gelişmiş kullanıcılar, özel proje ve proje öğesi şablonları oluşturabilir. daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Project şablonları
 SharePoint proje şablonlarının listesi aşağıda verilmiştir. Visual Studio SharePoint proje şablonlarını görüntülemek için, **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** altındaki **SharePoint** düğümünü genişletin ve ardından **2010** öğesini seçin.

### <a name="sharepoint-2010-project"></a>SharePoint 2010 projesi
 *SharePoint 2010 Project* içerikleri her SharePoint proje şablonuna dahil edilmiştir. SharePoint 2010 Project şunları içerir:

- Bir proje dosyası.

- Proje Özellikleri sayfası.

- Projedeki tüm derleme başvurularını listeleyerek **Başvurular** klasörü.

- SharePoint sunucusuna özellikleri dağıtmak için kullanılan *. feature* yapılandırma dosyasını içeren bir **özellikler** klasörü.

- Çözümü SharePoint dağıtmak için kullanılan *Package. Package* dosyasını Içeren bir **paket** klasörü.

- Gelişmiş güvenlik için derlemeyi güçlü bir adla imzalamak için kullanılan Key. snk (tanımlayıcı-ad anahtarı) dosyası.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight web bölümü
 *SharePoint 2010 silverlight Web bölümü* projeleri, silverlight uygulamalarını görüntüleyen SharePoint için web bölümleri oluşturmanızı sağlar. Bu projeyi oluştururken, buna yeni bir Silverlight uygulaması eklenip eklenmeyeceğini veya var olan bir projeye başvurulacağını belirtebilirsiniz. daha fazla bilgi için bkz. [SharePoint web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md) ve [izlenecek yol: SharePoint için OData görüntüleyen bir Silverlight web bölümü oluşturma](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 visual web bölümü
 *SharePoint 2010 Visual Web bölümü* projesi bir *Elements.xml* tanım dosyası, bir **Web bölümü** öğesi ve bir **kullanıcı denetim** öğesi içerir. Visual Studio araç kutusundan denetimleri kullanıcı denetimi yüzeyine sürükleyerek veya kopyalayarak görsel web bölümünün görünümünü tasarlayabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: tasarımcı ve yapı bloğu kullanarak SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [: Web Bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010 çözüm paketini içeri aktar
 *içeri aktarma SharePoint 2010 çözüm paketi* projeleri, var olan bir SharePoint 2010 sitesinin tümünü veya bir kısmını Visual Studio SharePoint çözüm (*. wsp*) dosyasına dışarı aktarmanıza olanak tanır. Visual Studio içine aktarıldıktan sonra, öğelerini özelleştirebilir ve yeniden dağıtabilirsiniz. daha fazla bilgi için bkz. [mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>yeniden kullanılabilir SharePoint 2010 iş akışını içeri aktar
 yeniden *kullanılabilir SharePoint 2010 iş akışı* projeleri, SharePoint tasarımcı 2010 ' de oluşturulan yeniden kullanılabilir, bildirime dayalı bir iş akışını Visual Studio içine aktarmanızı sağlar iş akışı, SharePoint sitesinden *. wsp* dosyası olarak verilir. Visual Studio içine aktarıldıktan sonra, bunu özelleştirebilir, kod ekleyebilir ve sonra bir SharePoint sitesine dağıtabilirsiniz. daha fazla bilgi için bkz. [izlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio içine aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Project öğesi şablonları
 SharePoint proje öğesi şablonlarının listesi aşağıda verilmiştir. Project öğe şablonları, site sütunları, listeler ve içerik türleri gibi SharePoint işlevselliğini desteklemek için SharePoint çözümüne dosya ekler. Örneğin, çözümünüze bir site sütunu eklemek *Elements.xml* tanım dosyası içeren bir site sütunu projesi ekler. Visual Web Bölümü eklemek, çözümünüze bir *Elements.xml* dosyası, bir kullanıcı denetim öğesi ve bir görsel web bölümü öğesi içeren bir görsel web bölümü projesi ekler.

 SharePoint proje öğesi şablonlarını görüntülemek için **Çözüm Gezgini**, bir SharePoint projesinin kısayol menüsünü açın ve sonra **ekle**, **yeni öğe**' yi seçin. **Visual C#** veya **Visual Basic** altındaki **SharePoint** düğümünü genişletin ve ardından **2010** öğesini seçin.

### <a name="application-page-farm-solution-only"></a>Uygulama sayfası (yalnızca Grup çözümü)
 bir **uygulama sayfası (yalnızca grup çözümü)** öğesi, [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] bir SharePoint sitesi için web sayfası tasarlamanıza olanak sağlar. Uygulamalar sayfaları yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca Grup çözümlerine ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama sayfası](../sharepoint/how-to-create-an-application-page.md) ve [uygulama _layouts sayfa türü](/previous-versions/office/aa979604(v=office.14))oluşturma.

### <a name="business-data-connectivity-model-farm-solution-only"></a>İş verileri bağlantı modeli (yalnızca Grup çözümü)
 **Iş verileri bağlantı modeli (yalnızca Grup çözümü)** öğesi, iş verilerini SharePoint ile tümleştirmenize olanak sağlar. İş verileri [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] , Siebel ve Service Advertising Protokolü (SAP) gibi arka uç sunucu uygulamalarından gelebilir. İş verileri bağlantı modelleri yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca Grup çözümlerine ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md), [nasıl yapılır: Yerelleştirilmiş adlar, Özellikler ve Izinleri belirtmek Için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)ve yenilikler [: iş bağlantı Hizmetleri](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>İçerik türü
 *Içerik türü* öğeleri, bir belge, duyuru veya bir görev gibi var olan (temel) içerik türünü temel alan özel içerik türleri oluşturmanızı sağlar. Özel bir içerik türü, tanımladığınız tüm site sütunları (alanları) ile birlikte temel içerik türüyle aynı öznitelikleri ve alanları sağlar. Örneğin, SharePoint gelen temel kişi içerik türünü temel alan özel bir Iletişim içeriği türü oluşturabilirsiniz. Varolan site sütunlarını değiştirerek veya temel içerik türüne dahil olan olanlara daha fazla site sütunu ekleyerek içerik türünü özelleştirebilirsiniz.

> [!NOTE]
> SharePoint sınırlaması nedeniyle, korumalı çözüm içerik türünü temel alan bir grup çözümü içerik türü oluşturamazsınız.

 daha fazla bilgi için bkz. [izlenecek yol: site sütunu, içerik türü ve SharePoint ve yapı bloğu için liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) [: içerik türü](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Boş öğe
 *boş öğeler* çoğunlukla, Visual Studio bir proje veya proje öğesi şablonu olmayan SharePoint proje öğelerini tanımlamak için kullanılır. Projenize boş bir öğe eklediğinizde, EmptyElement [x] adlı bir düğüm (burada [x] benzersiz bir sayıdır) \) oluşturulur. EmptyElement [x],Elements.xml adlı tek bir dosya içerir *.* [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] *Elements.xml* istenen öğeleri tanımlamak için deyimlerini kullanın.

### <a name="event-receiver"></a>Olay alıcısı
 *olay alıcıları* , bir listeye bir öğe eklendiğinde, bir web öğesi silindiğinde veya bir iş akışı başlatıldığında olduğu gibi SharePoint sitesindeki öğelerin olaylarını işler. Olay alıcısı proje öğesi şablonu, idare etmenizi sağlar

- Olayları listeleme

- Öğe olaylarını listeleme

- E-posta olaylarını listeleme

- Web olayları

- İş akışı olaylarını listeleme

  olay alıcısı proje öğesi, **SharePoint özelleştirme sihirbazında** projeyi oluştururken belirttiğiniz tüm olaylar için olay işleyicileri içeren tek bir sınıf dosyası içeren bir **olay alıcısı** klasörü oluşturur. olay alıcısı sınıfı, dosyalar, alanlar, öğeler, listeler, ekler, web bölümleri ve iş akışları gibi öğeler eklendiğinde, güncelleştirilirken, silindiğinde veya kaldırıldığında SharePoint sitesinde gerçekleşen olayları işleyebilir. Daha fazla bilgi için bkz. [nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md) ve [derleme bloğu: olay işleme](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>Liste
 liste, bir takvim veya görev listesi gibi yeniden kullanılabilir bir temel SharePoint liste tanımının bir örneğidir. Çözümünüze bir liste eklendikten sonra liste Tasarımcısı, listeye site sütunları eklemenize ve özel liste sütunları oluşturmanıza olanak sağlar. Bu, içerik türlerinden site sütunları içerir. Liste için, listede görünecek sütunları belirleyen *görünümü* belirtebilirsiniz. daha fazla bilgi için bkz. [izlenecek yol: site sütunu, içerik türü ve SharePoint ve yapı bloğu için liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) [: listeler ve belge kitaplıkları](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Modül
 *modüller* ( [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] modüllerle karıştırılmamalıdır), görüntü veya not gibi SharePoint sunucusuna dağıtmak istediğiniz herhangi bir dosyayı içerir. Modül proje öğesi bir **Modül** düğümü içerir. Modül düğümü iki proje öğesi şablonu içerir: modül için bildirim olarak davranan bir XML tanım dosyası ve bir *sample.txt* dosyası, yer tutucu dosyası. Daha fazla bilgi için bkz. çözüm ve [modüllerde](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)) [dosya eklemek için modülleri kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md) .

### <a name="sequential-workflow-farm-solution-only"></a>Sıralı iş akışı (yalnızca Grup çözümü)
 *Sıralı bir iş akışı* , son adım tamamlanana kadar sırayla gerçekleştirilen bir dizi iş mantığı adımıdır. sıralı iş akışları, listeler ve belgeler gibi SharePoint öğeleri içeren süreçler yönetmek için kullanılır. Site düzeyi (genel) iş akışları veya liste düzeyi (yerel) iş akışları oluşturabilir ve bir iş akışının otomatik olarak mı yoksa el ile mi başlayacağını belirleyebilirsiniz. Bu proje öğesi yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca Grup çözümlerine ekleyebilirsiniz. daha fazla bilgi için bkz. [Create SharePoint workflow solutions](../sharepoint/creating-sharepoint-workflow-solutions.md), [SharePoint Server 2010 ' deki iş akışları](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))ve yenilikler [: iş akışı geliştirmeleri](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Silverlight Web Bölümü
 *silverlight web bölümü* proje öğeleri, silverlight uygulamalarını görüntüleyen SharePoint için web bölümleri oluşturmanızı sağlar. Çözümünüze bu proje öğesini eklediğinizde, yeni bir Silverlight uygulaması eklenip eklenmeyeceğini veya daha sonra var olan bir sürüme başvurulacağını seçebilirsiniz. daha fazla bilgi için bkz. [SharePoint web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md) ve [izlenecek yol: SharePoint için OData görüntüleyen bir Silverlight web bölümü oluşturma](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Site sütunu
 *alan* olarak da bilinen bir *site sütunu*, bir SharePoint projesine ekleyebileceğiniz en temel öğelerden biridir. Bir site sütunu, telefon numarası, metin yorumu veya iletişim listesindeki kişinin şehir adı gibi bir veri türünü temsil eder. daha fazla bilgi için bkz. SharePoint ve [sütunları](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)) [için site sütunları, içerik türleri ve listeler oluşturma](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) .

### <a name="site-definition-farm-solution-only"></a>Site tanımı (yalnızca Grup çözümü)
 *Site tanımı* proje öğeleri, aşağıdaki dosyaları içeren bir site tanımı klasörü içerir:

- Site için varsayılan Web sayfası olarak kullanılan default. aspx sayfası.

- Sitenin bileşenlerini tanımlayan bir *onet.xml* dosyası.

- **yeni SharePoint site** sayfasının **şablon seçimi** bölümünde görünen site tanımı yapılandırmasını belirten bir webtemp xml dosyası.

  Bir site tanımı ekledikten sonra işlevselliği tanıtmak için kod ve dosyaları eklersiniz. Bu proje öğesi yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca Grup çözümlerine ekleyebilirsiniz. daha fazla bilgi için bkz. SharePoint ve [site tanımları ve yapılandırma](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)) [için site tanımları oluşturma](../sharepoint/creating-site-definitions-for-sharepoint.md) .

### <a name="state-machine-workflow-farm-solution-only"></a>Durum makinesi iş akışı (yalnızca Grup çözümü)
 Bir *durum makinesi iş akışı* , iş mantığı durumları, geçişler ve eylemler kümesidir. Bir durum makinesi iş akışındaki adımlar sırayla gerçekleştirilmez; Bunun yerine, Eylemler ve durumlar tarafından tetiklenir. sıralı bir iş akışı gibi, durum makine iş akışları listeler ve belgeler gibi SharePoint öğelerle ilişkilendirilir. Bir kez daha, site düzeyi (genel) iş akışları veya liste düzeyi (yerel) iş akışları oluşturabilirsiniz. Ayrıca, bir iş akışının otomatik olarak mı yoksa el ile mi başlayacağını seçebilirsiniz. Bu proje öğesi yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca Grup çözümlerine ekleyebilirsiniz. daha fazla bilgi için bkz. [Create SharePoint workflow solutions](../sharepoint/creating-sharepoint-workflow-solutions.md), [SharePoint Server 2010 ' deki iş akışları](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))ve yenilikler [: iş akışı geliştirmeleri](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Kullanıcı denetimi (yalnızca Grup çözümü)
 *kullanıcı denetimi* , diğer ASP.NET denetimleri ve SharePoint denetimleri ekleyebileceğiniz özel, yeniden kullanılabilir bir denetimdir. Kullanıcı denetimi, SharePoint ' de çalışan uygulama sayfalarına ve Web bölümlerine eklenebilir. Bu proje öğesi yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesini yalnızca Grup çözümlerine ekleyebilirsiniz. daha fazla bilgi için bkz. [Web Bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Görsel web bölümü
 *Visual Web Bölümü* proje öğesi *Elements.xml* bir tanım dosyası, bir **Web Bölümü** öğesi ve bir **Kullanıcı denetim** öğesi içerir. Visual Studio araç kutusundan denetimleri kullanıcı denetimi yüzeyine sürükleyerek veya kopyalayarak görsel web bölümünün görünümünü tasarlayabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: tasarımcı ve yapı bloğu kullanarak SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [: Web Bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web kısmı
 *Web Bölümü* , Web Bölümü sayfası adlı özel bir sayfa türünün içinde çalışan bir sunucu tarafı denetimidir. bunlar, SharePoint sitesinde görünen sayfaların yapı taşlarıdır. web bölümü öğesi, bir SharePoint sitesi için bir web bölümü tasarlamanıza olanak sağlayan dosyalar sağlar. daha fazla bilgi için bkz. [nasıl yapılır: oluşturma SharePoint web bölümü](../sharepoint/how-to-create-a-sharepoint-web-part.md) ve [yapı bloğu: Web Bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint Ürünler ve teknolojiler](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
