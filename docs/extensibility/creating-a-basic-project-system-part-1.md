---
title: temel Project sistemi oluşturma, bölüm 1 | Microsoft Docs
description: Uzantı. myproj adlı bir proje türü oluşturmayı öğrenin. Visual Studio, projeler kaynak kodu dosyalarını ve diğer varlıkları düzenlemek için kullanılan kapsayıcılardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a166f33222515163b330ac0f8a22a7d36b10177a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051228"
---
# <a name="create-a-basic-project-system-part-1"></a>Temel proje sistemi oluşturma, Bölüm 1
Visual Studio, projeler, geliştiricilerin kaynak kodu dosyalarını ve diğer varlıkları düzenlemek için kullandığı kapsayıcılardır. Projeler **Çözüm Gezgini** çözümlerin alt öğeleri olarak görünür. Projeler, kaynak kodu düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza, Web Hizmetleri, veritabanları ve diğer kaynaklara başvurular oluşturmanıza imkan tanır.

 Projeler proje dosyalarında tanımlanır, örneğin bir Visual C# projesi için *. csproj* dosyası. Kendi proje dosya adı uzantınıza sahip olan kendi proje türünü de oluşturabilirsiniz. proje türleri hakkında daha fazla bilgi için bkz. [Project types](../extensibility/internals/project-types.md).

> [!NOTE]
> Visual Studio özel bir proje türüyle genişletmenize gerek duyuyorsanız, sıfırdan bir proje sistemi oluşturma konusunda birçok avantaj içeren [Visual Studio proje sisteminin](https://github.com/Microsoft/VSProjectSystem) (vsps) kullanılmasını kesinlikle öneririz:
>
> - Daha kolay ekleme.  Temel bir proje sistemi bile on binlerce satır kod gerektirir.  VSPS 'yi kullanmak, gereksinimlerinize göre özelleştirmeye başlamadan önce ekleme maliyetini birkaç tıklamayla azaltır.
> - Daha kolay bakım.  VSPS 'den yararlanarak yalnızca kendi senaryolarınızı korumanız gerekir.  Tüm proje sistemi altyapısının sürekli tutulmasını yaptık.
>
>   Visual Studio 2013 eski Visual Studio sürümlerini hedefliyorsanız, bir Visual Studio uzantısında vsps 'den yararlanabilemeyeceksiniz.  Böyle bir durum söz konusu olduğunda bu izlenecek yol, başlamak için iyi bir yerdir.

 Bu izlenecek yol, proje dosya adı uzantısına sahip bir proje türünün nasıl oluşturulacağını gösterir *. myproj*. Bu, var olan Visual C# Proje sisteminden boratır izlenecek yolu.

> [!NOTE]
> Uzantı projelerine ilişkin daha fazla örnek için bkz. [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:

- Temel proje türü oluşturun.

- Temel bir proje şablonu oluşturun.

- Proje şablonunu Visual Studio kaydedin.

- **yeni Project** iletişim kutusunu açıp şablonunuzu kullanarak bir proje örneği oluşturun.

- Proje sisteminiz için bir proje fabrikası oluşturun.

- Proje sisteminiz için bir proje düğümü oluşturun.

- Proje sistemi için özel simgeler ekleyin.

- Temel şablon parametre değişimini uygulayın.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

 Ayrıca, [Projeler Için yönetilen paket çerçevesi](https://github.com/tunnelvisionlabs/MPFProj10)için kaynak kodunu da indirmeniz gerekir. Dosyayı oluşturacağınız çözümün erişebileceği bir konuma ayıklayın.

## <a name="create-a-basic-project-type"></a>Temel proje türü oluşturma
 **SimpleProject** ADLı BIR C# VSIX projesi oluşturun. (**Dosya**  >  **Yeni**  >  **Project** ve ardından **Visual C#**  >  **genişletilebilirlik**  >  **vsıx Project**). bir Visual Studio paketi proje öğesi şablonu ekleyin ( **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **yeni öğe** ekle ' yi seçin, ardından **genişletilebilirlik**  >  **Visual Studio paketi**' ne gidin). Dosyayı *Simpleprojectpackage* olarak adlandırın.

## <a name="creating-a-basic-project-template"></a>Temel proje şablonu oluşturma
 Şimdi, yeni *. myproj* proje türünü uygulamak için bu temel VSPackage 'ı değiştirebilirsiniz. *. myproj* proje türünü temel alan bir proje oluşturmak için Visual Studio, yeni projeye hangi dosya, kaynak ve başvuru ekleneceğini bilmelidir. Bu bilgileri sağlamak için proje dosyalarını bir proje şablonu klasörüne koyun. Bir Kullanıcı bir proje oluşturmak için *. myproj* projesini kullandığında, dosyalar yeni projeye kopyalanır.

### <a name="to-create-a-basic-project-template"></a>Temel proje şablonu oluşturmak için

1. Projeye bir tane olmak üzere üç klasör ekleyin: *Templates\projeler* ( **Çözüm Gezgini**, **SimpleProject** proje düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni klasör**' e tıklayın. Klasör *şablonlarını* adlandırın. *Şablonlar* klasöründe, *Projeler* adlı bir klasör ekleyin. *Projeler* klasöründe, *SimpleProject* adlı bir klasör ekleyin.)

2. *Templates\projeler\simpleproject* klasöründe, *SimpleProject. ico* adlı simge olarak kullanılacak bir bit eşlem resim dosyası ekleyin. **Ekle**' ye tıkladığınızda, simge Düzenleyicisi açılır.

3. Simgeyi farklı yapın. bu simge, izlenecek yolun ilerleyen kısımlarında yer alacak **yeni Project** iletişim kutusunda görünür.

    ![basit Project simgesi](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Simgeyi kaydedin ve simge düzenleyicisini kapatın.

5. *Templates\projeler\simpleproject* klasöründe *program. cs* adlı bir **sınıf** öğesi ekleyin.

6. Mevcut kodu aşağıdaki satırlarla değiştirin.

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
   > Bu, programın son formu değildir *. cs* kodu; değiştirme parametreleri sonraki bir adımda ele alınacaktır. Derleme hataları görebilirsiniz, ancak dosyanın **Builkaction** **içeriği** olduğu sürece projeyi her zamanki gibi derleyip çalıştırabilirsiniz.

7. Dosyayı kaydedin.

8. *AssemblyInfo. cs* dosyasını *Properties* klasöründen *Projelerim SimpleProject* klasörüne kopyalayın.

9. *Projeler\simpleproject* klasöründe, *SimpleProject. myproj* adlı bir XML dosyası ekleyin.

   > [!NOTE]
   > Bu türden tüm projeler için dosya adı uzantısı *. myproj*' dir. Bunu değiştirmek istiyorsanız, izlenecek yolda bahsedilen her yerde değiştirmeniz gerekir.

10. Mevcut içeriği aşağıdaki satırlarla değiştirin.

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

12. **Özellikler** penceresinde, *AssemblyInfo. cs*, *program. cs*, *SimpleProject. ico* ve *SimpleProject. myproj* ' ın **derleme eylemini** **içeriğe** ayarlayın ve **VSIX özelliklerinde Include** değerlerini **true** olarak ayarlayın.

    Bu proje şablonu, hem hata ayıklama yapılandırması hem de sürüm yapılandırması olan temel bir Visual C# projesi tanımlar. Proje iki kaynak dosyası, *AssemblyInfo. cs* ve *program. cs* ve birkaç derleme başvurusu içerir. Şablondan bir proje oluşturulduğunda, Projectguıd değeri otomatik olarak yeni bir GUID ile değiştirilmiştir.

    **Çözüm Gezgini**, genişletilmiş **Şablonlar** klasörü aşağıdaki gibi görünmelidir:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Temel proje fabrikası oluşturma
 proje şablonu klasörünüzün konumunun Visual Studio söylemeniz gerekir. Bunu yapmak için, VSPackage oluşturulduğunda şablon konumunun sistem kayıt defterine yazılması için, VSPackage sınıfına proje fabrikası uygulayan bir öznitelik ekleyin. Bir proje fabrikası GUID 'ı tarafından tanımlanan temel bir proje fabrikası oluşturarak başlayın. <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>Proje fabrikasını sınıfa bağlamak için özniteliğini kullanın `SimpleProjectPackage` .

### <a name="to-create-a-basic-project-factory"></a>Temel bir proje fabrikası oluşturmak için

1. Proje fabrikanızın GUID 'Leri oluşturun ( **Araçlar** menüsünde **GUID oluştur**' a tıklayın) veya aşağıdaki örnekteki birini kullanın. GUID 'yi, `SimpleProjectPackage` zaten tanımlanmış olan bölümün yakınında sınıfa ekleyin `PackageGuidString` . GUID 'Ler hem GUID biçiminde hem de dize biçiminde olmalıdır. Elde edilen kod aşağıdaki örneğe benzemelidir.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. *Simpleprojectfactory. cs* adlı üst *SimpleProject* klasörüne bir sınıf ekleyin.

3. Aşağıdaki using yönergelerini ekleyin:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Sınıfa bir GUID özniteliği ekleyin `SimpleProjectFactory` . Özniteliğin değeri, yeni proje fabrikası GUID 'sidir.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Artık proje şablonunuzu kaydedebilirsiniz.

### <a name="to-register-the-project-template"></a>Proje şablonunu kaydetmek için

1. *Simpleprojectpackage. cs* dosyasında <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> aşağıdaki gibi sınıfa bir öznitelik ekleyin `SimpleProjectPackage` .

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.

    Yeniden derleme proje şablonunu kaydeder.

   Parametreler `defaultProjectExtension` ve `possibleProjectExtensions` Proje dosya adı uzantısına ayarlanır (*. myproj*). `projectTemplatesDirectory`Parametresi, *Şablonlar* klasörünün göreli yoluna ayarlanır. Derleme sırasında, bu yol tam bir yapıya dönüştürülür ve proje sistemini kaydetmek için kayıt defterine eklenir.

## <a name="test-the-template-registration"></a>Şablon kaydını test etme
 şablon kaydı, Visual Studio **yeni Project** iletişim kutusunda şablon adı ve simgesini görüntüleyebilmesi için proje şablonu klasörünüzün konumunu Visual Studio söyler.

### <a name="to-test-the-template-registration"></a>Şablon kaydını test etmek için

1. Visual Studio deneysel örneğinde hata ayıklamaya başlamak için **F5** 'e basın.

2. Deneysel örnekte, yeni oluşturulan proje türünden yeni bir proje oluşturun. **yeni Project** iletişim kutusunda, **yüklü şablonlar** altında **simpleproject** ' i görmeniz gerekir.

   Artık kayıtlı bir proje fabrikasına sahipsiniz. Ancak, henüz bir proje oluşturamaz. Proje paketi ve proje fabrikası bir proje oluşturmak ve başlatmak için birlikte çalışır.

## <a name="add-the-managed-package-framework-code"></a>Yönetilen paket çerçevesi kodunu ekleyin
 Proje paketiyle proje fabrikası arasındaki bağlantıyı uygulayın.

- Yönetilen paket çerçevesi için kaynak kodu dosyalarını içeri aktarın.

    1. simpleproject projesini kaldırın ( **Çözüm Gezgini**, proje düğümünü seçin ve bağlam menüsünde, **Project kaldır**' a tıklayın.) ve proje dosyasını XML düzenleyicisinde açın.

    2. Aşağıdaki blokları proje dosyasına ekleyin (blokların hemen üzerinde \<Import> ). `ProjectBasePath`Yeni Indirdiğiniz yönetilen paket çerçevesi kodunda *ProjectBase. Files* dosyasının konumuna ayarlanır. Yol adına bir ters eğik çizgi eklemeniz gerekebilir. Bunu yapmazsanız, proje yönetilen paket çerçevesi kaynak kodunu bulamamasına neden olabilir.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Yolun sonundaki ters eğik çizgiyi unutmayın.

    3. Projeyi yeniden yükleyin.

    4. Aşağıdaki derlemelere başvurular ekleyin:

        - `Microsoft.VisualStudio.Designer.Interfaces`( *\<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Proje fabrikasını başlatmak için

1. *Simpleprojectpackage. cs* dosyasında aşağıdaki `using` yönergeyi ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Sınıfından türet `SimpleProjectPackage` `Microsoft.VisualStudio.Package.ProjectPackage` .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Proje fabrikasını kaydedin. Yöntemine hemen sonra aşağıdaki satırı ekleyin `SimpleProjectPackage.Initialize` `base.Initialize` .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Soyut özelliği uygulayın `ProductUserContext` :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. *Simpleprojectfactory. cs* dosyasında, `using` mevcut yönergelerden sonra aşağıdaki yönergeyi ekleyin `using` .

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Sınıfından türet `SimpleProjectFactory` `ProjectFactory` .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Aşağıdaki kukla yöntemi `SimpleProjectFactory` sınıfına ekleyin. Bu yöntemi sonraki bir bölümde uygulayacaksınız.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Sınıfına aşağıdaki alanı ve oluşturucuyu ekleyin `SimpleProjectFactory` . Bu `SimpleProjectPackage` başvuru, bir hizmet sağlayıcı sitesi ayarlamakta kullanılabilmesi için özel bir alanda önbelleğe alınır.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.

## <a name="test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etme
 Proje fabrikası uygulamanızın oluşturucusunun adlandırılıp çağrılmadığını test edin.

### <a name="to-test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etmek için

1. *Simpleprojectfactory. cs* dosyasında, oluşturucunun aşağıdaki satırında bir kesme noktası ayarlayın `SimpleProjectFactory` .

    ```csharp
    this.package = package;
    ```

2. Visual Studio deneysel bir örneğini başlatmak için **F5** tuşuna basın.

3. Deneysel örnekte, yeni bir proje oluşturmaya başlayın. **yeni Project** iletişim kutusunda, **simpleproject** proje türünü seçin ve ardından **tamam**' a tıklayın. Yürütme kesme noktasında durmaktadır.

4. Kesme noktasını temizle ve hata ayıklamayı Durdur. Henüz bir proje düğümü oluşturmadınız, proje oluşturma kodu hala özel durumlar oluşturuyor.

## <a name="extend-the-projectnode-class"></a>ProjectNode sınıfını genişletme
 Artık `SimpleProjectNode` sınıfından türeten sınıfını uygulayabilirsiniz `ProjectNode` . `ProjectNode`Temel sınıf, proje oluşturma için aşağıdaki görevleri işler:

- *SimpleProject. myproj* proje şablon dosyasını yeni proje klasörüne kopyalar. kopya, **yeni Project** iletişim kutusuna girilen ada göre yeniden adlandırılır. `ProjectGuid`Özellik değeri yeni BIR GUID ile değiştirilmiştir.

- , *simpleproject. myproj* proje şablon dosyasının MSBuild öğelerini geçer ve `Compile` öğeleri arar. Her `Compile` hedef dosya için dosyayı yeni proje klasörüne kopyalar.

  Türetilmiş `SimpleProjectNode` sınıf şu görevleri gerçekleştirir:

- **Çözüm Gezgini** veya seçilmesi için proje ve dosya düğümlerinin simgelerini sağlar.

- Ek proje şablonu parametre değişimlerin belirtilmesini sağlar.

### <a name="to-extend-the-projectnode-class"></a>ProjectNode sınıfını genişletmek için

1. Adlı bir sınıf ekleyin `SimpleProjectNode.cs` .

2. Mevcut kodu aşağıdaki kodla değiştirin.

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

   Bu `SimpleProjectNode` sınıf uygulamasında bu geçersiz kılınan yöntemler vardır:

- `ProjectGuid`, proje fabrikası GUID 'sini döndürür.

- `ProjectType`, proje türünün yerelleştirilmiş adını döndürür.

- `AddFileFromTemplate`Seçili dosyaları şablon klasöründen hedef projeye kopyalayan. Bu yöntem daha sonraki bir bölümde daha da uygulanabilir.

  Oluşturucu `SimpleProjectNode` gibi Oluşturucu, `SimpleProjectFactory` `SimpleProjectPackage` daha sonra kullanılmak üzere bir özel alanda bir başvuruyu önbelleğe alır.

  `SimpleProjectFactory`Sınıfı sınıfa bağlamak için `SimpleProjectNode` , yönteminde yeni bir örneği oluşturmanız `SimpleProjectNode` `SimpleProjectFactory.CreateProject` ve daha sonra kullanmak üzere özel bir alanda önbelleğe almanız gerekir.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Project Factory sınıfını ve Node sınıfını bağlamak için

1. *Simpleprojectfactory. cs* dosyasında aşağıdaki `using` yönergeyi ekleyin:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. `SimpleProjectFactory.CreateProject`Aşağıdaki kodu kullanarak yöntemini değiştirin.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.

## <a name="test-the-projectnode-class"></a>ProjectNode sınıfını test etme
 Proje fabrikasını bir proje hiyerarşisi oluşturup oluşturmadığını görmek için test edin.

### <a name="to-test-the-projectnode-class"></a>ProjectNode sınıfını test etmek için

1. Hata ayıklamaya başlamak için **F5**'e basın. Deneysel örnekte, yeni bir SimpleProject oluşturun.

2. Visual Studio proje oluşturmak için proje fabrikasını çağırmalıdır.

3. Visual Studio Deneysel örneğini kapatın.

## <a name="add-a-custom-project-node-icon"></a>Özel bir proje düğümü simgesi ekleyin
 Önceki bölümdeki proje düğümü simgesi varsayılan simgedir. Bunu özel bir simge olarak değiştirebilirsiniz.

### <a name="to-add-a-custom-project-node-icon"></a>Özel bir proje düğümü simgesi eklemek için

1. **Kaynaklar** klasöründe *SimpleProjectNode.bmp* adlı bir bit eşlem dosyası ekleyin.

2. **Özellikler** penceresinde bit eşlemi 16 ile 16 piksel azaltın. Bit eşlemi farklı hale getirin.

    ![basit Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. **Özellikler** penceresinde, bit eşlemin **derleme eylemini** **katıştırılmış kaynak** olarak değiştirin.

4. *SimpleProjectNode. cs* dosyasında aşağıdaki `using` yönergeleri ekleyin:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Sınıfına aşağıdaki static alanı ve oluşturucuyu ekleyin `SimpleProjectNode` .

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Aşağıdaki özelliği sınıfının başına ekleyin `SimpleProjectNode` .

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Örnek oluşturucusunu aşağıdaki kodla değiştirin.

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

   Statik oluşturma sırasında, `SimpleProjectNode` derleme bildirim kaynaklarından proje düğümü bit eşlemini alır ve daha sonra kullanmak üzere özel bir alanda önbelleğe alır. Görüntü yolunun söz dizimine dikkat edin <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> . Bir derlemeye gömülü olan bildirim kaynaklarının adlarını görmek için <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> yöntemini kullanın. Bu yöntem `SimpleProject` derlemeye uygulandığında, sonuçlar aşağıdaki gibi olmalıdır:

- *SimpleProject. resources. resources*

- *VisualStudio. Project. kaynaklar*

- *SimpleProject. VSPackage. resources*

- *Resources.imagelis.bmp*

- *Microsoft. VisualStudio. Project. DontShowAgainDialog. resources*

- *Microsoft. VisualStudio. Project. SecurityWarningDialog. resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Örnek oluşturma sırasında, `ProjectNode` temel sınıf, *Resources\imagelis.bmp*, yaygın olarak kullanılan 16 x 16 bit eşlem olan *Resources.imagelis.bmp* yükler. Bu bit eşlem listesi olarak kullanılabilir hale `SimpleProjectNode` getirilir `ImageHandler.ImageList` . `SimpleProjectNode` , proje düğümü bit eşlemini listeye ekler. Görüntü listesinde proje düğümü bit eşlem uzaklığı, daha sonra ortak özelliğin değeri olarak kullanmak üzere önbelleğe `ImageIndex` alınmaktadır. Visual Studio, proje düğümü simgesi olarak hangi bit eşlem'in görüntüll olduğunu belirlemek için bu özelliği kullanır.

## <a name="test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etmek
 Proje fabrikanızı test edip özel proje düğümü simgenizi olan bir proje hiyerarşisi mi oluşturduğuna bakın.

### <a name="to-test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etmek için

1. Hata ayıklamayı başlat ve deneysel örnekte yeni bir SimpleProject oluşturun.

2. Yeni oluşturulan projede, proje düğümü *SimpleProjectNode.bmp* olarak yeni bir uygulamanın kullanılmaya dikkat kullanılmaktadır.

     ![Basit Project Yeni Project Node](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Kod düzenleyicisinde *Program.cs* dosyasını açın. Aşağıdaki koda benzer bir kaynak kodu görüyor olun.

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

     $nameSpace$ ve $className$ şablon parametrelerinin yeni değerlere sahip olmadığını fark edersiniz. Sonraki bölümde şablon parametresi değiştirmenin nasıl uygulandığını öğrenirsiniz.

## <a name="substitute-template-parameters"></a>Şablon parametrelerini değiştir
 Önceki bir bölümde, özniteliğini kullanarak proje şablonunu Visual Studio ile `ProvideProjectFactory` kaydettiniz. Şablon klasörünün yolunu bu şekilde kaydetmek, sınıfı geçersiz karak ve genişleterek temel şablon parametresi değiştirmesini etkinleştirmenizi `ProjectNode.AddFileFromTemplate` sağlar. Daha fazla bilgi için [bkz. Yeni proje oluşturma: Başlık altında, ikinci bölüm.](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Şimdi sınıfına değiştirme kodu `AddFileFromTemplate` ekleyin.

### <a name="to-substitute-template-parameters"></a>Şablon parametrelerinin yerine kullanmak için

1. *SimpleProjectNode.cs* dosyasına aşağıdaki yönergeyi `using` ekleyin.

   ```csharp
   using System.IO;
   ```

2. aşağıdaki `AddFileFromTemplate` kodu kullanarak yöntemini değiştirin.

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

3. yönteminde, atama deyiminden hemen sonra bir `className` kesme noktası ayarlayın.

   Atama deyimleri, bir ad alanı ve yeni bir sınıf adı için makul değerleri belirler. İki yöntem `ProjectNode.FileTemplateProcessor.AddReplace` çağrısı, karşılık gelen şablon parametre değerlerini bu yeni değerleri kullanarak değiştirir.

## <a name="test-the-template-parameter-substitution"></a>Şablon parametresini değiştirme testi
 Artık şablon parametresi değiştirme testini kullanabilirsiniz.

### <a name="to-test-the-template-parameter-substitution"></a>Şablon parametresi değiştirme test etmek için

1. Hata ayıklamayı başlat ve deneysel örnekte yeni bir SimpleProject oluşturun.

2. Yürütme yönteminde kesme noktası sırasında `AddFileFromTemplate` durdurulur.

3. ve parametrelerinin `nameSpace` değerlerini `className` inceleme.

   - `nameSpace` öğesine \<RootNamespace> *\Templates\Projects\SimpleProject\SimpleProject.myproj* proje şablonu dosyasında öğesi değeri verilir. Bu durumda, değeri `MyRootNamespace` olur.

   - `className` , dosya adı uzantısı olmadan sınıf kaynak dosya adının değerine verilir. Bu durumda, hedef klasöre kopyalanan ilk dosya *AssemblyInfo.cs dosyasıdır;* bu nedenle className değeri `AssemblyInfo` olur.

4. Kesme noktası kaldırın ve yürütmeye devam **etmek için F5** tuşuna basın.

    Visual Studio proje oluşturmayı bitirmeniz gerekir.

5. Kod düzenleyicisinde *Program.cs* dosyasını açın. Aşağıdaki koda benzer bir kaynak kodu görüyor olun.

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

    Ad alanının şimdi ve sınıf `MyRootNamespace` adının artık olduğunu fark `Program` vardır.

6. Projede hata ayıklamaya başlama. Yeni proje derlenmiş, çalıştırlı ve "Hello VSX!!!" görüntüleniyor seçin.

    ![Basit Project Komutu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Tebrikler! Temel bir yönetilen proje sistemi uygulamaya alındı.
