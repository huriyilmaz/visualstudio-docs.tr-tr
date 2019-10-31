---
title: Öğe şablonu, Bölüm 1 ile özel eylem proje öğesi oluşturma
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4a114345363deb9c5ddd0f5a4141cd7d99f0ac1c
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189184"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma
  Visual Studio 'da SharePoint proje sistemini, kendi proje öğesi türlerinizi oluşturarak genişletebilirsiniz. Bu kılavuzda, bir SharePoint sitesinde özel bir eylem oluşturmak için bir SharePoint projesine eklenebilen bir proje öğesi oluşturacaksınız. Özel eylem, SharePoint sitesinin **Site eylemleri** menüsüne bir menü öğesi ekler.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel bir eylem için yeni bir tür SharePoint proje öğesi tanımlayan bir Visual Studio uzantısı oluşturma. Yeni proje öğesi türü çeşitli özel özellikler uygular:

  - Visual Studio 'da özel eylem için tasarımcı görüntüleme gibi, proje öğesiyle ilgili ek görevler için başlangıç noktası görevi gören bir kısayol menüsü.

  - Bir geliştirici proje öğesinin belirli özelliklerini ve onu içeren projeyi değiştirdiğinde çalıştırılan kod.

  - **Çözüm Gezgini**içindeki proje öğesinin yanında görünen özel bir simge.

- Proje öğesi için Visual Studio öğe şablonu oluşturuluyor.

- Proje öğesi şablonunu ve uzantı derlemesini dağıtmak için bir Visual Studio uzantısı (VSıX) paketi oluşturma.

- Proje öğesini hata ayıklama ve test etme.

  Bu tek başına bir yönergedir. Bu yönergeyi tamamladıktan sonra, öğe şablonuna bir sihirbaz ekleyerek Proje öğesini geliştirebilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> Bir iş akışı için nasıl özel etkinlik oluşturulacağını gösteren [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 'dan bir örnek indirebilirsiniz.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Microsoft Windows, SharePoint ve Visual Studio sürümleri.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu izlenecek yol, Proje öğesini dağıtmak üzere bir VSıX paketi oluşturmak için SDK 'daki **VSIX proje** şablonunu kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- SharePoint 'te özel eylemler. Daha fazla bilgi için bkz. [özel eylem](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Visual Studio 'daki öğe şablonları. Daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için üç proje oluşturmanız gerekir:

- Bir VSıX projesi. Bu proje, SharePoint proje öğesini dağıtmak için VSıX paketini oluşturur.

- Bir öğe şablonu projesi. Bu proje, SharePoint proje öğesini bir SharePoint projesine eklemek için kullanılabilecek bir öğe şablonu oluşturur.

- Bir sınıf kitaplığı projesi. Bu proje, SharePoint proje öğesinin davranışını tanımlayan bir Visual Studio uzantısı uygular.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]başlatın.

2. Menü çubuğunda **dosya**  > **Yeni**  > **Proje**' yi seçin.

3. **Yeni proje** iletişim kutusunun üst kısmındaki listede **.NET Framework 4,5** ' nin seçili olduğundan emin olun.

4. **Yeni proje** iletişim kutusunda,  **C# Visual** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > **Genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'sını yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

5. **VSIX proje** şablonunu seçin.

6. **Ad** kutusuna **CustomActionProjectItem**girin ve sonra **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **CustomActionProjectItem** projesini **Çözüm Gezgini**ekler.

#### <a name="to-create-the-item-template-project"></a>Öğe şablonu projesi oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunun üst kısmındaki listede **.NET Framework 4,5** ' nin seçili olduğundan emin olun.

3. **Yeni proje** iletişim kutusunda,  **C# Visual** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

4. Proje şablonları listesinde,  **C# öğe** şablonunu veya **Visual Basic öğesi** şablonu şablonunu seçin.

5. **Ad** kutusuna **ItemTemplate**yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **ItemTemplate** projesini çözüme ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunun üst kısmındaki listede **.NET Framework 4,5** ' nin seçili olduğundan emin olun.

3. **Yeni proje** iletişim kutusunda, **Visual C#**  veya **Visual Basic** düğümlerini genişletin, **Windows** düğümünü seçin ve ardından **sınıf kitaplığı** proje şablonu ' nu seçin.

4. **Ad** kutusuna **ProjectItemDefinition**yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **ProjectItemDefinition** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

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

    - System. Windows. Forms

7. **Uzantılar** düğümünü seçin, Microsoft. VisualStudio. SharePoint derlemesinin yanındaki onay kutusunu Işaretleyin ve **Tamam** düğmesini seçin.

## <a name="define-the-new-sharepoint-project-item-type"></a>Yeni SharePoint proje öğesi türünü tanımlayın
 Yeni proje öğesi türünün davranışını tanımlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> arabirimini uygulayan bir sınıf oluşturun. Yeni proje öğesi türünü tanımlamak istediğinizde bu arabirimi uygulayın.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Yeni SharePoint proje öğesi türünü tanımlamak için

1. ProjectItemDefinition projesinde, CustomAction kod dosyasını açın.

2. Bu dosyadaki kodu aşağıdaki kodla değiştirin.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Çözüm Gezgini içinde proje öğesi için bir simge oluşturun
 Özel bir SharePoint proje öğesi oluşturduğunuzda, bir görüntüyü (simge veya bit eşlem) proje öğesiyle ilişkilendirebilirsiniz. Bu görüntü, **Çözüm Gezgini**içindeki proje öğesinin yanında görünür.

 Aşağıdaki yordamda, proje öğesi için bir simge oluşturacak ve simgeyi uzantı derlemesine katıştıraöğreneceksiniz. Bu simgeye, daha önce oluşturduğunuz `CustomActionProjectItemTypeProvider` sınıfının <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> başvurulur.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Proje öğesi için özel bir simge oluşturmak için

1. **Çözüm Gezgini**' de **ProjectItemDefinition** projesi için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe...** ' yi seçin.

2. Proje öğeleri listesinde, **simge dosyası** öğesini seçin.

    > [!NOTE]
    > Visual Basic projelerinde, **simge dosya** öğesini göstermek için **genel** düğümünü seçmeniz gerekir.

3. **Ad** kutusuna **CustomAction_SolutionExplorer. ico**girin ve sonra **Ekle** düğmesini seçin.

     Yeni simge **görüntü düzenleyicisinde**açılır.

4. Simge dosyasının 16x16 sürümünü, tanıyabileceğiniz bir tasarıma sahip olacak şekilde düzenleyin ve ardından simge dosyasını kaydedin.

5. **Çözüm Gezgini**' de **CustomAction_SolutionExplorer. ico**' ı seçin.

6. **Özellikler** penceresinde, **Yapı eylemi** özelliğinin yanındaki oku seçin.

7. Görüntülenen listede, **gömülü kaynak**' ı seçin.

## <a name="checkpoint"></a>Mak
 Bu noktada, proje öğesi için tüm kod artık projede bulunur. Hata olmadan derlendiğini doğrulamak için projeyi derleyin.

#### <a name="to-build-your-project"></a>Projenizi derlemek için

1. **ProjectItemDefinition** projesi için kısayol menüsünü açın ve **Oluştur**' a tıklayın.

## <a name="create-a-visual-studio-item-template"></a>Visual Studio öğe şablonu oluşturma
 Diğer geliştiricilerin Proje öğesini kullanmasını sağlamak için bir proje şablonu veya öğe şablonu oluşturmanız gerekir. Geliştiriciler, yeni bir proje oluşturarak veya mevcut bir projeye bir öğe ekleyerek proje öğesinin bir örneğini oluşturmak için Visual Studio 'daki bu şablonları kullanır. Bu izlenecek yol için, Proje öğesini yapılandırmak üzere ItemTemplate projesini kullanın.

#### <a name="to-create-the-item-template"></a>Öğe şablonu oluşturmak için

1. ItemTemplate projesinden Class1 kod dosyasını silin.

2. ItemTemplate projesinde *ItemTemplate. vstemplate* dosyasını açın.

3. Dosyanın içeriğini aşağıdaki XML ile değiştirin ve sonra dosyayı kaydedip kapatın.

    > [!NOTE]
    > Aşağıdaki XML bir görsel C# öğe şablonu içindir. Visual Basic bir öğe şablonu oluşturuyorsanız, `ProjectType` öğesinin değerini `VisualBasic`ile değiştirin.

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

     Bu dosya, öğe şablonunun içeriğini ve davranışını tanımlar. Bu dosyanın içeriği hakkında daha fazla bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md).

4. **Çözüm Gezgini**, **ItemTemplate** projesinin kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

5. **Yeni öğe Ekle** Iletişim kutusunda **metin dosyası** şablonunu seçin.

6. **Ad** kutusuna, **CustomAction. spdata**girin ve sonra **Ekle** düğmesini seçin.

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

     Bu dosya, proje öğesinin içerdiği dosyalarla ilgili bilgiler içerir. `ProjectItem` öğesinin `Type` özniteliği, proje öğesi tanımında <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> iletilen aynı dizeye ayarlanmalıdır (Bu kılavuzda daha önce oluşturduğunuz `CustomActionProjectItemTypeProvider` sınıfı). *. Spdata* dosyalarının içerikleri hakkında daha fazla bilgi için bkz. [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md).

8. **Çözüm Gezgini**, **ItemTemplate** projesinin kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

9. **Yeni öğe Ekle** iletişim kutusunda, **XML dosya** şablonunu seçin.

10. **Ad** kutusunda, **Elements. xml**girin ve sonra **Ekle** düğmesini seçin.

11. *Elements. xml* dosyasının IÇERIĞINI aşağıdaki XML ile değiştirin ve sonra dosyayı kaydedip kapatın.

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

     Bu dosya, SharePoint sitesinin **Site eylemleri** menüsünde bir menü öğesi oluşturan varsayılan bir özel eylem tanımlar. Bir Kullanıcı menü öğesini seçtiğinde, `UrlAction` öğesinde belirtilen URL Web tarayıcısında açılır. Özel bir eylem tanımlamak için kullanabileceğiniz XML öğeleri hakkında daha fazla bilgi için bkz. [özel eylem tanımları](/sharepoint/dev/schema/custom-action-definition-schema).

12. İsteğe bağlı olarak, *ItemTemplate. ico* dosyasını açın ve bunu tanıyabileceğiniz bir tasarıma sahip olacak şekilde değiştirin. Bu simge, **Yeni öğe Ekle** iletişim kutusunda proje öğesinin yanında görüntülenir.

13. **Çözüm Gezgini**, **ItemTemplate** projesi için kısayol menüsünü açın ve ardından **Projeyi Kaldır**' ı seçin.

14. **ItemTemplate** projesinin kısayol menüsünü yeniden açın ve ardından **ItemTemplate. csproj Düzenle** veya **ItemTemplate. vbproj**öğesini Düzenle ' yi seçin.

15. Aşağıdaki `VSTemplate` öğesini proje dosyasında bulun.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Bu `VSTemplate` öğesini aşağıdaki XML ile değiştirin ve sonra dosyayı kaydedip kapatın.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` öğesi, proje oluşturduğunuzda öğe şablonunun oluşturulduğu yolda ek klasörleri belirtir. Burada belirtilen klasörler, öğe şablonunun yalnızca müşteriler **Yeni öğe Ekle** iletişim kutusunu açtıklarında kullanılabilir olacağını ve **SharePoint** düğümünü genişlettikten sonra **2010** düğümünü seçmesini de sağlamaktır.

17. **Çözüm Gezgini**, **ItemTemplate** projesi için kısayol menüsünü açın ve ardından **projeyi yeniden yükle**' yi seçin.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Proje öğesini dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, VSIX projesinde bulunan kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSıX paketini yapılandırmak ve oluşturmak için

1. **Çözüm Gezgini**' de, CustomActionProjectItem projesinde **kaynak. Extension. valtmanifest** dosyasının kısayol menüsünü açın ve **Aç**' ı seçin.

     Visual Studio, dosyayı bildirim düzenleyicisinde açar. Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. **Ürün adı** kutusuna **özel eylem proje öğesi**girin.

3. **Yazar** kutusuna **contoso**girin.

4. **Açıklama** kutusunda, **özel bir eylemi temsil eden bir SharePoint proje öğesi**girin.

5. **Varlıklar** sekmesinde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

6. **Tür** listesinde, **Microsoft. VisualStudio. ItemTemplate**' i seçin.

    > [!NOTE]
    > Bu değer, Extension. valtmanifest dosyasındaki `ItemTemplate` öğesine karşılık gelir. Bu öğe, proje öğesi şablonunu içeren VSıX paketindeki alt klasörü tanımlar. Daha fazla bilgi için bkz. [ItemTemplate öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje**seçin.

8. **Proje** listesinde **ItemTemplate**' i ve ardından **Tamam** düğmesini seçin.

9. **Varlıklar** sekmesinde **Yeni** düğmesini yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

10. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent**öğesini seçin.

    > [!NOTE]
    > Bu değer, Extension. valtmanifest dosyasındaki `MefComponent` öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. **Kaynak** listesinde, **Geçerli çözümde bir proje**seçin.

12. **Proje** listesinde **ProjectItemDefinition**' ı seçin.

13. **Tamam** düğmesini seçin.

14. Menü çubuğunda **derleme** > **Oluştur çözüm**' ü seçin ve ardından projenin hatasız derlendiğinden emin olun.

15. CustomActionProjectItem projesinin derleme çıkış klasörünün CustomActionProjectItem. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... CustomActionProjectItem projesini içeren klasörün altındaki \bin\Debug klasörü.

## <a name="test-the-project-item"></a>Proje öğesini test etme
 Artık proje öğesini test etmeye hazırsınız. İlk olarak, Visual Studio 'nun deneysel örneğinde CustomActionProjectItem çözümünde hata ayıklamayı başlatın. Ardından, **özel eylem** Proje öğesini Visual Studio 'nun Deneysel örneğindeki bir SharePoint projesinde test edin. Son olarak, özel eylemin beklendiği gibi çalıştığını doğrulamak için SharePoint projesini derleyin ve çalıştırın.

#### <a name="to-start-debugging-the-solution"></a>Çözümdeki hata ayıklamayı başlatmak için

1. Visual Studio 'Yu yönetici kimlik bilgileriyle yeniden başlatın ve CustomActionProjectItem çözümünü açın.

2. CustomAction kod dosyasını açın ve sonra `InitializeType` yöntemindeki ilk kod satırına bir kesme noktası ekleyin.

3. Hata ayıklamayı başlatmak için **F5** tuşunu seçin.

     Visual Studio, uzantıyı%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project ıtem\1.0 ' a yükleyerek Visual Studio 'nun deneysel bir örneğini başlatır. Bu Visual Studio örneğinde Proje öğesini test edeceksiniz.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Visual Studio 'da Proje öğesini test etmek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **dosya** > **Yeni** > **projesi**' ni seçin.

2. **Görsel C#**  veya **Visual Basic** (öğe şablonunuzun desteklediği dile bağlı olarak) öğesini genişletin, **SharePoint**' i genişletin ve ardından **2010** düğümünü seçin.

3. Proje şablonları listesinde **SharePoint 2010 projesi**' ni seçin.

4. **Ad** kutusuna **CustomActionTest**girin ve sonra **Tamam** düğmesini seçin.

5. **SharePoint Özelleştirme Sihirbazı**'nda, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin ve ardından **son** düğmesini seçin.

6. **Çözüm Gezgini**, proje düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

7. **Yeni öğe Ekle** iletişim kutusunda, **SharePoint** düğümünün altındaki **2010** düğümünü seçin.

     **Özel eylem** öğesinin proje öğeleri listesinde göründüğünü doğrulayın.

8. **Özel eylem** öğesini seçin ve sonra **Ekle** düğmesini seçin.

     Visual Studio, **CustomAction1** adlı bir öğeyi projenize ekler ve *öğeleri. xml* dosyasını düzenleyicide açar.

9. Visual Studio 'nun diğer örneğindeki kodun, `InitializeType` yönteminde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın.

10. Projede hata ayıklamaya devam etmek için **F5** tuşunu seçin.

11. Visual Studio 'nun deneysel örneğinde, **Çözüm Gezgini**, **CustomAction1** düğümünün kısayol menüsünü açın ve ardından **özel eylem tasarımcısını görüntüle**' yi seçin.

12. İleti kutusunun göründüğünü doğrulayın ve sonra **Tamam** düğmesini seçin.

     Bu kısayol menüsünü, geliştiriciler için özel eylem için bir tasarımcı görüntüleme gibi ek seçenekler veya komutlar sağlamak için kullanabilirsiniz.

13. Menü çubuğunda > **çıktıyı** **görüntüle** ' yi seçin.

     **Çıkış** penceresi açılır.

14. **Çözüm Gezgini**' de, **CustomAction1** öğesi için kısayol menüsünü açın ve adını **MyCustomAction**olarak değiştirin.

     **Çıkış** penceresinde bir onay iletisi görüntülenir. Bu ileti, `CustomActionProjectItemTypeProvider` sınıfında tanımladığınız <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> olay işleyicisi tarafından yazılır. Geliştirici Proje öğesini değiştirdiğinde özel davranışı uygulamak için bu olayı ve diğer proje öğesi olaylarını işleyebilirsiniz.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint 'te özel eylemi test etmek için

1. Visual Studio 'nun deneysel örneğinde, **MyCustomAction** proje öğesinin bir alt öğesi olan *Elements. xml* dosyasını açın.

2. *Elements. xml* dosyasında aşağıdaki değişiklikleri yapın ve dosyayı kaydedin:

    - `CustomAction` öğesinde, aşağıdaki örnekte gösterildiği gibi, `Id` özniteliğini bir GUID veya başka bir benzersiz dize olarak ayarlayın:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - `CustomAction` öğesinde, aşağıdaki örnekte gösterildiği gibi `Title` özniteliğini ayarlayın:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - `CustomAction` öğesinde, aşağıdaki örnekte gösterildiği gibi `Description` özniteliğini ayarlayın:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - `UrlAction` öğesinde, aşağıdaki örnekte gösterildiği gibi `Url` özniteliğini ayarlayın:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. **F5** tuşunu seçin.

     Özel eylem paketlenir ve projenin **SITE URL** özelliğinde belirtilen SharePoint sitesine dağıtılır. Web tarayıcısı, bu sitenin varsayılan sayfasına açılır.

    > [!NOTE]
    > **Betik hata ayıklaması devre dışı** iletişim kutusu görüntülenirse, projede hata ayıklamaya devam etmek için **Evet** düğmesini seçin.

4. **Site eylemleri** menüsünde **SharePoint Geliştirici Merkezi**' ni seçin, tarayıcının https://docs.microsoft.com/sharepoint/dev/ Web sitesini açtığından emin olun ve ardından Web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Proje öğesini test etmeyi tamamladıktan sonra, Visual Studio 'nun deneysel örneğinden proje öğesi şablonunu kaldırın.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizlemek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **araçlar** > **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde **özel eylem proje öğesi**' ni seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin.

4. Kaldırma işlemini gerçekleştirmek için **Şimdi yeniden Başlat** düğmesini seçin.

5. Visual Studio 'nun Deneysel örneğini ve CustomActionProjectItem çözümünün açık olduğu örneğini kapatın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu yönergeyi tamamladıktan sonra, öğe şablonuna bir sihirbaz ekleyebilirsiniz. Bir Kullanıcı bir SharePoint projesine özel bir eylem proje öğesi eklediğinde, sihirbaz eyleme (konum ve eylem seçildiğinde gidilecek URL gibi) ilişkin bilgileri toplar ve bu bilgileri yeni bir dosyadaki *Elements. xml* dosyasına ekler Proje öğesi. Daha fazla bilgi için bkz. [Izlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Simgeler için Görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons)
- [Simgeler için simge veya diğer görüntü &#40;resmi Düzenleyicisi oluşturma&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)