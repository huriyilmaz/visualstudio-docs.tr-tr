---
title: 'Walkthrough: Sıfırdan MSBuild Proje Dosyası Oluşturma | Microsoft Dokümanlar'
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
ms.openlocfilehash: 5fe9f052c10f31c4db0f8bf09f273be5814ff732
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263142"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Walkthrough: Sıfırdan bir MSBuild proje dosyası oluşturma

.NET Framework'u hedefleyen programlama dilleri, uygulama oluşturma işlemini açıklamak ve denetlemek için MSBuild proje dosyalarını kullanır. Bir MSBuild proje dosyası oluşturmak için Visual Studio'yu kullandığınızda, dosyaya otomatik olarak uygun XML eklenir. Ancak, XML'in nasıl düzenlendiğini ve bir yapıyı denetlemek için nasıl değiştirebileceğinizi anlamanız yararlı olabilir.

 Bir C++ projesi için proje dosyası oluşturma hakkında bilgi için [MSBuild (C++)](/cpp/build/msbuild-visual-cpp)bakın.

 Bu gözden geçirme, yalnızca bir metin düzenleyicisi kullanarak temel bir proje dosyasının nasıl artımlı olarak oluşturulacak şekilde oluşturulabildiğini gösterir. İznin izlemesi aşağıdaki adımları izler:

1. En az uygulama kaynağı dosyası oluşturun.

2. En az MSBuild proje dosyası oluşturun.

3. PATH ortamı değişkenini MSBuild'i içerecek şekilde genişletin.

4. Proje dosyasını kullanarak uygulamayı oluşturun.

5. Yapıyı denetlemek için özellikler ekleyin.

6. Özellik değerlerini değiştirerek yapıyı denetle.

7. Yapıya hedefler ekleyin.

8. Hedefleri belirterek yapıyı denetle.

9. Artımlı olarak oluşturun.

Bu gözden geçirme komut isteminde projenin nasıl inşa edilebildiğini ve sonuçları nasıl inceleyeceğini gösterir. MSBuild hakkında daha fazla bilgi ve komut isteminde MSBuild'in nasıl çalıştırılabildiğini öğrenmek için [Walkthrough: MSBuild'i kullanın.](../msbuild/walkthrough-using-msbuild.md)

İzlemi tamamlamak için,.NET Framework'ü (sürüm 2.0, 3.5, 4.0 veya daha sonra) MSBuild ve visual C# derleyicisini içerdiğinden yüklü olmalıdır.

## <a name="create-a-minimal-application"></a>En az uygulama oluşturma

 Bu bölümde, metin düzenleyicisi kullanarak en az C# uygulama kaynağı dosyasının nasıl oluşturulacagın bir bölümü gösterilmektedir.

1. Komut isteminde, uygulamayı oluşturmak istediğiniz klasöre *(örneğin,\\ \Belgelerim* veya *\Masaüstü)\\*göz atın.

2. *\HelloWorld\\*adlı bir alt klasör oluşturmak için **md HelloWorld** yazın.

3. Yeni klasöre değiştirmek için **cd HelloWorld** yazın.

4. Not Defteri'ni veya başka bir metin düzenleyicisini başlatın ve ardından aşağıdaki kodu yazın.

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

5. Bu kaynak kodu dosyayı kaydedin ve *Helloworld.cs.*

6. Komut isteminde **csc helloworld.cs** yazarak uygulamayı oluşturun.

7. Komut isteminde **helloworld** yazarak uygulamayı test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

8. Komut isteminde **del helloworld.exe** yazarak uygulamayı silin.

## <a name="create-a-minimal-msbuild-project-file"></a>En az MSBuild proje dosyası oluşturma

 Artık en az uygulama kaynağı dosyanız olduğuna göre, uygulamayı oluşturmak için en az proje dosyası oluşturabilirsiniz. Bu proje dosyası aşağıdaki öğeleri içerir:

- Gerekli kök `Project` düğümü.

- Öğe `ItemGroup` öğelerini içeren bir düğüm.

- Uygulama kaynak dosyasına başvuran bir öğe öğesi.

- Uygulamayı `Target` oluşturmak için gereken görevleri içeren bir düğüm.

- Uygulamayı `Task` oluşturmak için Visual C# derleyicisini başlatacak bir öğe.

### <a name="to-create-a-minimal-msbuild-project-file"></a>En az MSBuild proje dosyası oluşturmak için

1. Metin düzenleyicisinde, varolan metni şu iki satırı kullanarak değiştirin:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Bu `ItemGroup` düğümü `Project` düğümü niçin alt öğesi olarak ekleyin:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Bunun zaten `ItemGroup` bir öğe öğesi içerdiğine dikkat edin.

3. Düğümün `Target` alt öğesi olarak bir düğüm ekleyin. `Project` Düğümü `Build`adlandırın.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Bu görev öğesini `Target` düğümün alt öğesi olarak ekleyin:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Bu proje dosyayı kaydedin ve *helloworld.csproj*adını.

En küçük proje dosyanız aşağıdaki koda benzemelidir:

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

Yap hedefindeki görevler sırayla yürütülür. Bu durumda, Visual C# `Csc` derleyici söyleyici görevi tek görevdir. Kaynak dosyaların bir listesini derlemek için bekler ve bu `Compile` öğenin değeri tarafından verilir. Öğe `Compile` yalnızca bir kaynak dosyaya başvurur, *Helloworld.cs.*

> [!NOTE]
> Öğe öğesinde, *.cs* dosya adı uzantısı\*olan tüm dosyalara başvurmak için yıldız işareti joker karakter ( ) 'yi aşağıdaki gibi kullanabilirsiniz:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="extend-the-path-to-include-msbuild"></a>Yolu MSBuild'i içerecek şekilde genişletme

MSBuild'e erişemeden önce PATH ortamı değişkenini .NET Framework klasörünü içerecek şekilde genişletmeniz gerekir.

Visual Studio 2013'ten başlayarak *MSBuild.exe'yi* MSBuild klasöründe *(%ProgramFiles%\MSBuild* 32 bit işletim sisteminde veya *%ProgramFiles(x86)%\MSBuild'te* 64 bit işletim sisteminde bulabilirsiniz).

Komut isteminde **PATH=%PATH%;%ProgramFiles%;MSBuild** veya **SET PATH=%PATH%;%ProgramFiles(x86)%\MSBuild**yazın.

Alternatif olarak, Visual Studio yüklü varsa, *MSBuild* klasörü içeren bir yolu olan **Visual Studio için Geliştirici Komut Komut Ustem Komut Ustem'i**kullanabilirsiniz.

## <a name="build-the-application"></a>Uygulama oluşturma

 Şimdi, uygulamayı oluşturmak için, yeni oluşturduğunuz proje dosyasını kullanın.

1. Komut istemi, **yazın msbuild helloworld.csproj -t:Build**.

     Bu, Helloworld uygulamasını oluşturmak için Visual C# derleyicisini çağırarak Helloworld proje dosyasının Build hedefini oluşturur.

2. **Helloworld**yazarak uygulamayı test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

> [!NOTE]
> Ayrıntılı bilgi düzeyini artırarak yapı hakkında daha fazla ayrıntı görebilirsiniz. Ayrıntılılık düzeyini "ayrıntılı" olarak ayarlamak için, komut istemine bu komutu yazın:
>
> **msbuild helloworld.csproj -t:Yapı -ayrıntılı**

## <a name="add-build-properties"></a>Yapı özellikleri ekleme

 Yapıyı daha fazla denetlemek için proje dosyasına yapı özellikleri ekleyebilirsiniz. Şimdi bu özellikleri ekleyin:

- Uygulamanın adını belirtmek için bir `AssemblyName` özellik.

- Uygulamayı `OutputPath` içerecek bir klasör belirtecek bir özellik.

### <a name="to-add-build-properties"></a>Yapı özellikleri eklemek için

1. Komut isteminde **del helloworld.exe** yazarak varolan uygulamayı silin.

2. Proje dosyasına, bu `PropertyGroup` öğeyi açılış `Project` öğesinden hemen sonra ekleyin:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Bu görevi görevden hemen önce `Csc` Yap hedefine ekleyin:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     Görev, `MakeDir` şu anda bu ada göre klasör bulunmaması koşuluyla, `OutputPath` özellik tarafından adlandırılmış bir klasör oluşturur.

4. `Csc` Göreve bu `OutputAssembly` özniteliği ekleyin:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     Bu, Visual C# derleyicisine özellik tarafından adlandırılmış `AssemblyName` bir derleme oluşturmasını `OutputPath` ve özelliğin adlandırdığı klasöre koymasını bildirir.

5. Yaptığınız değişiklikleri kaydedin.

Proje dosyanız artık aşağıdaki koda benzemelidir:

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
> Görevin\\özniteliğine `OutputPath` `OutputAssembly` `Csc` eklemek yerine, öğede belirttiğiniz zaman klasör adının sonuna ters eğik çizgi ( ) yol delimiter eklemenizi öneririz. Bu nedenle,
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`
>
> daha iyidir
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Yapı özelliklerini test edin

 Artık, çıktı klasörünü ve uygulama adını belirtmek için yapı özelliklerini kullandığınız proje dosyasını kullanarak uygulamayı oluşturabilirsiniz.

1. Komut istemi, **yazın msbuild helloworld.csproj -t:Build**.

     *\\ Bu\Bin* klasörünü oluşturur ve sonra *MSBuildSample* uygulamasını oluşturmak için Visual C# derleyicisini çağırır ve *\Bin\\ * klasörüne koyar.

2. *\\ \Bin* klasörü oluşturulduğunu ve *MSBuildSample* uygulamasını içerdiğini doğrulamak için **dir Bin**yazın.

3. **Bin\MSBuildSample**yazarak uygulamayı test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

## <a name="add-build-targets"></a>Yapı hedefleri ekleme

 Ardından, proje dosyasına aşağıdaki gibi iki hedef daha ekleyin:

- Eski dosyaları silen temiz hedef.

- Yapı görevinden `DependsOnTargets` önce Temiz görev çalışmasına zorlamak için özniteliği kullanan yeniden oluşturma hedefi.

Artık birden çok hedefiniz olduğuna göre, Yapı hedefini varsayılan hedef olarak ayarlayabilirsiniz.

### <a name="to-add-build-targets"></a>Yapı hedefleri eklemek için

1. Proje dosyasına, Yapı hedefinden hemen sonra bu iki hedefi ekleyin:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Temiz hedefi, uygulamayı silmek için Sil görevini çağırır. Yeniden Oluşturma hedefi, hem Temiz hedef hem de Yapı hedefi çalışana kadar çalışmaz. Yeniden Oluşturma hedefinin görevi olmamasına rağmen, Temiz hedefin Yapı hedefinden önce çalışmasına neden olur.

2. Bu `DefaultTargets` özniteliği açılış `Project` öğesine ekleyin:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Bu, Yapı hedefini varsayılan hedef olarak ayarlar.

Proje dosyanız artık aşağıdaki koda benzemelidir:

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

## <a name="test-the-build-targets"></a>Yapı hedeflerini test edin

 Proje dosyasının bu özelliklerini sınamak için yeni yapı hedeflerini egzersiz yapabilirsiniz:

- Varsayılan yapıyı oluşturma.

- Komut isteminde uygulama adını ayarlama.

- Başka bir uygulama oluşturulmadan önce uygulama silme.

- Başka bir uygulama oluşturmadan uygulamayı silme.

### <a name="to-test-the-build-targets"></a>Yapı hedeflerini sınamak için

1. Komut isteminde **msbuild helloworld.csproj -p:AssemblyName=Selamlar**yazın.

     **-t** anahtarını hedefi açıkça ayarlamak için kullanmadığınız için, MSBuild varsayılan Yapı hedefini çalıştırın. **-p** anahtarı `AssemblyName` özelliği geçersiz kılar ve ona `Greetings`yeni bir değer verir. Bu, *\Bin\\ * klasöründe oluşturulacak yeni bir uygulama, *Greetings.exe,* neden olur.

2. *\\ \Bin* klasöründe hem *MSBuildSample* uygulamasını hem de yeni *Karşılar* uygulamasını içerdiğini doğrulamak için **dir Bin**yazın.

3. **Bin\Greetings**yazarak Selamlar uygulamasını test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

4. **MSBuildSample uygulamasını msbuild helloworld.csproj -t:clean**yazarak silin.

     Bu, varsayılan `AssemblyName` özellik değerine sahip uygulamayı kaldırmak `MSBuildSample`için Temiz görev çalışır.

5. **msbuild helloworld.csproj -t:clean -p:AssemblyName=Greetings**yazarak Selamlar uygulamasını silin .

     Bu, verilen **AssemblyName** özellik değerine sahip uygulamayı kaldırmak `Greetings`için Temiz görevi çalıştırAr.

6. *\\ \Bin* klasörü artık boş olduğunu doğrulamak için **dir Bin**yazın.

7. **Msbuild**yazın.

     Proje dosyası belirtilmese de, geçerli klasörde yalnızca bir proje dosyası olduğundan MSBuild *helloworld.csproj* dosyasını oluşturur. Bu, *MSBuildSample* uygulamasının *\Bin\\ * klasöründe oluşturulmasına neden olur.

     *\\ \Bin* klasöründe *MSBuildSample* uygulamasını içerdiğini doğrulamak için **dir Bin**yazın.

## <a name="build-incrementally"></a>Artımlı olarak oluşturma

 MSBuild'e yalnızca hedefin bağlı olduğu kaynak dosyalar veya hedef dosyaları değiştiyse hedef oluşturmasını söyleyebilirsiniz. MSBuild, dosyanın değişip değişmediğini belirlemek için dosyanın zaman damgasını kullanır.

### <a name="to-build-incrementally"></a>Artımlı oluşturmak için

1. Proje dosyasında, bu öznitelikleri açılış Yapı hedefine ekleyin:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Bu, Yapı hedefinin `Compile` madde grubunda belirtilen giriş dosyalarına bağlı olduğunu ve çıktı hedefinin uygulama dosyası olduğunu belirtir.

     Ortaya çıkan Yapı hedefi aşağıdaki koda benzemelidir:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Komut istemine **msbuild -v:d** yazarak Yapı hedefini test edin.

     *Helloworld.csproj'un* varsayılan proje dosyası olduğunu ve Build'in varsayılan hedef olduğunu unutmayın.

     **-v:d** anahtarı, yapı işlemi için ayrıntılı bir açıklama belirtir.

     Bu satırlar görüntülenmelidir:

     **Tüm çıktı dosyaları giriş dosyalarına göre güncel olduğundan hedef "Oluştur" atlanır.**

     **Giriş dosyaları: HelloWorld.cs**

     **Çıkış dosyaları: BinMSBuildSample.exe**

     UYGULAMA son oluşturulan bu yana kaynak dosyaların hiçbiri değişmediğinden MSBuild Yapı hedefini atlar.

## <a name="c-example"></a>C# örneği

Aşağıdaki örnekte, C# uygulamasını derleyen ve çıktı dosyası adını içeren bir iletiyi günlüğe kaydeden bir proje dosyası gösterilmektedir.

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

Aşağıdaki örnek, Visual Basic uygulamasını derleyen ve çıktı dosyası adını içeren bir iletiyi günlüğe kaydeden bir proje dosyasını gösterir.

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

 Visual Studio bu izbinde gösterilen işlerin çoğunu otomatik olarak yapabilir. MSBuild proje dosyalarını oluşturmak, oluşturmak, oluşturmak ve test etmek için Visual Studio'nun nasıl kullanılacağını öğrenmek için [Bkz. Walkthrough: MSBuild'i kullanın.](../msbuild/walkthrough-using-msbuild.md)

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild'e genel bakış](../msbuild/msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
