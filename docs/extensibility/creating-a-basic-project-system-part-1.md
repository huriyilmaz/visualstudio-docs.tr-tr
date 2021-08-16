---
title: Temel Project Sistemi Oluşturma, Bölüm 1 | Microsoft Docs
description: extension.myproj adlı bir proje türü oluşturma hakkında bilgi. Bu Visual Studio, kaynak kod dosyalarını ve diğer varlıkları düzenlemek için kullanılan kapsayıcılardır.
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
ms.openlocfilehash: c24fc5a1e685c80cbc1d122538fbcbae520995614591085effed104e6e094215
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403469"
---
# <a name="create-a-basic-project-system-part-1"></a>Temel proje sistemi oluşturma, bölüm 1
Bu Visual Studio, geliştiricilerin kaynak kod dosyalarını ve diğer varlıkları düzenlemek için kullanabileceği kapsayıcılardır. Projeler, projesinde çözümlerin **Çözüm Gezgini.** Projeler kaynak kodunu düzenlemenize, derlemenize, hata ayıklamanızı ve dağıtmanızı ve Web hizmetleri, veritabanları ve diğer kaynaklara başvurular oluşturmanızı sağlar.

 Projeler, bir Visual C# projesi için *.csproj* dosyası gibi proje dosyalarında tanımlanır. Kendi proje dosya adı uzantınıza sahip kendi proje türlerinizi oluşturabilirsiniz. Proje türleri hakkında daha fazla bilgi için [bkz. Project türleri.](../extensibility/internals/project-types.md)

> [!NOTE]
> Visual Studio'i özel bir proje türüyle genişletmeniz gerekirse, sıfırdan proje sistemi oluşturmanın bir dizi avantajı olan [Visual Studio](https://github.com/Microsoft/VSProjectSystem) proje sisteminden (VSPS) kesinlikle kullanılması önerilir:
>
> - Daha kolay ekleme.  Temel bir proje sistemi bile on binlerce kod satırı gerektirir.  VSPS'den yararlanarak, gereksinimlerinize göre özelleştirmeye hazır olmadan önce ekleme maliyetini birkaç tıklamaya düşürebilirsiniz.
> - Daha kolay bakım.  VSPS'den yararlanarak yalnızca kendi senaryolarınızı sürdürmeniz gerekir.  Tüm proje sistemi altyapısının bakımlarını biz hallederiz.
>
>   Önceki sürümlerden daha eski Visual Studio hedeflemeniz Visual Studio 2013, bir uzantıda VSPS'den Visual Studio olmaz.  Bu durumda, bu izlenecek yol çalışmaya başlamaya iyi bir yerdir.

 Bu izlenecek yol, .myproj proje dosya adı uzantısına sahip bir proje *türünün nasıl oluşturularak ilgili adım adım kılavuzda size yol gösterir.* Bu kılavuz, mevcut Visual C# proje sisteminden ödünç alınıyor.

> [!NOTE]
> Uzantı projelerine daha fazla örnek için bkz. [VSSDK örnekleri.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

 Bu kılavuzda, bu görevlerin nasıl yerine ulaşacağız öğretildi:

- Temel bir proje türü oluşturun.

- Temel bir proje şablonu oluşturun.

- Proje şablonunu Visual Studio.

- Yeni Uygulama iletişim kutusunu açarak **ve Project** kullanarak bir proje örneği oluşturun.

- Proje sisteminiz için bir proje fabrikası oluşturun.

- Proje sisteminiz için bir proje düğümü oluşturun.

- Proje sistemi için özel simgeler ekleyin.

- Temel şablon parametresi değiştirmesi uygulama.

## <a name="prerequisites"></a>Önkoşullar
 2015 Visual Studio den başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

 Ayrıca projeleri için Yönetilen Paket [Çerçevesi'nin kaynak kodunu da indirmeniz gerekir.](https://github.com/tunnelvisionlabs/MPFProj10) Dosyayı, oluşturacakları çözümün erişilebilen bir konuma ayıklar.

## <a name="create-a-basic-project-type"></a>Temel proje türü oluşturma
 **SimpleProject** adlı bir C# VSIX projesi oluşturun. (**Dosya**  >  **Yeni**  >  **Project** ve ardından **Visual C#**  >  **Genişletilebilirlik**  >  **VSIX Project**). Bir Visual Studio Paket proje öğesi şablonu **ekleyin (Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe Ekle'yi seçin, ardından Genişletilebilirlik  >  Visual Studio   >  **Paket) gidin.** *Dosyaya SimpleProjectPackage adını girin.*

## <a name="creating-a-basic-project-template"></a>Temel proje şablonu oluşturma
 Şimdi, bu temel VSPackage'ı yeni *.myproj proje türünü uygulamak için* değiştirebilirsiniz. *.myproj* proje türünü temel alan bir proje oluşturmak için Visual Studio hangi dosyaların, kaynakların ve başvuruların yeni projeye ekli olduğunu bilmek gerekir. Bu bilgileri sağlamak için proje dosyalarını bir proje şablonu klasörüne girin. Bir kullanıcı proje oluşturmak *için .myproj* projesini kullandığında, dosyalar yeni projeye kopyalanır.

### <a name="to-create-a-basic-project-template"></a>Temel bir proje şablonu oluşturmak için

1. Projeye biri diğeri altında üç klasör ekleyin: *Templates\Projects\SimpleProject*. **(Çözüm Gezgini'da** **SimpleProject** proje düğümüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Yeni **Klasör'e tıklayın.** Klasöre *Templates adını girin.* Şablonlar *klasörüne* Projects adlı bir klasör *ekleyin.* Projeler *klasörüne* *SimpleProject* adlı bir klasör ekleyin.)

2. *Templates\Projects\SimpleProject* klasöründe *SimpleProject.ico* adlı simge olarak kullanmak üzere bir Bit Eşlem Görüntüsü dosyası ekleyin. **Ekle'ye tıklarsanız** simge düzenleyicisi açılır.

3. Simgeyi ayırt edici hale sürükleyin. Bu simge, kılavuzda **daha Project** Yeni Uygulama iletişim kutusunda görünür.

    ![Basit Project Simgesi](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Simgeyi kaydedin ve simge düzenleyicisini kapatın.

5. *Templates\Projects\SimpleProject klasörüne* *Program.cs* adlı **bir** Sınıf öğesi ekleyin.

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
   > Bu, *Program.cs* kodunun son biçimi değildir; değiştirme parametreleri daha sonraki bir adımda ele alınacak. Derleme hataları görebilir, ancak dosyanın **BuildAction'sı** İçerik olduğu sürece projeyi her zamanki gibi derleye ve çalıştırabilirsiniz. 

7. Dosyayı kaydedin.

8. Properties *klasöründeki AssemblyInfo.cs* *dosyasını* *Projects\SimpleProject klasörüne* kopyalayın.

9. *Projects\SimpleProject klasörüne* *SimpleProject.myproj adlı* bir XML dosyası ekleyin.

   > [!NOTE]
   > Bu tür tüm projeler için dosya adı uzantısı *.myproj'dır.* Bunu değiştirmek için izlenecek yolda belirtilen her yerde bunu değiştirmelisiniz.

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

12. Özellikler **penceresinde** *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico* ve *SimpleProject.myproj* Derleme Eylemlerini İçerik olarak ayarlayın ve **VSIX** özelliklerine dahil edin özelliklerini True olarak **ayarlayın.** 

    Bu proje şablonu, hem Hata Ayıklama yapılandırmasına hem de Yayın yapılandırmasına sahip temel bir Visual C# projesini açıklar. Proje, *AssemblyInfo.cs* ve *Program.cs* olmak için iki kaynak dosya ve çeşitli derleme başvuruları içerir. Şablondan bir proje oluşturulduğunda ProjectGuid değeri otomatik olarak yeni bir GUID ile değiştirilir.

    Bu **Çözüm Gezgini** genişletilmiş Şablonlar **klasörü** aşağıdaki gibi görünilmelidir:

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
 Proje şablonu Visual Studio konumunu söylemeniz gerekir. Bunu yapmak için, VSPackage builtedken şablon konumunun sistem kayıt defterine yazıldığı şekilde proje fabrikasını uygulayan VSPackage sınıfına bir öznitelik ekleyin. Başlangıç olarak proje fabrikası GUID'si tarafından tanımlanan temel bir proje fabrikası oluşturma. Proje <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> fabrikasını sınıfına bağlamak için özniteliğini `SimpleProjectPackage` kullanın.

### <a name="to-create-a-basic-project-factory"></a>Temel bir proje fabrikası oluşturmak için

1. Proje fabrikanız için GUID'ler oluşturun **(Araçlar** menüsünde **GUID** Oluştur'a tıklayın) veya aşağıdaki örnekteki GUID'i kullanın. GUID'leri, `SimpleProjectPackage` zaten tanımlanmış olan bölümüyle yakın sınıfına `PackageGuidString` ekleyin. GUID'ler hem GUID formunda hem de dize formunda olmalıdır. Sonuçta elde edilen kod aşağıdaki örnekteki gibi bir sonuç elde edilebilir.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. *SimpleProjectFactory.cs adlı üst SimpleProject klasörüne bir sınıf ekleyin.* 

3. Aşağıdaki using yönergelerini ekleyin:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. sınıfına bir GUID özniteliği `SimpleProjectFactory` ekleyin. özniteliğinin değeri yeni proje fabrikası GUID değeridir.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Artık proje şablonlarınızı kaydedebilirsiniz.

### <a name="to-register-the-project-template"></a>Proje şablonunu kaydetmek için

1. *SimpleProjectPackage.cs* içinde, <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> sınıfına aşağıdaki `SimpleProjectPackage` gibi bir öznitelik ekleyin.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Çözümü yeniden derleme ve hatasız olarak derlemeyi doğrulama.

    Yeniden oluşturmak proje şablonunu kaydedmektedir.

   ve parametreleri `defaultProjectExtension` `possibleProjectExtensions` proje dosya adı uzantısına (*.myproj*) ayarlanır. `projectTemplatesDirectory`parametresi, *Templates* klasörünün göreli yoluna ayarlanır. Derleme sırasında bu yol tam derlemeye dönüştürülür ve proje sistemini kaydetmek için kayıt defterine eklenir.

## <a name="test-the-template-registration"></a>Şablon kaydını test etmek
 Şablon kaydı Visual Studio proje şablonu klasör Visual Studio yeni klasör iletişim kutusunda şablon adını ve simgesini **görüntüley Project** söyler.

### <a name="to-test-the-template-registration"></a>Şablon kaydını test etmek için

1. Deneysel bir örnek hata ayıklamaya başlamak için **F5** tuşuna Visual Studio.

2. Deneysel örnekte, yeni oluşturduğunuz proje türünde yeni bir proje oluşturun. Yeni **Proje Project** kutusunda, Yüklü şablonlar **altında SimpleProject** **öğesini görüyorsanız.**

   Artık kayıtlı bir proje fabrikana sahipsiniz. Ancak, henüz bir proje oluşturamaz. Proje paketi ve proje fabrikası, bir proje oluşturmak ve başlatmak için birlikte çalışır.

## <a name="add-the-managed-package-framework-code"></a>Yönetilen Paket Çerçevesi kodunu ekleme
 Proje paketi ile proje fabrikası arasındaki bağlantıyı uygulama.

- Yönetilen Paket Çerçevesi için kaynak kodu dosyalarını içeri aktarın.

    1. SimpleProject projesini kaldır **(Çözüm Gezgini** proje düğümünü seçin ve bağlam menüsünde **Project.)** kaldır'a tıklayın ve proje dosyasını XML düzenleyicisinde açın.

    2. Proje dosyasına aşağıdaki blokları ekleyin (blokların hemen \<Import> üzerinde). Az `ProjectBasePath` önce indirdiğiniz *Yönetilen Paket Çerçevesi kodunda ProjectBase.files* dosyasının konumu olarak ayarlayın. Pathname'e ters eğik çizgi eklemeniz gerekir. Yoksa, proje Yönetilen Paket Çerçevesi kaynak kodunu bulamaz.

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

        - `Microsoft.VisualStudio.Designer.Interfaces`*\<VSSDK install> (\VisualStudioIntegration\Common\Assemblies\v2.0 içinde)*

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Proje fabrikasını başlatmak için

1. *SimpleProjectPackage.cs* dosyasına aşağıdaki yönergeyi `using` ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. sınıfından `SimpleProjectPackage` sınıfını `Microsoft.VisualStudio.Package.ProjectPackage` türetin.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Proje fabrikasını kaydetme. hemen sonra yöntemine `SimpleProjectPackage.Initialize` aşağıdaki satırı `base.Initialize` ekleyin.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. soyut özelliğini `ProductUserContext` uygulama:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. *SimpleProjectFactory.cs* içinde, mevcut `using` yönergelerinin ardından aşağıdaki `using` yönergeyi ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. sınıfından `SimpleProjectFactory` sınıfını `ProjectFactory` türetin.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Aşağıdaki sahte yöntemi sınıfına `SimpleProjectFactory` ekleyin. Bu yöntemi sonraki bir bölümde uygulayacağız.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Sınıfına aşağıdaki alanı ve oluşturucusu `SimpleProjectFactory` ekleyin. Bu `SimpleProjectPackage` başvuru özel bir alanda önbelleğe alınarak hizmet sağlayıcısı sitesi ayarlamada kullanılabilir.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Çözümü yeniden derleme ve hatasız olarak derlemeyi doğrulama.

## <a name="test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etmek
 Proje fabrikası uygulamanıza yönelik oluşturucu çağrılıp çağrılmay olmadığını test eder.

### <a name="to-test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etmek için

1. *SimpleProjectFactory.cs* dosyasında, oluşturucuda aşağıdaki satırda bir kesme noktası `SimpleProjectFactory` ayarlayın.

    ```csharp
    this.package = package;
    ```

2. Deneme örneği başlatmak için **F5** tuşuna Visual Studio.

3. Deneysel örnekte yeni bir proje oluşturun. Yeni Proje **Project** kutusunda **SimpleProject** proje türünü seçin ve ardından Tamam'a **tıklayın.** Yürütme kesme noktası sırasında durdurulur.

4. Kesme noktası temiz ve hata ayıklamayı durdur. Henüz bir proje düğümü oluşturmadık, proje oluşturma kodu hala özel durumlar oluşturur.

## <a name="extend-the-projectnode-class"></a>ProjectNode sınıfını genişletme
 Artık sınıfından `SimpleProjectNode` türeten sınıfını `ProjectNode` gerçekleştirin. Temel `ProjectNode` sınıf, aşağıdaki proje oluşturma görevlerini işler:

- *SimpleProject.myproj* proje şablonu dosyasını yeni proje klasörüne kopyalar. Kopya, Yeni Giriş iletişim kutusuna girilen adla **Project** adlandırılır. Özellik `ProjectGuid` değeri yeni bir GUID ile değiştirilir.

- *SimpleProject.myproj* proje şablonu dosyasının MSBuild öğeleri arasında geçişler ve `Compile` öğelerine bakarak. Her `Compile` hedef dosya için dosyayı yeni proje klasörüne kopyalar.

  Türetilmiş sınıf `SimpleProjectNode` şu görevleri işler:

- Proje ve dosya düğümlerinin oluşturulacak veya **Çözüm Gezgini** için simgelere olanak sağlar.

- Ek proje şablonu parametre değiştirmeleri belirtilebilir.

### <a name="to-extend-the-projectnode-class"></a>ProjectNode sınıfını genişletmek için

1. adlı bir sınıf `SimpleProjectNode.cs` ekleyin.

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

   Bu `SimpleProjectNode` sınıf uygulaması şu geçersiz kılınan yöntemlere sahip:

- `ProjectGuid`, proje fabrikası GUID'sini döndürür.

- `ProjectType`, proje türünün yerelleştirilmiş adını döndürür.

- `AddFileFromTemplate`, seçilen dosyaları şablon klasöründen hedef projeye kopyalar. Bu yöntem daha sonraki bir bölümde de uygulanır.

  Oluşturucu `SimpleProjectNode` gibi `SimpleProjectFactory` oluşturucu, daha sonra kullanmak üzere özel bir `SimpleProjectPackage` alanda bir başvuru önbelleğe.

  sınıfını sınıfına bağlamak için yönteminde yeni bir örneği ve daha sonra kullanmak üzere `SimpleProjectFactory` `SimpleProjectNode` özel bir alanda `SimpleProjectNode` `SimpleProjectFactory.CreateProject` önbelleğe a gerekir.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Proje fabrikası sınıfını ve node sınıfını bağlamak için

1. *SimpleProjectFactory.cs* dosyasına aşağıdaki yönergeyi `using` ekleyin:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. aşağıdaki `SimpleProjectFactory.CreateProject` kodu kullanarak yöntemini değiştirin.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Çözümü yeniden derleme ve hatasız olarak derlemeyi doğrulama.

## <a name="test-the-projectnode-class"></a>ProjectNode sınıfını test etmek
 Proje fabrikanızı test edip proje hiyerarşisi oluşturduğuna bakın.

### <a name="to-test-the-projectnode-class"></a>ProjectNode sınıfını test etmek için

1. Hata ayıklamaya başlamak için **F5**'e basın. Deneysel örnekte yeni bir SimpleProject oluşturun.

2. Visual Studio oluşturmak için proje fabrikanızı çağırmanız gerekir.

3. Deneysel Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Özel proje düğümü ekleme simgesi
 Önceki bölümdeki proje düğümü simgesi varsayılan bir simgedir. Bunu özel bir simgeyle değiştirebilirsiniz.

### <a name="to-add-a-custom-project-node-icon"></a>Özel proje düğümü simgesi eklemek için

1. Resources **klasörüne** SimpleProjectNode.bmpadlı bir *bit eşlem dosyası ekleyin.*

2. Özellikler **pencerelerde** bit eşlemi 16 x 16 piksele düşürebilirsiniz. Bit eşlemi ayırt edici hale.

    ![Basit Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. Özellikler penceresinde **bit** eşlem **derleme eylemlerini** Katıştırılmış Kaynak **olarak değiştirin.**

4. *SimpleProjectNode.cs* içinde aşağıdaki `using` yönergeleri ekleyin:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Aşağıdaki statik alanı ve oluşturucusu sınıfına `SimpleProjectNode` ekleyin.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Aşağıdaki özelliği sınıfının başına `SimpleProjectNode` ekleyin.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Örnek oluşturucusu'nu aşağıdaki kodla değiştirin.

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

   Statik yapı sırasında, derleme bildirimi kaynaklarından proje düğümü bit eşlemi alınır ve daha sonra kullanmak `SimpleProjectNode` üzere özel bir alanda önbelleğe alınır. Görüntü yolunun söz dizim <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> dikkati. Derlemeye eklenmiş bildirim kaynaklarının adlarını görmek için yöntemini <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> kullanın. Bu yöntem derlemeye `SimpleProject` uygulandığında, sonuçlar aşağıdaki gibi olmalıdır:

- *SimpleProject.Resources.resources*

- *VisualStudio. Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio. Project. DontShowAgainDialog.resources*

- *Microsoft.VisualStudio. Project. SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Örnek oluşturulurken, temel sınıfResources.imagelis.bmpyükler. Bu, içinde genellikleResources\imagelis.bmp'den `ProjectNode` 16 x 16 bit *eşlem kullanılır.* ** Bu bit eşlem listesi olarak `SimpleProjectNode` `ImageHandler.ImageList` kullanılabilir. `SimpleProjectNode` , proje düğümü bit eşlemini listeye ekler. Görüntü listesinde proje düğümü bit eşlem uzaklığı, daha sonra ortak özelliğin değeri olarak kullanmak üzere önbelleğe `ImageIndex` alınmaktadır. Visual Studio, proje düğümü simgesi olarak hangi bit eşlem'in görüntül olduğunu belirlemek için bu özelliği kullanır.

## <a name="test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etmek
 Proje fabrikanızı test edip özel proje düğümü simgenizi olan bir proje hiyerarşisi mi oluşturduğuna bakın.

### <a name="to-test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etmek için

1. Hata ayıklamayı başlat ve deneysel örnekte yeni bir SimpleProject oluşturun.

2. Yeni oluşturulan projede, proje düğümü *SimpleProjectNode.bmp* olarak yeni bir uygulamanın kullanılmaya dikkat kullanılmaktadır.

     ![Simple Project New Project Node](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

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
