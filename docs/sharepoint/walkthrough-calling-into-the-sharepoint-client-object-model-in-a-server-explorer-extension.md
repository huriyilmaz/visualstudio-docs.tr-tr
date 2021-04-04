---
title: 'Sunucu Gezgini: SharePoint bağlantıları düğümünü genişletme'
titleSuffix: ''
description: Bu kılavuzda, Sunucu Gezgini SharePoint bağlantıları düğümü için bir uzantıdan SharePoint istemci nesne modelini çağırma konusuna bakın.
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
ms.workload:
- office
ms.openlocfilehash: dee53642e042c8d4db88bdba7c093f327527798d
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217027"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>İzlenecek yol: Sunucu Gezgini uzantısında SharePoint istemci nesne modelini çağırma
  Bu izlenecek yolda, SharePoint istemci nesne modelinin **Sunucu Gezgini** **SharePoint bağlantıları** düğümü uzantısından nasıl çağrılacağını gösterir. SharePoint istemci nesne modelini kullanma hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aşağıdaki yollarla **Sunucu Gezgini** **SharePoint bağlantıları** düğümünü genişleten bir uzantı oluşturma:

  - Uzantı, **Sunucu Gezgini** Içindeki her SharePoint site düğümünün altına bir **Web Bölümü Galerisi** düğümü ekler. Bu yeni düğüm, sitede Web Bölümü galerisinde her bir Web bölümünü temsil eden alt düğümleri içerir.

  - Uzantı, bir Web bölümü örneğini temsil eden yeni bir düğüm türü tanımlar. Bu yeni düğüm türü, yeni **Web Bölümü Galerisi** düğümü altındaki alt düğümlerin temelini oluşturur. Yeni Web Bölümü düğüm türü, düğümün temsil ettiği Web bölümüyle ilgili **Özellikler** penceresinde bilgileri görüntüler.

- Uzantıyı dağıtmak için bir Visual Studio uzantısı (VSıX) paketi oluşturma.

- Uzantı hatalarını ayıklama ve test etme.

> [!NOTE]
> Bu kılavuzda oluşturduğunuz uzantı, [Izlenecek yol: Sunucu Gezgini Web bölümlerini göstermek Için genişletin](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Bu izlenecek yol SharePoint Server nesne modelini kullanır, ancak bu izlenecek yol, istemci nesne modelini kullanarak aynı görevleri gerçekleştirir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- Windows, SharePoint ve Visual Studio 'nun desteklenen sürümleri.

- Visual Studio SDK 'Sı. Bu izlenecek yol, uzantıyı dağıtmak üzere bir VSıX paketi oluşturmak için SDK 'daki **VSIX proje** şablonunu kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- SharePoint istemci nesne modelini kullanma. Daha fazla bilgi için bkz. [yönetilen Istemci nesne modeli](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).

- SharePoint 'teki Web bölümleri. Daha fazla bilgi için bkz. [Web bölümleri genel bakış](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için iki proje oluşturmanız gerekir:

- **Sunucu Gezgini** uzantısını DAĞıTMAK için VSIX paketi oluşturmak üzere bir VSIX projesi.

- **Sunucu Gezgini** uzantısını uygulayan bir sınıf kitaplığı projesi.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

3. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik**' i seçin.

    > [!NOTE]
    > **Genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'sını yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

     SharePoint Araç Uzantıları .NET Framework bu sürümünde özellikleri gerektirir.

5. **VSIX proje** şablonunu seçin.

6. **Ad** kutusuna **WebPartNode** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNode** projesini **Çözüm Gezgini** ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **Windows**' u seçin.

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

4. Proje şablonları listesinde **sınıf kitaplığı**' nı seçin.

5. **Ad** kutusuna **WebPartNodeExtension** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüme bir **WebPartNodeExtension** projesi ekler ve varsayılan Class1 kod dosyasını açar.

6. Class1 kod dosyasını projeden silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Uzantıyı oluşturmak için kod yazmadan önce projenize kod dosyaları ve derleme başvuruları eklemeniz ve varsayılan ad alanını güncelleştirmeniz gerekir.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. **WebPartNodeExtension** projesinde, SiteNodeExtension ve WebPartNodeTypeProvider adlı iki kod dosyası ekleyin.

2. WebPartNodeExtension projesi için kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

3. **Başvuru Yöneticisi-WebPartNodeExtension** Iletişim kutusunda **Framework** düğümünü seçin ve ardından System. ComponentModel. Composition ve System. Windows. Forms derlemelerinin onay kutularını seçin.

4. **Uzantılar** düğümünü seçin, aşağıdaki derlemelerin her biri için onay kutusunu seçin ve ardından **Tamam** düğmesini seçin:

    - Microsoft. SharePoint. Client

    - Microsoft. SharePoint. Client. Runtime

    - Microsoft. VisualStudio. SharePoint

5. **WebPartNodeExtension** projesi için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

     **Proje Tasarımcısı** açılır.

6. **Uygulama** sekmesini seçin.

7. **Varsayılan ad alanı** kutusuna (C#) veya **kök ad alanı** kutusuna (Visual Basic) **ServerExplorer. SharePointConnections. WebPartNode** yazın.

## <a name="create-icons-for-the-new-nodes"></a>Yeni düğümler için simgeler oluşturma
 **Sunucu Gezgini** uzantısı için iki simge oluşturun: yeni **Web Bölümü Galerisi** düğümü Için bir simge ve **Web Bölümü Galerisi** düğümünün altındaki her bir alt Web bölümü düğümü için bir simge. Bu izlenecek yolda daha sonra bu simgeleri düğümlerle ilişkilendiren bir kod yazacaksınız.

#### <a name="to-create-icons-for-the-nodes"></a>Düğümler için simgeler oluşturmak için

1. WebPartNodeExtension projesi **Proje tasarımcısında** **kaynaklar** sekmesini seçin.

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
 Yeni **Web Bölümü Galerisi** düğümünü her bir SharePoint site düğümüne ekleyen bir sınıf oluşturun. Yeni düğümü eklemek için sınıfı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> arabirimini uygular. Bu arabirimi, bir düğüme yeni bir alt düğüm ekleme gibi **Sunucu Gezgini** var olan bir düğümün davranışını her uzatmak istediğinizde uygulayın.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini eklemek için

1. Aşağıdaki kodu, **WebPartNodeExtension** projesi için **SiteNodeExtension** kod dosyasına yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra, projede bazı derleme hataları olur. Sonraki adımlarda kod eklediğinizde bu hatalar kaybolur.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>Bir Web bölümünü temsil eden bir düğüm türü tanımlama
 Bir Web bölümünü temsil eden yeni bir düğüm türünü tanımlayan bir sınıf oluşturun. Visual Studio, **Web Bölümü Galerisi** düğümünün altında alt düğümleri göstermek için bu yeni düğüm türünü kullanır. Bu alt düğümlerin her biri, SharePoint sitesindeki tek bir Web bölümünü temsil eder.

 Yeni düğüm türünü tanımlamak için sınıfı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> arabirimini uygular. **Sunucu Gezgini** yeni bir düğüm türü tanımlamak istediğinizde bu arabirimi uygulayın.

#### <a name="to-define-the-web-part-node-type"></a>Web Bölümü düğüm türünü tanımlamak için

1. Aşağıdaki kodu **WebPartNodeExtension** projesi Için **WebPartNodeTypeProvider** kod dosyasına yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::

## <a name="checkpoint"></a>Checkpoint
 Bu noktada, **Web Bölümü Galerisi** düğümü için tüm kod artık projede bulunur. Hata olmadan derlendiğinden emin olmak için **WebPartNodeExtension** projesi oluşturun.

#### <a name="to-build-the-project"></a>Projeyi derlemek için

1. **Çözüm Gezgini**, **WebPartNodeExtension** projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, projeye dahil olan source. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-the-vsix-package"></a>VSıX paketini yapılandırmak için

1. **Çözüm Gezgini**, **WebPartNode** projesinde, bildirim düzenleyicisinde **Source. Extension. valtmanifest** dosyasını açın.

     Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)).

2. **Ürün adı** kutusuna **Sunucu Gezgini Için Web Bölümü Galerisi düğümünü** girin.

3. **Yazar** kutusuna **contoso** girin.

4. **Açıklama** kutusuna, **Sunucu Gezgini SharePoint bağlantıları düğümüne özel bir Web Bölümü Galerisi düğümü ekler** yazın.

5. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmesini seçin.

6. **Yeni varlık Ekle** Iletişim kutusundaki **tür** listesinde **Microsoft. VisualStudio. MefComponent** öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

8. **Proje** listesinde, **WebPartNodeExtension**' ı seçin ve ardından **Tamam** düğmesini seçin.

9. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından çözümün hatasız derlendiğinden emin olun.

10. WebPartNode projesi için derleme çıkış klasörünün şimdi WebPartNode. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... proje dosyanızı içeren klasörün altındaki \bin\Debug klasörü.

## <a name="test-the-extension"></a>Uzantıyı test etme
 Artık **Sunucu Gezgini** yeni **Web Bölümü Galerisi** düğümünü test etmeye hazırsınız. İlk olarak, Visual Studio 'nun Deneysel örneğindeki uzantı projesinde hata ayıklamaya başlayın. Ardından, Visual Studio 'nun Deneysel örneğindeki yeni **Web bölümleri** düğümünü kullanın.

#### <a name="to-start-debugging-the-extension"></a>Uzantının hatalarını ayıklamaya başlamak için

1. Visual Studio 'Yu yönetici kimlik bilgileriyle yeniden başlatın ve ardından **WebPartNode** çözümünü açın.

2. WebPartNodeExtension projesinde, **SiteNodeExtension** kod dosyasını açın ve ardından ve yöntemlerinde ilk kod satırlarına bir kesme noktası ekleyin `NodeChildrenRequested` `CreateWebPartNodes` .

3. Hata ayıklamayı başlatmak için **F5** tuşunu seçin.

     Visual Studio, uzantısı, Server Explorer\1.0 için%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Bölümü Galerisi düğüm uzantısına ve Visual Studio 'nun deneysel bir örneğini başlatır. Bu Visual Studio örneğinde Proje öğesini test edeceksiniz.

#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda Sunucu Gezgini **görüntüle**' yi seçin  >  .

2. Test için kullanmak istediğiniz SharePoint sitesinin **Sunucu Gezgini** Içindeki **SharePoint bağlantıları** düğümü altında göründüğünü doğrulayın. Listede yoksa, aşağıdaki adımları izleyin:

    1. **SharePoint bağlantıları** için kısayol menüsünü açın ve sonra **bağlantı ekle**' yi seçin.

    2. **SharePoint bağlantısı ekle** iletişim kutusunda, bağlanmak istediğiniz SharePoint sitesinin URL 'sini girin ve **Tamam** düğmesini seçin.

         Geliştirme bilgisayarınızda SharePoint sitesini belirtmek için, yazın **http://localhost** .

3. Site bağlantısı düğümünü (sitenizin URL 'sini gösterir) genişletin ve sonra bir alt site düğümünü (örneğin, **ekip sitesi**) genişletin.

4. Visual Studio 'nun diğer örneğindeki kodun, yönteminde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `NodeChildrenRequested` ve sonra projede hata ayıklamaya devam etmek Için **F5** tuşunu seçin.

5. Visual Studio 'nun deneysel örneğinde, üst düzey site düğümü altında görünen **Web Bölümü Galerisi** düğümünü genişletin.

6. Visual Studio 'nun diğer örneğindeki kodun, yönteminde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `CreateWebPartNodes` ve sonra projede hata ayıklamaya devam etmek Için **F5** tuşunu seçin.

7. Visual Studio 'nun deneysel örneğinde, bağlantılı sitedeki tüm Web Bölümleri **Sunucu Gezgini** **Web Bölümü Galerisi** düğümünün altında göründüğünü doğrulayın.

8. Bir Web bölümü için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

9. **Özellikler** penceresinde web bölümüyle ilgili ayrıntıların göründüğünü doğrulayın.

10. **Sunucu Gezgini**' de, aynı Web bölümü için kısayol menüsünü açın ve ardından **ileti görüntüle**' yi seçin.

     Görüntülenen ileti kutusunda **Tamam** düğmesini seçin.

## <a name="uninstall-the-extension-from-visual-studio"></a>Uzantıyı Visual Studio 'dan kaldırma
 Uzantıyı test etmeyi bitirdikten sonra Visual Studio 'dan kaldırın.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde, **Sunucu Gezgini Için Web Bölümü Galerisi düğümünü** seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda **Evet** düğmesini seçin.

4. Kaldırma işlemini gerçekleştirmek için **Şimdi yeniden Başlat** düğmesini seçin.

     Proje öğesi de kaldırılır.

5. Her iki Visual Studio örneğini kapatın (WebPartNode çözümünün açık olduğu deneysel örnek ve Visual Studio örneği).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için bir simge veya diğer görüntü &#40;görüntü Düzenleyicisi oluşturma&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)