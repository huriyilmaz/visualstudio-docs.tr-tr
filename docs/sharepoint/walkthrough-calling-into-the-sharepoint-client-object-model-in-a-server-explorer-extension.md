---
title: 'Sunucu Gezgini: SharePoint Connections düğümünü genişletme'
titleSuffix: ''
description: bu kılavuzda, Sunucu Gezgini SharePoint bağlantıları düğümü için bir uzantıdan SharePoint istemci nesne modelini çağırma konusuna bakın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: cf618a3fa237035ead1540a64bc772d325954ff4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156116"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>izlenecek yol: Sunucu Gezgini uzantısında SharePoint istemci nesne modeline çağırma
  bu izlenecek yol, **Sunucu Gezgini** **SharePoint bağlantıları** düğümü için bir uzantıdan SharePoint istemci nesne modelinin nasıl çağrılacağını gösterir. SharePoint istemci nesne modelini kullanma hakkında daha fazla bilgi için, bkz. [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aşağıdaki yollarla **Sunucu Gezgini** **SharePoint bağlantıları** düğümünü genişleten bir uzantı oluşturma:

  - uzantı, **Sunucu Gezgini** her bir SharePoint site düğümünün altına bir **Web bölümü galerisi** düğümü ekler. Bu yeni düğüm, sitede Web Bölümü galerisinde her bir Web bölümünü temsil eden alt düğümleri içerir.

  - Uzantı, bir Web bölümü örneğini temsil eden yeni bir düğüm türü tanımlar. Bu yeni düğüm türü, yeni **Web Bölümü Galerisi** düğümü altındaki alt düğümlerin temelini oluşturur. Yeni Web Bölümü düğüm türü, düğümün temsil ettiği Web bölümüyle ilgili **Özellikler** penceresinde bilgileri görüntüler.

- uzantıyı dağıtmak için bir Visual Studio uzantısı (vsıx) paketi oluşturma.

- Uzantı hatalarını ayıklama ve test etme.

> [!NOTE]
> Bu kılavuzda oluşturduğunuz uzantı, [Izlenecek yol: Sunucu Gezgini Web bölümlerini göstermek Için genişletin](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). bu izlenecek yol SharePoint server nesne modelini kullanır, ancak bu izlenecek yol, istemci nesne modelini kullanarak aynı görevleri gerçekleştirir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- Windows, SharePoint ve Visual Studio desteklenen sürümleri.

- Visual Studio SDK. bu izlenecek yol, uzantıyı dağıtmak üzere bir vsıx paketi oluşturmak için SDK 'daki **vsıx Project** şablonunu kullanır. daha fazla bilgi için bkz. [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- SharePoint istemci nesne modelini kullanma. Daha fazla bilgi için bkz. [yönetilen Istemci nesne modeli](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).

- SharePoint Web bölümleri. daha fazla bilgi için bkz. [Web Bölümleri genel bakış](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için iki proje oluşturmanız gerekir:

- **Sunucu Gezgini** uzantısını DAĞıTMAK için VSIX paketi oluşturmak üzere bir VSIX projesi.

- **Sunucu Gezgini** uzantısını uygulayan bir sınıf kitaplığı projesi.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

3. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik**' i seçin.

    > [!NOTE]
    > **genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'yı yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

4. iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

     SharePoint araç uzantıları, .NET Framework bu sürümünde özellikler gerektirir.

5. **vsıx Project** şablonunu seçin.

6. **Ad** kutusuna **WebPartNode** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNode** projesini **Çözüm Gezgini** ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

2. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **Windows**' yı seçin.

3. iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

4. Proje şablonları listesinde **sınıf kitaplığı**' nı seçin.

5. **Ad** kutusuna **WebPartNodeExtension** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüme bir **WebPartNodeExtension** projesi ekler ve varsayılan Class1 kod dosyasını açar.

6. Class1 kod dosyasını projeden silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Uzantıyı oluşturmak için kod yazmadan önce projenize kod dosyaları ve derleme başvuruları eklemeniz ve varsayılan ad alanını güncelleştirmeniz gerekir.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. **WebPartNodeExtension** projesinde, SiteNodeExtension ve WebPartNodeTypeProvider adlı iki kod dosyası ekleyin.

2. WebPartNodeExtension projesi için kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

3. **Başvuru Yöneticisi-WebPartNodeExtension** Iletişim kutusunda **Framework** düğümünü seçin ve ardından System. ComponentModel. Composition ve sistem onay kutularını seçin. Windows. Forms derlemeleri.

4. **Uzantılar** düğümünü seçin, aşağıdaki derlemelerin her biri için onay kutusunu seçin ve ardından **Tamam** düğmesini seçin:

    - MICROSOFT. SharePoint. İstemcilerinin

    - MICROSOFT. SharePoint. Client. Runtime

    - Microsoft. VisualStudio. SharePoint

5. **WebPartNodeExtension** projesi için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

     **Project tasarımcısı** açılır.

6. **Uygulama** sekmesini seçin.

7. **varsayılan ad alanı** kutusuna (C#) veya **kök ad alanı** kutusuna (Visual Basic) **serverexplorer. sharepointconnections. webpartnode** yazın.

## <a name="create-icons-for-the-new-nodes"></a>Yeni düğümler için simgeler oluşturma
 **Sunucu Gezgini** uzantısı için iki simge oluşturun: yeni **Web Bölümü Galerisi** düğümü Için bir simge ve **Web Bölümü Galerisi** düğümünün altındaki her bir alt Web bölümü düğümü için bir simge. Bu izlenecek yolda daha sonra bu simgeleri düğümlerle ilişkilendiren bir kod yazacaksınız.

#### <a name="to-create-icons-for-the-nodes"></a>Düğümler için simgeler oluşturmak için

1. webpartnodeextension projesi için **Project tasarımcısında** **kaynaklar** sekmesini seçin.

2. **Bu projenin varsayılan bir kaynak dosyası içermediğini bağlantıyı seçin. Bir tane oluşturmak için buraya tıklayın.**

     Visual Studio bir kaynak dosyası oluşturur ve tasarımcıda açar.

3. Tasarımcının en üstünde, **Kaynak Ekle** menü komutundaki oku seçin ve ardından **Yeni simge Ekle**' yi seçin.

4. Yeni simge adı için **WebPartsNode** girin ve sonra **Ekle** düğmesini seçin.

     Yeni simge **görüntü düzenleyicisinde** açılır.

5. Simgenin 16x16 sürümünü, kolayca tanıyabileceğiniz bir tasarıma sahip olacak şekilde düzenleyin.

6. Simgenin 32x32 sürümüne ait kısayol menüsünü açın ve ardından **görüntü türünü sil**' i seçin.

7. Proje kaynaklarına ikinci bir simge eklemek ve bu simge **Web bölümünü** adlandırmak için 3 ile 7 arasındaki adımları yineleyin.

8. **Çözüm Gezgini**, **WebPartNodeExtension** projesi Için **kaynaklar** klasöründe, *WebPartsNode. ico*' ı seçin.

9. **Özellikler** penceresinde, **derleme eylemi** listesini açın ve ardından **gömülü kaynak**' ı seçin.

10. *WebPart. ico* için son iki adımı tekrarlayın.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini ekleyin
 her bir SharePoint site düğümüne yeni **Web bölümü galerisi** düğümünü ekleyen bir sınıf oluşturun. Yeni düğümü eklemek için sınıfı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> arabirimini uygular. Bu arabirimi, bir düğüme yeni bir alt düğüm ekleme gibi **Sunucu Gezgini** var olan bir düğümün davranışını her uzatmak istediğinizde uygulayın.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini eklemek için

1. Aşağıdaki kodu, **WebPartNodeExtension** projesi için **SiteNodeExtension** kod dosyasına yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra, projede bazı derleme hataları olur. Sonraki adımlarda kod eklediğinizde bu hatalar kaybolur.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>Bir Web bölümünü temsil eden bir düğüm türü tanımlama
 Bir Web bölümünü temsil eden yeni bir düğüm türünü tanımlayan bir sınıf oluşturun. Visual Studio, **Web bölümü galerisi** düğümünün altında alt düğümleri göstermek için bu yeni düğüm türünü kullanır. bu alt düğümlerin her biri, SharePoint sitesindeki tek bir Web bölümünü temsil eder.

 Yeni düğüm türünü tanımlamak için sınıfı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> arabirimini uygular. **Sunucu Gezgini** yeni bir düğüm türü tanımlamak istediğinizde bu arabirimi uygulayın.

#### <a name="to-define-the-web-part-node-type"></a>Web Bölümü düğüm türünü tanımlamak için

1. Aşağıdaki kodu **WebPartNodeExtension** projesi Için **WebPartNodeTypeProvider** kod dosyasına yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::

## <a name="checkpoint"></a>Checkpoint
 Bu noktada, **Web Bölümü Galerisi** düğümü için tüm kod artık projede bulunur. Hata olmadan derlendiğinden emin olmak için **WebPartNodeExtension** projesi oluşturun.

#### <a name="to-build-the-project"></a>Projeyi derlemek için

1. Bu **Çözüm Gezgini** **WebPartNodeExtension** projesinin kısayol menüsünü açın ve Ardından Oluştur'a **tıklayın.**

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için çözümünüzde VSIX projesini kullanarak bir VSIX paketi oluşturun. İlk olarak, projeye dahil edilen source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırabilirsiniz. Ardından çözümü oluşturarak VSIX paketini oluşturun.

#### <a name="to-configure-the-vsix-package"></a>VSIX paketini yapılandırmak için

1. Bu **Çözüm Gezgini** **WebPartNode** projesinde, bildirim düzenleyicisinde **source.extension.vsixmanifest** dosyasını açın.

     source.extension.vsixmanifest dosyası, tüm VSIX paketlerinin gerekli olduğu extension.vsixmanifest dosyasının temelini alır. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 Başvurusu.](/previous-versions/dd393700(v=vs.110))

2. Ürün Adı **kutusuna,** ürün için **Web Bölümü Galeri Düğümü Sunucu Gezgini.**

3. Yazar **kutusuna** Contoso **yazın.**

4. Açıklama **kutusuna,** Sunucu Gezgini'daki SharePoint Connections düğümüne özel bir Web Bölümü **Galerisi düğümü Sunucu Gezgini.**

5. Düzenleyicinin  Varlıklar sekmesinde Yeni **düğmesini** seçin.

6. Yeni Varlık **Ekle iletişim** kutusundaki  Tür listesinde **Microsoft.VisualStudio.MefComponent öğesini seçin.**

    > [!NOTE]
    > Bu değer `MefComponent` extension.vsixmanifest dosyasındaki öğesine karşılık gelen bir değerdir. Bu öğe VSIX paketinde bir uzantı derlemenin adını belirtir. Daha fazla bilgi için bkz. [MEFComponent Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

8. Uygulama **Project** **WebPartNodeExtension'ı ve** ardından Tamam **düğmesini** seçin.

9. Menü çubuğunda Derleme   >  **Çözümü'yü seçin** ve çözümün hatasız derlenmiş olduğundan emin olun.

10. WebPartNode projesinin derleme çıkış klasörünün artık WebPartNode.vsix dosyasını içerdiğini emin olun.

     Varsayılan olarak, derleme çıkış klasörü .'dür. Proje dosyanızı içeren klasörün altında \bin\Debug klasörü.

## <a name="test-the-extension"></a>Uzantıyı test etmek
 Artık yeni Web Bölümü Galerisi düğümünü **'de test** etmeye **Sunucu Gezgini.** İlk olarak, uzantı projesinin deneysel bir örneğinde hata ayıklamaya Visual Studio. Ardından deneysel **Web Bölümleri** yeni düğüm düğümünü Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Uzantıda hata ayıklamaya başlamak için

1. Yönetici Visual Studio ile yeniden başlatın ve ardından **WebPartNode çözümünü** açın.

2. WebPartNodeExtension projesinde **SiteNodeExtension** kod dosyasını açın ve ardından ve yöntemlerinde ilk kod satırlarına bir kesme `NodeChildrenRequested` `CreateWebPartNodes` noktası ekleyin.

3. Hata **ayıklamayı başlatmak** için F5 tuşuna basın.

     Visual Studio%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Bölümü Galeri Düğümü Uzantısı uzantısını Sunucu Gezgini\1.0 için yüker ve deneysel bir Visual Studio. Proje öğesini bu örnek içinde test Visual Studio.

#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için

1. Deneysel örnek Visual Studio menü çubuğunda Görünüm'Sunucu Gezgini.   >  

2. Test için SharePoint istediğiniz sitenin, **SharePoint'daki Bağlantılar** düğümü altında **Sunucu Gezgini.** Listelenmiyorsa şu adımları izleyin:

    1. Bağlantılar'ın kısayol **SharePoint açın ve** Ardından Bağlantı **Ekle'yi seçin.**

    2. Bağlantı **Ekle SharePoint iletişim** kutusunda, bağlanmak istediğiniz SharePoint sitenin URL'sini girin ve ardından Tamam **düğmesini** seçin.

         Geliştirme bilgisayarınızda SharePoint siteyi belirtmek için **http://localhost** yazın.

3. Site bağlantı düğümünü genişletin (bu, sitenizin URL'sini görüntüler) ve ardından bir alt site düğümünü (örneğin, **Takım Sitesi) genişletin.**

4. Visual Studio'nin diğer örneğinde yer alan kodun yönteminde daha önce ayar seçtiğiniz kesme noktası üzerinde durarak projesinde hata ayıklamaya devam etmek için `NodeChildrenRequested` **F5** tuşuna basın.

5. Visual Studio'nin deneysel örneğinde, üst düzey site düğümü altında görünen **Web** Bölümü Galerisi düğümünü genişletin.

6. Visual Studio'nin diğer örneğinde yer alan kodun yönteminde daha önce ayar seçtiğiniz kesme noktası üzerinde durarak projesinde hata ayıklamaya devam etmek için `CreateWebPartNodes` **F5** tuşuna basın.

7. deneysel Visual Studio örneğinde, bağlı sitedeki tüm Web Bölümleri'nin Sunucu Gezgini'daki **Web** Bölümü Galerisi düğümü **altında görüntü Sunucu Gezgini.**

8. Bir Web Bölümü için kısayol menüsünü açın ve Özellikler'i **seçin.**

9. Özellikler **penceresinde** Web Bölümü ile ilgili ayrıntıların görüntü olduğunu doğrulayın.

10. Bu **Sunucu Gezgini,** aynı Web Bölümü için kısayol menüsünü açın ve ardından İleti **görüntüle'yi seçin.**

     Görüntülenen ileti kutusunda Tamam **düğmesini** seçin.

## <a name="uninstall-the-extension-from-visual-studio"></a>Uzantıyı dosyadan Visual Studio
 Uzantıyı test etme işlemi tamamdikten sonra uzantıyı Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Deneysel Visual Studio menü çubuğunda Araçlar Uzantıları ve   >  **Güncelleştirmeler'i seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinde, uzantılar için **Web Bölümü Galeri Düğümü'Sunucu Gezgini** ve ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda Evet **düğmesini** seçin.

4. Kaldırma işlemini **tamamlamak için** Şimdi Yeniden Başlat düğmesini seçin.

     Proje öğesi de kaldırılır.

5. Her iki Visual Studio (deneysel örnek ve WebPartNode çözümünün Visual Studio örnek) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nesne modellerini SharePoint çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Kümedeki SharePoint düğümünü Sunucu Gezgini](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Adım adım kılavuz: Sunucu Gezgini bölümlerini görüntülemek için uygulamanın süresini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Simgeler için Görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için Görüntü Düzenleyicisi'nde &#40;Veya Başka Bir Görüntü&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)