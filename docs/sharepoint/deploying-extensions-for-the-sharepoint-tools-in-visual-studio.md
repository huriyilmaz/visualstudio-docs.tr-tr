---
title: Visual Studio SharePoint araçları için uzantılar dağıtılıyor | Microsoft Docs
description: Visual Studio SharePoint araçları için uzantıları dağıtın. vsıx paketleri oluşturmak için Visual Studio uzantısı (vsıx) projelerini kullanın.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 26c2b23be3708f3e55b5559f06d3ae869c49764e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060264"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio SharePoint araçları için uzantıları dağıtma

bir SharePoint araçları uzantısı dağıtmak için, uzantı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] derlemesini ve uzantıyla dağıtmak istediğiniz diğer dosyaları içeren bir uzantı (vsıx) paketi oluşturun. VSıX paketi, açık paketleme kuralları (OPC) standardını izleyen sıkıştırılmış bir dosyadır. VSıX paketleri *. vsix* uzantısına sahiptir.

Bir VSıX paketi oluşturduktan sonra, diğer kullanıcılar uzantınızı yüklemek için. VSIX dosyasını çalıştırabilir. Bir Kullanıcı uzantınızı yüklediğinde, tüm dosyalar%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions klasörüne yüklenir. uzantıyı dağıtmak için vsıx paketini [Visual Studio marketi](https://marketplace.visualstudio.com/) Web sitesine yükleyebilir veya paketi bir ağ paylaşımında ya da başka bir Web sitesinde barındırmak gibi başka yollarla da müşterilerinize dağıtabilirsiniz.

vsıx paketleri oluşturma ve bunları [Visual Studio market](https://marketplace.visualstudio.com/)'e dağıtma hakkında daha fazla bilgi için bkz. [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 Visual Studio **vsıx Project** şablonunu kullanarak bir vsıx paketi oluşturabilir veya el ile bir vsıx paketi oluşturabilirsiniz.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>VSIX paketleri oluşturmak için VSıX projelerini kullanın

SharePoint araçları uzantıları için vsıx paketleri oluşturmak üzere Visual Studio SDK tarafından sunulan **vsıx Project** şablonunu kullanabilirsiniz. VSıX projesi kullanmak, el ile bir VSıX paketi oluşturmak için çeşitli avantajlar sağlar:

- Visual Studio, projeyi derlediğinizde vsıx paketini otomatik olarak oluşturur. Dağıtım dosyalarını pakete ekleme ve paketin [Content_Types] .xml dosyasının oluşturulması gibi görevler sizin için yapılır.

- VSIX projesini uzantı projenizin derleme çıkışını ve proje şablonları ve öğe şablonları gibi diğer dosyaları VSıX paketine eklemek için yapılandırabilirsiniz.

vsıx projesi kullanma hakkında daha fazla bilgi için bkz. [vsıx Project şablonu](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Projelerinizi düzenleme

Varsayılan olarak, VSıX projeleri derleme değil yalnızca VSıX paketleri oluşturur. bu nedenle, genellikle bir vsıx projesinde SharePoint araçları uzantısı gerçekleştirmeyin. Genellikle en az iki projeyle çalışırsınız:

- Bir VSıX projesi.

- Uzantınızı uygulayan bir sınıf kitaplığı projesi.

Ayrıca, belirli uzantı türleri için ek projelerle da çalışabilirsiniz:

- uzantınızın kullandığı SharePoint komutlarını uygulayan bir sınıf kitaplığı projesi. Bu senaryoyu gösteren bir anlatım için bkz. [Izlenecek yol: Sunucu Gezgini Web bölümlerini görüntülemek Için genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- uzantınız yeni bir tür SharePoint proje öğesi tanımlıyorsa bir öğe şablonu veya proje şablonu oluşturan Project şablon projesi. Bu senaryoyu gösteren bir anlatım için bkz. [Izlenecek yol: bir öğe şablonuyla özel eylem projesi öğesi oluşturma, 1. Bölüm](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Uzantınız bir şablon içeriyorsa, bir öğe şablonu veya proje şablonu için özel sihirbaz uygulayan bir sınıf kitaplığı projesi. Bu senaryoyu gösteren bir anlatım için bkz. [Izlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

tüm projeleri aynı Visual Studio çözümüne eklerseniz, sınıf kitaplığı projelerinin yapı çıkışını dahil etmek için vsıx projesindeki kaynak. extension. valtmanifest dosyasını değiştirebilirsiniz.

### <a name="edit-the-vsix-manifest"></a>VSıX bildirimini düzenleme

Uzantınızın içine dahil etmek istediğiniz tüm öğelerin girişlerini dahil etmek için VSıX projesindeki kaynak. Extension. valtmanifest dosyasını düzenlemeniz gerekir. Kaynak. Extension. valtmanifest dosyasını kısayol menüsünden açtığınızda, dosya dosyadaki XML 'yi düzenlemede kullanılacak bir kullanıcı arabirimi sağlayan bir tasarımcıda görüntülenir. Daha fazla bilgi için bkz. [VSIX bildirim Tasarımcısı](../extensibility/vsix-manifest-designer.md).

Aşağıdaki öğeler için kaynak. Extension. valtmanifest dosyasına girdi eklemeniz gerekir:

- Uzantı derlemesi.

- uzantınızın kullandığı SharePoint komutlarını uygulayan derleme.

- Uzantılarınızla ilişkili tüm proje şablonları veya öğe şablonları.

- Uzantınızın ilişkilendirildiği bir şablon için özel bir sihirbaz.

Aşağıdaki yordamlar, bu öğelerin her biri için. valtmanifest dosyasına girişlerin nasıl ekleneceğini açıklamaktadır.

#### <a name="to-include-the-extension-assembly"></a>Uzantı derlemesini dahil etmek için

1. VSıX projesinde, kaynak. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç**' ı seçin.

     Dosya tasarımcıda açılır

2. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

4. **Kaynak** listesinde aşağıdaki adımlardan birini gerçekleştirin:

    - Uzantı derlemesi, VSıX projesiyle aynı çözümde bulunan bir projeden derlenmiş ise, **Geçerli çözümde bir proje** seçin. **Project** listesinde, projenin adını seçin.

    - Uzantı derlemesi projenize bir dosya olarak dahil edilip dosya **sistemi üzerinde dosya**' yı seçin. **Yol** listesinde, uzantı derleme dosyasının tüm yolunu girin veya derleme dosyasını bulmak ve seçmek için **Araştır** düğmesini kullanın.

5. **Tamam** düğmesini seçin.

#### <a name="to-include-a-sharepoint-command-assembly"></a>SharePoint bir komut derlemesi eklemek için

1. VSıX projesinde, Source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç** düğmesini seçin.

     Dosya tasarımcıda açılır.

2. Düzenleyicinin **varlıklar** bölümünde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3. **Tür** kutusuna **SharePoint girin. Commands. v4**.

4. **Kaynak** listesinde aşağıdaki adımlardan birini gerçekleştirin:

    - Komut derlemesi, VSıX projesiyle aynı çözümde bulunan bir projeden derlenmiş ise, **Geçerli çözümde bir proje** seçin. **Project** listesinde, projenin adını seçin.

    - Komut derlemesi projenize bir dosya olarak dahil edilip dosya **sistemi üzerinde dosya**' yı seçin. **Yol** listesinde, uzantı derleme dosyasının tüm yolunu girin veya derleme dosyasını bulmak ve seçmek için **Araştır** düğmesini kullanın.

5. **Tamam** düğmesini seçin.

#### <a name="to-include-a-template-that-you-create"></a>Oluşturduğunuz bir şablonu eklemek için

1. VSıX projesinde, Source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç** düğmesini seçin.

     Dosya tasarımcıda açılır.

2. Düzenleyicinin **varlıklar** bölümünde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3. **Tür** listesinde **Microsoft. VisualStudio. ProjectTemplate** veya **Microsoft. VisualStudio. ItemTemplate**' i seçin.

4. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

5. **Project** listesinde, projenin adını seçin ve **tamam** düğmesini seçin.

6. **Çözüm Gezgini**' de, Project şablonunuz veya öğe şablonu projeniz için kısayol menüsünü açın ve ardından **Project kaldır**' ı seçin.

7. Proje düğümü için kısayol menüsünü yeniden açın ve ardından _yourtemplateprojectname_**. csproj** **Düzenle**' yi seçin veya _yourtemplateprojectname_**. vbproj**' i **düzenleyin**.

8. `VSTemplate`Proje dosyasında aşağıdaki öğeyi bulun.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Bu öğeyi aşağıdaki XML ile değiştirin.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Öğesi, proje oluşturduğunuzda proje şablonunun oluşturulduğu yolda ek klasörleri belirtir. burada belirtilen klasörler, öğe şablonunun yalnızca müşteriler **yeni Project ekle** iletişim kutusunu açtıklarında kullanılabilir olacağını ve **SharePoint** düğümünü genişlettikten sonra **2010** düğümünü seçmesini sağlamaktır.

10. Dosyayı kaydedin ve kapatın.

11. **Çözüm Gezgini**' de, Project şablonu veya öğe şablonu projesi için kısayol menüsünü açın ve ardından **Project yeniden yükle**' yi seçin.

#### <a name="to-include-a-template-that-you-create-manually"></a>El ile oluşturduğunuz bir şablonu dahil etmek için

1. VSıX projesinde, şablonu içerecek şekilde projeye yeni bir klasör ekleyin.

2. Bu yeni klasör altında aşağıdaki alt klasörleri oluşturun ve şablon (.zip) dosyasını *yerel ayar kimliği* klasörüne ekleyin.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *Yerel Ayar Kimliği*

     *YourTemplateName*.zip

     Örneğin, Ingilizce (Birleşik Devletler) yerel ayarını destekleyen ContosoCustomAction.zip adlı bir öğe şablonunuz varsa, tam yol *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* olabilir.

3. **Çözüm Gezgini**, şablon dosyasını (*yourtemplatename*.zip) seçin.

4. **Özellikler** penceresinde, **derleme eylemi** özelliğini **içerik** olarak ayarlayın.

5. Source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç**' ı seçin.

     Dosya tasarımcıda açılır.

6. Düzenleyicinin **varlıklar** bölümünde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

7. **Tür** listesinde, **Microsoft. VisualStudio. ItemTemplate** veya **Microsoft. VisualStudio. ProjectTemplate**' i seçin.

8. **Kaynak** listesinde **dosya sistemi üzerinde dosya**' yı seçin.

9. Yol **alanına** derlemenin tam yolunu girin *(örneğin,ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* veya Gözat  düğmesini kullanarak derlemeyi bulup seçin ve ardından **Tamam düğmesini** seçin.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Proje şablonuna veya öğe şablonuna sihirbaz eklemek için

1. VSIX projesinde source.extension.vsixmanifest dosyasının kısayol menüsünü açın ve aç'ı **seçin.**

     Dosya tasarımcıda açılır.

2. Düzenleyicinin **Varlıklar** bölümünde Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu açılır.

3. Tür listesinde **Microsoft.VisualStudio.Assembly'i seçin.** 

4. Kaynak **listesinde** aşağıdaki adımlardan birini gerçekleştirin:

    - Sihirbaz derlemesi VSIX projesiyle aynı çözümde yer alan bir projeden oluşturulursa, Geçerli çözümde **bir proje'yi seçin.** Project **listesinde** projenin adını seçin.

    - Sihirbaz derlemesi projenize bir dosya olarak dahil edildiyse dosya sisteminde **dosya'ya tıklayın.** Yol **alanına** derleme dosyasının tam yolunu girin veya Gözat düğmesini kullanarak **derlemeyi** bulup seçin.

5. Tamam **düğmesini** seçin.

### <a name="related-walkthroughs"></a>İlgili kılavuzlar

Aşağıdaki tabloda, bir VSIX projesinin farklı türlerde araç uzantıları dağıtmak için nasıl SharePoint izlenecek yollar listelenecektir.

|Uzantı türü|İlgili kılavuzlar|
|--------------------|--------------------------|
|Yalnızca uzantı derlemesi içeren bir uzantı|[Adım adım kılavuz: SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Adım adım kılavuz: SharePoint Project oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Adım adım kılavuz: SharePoint uzantısında istemci nesne modeline Sunucu Gezgini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|SharePoint içeren bir uzantı|[Adım adım kılavuz: Proje oluşturmak için özel SharePoint oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Adım adım kılavuz: Sunucu Gezgini bölümlerini görüntülemek için uygulamanın süresini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Adım adım kılavuz: Proje şablonuyla site sütunu proje öğesi oluşturma, Bölüm 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Visual Studio şablonu içeren bir uzantı|[Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Adım adım kılavuz: Proje şablonuyla Site sütunu proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Şablon sihirbazı içeren bir uzantı|[Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Adım adım kılavuz: Proje şablonuyla Site sütunu proje öğesi oluşturma, Bölüm 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>VSIX paketlerini el ile oluşturma

SharePoint araçları uzantınız için VSIX paketini el ile oluşturmak için aşağıdaki adımları gerçekleştirin:

1. Extension.vsixmanifest dosyasını ve [Content_Types].xml dosyasını yeni bir klasörde oluşturun. Daha fazla bilgi için [bkz. VSIX Paketinin Anatomisi.](../extensibility/anatomy-of-a-vsix-package.md)

2. Windows Gezgini'nde, iki XML dosyasını içeren klasöre sağ tıklayın, Gönder'e tıklayın ve ardından Sıkıştırılmış (sıkıştırılmış) Klasör'e tıklayın. Sonuçta elde edilen .zip Dosyaadı.vsix olarak yeniden adlandırır; burada Filename, paketinizi yüken yeniden dağıtılabilir dosyanın adıdır.

3. Uzantı derlemenizi VSIX paketine ekleyin. Uzantınız bir SharePoint komutu içerirse, vsIX paketine SharePoint derlemeyi de ekleyin.

4. extension.vsixmanifest dosyasını değiştirme:

    - öğesinin altına bir öğesi ekleyin ve ardından yeni öğenin değerini VSIX paketinde uzantınızı uygulayan derlemenin göreli `Microsoft.VisualStudio.MefComponent` `Assets` yoluna ayarlayın. Daha fazla bilgi için bkz. [MEFComponent Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Uzantınız, SharePoint için sunucu nesne modeline çağrı SharePoint bir komut SharePoint `Microsoft.VisualStudio.Assembly` öğesinin altına bir öğesi `Assets` ekleyin. Yeni öğenin değerini VSIX paketinde SharePoint uygulayan derlemenin göreli yoluna ayarlayın. Daha fazla bilgi için [bkz. Varlık Öğesi (VSX Şeması)](/previous-versions/dd393737(v=vs.110)).

    - Uzantınız bir proje şablonu veya öğe şablonu içerirse öğesinin `ProjectTemplate` altına bir veya öğesi `ItemTemplate` `Assets` ekleyin. Yeni öğenin değerini VSIX paketinde şablonu içeren klasörün göreli yoluna ayarlayın. Daha fazla bilgi için bkz. [ProjectTemplate Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) ve [ItemTemplate Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Uzantınız bir proje şablonu veya öğe şablonu için özel bir sihirbaz içerirse öğesinin `Assembly` altına bir öğe `Assets` ekleyin. Yeni öğenin değerini VSIX paketinde derlemenin göreli yoluna ayarlayın ve ardından özniteliğini tam derleme adına (sürüm, kültür ve ortak anahtar belirteci dahil) `AssemblyName` ayarlayın. Daha fazla bilgi için [bkz. Dependency Öğesi (VSX Şeması)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Örnek

Aşağıdaki örnek, bir SharePoint tools uzantısı için extension.vsixmanifest dosyasının içeriğini gösterir. Uzantı, Contoso.ProjectExtension.dll adlı bir derlemede uygulanır. Uzantı, SharePoint adlı bir komut derlemesi Contoso.ExtensionCommands.dll VSIX paketinde **ItemTemplates** adlı bir klasör altında bir öğe şablonu içerir. Bu örnekte, her iki derlemenin de VSIX paketinde extension.vsixmanifest dosyasıyla aynı klasörde olduğu varsayılacaktır.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [Kümedeki SharePoint düğümünü Sunucu Gezgini](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Nesne modellerini SharePoint çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Visual Studio'de SharePoint için uzantılarda hata Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)