---
title: Temel proje sistemi oluşturma, Bölüm 1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20637fb47d85b7cb8341df22d056ffe44534835f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295487"
---
# <a name="creating-a-basic-project-system-part-1"></a>Temel Proje Sistemi Oluşturma, Bölüm 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, projeler, geliştiricilerin kaynak kodu dosyalarını ve diğer varlıkları düzenlemek için kullandığı kapsayıcılardır. Projeler **Çözüm Gezgini**çözümlerin alt öğeleri olarak görünür. Projeler, kaynak kodu düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza, Web Hizmetleri, veritabanları ve diğer kaynaklara başvurular oluşturmanıza imkan tanır.  
  
 Projeler proje dosyalarında tanımlanır, örneğin bir görsel C# proje için. csproj dosyası. Kendi proje dosya adı uzantınıza sahip olan kendi proje türünü de oluşturabilirsiniz. Proje türleri hakkında daha fazla bilgi için bkz. [Proje türleri](../extensibility/internals/project-types.md).  
  
> [!NOTE]
> Visual Studio 'Yu özel bir proje türüyle genişletmenize gerek duyuyorsanız, sıfırdan bir proje sistemi oluşturma konusunda birçok avantaj içeren [Visual Studio proje sisteminin](https://github.com/Microsoft/VSProjectSystem) kullanılmasını önemle öneririz:  
> 
> - Daha kolay ekleme.  Temel bir proje sistemi bile on binlerce satır kod gerektirir.  CPS 'yi kullanmak, ekleme maliyetini gereksinimlerinize göre özelleştirmeye başlamadan önce birkaç tıklamayla azaltır.  
>   - Daha kolay bakım.  CPS 'den yararlanarak yalnızca kendi senaryolarınızı korumanız gerekir.  Tüm proje sistemi altyapısının sürekli tutulmasını yaptık.  
> 
>   Visual Studio 'nun Visual Studio 2013 'den eski sürümlerini hedefliyorsanız, Visual Studio uzantısında CPS 'den yararlanabilemeyeceksiniz.  Böyle bir durum söz konusu olduğunda bu izlenecek yol, başlamak için iyi bir yerdir.  
  
 Bu izlenecek yol, proje dosya adı uzantısına sahip bir proje türünün nasıl oluşturulacağını gösterir. myproj. Bu, varolan görsel C# Proje sisteminden boratır izlenecek yolu.  
  
> [!NOTE]
> Tam dil projesi sisteminin uçtan uca bir örneği için bkz. [VSSDK örnekleri](../misc/vssdk-samples.md)Içindeki IronPython örnek derin açıklaması.  
  
 Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:  
  
- Temel proje türü oluşturun.  
  
- Temel bir proje şablonu oluşturun.  
  
- Proje şablonunu Visual Studio ile kaydedin.  
  
- **Yeni proje** iletişim kutusunu açıp şablonunuzu kullanarak bir proje örneği oluşturun.  
  
- Proje sisteminiz için bir proje fabrikası oluşturun.  
  
- Proje sisteminiz için bir proje düğümü oluşturun.  
  
- Proje sistemi için özel simgeler ekleyin.  
  
- Temel şablon parametre değişimini uygulayın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Ayrıca, [Projeler Için yönetilen paket çerçevesi](https://archive.codeplex.com/?p=mpfproj12)için kaynak kodunu da indirmeniz gerekir. Dosyayı oluşturacağınız çözümün erişebileceği bir konuma ayıklayın.  
  
## <a name="creating-a-basic-project-type"></a>Temel proje türü oluşturma  
 C# **SimpleProject**adlı bir VSIX projesi oluşturun. (**Dosya, yeni, proje** ve daha sonra  **C#genişletilebilirlik, Visual Studio paketi**). Visual Studio Package proje öğesi şablonu ekleyin (Çözüm Gezgini, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin, ardından **genişletilebilirlik/Visual Studio paketine**gidin). Dosyayı **Simpleprojectpackage**olarak adlandırın.  
  
## <a name="creating-a-basic-project-template"></a>Temel proje şablonu oluşturma  
 Şimdi, yeni. myproj proje türünü uygulamak için bu temel VSPackage 'ı değiştirebilirsiniz. . Myproj proje türünü temel alan bir proje oluşturmak için, Visual Studio 'nun hangi dosyaları, kaynakları ve başvuruları yeni projeye ekleneceğini bilmeleri gerekir. Bu bilgileri sağlamak için proje dosyalarını bir proje şablonu klasörüne koyun. Bir Kullanıcı bir proje oluşturmak için. myproj projesini kullandığında, dosyalar yeni projeye kopyalanır.  
  
#### <a name="to-create-a-basic-project-template"></a>Temel proje şablonu oluşturmak için  
  
1. Projeye bir tane olmak üzere üç klasör ekleyin: **Templates\projeler** ( **Çözüm Gezgini**, **SimpleProject** proje düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni klasör**' e tıklayın. Klasörü `Templates`adlandırın. **Şablonlar** klasöründe `Projects`adlı bir klasör ekleyin. **Projeler** klasöründe `SimpleProject`adlı bir klasör ekleyin.)  
  
2. **Projeler\simpleproject** klasöründe `SimpleProject.ico`adlı bir simge dosyası ekleyin. **Ekle**' ye tıkladığınızda, simge Düzenleyicisi açılır.  
  
3. Simgeyi farklı yapın. Bu simge, izlenecek yolun ilerleyen kısımlarında yer alacak **Yeni proje** iletişim kutusunda görünür.  
  
    ![Basit proje simgesi](../extensibility/media/simpleprojicon.png "Simpleprojıcon")  
  
4. Simgeyi kaydedin ve simge düzenleyicisini kapatın.  
  
5. **Projeler\simpleproject** klasöründe `Program.cs`adlı bir **sınıf** öğesi ekleyin.  
  
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
   > Bu, Program.cs kodunun son formu değildir; değiştirme parametreleri sonraki bir adımda ele alınacaktır. Derleme hataları görebilirsiniz, ancak dosyanın **Builkaction** **içeriği**olduğu sürece projeyi her zamanki gibi derleyip çalıştırabilirsiniz.  
  
7. Dosyayı kaydedin.  
  
8. AssemblyInfo.cs dosyasını **Özellikler** klasöründen, **projelerprojem proje** klasörüne kopyalayın.  
  
9. **Projeler\simpleproject** klasöründe `SimpleProject.myproj`ADLı bir XML dosyası ekleyin.  
  
   > [!NOTE]
   > Bu türden tüm projeler için dosya adı uzantısı. myproj ' dir. Bunu değiştirmek istiyorsanız, izlenecek yolda bahsedilen her yerde değiştirmeniz gerekir.  
  
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
  
12. **Özellikler** penceresinde, AssemblyInfo.cs, program.cs, SimpleProject. ICO ve SimpleProject. myproj öğesinin **Build eylemini** **Content**olarak ayarlayın ve **VSIX özellikleri içindeki Include** değerlerini **true**olarak ayarlayın.  
  
    Bu proje şablonu, hem hata ayıklama C# Yapılandırması hem de sürüm yapılandırması olan temel bir görsel proje tanımlar. Proje iki kaynak dosyası, AssemblyInfo.cs ve Program.cs ve çeşitli derleme başvuruları içerir. Şablondan bir proje oluşturulduğunda, Projectguıd değeri otomatik olarak yeni bir GUID ile değiştirilmiştir.  
  
    **Çözüm Gezgini**, genişletilmiş **Şablonlar** klasörü aşağıdaki gibi görünmelidir:  
  
    Şablonlar  
  
    Projeler  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject. ico  
  
    SimpleProject. myproj  
  
## <a name="creating-a-basic-project-factory"></a>Temel proje fabrikası oluşturma  
 Visual Studio 'nun proje şablonu klasörünüzün konumunu söylemeniz gerekir. Bunu yapmak için, VSPackage oluşturulduğunda şablon konumunun sistem kayıt defterine yazılması için, VSPackage sınıfına proje fabrikası uygulayan bir öznitelik ekleyin. Bir proje fabrikası GUID 'ı tarafından tanımlanan temel bir proje fabrikası oluşturarak başlayın. Proje fabrikasını SimpleProjectPackage sınıfına bağlamak için <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> özniteliğini kullanın.  
  
#### <a name="to-create-a-basic-project-factory"></a>Temel bir proje fabrikası oluşturmak için  
  
1. Kod düzenleyicisinde SimpleProjectPackageGuids.cs öğesini açın.  
  
2. Proje fabrikanızın GUID 'Leri oluşturun ( **Araçlar** menüsünde **GUID oluştur**' a tıklayın) veya aşağıdaki örnekteki birini kullanın. GUID 'Leri Simpleprojectpackageguıd sınıfına ekleyin. GUID 'Ler hem GUID biçiminde hem de dize biçiminde olmalıdır. Elde edilen kod aşağıdaki örneğe benzemelidir.  
  
   ```  
   static class SimpleProjectPackageGuids  
   {  
       public const string guidSimpleProjectPkgString =   
           "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
       public const string guidSimpleProjectCmdSetString =   
           "72c23e1d-f389-410a-b5f1-c938303f1391";  
       public const string guidSimpleProjectFactoryString =   
           "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
       public static readonly Guid guidSimpleProjectCmdSet =   
           new Guid(guidSimpleProjectCmdSetString);  
       public static readonly Guid guidSimpleProjectFactory =   
           new Guid(guidSimpleProjectFactoryString);  
   }  
   ```  
  
3. `SimpleProjectFactory.cs`adlı üst **SimpleProject** klasörüne bir sınıf ekleyin.  
  
4. Aşağıdaki using deyimlerini ekleyin:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. SimpleProjectFactory sınıfına bir Guid özniteliği ekleyin. Özniteliğin değeri, yeni proje fabrikası GUID 'sidir.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   Artık proje şablonunuzu kaydedebilirsiniz.  
  
#### <a name="to-register-the-project-template"></a>Proje şablonunu kaydetmek için  
  
1. SimpleProjectPackage.cs ' de, SimpleProjectPackage sınıfına aşağıdaki şekilde bir <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> özniteliği ekleyin.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.  
  
    Yeniden derleme proje şablonunu kaydeder.  
  
   `defaultProjectExtension` ve `possibleProjectExtensions` parametreleri proje dosya adı uzantısına ayarlanır (. Myproj). `projectTemplatesDirectory` parametresi, Şablonlar klasörünün göreli yoluna ayarlanır. Derleme sırasında, bu yol tam bir yapıya dönüştürülür ve proje sistemini kaydetmek için kayıt defterine eklenir.  
  
## <a name="testing-the-template-registration"></a>Şablon kaydını test etme  
 Şablon kaydı, Visual Studio 'Ya proje şablonu klasörünüzün konumunu söyler, böylece Visual Studio **Yeni proje** iletişim kutusunda şablon adı ve simgesini görüntüleyebilir.  
  
#### <a name="to-test-the-template-registration"></a>Şablon kaydını test etmek için  
  
1. Visual Studio 'nun deneysel örneğinde hata ayıklamaya başlamak için F5 'e basın.  
  
2. Deneysel örnekte, yeni oluşturulan proje türünden yeni bir proje oluşturun. **Yeni proje** iletişim kutusunda, **yüklü şablonlar**altında **SimpleProject** ' i görmeniz gerekir.  
  
   Artık kayıtlı bir proje fabrikasına sahipsiniz. Ancak, henüz bir proje oluşturamaz. Proje paketi ve proje fabrikası bir proje oluşturmak ve başlatmak için birlikte çalışır.  
  
## <a name="add-the-managed-package-framework-code"></a>Yönetilen paket çerçevesi kodunu ekleyin  
 Proje paketiyle proje fabrikası arasındaki bağlantıyı uygulayın.  
  
- Yönetilen paket çerçevesi için kaynak kodu dosyalarını içeri aktarın.  
  
    1. SimpleProject projesini kaldırın ( **Çözüm Gezgini**, proje düğümünü seçin ve bağlam menüsünde **Projeyi Kaldır**' a tıklayın.) ve proje dosyasını XML düzenleyicisinde açın.  
  
    2. Aşağıdaki blokları proje dosyasına ekleyin (\<Içeri aktarma > bloklarının hemen üzerinde). ProjectBasePath öğesini, indirdiğiniz yönetilen paket çerçeve kodundaki ProjectBase. Files dosyasının konumuna ayarlayın. Yol adına bir ters eğik çizgi eklemeniz gerekebilir. Bunu yapmazsanız, proje yönetilen paket çerçevesi kodunu bulamamasına neden olabilir.  
  
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
  
        - Microsoft. VisualStudio. Designer. Interfaces (\<VSSDK Install > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        - WindowsBase  
  
        - Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Proje fabrikasını başlatmak için  
  
1. SimpleProjectPackage.cs dosyasında aşağıdaki `using` ifadesini ekleyin.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. `SimpleProjectPackage` sınıfını `Microsoft.VisualStudio.Package.ProjectPackage`türet.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. Proje fabrikasını kaydedin. Aşağıdaki satırı, `base.Initialize`hemen sonra `SimpleProjectPackage.Initialize` yöntemine ekleyin.  
  
    ```  
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
  
5. SimpleProjectFactory.cs ' de, mevcut `using` deyimlerinden sonra aşağıdaki `using` deyimini ekleyin.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. `SimpleProjectFactory` sınıfını `ProjectFactory`türet.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. Aşağıdaki kukla yöntemi `SimpleProjectFactory` sınıfına ekleyin. Bu yöntemi sonraki bir bölümde uygulayacaksınız.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. Aşağıdaki alanı ve oluşturucuyu `SimpleProjectFactory` sınıfına ekleyin. Bu `SimpleProjectPackage` başvurusu bir özel alanda önbelleğe alınır, böylece bir hizmet sağlayıcı sitesi ayarlamada kullanılabilir.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.  
  
## <a name="testing-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etme  
 Proje fabrikası uygulamanızın oluşturucusunun adlandırılıp çağrılmadığını test edin.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Proje fabrikası uygulamasını test etmek için  
  
1. SimpleProjectFactory.cs dosyasında, `SimpleProjectFactory` oluşturucusunun aşağıdaki satırında bir kesme noktası ayarlayın.  
  
    ```  
    this.package = package;  
    ```  
  
2. Visual Studio 'nun deneysel bir örneğini başlatmak için F5 tuşuna basın.  
  
3. Deneysel örnekte, yeni bir proje oluşturmaya başlayın. **Yeni proje** iletişim kutusunda, SimpleProject proje türünü seçin ve ardından **Tamam**' a tıklayın. Yürütme kesme noktasında durmaktadır.  
  
4. Kesme noktasını temizle ve hata ayıklamayı Durdur. Henüz bir proje düğümü oluşturmadınız, proje oluşturma kodu hala özel durumlar oluşturuyor.  
  
## <a name="extending-the-project-node-class"></a>Proje düğümü sınıfını genişletme  
 Artık `ProjectNode` sınıfından türeten `SimpleProjectNode` sınıfını uygulayabilirsiniz. `ProjectNode` temel sınıfı, proje oluşturma için aşağıdaki görevleri işler:  
  
- SimpleProject. myproj proje şablon dosyasını yeni proje klasörüne kopyalar. Kopya, **Yeni proje** iletişim kutusuna girilen ada göre yeniden adlandırılır. `ProjectGuid` özelliği değeri yeni bir GUID ile değiştirilmiştir.  
  
- , SimpleProject. myproj proje şablon dosyasının MSBuild öğelerine erişir ve `Compile` öğeleri arar. Her bir `Compile` hedef dosya için dosyayı yeni proje klasörüne kopyalar.  
  
  Türetilmiş `SimpleProjectNode` sınıfı şu görevleri gerçekleştirir:  
  
- **Çözüm Gezgini** veya seçilmesi için proje ve dosya düğümlerinin simgelerini sağlar.  
  
- Ek proje şablonu parametre değişimlerin belirtilmesini sağlar.  
  
#### <a name="to-extend-the-project-node-class"></a>Proje düğümü sınıfını genişletmek için  
  
1. 
  
2. `SimpleProjectNode.cs`adlı bir sınıf ekleyin.  
  
3. Mevcut kodu aşağıdaki kodla değiştirin.  
  
   ```  
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
               get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
   Bu `SimpleProjectNode` sınıfı uygulamasının bu geçersiz kılınan yöntemleri vardır:  
  
- proje fabrikası GUID 'sini döndüren `ProjectGuid`.  
  
- Proje türünün yerelleştirilmiş adını döndüren `ProjectType`.  
  
- Seçili dosyaları şablon klasöründen hedef projeye kopyalayan `AddFileFromTemplate`. Bu yöntem daha sonraki bir bölümde daha da uygulanabilir.  
  
  `SimpleProjectFactory` Oluşturucusu gibi `SimpleProjectNode` Oluşturucu, daha sonra kullanmak üzere bir özel alanda `SimpleProjectPackage` başvurusunu önbelleğe alır.  
  
  `SimpleProjectFactory` sınıfını `SimpleProjectNode` sınıfına bağlamak için, `SimpleProjectFactory.CreateProject` yönteminde yeni bir `SimpleProjectNode` örneği oluşturmanız ve daha sonra kullanmak üzere özel bir alanda önbelleğe almanız gerekir.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Project Factory sınıfını ve Node sınıfını bağlamak için  
  
1. SimpleProjectFactory.cs dosyasında aşağıdaki `using` ifadesini ekleyin:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. Aşağıdaki kodu kullanarak `SimpleProjectFactory.CreateProject` yöntemini değiştirin.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. Çözümü yeniden oluşturun ve hata olmadan oluşturulduğunu doğrulayın.  
  
## <a name="testing-the-project-node-class"></a>Proje düğümü sınıfını test etme  
 Proje fabrikasını bir proje hiyerarşisi oluşturup oluşturmadığını görmek için test edin.  
  
#### <a name="to-test-the-project-node-class"></a>Proje düğümü sınıfını test etmek için  
  
1. Hata ayıklamayı başlatmak için F5 'e basın. Deneysel örnekte, yeni bir SimpleProject oluşturun.  
  
2. Visual Studio proje oluşturmak için proje fabrikasını çağırmalıdır.  
  
3. Visual Studio'nun deneysel örneği kapatın.  
  
## <a name="adding-a-custom-project-node-icon"></a>Özel proje düğümü simgesi ekleme  
 Önceki bölümdeki proje düğümü simgesi varsayılan simgedir. Bunu özel bir simge olarak değiştirebilirsiniz.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Özel bir proje düğümü simgesi eklemek için  
  
1. **Kaynaklar** klasöründe, SimpleProjectNode. bmp adlı bir bit eşlem dosyası ekleyin.  
  
2. **Özellikler** penceresinde bit eşlemi 16 ile 16 piksel azaltın. Bit eşlemi farklı hale getirin.  
  
    ![Basit proje Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. **Özellikler** penceresinde, bit eşlemin **derleme eylemini** **katıştırılmış kaynak**olarak değiştirin.  
  
4. SimpleProjectNode.cs ' de aşağıdaki `using` deyimlerini ekleyin:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Aşağıdaki statik alanı ve oluşturucuyu `SimpleProjectNode` sınıfına ekleyin.  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Aşağıdaki özelliği `SimpleProjectNode` sınıfının başına ekleyin.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Örnek oluşturucusunu aşağıdaki kodla değiştirin.  
  
   ```  
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
  
   Statik oluşturma sırasında `SimpleProjectNode`, derleme bildirim kaynaklarından proje düğümü bit eşlemini alır ve daha sonra kullanmak üzere özel bir alanda önbelleğe alır. <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> resim yolunun söz dizimini görürsünüz. Bir derlemeye gömülü olan bildirim kaynaklarının adlarını görmek için <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> yöntemini kullanın. Bu yöntem `SimpleProject` derlemesine uygulandığında, sonuçlar aşağıdaki gibi olmalıdır:  
  
- SimpleProject. resources. resources  
  
- VisualStudio. Project. resources  
  
- SimpleProject.VSPackage.resources  
  
- Resources. imagelis. bmp  
  
- Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
- Microsoft. VisualStudio. Project. SecurityWarningDialog. resources  
  
- SimpleProject. resources. SimpleProjectNode. bmp  
  
  Örnek oluşturma sırasında `ProjectNode` temel sınıfı, Resources\imagelis.bmp. 'den yaygın olarak kullanılan 16 x 16 bit eşlem olan resources. imagelis. bmp yükler. Bu bit eşlem listesi ImageHandler. ImageList olarak `SimpleProjectNode` kullanılabilir hale getirilir. `SimpleProjectNode`, proje düğümü bit eşlemini listeye ekler. Görüntü listesindeki proje düğümü bit eşleminin, daha sonra public `ImageIndex` özelliğinin değeri olarak kullanılmak üzere önbelleğe alınır. Visual Studio, proje düğümü simgesi olarak hangi bit eşlemin gösterileceğini öğrenmek için bu özelliği kullanır.  
  
## <a name="testing-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etme  
 Özel proje düğümünüz simgenizi içeren bir proje hiyerarşisi oluşturup oluşturmadığını görmek için proje fabrikasını test edin.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Özel proje düğümü simgesini test etmek için  
  
1. Hata ayıklamayı başlatın ve deneysel örnekte yeni bir SimpleProject oluşturun.  
  
2. Yeni oluşturulan projede, SimpleProjectNode. bmp ' nin proje düğümü simgesi olarak kullanıldığını görürsünüz.  
  
     ![Basit proje yeni proje düğümü](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3. Kod düzenleyicisinde Program.cs öğesini açın. Aşağıdaki koda benzer kaynak kodu görmeniz gerekir.  
  
    ```  
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
  
     $NameSpace $ ve $className $ şablon parametrelerinin yeni değerlere sahip olmadığına dikkat edin. Bir sonraki bölümde şablon parametre değişimini nasıl uygulayacağınızı öğreneceksiniz.  
  
## <a name="substituting-template-parameters"></a>Şablon parametrelerini değiştirme  
 Daha önceki bir bölümde, `ProvideProjectFactory` özniteliğini kullanarak proje şablonunu Visual Studio ile kaydettiniz. Bir şablon klasörünün yolunu bu şekilde kaydetme, `ProjectNode.AddFileFromTemplate` sınıfını geçersiz kılarak ve genişleterek temel şablon parametre değişimini etkinleştirmenizi sağlar. Daha fazla bilgi için bkz. [Yeni proje oluşturma: Ikinci bölüm altında](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Şimdi `AddFileFromTemplate` sınıfına değiştirme kodu ekleyin.  
  
#### <a name="to-substitute-template-parameters"></a>Şablon parametrelerini koymak için  
  
1. SimpleProjectNode.cs dosyasında aşağıdaki `using` ifadesini ekleyin.  
  
   ```  
   using System.IO;  
   ```  
  
2. Aşağıdaki kodu kullanarak `AddFileFromTemplate` yöntemini değiştirin.  
  
   ```  
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
  
3. Yönteminde, `className` atama ifadesinden hemen sonra bir kesme noktası ayarlayın.  
  
   Atama deyimleri, bir ad alanı ve yeni bir sınıf adı için makul değerler belirlenir. İki `ProjectNode.FileTemplateProcessor.AddReplace` yöntemi çağrısı, bu yeni değerleri kullanarak karşılık gelen şablon parametre değerlerini değiştirir.  
  
## <a name="testing-the-template-parameter-substitution"></a>Şablon parametre değişimini test etme  
 Artık şablon parametre değişimini test edebilirsiniz.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Şablon parametre değişimini test etmek için  
  
1. Hata ayıklamayı başlatın ve deneysel örnekte yeni bir SimpleProject oluşturun.  
  
2. Yürütme `AddFileFromTemplate` yönteminde kesme noktasında durmaktadır.  
  
3. `nameSpace` ve `className` parametrelerinin değerlerini inceleyin.  
  
   - `nameSpace`, \Templates\ısısimpsimpproject\simpleproject.exe. myproj proje şablonu dosyasında \<RootNamespace > öğesinin değeri olarak verilir. Bu durumda, değer "MyRootNamespace" olur.  
  
   - `className`, dosya adı uzantısı olmadan sınıf kaynak dosya adının değeri olarak verilir. Bu durumda, hedef klasöre kopyalanacak ilk dosya AssemblyInfo.cs; Bu nedenle, className değeri "AssemblyInfo" olur.  
  
4. Kesme noktasını kaldırın ve yürütmeye devam etmek için F5 'e basın.  
  
    Visual Studio 'Nun bir proje oluşturmayı tamamlaması gerekir.  
  
5. Kod düzenleyicisinde Program.cs öğesini açın. Aşağıdaki koda benzer kaynak kodu görmeniz gerekir.  
  
   ```  
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
  
    Ad alanının artık "MyRootNamespace" olduğuna ve sınıf adının artık "program" olduğuna dikkat edin.  
  
6. Projede hata ayıklamayı başlatın. Yeni projenin derlenmesi, çalıştırması ve "Hello VSX!!!" görüntülemesi gerekir Konsol penceresinde.  
  
    ![Basit proje komutu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   Tebrikler! Temel yönetilen bir proje sistemi uyguladık.
