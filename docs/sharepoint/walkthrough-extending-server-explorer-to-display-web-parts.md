---
title: "Adım adım kılavuz: Sunucu Gezgini'i Görüntü Ekranı'Web Bölümleri | Microsoft Docs"
titleSuffix: ''
description: Bu kılavuzda, bağlı Sunucu Gezgini web sitesi üzerinde Web Bölümü galerisini görüntüecek şekilde SharePoint genişletebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7654b6b4f73ea3245cb4d21480eb4db4ceabc648
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148772"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Adım adım kılavuz: Sunucu Gezgini bölümlerini görüntülemek için uygulamanın süresini genişletme
  Bu Visual Studio, sitelerde bileşenleri **SharePoint** için **Sunucu Gezgini** bağlantılar düğümünü SharePoint kullanabilirsiniz. Ancak **Sunucu Gezgini** varsayılan olarak bazı bileşenleri görüntülemez. Bu kılavuzda, bağlı Sunucu Gezgini  web sitesi üzerinde Web Bölümü galerisini görüntülemesi için bu SharePoint gerekir.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Aşağıdaki Visual Studio genişleten **bir Sunucu Gezgini** uzantısı oluşturma:

  - Uzantı, **'deki her bir** site düğümüne SharePoint Web Bölümü **Galerisi** Sunucu Gezgini. Bu yeni düğüm, sitedeki Web Bölümü galerisinde her Bir Web Bölümünü temsil eden alt düğümler içerir.

  - Uzantı, Web Bölümü örneğini temsil eden yeni bir düğüm türünü tanımlar. Bu yeni düğüm türü, yeni Web Bölümü Galerisi düğümü altındaki alt **düğümlerin temelini** sağlar. Yeni Web Bölümü düğüm türü, Özellikler penceresinde **temsil** ettiği Web Bölümü ile ilgili bilgileri görüntüler. Düğüm türü, Web Bölümü ile ilgili diğer görevleri gerçekleştirmek için başlangıç noktası olarak kullanabileceğiniz özel bir kısayol menü öğesi de içerir.

- Uzantı derlemesi tarafından SharePoint özel komutlar oluşturun. SharePoint komutları, uzantı derlemeleri tarafından sunucu nesne modelinde API'leri kullanmak üzere çağrıl SharePoint. Bu kılavuzda, geliştirme bilgisayarına yerel siteden Web Bölümü bilgilerini SharePoint komutlar oluşturabilirsiniz. Daha fazla bilgi için [bkz. SharePoint nesne modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Uzantıyı Visual Studio bir Uzantı (VSIX) paketi oluşturma.

- Uzantıda hata ayıklama ve test etme.

> [!NOTE]
> Bu izlenecek yol'un sunucu nesne modeli yerine SharePoint için istemci nesne modelini kullanan alternatif bir sürümü için bkz. Adım adım: Sunucu Gezgini uzantısında SharePoint istemci nesne [modeline çağırma.](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows, SharePoint ve Visual Studio.

- Visual Studio SDK'sı. Bu kılavuzda, **proje öğesini Project** bir VSIX paketi oluşturmak için SDK'daki VSIX uygulama şablonu kullanılır. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

  Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- SharePoint için sunucu nesne modelini kullanma. Daha fazla bilgi için [bkz. SharePoint Foundation Server-Side Nesne Modelini Kullanma.](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14))

- Web Bölümleri çözümlerde SharePoint. Daha fazla bilgi için [bkz. Web Bölümleri Genel Bakış.](/previous-versions/office/ms432401(v=office.14))

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için üç proje oluşturmanız gerekir:

- Uzantıyı dağıtmak için VSIX paketini oluşturmak için bir VSIX projesi.

- Uzantıyı uygulayan bir sınıf kitaplığı projesi. Bu projenin 4.5 .NET Framework hedeflesi gerekir.

- Özel uygulama ve komutlarını tanımlayan bir SharePoint projesi. Bu proje, the.NET Framework 3.5'i hedeflemeli.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-vsix-project"></a>VSIX projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Menü çubuğunda Dosya Yeni'yi **seçin**  >  **ve**  >  **Project.**

3. Yeni **Project** iletişim kutusunda **Visual C#** **veya** Visual Basic genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

    > [!NOTE]
    > **Genişletilebilirlik düğümü** yalnızca Visual Studio SDK'sı yüklüyse kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework sürümleri **listesinden 4.5'i** .NET Framework.

5. **VSIX Project** şablonunu seçin, projeye **WebPartNode** adını ve ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNode projesini** **uygulamasına Çözüm Gezgini.**

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **seçin** ve ardından Yeni **oluştur'Project.**

2. Yeni **Project** iletişim **kutusunda, Visual C#** düğümünü **veya** Visual Basic düğümünü genişletin ve ardından Windows **seçin.**

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri **listesinden 4.5'i** .NET Framework.

4. Proje şablonları listesinde Sınıf Kitaplığı'yı **seçin,** projeyi **WebPartNodeExtension olarak adlandırın** ve ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNodeExtension** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **seçin** ve ardından Yeni **oluştur'Project.**

2. Yeni **Project** iletişim **kutusunda, Visual C#** düğümünü **veya Visual Basic** düğümünü genişletin ve Windows **seçin.**

3. İletişim kutusunun üst kısmında, .NET Framework **sürümleri listesinden 3.5'i** .NET Framework.

4. Proje şablonları listesinde Sınıf Kitaplığı'yı **seçin,** projeye **WebPartCommands** adını ve ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartCommands projesini** çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Uzantıyı oluşturmak için kod yazmadan önce kod dosyaları ve derleme başvuruları eklemeniz ve proje ayarlarını yapılandırmanız gerekir.

#### <a name="to-configure-the-webpartnodeextension-project"></a>WebPartNodeExtension projesini yapılandırmak için

1. WebPartNodeExtension projesine aşağıdaki adlara sahip dört kod dosyası ekleyin:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. **WebPartNodeExtension projesinin kısayol menüsünü açın** ve Başvuru Ekle'yi **seçin.**

3. Başvuru **Yöneticisi - WebPartNodeExtension** iletişim kutusunda **Çerçeve** sekmesini seçin ve ardından aşağıdaki derlemelerin her biri için onay kutusunu seçin:

    - System.ComponentModel.Composition

    - Sistem. Windows. Forms

4. Uzantılar **sekmesini** seçin, Microsoft.VisualStudio onay kutusunu seçin. SharePoint ve ardından Tamam **düğmesini** seçin.

5. Bu **Çözüm Gezgini** **WebPartNodeExtension** proje düğümü için kısayol menüsünü açın ve Özellikler'i **seçin.**

     Project **Tasarımcısı** açılır.

6. Uygulama **sekmesini** seçin.

7. Varsayılan ad **alanı kutusuna** (C#) veya **Kök ad** alanı kutusuna ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), **ServerExplorer.SharePointConnections.WebPartNode girin.**

#### <a name="to-configure-the-webpartcommands-project"></a>Webpartcommands projesini yapılandırmak için

1. WebPartCommands projesine WebPartCommands adlı bir kod dosyası ekleyin.

2. Bu **Çözüm Gezgini** **WebPartCommands** proje düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Var Olan Öğe'yi **seçin.**

3. Var **Olan Öğeyi Ekle** iletişim kutusunda, WebPartNodeExtension projesinin kod dosyalarını içeren klasöre göz atarak WebPartNodeInfo ve WebPartCommandIds kod dosyalarını seçin.

4. Ekle düğmesinin yanındaki **oku seçin** ve sonra görüntülenen **menüden Farklı** Ekle Bağlantısı'ı seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Kod dosyalarını WebPartCommands projesine bağlantılar olarak ekler. Sonuç olarak, kod dosyaları WebPartNodeExtension projesinde bulunur, ancak dosyalarda yer alan kod da WebPartCommands projesinde derlenmiş olur.

5. **WebPartCommands projesinin kısayol menüsünü yeniden** açın ve Başvuru Ekle'yi **seçin.**

6. Başvuru **Yöneticisi - WebPartCommands** iletişim kutusunda  Uzantılar sekmesini seçin, aşağıdaki derlemelerin her biri için onay kutusunu seçin ve ardından **Tamam düğmesini** seçin:

    - Microsoft. SharePoint

    - Microsoft.VisualStudio. SharePoint. Komut

7. Bu **Çözüm Gezgini** **WebPartCommands** projesinin kısayol menüsünü yeniden açın ve Özellikler'i **seçin.**

     Project **Tasarımcısı** açılır.

8. Uygulama **sekmesini** seçin.

9. Varsayılan ad **alanı kutusuna** (C#) veya **Kök ad** alanı kutusuna ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), **ServerExplorer.SharePointConnections.WebPartNode girin.**

## <a name="create-icons-for-the-new-nodes"></a>Yeni düğümler için simgeler oluşturma
 **Sunucu Gezgini** uzantısı için iki simge oluşturun: yeni **Web** Bölümü Galerisi düğümü için bir simge ve Web Bölümü Galerisi düğümü altındaki her alt Web Bölümü düğümü için **başka bir** simge. Bu kılavuzda daha sonra bu simgeleri düğümlerle ilişkilendiren kod yazacağız.

#### <a name="to-create-icons-for-the-nodes"></a>Düğümler için simgeler oluşturmak için

1. Bu **Çözüm Gezgini** **WebPartNodeExtension** projesinin kısayol menüsünü açın ve Özellikler'i **seçin.**

2. **Project tasarımcısı** açılır.

3. **Kaynaklar** sekmesini seçin ve ardından **Bu proje varsayılan bir kaynak dosyası içermez öğesini seçin. Bir bağlantı oluşturmak için buraya tıklayın** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir kaynak dosyası oluşturur ve tasarımcıda açar.

4. Tasarımcının üst kısmında, **Kaynak Ekle** menü komutunun yanındaki oku seçin ve açılan menüden **Yeni simge Ekle** ' yi seçin.

5. **Yeni Kaynak Ekle** iletişim kutusunda, yeni simgeyi **WebPartsNode** olarak adlandırın ve ardından **Ekle** düğmesini seçin.

     Yeni simge **görüntü düzenleyicisinde** açılır.

6. Simgenin 16x16 sürümünü, kolayca tanıyabileceğiniz bir tasarıma sahip olacak şekilde düzenleyin.

7. Simgenin 32x32 sürümüne ait kısayol menüsünü açın ve ardından **görüntü türünü sil**' i seçin.

8. Proje kaynaklarına ikinci bir simge eklemek ve bu simge **Web bölümünü** adlandırmak için 5 ' ten 8 ' e kadar olan adımları yineleyin.

9. **Çözüm Gezgini**, **WebPartNodeExtension** projesi için **kaynaklar** klasörü altında, **WebPartsNode. ico** için kısayol menüsünü açın.

10. **Özellikler** penceresinde, **derleme eylemi**' nin yanındaki oku seçin ve açılan menüden **gömülü kaynak** ' ı seçin.

11. **WebPart. ico** için son iki adımı tekrarlayın.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini ekleyin
 her bir SharePoint site düğümüne yeni **Web bölümü galerisi** düğümünü ekleyen bir sınıf oluşturun. Yeni düğümü eklemek için sınıfı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> arabirimini uygular. Bir düğüme alt düğüm ekleme gibi **Sunucu Gezgini** var olan bir düğümün davranışını her genişletmek istediğinizde bu arabirimi uygulayın.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini eklemek için

1. WebPartNodeExtension projesinde, SiteNodeExtension kod dosyasını açın ve ardından aşağıdaki kodu içine yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra, projede bazı derleme hataları olacaktır, ancak sonraki adımlarda kod eklediğinizde bu işlemler kaybolur.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>Bir Web bölümünü temsil eden bir düğüm türü tanımlama
 Bir Web bölümünü temsil eden yeni bir düğüm türünü tanımlayan bir sınıf oluşturun. Visual Studio, **Web bölümü galerisi** düğümünün altında alt düğümleri göstermek için bu yeni düğüm türünü kullanır. her alt düğüm SharePoint sitesinde tek bir Web bölümünü temsil eder.

 Yeni düğüm türünü tanımlamak için sınıfı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> arabirimini uygular. **Sunucu Gezgini** yeni bir düğüm türü tanımlamak istediğinizde bu arabirimi uygulayın.

#### <a name="to-define-the-web-part-node-type"></a>Web Bölümü düğüm türünü tanımlamak için

1. WebPartNodeExtension projesinde, WebPartNodeTypeProvder kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::

## <a name="define-the-web-part-data-class"></a>Web bölümü veri sınıfını tanımlama
 SharePoint sitesindeki tek bir Web bölümü hakkında veri içeren bir sınıf tanımlayın. bu kılavuzda daha sonra, sitedeki her bir Web bölümü hakkında verileri alan ve ardından verileri bu sınıfın örneklerine atayan özel bir SharePoint komutu oluşturacaksınız.

#### <a name="to-define-the-web-part-data-class"></a>Web bölümü veri sınıfını tanımlamak için

1. WebPartNodeExtension projesinde, WebPartNodeInfo kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs" id="Snippet3":::

## <a name="define-the-ids-for-the-sharepoint-commands"></a>SharePoint komutlarının kimliklerini tanımlayın
 özel SharePoint komutlarını tanımlayan birkaç dize tanımlayın. Bu komutları daha sonra Bu izlenecek yolda uygulayacaksınız.

#### <a name="to-define-the-command-ids"></a>Komut kimliklerini tanımlamak için

1. WebPartNodeExtension projesinde, WebPartCommandIds kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb" id="Snippet4":::

## <a name="create-the-custom-sharepoint-commands"></a>özel SharePoint komutlarını oluşturma
 SharePoint sitesindeki Web Bölümleri hakkında verileri almak için SharePoint sunucu nesne modeline çağıran özel komutlar oluşturun. Her komut, <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> kendisine uygulanan bir yöntemdir.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutlarını tanımlamak için

1. WebPartCommands projesinde, WebPartCommands kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb" id="Snippet6":::

## <a name="checkpoint"></a>Checkpoint
 bu noktada, **Web bölümü galerisi** düğümü için tüm kod ve SharePoint komutları artık projelerde bulunur. Her iki projenin hatasız derlendiğinden emin olmak için çözümü oluşturun.

#### <a name="to-build-the-solution"></a>Çözümü oluşturmak için

1. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

    > [!WARNING]
    > Bu noktada, VSıX bildirim dosyası yazar için bir değere sahip olmadığından WebPartNode projesinde bir yapı hatası olabilir. Sonraki adımlarda bir değer eklediğinizde bu hata geçer.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, VSıX projesinde kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-the-vsix-package"></a>VSıX paketini yapılandırmak için

1. **Çözüm Gezgini**, WebPartNode projesi altında, bildirim düzenleyicisinde **Source. Extension. valtmanifest** dosyasını açın.

     Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)).

2. **Ürün adı** kutusuna **Sunucu Gezgini Için Web Bölümü Galerisi düğümünü** girin.

3. **Yazar** kutusuna **contoso** girin.

4. **açıklama** kutusunda, **Sunucu Gezgini SharePoint bağlantıları düğümüne özel bir Web bölümü galerisi düğümü ekler yazın. bu uzantı sunucu nesne modeline çağırmak için özel bir SharePoint komutu kullanır.**

5. Düzenleyicinin **varlıklar** sekmesini seçin ve ardından **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

6. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

8. **Project** listesinde, **webpartnodeextension** ' ı seçin ve ardından **tamam** düğmesini seçin.

9. Bildirim düzenleyicisinde **Yeni** düğmesini yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

10. **Tür** kutusuna **SharePoint girin. Commands. v4**.

    > [!NOTE]
    > bu öğe Visual Studio uzantısına eklemek istediğiniz özel bir uzantıyı belirtir. Daha fazla bilgi için bkz. [varlık öğesi (VSX şeması)](/previous-versions/dd393737(v=vs.110)).

11. **Kaynak** listesinde, geçerli çözüm listesi öğesinde **bir proje** seçin.

12. **Project** listesinde, **webpartcommands**' i ve sonra **tamam** düğmesini seçin.

13. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından çözümün hatasız derlendiğinden emin olun.

14. WebPartNode projesi için derleme çıkış klasörünün şimdi WebPartNode. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... proje dosyanızı içeren klasörün altındaki \bin\Debug klasörü.

## <a name="test-the-extension"></a>Uzantıyı test etme
 Artık **Sunucu Gezgini** yeni **Web Bölümü Galerisi** düğümünü test etmeye hazırsınız. İlk olarak, Visual Studio deneysel bir örneğinde uzantı hata ayıklamaya başlayın. ardından, deneysel örneğinde yeni **Web Bölümleri** düğümünü kullanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>Uzantının hatalarını ayıklamaya başlamak için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Yönetici kimlik bilgileriyle yeniden başlatın ve ardından WebPartNode çözümünü açın.

2. WebPartNodeExtension projesinde, SiteNodeExtension kod dosyasını açın ve ardından ve yöntemlerinde ilk kod satırına bir kesme noktası ekleyin `NodeChildrenRequested` `CreateWebPartNodes` .

3. Hata ayıklamayı başlatmak için **F5** tuşunu seçin.

     Visual Studio, uzantısı, Server explorer\1.0 için%userprofıle%\appdata\local\microsoft\visualstudio\11.0exp\extensions\contoso\web bölümü galerisi düğüm uzantısına ve Visual Studio deneysel bir örneğini başlatır. Proje öğesini bu Visual Studio örneğinde test edersiniz.

#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için

1. Deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , menü çubuğunda Sunucu Gezgini **görüntüle**' yi seçin  >  .

2. test için kullanmak istediğiniz SharePoint sitesi **Sunucu Gezgini**' deki **SharePoint bağlantıları** düğümü altında görünmezse aşağıdaki adımları gerçekleştirin:

    1. **Sunucu Gezgini**' de, **SharePoint bağlantıları** için kısayol menüsünü açın ve sonra **bağlantı ekle**' yi seçin.

    2. **SharePoint bağlantısı ekle** iletişim kutusunda, bağlanmak istediğiniz SharePoint sitesinin URL 'sini girin ve **tamam** düğmesini seçin.

         geliştirme bilgisayarınızda SharePoint sitesini belirtmek için, girin **http://localhost** .

3. Site bağlantısı düğümünü (sitenizin URL 'sini gösterir) genişletin ve sonra bir alt site düğümünü (örneğin, **ekip sitesi**) genişletin.

4. Diğer örneğindeki kodun, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yönteminde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `NodeChildrenRequested` ve sonra projede hata ayıklamaya devam etmek için **F5** ' i seçin.

5. Visual Studio deneysel örneğinde, en üst düzey site düğümü altında **web bölümü galerisi** adlı yeni bir düğümün göründüğünü doğrulayın ve ardından **web bölümü galerisi** düğümünü genişletin.

6. diğer Visual Studio örneğindeki kodun, yöntemde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `CreateWebPartNodes` ve sonra projede hata ayıklamaya devam etmek için **F5** tuşunu seçin.

7. Visual Studio deneysel örneğinde, bağlantılı sitedeki tüm Web Bölümleri **Sunucu Gezgini**' deki **Web bölümü galerisi** düğümünün altında göründüğünü doğrulayın.

8. **Sunucu Gezgini**' de, Web Bölümleri biri için kısayol menüsünü açın ve ardından **özellikler**' i seçin.

9. Hata [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayıklaması yapılan örneğinde, Özellikler penceresinde Web Bölümü ile ilgili ayrıntıların görüntü **olduğunu** doğrulayın.

## <a name="uninstall-the-extension-from-visual-studio"></a>Uzantıyı dosyadan Visual Studio
 Uzantıyı test etme işlemi tamam olduktan sonra uzantıyı Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. deneysel örneğinde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] menü çubuğunda Araçlar Uzantıları ve **Güncelleştirmeler'i**  >  **seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinde, Sunucu Gezgini **için Web Bölümü Galerisi** Düğüm Uzantısı'Sunucu Gezgini ve ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı  kaldırmak istediğinizden emin olmak için Evet düğmesini  seçin ve ardından kaldırma işlemini tamamlamak için Şimdi Yeniden Başlat düğmesini seçin.

4. Her iki Visual Studio (deneysel örnek ve WebPartNode çözümünün Visual Studio örnek) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Kümedeki SharePoint düğümünü Sunucu Gezgini](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Adım adım kılavuz: SharePoint uzantısında istemci nesne modeline Sunucu Gezgini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Simgeler için Görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için Görüntü Düzenleyicisi'nde &#40;Veya Başka Bir Görüntü&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)