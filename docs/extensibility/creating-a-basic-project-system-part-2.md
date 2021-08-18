---
title: Temel Project Sistemi Oluşturma, Bölüm 2 | Microsoft Docs
description: Önceki makalede oluşturulan bir projeye Visual Studio şablon, özellik sayfası ve diğer özellikleri nasıl ekleyebilirsiniz?
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
ms.openlocfilehash: 4aa62227051b68307c0bb4ab301a218d8e535461
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058025"
---
# <a name="create-a-basic-project-system-part-2"></a>Temel proje sistemi oluşturma, bölüm 2
Bu serinin ilk izlenecek yolu olan Temel bir [proje sistemi oluşturma, bölüm 1,](../extensibility/creating-a-basic-project-system-part-1.md)temel bir proje sisteminin nasıl oluşturulacaklarını gösterir. Bu izlenecek yol, temel proje sistemi üzerinde temel bir Visual Studio şablonu, özellik sayfası ve diğer özellikleri ekler. Bunu başlatmadan önce ilk izlenecek yolu tamamlamanız gerekir.

Bu kılavuzda, .myproj proje dosya adı uzantısına sahip bir proje türünün *nasıl oluşturularak ilgili bilgi veresin.* Bu izlenecek yolu tamamlamak için kendi dilinizi oluşturmanıza gerek yok çünkü izlenecek yol mevcut Visual C# proje sisteminden ödünç alınıyor.

Bu kılavuzda, bu görevlerin nasıl yerine ulaşacağız öğretildi:

- Yeni bir Visual Studio oluşturun.

- Bir Visual Studio dağıtın.

- Yeni Uygulama iletişim kutusunda proje türü **alt Project** oluşturun.

- Uygulama şablonunda parametre değiştirme Visual Studio etkinleştirin.

- Proje özellik sayfası oluşturun.

> [!NOTE]
> Bu kılavuzda yer alan adımlar bir C# projesine dayalıdır. Ancak, dosya adı uzantıları ve kod gibi özeller dışında, bir proje için aynı adımları Visual Basic kullanabilirsiniz.

## <a name="create-a-visual-studio-template"></a>Visual Studio şablonu oluşturma
- [Temel bir proje sistemi oluşturma, 1.](../extensibility/creating-a-basic-project-system-part-1.md) bölüm, temel bir proje şablonunun nasıl oluşturularak proje sistemine ekliln olduğunu gösterir. Ayrıca, sistem kayıt defterinde <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> *\\ Templates\Projects\SimpleProject \\* klasörünün tam yolunu yazan özniteliğini kullanarak bu şablonu Visual Studio'a kaydetmeyi de gösterir.

Temel bir Visual Studio şablonu yerine bir Visual Studio şablonu *(.vstemplate* dosyası) kullanarak, şablonun **Yeni** Project iletişim kutusunda nasıl görüntülendiğinden ve şablon parametrelerinin yerinin nasıl değiştirilir? *.vstemplate* dosyası, proje sistem şablonu kullanılarak bir proje oluşturulduğunda kaynak dosyaların nasıl dahil edileceklerini açıklayan bir XML dosyasıdır. Proje sistemi, *.vstemplate* dosyasını ve kaynak dosyaları bir *.zip* dosyasında toplayarak ve *.zip* dosyası tarafından bilinen bir konuma kopyalayarak Visual Studio. Bu işlem, bu kılavuzda daha sonra daha ayrıntılı olarak açıklanmaktadır.

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'de, Temel proje sistemi oluşturma bölümünü [1'i](../extensibility/creating-a-basic-project-system-part-1.md)takip eden SimpleProject çözümünü açın.

2. *SimpleProjectPackage.cs* dosyasında ProvideProjectFactory özniteliğini bulun. İkinci parametreyi (proje adı) null, dördüncü parametreyi (proje şablonu klasörünün yolu) ise " ile değiştirin. \\ \NullPath", aşağıdaki gibi.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. *\\ Templates\Projects\SimpleProject \\* *klasörüne SimpleProject.vstemplate* adlı bir XML dosyası ekleyin.

4. *SimpleProject.vstemplate içeriğini* aşağıdaki kodla değiştirin.

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

5. Özellikler **penceresinde** *\\ Templates\Projects\SimpleProject \\* klasöründeki beş dosyanın hepsini seçin ve **Derleme** Eylemi'nin **ZipProject olarak ayarlayın.**

    ![Basit Project Klasörü](../extensibility/media/simpproj2.png "SimpProj2")

    bölümü, New Project iletişim kutusundaki \<TemplateData> SimpleProject proje **türünün konumunu ve görünümünü** aşağıdaki gibi belirler:

- öğesi, \<Name> proje şablonunu SimpleProject Application olarak adlar.

- \<Description>öğesi, proje şablonu seçildiğinde **Yeni** Project iletişim kutusunda görünen açıklamayı içerir.

- \<Icon>öğesi SimpleProject proje türüyle birlikte görüntülenen simgeyi belirtir.

- Öğesi, \<ProjectType> Yeni Project iletişim kutusunda  Project olarak adlar. Bu ad, ProvideProjectFactory özniteliğinin proje adı parametresinin yerini almaktadır.

  > [!NOTE]
  > öğesi \<ProjectType> `LanguageVsTemplate` `ProvideProjectFactory` SimpleProjectPackage.cs dosyasındaki özniteliğinin bağımsız değişkeniyle eşleşmeli.

  bölümünde, \<TemplateContent> yeni bir proje oluşturulduğunda oluşturulan şu dosyalar açıklandı:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Üç dosyanın da `ReplaceParameters` parametre değiştirmeyi sağlayan true değerine ayarlanmıştır. *Program.cs* dosyası true olarak ayarlanmıştır ve bu da proje oluşturulduğunda dosyanın `OpenInEditor` kod düzenleyicisinde açılmasına neden olur.

  Visual Studio Şablonu şemasında öğeler hakkında daha fazla bilgi için [bkz. Visual Studio şema başvurusu.](../extensibility/visual-studio-template-schema-reference.md)

> [!NOTE]
> Bir projede birden fazla Visual Studio şablon varsa, her şablon ayrı bir klasördedir. Bu klasördeki her dosyanın Derleme Eylemi **ZipProject olarak ayarlanmış olması gerekir.** 

## <a name="adding-a-minimal-vsct-file"></a>En az bir .vsct dosyası ekleme
 Visual Studio yeni veya değiştirilmiş bir şablonu tanımak için kurulum modunda Visual Studio gerekir. Kurulum modu bir *.vsct dosyasının* mevcut olması gerekir. Bu nedenle, projeye en az *bir .vsct* dosyası eklemeniz gerekir.

1. *SimpleProject projesine SimpleProject.vsct* adlı bir XML dosyası ekleyin.

2. *SimpleProject.vsct dosyasının içeriğini* aşağıdaki kodla değiştirin.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Bu **dosyanın Derleme** Eylemi'nin **VSCTCompile olarak ayarlayın.** Bunu, Özellikler penceresinde değil *yalnızca .csproj* **dosyasından yapabiliriz.** Bu dosyanın **Derleme Eylemi'nin** bu noktada Yok olarak **ayarlanmış** olduğundan emin olun.

    1. SimpleProject düğümüne sağ tıklayın ve ardından **SimpleProject.csproj'u Düzenle'ye tıklayın.**

    2. *.csproj dosyasında* *SimpleProject.vsct öğesini* bulun.

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Derleme eylemlerini **VSCTCompile olarak değiştirme.**

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. proje dosyasını açın ve düzenleyiciyi kapatın.

    5. SimpleProject düğümünü kaydedin ve ardından Çözüm Gezgini **Yeniden** **Yükle'ye** Project.

## <a name="examine-the-visual-studio-template-build-steps"></a>Şablon Visual Studio adımlarını inceleme
 VSPackage proje derleme sistemi genellikle *.vstemplate* dosyası Visual Studio veya *.vstemplate* dosyasını içeren proje yeniden değiştirilebilirken kurulum modunda çalışır. Bu adımları takip etmek için normal veya daha yüksek bir MSBuild düzeyine kadar devam edin.

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. Projeler ve **Çözümler düğümünü genişletin** ve ardından Derleme ve **Çalıştırma'ya seçin.**

3. Proje **MSBuild çıkışını Normal olarak** **ayarlayın.** **Tamam**'a tıklayın.

4. SimpleProject projesini yeniden oluşturma.

    .zipproje dosyasını *oluşturmak* için derleme adımı aşağıdaki örnekteki gibi olması gerekir.

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

## <a name="deploy-a-visual-studio-template"></a>Bir Visual Studio dağıtma
Visual Studio şablonları yol bilgisi içermez. Bu *nedenle,.zip* dosyası, dosyanın dağıtılacağı bilinen bir konuma Visual Studio. ProjectTemplates klasörünün konumu genellikle *<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates konumundadır.*

Proje fabrikanızı dağıtmak için yükleme programının yönetici ayrıcalıkları olmalıdır. Şablonları şu yükleme düğümü Visual Studio dağıtır: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Bir Visual Studio test
Proje fabrikanızı test etmek için proje şablonunu kullanarak bir proje hiyerarşisi Visual Studio bakın.

1. Visual Studio SDK deneysel örneğini sıfırlayın.

    üzerinde: [!INCLUDE[win7](../debugger/includes/win7_md.md)] Başlat **menüsünde** **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** klasörünü bulun ve Deneysel örneği **Microsoft Visual Studio'yi seçin.**

    Sonraki sürümlerde Windows: Başlangıç **ekranında** Deneysel Örneği **Microsoft Visual Studio \<version> yazın.**

2. Bir komut istemi penceresi görüntülenir. Devam etmek için herhangi bir **tuşa basın sözcüklerini gördüğünüzde** ENTER tuşuna **basın.** Pencere kapattıktan sonra Visual Studio.

3. SimpleProject projesini yeniden oluşturma ve hata ayıklamayı başlatma. Deneysel örnek görünür.

4. Deneysel örnekte bir SimpleProject projesi oluşturun. Yeni Proje **Project** Kutusunda **SimpleProject'i seçin.**

5. SimpleProject'in yeni bir örneğini görüyor gerekir.

    ![Basit Project Yeni Örnek](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![My Project New Instance](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Proje türü alt düğümü oluşturma
Yeni Düğümler iletişim kutusunda proje türü düğümüne bir **alt Project** eklemek için kullanabilirsiniz. Örneğin SimpleProject proje türü için konsol uygulamaları, pencere uygulamaları, web uygulamaları vb. için alt düğümleriniz olabilir.

Alt düğümler, proje dosyası değiştirerek ve öğelere \<OutputSubPath> alt öğe ekleyerek \<ZipProject> oluşturulur. Bir şablon derleme veya dağıtım sırasında kopyalanırsa, her alt düğüm proje şablonları klasörünün bir alt klasörü olur.

Bu bölümde SimpleProject proje türü için konsol alt düğümünün nasıl oluşturularak oluşturul açıklanabilir.

1. *\\ Templates\Projects\SimpleProject \\* klasörünü *\\ Templates\Projects\ConsoleApp \\ olarak yeniden adlandırabilirsiniz.*

2. Özellikler **penceresinde** *\\ Templates\Projects\ConsoleApp \\* klasöründeki beş dosyanın hepsini seçin  ve Derleme Eylemi'nin **ZipProject** olarak ayarlanmış olduğundan emin olun.

3. SimpleProject.vstemplate dosyasında, bölümün sonuna, kapanış etiketinin \<TemplateData> hemen öncesine aşağıdaki satırı ekleyin.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Bu, Konsol Uygulaması şablonunun hem Konsol alt düğümünde hem de alt düğümün bir düzeyi üzerindeki SimpleProject üst düğümünde görünmesine neden olur.

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
**konsol** alt düğümünün **yeni Project** iletişim kutusunda görünüp görüntülenmediğini görmek için değiştirilen proje dosyasını Test edin.

1. **Microsoft Visual Studio deneysel örnek aracını sıfırla** ' yı çalıştırın.

2. SimpleProject projesini yeniden oluşturun ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir

3. **yeni Project** iletişim kutusunda **simpleproject** düğümüne tıklayın. **Konsol uygulaması** şablonu **Şablonlar** bölmesinde görünmelidir.

4. **SimpleProject** düğümünü genişletin. **Konsol** alt düğümü görünmelidir. **SimpleProject uygulama** şablonu, **Şablonlar** bölmesinde görünmeye devam eder.

5. **İptal** ' e tıklayın ve hata ayıklamayı durdurun.

    ![basit Project toplaması](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![basit Project konsol düğümü](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Proje şablonu parametrelerini değiştir
- [Temel proje sistemi oluşturma, 1. bölüm,](../extensibility/creating-a-basic-project-system-part-1.md) `ProjectNode.AddFileFromTemplate` temel tür bir şablon parametresi değiştirme yöntemi için yöntemin üzerine yazmayı gösterdi. bu bölüm, daha gelişmiş Visual Studio şablonu parametrelerini kullanmayı öğretir.

**yeni Project** iletişim kutusunda bir Visual Studio şablonu kullanarak bir proje oluşturduğunuzda, proje özelleştirmek için şablon parametreleri dizeler ile değiştirilmiştir. Şablon parametresi, bir dolar işaretiyle başlayan ve biten özel bir belirteçtir; Örneğin, $time $. Aşağıdaki iki parametre, şablonu temel alan projelerde özelleştirmeyi etkinleştirmek için özellikle yararlıdır:

- $GUID [1-10] $, yeni bir GUID ile değiştirilmiştir. En fazla 10 benzersiz GUID belirtebilirsiniz, örneğin $guid $1.

- $safeprojectname $, **yeni Project** iletişim kutusunda bir kullanıcı tarafından belirtilen addır ve tüm güvenli olmayan karakterleri ve boşlukları kaldırmak için değiştirilir.

  Şablon parametrelerinin tüm listesi için bkz. [şablon parametreleri](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Proje şablonu parametrelerini koymak için

1. *SimpleProjectNode. cs* dosyasında, `AddFileFromTemplate` yöntemini kaldırın.

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

5. Yeni bir SimpleProject konsol uygulaması oluşturun. ( **Project türleri** bölmesinde, **simpleproject**' i seçin. **yüklü şablonlar Visual Studio** altında, **konsol uygulaması**' nı seçin.)

6. Yeni oluşturulan projede *program. cs*' yi açın. Aşağıdaki gibi görünmelidir (dosyanızdaki GUID değerleri farklı olur.):

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

1. *Simpleprojectpackage. cs* dosyasında bu `ProvideObject` özniteliği `SimpleProjectPackage` sınıfa ekleyin:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Bu, özellik sayfası sınıfını `GeneralPropertyPage` com ile kaydeder.

2. *SimpleProjectNode. cs* dosyasında, bu iki geçersiz kılınan yöntemi `SimpleProjectNode` sınıfına ekleyin:

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

3. SimpleProject projesine *GeneralPropertyPage. cs* adlı bir sınıf dosyası ekleyin.

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

7. Visual Studio, Visual Studio şablonunu kullanarak proje oluşturmak için proje fabrikanızı çağırır. Yeni *program. cs* dosyası kod düzenleyicisinde açılır.

8. **Çözüm Gezgini**' de proje düğümüne sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Özellik Sayfaları** iletişim kutusu görüntülenir.

    ![basit Project özellik sayfası](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Proje özellik sayfasını test etme
Artık özellik değerlerini değiştirip değiştirip değiştiremeyeceğinizi test edebilirsiniz.

1. **Myconsoleapplication Özellik sayfaları** iletişim kutusunda, **DefaultNamespace** öğesini **MyApplication** olarak değiştirin.

2. **OutputType** özelliğini seçin ve ardından **sınıf kitaplığı**' nı seçin.

3. **Uygula**' ya ve ardından **Tamam**' a tıklayın.

4. **Özellik sayfaları** iletişim kutusunu yeniden açın ve değişikliklerinizin kalıcı olduğunu doğrulayın.

5. Visual Studio Deneysel örneğini kapatın.

6. Deneysel örneği yeniden açın.

7. **Özellik sayfaları** iletişim kutusunu yeniden açın ve değişikliklerinizin kalıcı olduğunu doğrulayın.

8. Visual Studio Deneysel örneğini kapatın.
    ![Deneysel örneği Kapat](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
