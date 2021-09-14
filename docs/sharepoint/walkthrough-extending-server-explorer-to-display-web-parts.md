---
title: "Adım adım kılavuz: Sunucu Gezgini'i Görüntüleme Ekranına Web Bölümleri | Microsoft Docs"
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628209"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Adım adım kılavuz: Web Sunucu Gezgini görüntülemek için uygulamanın süresini genişletme
  Bu Visual Studio sitelerde **bileşenleri SharePoint** için **Sunucu Gezgini** bağlantılar düğümünü SharePoint kullanabilirsiniz. Ancak **Sunucu Gezgini** bazı bileşenler varsayılan olarak görüntülenmez. Bu kılavuzda, bağlı Sunucu Gezgini  web sitesi üzerinde Web Bölümü galerisini görüntüecek şekilde SharePoint genişleteceğiz.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Aşağıdaki Visual Studio uzantıyı **genişleten Sunucu Gezgini** uzantısı oluşturma:

  - Uzantı, **'deki her bir** site düğümüne SharePoint Web Bölümü **Galerisi** Sunucu Gezgini. Bu yeni düğüm, sitedeki Web Bölümü galerisinde her Bir Web Bölümünü temsil eden alt düğümler içerir.

  - Uzantı, Web Bölümü örneğini temsil eden yeni bir düğüm türünü tanımlar. Bu yeni düğüm türü, yeni Web Bölümü Galerisi düğümü altındaki alt **düğümlerin temelini** sağlar. Yeni Web Bölümü düğüm türü, Özellikler penceresinde **temsil** ettiği Web Bölümü ile ilgili bilgileri görüntüler. Düğüm türü, Web Bölümü ile ilgili diğer görevleri gerçekleştirmek için başlangıç noktası olarak kullanabileceğiniz özel bir kısayol menü öğesi de içerir.

- Uzantı derlemesi SharePoint iki özel komut oluşturun. SharePoint komutları, uzantı derlemeleri tarafından sunucu nesne modelinde API'leri kullanmak üzere çağrıl SharePoint. Bu kılavuzda, geliştirme bilgisayarına yerel siteden Web Bölümü bilgilerini SharePoint komutlar oluşturabilirsiniz. Daha fazla bilgi için [bkz. SharePoint nesne modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Uzantıyı Visual Studio için bir Visual Studio Uzantısı (VSIX) paketi oluşturma.

- Uzantıda hata ayıklama ve test etme.

> [!NOTE]
> Sunucu nesne modeli yerine SharePoint için istemci nesne modelini kullanan bu izlenecek yol'un alternatif bir sürümü için bkz. Adım adım: Sunucu Gezgini uzantısında SharePoint istemci [nesne modeline çağırma.](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

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

- Özel uygulama komutlarını tanımlayan bir sınıf SharePoint projesi. Bu proje, the.NET Framework 3.5'i hedeflemeli.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-vsix-project"></a>VSIX projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Menü çubuğunda Dosya Yeni'yi **seçin**  >  **ve**  >  **Project.**

3. Yeni **Project** iletişim kutusunda **Visual C#** veya Visual Basic **düğümlerini** genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

    > [!NOTE]
    > **Genişletilebilirlik düğümü** yalnızca Visual Studio SDK'sı yüklenirse kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework **sürümleri listesinden 4.5'i** .NET Framework.

5. **VSIX Project** şablonunu seçin, projeye **WebPartNode** adını ve ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNode projesini** **uygulamasına Çözüm Gezgini.**

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

2. Yeni **Project** iletişim **kutusunda, Visual C#** düğümünü **veya** Visual Basic düğümünü genişletin ve ardından Windows **seçin.**

3. İletişim kutusunun üst kısmında, .NET Framework **sürümleri listesinden 4.5'i** .NET Framework.

4. Proje şablonları listesinde Sınıf Kitaplığı'yı **seçin,** projeyi **WebPartNodeExtension olarak adlandırın** ve ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**WebPartNodeExtension** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

2. Yeni **Project** iletişim kutusunda **Visual C#** düğümünü **veya** Visual Basic düğümünü genişletin ve Windows **seçin.**

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri **listesinden 3.5'i** .NET Framework.

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

2. Bu **Çözüm Gezgini** **WebPartCommands** proje düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Var Olan **Öğe'yi seçin.**

3. Var **Olan Öğeyi Ekle** iletişim kutusunda WebPartNodeExtension projesinin kod dosyalarını içeren klasöre göz atarak WebPartNodeInfo ve WebPartCommandIds kod dosyalarını seçin.

4. Ekle düğmesinin yanındaki **oku seçin** ve sonra görüntülenen **menüden Farklı** Ekle Bağlantısı'ı seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Kod dosyalarını WebPartCommands projesine bağlantılar olarak ekler. Sonuç olarak, kod dosyaları WebPartNodeExtension projesinde bulunur, ancak dosyalarda yer alan kod da WebPartCommands projesinde derlenmiş olur.

5. **WebPartCommands** projesinin kısayol menüsünü yeniden açın ve Başvuru **Ekle'yi seçin.**

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

2. Project **Tasarımcısı** açılır.

3. Kaynaklar **sekmesini** ve ardından Bu proje **varsayılan kaynaklar içermedi dosyasını seçin. Tek bir bağlantı oluşturmak için buraya** tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir kaynak dosyası oluşturur ve tasarımcıda açar.

4. Tasarımcının üst kısmında Kaynak Ekle menü  komutunun yanındaki oku seçin ve sonra görüntülenen **menüden Yeni Ekle Simgesi'ne** tıklayın.

5. Yeni Kaynak **Ekle iletişim** kutusunda yeni simgeye **WebPartsNode adını ve** ardından Ekle **düğmesini** seçin.

     Yeni simge Görüntü **Düzenleyicisi'nde açılır.**

6. Simgenin 16x16 sürümünü, kolayca tanıyabilirsiniz bir tasarıma sahip olacak şekilde düzenleyin.

7. Simgenin 32x32 sürümü için kısayol menüsünü açın ve Ardından Görüntü Türünü **Sil'i seçin.**

8. Proje kaynaklarına ikinci bir simge eklemek için 5 ile 8 arasında adımları tekrarlayın ve bu simgeye **WebPart adını girin.**

9. Bu **Çözüm Gezgini** **WebPartNodeExtension** projesinin Kaynaklar klasörünün altında **WebPartsNode.ico** kısayol menüsünü açın. 

10. Özellikler **penceresinde,** Derleme Eylemi'nin yanındaki **oku seçin** ve sonra görüntülenen menüde **Katıştırılmış** Kaynak'ı seçin.

11. **WebPart.ico için son iki adımı tekrarlayın.**

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini
 Yeni Web Bölümü Galerisi düğümünü her bir **site** düğümüne ekleyen SharePoint oluşturun. Sınıfı, yeni düğümü eklemek için arabirimini <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> uygulamaya almaktadır. bir düğüme alt düğüm ekleme gibi bir Sunucu Gezgini mevcut düğümün davranışını genişletmek istediğiniz her durumda bu arabirimi gerçekleştirin.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Web Bölümü Galerisi düğümünü Sunucu Gezgini

1. WebPartNodeExtension projesinde SiteNodeExtension kod dosyasını açın ve içine aşağıdaki kodu yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra projede bazı derleme hataları olur, ancak sonraki adımlarda kod eklerken bunlar gider.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>Web bölümünü temsil eden bir düğüm türü tanımlama
 Web Bölümünü temsil eden yeni bir düğüm türünü tanımlayan bir sınıf oluşturun. Visual Studio, Web Bölümü Galerisi düğümü altındaki alt düğümleri görüntülemek için bu **yeni düğüm türünü** kullanır. Her alt düğüm, sitedeki tek bir Web Bölümünü SharePoint temsil eder.

 Sınıfı, yeni düğüm türünü tanımlamak için arabirimini <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> uygulamaya almaktadır. içinde yeni bir düğüm türü tanımlamak istediğiniz her durumda bu arabirimi **Sunucu Gezgini.**

#### <a name="to-define-the-web-part-node-type"></a>Web bölümü düğüm türünü tanımlamak için

1. WebPartNodeExtension projesinde WebPartNodeTypeProvder kod dosyasını açın ve içine aşağıdaki kodu yapıştırın.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::

## <a name="define-the-web-part-data-class"></a>Web bölümü veri sınıfını tanımlama
 SharePoint sitesinde tek bir Web Bölümü hakkında veri içeren bir SharePoint tanımlayın. Bu kılavuzda daha sonra, sitenin her Web Bölümü SharePoint alan ve ardından bu sınıfın örneklerine veri ataan özel bir SharePoint komutu oluşturacağız.

#### <a name="to-define-the-web-part-data-class"></a>Web bölümü veri sınıfını tanımlamak için

1. WebPartNodeExtension projesinde WebPartNodeInfo kod dosyasını açın ve içine aşağıdaki kodu yapıştırın.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs" id="Snippet3":::

## <a name="define-the-ids-for-the-sharepoint-commands"></a>SharePoint komutları için kimlikleri tanımlama
 Özel dize komutlarını tanımlayan birkaç dize SharePoint tanımlayın. Bu komutları daha sonra bu kılavuzda uygulayacağız.

#### <a name="to-define-the-command-ids"></a>Komut kimliklerini tanımlamak için

1. WebPartNodeExtension projesinde WebPartCommandIds kod dosyasını açın ve içine aşağıdaki kodu yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb" id="Snippet4":::

## <a name="create-the-custom-sharepoint-commands"></a>Özel SharePoint oluşturma
 SharePoint sitenin sunucu nesnesiyle ilgili verileri almak için sunucu nesne modeline Web Bölümleri özel SharePoint oluşturun. Her komut, uygulanan bir <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> yöntemdir.

#### <a name="to-define-the-sharepoint-commands"></a>Komutlarını tanımlamak SharePoint için

1. WebPartCommands projesinde WebPartCommands kod dosyasını açın ve içine aşağıdaki kodu yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb" id="Snippet6":::

## <a name="checkpoint"></a>Checkpoint
 Kılavuzda bu noktada, **Web** Bölümü Galerisi düğümü ve SharePoint kodu artık projelerdedir. Her iki proje de hatasız derlenmiş olduğundan emin olmak için çözümü derle.

#### <a name="to-build-the-solution"></a>Çözümü derlemek için

1. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

    > [!WARNING]
    > Bu noktada, VSIX bildirim dosyasının Author değerine sahip olmadığını için WebPartNode projesi bir derleme hatasına sahip olabilir. Sonraki adımlarda bir değer eklerken bu hata gider.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için çözümünüzde VSIX projesini kullanarak bir VSIX paketi oluşturun. İlk olarak VSIX projesinde source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırabilirsiniz. Ardından, çözümü oluşturarak VSIX paketini oluşturun.

#### <a name="to-configure-the-vsix-package"></a>VSIX paketini yapılandırmak için

1. Bu **Çözüm Gezgini** WebPartNode projesinin altında **source.extension.vsixmanifest** dosyasını bildirim düzenleyicisinde açın.

     source.extension.vsixmanifest dosyası, tüm VSIX paketlerinin gerekli olduğu extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 Başvurusu.](/previous-versions/dd393700(v=vs.110))

2. Ürün Adı **kutusuna,** ürün için **Web Bölümü Galeri Düğümü Sunucu Gezgini.**

3. Yazar **kutusuna** Contoso **yazın.**

4. Açıklama **kutusuna,** SharePoint Connections düğümüne özel **bir Web Bölümü Galerisi düğümü ekler Sunucu Gezgini. Bu uzantı, sunucu nesne modeline SharePoint için özel bir komut satırı komutu kullanır.**

5. Düzenleyicinin **Varlıklar** sekmesini ve ardından Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

6. Tür **listesinde** **Microsoft.VisualStudio.MefComponent'ı seçin.**

    > [!NOTE]
    > Bu değer `MefComponent` extension.vsixmanifest dosyasındaki öğesine karşılık gelen bir değerdir. Bu öğe VSIX paketinde bir uzantı derlemenin adını belirtir. Daha fazla bilgi için bkz. [MEFComponent Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

8. Uygulama **Project** **WebPartNodeExtension'ı ve** ardından Tamam **düğmesini** seçin.

9. Bildirim düzenleyicisinde Yeni düğmesini **yeniden** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

10. Tür **kutusuna** **SharePoint. Commands.v4**.

    > [!NOTE]
    > Bu öğe, uygulama uzantısına eklemek istediğiniz özel bir Visual Studio belirtir. Daha fazla bilgi için [bkz. Varlık Öğesi (VSX Şeması)](/previous-versions/dd393737(v=vs.110)).

11. Kaynak **listesinde,** geçerli çözüm **listesi öğesinde A projesi'yi** seçin.

12. Uygulama **Project** **WebPartCommands'i ve** ardından Tamam **düğmesini** seçin.

13. Menü çubuğunda Derleme   >  **Çözümü'yü seçin** ve çözümün hatasız derlenmiş olduğundan emin olun.

14. WebPartNode projesinin derleme çıkış klasörünün artık WebPartNode.vsix dosyasını içerdiğini emin olun.

     Varsayılan olarak, derleme çıkış klasörü . Proje dosyanızı içeren klasörün altında \bin\Debug klasörü.

## <a name="test-the-extension"></a>Uzantıyı test etmek
 Artık web'de yeni Web Bölümü Galerisi **düğümünü test** etmeye **Sunucu Gezgini.** İlk olarak, uzantının deneysel bir örneğinde hata ayıklamaya Visual Studio. Ardından, deneysel **Web Bölümleri** yeni düğüm düğümünü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanın.

#### <a name="to-start-debugging-the-extension"></a>Uzantıda hata ayıklamaya başlamak için

1. Yönetici [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kimlik bilgileriyle yeniden başlatın ve ardından WebPartNode çözümünü açın.

2. WebPartNodeExtension projesinde SiteNodeExtension kod dosyasını açın ve ardından ve yöntemlerinde ilk kod satırına bir kesme `NodeChildrenRequested` `CreateWebPartNodes` noktası ekleyin.

3. Hata **ayıklamayı başlatmak için F5** anahtarını seçin.

     Visual Studio%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Bölümü Galeri Düğümü Uzantısı uzantısını Sunucu Gezgini\1.0 için yüker ve deneysel bir Visual Studio. Proje öğesini bu örnek içinde test Visual Studio.

#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için

1. deneysel örneğinde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] menü çubuğunda Görünüm ve  >  Sunucu Gezgini.

2. Test için kullanmak istediğiniz SharePoint site, SharePoint **Bağlantılar** düğümü altında görünmüyorsa aşağıdaki **adımları Sunucu Gezgini:**

    1. Bu **Sunucu Gezgini,** Bağlantılar için kısayol **menüsünü SharePoint ve** ardından Bağlantı Ekle'yi **seçin.**

    2. Bağlantı **Ekle SharePoint iletişim** kutusunda, bağlanmak istediğiniz SharePoint sitenin URL'sini girin ve ardından Tamam **düğmesini** seçin.

         Geliştirme bilgisayarınızda SharePoint siteyi belirtmek için **http://localhost** girin.

3. Site bağlantı düğümünü genişletin (bu, sitenizin URL'sini görüntüler) ve ardından bir alt site düğümünü (örneğin, **Takım Sitesi) genişletin.**

4. Diğer örneğinde yer alan kodun, yönteminde daha önce ayar seçtiğiniz kesme noktası üzerinde durarak projesinde hata ayıklamaya devam etmek için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] `NodeChildrenRequested` **F5'i** seçin.

5. Visual Studio adlı yeni bir düğümün üst düzey site  düğümü altında görüntülendiğinden emin olmak için Visual Studio Bölümü Galerisi **düğümünü** genişletin.

6. Visual Studio'nin diğer örneğinde yer alan kodun yönteminde daha önce ayar seçtiğiniz kesme noktası üzerinde durarak projesinde hata ayıklamaya devam etmek için `CreateWebPartNodes` **F5** tuşuna basın.

7. Deneysel Visual Studio örneğinde, bağlı sitedeki tüm Web Bölümleri'nin Sunucu Gezgini'daki **Web** Bölümü Galerisi düğümü **altında görüntü Sunucu Gezgini.**

8. Bu **Sunucu Gezgini,** dosyadan birinin kısayol menüsünü açın Web Bölümleri'yi **seçin.**

9. Hata ayıklaması yaptığınız örnekte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **Özellikler** penceresinde web bölümüyle ilgili ayrıntıların göründüğünü doğrulayın.

## <a name="uninstall-the-extension-from-visual-studio"></a>Uzantıyı Visual Studio kaldır
 Uzantıyı test etmeyi bitirdikten sonra uzantıyı Visual Studio ' den kaldırın.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , menü çubuğunda **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde, **Sunucu Gezgini Için Web Bölümü Galerisi düğüm uzantısı**' nı seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin ve ardından kaldırma işlemini gerçekleştirmek Için **Şimdi yeniden Başlat** düğmesini seçin.

4. her iki Visual Studio örneğini (deneysel örnek ve webpartnode çözümünün açık olduğu Visual Studio örneğini) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [izlenecek yol: Sunucu Gezgini uzantısında SharePoint istemci nesne modelini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için bir simge veya diğer görüntü &#40;görüntü Düzenleyicisi oluşturma&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)