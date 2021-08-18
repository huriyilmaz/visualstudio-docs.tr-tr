---
title: Öğe şablonu, Bölüm 1 ile özel eylem proje öğesi oluşturma
titleSuffix: ''
description: bir öğe şablonu kullanarak, bir SharePoint sitesinde özel bir eylem oluşturmak için bir SharePoint projesine eklenebilen bir proje öğesi oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 79894d13457096ab15e7990fc10b9bcb0e8d7f22
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130786"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma
  kendi proje öğesi türlerinizi oluşturarak Visual Studio SharePoint proje sistemini genişletebilirsiniz. bu kılavuzda, bir SharePoint sitesinde özel bir eylem oluşturmak için bir SharePoint projesine eklenebilen bir proje öğesi oluşturacaksınız. özel eylem, SharePoint sitesinin **site eylemleri** menüsüne bir menü öğesi ekler.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- özel bir eylem için yeni bir SharePoint proje öğesi türünü tanımlayan Visual Studio uzantısı oluşturma. Yeni proje öğesi türü çeşitli özel özellikler uygular:

  - Visual Studio bir özel eylem için tasarımcı görüntüleme gibi proje öğesiyle ilgili ek görevler için başlangıç noktası görevi gören bir kısayol menüsü.

  - Bir geliştirici proje öğesinin belirli özelliklerini ve onu içeren projeyi değiştirdiğinde çalıştırılan kod.

  - **Çözüm Gezgini** içindeki proje öğesinin yanında görünen özel bir simge.

- proje öğesi için Visual Studio öğe şablonu oluşturuluyor.

- proje öğesi şablonunu ve uzantı derlemesini dağıtmak için bir Visual Studio uzantısı (vsıx) paketi oluşturma.

- Proje öğesini hata ayıklama ve test etme.

  Bu tek başına bir yönergedir. Bu yönergeyi tamamladıktan sonra, öğe şablonuna bir sihirbaz ekleyerek Proje öğesini geliştirebilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> Bir iş akışı için nasıl özel etkinlik oluşturulacağını gösteren [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 'dan bir örnek indirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen Microsoft Windows sürümleri, SharePoint ve Visual Studio.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. bu izlenecek yol SDK 'daki **vsıx Project** şablonunu, proje öğesini dağıtmak için bir vsıx paketi oluşturmak için kullanır. daha fazla bilgi için bkz. [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- SharePoint özel eylemler. Daha fazla bilgi için bkz. [özel eylem](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Visual Studio öğe şablonları. daha fazla bilgi için bkz. [Project ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için üç proje oluşturmanız gerekir:

- Bir VSıX projesi. bu proje, SharePoint projesi öğesini dağıtmak için vsıx paketini oluşturur.

- Bir öğe şablonu projesi. bu proje, bir SharePoint projesine SharePoint proje öğesi eklemek için kullanılabilecek bir öğe şablonu oluşturur.

- Bir sınıf kitaplığı projesi. bu proje, SharePoint proje öğesinin davranışını tanımlayan bir Visual Studio uzantısı uygular.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

3. **yeni Project** iletişim kutusunun en üstündeki listede **.NET Framework 4,5** ' nin seçildiğinden emin olun.

4. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > **genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'yı yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

5. **vsıx Project** şablonunu seçin.

6. **Ad** kutusuna **CustomActionProjectItem** girin ve sonra **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**CustomActionProjectItem** projesini **Çözüm Gezgini** ekler.

#### <a name="to-create-the-item-template-project"></a>Öğe şablonu projesi oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

2. **yeni Project** iletişim kutusunun en üstündeki listede **.NET Framework 4,5** ' nin seçildiğinden emin olun.

3. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

4. proje şablonları listesinde **C# öğe** şablonunu veya **Visual Basic öğesi** şablonu şablonunu seçin.

5. **Ad** kutusuna **ItemTemplate** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ItemTemplate** projesini çözüme ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

2. **yeni Project** iletişim kutusunun en üstündeki listede **.NET Framework 4,5** ' nin seçildiğinden emin olun.

3. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin, **Windows** düğümünü seçin ve ardından **sınıf kitaplığı** proje şablonu ' nu seçin.

4. **Ad** kutusuna **ProjectItemDefinition** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ProjectItemDefinition** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 SharePoint proje öğesi türünü tanımlamak için kod yazmadan önce, uzantı projesine kod dosyaları ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. **Çözüm Gezgini**' de **ProjectItemDefinition** projesi için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

2. Proje öğeleri listesinde **kod dosyası**' nı seçin.

3. **Ad** kutusuna uygun **dosya adı uzantısına sahip adını** girin ve sonra **Ekle** düğmesini seçin.

4. **Çözüm Gezgini**' de **ProjectItemDefinition** projesi için kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

5. **Başvuru Yöneticisi-ProjectItemDefinition** Iletişim kutusunda **derlemeler** düğümünü seçin ve ardından **Framework** düğümünü seçin.

6. Aşağıdaki derlemelerin her birinin yanındaki onay kutusunu işaretleyin:

    - System. ComponentModel. Composition

    - Sistemin. Windows. Formlarındaki

7. **Uzantılar** düğümünü seçin, Microsoft. VisualStudio. SharePoint derlemesinin yanındaki onay kutusunu Işaretleyin ve **Tamam** düğmesini seçin.

## <a name="define-the-new-sharepoint-project-item-type"></a>yeni SharePoint proje öğesi türünü tanımlayın
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>Yeni proje öğesi türünün davranışını tanımlamak için arabirimini uygulayan bir sınıf oluşturun. Yeni proje öğesi türünü tanımlamak istediğinizde bu arabirimi uygulayın.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>yeni SharePoint proje öğesi türünü tanımlamak için

1. ProjectItemDefinition projesinde, CustomAction kod dosyasını açın.

2. Bu dosyadaki kodu aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb" id="Snippet1":::

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Çözüm Gezgini içinde proje öğesi için bir simge oluşturun
 özel bir SharePoint proje öğesi oluşturduğunuzda, bir görüntüyü (simge veya bit eşlem) proje öğesiyle ilişkilendirebilirsiniz. Bu görüntü, **Çözüm Gezgini** içindeki proje öğesinin yanında görünür.

 Aşağıdaki yordamda, proje öğesi için bir simge oluşturacak ve simgeyi uzantı derlemesine katıştıraöğreneceksiniz. Bu simgeye, <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> `CustomActionProjectItemTypeProvider` daha önce oluşturduğunuz sınıf tarafından başvurulur.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Proje öğesi için özel bir simge oluşturmak için

1. **Çözüm Gezgini**' de **ProjectItemDefinition** projesi için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe...**' yi seçin.

2. Proje öğeleri listesinde, **simge dosyası** öğesini seçin.

    > [!NOTE]
    > Visual Basic projelerinde, **simge dosya** öğesini göstermek için **genel** düğümünü seçmeniz gerekir.

3. **Ad** kutusuna **CustomAction_SolutionExplorer. ico** girin ve sonra **Ekle** düğmesini seçin.

     Yeni simge **görüntü düzenleyicisinde** açılır.

4. Simge dosyasının 16x16 sürümünü, tanıyabileceğiniz bir tasarıma sahip olacak şekilde düzenleyin ve ardından simge dosyasını kaydedin.

5. **Çözüm Gezgini**' de **CustomAction_SolutionExplorer. ico**' ı seçin.

6. **Özellikler** penceresinde, **Yapı eylemi** özelliğinin yanındaki oku seçin.

7. Görüntülenen listede, **gömülü kaynak**' ı seçin.

## <a name="checkpoint"></a>Checkpoint
 Bu noktada, proje öğesi için tüm kod artık projede bulunur. Hata olmadan derlendiğini doğrulamak için projeyi derleyin.

#### <a name="to-build-your-project"></a>Projenizi derlemek için

1. **ProjectItemDefinition** projesi için kısayol menüsünü açın ve **Oluştur**' a tıklayın.

## <a name="create-a-visual-studio-item-template"></a>Visual Studio öğesi şablonu oluşturma
 Diğer geliştiricilerin Proje öğesini kullanmasını sağlamak için bir proje şablonu veya öğe şablonu oluşturmanız gerekir. geliştiriciler yeni bir proje oluşturarak veya mevcut bir projeye bir öğe ekleyerek proje öğesinin bir örneğini oluşturmak için Visual Studio bu şablonları kullanır. Bu izlenecek yol için, Proje öğesini yapılandırmak üzere ItemTemplate projesini kullanın.

#### <a name="to-create-the-item-template"></a>Öğe şablonu oluşturmak için

1. ItemTemplate projesinden Class1 kod dosyasını silin.

2. ItemTemplate projesinde *ItemTemplate. vstemplate* dosyasını açın.

3. Dosyanın içeriğini aşağıdaki XML ile değiştirin ve sonra dosyayı kaydedip kapatın.

    > [!NOTE]
    > Aşağıdaki XML, bir Visual C# öğe şablonu içindir. Visual Basic bir öğe şablonu oluşturuyorsanız, `ProjectType` öğesinin değerini ile değiştirin `VisualBasic` .

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     Bu dosya, öğe şablonunun içeriğini ve davranışını tanımlar. bu dosyanın içeriği hakkında daha fazla bilgi için bkz. [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md).

4. **Çözüm Gezgini**, **ItemTemplate** projesinin kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

5. **Yeni öğe Ekle** Iletişim kutusunda **metin dosyası** şablonunu seçin.

6. **Ad** kutusuna, **CustomAction. spdata** girin ve sonra **Ekle** düğmesini seçin.

7. Aşağıdaki XML 'i *CustomAction. spdata* dosyasına ekleyin ve dosyayı kaydedin ve kapatın.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Bu dosya, proje öğesinin içerdiği dosyalarla ilgili bilgiler içerir. `Type`Öğesinin özniteliği, `ProjectItem` <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> Proje öğesi tanımında ( `CustomActionProjectItemTypeProvider` Bu kılavuzda daha önce oluşturduğunuz sınıf) geçirilen aynı dizeye ayarlanmalıdır. *. spdata* dosyalarının içerikleri hakkında daha fazla bilgi için bkz. [SharePoint proje öğesi şeması başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md).

8. **Çözüm Gezgini**, **ItemTemplate** projesinin kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

9. **Yeni öğe Ekle** iletişim kutusunda, **XML dosya** şablonunu seçin.

10. **Ad** kutusuna **Elements.xml** girin ve sonra **Ekle** düğmesini seçin.

11. *Elements.xml* dosyasının IÇERIĞINI aşağıdaki XML ile değiştirin ve sonra dosyayı kaydedip kapatın.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     bu dosya, SharePoint sitesinin **site eylemleri** menüsünde bir menü öğesi oluşturan varsayılan bir özel eylem tanımlar. Bir Kullanıcı menü öğesini seçtiğinde, öğesinde belirtilen URL `UrlAction` Web tarayıcısında açılır. Özel bir eylem tanımlamak için kullanabileceğiniz XML öğeleri hakkında daha fazla bilgi için bkz. [özel eylem tanımları](/sharepoint/dev/schema/custom-action-definition-schema).

12. İsteğe bağlı olarak, *ItemTemplate. ico* dosyasını açın ve bunu tanıyabileceğiniz bir tasarıma sahip olacak şekilde değiştirin. Bu simge, **Yeni öğe Ekle** iletişim kutusunda proje öğesinin yanında görüntülenir.

13. **Çözüm Gezgini**, **ItemTemplate** projesi için kısayol menüsünü açın ve ardından **Project kaldır**' ı seçin.

14. **ItemTemplate** projesinin kısayol menüsünü yeniden açın ve ardından **ItemTemplate. csproj Düzenle** veya **ItemTemplate. vbproj** öğesini Düzenle ' yi seçin.

15. `VSTemplate`Proje dosyasında aşağıdaki öğeyi bulun.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Bu `VSTemplate` öğeyi AŞAĞıDAKI XML ile değiştirin ve sonra dosyayı kaydedip kapatın.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Öğesi, proje oluşturduğunuzda öğe şablonunun oluşturulduğu yolda ek klasörleri belirler. burada belirtilen klasörler, öğe şablonunun yalnızca müşteriler **yeni öğe ekle** iletişim kutusunu açtıklarında kullanılabilir olacağını ve **SharePoint** düğümünü genişlettikten sonra **2010** düğümünü seçmesini sağlamaktır.

17. **Çözüm Gezgini**, **ItemTemplate** projesi için kısayol menüsünü açın ve ardından **Project yeniden yükle**' yi seçin.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Proje öğesini dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, VSIX projesinde bulunan kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSıX paketini yapılandırmak ve oluşturmak için

1. **Çözüm Gezgini**' de, CustomActionProjectItem projesinde **kaynak. Extension. valtmanifest** dosyasının kısayol menüsünü açın ve **Aç**' ı seçin.

     Visual Studio, dosyayı bildirim düzenleyicisinde açar. Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)).

2. **ürün adı** kutusuna, **öğe Project özel eylem** girin.

3. **Yazar** kutusuna **contoso** girin.

4. **açıklama** kutusuna, **özel bir eylemi temsil eden SharePoint bir proje öğesi** girin.

5. **Varlıklar** sekmesinde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

6. **Tür** listesinde, **Microsoft. VisualStudio. ItemTemplate**' i seçin.

    > [!NOTE]
    > Bu değer, `ItemTemplate` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe, proje öğesi şablonunu içeren VSıX paketindeki alt klasörü tanımlar. Daha fazla bilgi için bkz. [ItemTemplate öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

8. **Project** listesinde **ıtemtemplate**' i ve sonra **tamam** düğmesini seçin.

9. **Varlıklar** sekmesinde **Yeni** düğmesini yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

10. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

12. **Project** listesinde **projectıtemdefinition**' ı seçin.

13. **Tamam** düğmesini seçin.

14. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından projenin hatasız derlendiğinden emin olun.

15. CustomActionProjectItem projesinin derleme çıkış klasörünün CustomActionProjectItem. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... CustomActionProjectItem projesini içeren klasörün altındaki \bin\Debug klasörü.

## <a name="test-the-project-item"></a>Proje öğesini test etme
 Artık proje öğesini test etmeye hazırsınız. İlk olarak, Visual Studio deneysel örneğinde CustomActionProjectItem çözümünün hata ayıklamasını başlatın. ardından, **özel eylem** proje öğesini Visual Studio deneysel örneğinde bir SharePoint projesinde test edin. son olarak, özel eylemin beklendiği gibi çalıştığını doğrulamak için SharePoint projesi derleyin ve çalıştırın.

#### <a name="to-start-debugging-the-solution"></a>Çözümdeki hata ayıklamayı başlatmak için

1. yönetici kimlik bilgileriyle Visual Studio yeniden başlatın ve sonra CustomActionProjectItem çözümünü açın.

2. CustomAction kod dosyasını açın ve sonra yöntemdeki kodun ilk satırına bir kesme noktası ekleyin `InitializeType` .

3. Hata ayıklamayı başlatmak için **F5** tuşunu seçin.

     Visual Studio, uzantıyı%userprofile%\appdata\local\microsoft\visualstudio\10.0exp\extensions\contoso\custom Action Project ıtem\1.0 dizinine yükleyerek Visual Studio deneysel örneğini başlatır. Proje öğesini bu Visual Studio örneğinde test edersiniz.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Proje öğesini Visual Studio test etmek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **dosya**  >  **yeni**  >  **Project**' ni seçin.

2. **Visual C#** veya **Visual Basic** (öğe şablonunuzun desteklediği dile bağlı olarak) genişletin, **SharePoint**' i genişletin ve ardından **2010** düğümünü seçin.

3. proje şablonları listesinde **SharePoint 2010 Project** öğesini seçin.

4. **Ad** kutusuna **CustomActionTest** girin ve sonra **Tamam** düğmesini seçin.

5. **SharePoint özelleştirme sihirbazında**, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin ve ardından **son** düğmesini seçin.

6. **Çözüm Gezgini**, proje düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

7. **yeni öğe ekle** iletişim kutusunda **SharePoint** düğümü altında **2010** düğümünü seçin.

     **Özel eylem** öğesinin proje öğeleri listesinde göründüğünü doğrulayın.

8. **Özel eylem** öğesini seçin ve sonra **Ekle** düğmesini seçin.

     Visual Studio, projenize **CustomAction1** adlı bir öğe ekler ve *Elements.xml* dosyasını düzenleyicide açar.

9. diğer Visual Studio örneğindeki kodun, daha önce yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın `InitializeType` .

10. Projede hata ayıklamaya devam etmek için **F5** tuşunu seçin.

11. Visual Studio deneysel örneğinde, **Çözüm Gezgini**' de **CustomAction1** düğümünün kısayol menüsünü açın ve ardından **özel eylem tasarımcısını görüntüle**' yi seçin.

12. İleti kutusunun göründüğünü doğrulayın ve sonra **Tamam** düğmesini seçin.

     Bu kısayol menüsünü, geliştiriciler için özel eylem için bir tasarımcı görüntüleme gibi ek seçenekler veya komutlar sağlamak için kullanabilirsiniz.

13. Menü çubuğunda çıktıyı **görüntüle**' yi seçin  >  .

     **Çıkış** penceresi açılır.

14. **Çözüm Gezgini**' de, **CustomAction1** öğesi için kısayol menüsünü açın ve adını **MyCustomAction** olarak değiştirin.

     **Çıkış** penceresinde bir onay iletisi görüntülenir. Bu ileti, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> sınıfında tanımladığınız olay işleyicisi tarafından yazılır `CustomActionProjectItemTypeProvider` . Geliştirici proje öğesini değiştiren özel davranış uygulamak için bu olayı ve diğer proje öğesi olaylarını işebilirsiniz.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Özel eylemi SharePoint

1. Visual Studio'nin deneysel örneğinde, **MyCustomAction** proje öğesinin alt öğesi olanElements.xmldosyasını açın. 

2. Elements.xml *dosyasında* aşağıdaki değişiklikleri yapın ve dosyayı kaydedin:

    - `CustomAction`öğesinde, özniteliğini `Id` guid veya başka bir benzersiz dize olarak ayarlayın, aşağıdaki örnekte olduğu gibi:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - öğesinde `CustomAction` özniteliğini `Title` aşağıdaki örnekte olduğu gibi ayarlayın:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - öğesinde `CustomAction` özniteliğini `Description` aşağıdaki örnekte olduğu gibi ayarlayın:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - öğesinde `UrlAction` özniteliğini `Url` aşağıdaki örnekte olduğu gibi ayarlayın:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. **F5 anahtarını** seçin.

     Özel eylem, projenin Site **URL'si** özelliğinde belirtilen SharePoint site için paketli ve dağıtılmıştır. Web tarayıcısı bu sitenin varsayılan sayfasını açar.

    > [!NOTE]
    > Betik **Hata Ayıklama Devre Dışı** iletişim kutusu görüntülenirse projede **hata** ayıklamaya devam etmek için Evet düğmesini seçin.

4. Site **Eylemleri menüsünde Geliştirici** Merkezi'SharePoint **seçin,** tarayıcının web sitesini açtığını doğrulayın ve ardından https://docs.microsoft.com/sharepoint/dev/ web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizleme
 Proje öğesini test etme tamam olduktan sonra, proje öğesi şablonunu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizlemek için

1. Deneysel Visual Studio menü çubuğunda Araçlar Uzantıları ve   >  **Güncelleştirmeler'i seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinde Özel Eylem'i seçin **Project Ve** ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı **kaldırmak istediğinizden** emin olmak için Evet düğmesini seçin.

4. Kaldırma işlemini **tamamlamak için** Şimdi Yeniden Başlat düğmesini seçin.

5. Hem deneysel Visual Studio customActionProjectItem çözümünün açık olduğu örneği kapatın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yolu tamamlandıktan sonra, öğe şablonuna bir sihirbaz abilirsiniz. Bir kullanıcı bir SharePoint projesine Özel Eylem proje öğesi ekleyse sihirbaz, eylem hakkında (eylemin seçilecek konumu ve gidilecek URL gibi) bilgi toplar ve bu bilgileri yeni proje öğesinde *Elements.xml* dosyasına ekler. Daha fazla bilgi için [bkz. Adım adım: Öğe şablonuyla](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)özel eylem proje öğesi oluşturma, Bölüm 2 .

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Özel proje SharePoint türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint proje hizmeti](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Simgeler için Görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için Görüntü Düzenleyicisi'nde &#40;Veya Başka Bir Görüntü&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)