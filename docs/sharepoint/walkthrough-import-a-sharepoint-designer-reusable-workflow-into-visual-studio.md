---
title: 'Adım adım kılavuz: SharePoint Tasarımcısı yeniden kullanılabilir iş akışı akışını içeri | Microsoft Docs'
titleSuffix: ''
description: Bu kılavuzda, SharePoint Designer'da oluşturulan yeniden Visual Studio SharePoint iş akışı projesine aktarın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ab8357b126ab2bfacea24cd3b922baa40fb25da4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628208"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>Adım adım kılavuz: SharePoint Tasarımcısı yeniden kullanılabilir iş akışını içeri aktarma

  Bu kılavuzda, SharePoint Designer 2010'da oluşturulan yeniden kullanılabilir iş akışını bir iş akışı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projesine SharePoint nasıl içeri aktarabilirsiniz.

 SharePoint Designer'da oluşturulan iş akışları veya bildirimli *iş akışları,* kod [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] yerine deyimlerden oluşur. SharePoint Tasarımcı 2010' da, sitelerde farklı listeler tarafından kullanılmaktadır taşınabilir, bildirime açık iş akışları olan yeniden kullanılabilir iş SharePoint tanıtır.

 içinde oluşturulan sıralı [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] ve durum makinesi iş akışları gibi iş akışlarına kod iş akışları *denir.* Kod iş akışları, kullanıcıların iş akışının davranışını özelleştirebileceğiniz XML dosya ve kod modüllerinden oluşur.

 Visual Studio, SharePoint Designer 2010'da oluşturulan yeniden kullanılabilir iş akışlarını içeri aktarmanıza ve bunları sitelerde kullanmak üzere kod iş akışlarına SharePoint sağlar.

 Bu kılavuz aşağıdaki görevleri gösterir:

- SharePoint Designer'da basit, yeniden kullanılabilir bir iş akışı oluşturma.

- SharePoint Tasarımcısı yeniden kullanılabilir iş akışını bir *.wsp* dosyasına ve bir .wsp dosyasına SharePoint.

- Yeniden Kullanılabilir İş Akışını İçeri Aktar projesini kullanarak *.wsp* [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dosyasını içine aktarma.

- Kod ekleyerek iş akışını değiştirme.

- İçe aktarılan iş akışını bir SharePoint kullanma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen ve sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] SharePoint.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Hedef SharePoint siteleri oluşturma
 İlk olarak iki yeni SharePoint oluşturun: biri SharePoint Designer'dan yeniden kullanılabilir iş akışlarını barındırmak için, diğeri dönüştürülen iş akışlarını barındırmak için.

#### <a name="to-create-sharepoint-subsites"></a>SharePoint alt siteleri oluşturmak için

1. Tasarımcı SharePoint 2010'da, menü çubuğunda Dosya Yeni **Boş**  >  **Web Sitesi'ne tıklayın.**

2. Yeni **Boş Web Sitesi** iletişim kutusunda, iş akışını oluşturmak istediğiniz bir SharePoint sitesine göz atabilir veya http://<em>SystemName</em>/ değerini kullanarak Tamam **düğmesini** seçin.

    Giriş sayfası görüntülenir.

3. Alt **siteler bölümünde** Yeni **düğmesini** seçin.

4. Yeni **iletişim** kutusunda, **sol bölmede SharePoint** Listeden Yeni Şablonlar'ı  ve sağ bölmede listeden Takım Sitesi'ni seçin.

5. Web **sitesinin konumunu belirtin kutusunda** URL'de alt **site** sözcüğü yerine **SPD1** yazın ve Tamam **düğmesini** seçin.

    Bu, yeni alt siteyi SharePoint açar. SharePoint Designer'ın bu örneğini kapatın ve ilk örnek (üst düzey site) geri gidin.

6. İkinci alt siteyi oluşturmak için 3- 5 arası adımları tekrarlayın, bu kez içinde alt **site** [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] sözcüğü **SPD2 ile değiştirildi.**

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Tasarımcısı yeniden kullanılabilir iş akışı oluşturma
 Bu SharePoint için kullanabileceğiniz herhangi bir yeniden kullanılabilir iş akışı içermeyebilirsiniz, bir iş akışı oluşturabilirsiniz. Bu basit iş akışında, bir kullanıcı Görev listesine belirli bir başlığı olan yeni bir görev girdiği zaman, görev o kullanıcıya atanır.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer yeniden kullanılabilir iş akışı oluşturmak için

1. Alt **siteler bölümünde,** değiştirmek için **SPD1** sitesini seçin.

2. Şeritte Yeniden Kullanılabilir **İş Akışı düğmesini** seçin.

     Yeniden Kullanılabilir İş Akışı Oluşturma sihirbazı görüntülenir.

3. Ad **kutusuna** SPD Görev **İş Akışı yazın.**

4. İçerik **Türü listesinde Görev'i** **ve** ardından Tamam **düğmesini** seçin.

     İş akışı, SharePoint Tasarımcısı iş akışı tasarımcısında açılır.

5. İş akışı tasarımcısında 1. Adım'ı seçin ve şeritte Koşul **düğmesini** seçin.

6. Koşullar listesinde Geçerli öğe alanı **değerine eşitse'yi seçin.**

     Bu adım, If alanı değerine **eşitse adlı bir koşul ekler.**

7. If **alanında değer koşulu eşittir** alanında alan **bağlantısını** seçin.

8. Değer listesinde Başlık'ı **seçin.**

9. If **alanında değer koşulu eşittir** alanında değer **bağlantısını** seçin.

10. Kutuya Yeni görev **yazın.**

     Condition deyimi artık If **Current Item:Title equals New task (Geçerli Öğe:Başlık yeni görevse) ifadesini okur.**

11. Condition deyiminin altındaki satırı seçin ve şeritte Eylem **düğmesini** seçin.

12. Eylem listesinde, Geçerli öğede **alanı ayarla'ya tıklayın.**

13. Alan **değerini ayarla eylem alanında** alan **bağlantısını seçin** ve sonra listede Atanan'ı **seçin.**

14. Değer **olarak ayarla eylem alanında**  değer bağlantısını seçin ve ardından mevcut kullanıcılar ve gruplar listesinde öğesini oluşturan **kullanıcı'ya tıklayın.**

15. Ekle **düğmesini** ve ardından Tamam **düğmesini** seçin.

     Eylem deyimi artık Set **Atanan To Current Item:CreatedBy (Geçerli Öğe:CreatedBy) olarak ayarlanmıştır.**

## <a name="save-and-deploy-the-reusable-workflow"></a>Yeniden kullanılabilir iş akışını kaydetme ve dağıtma
 Yalnızca .wsp dosyalarını içeri aktarana kadar, yeniden kullanılabilir iş akışını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] *bir .wsp* dosyası olarak kaydetmeli ve içine aktarmadan önce SharePoint dosyasına dağıtmanız  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] gerekir.

> [!IMPORTANT]
> Aşağıdaki yordamı gerçekleştiren bir çalışma zamanı hatası alırsanız, yordamı SharePoint sitesine erişimi olan bir sistemde gerçekleştirmeniz gerekir.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Yeniden kullanılabilir iş akışını kaydetmek ve dağıtmak için

1. SharePoint Tasarımcısı'nın üst kısmında Kaydet  düğmesini seçen ve ilerleme durumunuz  kaydedecek ve ardından Yayımla düğmesini seçecek şekilde iş akışını **SPD1** SharePoint dağıtın.

2. Gezinti bölmesinde İş Akışları **nesnesini** seçin.

3. Yeniden **Kullanılabilir İş Akışı altında** SPD Görev İş **Akışı'ı seçin.**

4. Şeritte Şablon Olarak Kaydet **düğmesini seçerek** iş akışını *bir .wsp dosyası olarak* kaydedin.

5. *.wsp* dosyasını SharePoint için **SPD1** SharePoint sitesini tarayıcıda SharePoint.

6. QuickLaunch çubuğunda Kitaplıklar **bağlantısını** seçin.

7. Belge **Kitaplıkları bölümünde** Site Varlıkları **bağlantısını** seçin.

     **SPD Görev İş Akışı** dosyası diğer site varlıklarıyla listelenir.

8. Dosya listesinde bu dosyanın adını seçin

9. *.wsp* **dosyasını** yerel **sisteminize kaydetmek** için Dosya İndirme iletişim kutusunda Kaydet düğmesini seçin.

## <a name="import-the-wsp-file-into-visual-studio"></a>.wsp dosyasını Visual Studio
 Yeniden Kullanılabilir İş Akışını İçeri Aktar projesini kullanarak *.wsp* [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dosyasını içine aktarın. Bu proje, iş akışını yeniden kullanılabilir, bildirimli bir iş akışından kod iş akışına dönüştürür. İş akışı dönüştürüldikten sonra davranışını değiştirmek için kodu kullanabilirsiniz.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Bir iş akışını .wsp dosyasından içeri aktarmak ve değiştirmek için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]'de, menü çubuğunda Dosya Yeni **Dosya'Project.**  >    >  

2. Yeni **Project** iletişim **kutusunda, Visual C#** **SharePoint** veya Visual Basic altındaki Visual Basic düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

3. Şablonlar **bölmesinde** Yeniden Kullanılabilir İş Akışı İçeri Aktar **SharePoint 2010** İş Akışı şablonunu seçin, projenin adını **WorkflowImportProject1** olarak bırakın ve ardından **Tamam düğmesini** seçin.

    SharePoint Özelleştirme Sihirbazı görüntülenir.

4. Hata **ayıklama için siteyi** ve güvenlik düzeyini belirtin sayfasında, daha önce oluşturduğunuz ikinci SharePoint site için girin: http:// sistem adı [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] <em></em>/SPD2.

5. Bu **grup çözümü için SharePoint** düzeyi nedir? bölümünde Grup  çözümü olarak dağıt seçeneğini belirleyin ve ardından Sonraki **düğmesini** seçin.

    Korumalı alan veya grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

6. Yeni **proje kaynağını belirtin** sayfasında, sistemde daha önce *.wsp* dosyasını kaydedip dosyayı belirttiğiniz konuma göz atın, dosyayı açın ve ardından Sonraki **düğmesini** seçin.

   > [!NOTE]
   > *.wsp* **dosyasındaki** tüm kullanılabilir öğeleri içeri aktarın.

    Bu, içeri aktarılabilir yeniden kullanılabilir iş akışlarının listesini görüntüler.

7. İçeri **aktarıla öğeleri seçin** kutusunda **SPD** Görev İş Akışı iş akışını ve ardından Son **düğmesini** seçin.

    İçeri aktarma işlemi tamam olduktan sonra, SPD_Workflow_TestFT adlı bir iş akışı içeren **WorkflowImportProject1** **adlı bir proje oluşturulur.** Bu klasörde iş akışının tanım dosyası ve *Elements.xml* tasarımcısı dosyası (*.xoml*). Tasarımcı iki dosya içerir: projenizin programlama diline bağlı olarak kurallar dosyası (.rules) ve arka arkasındaki kod dosyası *(.cs* veya *.vb).*

8. Bu **Çözüm Gezgini,** Diğer **İçe Aktarılan Dosyalar klasörünü** silin.

9. Dosyanın *Elements.xml* `InstantiationURL="_layouts/IniErkflIP.sspx"` silin.

10. Bu **Çözüm Gezgini** **WorkflowImportProject1'i** seçin ve ardından menü çubuğunda Project Başlangıç Öğesi olarak ayarla'Project  >   **WorkflowImportProject1'i** Başlangıç Öğesi olarak ayarlayın.

     Bu, projede hata ayıklana listeyi hemen görüntüler.

11. Yeniden **Kullanılabilir İçeri Aktar SharePoint 2010** İş Akışı şablonu içeri aktarılan iş akışının ilişkilendirme özelliği değerlerini içeri aktarmaz, bunları girmeniz gerekir. Bunu yapmak için:

    1. Bu **Çözüm Gezgini**, **düğümünü SPD_Workflow_TestFT** seçin.

    2. Hedef Liste özelliği gibi ![liste ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")yanındaki üç nokta ( Mobil Tasarımcı üç nokta ) **düğmesini** seçin.

    3. Özelleştirme Sihirbazı'nda eksik SharePoint doldurun ve ardından Son **düğmesini** seçin.

12. .xoml dosyasını seçin ve ardından, iş akışı tasarımcısında içe aktarılan iş akışını görüntülemek için menü çubuğunda  >   Tasarımcıyı Görüntüle'yi seçin.

13. Araç **Windows İş Akışı v3.0** düğümünde, aşağıdaki adımlardan birini gerçekleştirin:

    - **Kod** etkinliğinin kısayol menüsünü açın ve **Kopyala**' yı seçin. İş akışı tasarımcısında, **SequenceActivity1** etkinliğinin altındaki satır için kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    - **Kod** etkinliğini **araç kutusu** ' ndan iş akışı tasarımcısına sürükleyin ve **SequenceActivity1** etkinliğinin altındaki satıra bağlayın.

      Bu, **CodeActivity1** adlı iş akışı tasarımcısına bir etkinlik ekler. Bu etkinlikte Kullanıcı iş akışını başlattığında Duyurular listesinde duyuru oluşturan bir kod eylemi ekleyeceksiniz.

14. Aşağıdaki adım kümelerinden birini uygulayın:

    - Bir olay işleyicisi oluşturmak ve kodu görüntülemek için **CodeActivity1** öğesine çift tıklayın.

    - **CodeActivity1** için **Özellikler** penceresinde, **ExecuteCode** özelliğinin değerini **codeActivity_ExecuteCode** olarak ayarlayın.

15. Var olan **using** veya **Imports** yönergelerinin altına şunu ekleyin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb" id="Snippet1":::

16. `codeActivity1_ExecuteCode`Şu kodla değiştirin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb" id="Snippet2":::

## <a name="deploy-the-project-and-associate-the-workflow"></a>Projeyi dağıtın ve iş akışını ilişkilendirin
 sonra, bir SharePoint sitesine dağıtmak için WorkflowImportProject1 çalıştırın ve ardından değiştirilen, dönüştürülmüş iş akışını görüntülemek ve test etmek için iş akışını görevler listesiyle ilişkilendirirsiniz.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Projeyi dağıtmak ve iş akışını ilişkilendirmek için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dönüştürülen iş akışı projesini çalıştırmak ve dağıtmak Için **F5** tuşunu seçin.

2. Hızlı Başlat çubuğunda görevler listesini göstermek için **Görevler** bağlantısını seçin.

3. **Liste araçları** sekmesinde, **öğeler** düğmesini seçin ve sonra **Yeni öğe** düğmesini seçin.

     **Görevler-yeni öğe** iletişim kutusu açılır.

4. **Başlık** kutusuna **Yeni görev** girin ve **Kaydet** düğmesini seçin.

5. **liste araçları** sekmesinde **liste** düğmesini seçin ve ardından **liste Ayarlar** düğmesini seçin.

     **liste Ayarlar** sayfası görüntülenir.

6. **izinler ve yönetim** bölümünde, **iş akışı Ayarlar** bağlantısını seçin.

     **iş akışı Ayarlar** sayfası görüntülenir.

7. **Iş akışı Ekle** bağlantısını seçin.

8. **Iş akışı** listesinde **WorkflowImportProject1-SPD iş akışı sınaması**' nı seçin.

9. **Ad** kutusunda, **SPD iş akışı testi** girin ve **Tamam** düğmesini seçin.

10. Hızlı Başlat çubuğunda **Görevler** listesini seçin.

11. **Yeni görev**' in yanındaki oku seçin ve ardından listede **iş akışları**' nı seçin.

12. **Yeni bir Iş akışı Başlat** bölümünde, **SPD iş akışı testinin** bağlantısını seçin ve ardından Iş akışını başlatmak için **Başlat** düğmesini seçin.

    > [!NOTE]
    > Alternatif olarak, iş akışı ayarları Sihirbazı 'nı çalıştırarak ve iş akışını otomatik ilişkilendirmek üzere ayarlayarak bir iş akışını bir listeyle otomatik olarak ilişkilendirebilirsiniz.

     İş akışı tarafından iki eylem gerçekleştirildiğine dikkat edin: adınızın görevin **atanan** sütununda göründüğünü ve **Duyurular** listesinde bir duyuru göründüğünü unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [mevcut bir SharePoint sitesinden öğeleri içeri aktar](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
