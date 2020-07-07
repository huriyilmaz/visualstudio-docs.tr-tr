---
title: 'İzlenecek yol: mevcut bir SharePoint sitesinden öğeleri Içeri aktarma | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46bc2ceacfde599a70b4e84bba134c4a4d5f9757
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017120"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>İzlenecek yol: mevcut bir SharePoint sitesinden öğeleri Içeri aktarma
  Bu izlenecek yol, mevcut bir SharePoint sitesinden SharePoint projesine nasıl öğe aktarılacağını gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel bir site sütunu ( *alan*olarak da bilinir) ekleyerek bir SharePoint sitesini özelleştirme.

- Bir SharePoint sitesini bir. wsp dosyasına aktarma.

- . Wsp dosyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . wsp Içeri aktarma projesini kullanarak SharePoint 'e aktarma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Ve SharePoint 'in desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] .

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>SharePoint sitesini özelleştirme
 Bu örnekte, üzerine yeni bir site sütunu ekleyerek ve daha sonra kullanmak üzere başka bir alt site oluşturarak bir SharePoint alt sitesi oluşturup özelleştirecek. Daha sonra, ilk alt siteyi bir. wsp dosyasına aktarır ve sonra. wsp Içeri aktarma projesini kullanarak özel site sütununu ikinci alt siteye içeri aktarabilirsiniz.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Bir SharePoint sitesi oluşturmak ve özelleştirmek için

1. Web tarayıcısını kullanarak bir SharePoint sitesini açın, örneğin http://<em>sistem adı</em>/SitePages/Home.exe.

2. **Site eylemleri** menüsünü açıp **Yeni site**' yi seçerek ana SharePoint sitesinden bir alt site oluşturun.

3. Sitenin **Oluştur** Iletişim kutusunda **boş site** türünü seçin.

4. **Başlık** kutusuna **site sütunu testi 1**' i girin. **URL adı** kutusuna **columntest1**; yazın. diğer ayarları varsayılan değerlerinde bırakın; ardından **Oluştur** düğmesini seçin.

5. Site oluşturulduktan sonra, tarayıcıda http://<em>sistem adı</em>/SitePages/Home.exe adlı ana siteye geri gidin.

6. Daha sonra, **Site eylemleri** menüsünü açıp **Yeni site**' yi seçip **boş site** türünü seçerek ana SharePoint sitesinden boş bir alt site oluşturun.

7. **Başlık** kutusuna **site sütunu test 2**yazın; **URL adı** kutusuna **columntest2**; yazın. diğer ayarları varsayılan değerlerinde bırakın; ardından **Oluştur** düğmesini seçin.

8. Http://<em>SystemName</em>/columntest1/default.exe adlı ilk alt siteye geri gidin.

9. Site **eylemleri** menüsünde, **Site Ayarları ' nı seçerek site** ayarları sayfasını görüntüleyin.

10. **Galeriler** bölümünde, **site sütunları** bağlantısını seçin.

11. **Site sütunu Galerisi** sayfasının en üstünde **Oluştur** düğmesini seçin.

12. **Sütun adı** kutusuna **Test sütunu**girin, diğer varsayılan değerleri koruyun ve **Tamam** düğmesini seçin.

13. **Test sütunu** sütunu, site sütunu galerisinde özel sütunlar başlığı altında görüntülenir.

## <a name="exporting-the-sharepoint-site"></a>SharePoint sitesi dışarı aktarılıyor
 Ardından, SharePoint projenize aktarmak istediğiniz SharePoint öğelerini ve öğelerini içeren bir SharePoint kurulum (. wsp) dosyası edinin [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Henüz bir. wsp dosyanız yoksa, mevcut bir SharePoint sitesinden bir tane oluşturmanız gerekir. Bu örnekte, varsayılan SharePoint sitesini bir. wsp dosyasına dışarı aktarcaksınız.

> [!IMPORTANT]
> Aşağıdaki yordamı gerçekleştirirken bir çalışma zamanı hatası alırsanız, yordamı SharePoint sitesine erişimi olan bir sistemde gerçekleştirmeniz gerekir.

### <a name="to-export-an-existing-sharepoint-site"></a>Var olan bir SharePoint sitesini dışarı aktarmak için

1. Site Ayarları sayfasını göstermek için SharePoint sitesinde site **eylemleri** sekmesinde **site ayarları** ' nı seçin.

2. Site Ayarları sayfasının **Site eylemleri** bölümünde **siteyi şablon olarak kaydet** bağlantısı ' nı seçin.

3. **Dosya adı** kutusuna **ExampleSite**girin ve **şablon adı** kutusuna **örnek site**girin.

4. Bu örnek için **Içerik Ekle** onay kutusunu boş bırakın.

     Bu kutuyu seçerseniz, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tüm listeleri ve belge kitaplıklarını ve bunların içeriğini. wsp dosyasına kaydeder. Bu, bazı durumlarda yararlı olsa da bu örnek için gerekli değildir.

5. İşlem başarıyla tamamlandığında,. wsp dosyasını görüntülemek için **Çözüm Galerisi** bağlantısını seçin.

     Çözüm Galerisi sayfasını daha sonra görüntülemek için, **Site eylemleri** menüsünü açın, site **ayarları**' nı seçin, **site koleksiyonu yönetimi** bölümünde **en üst düzeye git site ayarları** bağlantısını seçin ve ardından **galeriler** bölümünde **çözümler** bağlantısını seçin.

6. Çözümler galerisinde, **ExampleSite** bağlantısını seçin.

7. **Dosya indirme** iletişim kutusunda, dosyayı yerel sisteminize, varsayılan olarak, indirmeler klasörünüze kaydetmek için **Kaydet** düğmesini seçin.

## <a name="import-the-wsp-file"></a>. Wsp dosyasını içeri aktarma
 Artık yeniden kullanmak istediğiniz bir öğeyi içeren bir *. wsp* dosyanız olduğuna göre (özel site sütunu test sütunu), dosyaya erişmek için *. wsp* dosyasını içeri aktarın.

### <a name="to-import-a-wsp-file"></a>Bir. wsp dosyasını içeri aktarmak için

1. ' De [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , menü çubuğunda **File**  >  **New**  >  **Yeni** proje iletişim kutusunu göstermek için dosya yeni**Proje** ' yi seçin. IDE 'niz Visual Basic geliştirme ayarlarını kullanacak şekilde ayarlandıysa, menü çubuğunda **Dosya**  >  **Yeni proje**' yi seçin.

2. **Visual C#** veya **Visual Basic**altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **Şablonlar** bölmesinde **SharePoint 2010 çözüm paketini içeri aktar** ' ı seçin, projenin adını WspImportProject1 olarak bırakın ve **Tamam** düğmesini seçin.

    **SharePoint Özelleştirme Sihirbazı** görüntülenir.

4. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] daha önce oluşturduğunuz ikinci SharePoint alt sitesi için öğesini girin. Http://<em>sistem adı</em>/columntest2 adlı yeni özel alan öğesini bu alt siteye eklersiniz.

5. **Bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, seçimi **bir korumalı çözüm olarak dağıt**olarak bırakın.

6. **Yeni proje kaynağını belirtin** sayfasında, daha önce *. wsp* dosyasını kaydettiğiniz sistemdeki konuma gidin ve sonra **İleri** düğmesini seçin.

   > [!NOTE]
   > Bu sayfada **son** düğmesini seçerseniz, *. wsp* dosyasındaki tüm kullanılabilir öğeler içeri aktarılır.

7. **İçeri aktarılacak öğeleri seçin** kutusunda, listede **Test sütunu**hariç tüm onay kutularını temizleyin ve ardından **son** düğmesini seçin.

    Listede çok sayıda öğe bulunduğundan, listedeki tüm öğeleri seçmek için **CTRL** + **tuşuna** basın ' ı seçebilirsiniz, tüm onay kutularını temizlemek için ara çubuğu tuşunu ve ardından yalnızca **Test sütunu** öğesinin yanındaki onay kutusunu seçebilirsiniz.

    İçeri aktarma işlemi tamamlandıktan sonra, **alanlar**adlı bir klasör içeren **WspImportProject1** adlı yeni bir proje oluşturulur. Bu klasörde özel site sütunu **Test sütunu** ve tanım dosyası *Elements.xml*.

## <a name="deploy-the-project"></a>Projeyi dağıtma
 Son olarak, özel site sütununu görüntülemek için daha önce oluşturduğunuz ikinci SharePoint alt sitesine **WspImportProject1** dağıtın.

### <a name="to-deploy-the-project"></a>Projeyi dağıtmak için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , *. wsp* içeri aktarma projesini dağıtmak ve çalıştırmak için **F5** tuşunu seçin.

2. SharePoint sitesinde, site **eylemleri** menüsünü açın ve ardından site **ayarları** ' nı seçerek site ayarları sayfasını görüntüleyin.

3. **Galeriler** bölümünde, **site sütunları** bağlantısını seçin.

4. **Özel sütunlar** bölümüne aşağı kaydırın.

     İlk SharePoint sitesinden içeri aktardığınız özel site sütununun listede göründüğünü unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Mevcut bir SharePoint sitesinden öğeleri içeri aktar](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
