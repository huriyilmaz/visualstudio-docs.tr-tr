---
title: Öğe şablonu, bölüm 1 ile özel eylem proje öğesi oluşturma
titleSuffix: ''
description: Bir öğe şablonu kullanarak, bir SharePoint sitesinde özel eylem oluşturmak için bir SharePoint oluşturun.
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
ms.openlocfilehash: b01352aa0774f059329e849badbae257951e0ccb
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980962"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 1
  Kendi proje öğesi SharePoint oluşturarak Visual Studio proje sistemini genişletebilirsiniz. Bu kılavuzda, bir SharePoint sitesinde özel eylem oluşturmak için bir SharePoint oluşturabilirsiniz. Özel eylem, sitenin Site Eylemleri **menüsüne** bir menü SharePoint ekler.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Özel Visual Studio için yeni bir tür proje öğesi tanımlayan SharePoint uzantısı oluşturma. Yeni proje öğesi türü birkaç özel özellik uygulayan:

  - Proje öğesiyle ilgili ek görevler için başlangıç noktası olarak görev yapan bir kısayol menüsü ( örneğin, proje öğesinde özel eylem için bir tasarımcı Visual Studio.

  - Geliştirici, proje öğesinin ve onu içeren projenin belirli özelliklerini değiştirirken çalışan kod.

  - öğesinde proje öğesinin yanında görünen özel bir **Çözüm Gezgini.**

- Proje Visual Studio için bir öğe şablonu oluşturma.

- Proje öğesi Visual Studio uzantı derlemesini dağıtmak için bir Uzantı (VSIX) paketi oluşturma.

- Proje öğesi hata ayıklama ve test etme.

  Bu tek başına izlenecek yol. Bu kılavuz tamamlandıktan sonra, öğe şablonuna bir sihirbaz ekleyerek proje öğesini geliştirebilirsiniz. Daha fazla bilgi için [bkz. Adım adım: Öğe şablonuyla](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)özel eylem proje öğesi oluşturma, Bölüm 2 .

> [!NOTE]
> GitHub'dan iş [](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) akışı için özel etkinlikler oluşturma adımlarını gösteren bir örnek indirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere ihtiyacınız vardır:

- Microsoft Windows, SharePoint ve Visual Studio.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu kılavuzda, **proje öğesini Project** bir VSIX paketi oluşturmak için SDK'daki VSIX uygulama şablonu kullanılır. Daha fazla bilgi için [bkz. SharePoint Araçları'Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

  Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- Özel eylemler SharePoint. Daha fazla bilgi için bkz. [Özel Eylem](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Uygulama içinde öğe Visual Studio. Daha fazla bilgi için [bkz. Project Ve Öğe Şablonları Oluşturma.](../ide/creating-project-and-item-templates.md)

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için üç proje oluşturmanız gerekir:

- VSIX projesi. Bu proje, proje öğesini dağıtmak için VSIX SharePoint oluşturur.

- Öğe şablonu projesi. Bu proje, proje öğesini bir SharePoint projesine eklemek için kullanılmaktadır SharePoint oluşturur.

- Bir sınıf kitaplığı projesi. Bu proje, Visual Studio öğesinin davranışını tanımlayan bir SharePoint uzantısını kullanır.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-vsix-project"></a>VSIX projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Menü çubuğunda Dosya Yeni'yi **seçin**  >  **ve**  >  **Project.**

3. Yeni Özellikler iletişim kutusunun en **üstünde yer alan Project** **4.5 .NET Framework emin** olun.

4. Yeni **Project** iletişim kutusunda **Visual C#** **veya** Visual Basic genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

    > [!NOTE]
    > **Genişletilebilirlik düğümü yalnızca** Visual Studio SDK'sı yüklüyse kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan önkoşullar bölümüne bakın.

5. **VSIX Project** seçin.

6. Ad **kutusuna** **CustomActionProjectItem yazın** ve tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**CustomActionProjectItem projesini Çözüm Gezgini.** 

#### <a name="to-create-the-item-template-project"></a>Öğe şablonu projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

2. Yeni Özellikler iletişim kutusunun en **üstünde yer alan Project** **4.5 .NET Framework emin** olun.

3. Yeni **Project** iletişim kutusunda **Visual C#** **veya** Visual Basic genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

4. Proje şablonları listesinde **C#** Öğe Şablonu'Visual Basic  seçin.

5. Ad **kutusuna** **ItemTemplate yazın** ve tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Çözüme ItemTemplate** projesini ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

2. Yeni Özellikler iletişim kutusunun en **üstünde yer alan Project** **4.5 .NET Framework emin** olun.

3. Yeni **Project** iletişim kutusunda **Visual C#** **veya** Visual Basic düğümlerini genişletin, Windows  düğümünü seçin ve ardından Sınıf Kitaplığı **proje** şablonunu seçin.

4. Ad **kutusuna** **ProjectItemDefinition yazın ve** tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ProjectItemDefinition projesini** çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Proje öğesi türünü tanımlamak için SharePoint önce, uzantı projesine kod dosyaları ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. Bu **Çözüm Gezgini** **ProjeItemDefinition** projesinin kısayol menüsünü açın, Ekle'yi ve ardından Yeni Öğe'yi **seçin.**

2. Proje öğeleri listesinde Kod **Dosyası'ı seçin.**

3. Ad **kutusuna** uygun dosya adı uzantısına **sahip CustomAction** adını girin ve ekle **düğmesini** seçin.

4. Bu **Çözüm Gezgini** **ProjectItemDefinition** projesinin kısayol menüsünü açın ve Başvuru Ekle'yi **seçin.**

5. Başvuru **Yöneticisi - ProjectItemDefinition** iletişim kutusunda Derlemeler düğümünü **ve** ardından **Framework düğümünü** seçin.

6. Aşağıdaki derlemelerin her biri yanındaki onay kutusunu seçin:

    - System.ComponentModel.Composition

    - Sistem. Windows. Forms

7. Uzantılar **düğümünü** seçin, Microsoft.VisualStudio.Sharepoint derlemesi'nin yanındaki onay kutusunu işaretleyin ve ardından Tamam **düğmesini** seçin.

## <a name="define-the-new-sharepoint-project-item-type"></a>Yeni proje SharePoint türünü tanımlama
 Yeni proje öğesi türünün <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> davranışını tanımlamak için arabirimini uygulayan bir sınıf oluşturun. Yeni bir proje öğesi türü tanımlamak istediğiniz her durumda bu arabirimi gerçekleştirin.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Yeni proje öğesi SharePoint tanımlamak için

1. ProjectItemDefinition projesinde CustomAction kod dosyasını açın.

2. Bu dosyada yer alan kodu aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb" id="Snippet1":::

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Çözüm Gezgini'de proje öğesi için bir simge Çözüm Gezgini
 Özel bir proje öğesi SharePoint, bir görüntüyü (simge veya bit eşlem) proje öğesiyle ilişkilendirilebilirsiniz. Bu görüntü, öğesinde proje öğesinin **yanında Çözüm Gezgini.**

 Aşağıdaki yordamda, proje öğesi için bir simge oluşturun ve simgeyi uzantı derlemesine katıştırabilirsiniz. Bu simgeye daha önce <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> oluşturduğunuz sınıfının simgesi tarafından `CustomActionProjectItemTypeProvider` başvurabilirsiniz.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Proje öğesi için özel bir simge oluşturmak için

1. Bu **Çözüm Gezgini** **ProjectItemDefinition** projesinin kısayol menüsünü açın, Ekle'yi ve ardından Yeni **Öğe... seçeneğini belirleyin.**

2. Proje öğeleri listesinde Simge Dosyası **öğesini** seçin.

    > [!NOTE]
    > Bu Visual Basic, Simge Dosyası öğesini **görüntülemek için** Genel **düğümünü seçmeniz** gerekir.

3. Ad **kutusuna** **CustomAction_SolutionExplorer.ico yazın** ve ekle **düğmesini** seçin.

     Yeni simge Görüntü **Düzenleyicisi'nde açılır.**

4. Tanıyabilirsiniz bir tasarıma sahip olacak şekilde simge dosyasının 16x16 sürümünü düzenleyin ve simge dosyasını kaydedin.

5. Bu **Çözüm Gezgini,** **CustomAction_SolutionExplorer.ico'yu seçin.**

6. Özellikler **penceresinde,** Derleme Eylemi özelliğinin yanındaki **oku** seçin.

7. Görüntülenen listede Katıştırılmış **Kaynak'ı seçin.**

## <a name="checkpoint"></a>Checkpoint
 Kılavuzda bu noktada, proje öğesinin tüm kodu artık projededir. Hatasız derlenmiş olduğunu doğrulamak için projeyi derle.

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

     **Çıkış** penceresinde bir onay iletisi görüntülenir. Bu ileti, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> sınıfında tanımladığınız olay işleyicisi tarafından yazılır `CustomActionProjectItemTypeProvider` . Geliştirici Proje öğesini değiştirdiğinde özel davranışı uygulamak için bu olayı ve diğer proje öğesi olaylarını işleyebilirsiniz.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint özel eylemi test etmek için

1. Visual Studio deneysel örneğinde, **mycustomaction** proje öğesinin bir alt öğesi olan *Elements.xml* dosyasını açın.

2. *Elements.xml* dosyasında aşağıdaki değişiklikleri yapın ve dosyayı kaydedin:

    - `CustomAction`Öğesinde, `Id` Aşağıdaki örnekte gösterildiği gibi ÖZNITELIĞI bir GUID veya başka bir benzersiz dize olarak ayarlayın:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - Öğesinde, `CustomAction` `Title` Aşağıdaki örnekte gösterildiği gibi özniteliğini ayarlayın:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - Öğesinde, `CustomAction` `Description` Aşağıdaki örnekte gösterildiği gibi özniteliğini ayarlayın:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - Öğesinde, `UrlAction` `Url` Aşağıdaki örnekte gösterildiği gibi özniteliğini ayarlayın:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. **F5** tuşunu seçin.

     özel eylem paketlenir ve projenin **site URL** özelliğinde belirtilen SharePoint sitesine dağıtılır. Web tarayıcısı, bu sitenin varsayılan sayfasına açılır.

    > [!NOTE]
    > **Betik hata ayıklaması devre dışı** iletişim kutusu görüntülenirse, projede hata ayıklamaya devam etmek için **Evet** düğmesini seçin.

4. **Site eylemleri** menüsünde, **geliştirici merkezi SharePoint**' ni seçin, tarayıcının web sitesini açtığından emin olun `https://docs.microsoft.com/sharepoint/dev/` ve ardından web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Proje öğesini test etmeyi tamamladıktan sonra, Visual Studio deneysel örneğinden proje öğesi şablonunu kaldırın.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizlemek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **araçlar**  >  **uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. uzantılar listesinde, **öğe Project özel eylem**' i seçin ve ardından **kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin.

4. Kaldırma işlemini gerçekleştirmek için **Şimdi yeniden Başlat** düğmesini seçin.

5. Visual Studio deneysel örneğini ve CustomActionProjectItem çözümünün açık olduğu örneğini kapatın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu yönergeyi tamamladıktan sonra, öğe şablonuna bir sihirbaz ekleyebilirsiniz. bir kullanıcı bir SharePoint projesine özel bir eylem proje öğesi eklediğinde, sihirbaz eyleme (konum ve eylem seçildiğinde gidilecek URL gibi) ilişkin bilgileri toplar ve bu bilgileri yeni proje öğesindeki *Elements.xml* dosyasına ekler. Daha fazla bilgi için bkz. [Izlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint kullanın proje hizmeti](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için bir simge veya diğer görüntü &#40;görüntü Düzenleyicisi oluşturma&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)