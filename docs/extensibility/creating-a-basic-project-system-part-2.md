---
title: Temel proje sistemi oluşturma, Bölüm 2 | Microsoft Docs
description: Önceki bir makalede oluşturulan bir projeye Visual Studio şablonu, özellik sayfası ve diğer özellikleri nasıl ekleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 564d975a60c54a074d830742eb0ab6133fdbfe4e
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974606"
---
# <a name="create-a-basic-project-system-part-2"></a>Temel proje sistemi oluşturma, Bölüm 2
Bu serideki ilk izlenecek yol, [temel bir proje sistemi oluşturun, 1. Bölüm](../extensibility/creating-a-basic-project-system-part-1.md), temel bir proje sisteminin nasıl oluşturulacağını gösterir. Bu izlenecek yol, Visual Studio şablonu, özellik sayfası ve diğer özellikleri ekleyerek temel proje sisteminde derleme oluşturur. Bu, başlamadan önce ilk yönergeyi doldurmanız gerekir.

Bu izlenecek yol, proje dosya adı uzantısına sahip bir proje türünün nasıl oluşturulacağını öğretir. *myproj*. İzlenecek yolu tamamlamak için kendi dilinizi oluşturmanız gerekmez, çünkü izlenecek yol Visual C# Proje sisteminden boratır.

Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:

- Visual Studio şablonu oluşturun.

- Visual Studio şablonu dağıtın.

- **Yeni proje** iletişim kutusunda bir proje türü alt düğümü oluşturun.

- Visual Studio şablonunda parametre değişimini etkinleştirin.

- Proje özellik sayfası oluştur.

> [!NOTE]
> Bu izlenecek yolda yer alan adımlar bir C# projesini temel alır. Ancak, dosya adı uzantıları ve kod gibi ayrıntılar dışında bir Visual Basic projesi için aynı adımları kullanabilirsiniz.

## <a name="create-a-visual-studio-template"></a>Visual Studio şablonu oluşturma
- [Temel bir proje sistemi oluşturun, 1. Bölüm](../extensibility/creating-a-basic-project-system-part-1.md) temel bir proje şablonu oluşturmayı ve bunu proje sistemine eklemeyi gösterir. Ayrıca, bu şablonu Visual Studio ile nasıl kaydedeceğinizi <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> , sistem kayıt defterindeki *\\ Templates\projelerisimpleproject \\* klasörünün tam yolunu yazan özniteliği kullanarak da gösterir.

Temel proje şablonu yerine bir Visual Studio şablonu (*. vstemplate* dosyası) kullanarak, şablonun **Yeni proje** iletişim kutusunda nasıl göründüğünü ve şablon parametrelerinin nasıl yerine geçmekte olduğunu kontrol edebilirsiniz. *. Vstemplate* dosyası, proje sistem şablonu kullanılarak bir proje oluşturulduğunda kaynak dosyaların nasıl dahil edileceğini açıklayan bir XML dosyasıdır. Proje sistemi,. *vstemplate* dosyası ve kaynak dosyaları bir *. zip* dosyasında toplanarak ve *. zip* dosyasını Visual Studio tarafından bilinen bir konuma kopyalayarak dağıtılır. Bu işlem daha sonra bu kılavuzda daha ayrıntılı olarak açıklanmıştır.

1. İçinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , [temel bir proje sistemi oluşturun, 1. Bölüm '](../extensibility/creating-a-basic-project-system-part-1.md)ü Izleyerek oluşturduğunuz SimpleProject çözümünü açın.

2. *SimpleProjectPackage.cs* dosyasında ProvideProjectFactory özniteliğini bulun. İkinci parametreyi (proje adı) null ve dördüncü parametre (proje şablonu klasörünün yolu) ile değiştirin. \\ \NullPath ", aşağıdaki gibi.

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

    ![Basit Proje klasörü](../extensibility/media/simpproj2.png "SimpProj2")

    Bu \<TemplateData> bölüm, **Yeni proje** Iletişim kutusundaki SimpleProject proje türünün konumunu ve görünümünü aşağıdaki gibi belirler:

- \<Name>Öğesi, proje şablonunu SimpleProject uygulaması olacak şekilde adlandırır.

- \<Description>Öğesi, proje şablonu seçildiğinde **Yeni proje** iletişim kutusunda görünen açıklamayı içerir.

- \<Icon>Öğesi, SimpleProject proje türü ile birlikte görünen simgeyi belirtir.

- \<ProjectType>Öğesi, proje türünü **Yeni proje** iletişim kutusunda adlandırır. Bu ad ProvideProjectFactory özniteliğinin proje adı parametresinin yerini alır.

  > [!NOTE]
  > \<ProjectType>Öğe, `LanguageVsTemplate` SimpleProjectPackage.cs dosyasındaki özniteliğin bağımsız değişkeniyle eşleşmelidir `ProvideProjectFactory` .

  \<TemplateContent>Bu bölümde, yeni bir proje oluşturulduğunda oluşturulan dosyalar açıklanmaktadır:

- *SimpleProject. myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Tüm üç dosya `ReplaceParameters` true olarak ayarlanmıştır, bu da parametre değişimini sağlar. *Program.cs* dosyası `OpenInEditor` true olarak ayarlanmıştır, bu, bir proje oluşturulduğunda dosyanın kod düzenleyicisinde açılmasına neden olur.

  Visual Studio şablon şeması içindeki öğeler hakkında daha fazla bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Projede birden fazla Visual Studio şablonu varsa, her şablon ayrı bir klasörde bulunur. Bu klasördeki her dosya **derleme eyleminin** **ZipProject** olarak ayarlanmış olması gerekir.

## <a name="adding-a-minimal-vsct-file"></a>En az bir. vsct dosyası ekleme
 Yeni veya değiştirilmiş bir Visual Studio şablonunu tanımak için Visual Studio 'nun kurulum modunda çalıştırılması gerekir. Kurulum modu, var olan bir *. vsct* dosyası gerektirir. Bu nedenle, projeye en az bir *. vsct* dosyası eklemeniz gerekir.

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

    5. SimpleProject düğümünü kaydedin ve sonra **Çözüm Gezgini** **projeyi yeniden yükle**' ye tıklayın.

## <a name="examine-the-visual-studio-template-build-steps"></a>Visual Studio şablonu derleme adımlarını inceleyin
 VSPackage proje derleme sistemi genellikle *. vstemplate* dosyası değiştirildiğinde veya *. vstemplate* dosyasını Içeren proje yeniden oluşturulduğunda Visual Studio 'yu kurulum modunda çalıştırır. MSBuild 'in ayrıntı düzeyini normal veya daha yükseğe ayarlayarak da izleyebilirsiniz.

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Projeler ve çözümler** düğümünü genişletin ve ardından **Oluştur ve Çalıştır**' ı seçin.

3. **MSBuild proje derlemesi çıkış ayrıntı düzeyini** **normal** olarak ayarlayın. **Tamam** düğmesine tıklayın.

4. SimpleProject projesini yeniden derleyin.

    *. Zip* proje dosyası oluşturmak için derleme adımı aşağıdaki örneğe benzemelidir.

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
Visual Studio şablonları yol bilgilerini içermez. Bu nedenle, template *. zip* dosyası Visual Studio tarafından bilinen bir konuma dağıtılmalıdır. ProjectTemplates klasörünün konumu genellikle *% LocalAppData% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates<*.

Proje fabrikasını dağıtmak için, yükleme programının yönetici ayrıcalıklarına sahip olması gerekir. Visual Studio yükleme düğümü altında Şablonlar dağıtır: *. ..\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Visual Studio şablonunu test etme
Visual Studio şablonunu kullanarak proje hiyerarşisi oluşturup oluşturmadığını görmek için proje fabrikasını test edin.

1. Visual Studio SDK Deneysel örneğini sıfırlayın.

    Açık [!INCLUDE[win7](../debugger/includes/win7_md.md)] : **başlat** menüsünde **Microsoft Visual Studio/Microsoft Visual Studio SDK/araçları** klasörünü bulun ve **Microsoft Visual Studio deneysel örneği Sıfırla**' yı seçin.

    Windows 'un sonraki sürümlerinde: **Başlangıç** ekranında **Microsoft Visual Studio \<version> deneysel örneği Sıfırla** yazın.

2. Bir komut istemi penceresi görüntülenir. **Devam etmek için herhangi bir tuşa basın** sözcüklerini gördüğünüzde, **ENTER**' a tıklayın. Pencere kapandıktan sonra Visual Studio 'Yu açın.

3. SimpleProject projesini yeniden oluşturun ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

4. Deneysel örnekte, bir SimpleProject projesi oluşturun. **Yeni proje** iletişim kutusunda, **SimpleProject**' i seçin.

5. SimpleProject 'in yeni bir örneğini görmeniz gerekir.

    ![Basit proje yeni örnek](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Projem yeni örnek](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Proje türü alt düğümü oluştur
**Yeni proje** iletişim kutusunda bir proje türü düğümüne alt düğüm ekleyebilirsiniz. Örneğin, SimpleProject proje türü için konsol uygulamaları, pencere uygulamaları, Web uygulamaları vb. için alt düğümlere sahip olabilirsiniz.

Alt düğümler, proje dosyasını değiştirerek ve öğelere alt öğe ekleyerek oluşturulur \<OutputSubPath> \<ZipProject> . Bir şablon, derleme veya dağıtım sırasında kopyalandığında, her alt düğüm proje şablonları klasörünün bir alt klasörü haline gelir.

Bu bölümde, SimpleProject proje türü için bir konsol alt düğümünün nasıl oluşturulacağı gösterilmektedir.

1. *\\ Templates\projeleri SimpleProject \\* klasörünü *\\ templates\projelerconsoleapp \\* olarak yeniden adlandırın.

2. **Özellikler** penceresinde, *\\ templates\projeler, \\* \ Windows \ uygulama klasöründeki beş dosyayı seçin ve **Build eyleminin** **ZipProject** olarak ayarlandığından emin olun.

3. SimpleProject. vstemplate dosyasında, \<TemplateData> kapanış etiketinden hemen önce, bölümünün sonuna aşağıdaki satırı ekleyin.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Bu, konsol uygulama şablonunun hem konsol alt düğümünde hem de alt düğümün üzerinde bir düzey olan SimpleProject üst düğümünde görünmesine neden olur.

4. *SimpleProject. vstemplate* dosyasını kaydedin.

5. *. Csproj* dosyasında, \<OutputSubPath> ZipProject öğelerinin her birine ekleyin. Projeyi daha önce olduğu gibi kaldırın ve proje dosyasını düzenleyin.

6. Öğeleri bulun \<ZipProject> . Her \<ZipProject> öğe için bir öğe ekleyin \<OutputSubPath> ve değer konsolu 'na verin. ZipProject

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

## <a name="test-the-project-type-child-node"></a>Proje türü alt düğümünü test etme
**Konsol** alt düğümünün **Yeni proje** iletişim kutusunda görünüp görüntülenmediğini görmek için değiştirilen proje dosyasını test edin.

1. **Microsoft Visual Studio deneysel örnek aracını Sıfırla** ' yı çalıştırın.

2. SimpleProject projesini yeniden oluşturun ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir

3. **Yeni proje** Iletişim kutusunda **SimpleProject** düğümüne tıklayın. **Konsol uygulaması** şablonu **Şablonlar** bölmesinde görünmelidir.

4. **SimpleProject** düğümünü genişletin. **Konsol** alt düğümü görünmelidir. **SimpleProject uygulama** şablonu, **Şablonlar** bölmesinde görünmeye devam eder.

5. **İptal** ' e tıklayın ve hata ayıklamayı durdurun.

    ![Basit proje paketi](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Basit proje konsol düğümü](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Proje şablonu parametrelerini değiştir
- [Temel proje sistemi oluşturma, 1. bölüm,](../extensibility/creating-a-basic-project-system-part-1.md) `ProjectNode.AddFileFromTemplate` temel tür bir şablon parametresi değiştirme yöntemi için yöntemin üzerine yazmayı gösterdi. Bu bölüm, daha karmaşık Visual Studio şablon parametrelerinin nasıl kullanılacağını öğretir.

**Yeni proje** iletişim kutusunda bir Visual Studio şablonu kullanarak bir proje oluşturduğunuzda, proje özelleştirmek için şablon parametrelerinin yerine dizeler kullanılır. Şablon parametresi, bir dolar işaretiyle başlayan ve biten özel bir belirteçtir; Örneğin, $time $. Aşağıdaki iki parametre, şablonu temel alan projelerde özelleştirmeyi etkinleştirmek için özellikle yararlıdır:

- $GUID [1-10] $, yeni bir GUID ile değiştirilmiştir. En fazla 10 benzersiz GUID belirtebilirsiniz, örneğin $guid $1.

- $safeprojectname $, **Yeni proje** iletişim kutusunda bir kullanıcı tarafından belirtilen addır ve tüm güvenli olmayan karakterleri ve boşlukları kaldırmak için değiştirilir.

  Şablon parametrelerinin tüm listesi için bkz. [şablon parametreleri](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Proje şablonu parametrelerini koymak için

1. *SimpleProjectNode.cs* dosyasında, `AddFileFromTemplate` yöntemini kaldırın.

2. *\\ Templates\projeleri\simpleproject\ myproj* dosyasında, \<RootNamespace> özelliğini bulun ve değerini $safeprojectname $ olarak değiştirin.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. *\\ Templates\projeler\simpleproject\program.cs* dosyasında, dosyanın içeriğini aşağıdaki kodla değiştirin:

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

4. SimpleProject projesini yeniden oluşturun ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

5. Yeni bir SimpleProject konsol uygulaması oluşturun. ( **Proje türleri** bölmesinde, **SimpleProject**' i seçin. **Visual Studio yüklü şablonlar** altında **konsol uygulaması**' nı seçin.)

6. Yeni oluşturulan projede, *program.cs*' yi açın. Aşağıdaki gibi görünmelidir (dosyanızdaki GUID değerleri farklı olur.):

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
Kullanıcıların şablonunuzu temel alan projelerde özellikleri görüntülemesi ve değiştirebilmeleri için, proje türü için bir özellik sayfası oluşturabilirsiniz. Bu bölümde, bir yapılandırma bağımsız Özellik sayfasının nasıl oluşturulacağı gösterilmektedir. Bu temel özellik sayfası, özellik sayfası sınıfında kullanıma sunabileceğiniz ortak özellikleri göstermek için bir Özellikler Kılavuzu kullanır.

Özellik sayfası sınıfınızı temel sınıftan türetirsiniz `SettingsPage` . Sınıfı tarafından sunulan Özellikler Kılavuzu, `SettingsPage` en basit veri türlerinin farkındadır ve bunların nasıl görüntüleneceğini bilir. Buna ek olarak, `SettingsPage` sınıfı özellik değerlerini proje dosyasına nasıl kalıcı hale getireceğini bilir.

Bu bölümde oluşturduğunuz Özellik sayfası bu proje özelliklerini değiştirmenizi ve kaydetmenizi sağlar:

- AssemblyName

- #B2

- RootNamespace.

1. *SimpleProjectPackage.cs* dosyasında bu `ProvideObject` özniteliği `SimpleProjectPackage` sınıfa ekleyin:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Bu, özellik sayfası sınıfını `GeneralPropertyPage` com ile kaydeder.

2. *SimpleProjectNode.cs* dosyasında, bu iki geçersiz kılınan yöntemi `SimpleProjectNode` sınıfına ekleyin:

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

    Bu yöntemlerin her ikisi de özellik sayfası GUID 'Lerinin bir dizisini döndürür. GeneralPropertyPage GUID 'SI dizideki tek öğedir, bu nedenle **Özellik sayfaları** iletişim kutusu yalnızca bir sayfa gösterir.

3. SimpleProject projesine *GeneralPropertyPage.cs* adlı bir sınıf dosyası ekleyin.

4. Bu dosyanın içeriğini aşağıdaki kodu kullanarak değiştirin:

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

    `GeneralPropertyPage`Sınıfı, AssemblyName, OutputType ve RootNamespace üç ortak özelliğini kullanıma sunar. AssemblyName bir set yöntemi içermediğinden, salt okunurdur özelliği olarak görüntülenir. OutputType, numaralandırılmış bir sabittir, bu nedenle açılan liste olarak görünür.

    `SettingsPage`Temel sınıf `ProjectMgr` , özellikleri kalıcı hale getirmek için sağlar. `BindProperties`Yöntemi, `ProjectMgr` kalıcı özellik değerlerini almak ve karşılık gelen özellikleri ayarlamak için kullanır. `ApplyChanges`Yöntemi, `ProjectMgr` özelliklerin değerlerini almak ve bunları proje dosyasında kalıcı hale getirmek için kullanır. Özellik kümesi yöntemi, `IsDirty` özelliklerin kalıcı olması gerektiğini belirtmek için true olarak ayarlanır. Kalıcılık, projeyi veya çözümü kaydettiğinizde oluşur.

5. SimpleProject çözümünü yeniden oluşturun ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

6. Deneysel örnekte, yeni bir SimpleProject uygulaması oluşturun.

7. Visual Studio, Visual Studio şablonunu kullanarak proje oluşturmak için proje fabrikanızı çağırır. Yeni *program.cs* dosyası kod düzenleyicisinde açılır.

8. **Çözüm Gezgini**' de proje düğümüne sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Özellik Sayfaları** iletişim kutusu görüntülenir.

    ![Basit proje özellik sayfası](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Proje özellik sayfasını test etme
Artık özellik değerlerini değiştirip değiştirip değiştiremeyeceğinizi test edebilirsiniz.

1. **Myconsoleapplication Özellik sayfaları** iletişim kutusunda, **DefaultNamespace** öğesini **MyApplication** olarak değiştirin.

2. **OutputType** özelliğini seçin ve ardından **sınıf kitaplığı**' nı seçin.

3. **Uygula**' ya ve ardından **Tamam**' a tıklayın.

4. **Özellik sayfaları** iletişim kutusunu yeniden açın ve değişikliklerinizin kalıcı olduğunu doğrulayın.

5. Visual Studio 'nun Deneysel örneğini kapatın.

6. Deneysel örneği yeniden açın.

7. **Özellik sayfaları** iletişim kutusunu yeniden açın ve değişikliklerinizin kalıcı olduğunu doğrulayın.

8. Visual Studio 'nun Deneysel örneğini kapatın.
    ![Deneysel örneği Kapat](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
