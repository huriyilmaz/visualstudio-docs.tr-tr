---
title: 'İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 891b0f1197ad178a705de5d64026beebc62615dd
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826503"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma
.NET Framework hedefleyen programlama dilleri, uygulama derleme sürecini anlatmak ve denetlemek için MSBuild proje dosyalarını kullanır. MSBuild proje dosyası oluşturmak için Visual Studio kullandığınızda, uygun XML dosyaya otomatik olarak eklenir. Ancak, XML 'nin nasıl düzenlendiğini ve bir derlemeyi denetlemek için nasıl değiştirileceğini anlamak yararlı olabilir.

 Bir C++ proje için proje dosyası oluşturma hakkında daha fazla bilgi için bkz. [MSBuildC++()](/cpp/build/msbuild-visual-cpp).

 Bu izlenecek yol, yalnızca bir metin Düzenleyicisi kullanılarak nasıl basit bir proje dosyası oluşturulduğunu gösterir. İzlenecek yol aşağıdaki adımları izler:

1. En az uygulama kaynak dosyası oluşturun.

2. En az MSBuild proje dosyası oluşturun.

3. PATH ortam değişkenini MSBuild içerecek şekilde genişletin.

4. Proje dosyasını kullanarak uygulamayı oluşturun.

5. Derlemeyi denetlemek için özellikler ekleyin.

6. Özellik değerlerini değiştirerek derlemeyi denetleyin.

7. Yapıya hedef ekleyin.

8. Hedefleri belirterek derlemeyi denetleyin.

9. Artımlı olarak oluşturun.

Bu izlenecek yol, komut isteminde projenin nasıl oluşturulacağını gösterir ve sonuçları inceleyin. MSBuild ve MSBuild 'in komut isteminde nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [Izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).

İzlenecek yolu tamamlamak için, .NET Framework (sürüm 2,0, 3,5, 4,0, 4,5 veya üzeri) yüklü olması gerekir, çünkü bu izlenecek yol için gereken MSBuild ve görsel C# derleyicisini içerir.

## <a name="create-a-minimal-application"></a>En az uygulama oluşturma
 Bu bölümde, bir metin düzenleyicisi kullanarak en C# az bir uygulama kaynak dosyasının nasıl oluşturulacağı gösterilmektedir.

1. Komut isteminde, uygulamayı oluşturmak istediğiniz klasöre göz atın, örneğin, *\Documents\\* veya *\Desktop\\* .

2. *\Helloworld\\* adlı bir alt klasör oluşturmak Için **md HelloWorld** yazın.

3. Yeni klasöre geçmek için **CD HelloWorld** yazın.

4. Not defteri veya başka bir metin düzenleyicisini başlatın ve ardından aşağıdaki kodu yazın.

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. Bu kaynak kodu dosyasını kaydedin ve *HelloWorld.cs*olarak adlandırın.

6. Komut istemine **csc helloworld.cs** yazarak uygulamayı derleyin.

7. Komut isteminde **HelloWorld** yazarak uygulamayı test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

8. Komut istemine **del helloworld. exe** yazarak uygulamayı silin.

## <a name="create-a-minimal-msbuild-project-file"></a>En az MSBuild proje dosyası oluşturma
 Artık en az bir uygulama kaynak dosyanız olduğuna göre, uygulamayı derlemek için en az bir proje dosyası oluşturabilirsiniz. Bu proje dosyası aşağıdaki öğeleri içerir:

- Gerekli kök `Project` düğümü.

- Öğe öğeleri içeren bir `ItemGroup` düğümü.

- Uygulama kaynak dosyasına başvuran bir öğe öğesi.

- Uygulamayı derlemek için gereken görevleri içeren bir `Target` düğümü.

- Uygulamayı derlemek için Visual C# derleyicisini başlatmak üzere bir `Task` öğesi.

### <a name="to-create-a-minimal-msbuild-project-file"></a>En az MSBuild proje dosyası oluşturmak için

1. Metin düzenleyicisinde, varolan metni şu iki satırı kullanarak değiştirin:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Bu `ItemGroup` düğümünü `Project` düğümünün alt öğesi olarak ekleyin:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Bu `ItemGroup` zaten bir öğe öğesi içerdiğini unutmayın.

3. `Project` düğümünün alt öğesi olarak bir `Target` düğümü ekleyin. Düğümü `Build`olarak adlandırın.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Bu görev öğesini `Target` düğümünün alt öğesi olarak ekle:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Bu proje dosyasını kaydedin ve *HelloWorld. csproj*olarak adlandırın.

Minimum proje dosyanız aşağıdaki koda benzemelidir:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

Yapı hedefi içindeki görevler sırayla yürütülür. Bu durumda, Visual C# Compiler `Csc` görevi tek görevdir. Derlemek için kaynak dosyalarının bir listesini bekler ve bu, `Compile` öğenin değeri tarafından verilir. `Compile` öğesi yalnızca bir kaynak dosyaya başvuruyor, *HelloWorld.cs*.

> [!NOTE]
> Öğe öğesinde, *. cs* dosya adı uzantısına sahip tüm dosyalara şu şekilde başvurmak için yıldız joker karakterini (\*) kullanabilirsiniz:
>
> ```xml
> <Compile Include="*.cs" />
> ```
>
> Ancak, kaynak dosyalar eklenirse veya silinirse hata ayıklamayı ve seçmeli hedefleri daha zor hale getiren joker karakter karakterlerinin kullanımını önermiyoruz.

## <a name="extend-the-path-to-include-msbuild"></a>Yolu MSBuild 'i içerecek şekilde genişletin

MSBuild 'e erişebilmek için, PATH ortam değişkenini .NET Framework klasörü içerecek şekilde genişletmeniz gerekir.

Visual Studio 2013 başlayarak, MSBuild *. exe* *' yi msbuild klasöründe (32* bitlik bir Işletim sisteminde veya *% ProgramFiles (x86)% \* ' de 64 bit işletim sisteminde MSBuild) bulabilirsiniz.

Komut isteminde **set path =% path%;%ProgramFiles%\MSBuild** veya **set PATH =% Path%;% ProgramFiles (x86)% \ MSBuild**yazın.

Alternatif olarak, Visual Studio yüklüyse, *MSBuild* klasörünü içeren bir yol Içeren **visual Studio için geliştirici komut istemi**kullanabilirsiniz.

## <a name="build-the-application"></a>Uygulama oluşturma
 Şimdi, uygulamayı derlemek için yeni oluşturduğunuz proje dosyasını kullanın.

1. Komut isteminde **MSBuild HelloWorld. csproj-t:Build**yazın.

     Bu, HelloWorld uygulamasını oluşturmak için Visual C# derleyicisini çağırarak HelloWorld proje dosyasının yapı hedefini oluşturur.

2. **HelloWorld**yazarak uygulamayı test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

> [!NOTE]
> Ayrıntı düzeyini artırarak derleme hakkında daha fazla ayrıntı görebilirsiniz. Ayrıntı düzeyini "ayrıntılı" olarak ayarlamak için komut isteminde şu komutu yazın:
>
> **MSBuild HelloWorld. csproj-t:Build-ayrıntı düzeyi: ayrıntılı**

## <a name="add-build-properties"></a>Derleme özellikleri ekle
 Derlemeyi daha fazla denetleyebilmeniz için proje dosyasına yapı özellikleri ekleyebilirsiniz. Şimdi şu özellikleri ekleyin:

- Uygulamanın adını belirtmek için bir `AssemblyName` özelliği.

- Uygulamayı içerecek bir klasörü belirtmek için bir `OutputPath` özelliği.

### <a name="to-add-build-properties"></a>Derleme özellikleri eklemek için

1. Komut istemine **del helloworld. exe** yazarak mevcut uygulamayı silin.

2. Proje dosyasında, açma `Project` öğesinden hemen sonra bu `PropertyGroup` öğesini ekleyin:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Bu görevi, `Csc` görevden hemen önce derleme hedefine ekleyin:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     `MakeDir` görevi, bu adı taşıyan hiçbir klasör mevcut olmadığından, `OutputPath` özelliği tarafından adlandırılan bir klasör oluşturur.

4. Bu `OutputAssembly` özniteliğini `Csc` görevine ekleyin:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     Bu, Visual C# derleyicisine `AssemblyName` özelliği tarafından adlandırılan bir derleme üretmesini ve `OutputPath` özelliği tarafından adlandırılan klasöre yerleştirmesini sağlar.

5. Değişikliklerinizi kaydedin.

Proje dosyanız şimdi aşağıdaki koda benzemelidir:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> `Csc` görevinin `OutputAssembly` özniteliğinde eklemek yerine, `OutputPath` öğesinde belirttiğinizde, klasör adının sonuna ters eğik çizgi (\\) yol sınırlayıcısı eklemenizi öneririz. Dolayısıyla
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`
>
> şundan daha iyidir
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Yapı özelliklerini test etme
 Artık, çıkış klasörünü ve uygulama adını belirtmek için yapı özelliklerini kullandığınız proje dosyasını kullanarak uygulamayı oluşturabilirsiniz.

1. Komut isteminde **MSBuild HelloWorld. csproj-t:Build**yazın.

     Bu, *\bin\\* klasörünü oluşturur ve ardından Visual C# derleyicisini çağırır ve *MSBuildSample* uygulamasını oluşturmak ve bunu *\Bin\\* klasörüne koyar.

2. *\Bin\\* klasörünün oluşturulduğunu ve *MSBuildSample* uygulamasını içerdiğini doğrulamak Için, tür **dir bin**.

3. Uygulamayı **Bin\msbuildsample**yazarak test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

## <a name="add-build-targets"></a>Derleme hedefleri Ekle
 Daha sonra, proje dosyasına aşağıdaki gibi iki hedef ekleyin:

- Eski dosyaları silen temiz bir hedef.

- Temizleme görevinin, derleme görevinden önce çalıştırılmasını zorlamak için `DependsOnTargets` özniteliğini kullanan bir yeniden oluşturma hedefi.

Artık birden çok hedef olduğuna göre, derleme hedefini varsayılan hedef olarak ayarlayabilirsiniz.

### <a name="to-add-build-targets"></a>Derleme hedefleri eklemek için

1. Proje dosyasında, derleme hedefinden hemen sonra bu iki hedefi ekleyin:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Temizleme hedefi, uygulamayı silmek için silme görevini çağırır. Yeniden oluşturma hedefi, hem Temizleme hedefi hem de derleme hedefi çalıştırılıncaya kadar çalışmaz. Yeniden oluşturma hedefinin hiç görevi olmadığından, bu, temizleme hedefinin derleme hedefinden önce çalışmasına neden olur.

2. Bu `DefaultTargets` özniteliğini açılış `Project` öğesine ekleyin:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Bu, derleme hedefini varsayılan hedef olarak ayarlar.

Proje dosyanız şimdi aşağıdaki koda benzemelidir:

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>Derleme hedeflerini test etme
 Proje dosyasının bu özelliklerini test etmek için yeni derleme hedeflerini kullanabilirsiniz:

- Varsayılan derleme oluşturuluyor.

- Uygulama adı komut isteminde ayarlanıyor.

- Başka bir uygulama oluşturulmadan önce uygulamayı silme.

- Başka bir uygulama oluşturmadan uygulamayı silme.

### <a name="to-test-the-build-targets"></a>Derleme hedeflerini test etmek için

1. Komut isteminde **MSBuild HelloWorld. csproj-p:AssemblyName = Greetings**yazın.

     Hedefi açıkça ayarlamak için **-t** anahtarını kullanmadınız, MSBuild varsayılan derleme hedefini çalıştırır. **-P** anahtarı `AssemblyName` özelliğini geçersiz kılar ve `Greetings`yeni bir değer verir. Bu, yeni bir uygulama olan *Greetings. exe*' nin *\Bin\\* klasöründe oluşturulmasına neden olur.

2. *\Bin\\* klasörünün hem *MSBuildSample* uygulamasını hem de yeni *Greetings* uygulamasını içerdiğini doğrulamak için, **dir bin**yazın.

3. **Bin\Greetings**yazarak Greetings uygulamasını test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

4. **MSBuild HelloWorld. csproj-t:Clean**yazarak MSBuildSample uygulamasını silin.

     Bu, varsayılan `AssemblyName` özellik değerine sahip uygulamayı kaldırmak için temizleme görevini çalıştırır `MSBuildSample`.

5. **MSBuild HelloWorld. csproj-t:Clean-p:AssemblyName = Greetings**yazarak Greetings uygulamasını silin.

     Bu, belirtilen **AssemblyName** özellik değerine sahip uygulamayı kaldırmak için temizleme görevini çalıştırır, `Greetings`.

6. *\Bin\\* klasörünün artık boş olduğunu doğrulamak için, **dir bin**yazın.

7. **MSBuild**yazın.

     Bir proje dosyası belirtilmese de, geçerli klasörde yalnızca bir proje dosyası olduğundan MSBuild *HelloWorld. csproj* dosyasını oluşturur. Bu, *MSBuildSample* uygulamasının *\Bin\\* klasöründe oluşturulmasına neden olur.

     *\Bin\\* klasörünün *MSBuildSample* uygulamasını içerdiğini doğrulamak Için, tür **dir bin**.

## <a name="build-incrementally"></a>Artımlı olarak derleyin
 MSBuild 'i yalnızca hedef dosya veya hedefin bağımlı olduğu hedef dosyalar değiştiyse bir hedef oluşturmak için söyleyebilirsiniz. MSBuild, değiştirilip değiştirilmediğini anlamak için bir dosyanın zaman damgasını kullanır.

### <a name="to-build-incrementally"></a>Artımlı olarak derlemek için

1. Proje dosyasında, bu öznitelikleri açma derleme hedefine ekleyin:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Bu, derleme hedefinin `Compile` öğesi grubunda belirtilen giriş dosyalarına ve çıktı hedefinin uygulama dosyası olduğunu belirtir.

     Elde edilen derleme hedefi aşağıdaki koda benzemelidir:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Komut istemine **MSBuild-v:d** yazarak derleme hedefini test edin.

     *HelloWorld. csproj* ' ın varsayılan proje dosyası olduğunu ve bu derleme varsayılan hedef olduğunu unutmayın.

     **-V:d** anahtarı yapı işlemi için ayrıntılı bir açıklama belirtir.

     Bu satırlar görüntülenmelidir:

     **Tüm çıkış dosyaları giriş dosyalarına göre güncel olduğundan "Build" hedefi atlanıyor.**

     **Giriş dosyaları: HelloWorld.cs**

     **Çıkış dosyaları: BinMSBuildSample. exe**

     Uygulama son derlenmesinden bu yana kaynak dosyalardan hiçbiri değişmediğinden MSBuild, derleme hedefini atlar.

## <a name="c-example"></a>C#örneğinde

Aşağıdaki örnek, bir C# uygulamayı derleyen ve çıkış dosyası adını içeren bir iletiyi kaydeden bir proje dosyası gösterir.

### <a name="code"></a>Kod

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="visual-basic-example"></a>Visual Basic örneği

Aşağıdaki örnek, bir Visual Basic uygulamasını derleyen ve çıkış dosyası adını içeren bir iletiyi kaydeden bir proje dosyası gösterir.

### <a name="code"></a>Kod

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>Sırada ne var?
 Visual Studio, bu kılavuzda gösterilen çalışmanın çoğunu otomatik olarak yapabilir. MSBuild proje dosyalarını oluşturmak, düzenlemek, derlemek ve test etmek için Visual Studio 'Yu nasıl kullanacağınızı öğrenmek için bkz. [Izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild genel bakış](../msbuild/msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
