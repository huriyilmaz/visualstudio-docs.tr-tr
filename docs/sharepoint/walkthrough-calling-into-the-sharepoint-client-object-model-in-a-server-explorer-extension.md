---
title: 'Sunucu Gezgini: SharePoint Bağlantılar düğümünü genişletme'
titleSuffix: ''
description: Bu kılavuzda, SharePoint'deki SharePoint düğümü için bir uzantıdan Sunucu Gezgini.
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
ms.openlocfilehash: 1062d98eb88d028480fa74f4733f6896c9c812ae97abac1d8ab18f4c9e373d0a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409338"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Adım adım kılavuz: SharePoint uzantısında istemci nesne modeline Sunucu Gezgini çağırma
  Bu kılavuzda, SharePoint'deki SharePoint Bağlantıları düğümü için bir uzantıdan **Sunucu Gezgini.**  İstemci nesnesi modelini kullanma hakkında daha fazla SharePoint için [bkz. SharePoint nesne modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

 Bu kılavuz aşağıdaki görevleri gösterir:

- SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Bağlantı düğümünü genişleten** **bir Sunucu Gezgini** oluşturma:

  - Uzantı, **'deki her bir** site düğümüne SharePoint Web Bölümü **Galerisi** Sunucu Gezgini. Bu yeni düğüm, sitedeki Web Bölümü galerisinde her Bir Web Bölümünü temsil eden alt düğümler içerir.

  - Uzantı, Web Bölümü örneğini temsil eden yeni bir düğüm türünü tanımlar. Bu yeni düğüm türü, yeni Web Bölümü Galerisi düğümü altındaki alt **düğümlerin temelini** sağlar. Yeni Web Bölümü düğüm türü, Özellikler penceresinde **düğümün** temsil ettiği Web Bölümü ile ilgili bilgileri görüntüler.

- Uzantıyı Visual Studio bir Uzantı (VSIX) paketi oluşturma.

- Uzantıda hata ayıklama ve test etme.

> [!NOTE]
> Bu kılavuzda oluştursanız uzantı, Adım adım: Web bölümlerini görüntülemek için uzantıyı Sunucu Gezgini adım adım [kılavuzda oluşturanın uzantısına benzer.](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md) Bu izlenecek yol SharePoint sunucusu nesne modelini kullanır, ancak bu izlenecek yol, istemci nesne modelini kullanarak aynı görevleri tamamlar.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows, SharePoint ve Visual Studio.

- Visual Studio SDK'sı. Bu kılavuzda, **uzantıyı dağıtmak Project** BIR VSIX paketi oluşturmak için SDK'daki VSIX Project şablonu lanmıştır. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- İstemci nesne SharePoint kullanarak. Daha fazla bilgi için [bkz. Yönetilen İstemci Nesne Modeli.](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14))

- Web bölümleri SharePoint. Daha fazla bilgi için [bkz. Web Bölümleri Genel Bakış.](/previous-versions/office/ms432401(v=office.14))

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için iki proje oluşturmanız gerekir:

- Uygulama uzantısını dağıtmak için VSIX paketini oluşturmak için bir **VSIX Sunucu Gezgini.**

- Uygulama uzantısını uygulayan bir **sınıf Sunucu Gezgini** projesi.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-vsix-project"></a>VSIX projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Menü çubuğunda Dosya Yeni **Dosya'Project.**  >    >  

3. Yeni **Project** iletişim kutusunda **Visual C#** veya Visual Basic **düğümlerini** genişletin ve ardından **Genişletilebilirlik'i seçin.**

    > [!NOTE]
    > **Genişletilebilirlik düğümü** yalnızca Visual Studio SDK'sı yüklüyse kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework **sürümleri listesinden 4.5'i** .NET Framework.

     SharePoint uzantısı, uygulamanın bu sürümünde özellikler .NET Framework.

5. **VSIX Project** seçin.

6. Ad **kutusuna** **WebPartNode yazın ve** tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNode projesini** **uygulamasına Çözüm Gezgini.**

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

2. Yeni **Project** iletişim **kutusunda, Visual C#** veya Visual Basic **düğümlerini** genişletin ve sonra **Windows.**

3. İletişim kutusunun üst kısmında, .NET Framework **sürümleri listesinden 4.5'i** .NET Framework.

4. Proje şablonları listesinde Sınıf **Kitaplığı'ı seçin.**

5. Ad **kutusuna** **WebPartNodeExtension yazın** ve tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNodeExtension** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

6. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Uzantıyı oluşturmak için kod yazmadan önce projenize kod dosyaları ve derleme başvuruları eklemeniz ve varsayılan ad alanını güncelleştirmeniz gerekir.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. **WebPartNodeExtension** projesine SiteNodeExtension ve WebPartNodeTypeProvider adlı iki kod dosyası ekleyin.

2. WebPartNodeExtension projesinin kısayol menüsünü açın ve Başvuru **Ekle'yi seçin.**

3. Başvuru Yöneticisi **- WebPartNodeExtension** iletişim kutusunda **Framework** düğümünü seçin ve ardından System.ComponentModel.Composition ve System onay kutularını seçin. Windows. Derlemeleri oluşturur.

4. Uzantılar **düğümünü** seçin, aşağıdaki derlemelerin her biri için onay kutusunu seçin ve ardından Tamam **düğmesini** seçin:

    - Microsoft. SharePoint. Istemci

    - Microsoft. SharePoint. Client.Runtime

    - Microsoft.VisualStudio. SharePoint

5. **WebPartNodeExtension projesinin kısayol menüsünü açın** ve Özellikler'i **seçin.**

     Project **Tasarımcısı** açılır.

6. Uygulama **sekmesini** seçin.

7. Varsayılan ad **alanı** kutusuna (C#) veya **Kök** ad alanı kutusuna (Visual Basic), **ServerExplorer.SharePointConnections.WebPartNode girin.**

## <a name="create-icons-for-the-new-nodes"></a>Yeni düğümler için simgeler oluşturma
 **Sunucu Gezgini** uzantısı için iki simge oluşturun: yeni **Web** Bölümü Galerisi düğümü için bir simge ve **Web Bölümü** Galerisi düğümü altındaki her alt Web Bölümü düğümü için başka bir simge. Bu kılavuzda daha sonra bu simgeleri düğümlerle ilişkilendiren kod yazacağız.

#### <a name="to-create-icons-for-the-nodes"></a>Düğümler için simgeler oluşturmak için

1. WebPartNodeExtension **projesine** Project Tasarımcısı'nda Kaynaklar **sekmesini** seçin.

2. Bu proje **varsayılan kaynaklar dosyasını içermez bağlantısını seçin. Oluşturmak için buraya tıklayın.**

     Visual Studio bir kaynak dosyası oluşturur ve tasarımcıda açar.

3. Tasarımcının üst kısmında Kaynak Ekle menü  komutunda oku ve ardından Yeni Simge **Ekle'yi seçin.**

4. Yeni **simge adı olarak WebPartsNode** girin ve ekle **düğmesini** seçin.

     Yeni simge Görüntü **Düzenleyicisi'nde açılır.**

5. Simgenin 16x16 sürümünü, kolayca tanıyabilirsiniz bir tasarıma sahip olacak şekilde düzenleyin.

6. Simgenin 32x32 sürümü için kısayol menüsünü açın ve Ardından Görüntü Türünü **Sil'i seçin.**

7. Proje kaynaklarına ikinci bir simge eklemek için 3 ile 7 arasında adımları tekrarlayın ve bu simgeye **WebPart adını girin.**

8. Bu **Çözüm Gezgini** **WebPartNodeExtension** projesinin **Kaynaklar** klasöründe *WebPartsNode.ico'yu seçin.*

9. Özellikler penceresinde **Derleme** Eylemi listesini **açın ve** Katıştırılmış Kaynak'ı **seçin.**

10. *WebPart.ico için son iki adımı tekrarlayın.*

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Web bölümü galeri düğümünü Sunucu Gezgini
 Yeni Web Bölümü Galerisi düğümünü her bir **site** düğümüne ekleyen SharePoint oluşturun. Sınıfı, yeni düğümü eklemek için arabirimini <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> uygulamaya almaktadır. Bir düğüme yeni bir alt düğüm ekleme gibi, Sunucu Gezgini mevcut bir düğümün davranışını genişletmek istediğiniz her durumda bu arabirimi gerçekleştirin.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Web bölümü galeri düğümünü Sunucu Gezgini

1. Aşağıdaki kodu **WebPartNodeExtension** projesinin **SiteNodeExtension** kod dosyasına yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra proje bazı derleme hatalarına sahip olur. Sonraki adımlarda kod eklerken bu hatalar gider.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>Web bölümünü temsil eden bir düğüm türü tanımlama
 Web Bölümünü temsil eden yeni bir düğüm türünü tanımlayan bir sınıf oluşturun. Visual Studio Web Bölümü Galerisi düğümü altında alt düğümleri görüntülemek için bu **yeni düğüm türünü** kullanır. Bu alt düğümlerin her biri, SharePoint sitesinde tek bir Web Bölümünü temsil eder.

 Sınıfı, yeni düğüm türünü tanımlamak için arabirimini <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> uygulamaya almaktadır. içinde yeni bir düğüm türü tanımlamak istediğiniz her durumda bu arabirimi **Sunucu Gezgini.**

#### <a name="to-define-the-web-part-node-type"></a>Web bölümü düğüm türünü tanımlamak için

1. Aşağıdaki kodu **WebPartNodeExtension** projesinin **WebPartNodeTypeProvider** kod dosyasına yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::

## <a name="checkpoint"></a>Checkpoint
 Kılavuzda bu noktada, Web Bölümü Galerisi düğümü için **tüm** kod artık projededir. Hatasız derlenmiş olduğundan emin olmak için **WebPartNodeExtension** projesini derle.

#### <a name="to-build-the-project"></a>Projeyi derlemek için

1. **Çözüm Gezgini**, **WebPartNodeExtension** projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, projeye dahil olan source. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-the-vsix-package"></a>VSıX paketini yapılandırmak için

1. **Çözüm Gezgini**, **WebPartNode** projesinde, bildirim düzenleyicisinde **Source. Extension. valtmanifest** dosyasını açın.

     Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)).

2. **Ürün adı** kutusuna **Sunucu Gezgini Için Web Bölümü Galerisi düğümünü** girin.

3. **Yazar** kutusuna **contoso** girin.

4. **açıklama** kutusunda, **Sunucu Gezgini SharePoint bağlantıları düğümüne özel bir Web bölümü galerisi düğümü ekler** yazın.

5. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmesini seçin.

6. **Yeni varlık Ekle** Iletişim kutusundaki **tür** listesinde **Microsoft. VisualStudio. MefComponent** öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

8. **Project** listesinde, **webpartnodeextension**' ı seçin ve ardından **tamam** düğmesini seçin.

9. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından çözümün hatasız derlendiğinden emin olun.

10. WebPartNode projesi için derleme çıkış klasörünün şimdi WebPartNode. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... proje dosyanızı içeren klasörün altındaki \bin\Debug klasörü.

## <a name="test-the-extension"></a>Uzantıyı test etme
 Artık **Sunucu Gezgini** yeni **Web Bölümü Galerisi** düğümünü test etmeye hazırsınız. İlk olarak, Visual Studio deneysel örneğinde uzantı projesinde hata ayıklamaya başlayın. sonra, Visual Studio deneysel örneğinde yeni **Web Bölümleri** düğümünü kullanın.

#### <a name="to-start-debugging-the-extension"></a>Uzantının hatalarını ayıklamaya başlamak için

1. yönetici kimlik bilgileriyle Visual Studio yeniden başlatın ve ardından **webpartnode** çözümünü açın.

2. WebPartNodeExtension projesinde, **SiteNodeExtension** kod dosyasını açın ve ardından ve yöntemlerinde ilk kod satırlarına bir kesme noktası ekleyin `NodeChildrenRequested` `CreateWebPartNodes` .

3. Hata ayıklamayı başlatmak için **F5** tuşunu seçin.

     Visual Studio, uzantısı, Server explorer\1.0 için%userprofıle%\appdata\local\microsoft\visualstudio\11.0exp\extensions\contoso\web bölümü galerisi düğüm uzantısına ve Visual Studio deneysel bir örneğini başlatır. Proje öğesini bu Visual Studio örneğinde test edersiniz.

#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için

1. Visual Studio deneysel örneğinde, menü çubuğunda, Sunucu Gezgini **görüntüle**' yi seçin  >  .

2. test için kullanmak istediğiniz SharePoint sitesinin **Sunucu Gezgini** **SharePoint bağlantıları** düğümü altında göründüğünü doğrulayın. Listede yoksa, aşağıdaki adımları izleyin:

    1. **SharePoint bağlantıları** için kısayol menüsünü açın ve sonra **bağlantı ekle**' yi seçin.

    2. **SharePoint bağlantısı ekle** iletişim kutusunda, bağlanmak istediğiniz SharePoint sitesinin URL 'sini girin ve **tamam** düğmesini seçin.

         geliştirme bilgisayarınızda SharePoint sitesini belirtmek için, yazın **http://localhost** .

3. Site bağlantısı düğümünü (sitenizin URL 'sini gösterir) genişletin ve sonra bir alt site düğümünü (örneğin, **ekip sitesi**) genişletin.

4. diğer Visual Studio örneğindeki kodun, yöntemde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `NodeChildrenRequested` ve sonra projede hata ayıklamaya devam etmek için **F5** tuşunu seçin.

5. Visual Studio deneysel örneğinde, üst düzey site düğümü altında görünen **Web bölümü galerisi** düğümünü genişletin.

6. diğer Visual Studio örneğindeki kodun, yöntemde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `CreateWebPartNodes` ve sonra projede hata ayıklamaya devam etmek için **F5** tuşunu seçin.

7. Visual Studio deneysel örneğinde, bağlantılı sitedeki tüm Web Bölümleri **Sunucu Gezgini**' deki **Web bölümü galerisi** düğümünün altında göründüğünü doğrulayın.

8. Bir Web bölümü için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

9. **Özellikler** penceresinde web bölümüyle ilgili ayrıntıların göründüğünü doğrulayın.

10. **Sunucu Gezgini**' de, aynı Web bölümü için kısayol menüsünü açın ve ardından **ileti görüntüle**' yi seçin.

     Görüntülenen ileti kutusunda **Tamam** düğmesini seçin.

## <a name="uninstall-the-extension-from-visual-studio"></a>Uzantıyı Visual Studio kaldır
 Uzantıyı test etmeyi bitirdikten sonra, Visual Studio ' den kaldırın.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Visual Studio deneysel örneğinde, menü çubuğunda **araçlar**  >  **uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde, **Sunucu Gezgini Için Web Bölümü Galerisi düğümünü** seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda **Evet** düğmesini seçin.

4. Kaldırma işlemini gerçekleştirmek için **Şimdi yeniden Başlat** düğmesini seçin.

     Proje öğesi de kaldırılır.

5. her iki Visual Studio örneğini (deneysel örnek ve webpartnode çözümünün açık olduğu Visual Studio örneğini) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için bir simge veya diğer görüntü &#40;görüntü Düzenleyicisi oluşturma&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)