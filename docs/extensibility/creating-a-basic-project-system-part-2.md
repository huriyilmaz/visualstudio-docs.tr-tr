---
title: temel bir Project sistemi oluşturma, bölüm 2 | Microsoft Docs
description: önceki makalede oluşturulan bir projeye Visual Studio şablonu, özellik sayfası ve diğer özellikleri nasıl ekleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 644921dac3a82da3ad618eda8787ee6866689753696268d026e73955ae286078
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452781"
---
# <a name="create-a-basic-project-system-part-2"></a>Temel proje sistemi oluşturma, Bölüm 2
Bu serideki ilk izlenecek yol, [temel bir proje sistemi oluşturun, 1. Bölüm](../extensibility/creating-a-basic-project-system-part-1.md), temel bir proje sisteminin nasıl oluşturulacağını gösterir. bu izlenecek yol, bir Visual Studio şablonu, özellik sayfası ve diğer özellikleri ekleyerek temel proje sisteminde derleme oluşturur. Bu, başlamadan önce ilk yönergeyi doldurmanız gerekir.

Bu izlenecek yol, proje dosya adı uzantısına sahip bir proje türünün nasıl oluşturulacağını öğretir. *myproj*. İzlenecek yolu tamamlamak için kendi dilinizi oluşturmanız gerekmez, çünkü izlenecek yol Visual C# Proje sisteminden boratır.

Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:

- Visual Studio şablonu oluşturun.

- Visual Studio şablonu dağıtın.

- **yeni Project** iletişim kutusunda bir proje türü alt düğümü oluşturun.

- Visual Studio şablonunda parametre değişimini etkinleştirin.

- Proje özellik sayfası oluştur.

> [!NOTE]
> Bu izlenecek yolda yer alan adımlar bir C# projesini temel alır. ancak, dosya adı uzantıları ve kod gibi ayrıntılar dışında bir Visual Basic projesi için aynı adımları kullanabilirsiniz.

## <a name="create-a-visual-studio-template"></a>Visual Studio şablonu oluşturma
- [Temel bir proje sistemi oluşturun, 1. Bölüm](../extensibility/creating-a-basic-project-system-part-1.md) temel bir proje şablonu oluşturmayı ve bunu proje sistemine eklemeyi gösterir. ayrıca <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> , sistem kayıt defterindeki *\\ templates\projssimpleproject \\* klasörünün tam yolunu yazan özniteliğini kullanarak bu şablonun Visual Studio nasıl kaydedileceği gösterilmektedir.

temel proje şablonu yerine bir Visual Studio şablonu (*. vstemplate* dosyası) kullanarak, şablonun **yeni Project** iletişim kutusunda nasıl göründüğünü ve şablon parametrelerinin nasıl yerine geçmekte olduğunu kontrol edebilirsiniz. *. Vstemplate* dosyası, proje sistem şablonu kullanılarak bir proje oluşturulduğunda kaynak dosyaların nasıl dahil edileceğini açıklayan bir XML dosyasıdır. Proje sistemi, *. vstemplate* dosyası ve kaynak dosyaları bir *.zip* dosyasında toplanarak ve *.zip* dosyası Visual Studio tanınan bir konuma kopyalanarak dağıtılır. Bu işlem daha sonra bu kılavuzda daha ayrıntılı olarak açıklanmıştır.

1. İçinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , [temel bir proje sistemi oluşturun, 1. Bölüm '](../extensibility/creating-a-basic-project-system-part-1.md)ü Izleyerek oluşturduğunuz SimpleProject çözümünü açın.

2. *Simpleprojectpackage. cs* dosyasında ProvideProjectFactory özniteliğini bulun. İkinci parametreyi (proje adı) null ve dördüncü parametre (proje şablonu klasörünün yolu) ile değiştirin. \\ \NullPath ", aşağıdaki gibi.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. \ Dosya \ *proje. vstemplate* ADLı bir XML dosyasını *\\ templates\projeler\simpleproject \\* klasörüne ekleyin.

4. *SimpleProject. vstemplate* içeriğini aşağıdaki kodla değiştirin.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. **Özellikler** penceresinde, \ Windows \ *\\ basit \\ Proje* klasöründeki beş dosyayı seçin ve **derleme eylemini** **ZipProject** olarak ayarlayın.

    ![basit Project klasörü](../extensibility/media/simpproj2.png "SimpProj2")

    bu \<TemplateData> bölüm, **yeni Project** iletişim kutusunda simpleproject proje türünün konumunu ve görünümünü aşağıdaki gibi belirler:

- \<Name>Öğesi, proje şablonunu SimpleProject uygulaması olacak şekilde adlandırır.

- \<Description>öğesi, proje şablonu seçildiğinde **yeni Project** iletişim kutusunda görünen açıklamayı içerir.

- \<Icon>Öğesi, SimpleProject proje türü ile birlikte görünen simgeyi belirtir.

- \<ProjectType>öğesi **yeni Project** iletişim kutusunda Project türünü adlandırır. Bu ad ProvideProjectFactory özniteliğinin proje adı parametresinin yerini alır.

  > [!NOTE]
  > \<ProjectType>Öğesi, `LanguageVsTemplate` `ProvideProjectFactory` simpleprojectpackage. cs dosyasındaki özniteliğin bağımsız değişkeniyle eşleşmelidir.

  \<TemplateContent>Bu bölümde, yeni bir proje oluşturulduğunda oluşturulan dosyalar açıklanmaktadır:

- *SimpleProject. myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Tüm üç dosya `ReplaceParameters` true olarak ayarlanmıştır, bu da parametre değişimini sağlar. *Program. cs* dosyası `OpenInEditor` true olarak ayarlanmıştır, bu da bir proje oluşturulduğunda dosyanın kod düzenleyicisinde açılmasına neden olur.

  Visual Studio şablon şemasındaki öğeler hakkında daha fazla bilgi için, [Visual Studio şablon şeması başvurusuna](../extensibility/visual-studio-template-schema-reference.md)bakın.

> [!NOTE]
> bir projede birden fazla Visual Studio şablonu varsa, her şablon ayrı bir klasörde bulunur. Bu klasördeki her dosya **derleme eyleminin** **ZipProject** olarak ayarlanmış olması gerekir.

## <a name="adding-a-minimal-vsct-file"></a>En az bir. vsct dosyası ekleme
 yeni veya değiştirilmiş bir Visual Studio şablonunu tanımak için Visual Studio kurulum modunda çalıştırılmalıdır. Kurulum modu, var olan bir *. vsct* dosyası gerektirir. Bu nedenle, projeye en az bir *. vsct* dosyası eklemeniz gerekir.

1. SimpleProject *. vsct* ADLı bir XML dosyasını SimpleProject projesine ekleyin.

2. *SimpleProject. vsct* dosyasının içeriğini aşağıdaki kodla değiştirin.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Bu dosyanın **derleme eylemini** **Vsctcompile** olarak ayarlayın. Bunu, **Özellikler** penceresinde değil yalnızca *. csproj* dosyasında yapabilirsiniz. Bu dosyanın **derleme eyleminin** bu noktada **none** olarak ayarlandığından emin olun.

    1. SimpleProject düğümüne sağ tıklayın ve ardından **SimpleProject. csproj öğesini Düzenle**' ye tıklayın.

    2. *. Csproj* dosyasında, *SimpleProject. vsct* öğesini bulun.

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Derleme eylemini **Vsctcompile** olarak değiştirin.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. Proje dosyası ve düzenleyiciyi kapatın.

    5. SimpleProject düğümünü kaydedin ve sonra **Çözüm Gezgini** **yeniden yükle**' ye tıklayın Project.

## <a name="examine-the-visual-studio-template-build-steps"></a>Visual Studio şablonu derleme adımlarını inceleyin
 vspackage proje derleme sistemi genellikle *. vstemplate* dosyası değiştirildiğinde veya *. vstemplate* dosyasını içeren proje yeniden oluşturulduğunda kurulum modunda Visual Studio çalışır. ayrıntı düzeyini MSBuild Normal veya daha yüksek olarak ayarlayarak da izleyebilirsiniz.

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Projeler ve çözümler** düğümünü genişletin ve ardından **Oluştur ve Çalıştır**' ı seçin.

3. **MSBuild projesi derleme çıkış ayrıntı düzeyini** **Normal** olarak ayarlayın. **Tamam**'a tıklayın.

4. SimpleProject projesini yeniden derleyin.

    *.zip* proje dosyası oluşturmak için derleme adımı aşağıdaki örneğe benzemelidir.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>Visual Studio şablonu dağıtma
Visual Studio şablonlar yol bilgilerini içermez. Bu nedenle, şablon *.zip* dosyasının Visual Studio bilinen bir konuma dağıtılması gerekir. ProjectTemplates klasörünün konumu genellikle *% LocalAppData% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates<*.

Proje fabrikasını dağıtmak için, yükleme programının yönetici ayrıcalıklarına sahip olması gerekir. Visual Studio yükleme düğümü altında şablonlar dağıtır: *... \ Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Visual Studio şablonunu Test etme
Visual Studio şablonunu kullanarak proje hiyerarşisi oluşturup oluşturmadığını görmek için proje fabrikasını Test edin.

1. Visual Studio SDK deneysel örneğini sıfırlayın.

    açık [!INCLUDE[win7](../debugger/includes/win7_md.md)] : **başlat** menüsünde **Microsoft Visual Studio/Microsoft Visual Studio SDK/tools** klasörünü bulun ve **Microsoft Visual Studio deneysel örneği sıfırla**' yı seçin.

    Windows sonraki sürümlerinde: **başlangıç** ekranında, **Microsoft Visual Studio \<version> deneysel örneği sıfırla** yazın.

2. Bir komut istemi penceresi görüntülenir. **Devam etmek için herhangi bir tuşa basın** sözcüklerini gördüğünüzde, **ENTER**' a tıklayın. Pencere kapandıktan sonra Visual Studio açın.

3. SimpleProject projesini yeniden oluşturun ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

4. Deneysel örnekte, bir SimpleProject projesi oluşturun. **yeni Project** iletişim kutusunda **simpleproject**' i seçin.

5. SimpleProject 'in yeni bir örneğini görmeniz gerekir.

    ![yeni örnek Project basit](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Project yeni örnek](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Proje türü alt düğümü oluştur
**yeni Project** iletişim kutusunda bir proje türü düğümüne alt düğüm ekleyebilirsiniz. Örneğin, SimpleProject proje türü için konsol uygulamaları, pencere uygulamaları, Web uygulamaları vb. için alt düğümlere sahip olabilirsiniz.

Alt düğümler, proje dosyasını değiştirerek ve öğelere alt öğe ekleyerek oluşturulur \<OutputSubPath> \<ZipProject> . Bir şablon, derleme veya dağıtım sırasında kopyalandığında, her alt düğüm proje şablonları klasörünün bir alt klasörü haline gelir.

Bu bölümde, SimpleProject proje türü için bir konsol alt düğümünün nasıl oluşturulacağı gösterilmektedir.

1. *\\ Templates\projeleri SimpleProject \\* klasörünü *\\ templates\projelerconsoleapp \\* olarak yeniden adlandırın.

2. **Özellikler** penceresinde, *\\ templates\projeler, \\* \ Windows \ uygulama klasöründeki beş dosyayı seçin ve **Build eyleminin** **ZipProject** olarak ayarlandığından emin olun.

3. SimpleProject. vstemplate dosyasında, \<TemplateData> kapanış etiketinden hemen önce, bölümünün sonuna aşağıdaki satırı ekleyin.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Bu, konsol uygulama şablonunun hem konsol alt düğümünde hem de alt düğümün üzerinde bir düzey olan SimpleProject üst düğümünde görünmesine neden olur.

4. *SimpleProject.vstemplate dosyasını* kaydedin.

5. *.csproj dosyasında,* \<OutputSubPath> ZipProject öğelerinin her biri için ekleyin. Daha önce olduğu gibi projeyi kaldırma ve proje dosyasını düzenleme.

6. Öğeleri \<ZipProject> bulun. Her \<ZipProject> öğeye bir öğe \<OutputSubPath> ekleyin ve Konsol değerini ekleyin. The ZipProject

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. Bunu \<PropertyGroup> proje dosyasına ekleyin:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Proje dosyasını kaydedin ve projeyi yeniden yükleyin.

## <a name="test-the-project-type-child-node"></a>Proje türü alt düğümünü test etmek
Konsol alt düğümünün Yeni Proje Konsolu **iletişim kutusunda** görüntülendiğinden emin olmak **için Project** test etmek.

1. Deneysel **Örneği Microsoft Visual Studio aracını** çalıştırın.

2. SimpleProject projesini yeniden oluşturma ve hata ayıklamayı başlatma. Deneysel örneğin görünmesi gerekir

3. Yeni **Proje Project** **SimpleProject düğümüne** tıklayın. Konsol **Uygulaması** şablonunun Şablonlar bölmesinde **görünmesi** gerekir.

4. **SimpleProject düğümünü** genişletin. Konsol **alt** düğümü görüntüleniyor. **SimpleProject Uygulaması** şablonu Şablonlar bölmesinde **görünmeye devam** eder.

5. **İptal'e** tıklayın ve hata ayıklamayı durdurun.

    ![Basit Project Paketi](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Basit Project Konsol Düğümü](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Proje şablonu parametrelerini değiştir
- [Temel bir proje sistemi oluşturmak için 1.](../extensibility/creating-a-basic-project-system-part-1.md) bölüm, temel bir şablon parametresi değiştirmesi yapmak için yönteminin `ProjectNode.AddFileFromTemplate` üzerine yazmayı gösterdi. Bu bölümde, şablon parametrelerinin daha karmaşık Visual Studio nasıl kullanılası öğretildi.

New **Project** iletişim kutusunda bir Visual Studio şablonu kullanarak proje oluşturursanız, şablon parametreleri projeyi özelleştirmek için dizelerle değiştirilir. Şablon parametresi, dolar işaretiyle başlayan ve sona eren özel bir belirteçtir( örneğin, $time$). Aşağıdaki iki parametre özellikle şablonu temel alan projelerde özelleştirmeyi etkinleştirmek için yararlıdır:

- $GUID[1-10]$ yeni bir Guid ile değiştirilir. En fazla 10 benzersiz GUID belirterek (örneğin, $guid 1$).

- $safeprojectname$, Yeni Çalışma Alanı iletişim kutusunda bir **kullanıcı tarafından Project** tüm güvenli olmayan karakterleri ve boşlukları kaldırmak için değiştirilmiş addır.

  Şablon parametrelerinin tam listesi için bkz. [Şablon parametreleri.](../ide/template-parameters.md)

### <a name="to-substitute-project-template-parameters"></a>Proje şablonu parametrelerinin yerine kullanmak için

1. *SimpleProjectNode.cs dosyasında* yöntemini `AddFileFromTemplate` kaldırın.

2. *\\ Templates\Projects\ConsoleApp\SimpleProject.myproj* dosyasında özelliğini bulun ve değerini \<RootNamespace> $safeprojectname$ olarak değiştirme.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. *\\ Templates\Projects\SimpleProject\Program.cs* dosyasında dosyanın içeriğini aşağıdaki kodla değiştirin:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. SimpleProject projesini yeniden oluşturma ve hata ayıklamayı başlatma. Deneysel örneğin görünmesi gerekir.

5. Yeni bir SimpleProject Konsol uygulaması oluşturun. (Veri **türleri Project** **SimpleProject'i seçin.** Yüklü **Visual Studio altında Konsol Uygulaması'nu** **seçin.)**

6. Yeni oluşturulan projede *Program.cs'yi açın.* Aşağıdakine benzer bir değere sahip olması gerekir (dosyanız için GUID değerleri farklılık gösterir).):

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>Proje özellik sayfası oluşturma
Kullanıcıların şablonunuza göre projelerde özellikleri görüntüley ve değiştiresin diye proje türünüz için bir özellik sayfası oluşturabilirsiniz. Bu bölümde, yapılandırmadan bağımsız bir özellik sayfası oluşturma hakkında size bir şey gösterir. Bu temel özellik sayfası, özellik sayfası sınıfınıza açık olan genel özellikleri görüntülemek için bir özellikler kılavuzu kullanır.

Özellik sayfası sınıfını temel sınıftan `SettingsPage` türetin. sınıfı tarafından sağlanan özellikler `SettingsPage` kılavuzu, çoğu temel veri türüne sahiptir ve bunların nasıl görüntülenbli olduğunu bilir. Buna ek olarak, `SettingsPage` sınıfı özellik değerlerinin proje dosyasında nasıl kalıcı olduğunu bilir.

Bu bölümde oluşturmakta olduğu özellik sayfası, şu proje özelliklerini değiştirmenizi ve kaydetmenizi sağlar:

- Assemblyname

- OutputType

- RootNamespace.

1. *SimpleProjectPackage.cs* dosyasında bu özniteliği `ProvideObject` sınıfına `SimpleProjectPackage` ekleyin:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Bu, özellik sayfası sınıfını `GeneralPropertyPage` COM'a kaydedmektedir.

2. *SimpleProjectNode.cs* dosyasında bu iki geçersiz kılınan yöntemi sınıfına `SimpleProjectNode` ekleyin:

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    Bu yöntemlerin her ikisi de özellik sayfası GUID'leri dizisi döndürür. GeneralPropertyPage GUID değeri dizideki tek öğedir, bu nedenle Özellik **Sayfaları** iletişim kutusunda yalnızca bir sayfa görüntülenir.

3. SimpleProject projesine *GeneralPropertyPage.cs* adlı bir sınıf dosyası ekleyin.

4. Aşağıdaki kodu kullanarak bu dosyanın içeriğini değiştirin:

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    sınıfı `GeneralPropertyPage` AssemblyName, OutputType ve RootNamespace ortak üç özelliği gösterir. AssemblyName'in ayarlanmış bir yöntemi yoktur, salt okunur özellik olarak görüntülenir. OutputType numaralandı sabiti olduğu için açılan liste olarak görünür.

    Temel `SettingsPage` sınıf, özellikleri `ProjectMgr` kalıcı yapmak için sağlar. yöntemi `BindProperties` kalıcı özellik değerlerini almak ve karşılık gelen özellikleri ayarlamak için `ProjectMgr` kullanır. yöntemi, `ApplyChanges` özelliklerin değerlerini almak ve bunları proje dosyasında kalıcı yapmak için `ProjectMgr` kullanır. özellik kümesi yöntemi, `IsDirty` özelliklerin kalıcı olması gerektirmektedir. Projeyi veya çözümü kaydeden kalıcılık oluşur.

5. SimpleProject çözümünü yeniden oluşturma ve hata ayıklamayı başlatma. Deneysel örneğin görünmesi gerekir.

6. Deneysel örnekte yeni bir SimpleProject Uygulaması oluşturun.

7. Visual Studio şablon kullanarak proje oluşturmak için proje fabrikanızı Visual Studio. Yeni *Program.cs* dosyası kod düzenleyicisinde açılır.

8. içinde proje düğümüne sağ tıklayın **Çözüm Gezgini** özellikler'e **tıklayın.** **Özellik Sayfaları** iletişim kutusu görüntülenir.

    ![Basit Project Özellik Sayfası](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Proje özellik sayfasını test edin
Artık özellik değerlerini değiştirebilir ve değiştirebilirsiniz.

1. **MyConsoleApplication Özellik Sayfaları** iletişim kutusunda **DefaultNamespace'i** **MyApplication olarak değiştirebilirsiniz.**

2. **OutputType özelliğini** ve ardından Sınıf Kitaplığı'ı **seçin.**

3. **Uygula'ya** ve ardından Tamam'a **tıklayın.**

4. Özellik Sayfaları **iletişim kutusunu** yeniden açın ve değişikliklerinizin kalıcı olduğunu doğrulayın.

5. Deneysel Visual Studio.

6. Deneysel örneği yeniden açın.

7. Özellik Sayfaları **iletişim kutusunu** yeniden açın ve değişikliklerinizin kalıcı olduğunu doğrulayın.

8. Deneysel Visual Studio.
    ![Deneysel örneği kapatma](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
