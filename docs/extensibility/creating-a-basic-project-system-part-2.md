---
title: Temel Proje Sistemi Oluşturma, Bölüm 2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739716"
---
# <a name="create-a-basic-project-system-part-2"></a>Temel bir proje sistemi oluşturma, bölüm 2
Bu serinin ilk walkthrough, [temel bir proje sistemi oluşturun, bölüm 1](../extensibility/creating-a-basic-project-system-part-1.md), nasıl temel bir proje sistemi oluşturmak için gösterir. Bu gözden geçirme, Visual Studio şablonu, özellik sayfası ve diğer özellikler ekleyerek temel proje sistemi üzerine inşa edilmiştir. Bu işe başlamadan önce ilk walkthrough tamamlamanız gerekir.

Bu walkthrough nasıl proje dosya adı uzantısı *.myproj*olan bir proje türü oluşturmak için öğretir. Gözden geçirme yi tamamlamak için, iznin varolan Visual C# proje sisteminden ödünç aldığı için kendi dilinizi oluşturmanız gerekmez.

Bu gözden geçirme, bu görevleri nasıl yerine getirilen öğretir:

- Visual Studio şablonu oluşturun.

- Visual Studio şablonu dağıtın.

- **Yeni Proje** iletişim kutusunda proje türü alt düğüm oluşturun.

- Visual Studio şablonunda parametre değiştirmesini etkinleştirin.

- Proje özelliği sayfası oluşturun.

> [!NOTE]
> Bu gözden geçirme deki adımlar bir C# projesine dayanır. Ancak, dosya adı uzantıları ve kod gibi ayrıntılar dışında, Visual Basic projesi için aynı adımları kullanabilirsiniz.

## <a name="create-a-visual-studio-template"></a>Visual Studio şablonu oluşturma
- [Temel bir proje sistemi oluşturun, bölüm 1](../extensibility/creating-a-basic-project-system-part-1.md) temel bir proje şablonu oluşturmak ve proje sistemine eklemek nasıl gösterir. Ayrıca, sistem kayıt defterinde <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> * \\Şablonlar\Projeler\SimpleProject\\ * klasörünün tam yolunu yazan özniteliği kullanarak bu şablonu Visual Studio'ya nasıl kaydedilen gösterir.

Temel proje şablonu yerine Visual Studio şablonu *(.vstemplate* dosyası) kullanarak, şablonun **Yeni Proje** iletişim kutusunda nasıl görünebileceğini ve şablon parametrelerinin nasıl değiştirilmesini denetleyebilirsiniz. *.vstemplate* dosyası, proje sistemi şablonu kullanılarak bir proje oluşturulduğunda kaynak dosyaların nasıl dahil edilebildiğini açıklayan bir XML dosyasıdır. Proje sisteminin kendisi *.vstemplate* dosyasını ve kaynak dosyaları bir *.zip* dosyasında toplayarak oluşturulur ve *.zip* dosyasını Visual Studio tarafından bilinen bir konuma kopyalayarak dağıtılır. Bu işlem daha sonra bu izlenme sürecinde daha ayrıntılı olarak açıklanır.

1. ' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [de, temel bir proje sistemi oluştur'u, bölüm 1'i](../extensibility/creating-a-basic-project-system-part-1.md)izleyerek oluşturduğunuz SimpleProject çözümlerini açın.

2. *SimpleProjectPackage.cs* dosyasında, ProvideProjectFactory özniteliğini bulun. İkinci parametreyi (proje adı) null ile, dördüncü parametreyi (proje şablonu klasörüne giden yol) "ile değiştirin. \\\NullPath", aşağıdaki gibi.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. * \\Şablonlar\Projeler\SimpleProject\\ * klasörüne *SimpleProject.vstemplate* adlı bir XML dosyası ekleyin.

4. *SimpleProject.vstemplate* içeriğini aşağıdaki kodla değiştirin.

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

5. **Özellikler** penceresinde, * \\Şablonlar\Projeler\SimpleProject\\ * klasöründeki beş dosyanın tümünü seçin ve Eylem **Oluştur'u ZipProject**olarak ayarlayın. **Build Action**

    ![Basit Proje Klasörü](../extensibility/media/simpproj2.png "SimpProj2")

    TemplateData> bölümü, Yeni Proje iletişim kutusundaki SimpleProject proje türünün konumunu ve görünümünü aşağıdaki gibi belirler: **New Project** \<

- \<Ad> öğesi, proje şablonuna SimpleProject Uygulaması olarak adlandırır.

- Açıklama \<> öğesi, proje şablonu seçildiğinde **Yeni Proje** iletişim kutusunda görünen açıklamayı içerir.

- \<Simge> öğesi, SimpleProject proje türüyle birlikte görünen simgeyi belirtir.

- \<ProjectType> **öğesi, Yeni Proje** iletişim kutusunda Proje türünü adlandırır. Bu ad, ProjectFactory özniteliğinin proje adı parametresinin yerini alır.

  > [!NOTE]
  > \<ProjectType> öğesi, `LanguageVsTemplate` SimpleProjectPackage.cs dosyasındaki öznitelik bağımsız değişkenini `ProvideProjectFactory` eşleştirmelidir.

  TemplateContent> bölümü, \<yeni bir proje oluşturulduğunda oluşturulan bu dosyaları açıklar:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Her üç `ReplaceParameters` dosya da parametre değiştirme sağlayan doğru ayarlanmıştır. *Program.cs* dosyası `OpenInEditor` doğru olarak ayarlanmıştır ve bu da bir proje oluşturulduğunda dosyanın kod düzenleyicisinde açılmasına neden olur.

  Visual Studio Template şemasındaki öğeler hakkında daha fazla bilgi için [Visual Studio şablon şeması referansına](../extensibility/visual-studio-template-schema-reference.md)bakın.

> [!NOTE]
> Bir projede birden fazla Visual Studio şablonu varsa, her şablon ayrı bir klasördedir. Bu klasördeki her dosya, **Oluşturma Eylemi'ni** **ZipProject**olarak ayarlamış olmalıdır.

## <a name="adding-a-minimal-vsct-file"></a>En az .vsct dosyası ekleme
 Visual Studio, yeni veya değiştirilmiş bir Visual Studio şablonunu tanımak için kurulum modunda çalıştırılmalıdır. Kurulum modunun bulunması için *.vsct* dosyası gerekir. Bu nedenle, projeye en az *.vsct* dosyası eklemeniz gerekir.

1. SimpleProject projesine *SimpleProject.vsct* adlı bir XML dosyası ekleyin.

2. *SimpleProject.vsct* dosyasının içeriğini aşağıdaki kodla değiştirin.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Bu dosyanın **Yapı Eylemini** **VSCTCompile**olarak ayarlayın. Bunu yalnızca *.csproj* dosyasında yapabilirsiniz, **Özellikler** penceresinde değil. Bu dosyanın **Yapı Eylemi'nin** bu noktada **Yok** olarak ayarlandıklarından emin olun.

    1. SimpleProject düğümsağ tıklayın ve sonra **SimpleItProject.csproj edit**tıklatın.

    2. *.csproj* dosyasında *SimpleProject.vsct* öğesini bulun.

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Yapı eylemini **VSCTCompile olarak değiştirin.**

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. proje dosyası ve düzenleyicikapatın.

    5. SimpleProject düğümkaydet ve ardından **Çözüm Gezgini'nde** **Project'i Yeniden Yükle'yi**tıklatın.

## <a name="examine-the-visual-studio-template-build-steps"></a>Visual Studio şablon oluşturma adımlarını inceleyin
 VSPackage proje oluşturma sistemi genellikle *.vstemplate* dosyası değiştirildiğinde veya *.vstemplate* dosyasını içeren proje yeniden oluşturulunca Visual Studio'yu kurulum modunda çalıştırır. MSBuild'in ayrıntılı düzeyini Normal veya daha yüksek olarak ayarlayarak takip edebilirsiniz.

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. Projeler **ve Çözümler** düğümünü genişletin ve ardından **Yap ve Çalıştır'ı**seçin.

3. **MSBuild projesi oluşturma çıkış ayrıntılılığını** **Normal'e**ayarlayın. **Tamam**'a tıklayın.

4. SimpleProject projesini yeniden oluştur.

    *.zip* proje dosyasını oluşturmak için yapı adımı aşağıdaki örneğe benzemelidir.

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
Visual Studio şablonları yol bilgilerini içermez. Bu nedenle, şablon *.zip* dosyası Visual Studio tarafından bilinen bir konuma dağıtılmalıdır. ProjectTemplates klasörünün konumu genellikle *%<'>%LOCALAPPDATA\>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates'tir.*

Proje fabrikanızı dağıtmak için yükleme programının yönetici ayrıcalıklarına sahip olması gerekir. Visual Studio yükleme düğümü altında şablonları dağıtır: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Visual Studio şablonu test edin
Visual Studio şablonunu kullanarak proje hiyerarşisi oluşturup oluşturmadığını görmek için proje fabrikanızı test edin.

1. Visual Studio SDK deneysel örneğini sıfırla.

    Açık [!INCLUDE[win7](../debugger/includes/win7_md.md)]: **Başlat** menüsünde, **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** klasörünü bulun ve ardından **Microsoft Visual Studio Deneme örneğini Sıfırla'yı**seçin.

    Windows'un sonraki sürümlerinde: **Başlangıç** **ekranında, Microsoft \<Visual Studio sürümünü> Deneysel Örnek'i sıfırla**yazın.

2. Komut istemi penceresi görüntülenir. Devam **etmek için herhangi bir tuşa basın**sözcüklerini gördüğünüzde **ENTER'u**tıklatın. Pencere kapandıktan sonra Visual Studio'yu açın.

3. SimpleProject projesini yeniden oluşturve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

4. Deneysel örnekte, bir SimpleProject projesi oluşturun. Yeni **Proje** iletişim kutusunda **SimpleProject'i**seçin.

5. SimpleProject'in yeni bir örneğini görmeniz gerekir.

    ![Basit Proje Yeni Örnek](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Projem Yeni Örneği](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Proje türü alt düğüm oluşturma
**Yeni Proje** iletişim kutusundaproje türü düğümüne bir alt düğüm ekleyebilirsiniz. Örneğin, SimpleProject proje türü için konsol uygulamaları, pencere uygulamaları, web uygulamaları ve benzeri için alt düğümler olabilir.

Alt düğümler proje dosyasını değiştirerek ve \< \<ZipProject> öğelerine> ÇıktıSubPath ekleyerek oluşturulur. Bir şablon oluşturma veya dağıtım sırasında kopyalandığında, her alt düğüm proje şablonları klasörünün bir alt klasörü olur.

Bu bölümde, SimpleProject proje türü için konsol alt düğümü nasıl oluşturulacak gösterilmektedir.

1. * \\Şablonlar\Projeler\SimpleProject\\ * klasörünü * \\Şablonlar\Projeler\ConsoleApp\\*olarak yeniden adlandırın.

2. **Özellikler** penceresinde, * \\Şablonlar\Projeler\ConsoleApp\\ * klasöründeki beş dosyanın tümünü seçin ve **Yapı Eylemi'nin** **ZipProject**olarak ayarlandıklarından emin olun.

3. SimpleProject.vstemplate dosyasında, kapanış etiketinden hemen önce \<TemplateData> bölümünün sonuna aşağıdaki satırı ekleyin.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Bu, Konsol Uygulaması şablonunun hem Konsol alt düğümünde hem de alt düğümden bir düzey üzerinde olan SimpleProject üst düğümünde görünmesine neden olur.

4. *SimpleProject.vstemplate* dosyasını kaydedin.

5. *.csproj* dosyasında, \<ZipProject öğelerinin her birine OutputSubPath> ekleyin. Projeyi daha önce olduğu gibi boşaltın ve proje dosyasını edin.

6. ZipProject \<> öğelerini bulun. Her \<ZipProject> öğesi \<için, bir OutputSubPath> öğesi ekleyin ve değeri Konsol verin. The ZipProject

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

7. Bu \<Özellik Grubu> proje dosyasına ekleyin:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Proje dosyasını kaydedin ve projeyi yeniden yükleyin.

## <a name="test-the-project-type-child-node"></a>Proje türünü alt düğüm test edin
**Konsol** alt düğümünün **Yeni Proje** iletişim kutusunda görünüp görünmediğini görmek için değiştirilmiş proje dosyasını sınayın.

1. Microsoft **Visual Studio Deneme Örneği'ni Sıfırla aracını çalıştırın.**

2. SimpleProject projesini yeniden oluşturve hata ayıklamaya başlayın. Deneysel örnek görünmelidir

3. Yeni **Proje** iletişim kutusunda **SimpleProject** düğümlerini tıklatın. **Konsol Uygulaması** şablonu **Şablonlar** bölmesinde görünmelidir.

4. **SimpleProject** düğümlerini genişletin. **Konsol** alt düğümü görünmelidir. **SimpleProject Uygulaması** şablonu **Şablonlar** bölmesinde görünmeye devam eder.

5. **İptal'i** tıklatın ve hata ayıklamayı durdurun.

    ![Basit Proje Toplama](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Basit Proje Konsol Düğümü](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Yedek proje şablon parametreleri
- [Temel bir proje sistemi oluşturma, bölüm](../extensibility/creating-a-basic-project-system-part-1.md) 1 `ProjectNode.AddFileFromTemplate` şablon parametre ikame temel bir tür yapmak için yöntem üzerine nasıl gösterilmektedir. Bu bölümde, daha gelişmiş Visual Studio şablon parametrelerinin nasıl kullanılacağı öğretilir.

**Yeni Proje** iletişim kutusunda Görsel Stüdyo şablonu kullanarak bir proje oluşturduğunuzda, şablon parametreleri projeyi özelleştirmek için dizeleri ile değiştirilir. Şablon parametresi, örneğin $time$ gibi bir dolar işaretiyle başlayan ve biten özel bir belirteçtir. Aşağıdaki iki parametre, şablonu temel alan projelerde özelleştirmeyi etkinleştirmek için özellikle yararlıdır:

- $GUID[1-10]$ yeni bir Guid ile değiştirilir. Örneğin, 10 $guid$ kadar benzersiz GUID belirtebilirsiniz.

- $safeprojectname$, **Yeni Proje** iletişim kutusunda bir kullanıcı tarafından sağlanan ve tüm güvenli olmayan karakterleri ve boşlukları kaldırmak üzere değiştirilen addır.

  Şablon parametrelerinin tam listesi için [Şablon parametrelerine](../ide/template-parameters.md)bakın.

### <a name="to-substitute-project-template-parameters"></a>Proje şablon parametrelerini değiştirmek için

1. *SimpleProjectNode.cs* `AddFileFromTemplate` dosyasında, yöntemi kaldırın.

2. \< * \\Şablonlar\Projects\ConsoleApp\SimpleProject.myproj* dosyasında RootNamespace> özelliğini bulun ve değerini $safeprojectname$ olarak değiştirin.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. * \\Şablonlar\Projeler\BasitProject\Program.cs* dosyasında, dosyanın içeriğini aşağıdaki kodla değiştirin:

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

4. SimpleProject projesini yeniden oluşturve hata ayıklamaya başlayın. Deneysel örnek görünmelidir.

5. Yeni bir SimpleProject Console uygulaması oluşturun. (Proje **türleri** bölmesinde **SimpleProject'i**seçin. **Visual Studio yüklü şablonlar**altında Konsol **Uygulaması'nı**seçin .)

6. Yeni oluşturulan projede, açık *Program.cs.* Aşağıdaki gibi bir şey görünmelidir (dosyanızdaki GUID değerleri farklı olacaktır.):

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

## <a name="create-a-project-property-page"></a>Proje özelliği sayfası oluşturma
Kullanıcıların şablonunuza dayalı projelerdeki özellikleri görüntüleyebilmeleri ve değiştirebilmeleri için proje türünüz için bir özellik sayfası oluşturabilirsiniz. Bu bölümde, yapılandırmadan bağımsız bir özellik sayfası nasıl oluşturulabileceğiniz gösterilmektedir. Bu temel özellik sayfası, özellik sayfası sınıfınızda ortaya çıkardığınız ortak özellikleri görüntülemek için bir özellik ızgarası kullanır.

Özellik sayfası sınıfınızı taban `SettingsPage` sınıftan türetin. `SettingsPage` Sınıf tarafından sağlanan özellikler ızgarası en ilkel veri türlerinin farkındadır ve bunları nasıl görüntülenebildiğini bilir. Buna ek `SettingsPage` olarak, sınıf proje dosyasına özellik değerlerini nasıl devam e-zorlar biliyor.

Bu bölümde oluşturduğunuz özellik sayfası, bu proje özelliklerini değiştirmenize ve kaydetmenize olanak tanır:

- Assemblyname

- Çıktı Türü

- RootNamespace.

1. *SimpleProjectPackage.cs* dosyasında, bu `ProvideObject` özniteliği `SimpleProjectPackage` sınıfa ekleyin:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Bu, com ile `GeneralPropertyPage` özellik sayfası sınıfını kaydeder.

2. *SimpleProjectNode.cs* dosyasında, bu iki geçersiz yöntemi `SimpleProjectNode` sınıfa ekleyin:

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

    Bu yöntemlerin her ikisi de özellik sayfası GUIDs bir dizi döndürün. Genel Özellik Sayfası GUID dizideki tek öğedir, bu nedenle **Özellik Sayfaları** iletişim kutusu yalnızca bir sayfa gösterir.

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

    Sınıf `GeneralPropertyPage` üç ortak özellikleri AssemblyName, OutputType ve RootNamespace ortaya çıkarır. AssemblyName'de ayarlanan bir yöntem olmadığından, salt okunur özellik olarak görüntülenir. OutputType numaralandırılmış bir sabittir, bu nedenle açılır liste olarak görünür.

    `SettingsPage` Taban sınıf `ProjectMgr` özellikleri kalıcı sağlar. Yöntem, `BindProperties` `ProjectMgr` kalıcı özellik değerlerini almak ve ilgili özellikleri ayarlamak için kullanır. Yöntem, `ApplyChanges` `ProjectMgr` özelliklerin değerlerini almak ve bunları proje dosyasında kalıcı hale getirmek için kullanır. Özellik kümesi yöntemi, özelliklerin kalıcı olması gerektiğini belirtmek için doğru olarak ayarlar. `IsDirty` Projeyi veya çözümü kaydettiğinizde kalıcılık oluşur.

5. SimpleProject çözümlerini yeniden oluşturve hata ayıklamaya başlayın. Deneysel örnek görünmelidir.

6. Deneysel örnekte, yeni bir SimpleProject Uygulaması oluşturun.

7. Visual Studio, Visual Studio şablonunu kullanarak proje fabrikanızı bir proje oluşturmak için çağırır. Yeni *Program.cs* dosyası kod düzenleyicisinde açılır.

8. **Çözüm Gezgini'nde**proje düğümüne sağ tıklayın ve ardından **Özellikler'i**tıklatın. **Özellik Sayfaları** iletişim kutusu görüntülenir.

    ![Basit Proje Özellik Sayfası](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Proje özelliği sayfasını test edin
Artık özellik değerlerini değiştirip değiştiremeyeceğiniz ve değiştirip değiştiremeyeceğiniz konusunda sınanabilirsiniz.

1. **MyConsoleApplication Özellik Sayfaları** iletişim kutusunda, **VarsayılanName alanını** MyApplication olarak **değiştirin.**

2. **OutputType** özelliğini seçin ve ardından **Sınıf Kitaplığı'nı**seçin.

3. **Uygula'yı**tıklatın ve ardından **Tamam'ı**tıklatın.

4. **Özellik Sayfaları** iletişim kutusunu yeniden açın ve değişikliklerinizin devam ettiğini doğrulayın.

5. Visual Studio'nun deneysel örneğini kapatın.

6. Deneysel örneği yeniden açın.

7. **Özellik Sayfaları** iletişim kutusunu yeniden açın ve değişikliklerinizin devam ettiğini doğrulayın.

8. Visual Studio'nun deneysel örneğini kapatın.
    ![Deneme örneğini kapatma](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
