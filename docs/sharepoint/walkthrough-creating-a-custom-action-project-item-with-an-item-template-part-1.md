---
title: Öğe şablonu, bölüm 1 ile özel eylem proje öğesi oluşturma
titleSuffix: ''
description: Bir öğe şablonu kullanarak, bir SharePoint sitesinde özel eylem oluşturmak için bir proje projesine eklen SharePoint oluşturun.
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
ms.openlocfilehash: 8662dfb53be04ef86e6587b26ff2897f869939bef2bbdea99c747e3d79145daa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385139"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 1
  Kendi proje öğesi SharePoint oluşturarak Visual Studio proje sistemini genişletebilirsiniz. Bu kılavuzda, bir SharePoint sitesinde özel eylem oluşturmak için bir SharePoint oluşturabilirsiniz. Özel eylem, sitenin Site Eylemleri **menüsüne** bir menü SharePoint ekler.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Özel Visual Studio için yeni bir tür proje öğesi tanımlayan SharePoint uzantısı oluşturma. Yeni proje öğesi türü birkaç özel özellik uygulayan:

  - Proje öğesiyle ilgili ek görevler için başlangıç noktası olarak görev yapan, özel eylem için tasarımcı görüntüleme gibi bir kısayol menüsü Visual Studio.

  - Geliştirici, proje öğesinin ve onu içeren projenin belirli özelliklerini değiştirirken çalışan kod.

  - öğesinde proje öğesinin yanında görünen özel bir **Çözüm Gezgini.**

- Proje Visual Studio için bir öğe şablonu oluşturma.

- Proje öğesi Visual Studio uzantı derlemesini dağıtmak için bir Visual Studio Uzantısı (VSIX) paketi oluşturma.

- Proje öğesi hata ayıklama ve test etme.

  Bu tek başına izlenecek yol. Bu kılavuz tamamlandıktan sonra, öğe şablonuna bir sihirbaz ekleyerek proje öğesini geliştirebilirsiniz. Daha fazla bilgi için [bkz. Adım adım: Öğe şablonuyla](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)özel eylem proje öğesi oluşturma, Bölüm 2 .

> [!NOTE]
> GitHub'dan iş [](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) akışı için özel etkinlikler oluşturma adımlarını gösteren bir örnek indirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere ihtiyacınız vardır:

- Microsoft Windows, SharePoint ve Visual Studio.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu kılavuzda, **proje öğesini Project** bir VSIX paketi oluşturmak için SDK'daki VSIX uygulama şablonu kullanılır. Daha fazla bilgi için [bkz. SharePoint Araçları'Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

  Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- Uygulama içinde özel SharePoint. Daha fazla bilgi için bkz. [Özel Eylem](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Uygulama içinde öğe Visual Studio. Daha fazla bilgi için [bkz. Project Ve Öğe Şablonları Oluşturma.](../ide/creating-project-and-item-templates.md)

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için üç proje oluşturmanız gerekir:

- VSIX projesi. Bu proje, proje öğesini dağıtmak için VSIX SharePoint oluşturur.

- Öğe şablonu projesi. Bu proje, proje öğesini bir SharePoint projesine eklemek için kullanılmaktadır SharePoint oluşturur.

- Bir sınıf kitaplığı projesi. Bu proje, Visual Studio öğesinin davranışını tanımlayan bir SharePoint uzantısını kullanır.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-vsix-project"></a>VSIX projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Menü çubuğunda Dosya Yeni **Dosya'Project.**  >    >  

3. Yeni Project iletişim kutusunun **en** üstünde yer alan listede, **4.5 .NET Framework emin** olun.

4. Yeni **Project** iletişim kutusunda **Visual C#** **veya** Visual Basic genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

    > [!NOTE]
    > **Genişletilebilirlik düğümü** yalnızca Visual Studio SDK'sı yüklüyse kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan önkoşullar bölümüne bakın.

5. **VSIX Project** seçin.

6. Ad **kutusuna** **CustomActionProjectItem yazın** ve tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**CustomActionProjectItem projesini Çözüm Gezgini.** 

#### <a name="to-create-the-item-template-project"></a>Öğe şablonu projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

2. Yeni Project iletişim kutusunun **en** üstünde yer alan listede, **4.5 .NET Framework emin** olun.

3. Yeni **Project** iletişim kutusunda **Visual C#** **veya** Visual Basic genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

4. Proje şablonları listesinde **C#** Öğe Şablonu'Visual Basic **seçin.**

5. Ad **kutusuna** **ItemTemplate yazın** ve tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Çözüme ItemTemplate** projesini ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

2. Yeni Project iletişim kutusunun **en** üstünde yer alan listede, **4.5 .NET Framework emin** olun.

3. Yeni **Project** iletişim kutusunda **Visual C#** **veya** Visual Basic düğümlerini genişletin, Windows  düğümünü seçin ve ardından Sınıf Kitaplığı **proje** şablonunu seçin.

4. Ad **kutusuna** **ProjectItemDefinition yazın ve** tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ProjectItemDefinition projesini** çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Proje öğesi türünü tanımlamak için SharePoint önce, uzantı projesine kod dosyaları ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. Bu **Çözüm Gezgini** **ProjectItemDefinition** projesinin kısayol menüsünü açın, Ekle'yi ve ardından Yeni **Öğe'yi seçin.**

2. Proje öğeleri listesinde Kod **Dosyası'ı seçin.**

3. Ad **kutusuna** uygun dosya adı uzantısına **sahip CustomAction** adını girin ve ekle **düğmesini** seçin.

4. Bu **Çözüm Gezgini** **ProjectItemDefinition** projesinin kısayol menüsünü açın ve Başvuru Ekle'yi **seçin.**

5. Başvuru **Yöneticisi - ProjectItemDefinition** iletişim kutusunda Derlemeler düğümünü **ve** ardından **Framework düğümünü** seçin.

6. Aşağıdaki derlemelerin her biri yanındaki onay kutusunu seçin:

    - System.ComponentModel.Composition

    - Sistem. Windows. Forms

7. Uzantılar **düğümünü** seçin, Microsoft.VisualStudio.Sharepoint derlemesi'nin yanındaki onay kutusunu işaretleyin ve ardından Tamam **düğmesini** seçin.

## <a name="define-the-new-sharepoint-project-item-type"></a>Yeni proje SharePoint türünü tanımlama
 Yeni proje öğesi türünün davranışını <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> tanımlamak için arabirimini uygulayan bir sınıf oluşturun. Yeni bir proje öğesi türü tanımlamak istediğiniz her durumda bu arabirimi gerçekleştirin.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Yeni proje öğesi SharePoint tanımlamak için

1. ProjectItemDefinition projesinde CustomAction kod dosyasını açın.

2. Bu dosyada yer alan kodu aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb" id="Snippet1":::

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Çözüm Gezgini'de proje öğesi için bir simge oluşturma
 Özel bir proje öğesi SharePoint, bir görüntüyü (simge veya bit eşlem) proje öğesiyle ilişkilendirilebilirsiniz. Bu görüntü, öğesinde proje öğesinin **yanında Çözüm Gezgini.**

 Aşağıdaki yordamda, proje öğesi için bir simge oluşturun ve simgeyi uzantı derlemesine katıştırabilirsiniz. Bu simgeye daha önce <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> oluşturduğunuz sınıfının simgesi tarafından `CustomActionProjectItemTypeProvider` başvurabilirsiniz.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Proje öğesi için özel bir simge oluşturmak için

1. Bu **Çözüm Gezgini** **ProjeItemDefinition** projesinin kısayol menüsünü açın, Ekle'yi ve ardından Yeni **Öğe... seçeneğini belirleyin.**

2. Proje öğeleri listesinde Simge Dosyası **öğesini** seçin.

    > [!NOTE]
    > Bu Visual Basic, Simge Dosyası öğesini **görüntülemek için** Genel **düğümünü seçmeniz** gerekir.

3. Ad **kutusuna** **CustomAction_SolutionExplorer.ico yazın** ve Ekle **düğmesini** seçin.

     Yeni simge Görüntü **Düzenleyicisi'nde açılır.**

4. Tanıyabilirsiniz bir tasarıma sahip olacak şekilde simge dosyasının 16x16 sürümünü düzenleyin ve simge dosyasını kaydedin.

5. Bu **Çözüm Gezgini**, **CustomAction_SolutionExplorer.ico'yu seçin.**

6. Özellikler **penceresinde,** Derleme Eylemi özelliğinin yanındaki **oku** seçin.

7. Görüntülenen listede Katıştırılmış **Kaynak'ı seçin.**

## <a name="checkpoint"></a>Checkpoint
 Kılavuzda bu noktada, proje öğesinin tüm kodu artık projededir. Hatasız derlenmiş olduğunu doğrulamak için projeyi derle.

#### <a name="to-build-your-project"></a>Projenizi derlemek için

1. **ProjectItemDefinition projesinin kısayol menüsünü açın ve** Oluştur'a **tıklayın.**

## <a name="create-a-visual-studio-item-template"></a>Bir Visual Studio şablonu oluşturma
 Diğer geliştiricilerin proje öğenizi kullanmalarını sağlamak için bir proje şablonu veya öğe şablonu oluşturmanız gerekir. Geliştiriciler yeni bir proje Visual Studio veya mevcut projeye öğe ekleyerek proje öğenizin bir örneğini oluşturmak için bu şablonları Visual Studio içinde kullanır. Bu kılavuzda, proje öğenizi yapılandırmak için ItemTemplate projesini kullanın.

#### <a name="to-create-the-item-template"></a>Öğe şablonunu oluşturmak için

1. ItemTemplate projesinde Class1 kod dosyasını silin.

2. ItemTemplate projesinde *ItemTemplate.vstemplate dosyasını* açın.

3. Dosyanın içeriğini aşağıdaki XML ile değiştirin ve ardından dosyayı kaydedin ve kapatın.

    > [!NOTE]
    > Aşağıdaki XML bir Visual C# öğe şablonuna göredir. Yeni bir öğe Visual Basic, öğesinin değerini `ProjectType` ile `VisualBasic` değiştirin.

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

     Bu dosya, öğe şablonunun içeriğini ve davranışını tanımlar. Bu dosyanın içeriği hakkında daha fazla bilgi için [bkz. Visual Studio Şablon Şeması Başvurusu.](../extensibility/visual-studio-template-schema-reference.md)

4. Bu **Çözüm Gezgini** **ItemTemplate** projesinin kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni Öğe'yi **seçin.**

5. Yeni **Öğe Ekle iletişim** kutusunda Metin Dosyası **şablonunu** seçin.

6. Ad **kutusuna** **CustomAction.spdata yazın** ve Ekle **düğmesini** seçin.

7. *CustomAction.spdata* dosyasına aşağıdaki XML'yi ekleyin ve ardından dosyayı kaydedin ve kapatın.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Bu dosya, proje öğesinin içerdiği dosyalar hakkında bilgi içerir. öğesinin özniteliği, proje öğesi tanımında (bu kılavuzda daha önce oluşturduğunuz sınıf) öğesine geçirilen aynı `Type` `ProjectItem` <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> `CustomActionProjectItemTypeProvider` dizeye ayar olmalıdır. *.spdata* dosyalarının içeriği hakkında daha fazla bilgi için [bkz. SharePoint proje öğesi şema başvurusu.](../sharepoint/sharepoint-project-item-schema-reference.md)

8. Bu **Çözüm Gezgini** **ItemTemplate** projesinin kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni Öğe'yi **seçin.**

9. Yeni **Öğe Ekle iletişim** kutusunda **XML** Dosyası şablonunu seçin.

10. Ad **kutusuna** Elements.xml **girin** ve ekle **düğmesini** seçin.

11. *dosyanın* içeriğiniElements.xmlXML ile değiştirin ve ardından dosyayı kaydedin ve kapatın.

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

     Bu dosya, sitenin **Site** Eylemleri menüsünde bir menü öğesi oluşturan varsayılan bir SharePoint tanımlar. Kullanıcı menü öğesini seçerse, öğesinde belirtilen URL `UrlAction` web tarayıcısında açılır. Özel eylem tanımlamak için kullanabileceğiniz XML öğeleri hakkında daha fazla bilgi için bkz. [Özel Eylem Tanımları.](/sharepoint/dev/schema/custom-action-definition-schema)

12. İsteğe bağlı *olarak, ItemTemplate.ico* dosyasını açın ve tanıyabilirsiniz bir tasarıma sahip olacak şekilde değiştirebilirsiniz. Bu simge, Yeni Öğe Ekle iletişim kutusunda proje **öğesinin yanında** görüntülenir.

13. Bu **Çözüm Gezgini** **ItemTemplate** projesinin kısayol menüsünü açın ve Ardından Yüklemeden kaldır'ı **Project.**

14. **ItemTemplate** projesinin kısayol menüsünü yeniden açın ve **ItemTemplate.csproj'yi** düzenle veya **ItemTemplate.vbproj öğesini düzenle'yi seçin.**

15. Proje dosyasında `VSTemplate` aşağıdaki öğeyi bulun.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Bu öğeyi `VSTemplate` aşağıdaki XML ile değiştirin ve ardından dosyayı kaydedin ve kapatın.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`öğesi, projeyi oluşturulduğunda öğe şablonunun oluşturulacak yolda ek klasörleri belirtir. Burada belirtilen klasörler, öğe şablonunun yalnızca müşteriler Yeni  Öğe Ekle iletişim kutusunu  açtıklarında kullanılabilir olmasını, SharePoint genişletin ve **ardından 2010 düğümünü** seçmesini sağlar.

17. Bu **Çözüm Gezgini** **ItemTemplate** projesinin kısayol menüsünü açın ve ardından Yeniden Yükle'yi **Project.**

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Proje öğesini dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için çözümünüzde VSIX projesini kullanarak bir VSIX paketi oluşturun. İlk olarak, VSIX projesine dahil edilen source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırabilirsiniz. Ardından, çözümü oluşturarak VSIX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX paketini yapılandırmak ve oluşturmak için

1. Bu **Çözüm Gezgini** CustomActionProjectItem projesinde **source.extension.vsixmanifest** dosyasının kısayol menüsünü açın ve aç'ı **seçin.**

     Visual Studio bildirim düzenleyicisinde açılır. source.extension.vsixmanifest dosyası, tüm VSIX paketlerinin gerekli olduğu extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 Başvurusu.](/previous-versions/dd393700(v=vs.110))

2. Ürün Adı **kutusuna Özel** Eylem ve Öğe **Project girin.**

3. Yazar **kutusuna** Contoso **yazın.**

4. Açıklama **kutusuna Özel** eylemi **temsil eden SharePoint bir proje öğesi seçin girin.**

5. Varlıklar **sekmesinde** Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

6. Tür **listesinde** **Microsoft.VisualStudio.ItemTemplate öğesini seçin.**

    > [!NOTE]
    > Bu değer `ItemTemplate` extension.vsixmanifest dosyasındaki öğesine karşılık gelen bir değerdir. Bu öğe, proje öğesi şablonunu içeren VSIX paketinde alt klasörü tanımlar. Daha fazla bilgi için bkz. [ItemTemplate Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

8. Yeni **Project** **ItemTemplate'ı ve** ardından Tamam **düğmesini** seçin.

9. Varlıklar **sekmesinde** Yeni düğmesini **yeniden** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

10. Tür **listesinde** **Microsoft.VisualStudio.MefComponent'ı seçin.**

    > [!NOTE]
    > Bu değer `MefComponent` extension.vsixmanifest dosyasındaki öğesine karşılık gelen bir değerdir. Bu öğe VSIX paketinde bir uzantı derlemenin adını belirtir. Daha fazla bilgi için bkz. [MEFComponent Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

12. Yeni **Project** **ProjectItemDefinition'ı seçin.**

13. Tamam **düğmesini** seçin.

14. Menü çubuğunda Derleme   >  **Çözümü'yü seçin** ve projenin hatasız derlenmiş olduğundan emin olun.

15. CustomActionProjectItem projesinin derleme çıkış klasöründe CustomActionProjectItem.vsix dosyasının olduğundan emin olun.

     Varsayılan olarak, derleme çıkış klasörü .'dür. CustomActionProjectItem projesini içeren klasörün altında \bin\Debug klasörü.

## <a name="test-the-project-item"></a>Proje öğesini test etmek
 Artık proje öğesini test etmeye hazır oluruz. İlk olarak, Visual Studio'nin deneysel örneğinde CustomActionProjectItem çözümünde hata ayıklamaya Visual Studio. Ardından, özel **eylemin deneysel** örneğinde yer alan SharePoint projesinde Özel Eylem proje öğesini Visual Studio. Son olarak, özel eylemin SharePoint çalıştığını doğrulamak için SharePoint projesini derleme ve çalıştırma.

#### <a name="to-start-debugging-the-solution"></a>Çözümde hata ayıklamaya başlamak için

1. Yönetici Visual Studio ile yeniden başlatın ve CustomActionProjectItem çözümünü açın.

2. CustomAction kod dosyasını açın ve ardından yönteminde ilk kod satırına bir kesme noktası `InitializeType` ekleyin.

3. Hata **ayıklamayı başlatmak için F5** anahtarını seçin.

     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project Item\1.0 uzantısını yüker ve deneysel bir Visual Studio. Proje öğesini bu örnek içinde test Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Proje öğesini Visual Studio

1. Deneysel Visual Studio örneğinde, menü çubuğunda Dosya Yeni   >    >  Dosya'Project.

2. **Visual C# veya** **Visual Basic** (öğe şablonunuz tarafından kullanılan dile bağlı olarak) öğesini genişletin, **SharePoint** genişletin ve **ardından 2010 düğümünü** seçin.

3. Proje şablonları listesinde, **2010 SharePoint'yi Project.**

4. Ad **kutusuna** **CustomActionTest yazın** ve tamam **düğmesini** seçin.

5. SharePoint **Özelleştirme Sihirbazı'nda,** hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin ve ardından Son **düğmesini** seçin.

6. Bu **Çözüm Gezgini** proje düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **Öğe'yi seçin.**

7. Yeni **Öğe Ekle iletişim** kutusunda, yeni öğe düğümü altındaki **2010** **SharePoint** seçin.

     Özel Eylem **öğesinin** proje öğeleri listesinde görüntülendiğinden emin olmak.

8. Özel **Eylem öğesini** ve ardından Ekle **düğmesini** seçin.

     Visual Studio **CustomAction1** adlı bir öğeyi projenize ekler ve *Elements.xml* dosyasını düzenleyicide açar.

9. Uygulamanın diğer örneğinde yer alan kodun Visual Studio daha önce yönteminde ayar güvenlik kesme noktası üzerinde durduğu `InitializeType` doğrulayın.

10. Projede hata ayıklamaya devam etmek için **F5** tuşuna basın.

11. Visual Studio'nin deneysel **örneğinde** **Çözüm Gezgini, CustomAction1** düğümünün kısayol menüsünü açın ve Ardından Özel Eylem Tasarımcısını **Görüntüle'yi seçin.**

12. Bir ileti kutusu görüntülendiğinden emin olup Tamam **düğmesini** seçin.

     Geliştiricilere özel eylem için tasarımcı görüntüleme gibi ek seçenekler veya komutlar sağlamak üzere bu kısayol menüsünü kullanabilirsiniz.

13. Menü çubuğunda Çıkışı **Görüntüle'yi**  >  **seçin.**

     Çıkış **penceresi** açılır.

14. Bu **Çözüm Gezgini** **CustomAction1** öğesinin kısayol menüsünü açın ve adını **MyCustomAction olarak değiştirebilirsiniz.**

     Çıkış **penceresinde** bir onay iletisi görüntülenir. Bu ileti, sınıfında <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> tanımlandığı olay işleyicisi tarafından `CustomActionProjectItemTypeProvider` yazılır. Geliştirici proje öğesini değiştiren özel davranış uygulamak için bu olayı ve diğer proje öğesi olaylarını işebilirsiniz.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Özel eylemi SharePoint

1. Visual Studio'nin deneysel *örneğinde,* **MyCustomAction** proje öğesinin alt öğesi olanElements.xmldosyasını açın.

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

2. Uzantı listesinde Özel Eylem ve Öğe **Project'ı ve** ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı **kaldırmak istediğinizden** emin olmak için Evet düğmesini seçin.

4. Kaldırma işlemini **tamamlamak için** Şimdi Yeniden Başlat düğmesini seçin.

5. Hem deneysel Visual Studio customActionProjectItem çözümünün açık olduğu örneği kapatın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yolu tamamlandıktan sonra, öğe şablonuna bir sihirbaz abilirsiniz. Kullanıcı bir SharePoint projesine Özel Eylem proje öğesi ekleyse sihirbaz, eylem hakkında (eylemin seçilecek konumu ve URL'si gibi) bilgi toplar ve bu bilgileri yeni proje öğesinde *Elements.xml* dosyasına ekler. Daha fazla bilgi için [bkz. Adım adım: Öğe şablonuyla](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)özel eylem proje öğesi oluşturma, Bölüm 2 .

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Özel proje SharePoint türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint proje hizmeti](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Simgeler için Görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için Görüntü Düzenleyicisi'nde &#40;Veya Başka Bir Görüntü&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)