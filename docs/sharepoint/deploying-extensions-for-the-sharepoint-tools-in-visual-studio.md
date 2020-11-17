---
title: Visual Studio 'da SharePoint araçları için uzantıları dağıtma | Microsoft Docs
description: Visual Studio 'da SharePoint araçları için uzantıları dağıtın. VSıX paketleri oluşturmak için Visual Studio uzantısı (VSıX) projelerini kullanın.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c8b05b5cb74a28157436f95f01992515c716e6a
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672684"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio 'da SharePoint araçları için uzantıları dağıtma

SharePoint araçları uzantısını dağıtmak için uzantı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] derlemesini ve uzantısıyla dağıtmak istediğiniz diğer dosyaları içeren bir uzantı (VSIX) paketi oluşturun. VSıX paketi, açık paketleme kuralları (OPC) standardını izleyen sıkıştırılmış bir dosyadır. VSıX paketleri *. vsix* uzantısına sahiptir.

Bir VSıX paketi oluşturduktan sonra, diğer kullanıcılar uzantınızı yüklemek için. VSIX dosyasını çalıştırabilir. Bir Kullanıcı uzantınızı yüklediğinde, tüm dosyalar%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions klasörüne yüklenir. Uzantıyı dağıtmak için VSıX paketini [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesine yükleyebilir veya paketi bir ağ paylaşımında ya da başka bir Web sitesinde barındırmak gibi başka bir yöntemle dağıtabilirsiniz.

VSıX paketleri oluşturma ve bunları [Visual Studio Market](https://marketplace.visualstudio.com/)dağıtma hakkında daha fazla bilgi için bkz. [Visual Studio uzantılarını gönderme](../extensibility/shipping-visual-studio-extensions.md).

 Visual Studio 'da **VSIX proje** şablonunu kullanarak bir VSIX paketi oluşturabilir veya el Ile bir VSIX paketi oluşturabilirsiniz.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>VSIX paketleri oluşturmak için VSıX projelerini kullanın

SharePoint Araçları uzantıları için VSıX paketleri oluşturmak üzere Visual Studio SDK 'Sı tarafından sunulan **VSIX proje** şablonunu kullanabilirsiniz. VSıX projesi kullanmak, el ile bir VSıX paketi oluşturmak için çeşitli avantajlar sağlar:

- Projeyi derlediğinizde Visual Studio VSıX paketini otomatik olarak oluşturur. Dağıtım dosyalarını pakete ekleme ve paketin [Content_Types]. xml dosyasını oluşturma gibi görevler sizin için yapılır.

- VSIX projesini uzantı projenizin derleme çıkışını ve proje şablonları ve öğe şablonları gibi diğer dosyaları VSıX paketine eklemek için yapılandırabilirsiniz.

VSıX projesi kullanma hakkında daha fazla bilgi için bkz. [VSIX proje şablonu](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Projelerinizi düzenleme

Varsayılan olarak, VSıX projeleri derleme değil yalnızca VSıX paketleri oluşturur. Bu nedenle, genellikle bir VSıX projesinde SharePoint araçları uzantısı gerçekleştirmeyin. Genellikle en az iki projeyle çalışırsınız:

- Bir VSıX projesi.

- Uzantınızı uygulayan bir sınıf kitaplığı projesi.

Ayrıca, belirli uzantı türleri için ek projelerle da çalışabilirsiniz:

- Uzantınız tarafından kullanılan herhangi bir SharePoint komutunu uygulayan bir sınıf kitaplığı projesi. Bu senaryoyu gösteren bir anlatım için bkz. [Izlenecek yol: Sunucu Gezgini Web bölümlerini görüntülemek Için genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Uzantınız yeni bir SharePoint proje öğesi türü tanımlıyorsa bir öğe şablonu veya proje şablonu oluşturan bir öğe şablonu veya proje şablonu projesi. Bu senaryoyu gösteren bir anlatım için bkz. [Izlenecek yol: bir öğe şablonuyla özel eylem projesi öğesi oluşturma, 1. Bölüm](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Uzantınız bir şablon içeriyorsa, bir öğe şablonu veya proje şablonu için özel sihirbaz uygulayan bir sınıf kitaplığı projesi. Bu senaryoyu gösteren bir anlatım için bkz. [Izlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Tüm projeleri aynı Visual Studio çözümüne eklerseniz, sınıf kitaplığı projelerinin yapı çıkışını dahil etmek için VSıX projesindeki kaynak. Extension. valtmanifest dosyasını değiştirebilirsiniz.

### <a name="edit-the-vsix-manifest"></a>VSıX bildirimini düzenleme

Uzantınızın içine dahil etmek istediğiniz tüm öğelerin girişlerini dahil etmek için VSıX projesindeki kaynak. Extension. valtmanifest dosyasını düzenlemeniz gerekir. Kaynak. Extension. valtmanifest dosyasını kısayol menüsünden açtığınızda, dosya dosyadaki XML 'yi düzenlemede kullanılacak bir kullanıcı arabirimi sağlayan bir tasarımcıda görüntülenir. Daha fazla bilgi için bkz. [VSIX bildirim Tasarımcısı](../extensibility/vsix-manifest-designer.md).

Aşağıdaki öğeler için kaynak. Extension. valtmanifest dosyasına girdi eklemeniz gerekir:

- Uzantı derlemesi.

- Uzantınızın kullandığı herhangi bir SharePoint komutunu uygulayan derleme.

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

    - Uzantı derlemesi, VSıX projesiyle aynı çözümde bulunan bir projeden derlenmiş ise, **Geçerli çözümde bir proje** seçin. **Proje** listesinde projenin adını seçin.

    - Uzantı derlemesi projenize bir dosya olarak dahil edilip dosya **sistemi üzerinde dosya**' yı seçin. **Yol** listesinde, uzantı derleme dosyasının tüm yolunu girin veya derleme dosyasını bulmak ve seçmek için **Araştır** düğmesini kullanın.

5. **Tamam** düğmesini seçin.

#### <a name="to-include-a-sharepoint-command-assembly"></a>Bir SharePoint komut derlemesi eklemek için

1. VSıX projesinde, Source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç** düğmesini seçin.

     Dosya tasarımcıda açılır.

2. Düzenleyicinin **varlıklar** bölümünde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3. **Tür** kutusuna **SharePoint. Commands. v4** yazın.

4. **Kaynak** listesinde aşağıdaki adımlardan birini gerçekleştirin:

    - Komut derlemesi, VSıX projesiyle aynı çözümde bulunan bir projeden derlenmiş ise, **Geçerli çözümde bir proje** seçin. **Proje** listesinde projenin adını seçin.

    - Komut derlemesi projenize bir dosya olarak dahil edilip dosya **sistemi üzerinde dosya**' yı seçin. **Yol** listesinde, uzantı derleme dosyasının tüm yolunu girin veya derleme dosyasını bulmak ve seçmek için **Araştır** düğmesini kullanın.

5. **Tamam** düğmesini seçin.

#### <a name="to-include-a-template-that-you-create"></a>Oluşturduğunuz bir şablonu eklemek için

1. VSıX projesinde, Source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç** düğmesini seçin.

     Dosya tasarımcıda açılır.

2. Düzenleyicinin **varlıklar** bölümünde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3. **Tür** listesinde **Microsoft. VisualStudio. ProjectTemplate** veya **Microsoft. VisualStudio. ItemTemplate**' i seçin.

4. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

5. **Proje** listesinde projenin adını seçin ve **Tamam** düğmesini seçin.

6. **Çözüm Gezgini**' de, proje şablonunuz veya öğe şablonu projeniz için kısayol menüsünü açın ve ardından **Projeyi Kaldır**' ı seçin.

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

     `OutputSubPath`Öğesi, proje oluşturduğunuzda proje şablonunun oluşturulduğu yolda ek klasörleri belirtir. Burada belirtilen klasörler, öğe şablonunun yalnızca müşteriler **Yeni Proje Ekle** iletişim kutusunu açtıklarında kullanılabilir olacağını ve **SharePoint** düğümünü genişlettikten sonra **2010** düğümünü seçmesini de sağlamaktır.

10. Dosyayı kaydedin ve kapatın.

11. **Çözüm Gezgini**' de proje şablonu veya öğe şablonu projesi için kısayol menüsünü açın ve ardından **projeyi yeniden yükle**' yi seçin.

#### <a name="to-include-a-template-that-you-create-manually"></a>El ile oluşturduğunuz bir şablonu dahil etmek için

1. VSıX projesinde, şablonu içerecek şekilde projeye yeni bir klasör ekleyin.

2. Bu yeni klasör altında, aşağıdaki alt klasörleri oluşturun ve ardından şablon (. zip) dosyasını *yerel ayar kimliği* klasörüne ekleyin.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *Yerel Ayar Kimliği*

     *YourTemplateName*. zip

     Örneğin, Ingilizce (Birleşik Devletler) yerel ayarını destekleyen ContosoCustomAction.zip adlı bir öğe şablonunuz varsa, tam yol *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* olabilir.

3. **Çözüm Gezgini**, şablon dosyasını (*YourTemplateName*. zip) seçin.

4. **Özellikler** penceresinde, **derleme eylemi** özelliğini **içerik** olarak ayarlayın.

5. Source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç**' ı seçin.

     Dosya tasarımcıda açılır.

6. Düzenleyicinin **varlıklar** bölümünde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

7. **Tür** listesinde, **Microsoft. VisualStudio. ItemTemplate** veya **Microsoft. VisualStudio. ProjectTemplate**' i seçin.

8. **Kaynak** listesinde **dosya sistemi üzerinde dosya**' yı seçin.

9. **Yol** alanına, derlemeye yönelik yolun tamamını girin (örneğin, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* veya derlemeyi bulmak ve seçmek için **Araştır** düğmesini kullanın ve ardından **Tamam** düğmesini seçin.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Proje şablonuna veya öğe şablonuna yönelik bir sihirbaz eklemek için

1. VSıX projesinde, kaynak. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç**' ı seçin.

     Dosya tasarımcıda açılır.

2. Düzenleyicinin **varlıklar** bölümünde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3. **Tür** listesinde **Microsoft. VisualStudio. Assembly** öğesini seçin.

4. **Kaynak** listesinde aşağıdaki adımlardan birini gerçekleştirin:

    - Sihirbaz derlemesi, VSıX projesiyle aynı çözümde bulunan bir projeden derlenmiş ise, **Geçerli çözümde bir proje** seçin. **Proje** listesinde projenin adını seçin.

    - Sihirbaz derlemesi projenize bir dosya olarak dahil edilip dosya **sistemi üzerinde dosya**' yı seçin. **Yol** alanına, derleme dosyasının tüm yolunu girin veya derlemeyi bulmak ve seçmek için **Araştır** düğmesini kullanın.

5. **Tamam** düğmesini seçin.

### <a name="related-walkthroughs"></a>İlgili izlenecek yollar

Aşağıdaki tabloda, farklı türlerde SharePoint Araçları uzantıları dağıtmak için VSıX projesinin nasıl kullanılacağını gösteren izlenecek yollar listelenmiştir.

|Uzantı türü|İlgili izlenecek yollar|
|--------------------|--------------------------|
|Yalnızca uzantı derlemesini içeren bir uzantı|[İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [İzlenecek yol: SharePoint Proje uzantısı oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [İzlenecek yol: Sunucu Gezgini uzantısında SharePoint istemci nesne modelini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|SharePoint komutlarını içeren bir uzantı|[İzlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Visual Studio şablonu içeren bir uzantı|[İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [İzlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Şablon Sihirbazı içeren bir uzantı|[İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>VSıX paketlerini el ile oluşturma

SharePoint araçları uzantınızın VSıX paketini el ile oluşturmak isterseniz, aşağıdaki adımları uygulayın:

1. Uzantısı. valtmanifest dosyasını ve [Content_Types]. xml dosyasını yeni bir klasörde oluşturun. Daha fazla bilgi için bkz. [BIR VSIX paketinin Anatomı](../extensibility/anatomy-of-a-vsix-package.md).

2. Windows Gezgini 'nde, iki XML dosyasını içeren klasöre sağ tıklayın, Gönder ' e tıklayın ve ardından sıkıştırılmış (daraltılmış) klasör ' e tıklayın. Elde edilen. zip dosyasını filename. vsix olarak yeniden adlandırın; burada filename, paketinizi yükleyen yeniden dağıtılabilir dosyanın adıdır.

3. Uzantı derlemenizi VSıX paketine ekleyin. Uzantınız bir SharePoint komutu içeriyorsa, SharePoint komutunu uygulayan derlemeyi VSıX paketine da ekleyin.

4. Extension. valtmanifest dosyasını değiştirin:

    - `Microsoft.VisualStudio.MefComponent`Öğesinin altına bir öğesi ekleyin `Assets` ve ardından New ÖĞESININ değerini VSIX paketinde uzantınızı uygulayan derlemenin göreli yolu olarak ayarlayın. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Uzantınız SharePoint için sunucu nesne modeline çağıran bir SharePoint komutu içeriyorsa, `Microsoft.VisualStudio.Assembly` öğe altına bir öğe ekleyin `Assets` . Yeni öğenin değerini VSıX paketindeki SharePoint komutunu uygulayan derlemenin göreli yoluna ayarlayın. Daha fazla bilgi için bkz. [varlık öğesi (VSX şeması)](/previous-versions/dd393737(v=vs.110)).

    - Uzantınız bir proje şablonu veya öğe şablonu içeriyorsa, `ProjectTemplate` öğe altına bir veya `ItemTemplate` öğesi ekleyin `Assets` . Yeni öğenin değerini VSıX paketindeki şablonu içeren klasörün göreli yoluna ayarlayın. Daha fazla bilgi için bkz. [ProjectTemplate öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) ve [ItemTemplate öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Uzantınız bir proje şablonu veya öğe şablonu için özel bir sihirbaz içeriyorsa, `Assembly` öğe altına bir öğe ekleyin `Assets` . Yeni öğenin değerini VSıX paketindeki derlemenin göreli yoluna ayarlayın ve ardından `AssemblyName` özniteliği tam derleme adı (sürüm, kültür ve ortak anahtar belirteci dahil) olarak ayarlayın. Daha fazla bilgi için bkz. [dependency öğesi (VSX şeması)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Örnek

Aşağıdaki örnek, bir SharePoint araçları uzantısı için bir Extension. valtmanifest dosyasının içeriğini gösterir. Uzantı, Contoso.ProjectExtension.dll adlı bir derlemede uygulanır. Uzantı Contoso.ExtensionCommands.dll adlı bir SharePoint komut derlemesini ve VSıX paketindeki **ItemTemplates** adlı bir klasör altında bir öğe şablonu içerir. Bu örnek, her iki derlemenin de VSıX paketindeki Extension. valtmanifest dosyası ile aynı klasörde olduğunu varsayar.

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
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Visual Studio 'da SharePoint araçları için hata ayıklama uzantıları](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)