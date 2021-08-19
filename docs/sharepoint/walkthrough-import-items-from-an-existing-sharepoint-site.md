---
title: 'adım adım kılavuz: Mevcut bir SharePoint Site | Microsoft Docs'
titleSuffix: ''
description: Bu kılavuzda, mevcut bir sitedeki öğeleri SharePoint bir Visual Studio SharePoint aktarın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 17f16b02749fe1431f1016334c96855ee505a0a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115362"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Adım adım kılavuz: Mevcut bir siteden öğeleri SharePoint alma
  Bu kılavuzda, mevcut bir sitedeki öğeleri SharePoint bir SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] gösterir.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Özel bir SharePoint (alan olarak da bilinir) ekleyerek bir siteyi *özelleştirme.*

- Bir SharePoint .wsp dosyasına dışarı aktarma.

- .wsp dosyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .wsp import SharePoint kullanarak .wsp dosyasına aktarma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen ve [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] SharePoint.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Bir siteyi SharePoint özelleştirme
 Bu örnekte, yeni bir site sütunu SharePoint ve daha sonra kullanmak üzere başka bir alt site oluşturarak yeni bir site oluşturacak ve özelleştirebilirsiniz. Daha sonra, ilk alt siteyi bir .wsp dosyasına aktaracak ve ardından .wsp Import projesini kullanarak özel site sütununu ikinci alt siteye içeri aktarın.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Bir siteyi oluşturmak ve SharePoint için

1. <em>/Site</em>SharePoint Pages/Home.aspx gibi bir web http:// kullanarak bir web sitesi açın.

2. Site Eylemleri menüsünü açarak ve ardından Yeni SharePoint'ı seçerek ana **sitenin** dışında bir alt **site oluşturun.**

3. Sitenin Oluştur **iletişim** kutusunda Boş Site **türünü** seçin.

4. Başlık **kutusuna Site** Sütunu **Test 1** girin; URL **adı kutusuna** **columntest1** girin; diğer ayarları varsayılan değerlerinde bırakın; ve ardından Oluştur **düğmesini** seçin.

5. Site oluşturulduktan sonra tarayıcıda ana siteye geri gidin ve<em></em>/SitePages/Home.aspx http:// sistem adını girin.

6. Yine Site Eylemleri menüsünü açarak, Yeni Site 'SharePoint'ı ve ardından Boş **Site** türünü seçerek ana sitenin dışında boş bir **alt site** oluşturun.

7. Başlık **kutusuna Site** Sütun **Testi 2** girin; URL **adı kutusuna** **columntest2** yazın; diğer ayarları varsayılan değerlerinde bırakın; ve ardından Oluştur **düğmesini** seçin.

8. <em>SystemName</em>/columntest1/default.aspx http:// adlı ilk alt siteye dönün.

9. Site **Eylemleri menüsünde Site** eylemleri sayfasını **görüntülemek Ayarlar** Site Eylemleri'Ayarlar seçin.

10. Galeriler **bölümünde** Site sütunları **bağlantısını** seçin.

11. **Site** Sütun Galerisi sayfasının üst kısmında Oluştur **düğmesini** seçin.

12. Sütun **adı kutusuna** **Test** Sütunu yazın, diğer varsayılan değerleri tutun ve tamam **düğmesini** seçin.

13. **Test Sütunu sütunu,** Site Sütun Galerisi'nin Özel Sütunlar başlığı altında görünür.

## <a name="exporting-the-sharepoint-site"></a>SharePoint dışarı aktarma
 Ardından, SharePoint projenize içeri SharePoint öğeleri içeren bir SharePoint kurulum (.wsp) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dosyası alın. Henüz bir .wsp dosyanız yoksa, mevcut bir siteden bir .wsp SharePoint oluşturmanız gerekir. Bu örnek için, varsayılan siteyi SharePoint bir .wsp dosyasına aktarın.

> [!IMPORTANT]
> Aşağıdaki yordamı gerçekleştiren bir çalışma zamanı hatası alırsanız, yordamı SharePoint sitesine erişimi olan bir sistemde gerçekleştirmeniz gerekir.

### <a name="to-export-an-existing-sharepoint-site"></a>Mevcut bir siteyi dışarı SharePoint için

1. Site SharePoint Site Eylemleri sekmesinde **site** **Ayarlar'ı** seçecek ve Site Ayarlar görüntüleyebilirsiniz.

2. Site **Şablonu sayfasının** Site Eylemleri Ayarlar Siteyi şablon olarak **kaydet bağlantısını** seçin.

3. Dosya **adı kutusuna** **ExampleSite girin** ve Şablon adı **kutusuna Örnek** Site **girin.**

4. Bu örnek için İçerik Dahil **Edin onay** kutusunu boş bırakın.

     Bu kutuyu seçersiniz, tüm listeleri ve belge kitaplıklarını ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] içeriklerini .wsp dosyasına kaydeder. Bu bazı durumlarda yararlı olsa da, bu örnek için gerekli değildir.

5. İşlem başarıyla tamamlandığında, .wsp **dosyasını görüntülemek** için çözüm galerisi bağlantısını seçin.

     Çözüm galerisi sayfasını daha sonra görüntülemek  için **Site** Eylemleri menüsünü açın, Site **Ayarlar'ı** seçin, **Site** Koleksiyonu Yönetimi bölümünde En üst düzey **site** ayarlarına git bağlantısını seçin ve galeriler bölümünde Çözümler bağlantısını seçin. 

6. Çözüm galerisinde **ExampleSite bağlantısını** seçin.

7. Dosya İndirme **iletişim** kutusunda, dosyayı varsayılan **olarak** İndirilenler klasörünüzdeki yerel sisteminize kaydetmek için Kaydet düğmesini seçin.

## <a name="import-the-wsp-file"></a>.wsp dosyasını içeri aktarma
 Artık yeniden kullanmak istediğiniz *bir öğeyi içeren bir .wsp* dosyanız (özel site sütunu Test Sütunu) sahip olduğunuza göre, buna erişmek için *.wsp* dosyasını içeri aktarın.

### <a name="to-import-a-wsp-file"></a>Bir .wsp dosyasını içeri aktarma

1. menüsünde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Yeni Dosya iletişim kutusunu görüntülemek **için**  >    >  **Project** **Yeni Dosya'Project** seçin. IDE'niz geliştirme ayarlarını Visual Basic olarak ayarlanmışsa, menü çubuğunda Dosya **Yeni**  >  **dosya'Project.**

2. Visual **C# SharePoint** altındaki  Visual Basic düğümünü **genişletin** ve **ardından 2010 düğümünü** seçin.

3. Şablonlar **bölmesinde SharePoint 2010** Çözüm Paketi şablonunu  seçin, projenin adını WspImportProject1 olarak bırakın ve ardından **Tamam düğmesini** seçin.

    SharePoint **Özelleştirme Sihirbazı** görüntülenir.

4. Hata **ayıklama için siteyi ve güvenlik düzeyini belirtin** sayfasında, daha önce oluşturduğunuz ikinci SharePoint site için [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] girin. Yeni özel Alan öğesini (http://<em>sistem</em>adı /columntest2) bu alt siteye eksersiniz.

5. Bu **çözüm için güven düzeyi nedir? SharePoint,** seçimi Korumalı alanlı çözüm olarak **dağıt olarak bırakın.**

6. Yeni **proje kaynağını belirtin sayfasında,** daha önce *.wsp* dosyasını kaydedip Sonraki düğmesini seçtiğiniz sistem konumunu **bulun.**

   > [!NOTE]
   > Bu sayfada Son **düğmesini** seçerseniz, *.wsp* dosyasındaki tüm kullanılabilir öğeler içe aktarılır.

7. İçeri **aktar menüsünde,** **Test** Sütunu dışındaki tüm onay kutularını temizleyin ve ardından Son **düğmesini** seçin.

    Listede çok sayıda öğe **olduğundan, Ctrl** A tuşlarını seçerek listede yer alan tüm öğeleri seçebilir, tüm onay kutularını temizlemek için Ara Çubuğu tuşunu ve ardından yalnızca Test Sütunu öğesinin yanındaki onay kutusunu +   seçebilirsiniz.

    İçeri aktarma işlemi tamam olduktan **sonra, Alanlar** adlı bir klasör içeren **WspImportProject1** adlı yeni bir proje oluşturulur. Bu klasörde özel site sütunu Test Sütunu **ve** tanım dosyası *Elements.xml.*

## <a name="deploy-the-project"></a>Projeyi dağıtma
 Son olarak, özel site sütununu görüntülemek için **wspImportProject1 SharePoint** oluşturduğunuz ikinci alt siteye dağıtın.

### <a name="to-deploy-the-project"></a>Projeyi dağıtmak için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , *.wsp* içeri aktarma projesini dağıtmak ve çalıştırmak için **F5** anahtarını seçin.

2. Site SharePoint Site Eylemleri menüsünü açın ve **site** eylemleri sayfasını görüntülemek için **Site Ayarlar'Ayarlar** seçin.

3. Galeriler **bölümünde** Site sütunları **bağlantısını** seçin.

4. Ekranı aşağı kaydırarak **Özel Sütunlar bölümüne** gidin.

     İlk siteden içe aktarılmış özel site sütun SharePoint listede göründüğüne dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.
- [Mevcut bir siteden öğeleri SharePoint alma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
