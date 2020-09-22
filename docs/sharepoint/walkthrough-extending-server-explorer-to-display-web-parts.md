---
title: 'İzlenecek yol: Web Bölümleri göstermek için Sunucu Gezgini genişletme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 915a1762782b2bf7177b87a3a5f4cdc6e08c6405
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90739999"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme
  Visual Studio 'da SharePoint sitelerindeki bileşenleri görüntülemek için **Sunucu Gezgini** **SharePoint bağlantıları** düğümünü kullanabilirsiniz. Ancak **Sunucu Gezgini** , bazı bileşenleri varsayılan olarak göstermez. Bu kılavuzda, her bağlı SharePoint sitesinde Web Bölümü galerisini görüntüleyecek şekilde **Sunucu Gezgini** genişleteceksiniz.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Aşağıdaki yollarla **Sunucu Gezgini** genişleten bir Visual Studio uzantısı oluşturma:

  - Uzantı, **Sunucu Gezgini**Içindeki her SharePoint site düğümünün altına bir **Web Bölümü Galerisi** düğümü ekler. Bu yeni düğüm, sitede Web Bölümü galerisinde her bir Web bölümünü temsil eden alt düğümleri içerir.

  - Uzantı, bir Web bölümü örneğini temsil eden yeni bir düğüm türü tanımlar. Bu yeni düğüm türü, yeni **Web Bölümü Galerisi** düğümü altındaki alt düğümlerin temelini oluşturur. Yeni Web Bölümü düğüm türü, **Özellikler** penceresinde temsil ettiği Web Bölümü hakkındaki bilgileri görüntüler. Düğüm türü Ayrıca, Web bölümüyle ilgili diğer görevleri gerçekleştirmek için bir başlangıç noktası olarak kullanabileceğiniz özel bir kısayol menü öğesi de içerir.

- Uzantı derlemesinin çağırdığı iki özel SharePoint komutu oluşturun. SharePoint komutları, SharePoint için sunucu nesne modelinde API 'Leri kullanmak için uzantı derlemeleri tarafından çağrılabilen yöntemlerdir. Bu izlenecek yolda, geliştirme bilgisayarındaki yerel SharePoint sitesinden Web bölümü bilgilerini alan komutlar oluşturacaksınız. Daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Uzantıyı dağıtmak için bir Visual Studio uzantısı (VSıX) paketi oluşturma.

- Uzantı hatalarını ayıklama ve test etme.

> [!NOTE]
> Bu izlenecek yolun sunucu nesne modeli yerine SharePoint için istemci nesne modelini kullanan alternatif bir sürümü için, bkz. [Izlenecek yol: SharePoint istemci nesne modelini bir Sunucu Gezgini uzantısında çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows, SharePoint ve Visual Studio sürümleri.

- Visual Studio SDK 'Sı. Bu izlenecek yol, Proje öğesini dağıtmak üzere bir VSıX paketi oluşturmak için SDK 'daki **VSIX proje** şablonunu kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- SharePoint için sunucu nesne modelini kullanma. Daha fazla bilgi için bkz. [SharePoint Foundation sunucu tarafı nesne modelini kullanma](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- SharePoint Çözümlerinde Web Bölümleri. Daha fazla bilgi için bkz. [Web bölümleri genel bakış](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için üç proje oluşturmanız gerekir:

- Uzantıyı dağıtmak için VSıX paketini oluşturmak üzere bir VSıX projesi.

- Uzantıyı uygulayan bir sınıf kitaplığı projesi. Bu projenin .NET Framework 4,5 ' i hedeflemesi gerekir.

- Özel SharePoint komutlarını tanımlayan bir sınıf kitaplığı projesi. Bu proje the.NET Framework 3,5 ' i hedeflemelidir.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

3. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > **Genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'sını yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

5. **VSIX proje** şablonu ' nu seçin, proje **WebPartNode**olarak adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNode** projesini **Çözüm Gezgini**ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#** düğümünü veya **Visual Basic** düğümünü genişletin ve ardından **Windows** düğümünü seçin.

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

4. Proje şablonları listesinde, **sınıf kitaplığı**' nı seçin, projeyi **WebPartNodeExtension**olarak adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüme bir **WebPartNodeExtension** projesi ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projesi oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#** düğümünü veya **Visual Basic** düğümünü genişletin ve ardından **Windows** düğümünü seçin.

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 3,5** ' ı seçin.

4. Proje şablonları listesinde, **sınıf kitaplığı**' nı seçin, projeyi **WebPartCommands**olarak adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüme bir **WebPartCommands** projesi ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Uzantıyı oluşturmak için kod yazmadan önce kod dosyalarını ve derleme başvurularını eklemeniz ve proje ayarlarını yapılandırmanız gerekir.

#### <a name="to-configure-the-webpartnodeextension-project"></a>WebPartNodeExtension projesini yapılandırmak için

1. WebPartNodeExtension projesinde, aşağıdaki adlara sahip dört kod dosyası ekleyin:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. **WebPartNodeExtension** projesi için kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

3. **Başvuru Yöneticisi-WebPartNodeExtension** Iletişim kutusunda **Framework** sekmesini seçin ve ardından aşağıdaki derlemelerin her biri için onay kutusunu seçin:

    - System. ComponentModel. Composition

    - System. Windows. Forms

4. **Uzantılar** sekmesini seçin, Microsoft. VisualStudio. SharePoint derlemesinin onay kutusunu seçin ve **Tamam** düğmesini seçin.

5. **Çözüm Gezgini**, **WebPartNodeExtension** proje düğümünün kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

     **Proje Tasarımcısı** açılır.

6. **Uygulama** sekmesini seçin.

7. **Varsayılan ad alanı** kutusuna (C#) veya **kök ad alanı** kutusuna ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) **ServerExplorer. SharePointConnections. WebPartNode**yazın.

#### <a name="to-configure-the-webpartcommands-project"></a>WebPartCommands projesini yapılandırmak için

1. WebPartCommands projesinde, WebPartCommands adlı bir kod dosyası ekleyin.

2. **Çözüm Gezgini**, **WebPartCommands** proje düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Varolan öğe**' yi seçin.

3. **Varolan öğe Ekle** iletişim kutusunda, WebPartNodeExtension projesi için kod dosyalarını içeren klasöre gidin ve ardından WebPartNodeInfo ve WebPartCommandIds kod dosyalarını seçin.

4. **Ekle** düğmesinin yanındaki oku seçin ve açılan menüden **bağlantı olarak ekle** ' yi seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kod dosyalarını, bağlantı olarak WebPartCommands projesine ekler. Sonuç olarak, kod dosyaları WebPartNodeExtension projesinde bulunur, ancak dosyalardaki kod de WebPartCommands projesinde derlenir.

5. **WebPartCommands** projesinin kısayol menüsünü yeniden açın ve **Başvuru Ekle**' yi seçin.

6. **Başvuru Yöneticisi-WebPartCommands** iletişim kutusunda, **Uzantılar** sekmesini seçin, aşağıdaki derlemelerin her biri için onay kutusunu seçin ve ardından **Tamam** düğmesini seçin:

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

7. **Çözüm Gezgini**, **WebPartCommands** projesinin kısayol menüsünü yeniden açın ve ardından **Özellikler**' i seçin.

     **Proje Tasarımcısı** açılır.

8. **Uygulama** sekmesini seçin.

9. **Varsayılan ad alanı** kutusuna (C#) veya **kök ad alanı** kutusuna ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) **ServerExplorer. SharePointConnections. WebPartNode**yazın.

## <a name="create-icons-for-the-new-nodes"></a>Yeni düğümler için simgeler oluşturma
 **Sunucu Gezgini** uzantısı için iki simge oluşturun: yeni **Web Bölümü Galerisi** düğümü Için bir simge ve **Web Bölümü Galerisi** düğümü altındaki her bir alt Web bölümü düğümü için başka bir simge. Bu izlenecek yolda daha sonra bu simgeleri düğümlerle ilişkilendiren kodu yazacaksınız.

#### <a name="to-create-icons-for-the-nodes"></a>Düğümler için simgeler oluşturmak için

1. **Çözüm Gezgini**, **WebPartNodeExtension** projesi için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. **Proje Tasarımcısı** açılır.

3. **Kaynaklar** sekmesini seçin ve ardından **Bu proje varsayılan bir kaynak dosyası içermez öğesini seçin. Bir bağlantı oluşturmak için buraya tıklayın** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir kaynak dosyası oluşturur ve tasarımcıda açar.

4. Tasarımcının üst kısmında, **Kaynak Ekle** menü komutunun yanındaki oku seçin ve açılan menüden **Yeni simge Ekle** ' yi seçin.

5. **Yeni Kaynak Ekle** iletişim kutusunda, yeni simgeyi **WebPartsNode**olarak adlandırın ve ardından **Ekle** düğmesini seçin.

     Yeni simge **görüntü düzenleyicisinde**açılır.

6. Simgenin 16x16 sürümünü, kolayca tanıyabileceğiniz bir tasarıma sahip olacak şekilde düzenleyin.

7. Simgenin 32x32 sürümüne ait kısayol menüsünü açın ve ardından **görüntü türünü sil**' i seçin.

8. Proje kaynaklarına ikinci bir simge eklemek ve bu simge **Web bölümünü**adlandırmak için 5 ' ten 8 ' e kadar olan adımları yineleyin.

9. **Çözüm Gezgini**, **WebPartNodeExtension** projesi için **kaynaklar** klasörü altında, **WebPartsNode. ico**için kısayol menüsünü açın.

10. **Özellikler** penceresinde, **derleme eylemi**' nin yanındaki oku seçin ve açılan menüden **gömülü kaynak** ' ı seçin.

11. **WebPart. ico**için son iki adımı tekrarlayın.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini ekleyin
 Yeni **Web Bölümü Galerisi** düğümünü her bir SharePoint site düğümüne ekleyen bir sınıf oluşturun. Yeni düğümü eklemek için sınıfı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> arabirimini uygular. Bir düğüme alt düğüm ekleme gibi **Sunucu Gezgini**var olan bir düğümün davranışını her genişletmek istediğinizde bu arabirimi uygulayın.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini eklemek için

1. WebPartNodeExtension projesinde, SiteNodeExtension kod dosyasını açın ve ardından aşağıdaki kodu içine yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra, projede bazı derleme hataları olacaktır, ancak sonraki adımlarda kod eklediğinizde bu işlemler kaybolur.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Bir Web bölümünü temsil eden bir düğüm türü tanımlama
 Bir Web bölümünü temsil eden yeni bir düğüm türünü tanımlayan bir sınıf oluşturun. Visual Studio, **Web Bölümü Galerisi** düğümünün altında alt düğümleri göstermek için bu yeni düğüm türünü kullanır. Her alt düğüm, SharePoint sitesindeki tek bir Web bölümünü temsil eder.

 Yeni düğüm türünü tanımlamak için sınıfı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> arabirimini uygular. **Sunucu Gezgini**yeni bir düğüm türü tanımlamak istediğinizde bu arabirimi uygulayın.

#### <a name="to-define-the-web-part-node-type"></a>Web Bölümü düğüm türünü tanımlamak için

1. WebPartNodeExtension projesinde, WebPartNodeTypeProvder kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Web bölümü veri sınıfını tanımlama
 SharePoint sitesindeki tek bir Web Bölümü hakkında veri içeren bir sınıf tanımlayın. Bu kılavuzda daha sonra, sitedeki her bir Web Bölümü hakkında verileri alan ve ardından verileri bu sınıfın örneklerine atayan özel bir SharePoint komutu oluşturacaksınız.

#### <a name="to-define-the-web-part-data-class"></a>Web bölümü veri sınıfını tanımlamak için

1. WebPartNodeExtension projesinde, WebPartNodeInfo kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>SharePoint komutlarının kimliklerini tanımlama
 Özel SharePoint komutlarını tanımlayan birkaç dize tanımlayın. Bu komutları daha sonra Bu izlenecek yolda uygulayacaksınız.

#### <a name="to-define-the-command-ids"></a>Komut kimliklerini tanımlamak için

1. WebPartNodeExtension projesinde, WebPartCommandIds kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Özel SharePoint komutlarını oluşturma
 SharePoint sitesindeki Web Bölümleri ilgili verileri almak için SharePoint sunucu nesne modeline çağıran özel komutlar oluşturun. Her komut, <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> kendisine uygulanan bir yöntemdir.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutlarını tanımlamak için

1. WebPartCommands projesinde, WebPartCommands kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Checkpoint
 Bu noktada, **Web Bölümü Galerisi** düğümü ve SharePoint komutları için tüm kodlar artık projelerde bulunur. Her iki projenin hatasız derlendiğinden emin olmak için çözümü oluşturun.

#### <a name="to-build-the-solution"></a>Çözümü oluşturmak için

1. Menü **çubuğunda Build**  >  **Build Solution**öğesini seçin.

    > [!WARNING]
    > Bu noktada, VSıX bildirim dosyası yazar için bir değere sahip olmadığından WebPartNode projesinde bir yapı hatası olabilir. Sonraki adımlarda bir değer eklediğinizde bu hata geçer.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, VSıX projesinde kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-the-vsix-package"></a>VSıX paketini yapılandırmak için

1. **Çözüm Gezgini**, WebPartNode projesi altında, bildirim düzenleyicisinde **Source. Extension. valtmanifest** dosyasını açın.

     Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)).

2. **Ürün adı** kutusuna **Sunucu Gezgini Için Web Bölümü Galerisi düğümünü**girin.

3. **Yazar** kutusuna **contoso**girin.

4. **Açıklama** kutusuna, **Sunucu Gezgini SharePoint bağlantıları düğümüne özel bir Web Bölümü Galerisi düğümü ekler yazın. Bu uzantı sunucu nesne modeline çağırmak için özel bir SharePoint komutu kullanır.**

5. Düzenleyicinin **varlıklar** sekmesini seçin ve ardından **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

6. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent**öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje**seçin.

8. **Proje** listesinde, **WebPartNodeExtension** ' ı ve sonra **Tamam** düğmesini seçin.

9. Bildirim düzenleyicisinde **Yeni** düğmesini yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

10. **Tür** kutusuna **SharePoint. Commands. v4**yazın.

    > [!NOTE]
    > Bu öğe, Visual Studio uzantısına eklemek istediğiniz özel bir uzantıyı belirtir. Daha fazla bilgi için bkz. [varlık öğesi (VSX şeması)](/previous-versions/dd393737(v=vs.110)).

11. **Kaynak** listesinde, geçerli çözüm listesi öğesinde **bir proje** seçin.

12. **Proje** listesinde, **WebPartCommands**' i ve sonra **Tamam** düğmesini seçin.

13. Menü **çubuğunda Build**  >  **Build Solution**öğesini seçin ve ardından çözümün hatasız derlendiğinden emin olun.

14. WebPartNode projesi için derleme çıkış klasörünün şimdi WebPartNode. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... proje dosyanızı içeren klasörün altındaki \bin\Debug klasörü.

## <a name="test-the-extension"></a>Uzantıyı test etme
 Artık **Sunucu Gezgini**yeni **Web Bölümü Galerisi** düğümünü test etmeye hazırsınız. İlk olarak, Visual Studio 'nun deneysel örneğinde uzantının hata ayıklamasını başlatın. Ardından, deneysel örneğinde yeni **Web bölümleri** düğümünü kullanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>Uzantının hatalarını ayıklamaya başlamak için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Yönetici kimlik bilgileriyle yeniden başlatın ve ardından WebPartNode çözümünü açın.

2. WebPartNodeExtension projesinde, SiteNodeExtension kod dosyasını açın ve ardından ve yöntemlerinde ilk kod satırına bir kesme noktası ekleyin `NodeChildrenRequested` `CreateWebPartNodes` .

3. Hata ayıklamayı başlatmak için **F5** tuşunu seçin.

     Visual Studio, uzantısı, Server Explorer\1.0 için%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Bölümü Galerisi düğüm uzantısına ve Visual Studio 'nun deneysel bir örneğini başlatır. Bu Visual Studio örneğinde Proje öğesini test edersiniz.

#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için

1. Deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , menü çubuğunda Sunucu Gezgini **görüntüle**' yi seçin  >  **Server Explorer**.

2. Test için kullanmak istediğiniz SharePoint sitesi **Sunucu Gezgini**' deki **SharePoint bağlantıları** düğümü altında görünmezse aşağıdaki adımları gerçekleştirin:

    1. **Sunucu Gezgini**' de **SharePoint bağlantıları**için kısayol menüsünü açın ve ardından **bağlantı ekle**' yi seçin.

    2. **SharePoint bağlantısı ekle** iletişim kutusunda, bağlanmak istediğiniz SharePoint sitesinin URL 'sini girin ve **Tamam** düğmesini seçin.

         Geliştirme bilgisayarınızda SharePoint sitesini belirtmek için girin **http://localhost** .

3. Site bağlantısı düğümünü (sitenizin URL 'sini gösterir) genişletin ve sonra bir alt site düğümünü (örneğin, **ekip sitesi**) genişletin.

4. Diğer örneğindeki kodun, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yönteminde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `NodeChildrenRequested` ve sonra projede hata ayıklamaya devam etmek için **F5** ' i seçin.

5. Visual Studio 'nun deneysel örneğinde, en üst düzey site düğümü altında **Web Bölümü Galerisi** adlı yeni bir düğümün göründüğünü doğrulayın ve ardından **Web Bölümü Galerisi** düğümünü genişletin.

6. Visual Studio 'nun diğer örneğindeki kodun, yönteminde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `CreateWebPartNodes` ve sonra projede hata ayıklamaya devam etmek Için **F5** tuşunu seçin.

7. Visual Studio 'nun deneysel örneğinde, bağlantılı sitedeki tüm Web Bölümleri **Sunucu Gezgini** **Web Bölümü Galerisi** düğümünün altında göründüğünü doğrulayın.

8. **Sunucu Gezgini**' de, Web bölümleri biri için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

9. Hata ayıklaması yaptığınız örnekte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **Özellikler** penceresinde web bölümüyle ilgili ayrıntıların göründüğünü doğrulayın.

## <a name="uninstall-the-extension-from-visual-studio"></a>Uzantıyı Visual Studio 'dan kaldırma
 Uzantıyı sınamayı bitirdikten sonra, uzantıyı Visual Studio 'dan kaldırın.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , menü çubuğunda **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde, **Sunucu Gezgini Için Web Bölümü Galerisi düğüm uzantısı**' nı seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin ve ardından kaldırma işlemini gerçekleştirmek Için **Şimdi yeniden Başlat** düğmesini seçin.

4. Her iki Visual Studio örneğini kapatın (WebPartNode çözümünün açık olduğu deneysel örnek ve Visual Studio örneği).

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [İzlenecek yol: Sunucu Gezgini uzantısında SharePoint istemci nesne modelini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için bir simge veya diğer görüntü &#40;görüntü Düzenleyicisi oluşturma&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)