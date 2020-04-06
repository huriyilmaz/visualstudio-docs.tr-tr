---
title: Temel Proje Sistemi Oluşturma, Bölüm 1 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739730"
---
# <a name="create-a-basic-project-system-part-1"></a>Temel bir proje sistemi oluşturma, bölüm 1
Visual Studio'da projeler, geliştiricilerin kaynak kodu dosyalarını ve diğer varlıkları düzenlemek için kullandıkları kapsayıcılardır. Projeler, **Çözüm Gezgini'ndeki**çözümlerin çocukları olarak görünür. Projeler, kaynak kodu düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza ve Web hizmetlerine, veritabanlarına ve diğer kaynaklara başvurular oluşturmanıza izin verir.

 Projeler proje dosyalarında tanımlanır, örneğin Visual C# projesi için *bir .csproj* dosyası. Kendi proje dosya adı uzantınıza sahip kendi proje türünü oluşturabilirsiniz. Proje türleri hakkında daha fazla bilgi için [Proje türlerine](../extensibility/internals/project-types.md)bakın.

> [!NOTE]
> Visual Studio'yu özel bir proje türüyle genişletmeniz gerekiyorsa, proje sistemini sıfırdan oluşturmanın bir takım avantajları na sahip olan [Visual Studio proje sisteminden](https://github.com/Microsoft/VSProjectSystem) (VSPS) yararlanmanızı şiddetle öneririz:
>
> - Uçağa binmedaha kolay.  Temel bir proje sistemi bile on binlerce kod satırı gerektirir.  VSPS'den yararlanmak, gereksinimlerinize göre özelleştirmeye hazır olmadan önce biniş maliyetini birkaç tıklamaya düşürür.
> - Daha kolay bakım.  VSPS'den yararlanarak yalnızca kendi senaryolarınızı korumanız gerekir.  Tüm proje sistemi altyapısının bakımını biz yönetiriz.
>
>   Visual Studio 2013'ten daha eski sürümlerini hedeflemeniz gerekiyorsa, Visual Studio uzantısında VSPS'den yararlanamazsınız.  Bu durumda, bu izbis başlamak için iyi bir yerdir.

 Bu gözden geçirme, proje dosya adı uzantısı *.myproj*olan bir proje türünü nasıl oluşturabileceğinizi gösterir. Bu gözden geçirme, varolan Visual C# proje sisteminden ödünç alınr.

> [!NOTE]
> Uzatma projelerine daha fazla örnek için [VSSDK örneklerine](https://github.com/Microsoft/VSSDK-Extensibility-Samples)bakın.

 Bu gözden geçirme, bu görevleri nasıl yerine getirilen öğretir:

- Temel bir proje türü oluşturun.

- Temel bir proje şablonu oluşturun.

- Proje şablonu Visual Studio'ya kaydolun.

- **Yeni Proje** iletişim kutusunu açıp şablonunuzu kullanarak bir proje örneği oluşturun.

- Proje sisteminiz için bir proje fabrikası oluşturun.

- Proje sisteminiz için bir proje düğümü oluşturun.

- Proje sistemi için özel simgeler ekleyin.

- Temel şablon parametre değiştirme uygulayın.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

 Ayrıca [projeler için Yönetilen Paket Çerçevesi için](https://github.com/tunnelvisionlabs/MPFProj10)kaynak kodunu indirmeniz gerekir. Dosyayı oluşturacağınız çözümiçin erişilebilir bir konuma ayıklayın.

## <a name="create-a-basic-project-type"></a>Temel proje türü oluşturma
 **SimpleProject**adında bir C# VSIX projesi oluşturun. (**Dosya** > **Yeni** > **Proje** ve sonra Görsel **C#** > **Genişletilebilirlik** > **VSIX Projesi**). Visual Studio Package proje öğesi şablonu ekleyin **(Çözüm Gezgini'nde,** proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin, ardından **Genişletilebilirlik** > **Görsel Stüdyo Paketi'ne**gidin). Dosyayı *SimpleProjectPackage*olarak adlandırın.

## <a name="creating-a-basic-project-template"></a>Temel proje şablonu oluşturma
 Şimdi, bu temel VSPackage'ı yeni *.myproj* proje türünü uygulamak için değiştirebilirsiniz. *.myproj* proje türünü temel alan bir proje oluşturmak için Visual Studio'nun yeni projeye ekleyeceğiniz dosyaları, kaynakları ve başvuruları bilmesi gerekiyor. Bu bilgileri sağlamak için proje dosyalarını proje şablonu klasörüne koyun. Bir kullanıcı bir proje oluşturmak için *.myproj* projesini kullandığında, dosyalar yeni projeye kopyalanır.

### <a name="to-create-a-basic-project-template"></a>Temel proje şablonu oluşturmak için

1. Projeye biri diğerinin altında olmak üzere üç klasör ekleyin: *Şablonlar\Projeler\BasitProject*. (Çözüm **Gezgini'nde** **SimpleProject** proje düğümüne sağ tıklayın, **Ekle'ye**işaret edin ve ardından **Yeni Klasör'ü**tıklatın. Klasör *şablonları*adlandırın. *Şablonlar* klasörüne Projeler *adlı*bir klasör ekleyin. *Projeler* klasörüne *SimpleProject*adlı bir klasör ekleyin .)

2. *Şablonlar\Projeler\SimpleProject* klasöründe, *SimpleProject.ico*adlı simge olarak kullanmak üzere bir Bitmap Image dosyası ekleyin. **Ekle'yi**tıklattığınızda simge düzenleyicisi açılır.

3. Simgeyi ayırt edici hale getirin. Bu simge daha sonra izlenecek yoldaki **Yeni Proje** iletişim kutusunda görünür.

    ![Basit Proje Simgesi](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Simgeyi kaydedin ve simge düzenleyicisini kapatın.

5. *Şablonlar\Projeler\SimpleProject* *klasörüne, Program.cs*adlı bir **Sınıf** öğesi ekleyin.

6. Varolan kodu aşağıdaki satırlarla değiştirin.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > Bu *Program.cs* kodun son şekli değildir; değiştirme parametreleri daha sonraki bir adımda ele alınacaktır. Derleme hataları görebilirsiniz, ancak dosyanın **BuildAction** **İçerik**olduğu sürece, projeyi her zamanki gibi oluşturup çalıştırabilmelisiniz.

7. Dosyayı kaydedin.

8. *AssemblyInfo.cs* dosyayı *Özellikler* klasöründen *Projeler\SimpleProject* klasörüne kopyalayın.

9. *Projeler\SimpleProject* klasöründe *SimpleProject.myproj*adlı bir XML dosyası ekleyin.

   > [!NOTE]
   > Bu türdeki tüm projeler için dosya adı uzantısı *.myproj'* dur. Değiştirmek istiyorsanız, gözden geçiricide bahsedilen her yerde değiştirmeniz gerekir.

10. Varolan içeriği aşağıdaki satırlarla değiştirin.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. Dosyayı kaydedin.

12. **Özellikler** penceresinde, *AssemblyInfo.cs,* *Program.cs*, *SimpleProject.ico*ve *SimpleProject.myproj* **to Content'in** **Yapı Eylemini** ayarlayın ve **VSIX** özelliklerine Uygun olarak dahil etme lerini **ayarlayın.**

    Bu proje şablonu, hem Hata Ayıklama yapılandırması hem de Sürüm yapılandırması olan temel bir Visual C# projesini açıklar. Proje iki kaynak dosyaları, *AssemblyInfo.cs* ve *Program.cs*ve birkaç derleme başvuruları içerir. Şablondan bir proje oluşturulduğunda, ProjectGuid değeri otomatik olarak yeni bir GUID ile değiştirilir.

    **Çözüm Gezgini'nde**genişletilmiş **Şablonlar** klasörü aşağıdaki gibi görünmelidir:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Temel bir proje fabrikası oluşturma
 Visual Studio'ya proje şablonklasörünüzün konumunu bildirmelisiniz. Bunu yapmak için, VSPackage oluşturulurken şablon konumunun sistem kayıt defterine yazılması için proje fabrikasını uygulayan VSPackage sınıfına bir öznitelik ekleyin. Bir proje fabrikası GUID tarafından tanımlanan temel bir proje fabrikası oluşturarak başlayın. Proje <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> fabrikasını `SimpleProjectPackage` sınıfa bağlamak için özniteliği kullanın.

### <a name="to-create-a-basic-project-factory"></a>Temel bir proje fabrikası oluşturmak için

1. Proje fabrikanız için GUID'ler oluşturun **(Araçlar** menüsünde **GUID Oluştur'u**tıklatın) veya aşağıdaki örnektekileri kullanın. GuiD'leri zaten `SimpleProjectPackage` tanımlanmış `PackageGuidString`olan bölümün yanındaki sınıfa ekleyin. GUID'ler hem GUID biçiminde hem de dize biçiminde olmalıdır. Ortaya çıkan kod aşağıdaki örneğe benzemelidir.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. *SimpleProjectFactory.cs*adlı en üst *SimpleProject* klasörüne bir sınıf ekleyin.

3. Yönergeleri kullanarak aşağıdakileri ekleyin:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. `SimpleProjectFactory` Sınıfa bir GUID özniteliği ekleyin. Özniteliğin değeri yeni proje fabrikası GUID'dir.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Artık proje şablonunuzu kaydedebilirsiniz.

### <a name="to-register-the-project-template"></a>Proje şablonuna kaydolmak için

1. SimpleProjectPackage.cs *SimpleProjectPackage.cs*olarak, <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> aşağıdaki gibi `SimpleProjectPackage` sınıfa bir öznitelik ekleyin.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Çözümü yeniden oluşturun ve hatasız oluşturduğunu doğrulayın.

    Yeniden oluşturma, proje şablonu kaydeder.

   Parametreler `defaultProjectExtension` ve `possibleProjectExtensions` proje dosya adı uzantısı (*.myproj*) ayarlanır. `projectTemplatesDirectory` Parametre *Şablonlar* klasörünün göreli yoluna ayarlanır. Yapı sırasında, bu yol tam bir yapıya dönüştürülür ve proje sistemini kaydetmek için kayıt defterine eklenir.

## <a name="test-the-template-registration"></a>Şablon kaydını test edin
 Şablon kaydı Visual Studio'ya proje şablonklasörünüzün konumunu söyler, böylece Visual Studio şablon adını ve simgesini **Yeni Proje** iletişim kutusunda görüntüleyebilir.

### <a name="to-test-the-template-registration"></a>Şablon kaydını test etmek için

1. Visual Studio'nun deneysel bir örneğini hata ayıklamaya başlamak için **F5** tuşuna basın.

2. Deneysel örnekte, yeni oluşturulan proje türüne ait yeni bir proje oluşturun. Yeni **Proje** iletişim kutusunda, **Yüklenilen şablonların**altındaki **SimpleProject'i** görmeniz gerekir.

   Şimdi kayıtlı bir proje fabrikanız var. Ancak, henüz bir proje oluşturamaz. Proje paketi ve proje fabrikası, bir proje oluşturmak ve başlatmak için birlikte çalışır.

## <a name="add-the-managed-package-framework-code"></a>Yönetilen Paket Çerçeve kodu ekleme
 Proje paketi ile proje fabrikası arasındaki bağlantıyı uygulayın.

- Yönetilen Paket Çerçevesi için kaynak kod dosyalarını içeri aktarın.

    1. SimpleProject projesini boşaltın **(Solution**Explorer'da, proje düğümünü seçin ve bağlam menüsünde **Projeyi Boşalt'ı**tıklatın .) ve XML düzenleyicisinde proje dosyasını açın.

    2. Proje dosyasına aşağıdaki blokları ekleyin (Alma> bloklarının \<hemen üstüne). Az `ProjectBasePath` önce indirdiğiniz Yönetilen Paket Çerçeve kodundaki *ProjectBase.files* dosyasının konumuna ayarlayın. Yol adına bir ters eğik çizgi eklemeniz gerekebilir. Bunu yapmazsanız, proje Yönetilen Paket Çerçeve kaynak kodunu bulmak için başarısız olabilir.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Yolun sonundaki ters eğik liği unutma.

    3. Projeyi yeniden yükleyin.

    4. Aşağıdaki derlemelere başvurular ekleyin:

        - `Microsoft.VisualStudio.Designer.Interfaces`* \<(VSSDK>\VisualStudioIntegration\Common\Assemblies\v2.0 yükle)*

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Proje fabrikasını başlatma

1. *SimpleProjectPackage.cs* dosyasına aşağıdaki `using` yönergeyi ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. `SimpleProjectPackage` Sınıfı `Microsoft.VisualStudio.Package.ProjectPackage`.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Proje fabrikasını kaydedin. `SimpleProjectPackage.Initialize` Yönteme aşağıdaki satırı ekleyin, `base.Initialize`hemen sonra .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Soyut özelliği `ProductUserContext`uygulayın:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. *SimpleProjectFactory.cs,* varolan `using` `using` yönergelerden sonra aşağıdaki yönergeleri ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. `SimpleProjectFactory` Sınıfı `ProjectFactory`.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Sınıfa aşağıdaki kukla yöntemini `SimpleProjectFactory` ekleyin. Bu yöntemi daha sonraki bir bölümde uygulayacaksınız.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Sınıfa aşağıdaki alanı ve `SimpleProjectFactory` oluşturucuyu ekleyin. Bu `SimpleProjectPackage` başvuru, bir hizmet sağlayıcı sitesi ayarı nda kullanılabilecek şekilde özel bir alanda önbelleğe alınarak önbelleğe alınmaktadır.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Çözümü yeniden oluşturun ve hatasız oluşturduğunu doğrulayın.

## <a name="test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test edin
 Proje fabrikauygulamanızın oluşturucusu çağrılıp çağrılmadığını test edin.

### <a name="to-test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etmek için

1. *SimpleProjectFactory.cs* dosyasında, `SimpleProjectFactory` oluşturucudaki aşağıdaki satırda bir kesme noktası ayarlayın.

    ```csharp
    this.package = package;
    ```

2. Visual Studio'nun deneysel bir örneğini başlatmak için **F5** tuşuna basın.

3. Deneysel örnekte, yeni bir proje oluşturmaya başlayın. Yeni **Proje** iletişim kutusunda, **SimpleProject** proje türünü seçin ve ardından **Tamam'ı**tıklatın. Yürütme kesme noktasında durur.

4. Kesme noktasını temizleyin ve hata ayıklamayı durdurun. Henüz bir proje düğümü oluşturmadığımıziçin, proje oluşturma kodu yine de özel durumlar oluşturur.

## <a name="extend-the-projectnode-class"></a>ProjectNode sınıfını genişletin
 Şimdi `SimpleProjectNode` `ProjectNode` sınıftan türetilen sınıfı uygulayabilirsiniz. `ProjectNode` Taban sınıf, proje oluşturma nın aşağıdaki görevlerini işler:

- Proje şablondosyası *SimpleProject.myproj'u*yeni proje klasörüne kopyalar. Kopya, **Yeni Proje** iletişim kutusuna girilen ada göre yeniden adlandırılır. Özellik `ProjectGuid` değeri yeni bir GUID ile değiştirilir.

- Proje şablon dosyası, *SimpleProject.myproj'un*MSBuild öğelerini `Compile` geçer ve öğeleri arar. Her `Compile` hedef dosya için dosyayı yeni proje klasörüne kopyalar.

  Türemiş `SimpleProjectNode` sınıf şu görevleri işler:

- **Çözüm Gezgini'ndeki** proje ve dosya düğümleri simgelerinin oluşturulmasını veya seçilmesini sağlar.

- Ek proje şablonu parametre değiştirmelerinin belirtilmesini sağlar.

### <a name="to-extend-the-projectnode-class"></a>ProjectNode sınıfını genişletmek için

1. Adlı sınıf `SimpleProjectNode.cs`ekle.

2. Varolan kodu aşağıdaki kodla değiştirin.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   Bu `SimpleProjectNode` sınıf uygulaması bu geçersiz yöntemleri vardır:

- `ProjectGuid`, hangi proje fabrikası GUID döndürür.

- `ProjectType`, proje türünün yerelleştirilmiş adını döndürür.

- `AddFileFromTemplate`, seçili dosyaları şablon klasöründen hedef projeye kopyalar. Bu yöntem daha sonraki bir bölümde daha da uygulanır.

  Yapıcı, `SimpleProjectNode` `SimpleProjectFactory` yapıcı gibi, daha sonra `SimpleProjectPackage` kullanmak için özel bir alanda bir referans önbelleğe gelir.

  `SimpleProjectFactory` Sınıfı `SimpleProjectNode` sınıfa bağlamak için yöntemde `SimpleProjectNode` `SimpleProjectFactory.CreateProject` yeni bir yeniyi anında kullanmanız ve daha sonra kullanmak üzere özel bir alanda önbelleğe almanız gerekir.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Proje fabrika sınıfını ve düğüm sınıfını bağlamak için

1. *SimpleProjectFactory.cs* dosyasına aşağıdaki `using` yönergeyi ekleyin:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Aşağıdaki `SimpleProjectFactory.CreateProject` kodu kullanarak yöntemi değiştirin.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Çözümü yeniden oluşturun ve hatasız oluşturduğunu doğrulayın.

## <a name="test-the-projectnode-class"></a>ProjectNode sınıfını test edin
 Proje hiyerarşisi oluşturup oluşturmadığını görmek için proje fabrikanızı test edin.

### <a name="to-test-the-projectnode-class"></a>ProjectNode sınıfını test etmek için

1. Hata ayıklamaya başlamak için **F5**'e basın. Deneysel örnekte, yeni bir SimpleProject oluşturun.

2. Visual Studio bir proje oluşturmak için proje fabrikanızı aramalıdır.

3. Visual Studio'nun deneysel örneğini kapatın.

## <a name="add-a-custom-project-node-icon"></a>Özel proje düğümü simgesi ekleme
 Önceki bölümdeki proje düğümü simgesi varsayılan bir simgedir. Özel bir simge olarak değiştirebilirsiniz.

### <a name="to-add-a-custom-project-node-icon"></a>Özel proje düğümü simgesi eklemek için

1. **Kaynaklar** klasörüne *SimpleProjectNode.bmp*adlı bir bitmap dosyası ekleyin.

2. **Özellikler** pencerelerinde, bit eşlemi 16 piksele düşürün. Bit eşlemi ayırt edici olun.

    ![Basit Proje Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. **Özellikler** penceresinde, biteşin **Yapı eylemini** **Katıştırılmış Kaynak**olarak değiştirin.

4. *SimpleProjectNode.cs*olarak, aşağıdaki `using` yönergeleri ekleyin:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Sınıfa aşağıdaki statik alanı ve `SimpleProjectNode` oluşturucuyu ekleyin.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. `SimpleProjectNode` Sınıfın başına aşağıdaki özelliği ekleyin.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Örnek oluşturucuyu aşağıdaki kodla değiştirin.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   Statik yapı `SimpleProjectNode` sırasında, yapı bildirimi kaynaklarından proje düğümü bit eşleğini alır ve daha sonra kullanmak üzere özel bir alanda önbelleğe alır. Görüntü yolunun sözdizimine dikkat edin. <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> Derlemeye katıştılmış bildirim kaynaklarının adlarını <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> görmek için yöntemi kullanın. Bu yöntem `SimpleProject` derlemeye uygulandığında, sonuçlar aşağıdaki gibi olmalıdır:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Kaynaklar.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Örnek oluşturma sırasında, `ProjectNode` taban sınıf yükler *Resources.imagelis.bmp*, hangi sık kullanılan gömülü 16 x 16 bitmaps *Kaynaklar\imagelis.bmp*. Bu bitmap listesi `SimpleProjectNode` olarak `ImageHandler.ImageList`kullanılabilir hale getirilir. `SimpleProjectNode`listeye proje düğümü bit eşlemi eklenir. Görüntü listesindeki proje düğümü bit eşlemi ofset, daha sonra kamu `ImageIndex` malının değeri olarak kullanılmak üzere önbelleğe alınr. Visual Studio, proje düğümü simgesi olarak hangi bit eşleningörüntülenemeye karar vermek için bu özelliği kullanır.

## <a name="test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test edin
 Özel proje düğüm simgenize sahip bir proje hiyerarşisi oluşturup oluşturmadığını görmek için proje fabrikanızı test edin.

### <a name="to-test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini sınamak için

1. Hata ayıklamaya başlayın ve deneme örneğinde yeni bir SimpleProject oluşturun.

2. Yeni oluşturulan projede, *SimpleProjectNode.bmp'nin* proje düğümü simgesi olarak kullanıldığına dikkat edin.

     ![Basit Proje Yeni Proje Düğümü](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Kod düzenleyicisinde *Program.cs* dosyasını açın. Aşağıdaki kodu andıran kaynak kodu görmeniz gerekir.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     Şablon parametrelerinin $nameSpace$ ve $className$ yeni değerlere sahip olmadığını unutmayın. Bir sonraki bölümde şablon parametre değiştirmenin nasıl uygulanacağını öğreneceksiniz.

## <a name="substitute-template-parameters"></a>Yedek şablon parametreleri
 Daha önceki bir bölümde, özniteliği kullanarak proje `ProvideProjectFactory` şablonu Visual Studio ile kaydedilmiştir. Şablon klasörünün yolunu bu şekilde kaydetmek, `ProjectNode.AddFileFromTemplate` sınıfı geçersiz kılarak ve genişleterek temel şablon parametre ikamesini etkinleştirmenizi sağlar. Daha fazla bilgi için, [Bkz. Yeni proje oluşturma: Başlık altında, bölüm iki](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Şimdi sınıfa `AddFileFromTemplate` değiştirme kodu ekleyin.

### <a name="to-substitute-template-parameters"></a>Şablon parametrelerini değiştirmek için

1. *SimpleProjectNode.cs* dosyasına aşağıdaki `using` yönergeyi ekleyin.

   ```csharp
   using System.IO;
   ```

2. Aşağıdaki `AddFileFromTemplate` kodu kullanarak yöntemi değiştirin.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. `className` Atama deyiminden hemen sonra yöntemde bir kesme noktası ayarlayın.

   Atama deyimleri, ad alanı ve yeni bir sınıf adı için makul değerleri belirler. İki `ProjectNode.FileTemplateProcessor.AddReplace` yöntem çağrısı, bu yeni değerleri kullanarak ilgili şablon parametre değerlerini değiştirir.

## <a name="test-the-template-parameter-substitution"></a>Şablon parametre değiştirmesini test edin
 Artık şablon parametre değiştirme test edebilirsiniz.

### <a name="to-test-the-template-parameter-substitution"></a>Şablon parametre değiştirmesini sınamak için

1. Hata ayıklamaya başlayın ve deneme örneğinde yeni bir SimpleProject oluşturun.

2. Yürütme `AddFileFromTemplate` yöntemdeki kesme noktasında durur.

3. Parametrelerve `className` parametreleriçin `nameSpace` değerleri inceleyin.

   - `nameSpace`\< *\Templates\Projects\SimpleProject\SimpleProject.myproj* proje şablon dosyasındaki RootNamespace> öğesinin değeri verilir. Bu durumda, değer `MyRootNamespace`.

   - `className`dosya adı uzantısı olmadan sınıf kaynak dosya adının değeri verilir. Bu durumda, hedef klasöre kopyalanacak ilk dosya *AssemblyInfo.cs;* bu nedenle, className `AssemblyInfo`değeri .

4. Kesme noktasını kaldırın ve yürütmeye devam etmek için **F5** tuşuna basın.

    Visual Studio bir proje oluşturmayı bitirmelidir.

5. Kod düzenleyicisinde *Program.cs* dosyasını açın. Aşağıdaki kodu andıran kaynak kodu görmeniz gerekir.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    Ad alanının şimdi `MyRootNamespace` ve sınıf adının `Program`şimdi olduğuna dikkat edin.

6. Projehatasını çıkarmaya başlayın. Yeni proje "Hello VSX!!!" derlenmesi, çalıştırMası ve görüntülemesi gerekir. konsol penceresinde.

    ![Basit Proje Komutu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Tebrikler! Temel yönetilen bir proje sistemi uyguladınız.
