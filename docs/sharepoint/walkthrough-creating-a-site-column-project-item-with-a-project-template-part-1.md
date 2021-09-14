---
title: Proje şablonu, Bölüm 1 ile site sütunu proje öğesi oluştur
titleSuffix: ''
description: bir site sütunu oluşturmak için bir proje öğesi türü tanımlayın ve ardından proje öğesini içeren SharePoint bir proje oluşturmak için kullanılacak bir proje şablonu oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 6ede65c0360a747c21d640e15b28c8b1dffe0583
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726751"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>İzlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma
  SharePoint projeler bir veya daha fazla SharePoint proje öğesi için kapsayıcılardır. kendi SharePoint proje öğesi türlerinizi oluşturup bunları bir proje şablonuyla ilişkilendirerek, Visual Studio SharePoint proje sistemini genişletebilirsiniz. Bu kılavuzda, bir site sütunu oluşturmak için bir proje öğesi türü tanımlayacaksınız ve sonra bir site sütunu proje öğesi içeren yeni bir proje oluşturmak için kullanılabilecek bir proje şablonu oluşturacaksınız.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- bir site sütunu için yeni bir SharePoint proje öğesi türünü tanımlayan Visual Studio uzantısı oluşturma. Proje öğesi türü, **Özellikler** penceresinde görünen basit özel bir özelliği içerir.

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Proje öğesi için proje şablonu oluşturuluyor.

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Proje şablonunu ve uzantı derlemesini dağıtmak için bir uzantı (VSIX) paketi oluşturma.

- Proje öğesini hata ayıklama ve test etme.

  Bu tek başına bir yönergedir. Bu yönergeyi tamamladıktan sonra proje şablonuna bir sihirbaz ekleyerek Proje öğesini geliştirebilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: proje şablonu, Bölüm 2 ile site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> örnek iş akışları serisi için bkz. [SharePoint iş akışı örnekleri](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen Microsoft Windows sürümleri, SharePoint ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. bu izlenecek yol SDK 'daki **vsıx Project** şablonunu, proje öğesini dağıtmak için bir vsıx paketi oluşturmak için kullanır. daha fazla bilgi için bkz. [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavram hakkında bilgi yararlı olur, ancak gerekli değildir:

- SharePoint içindeki site sütunları. Daha fazla bilgi için bkz. [sütunlar](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

- Visual Studio Project şablonlar. daha fazla bilgi için bkz. [Project ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için üç proje oluşturmanız gerekir:

- Bir VSıX projesi. Bu proje, site sütunu proje öğesini ve proje şablonunu dağıtmak için VSıX paketini oluşturur.

- Proje şablonu projesi. bu proje, site sütunu proje öğesini içeren yeni bir SharePoint projesi oluşturmak için kullanılabilecek bir proje şablonu oluşturur.

- Bir sınıf kitaplığı projesi. bu proje, site sütunu proje öğesinin davranışını tanımlayan bir Visual Studio uzantısı uygular.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

3. **yeni Project** iletişim kutusunun üst kısmında .NET Framework sürümleri listesinde **.NET Framework 4,5** ' nin seçildiğinden emin olun.

4. **Visual Basic** veya **Visual C#** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > **genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'yı yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

5. Proje şablonları listesinde **vsıx Project**' yi seçin.

6. **Ad** kutusuna **SiteColumnProjectItem** girin ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**SiteColumnProjectItem** projesini **Çözüm Gezgini** ekler.

#### <a name="to-create-the-project-template-project"></a>Proje şablonu projesi oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

2. **yeni Project** iletişim kutusunun üst kısmında .NET Framework sürümleri listesinde **.NET Framework 4,5** ' nin seçildiğinden emin olun.

3. **Visual C#** veya **Visual Basic** düğümünü genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

4. proje şablonları listesinde **C# Project şablonu** ' nu veya **Project şablon şablonu Visual Basic** ' nı seçin.

5. **Ad** kutusuna **SiteColumnProjectTemplate** girin ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**SiteColumnProjectTemplate** projesini çözüme ekler.

6. Class1 kod dosyasını projeden silin.

7. bir Visual Basic projesi oluşturduysanız, projeden aşağıdaki dosyaları da silin:

    - *MyApplication. Designer. vb*

    - MyApplication. MyApp

    - *Resources. Designer. vb*

    - *Resources. resx*

    - *Ayarlar. Tasarımcı. vb*

    - Ayarlar. ayarlar

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

2. **yeni Project** iletişim kutusunun üst kısmında .NET Framework sürümleri listesinde **.NET Framework 4,5** ' nin seçildiğinden emin olun.

3. **Visual C#** veya **Visual Basic** düğümlerini genişletin, **Windows** düğümünü seçin ve ardından **sınıf kitaplığı** şablonunu seçin.

4. **Ad** kutusuna **projectItemTypeDefinition** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**projectItemTypeDefinition** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Uzantı projesini yapılandırmak için kod dosyalarını ve derleme başvurularını ekleyin.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. ProjectItemTypeDefinition projesinde, **SiteColumnProjectItemTypeProvider** adlı bir kod dosyası ekleyin.

2. menü çubuğunda **Project**  >  **başvuru ekle**' yi seçin.

3. **Reference Manager-projectItemTypeDefinition** iletişim kutusunda, **derlemeler** düğümünü genişletin, **Framework** düğümünü seçin ve ardından System. ComponentModel. Composition onay kutusunu seçin.

4. **Uzantılar** düğümünü seçin, Microsoft. VisualStudio ' nin yanındaki onay kutusunu işaretleyin. SharePoint derleme ve sonra **tamam** düğmesini seçin.

## <a name="define-the-new-sharepoint-project-item-type"></a>yeni SharePoint proje öğesi türünü tanımlayın
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>Yeni proje öğesi türünün davranışını tanımlamak için arabirimini uygulayan bir sınıf oluşturun. Yeni proje öğesi türünü tanımlamak istediğinizde bu arabirimi uygulayın.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>yeni SharePoint proje öğesi türünü tanımlamak için

1. **SiteColumnProjectItemTypeProvider** kod dosyasında, varsayılan kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb" id="Snippet1":::

## <a name="create-a-visual-studio-project-template"></a>Visual Studio proje şablonu oluşturma
 bir proje şablonu oluşturarak, diğer geliştiricilerin site sütunu proje öğelerini içeren SharePoint projeler oluşturmasını sağlayabilirsiniz. SharePoint proje şablonu, *. csproj* veya *. vbproj* ve *. vstemplate* dosyaları gibi Visual Studio tüm projeler için gereken dosyaları ve SharePoint projelerine özgü dosyaları içerir. daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 bu yordamda, SharePoint projelerine özgü dosyaları oluşturmak için boş bir SharePoint projesi oluşturacaksınız. Daha sonra bu dosyaları, bu projeden oluşturulan şablona dahil olmaları için SiteColumnProjectTemplate projesine eklersiniz. ayrıca, **yeni Project** iletişim kutusunda proje şablonunun nerede göründüğünü belirtmek için sitecolumnprojecttemplate proje dosyasını da yapılandırırsınız.

#### <a name="to-create-the-files-for-the-project-template"></a>Proje şablonu dosyalarını oluşturmak için

1. Yönetici kimlik bilgileriyle ikinci bir örneğini başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **basesharepointproject** adında bir SharePoint 2010 projesi oluşturun.

   > [!IMPORTANT]
   > **SharePoint özelleştirme sihirbazında**, **grup çözümü olarak dağıt** seçenek düğmesini seçmeyin.

3. Projeye boş bir öğe öğesi ekleyin ve ardından öğeyi **alan1** olarak adlandırın.

4. Projeyi kaydedin ve ikinci örneğini kapatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

5. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SiteColumnProjectItem çözümü açık olan örneğinde, **Çözüm Gezgini**' de **SiteColumnProjectTemplate** proje düğümünün kısayol menüsünü açın, **Ekle**' yi seçin ve ardından **Varolan öğe**' yi seçin.

6. **Varolan öğe Ekle** iletişim kutusunda, dosya uzantılarının listesini açın ve **tüm dosyalar ( \* . \* )** öğesini seçin.

7. BaseSharePointProject projesini içeren dizinde Key. snk dosyasını seçin ve sonra **Ekle** düğmesini seçin.

   > [!NOTE]
   > Bu kılavuzda, oluşturduğunuz proje şablonu, şablonu kullanılarak oluşturulan her bir projeyi imzalamak için aynı Key. snk dosyasını kullanır. Her proje örneği için farklı bir Key. snk dosyası oluşturmak üzere bu örneği genişletmeyi öğrenmek için bkz. [Izlenecek yol: proje şablonu, Bölüm 2 ile site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. BaseSharePointProject dizinindeki belirtilen alt klasörlerden aşağıdaki dosyaları eklemek için 5-8 adımlarını yineleyin:

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     Bu dosyaları doğrudan SiteColumnProjectTemplate projesine ekleyin; projesinde Field1, Features veya Package alt klasörlerini yeniden oluşturama. Bu dosyalar hakkında daha fazla bilgi için bkz. Proje öğeleri için öğe [SharePoint ve proje şablonları oluşturma.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Geliştiricilerin Proje Şablonunu Yeni Uygulama iletişim kutusunda nasıl Project yapılandırmak için

1. Bu **Çözüm Gezgini,** **SiteColumnProjectTemplate** proje düğümü için kısayol menüsünü açın ve ardından Yüklemeden kaldır'ı **Project.** Herhangi bir dosyada yapılan değişiklikleri kaydetmeniz istenirse Evet **düğmesini** seçin.

2. **SiteColumnProjectTemplate** düğümünün kısayol menüsünü yeniden açın ve **siteyi düzenleColumnProjectTemplate.csproj veya** **Edit SiteColumnProjectTemplate.vbproj** öğesini seçin.

3. Proje dosyasında aşağıdaki öğeyi `VSTemplate` bulun.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Bu öğeyi aşağıdaki XML ile değiştirin.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`öğesi, projeyi oluşturulduğunda proje şablonunun oluşturulacak yolda ek klasörleri belirtir. Burada belirtilen klasörler, proje şablonunun yalnızca müşteriler **Yeni** Project iletişim kutusunu açtıklarında kullanılabilir olmasını, SharePoint düğümünü **genişletmesini** ve **ardından 2010 düğümünü seçmesini** sağlar.

5. Dosyayı kaydedin ve kapatın.

6. Bu **Çözüm Gezgini** **SiteColumnProjectTemplate** projesinin kısayol menüsünü açın ve sonra Yeniden Yükle'yi **Project.**

## <a name="edit-the-project-template-files"></a>Proje şablonu dosyalarını düzenleme
 SiteColumnProjectTemplate projesinde, proje şablonunun davranışını tanımlamak için aşağıdaki dosyaları düzenleyin:

- *AssemblyInfo.cs* veya *AssemblyInfo.vb*

- *Elements.xml*

- *SharePointProjectItem.spdata*

- *Özellik1.özellik*

- *Package.package*

- *SiteColumnProjectTemplate.vstemplate*

- *ProjectTemplate.csproj* veya *ProjectTemplate.vbproj*

  Aşağıdaki yordamlarda, bu dosyalardan bazılarında değiştirilebilir parametreler eksersiniz. Değiştirilebilir parametre, dolar işareti ($) karakteriyle başlayan ve sona eren bir belirteçtir. Kullanıcı proje oluşturmak için bu proje şablonunu kullandığında, Visual Studio yeni projede bu parametreleri otomatik olarak belirli değerlerle değiştirir. Daha fazla bilgi için [bkz. Değiştirilebilir parametreler.](../sharepoint/replaceable-parameters.md)

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>AssemblyInfo.cs veya AssemblyInfo.vb dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde *AssemblyInfo.cs* veya *AssemblyInfo.vb* dosyasını açın ve en üstüne aşağıdaki deyimi ekleyin:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Bir **SharePoint** projesinin Korumalı Çözüm özelliği **True** olarak Visual Studio AssemblyInfo kod <xref:System.Security.AllowPartiallyTrustedCallersAttribute> dosyasına ekler. Ancak, proje şablonundaki AssemblyInfo kod dosyası varsayılan olarak ad alanını <xref:System.Security> içeri aktarmaz. Derleme hatalarını önlemek için **bunu veya** **Imports** deyimini kullanarak eklemeniz gerekir.

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-elementsxml-file"></a>Elements.xml düzenlemek için

1. SiteColumnProjectTemplate projesinde, *Elements.xml* dosyasının içeriğini aşağıdaki XML ile değiştirin.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
          Name="$safeprojectname$"
          DisplayName="$projectname$"
          Type="Text"
          Group="Custom Columns">
      </Field>
    </Elements>
    ```

     Yeni XML, site sütunlarının adını, temel türünü ve galerideki site sütununu listelenin yer alan `Field` grubu tanımlayan bir öğe ekler. Bu dosyanın içeriği hakkında daha fazla bilgi için bkz. [Alan Tanımı Şeması.](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14))

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>SharePointProjectItem.spdata dosyasını düzenlemek için

1. SiteColumnProjectTemplate *projesinde, SharePointProjectItem.spdata* dosyasının içeriğini aşağıdaki XML ile değiştirin.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Yeni XML dosyasında aşağıdaki değişiklikleri yapar:

   - öğesinin özniteliğini, proje öğesi tanımında öğesine geçirilen aynı dizeye (bu kılavuzda daha önce `Type` `ProjectItem` oluşturduğunuz <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> `SiteColumnProjectItemTypeProvider` sınıf) değiştirir.

   - öğesinden `SupportedTrustLevels` `SupportedDeploymentScopes` ve özniteliklerini `ProjectItem` kaldırır. Güven düzeyleri ve dağıtım kapsamları ProjectItemTypeDefinition projesinde sınıfında belirtildiklerinden bu öznitelik `SiteColumnProjectItemTypeProvider` değerleri gereksizdir.

     *.spdata* dosyalarının içeriği hakkında daha fazla bilgi için [bkz. SharePoint proje öğesi şema başvurusu.](../sharepoint/sharepoint-project-item-schema-reference.md)

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-feature1feature-file"></a>Feature1.feature dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde *Feature1.feature* dosyasının içeriğini aşağıdaki XML ile değiştirin.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">
     <projectItems>
       <projectItemReference itemId="$guid2$" />
     </projectItems>
   </feature>
   ```

    Yeni XML dosyasında aşağıdaki değişiklikleri yapar:

   - öğesinin ve `Id` `featureId` özniteliklerinin değerlerini olarak `feature` `$guid4$` değiştirir.

   - öğesinin `itemId` özniteliğinin değerlerini `projectItemReference` olarak `$guid2$` değiştirir.

     *.feature* dosyaları hakkında daha fazla bilgi için bkz. Proje öğeleri için öğe [SharePoint ve proje şablonları oluşturma.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-packagepackage-file"></a>Package.package dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde *Package.package* dosyasının içeriğini aşağıdaki XML ile değiştirin.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">
     <features>
       <featureReference itemId="$guid4$" />
     </features>
   </package>
   ```

    Yeni XML dosyasında aşağıdaki değişiklikleri yapar:

   - öğesinin ve `Id` `solutionId` özniteliklerinin değerlerini olarak `package` `$guid3$` değiştirir.

   - öğesinin `itemId` özniteliğinin değerlerini `featureReference` olarak `$guid4$` değiştirir.

     *.package* dosyaları hakkında daha fazla bilgi için bkz. Proje öğeleri için öğe [SharePoint ve proje şablonları oluşturma.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>sitecolumnprojecttemplate.vstemplate dosyasını düzenlemek için

1. SiteColumnProjectTemplate projesinde, SiteColumnProjectTemplate.vstemplate dosyasının içeriğini aşağıdaki XML bölümlerinden biri ile değiştirin.

   - Visual C# proje şablonu oluşturuyorsanız aşağıdaki XML'yi kullanın.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>CSharp</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

   - Visual Basic proje şablonu oluşturuyorsanız aşağıdaki XML'yi kullanın.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>VisualBasic</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

    Yeni XML dosyasında aşağıdaki değişiklikleri yapar:

   - öğesini `Name` Site Sütunu **değerine ayarlar.** (Bu ad Yeni Dosya **iletişim Project** görünür).

   - Her `ProjectItem` bir proje örneğine dahil edilen her dosya için öğeler ekler.

   - ad alanını `http://schemas.microsoft.com/developer/vstemplate/2005` kullanır. Bu çözümde yer alan diğer proje dosyaları ad alanını `http://schemas.microsoft.com/developer/msbuild/2003` kullanır. Bu nedenle, XML şeması uyarı iletileri oluşturulur, ancak bu kılavuzda bunları göz ardı edersiniz.

     *.vstemplate* dosyalarının içeriği hakkında daha fazla bilgi için [bkz. Visual Studio Şema Başvurusu.](../extensibility/visual-studio-template-schema-reference.md)

2. Dosyayı kaydedin ve kapatın.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>projecttemplate.csproj veya projecttemplate.vbproj dosyasını düzenlemek için

1. SiteColumnProjectTemplate *projesinde, ProjectTemplate.csproj* dosyasının veya *ProjectTemplate.vbproj* dosyasının içeriğini aşağıdaki XML bölümlerinden biri ile değiştirin.

    - Visual C# proje şablonu oluşturuyorsanız aşağıdaki XML'yi kullanın.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <AppDesignerFolder>Properties</AppDesignerFolder>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Web" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="Properties\AssemblyInfo.cs" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <ItemGroup>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

    1. Visual Basic proje şablonu oluşturuyorsanız aşağıdaki XML'yi kullanın.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <ProductVersion>
        </ProductVersion>
        <SchemaVersion>
        </SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        <OptionExplicit>On</OptionExplicit>
        <OptionCompare>Binary</OptionCompare>
        <OptionStrict>Off</OptionStrict>
        <OptionInfer>On</OptionInfer>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <OutputPath>bin\Debug\</OutputPath>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <DefineDebug>false</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Import Include="Microsoft.VisualBasic" />
        <Import Include="System" />
        <Import Include="System.Collections" />
        <Import Include="System.Collections.Generic" />
        <Import Include="System.Data" />
        <Import Include="System.Diagnostics" />
        <Import Include="System.Linq" />
        <Import Include="System.Xml.Linq" />
        <Import Include="Microsoft.SharePoint" />
        <Import Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="My Project\AssemblyInfo.vb" />
      </ItemGroup>
      <ItemGroup>
        <AppDesigner Include="My Project\" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

     Yeni XML dosyasında aşağıdaki değişiklikleri yapar:

    - `TargetFrameworkVersion`4.5 yerine .NET Framework 3.5'i belirtmek için öğesini kullanır.

    - Proje `SignAssembly` `AssemblyOriginatorKeyFile` çıktısını imzalamak için ve öğelerini ekler.

    - Projelerin `Reference` kullanabileceği derleme başvuruları için SharePoint ekler.

    - projesinde her varsayılan dosya içinElements.xml ve *SharePointProjectItem.spdata gibi öğeler ekler.*

2. Dosyayı kaydedin ve kapatın.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Proje şablonunu dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için **SiteColumnProjectItem** çözümünde VSIX projesini kullanarak bir VSIX paketi oluşturun. İlk olarak, VSIX projesine dahil edilen source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırabilirsiniz. Ardından, çözümü oluşturarak VSIX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX paketini yapılandırmak ve oluşturmak için

1. Bu **Çözüm Gezgini** **SiteColumnProjectItem** projesinde source.extension.vsixmanifest dosyasını bildirim düzenleyicisinde açın.

     source.extension.vsixmanifest dosyası, tüm VSIX paketlerinin gerekli olduğu extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 Başvurusu.](/previous-versions/dd393700(v=vs.110))

2. Ürün Adı **kutusuna** Site Sütunu **girin.**

3. Yazar **kutusuna** Contoso **yazın.**

4. Açıklama **kutusuna Site** sütunları **oluşturmak SharePoint bir proje yazın.**

5. Varlıklar **sekmesini** ve ardından Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu açılır.

6. Tür **listesinde** **Microsoft.VisualStudio.ProjectTemplate'ı seçin.**

    > [!NOTE]
    > Bu değer, `ProjectTemplate` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe, proje şablonunu içeren VSıX paketindeki alt klasörü tanımlar. Daha fazla bilgi için bkz. [ProjectTemplate öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

8. **Project** listesinde, **sitecolumnprojecttemplate**' i ve sonra **tamam** düğmesini seçin.

9. **Yeni** düğmesini yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

10. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

12. **Project** listesinde **projectıtemtypedefinition**' ı seçin ve ardından **tamam** düğmesini seçin.

13. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından projenin hatasız derlendiğinden emin olun.

## <a name="test-the-project-template"></a>Proje şablonunu test etme
 Artık proje şablonunu test etmeye hazırsınız. İlk olarak, Visual Studio deneysel örneğinde SiteColumnProjectItem çözümünde hata ayıklamaya başlayın. Ardından, **site sütunu** projesini Visual Studio deneysel örneğinde test edin. son olarak, site sütununun beklendiği gibi çalıştığını doğrulamak için SharePoint projesi derleyin ve çalıştırın.

#### <a name="to-start-debugging-the-solution"></a>Çözümdeki hata ayıklamayı başlatmak için

1. yönetici kimlik bilgileriyle Visual Studio yeniden başlatın ve ardından sitecolumnprojectıtem çözümünü açın.

2. SiteColumnProjectItemTypeProvider kod dosyasında, yöntemdeki kodun ilk satırına bir kesme noktası ekleyin `InitializeType` ve ardından hata ayıklamayı başlatmak Için **F5** tuşunu seçin.

     Visual Studio, uzantıyı%userprofile%\appdata\local\microsoft\visualstudio\10.0exp\extensions\contoso\site column\1.0 dizinine yükleyerek Visual Studio deneysel bir örneğini başlatır. Proje öğesini bu Visual Studio örneğinde test edersiniz.

#### <a name="to-test-the-project-in-visual-studio"></a>Projeyi Visual Studio test etmek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **dosya**  >  **yeni**  >  **Project**' ni seçin.

2. **Visual C#** veya **Visual Basic** düğümünü (proje şablonunuzun desteklediği dile bağlı olarak) genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. Proje şablonları listesinde, **site sütunu** şablonunu seçin.

4. **Ad** kutusuna **SiteColumnTest** girin ve **Tamam** düğmesini seçin.

     **Çözüm Gezgini** Içinde, **alan1** adlı bir proje öğesiyle yeni bir proje görüntülenir.

5. diğer Visual Studio örneğindeki kodun, yöntemde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın `InitializeType` ve sonra projede hata ayıklamaya devam etmek için **F5** tuşunu seçin.

6. **Çözüm Gezgini**, **alan1** düğümünü seçin ve sonra **F4** tuşunu seçin.

     **Özellikler** penceresi açılır.

7. Özellikler listesinde, Property **example özelliğinin** göründüğünü doğrulayın.

#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint site sütununu test etmek için

1. **Çözüm Gezgini**, **SiteColumnTest** düğümünü seçin.

2. **Özellikler** penceresinde, **site URL** özelliğinin yanındaki metin kutusunda, girin **http://localhost** .

     bu adım, geliştirme bilgisayarında hata ayıklama için kullanmak istediğiniz yerel SharePoint sitesini belirtir.

    > [!NOTE]
    > Site sütunu proje şablonu proje oluşturulduğunda bu değerin toplanması için bir sihirbaz sağlamadığından, **site URL 'si** özelliği varsayılan olarak boştur. Geliştiriciyi bu değere soran bir sihirbaz ekleme ve sonra bu özelliği yeni projede yapılandırma hakkında bilgi edinmek için bkz. [Izlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. **F5** tuşunu seçin.

     site sütunu paketlenir ve projenin **site URL** özelliğinde belirtilen SharePoint sitesine dağıtılır. Web tarayıcısı, bu sitenin varsayılan sayfasına açılır.

    > [!NOTE]
    > **Betik hata ayıklaması devre dışı** iletişim kutusu görüntülenirse, projede hata ayıklamaya devam etmek için **Evet** düğmesini seçin.

4. **site eylemleri** menüsünde **site Ayarlar**' yi seçin.

5. **site Ayarlar** sayfasında, **galeriler** listesinde, **site sütunları** bağlantısını seçin.

6. Site sütunları listesinde, **özel bir sütun** grubunun **SiteColumnTest** adlı bir sütun içerdiğini doğrulayın.

7. Web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Projeyi test etmeyi bitirdikten sonra, proje şablonunu Visual Studio deneysel örneğinden kaldırın.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizlemek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **araçlar**  >  **uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde, **site sütunu** uzantısını seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin.

4. Kaldırma işlemini gerçekleştirmek için **Kapat** düğmesini seçin.

5. her iki Visual Studio örneğini (deneysel örnek ve sitecolumnprojectıtem çözümünün açık olduğu Visual Studio örneğini) kapatın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu yönergeyi tamamladıktan sonra, proje şablonuna bir sihirbaz ekleyebilirsiniz. Bir Kullanıcı bir site sütun projesi oluşturduğunda, sihirbaz kullanıcıdan hata ayıklama için kullanacağı site URL 'sini ve yeni çözümün korumalı olup olmadığını sorar ve sihirbaz yeni projeyi bu bilgilerle yapılandırır. Sihirbaz ayrıca sütun hakkındaki bilgileri (temel tür ve sütunun site sütunu galerisinde listekaydedileceği grup gibi) toplar ve bu bilgileri yeni projedeki *Elements.xml* dosyasına ekler. Daha fazla bilgi için bkz. [Izlenecek yol: proje şablonu, Bölüm 2 ile site sütunu oluşturma proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [özel verileri SharePoint araçları uzantılarıyla ilişkilendir](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)