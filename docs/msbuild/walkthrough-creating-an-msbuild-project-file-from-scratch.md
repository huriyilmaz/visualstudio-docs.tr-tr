---
title: sıfırdan MSBuild proje dosyası oluşturma
description: XML 'nin nasıl düzenlendiğini ve bir derlemeyi denetlemek üzere nasıl değiştirileceğini anlamak için sıfırdan MSBuild bir proje dosyası oluşturmayı adım adım inceleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: eace77a80823e1e47f9c685617630e2797706ae7
ms.sourcegitcommit: 76541583274c4af4218ac2a8ab4308077a7e340e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "132733185"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>izlenecek yol: sıfırdan MSBuild proje dosyası oluşturma

.NET Framework hedefleyen programlama dilleri, uygulama oluşturma işlemini anlatmak ve denetlemek için MSBuild proje dosyalarını kullanır. MSBuild bir proje dosyası oluşturmak için Visual Studio kullandığınızda, uygun XML dosyaya otomatik olarak eklenir. Ancak, XML 'nin nasıl düzenlendiğini ve bir derlemeyi denetlemek için nasıl değiştirileceğini anlamak yararlı olabilir.

 C++ projesi için proje dosyası oluşturma hakkında daha fazla bilgi için bkz. [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Bu izlenecek yol, yalnızca bir metin Düzenleyicisi kullanılarak nasıl basit bir proje dosyası oluşturulduğunu gösterir. İzlenecek yol aşağıdaki adımları izler:

1. PATH ortam değişkenini genişletin.

2. En az uygulama kaynak dosyası oluşturun.

3. en az bir proje dosyası MSBuild oluşturun.

4. Proje dosyasını kullanarak uygulamayı oluşturun.

5. Derlemeyi denetlemek için özellikler ekleyin.

6. Özellik değerlerini değiştirerek derlemeyi denetleyin.

7. Yapıya hedef ekleyin.

8. Hedefleri belirterek derlemeyi denetleyin.

9. Artımlı olarak oluşturun.

Bu izlenecek yol, komut isteminde projenin nasıl oluşturulacağını gösterir ve sonuçları inceleyin. MSBuild ve komut isteminde MSBuild çalıştırma hakkında daha fazla bilgi için bkz. [izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).

izlenecek yolu tamamlamak için Visual Studio yüklü olmalıdır, çünkü izlenecek yol için gereken MSBuild ve Visual C# derleyicisini içerir.

## <a name="extend-the-path"></a>Yolu uzat

MSBuild kullanabilmeniz için, PATH ortam değişkenini tüm gerekli araçları içerecek şekilde genişletmelidir. **Visual Studio için geliştirici komut istemi** kullanabilirsiniz. Windows görev çubuğundaki arama kutusunda Windows 10 arama yapın. ortamı sıradan bir komut isteminde veya bir betik ortamında ayarlamak için Visual Studio yüklemesinin *Common7/Tools* alt klasöründeki *VSDevCmd.bat* çalıştırın.

## <a name="create-a-minimal-application"></a>En az uygulama oluşturma

 Bu bölümde, bir metin düzenleyicisi kullanarak en az bir C# uygulama kaynak dosyasının nasıl oluşturulacağı gösterilmektedir.

1. Komut isteminde, uygulamayı oluşturmak istediğiniz klasöre göz atın, örneğin, *\Documents \\* veya *\Desktop \\*.

2. *\Helloworld \\* adlı bir alt klasör oluşturmak için **md HelloWorld** yazın.

3. Yeni klasöre geçmek için **CD HelloWorld** yazın.

4. Not Defteri veya başka bir metin düzenleyicisini başlatın ve ardından aşağıdaki kodu yazın.

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

5. Bu kaynak kodu dosyasını kaydedin ve *HelloWorld. cs* olarak adlandırın.

6. Komut istemine **csc helloworld. cs** yazarak uygulamayı oluşturun.

7. Komut isteminde **HelloWorld** yazarak uygulamayı test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

8. Komut istemine **del helloworld.exe** yazarak uygulamayı silin.

## <a name="create-a-minimal-msbuild-project-file"></a>en küçük MSBuild proje dosyası oluşturma

 Artık en az bir uygulama kaynak dosyanız olduğuna göre, uygulamayı derlemek için en az bir proje dosyası oluşturabilirsiniz. Bu proje dosyası aşağıdaki öğeleri içerir:

- Gerekli kök `Project` düğüm.

- `ItemGroup`Öğe öğeleri içeren düğüm.

- Uygulama kaynak dosyasına başvuran bir öğe öğesi.

- `Target`Uygulamayı oluşturmak için gereken görevleri içeren bir düğüm.

- `Task`Uygulamayı derlemek Için Visual C# derleyicisini başlatacak bir öğe.

### <a name="to-create-a-minimal-msbuild-project-file"></a>minimum MSBuild proje dosyası oluşturmak için

1. Metin düzenleyicisinde yeni bir dosya oluşturun ve şu iki satırı girin:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Bu `ItemGroup` düğümü düğümün alt öğesi olarak ekle `Project` :

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Bunun `ItemGroup` zaten bir öğe öğesi içerdiğine dikkat edin.

3. Düğümün `Target` alt öğesi olarak bir düğüm ekleyin `Project` . Düğümü adlandırın `Build` .

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Bu görev öğesini düğümün alt öğesi olarak ekle `Target` :

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Bu proje dosyasını kaydedin ve *HelloWorld. csproj* olarak adlandırın.

Minimum proje dosyanız aşağıdaki koda benzemelidir:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

Yapı hedefi içindeki görevler sırayla yürütülür. Bu durumda, Visual C# derleyici `Csc` görevi tek görevdir. Derlemek için kaynak dosyalarının bir listesini bekler ve bu, öğenin değeri tarafından verilir `Compile` . `Compile`Öğe yalnızca bir kaynak dosyasına ( *HelloWorld. cs*) başvuruyor.

> [!NOTE]
> Öğe öğesinde, \* *. cs* dosya adı uzantısına sahip tüm dosyalara şu şekilde başvurmak için yıldız joker karakterini () kullanabilirsiniz:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="build-the-application"></a>Uygulama oluşturma

 Şimdi, uygulamayı derlemek için yeni oluşturduğunuz proje dosyasını kullanın.

1. Komut isteminde **MSBuild HelloWorld. csproj-t:Build** yazın.

     Bu, HelloWorld uygulamasını oluşturmak için Visual C# derleyicisini çağırarak HelloWorld proje dosyasının yapı hedefini oluşturur.

2. **HelloWorld** yazarak uygulamayı test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

> [!NOTE]
> Ayrıntı düzeyini artırarak derleme hakkında daha fazla ayrıntı görebilirsiniz. Ayrıntı düzeyini "ayrıntılı" olarak ayarlamak için komut isteminde şu komutu yazın:
>
> **MSBuild HelloWorld. csproj-t:Build-ayrıntı düzeyi: ayrıntılı**

## <a name="add-build-properties"></a>Derleme özellikleri ekle

 Derlemeyi daha fazla denetleyebilmeniz için proje dosyasına yapı özellikleri ekleyebilirsiniz. Şimdi şu özellikleri ekleyin:

- `AssemblyName`Uygulamanın adını belirtmek için bir özellik.

- `OutputPath`Uygulamanın bulunduğu klasörü belirtmek için bir özellik.

### <a name="to-add-build-properties"></a>Derleme özellikleri eklemek için

1. Komut istemine **del helloworld.exe** yazarak mevcut uygulamayı silin.

2. Proje dosyasında, bu `PropertyGroup` öğeyi açılış öğesinden hemen sonra ekleyin `Project` :

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Bu görevi, görevden hemen önce derleme hedefine ekleyin `Csc` :

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     `MakeDir`Görev, `OutputPath` o ada sahip hiçbir klasör mevcut olmadığından, özelliği tarafından adlandırılan bir klasör oluşturur.

4. Bu `OutputAssembly` özniteliği `Csc` göreve ekleyin:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     Bu, Visual C# derleyicisine, özelliği tarafından adlandırılan bir derleme üretmesini `AssemblyName` ve özelliği tarafından adlandırılan klasöre yerleştirmesini sağlar `OutputPath` .

5. Yaptığınız değişiklikleri kaydedin.

Proje dosyanız şimdi aşağıdaki koda benzemelidir:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> \\ `OutputPath` Görevin özniteliğinde eklemek yerine, öğe içinde belirttiğinizde, klasör adının sonuna ters eğik çizgi () yol sınırlayıcısı eklemenizi öneririz `OutputAssembly` `Csc` . Yani:
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly="$(OutputPath)$(AssemblyName).exe" />`
>
> şundan daha iyidir
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Yapı özelliklerini test etme

 Artık, çıkış klasörünü ve uygulama adını belirtmek için yapı özelliklerini kullandığınız proje dosyasını kullanarak uygulamayı oluşturabilirsiniz.

1. Komut isteminde **MSBuild HelloWorld. csproj-t:Build** yazın.

     Bu, *\Bin \\* klasörünü oluşturur ve sonra *MSBuildSample* uygulamasını oluşturmak için Visual C# derleyicisini çağırır ve bunu *\Bin \\* klasörüne koyar.

2. *\\ \Bin* klasörünün oluşturulduğunu ve *MSBuildSample* uygulamasını içerdiğini doğrulamak için, tür **dir bin**.

3. Uygulamayı **Bin\msbuildsample** yazarak test edin.

     **Merhaba, dünya!** ileti görüntülenmelidir.

## <a name="add-build-targets"></a>Derleme hedefleri Ekle

 Daha sonra, proje dosyasına aşağıdaki gibi iki hedef ekleyin:

- Eski dosyaları silen temiz bir hedef.

- `DependsOnTargets`Temizleme görevinin, derleme görevinden önce çalıştırılmasını zorlamak için özniteliğini kullanan bir yeniden oluşturma hedefi.

Artık birden çok hedef olduğuna göre, derleme hedefini varsayılan hedef olarak ayarlayabilirsiniz.

### <a name="to-add-build-targets"></a>Derleme hedefleri eklemek için

1. Proje dosyasında, şu iki hedefi Derleme hedefinin hemen sonrası ekleyin:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Temiz hedef, uygulamayı silmek için Sil görevini çağırır. Hem Temiz hedef hem de Derleme hedefi çalıştırana kadar Yeniden Derleme hedefi çalıştırlanmaz. Yeniden Derleme hedefinin görevi yoktur ancak Temiz hedefin Derleme hedefi öncesinde çalışmasına neden olur.

2. Bu özniteliği `DefaultTargets` açılış öğesine `Project` ekleyin:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Bu, Derleme hedefini varsayılan hedef olarak ayarlar.

Proje dosyanız artık aşağıdaki koda benzeli:

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
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

## <a name="test-the-build-targets"></a>Derleme hedeflerini test etmek

 Proje dosyasının şu özelliklerini test etmek için yeni derleme hedeflerini alıştırmanız gerekir:

- Varsayılan derlemeyi oluşturma.

- Komut isteminde uygulama adını ayarlama.

- Başka bir uygulama oluşturmadan önce uygulamayı silme.

- Başka bir uygulama oluşturmadan uygulamayı silme.

### <a name="to-test-the-build-targets"></a>Derleme hedeflerini test etmek için

1. Komut isteminde **msbuild helloworld.csproj -p:AssemblyName=Greetings yazın.**

     Hedefi açıkça ayarlamak için **-t** anahtarını kullanmadınız, MSBuild derleme hedefini çalıştırır. **-p** anahtarı özelliğini geçersiz `AssemblyName` kılar ve yeni değerini `Greetings` verir. Bu, yeni bir *uygulamanınGreetings.exe*\Bin klasöründe oluşturulacak *şekilde oluşturulur. \\*

2. *\\ \Bin* klasörünün hem *MSBuildSample* uygulamasını hem de yeni *Greetings* uygulamasını içerdiğini doğrulamak için **dir Bin yazın.**

3. **Bin\Greetings** yazarak Greetings uygulamasını test edin.

     Merhaba **dünya!** iletisi görüntüleniyor.

4. **msbuild helloworld.csproj -t:clean** yazarak MSBuildSample uygulamasını silin.

     Bu, varsayılan özellik değeri olan uygulamayı kaldırmak için Temizleme `AssemblyName` görevini `MSBuildSample` çalıştırır.

5. **msbuild helloworld.csproj -t:clean -p:AssemblyName=Greetings** yazarak Greetings uygulamasını silin.

     Bu, verilen **AssemblyName** özellik değeri olan uygulamayı kaldırmak için Clean görevini `Greetings` çalıştırır.

6. *\Bin \\* klasörünün boş olduğunu doğrulamak için **dir Bin yazın.**

7. **msbuild yazın.**

     Proje dosyası belirtilmemiş olsa da, MSBuild klasörde yalnızca bir proje dosyası olduğundan *helloworld.csproj* dosyasını oluşturur. Bu, *MSBuildSample* uygulamasının *\Bin klasöründe \\ oluşturulmaya neden* olur.

     *\Bin \\* klasörünün *MSBuildSample* uygulamasını içerdiğini doğrulamak için dir Bin **yazın.**

## <a name="build-incrementally"></a>Artımlı olarak derleme

 Hedef MSBuild yalnızca hedefin bağlı olduğu kaynak dosyalar veya hedef dosyalar değişmişse, hedef oluşturması için bir şey söylemeniz gerekir. MSBuild dosyanın değişip değişmediğini belirlemek için zaman damgasını kullanır.

### <a name="to-build-incrementally"></a>Artımlı olarak derlemek için

1. Proje dosyasında, şu öznitelikleri açılış Derleme hedefine ekleyin:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Bu, Derleme hedefinin öğe grubunda belirtilen giriş dosyalarına bağlı olduğunu ve `Compile` çıkış hedefinin uygulama dosyası olduğunu belirtir.

     Sonuçta elde edilen Derleme hedefi aşağıdaki koda benzeli:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Komut istemine **msbuild -v:d yazarak** Derleme hedefini test edin.

     *helloworld.csproj dosyasının* varsayılan proje dosyası olduğunu ve Derleme'nin varsayılan hedef olduğunu unutmayın.

     **-v:d** anahtarı derleme işlemi için ayrıntılı bir açıklama belirtir.

     Bu satırlar görüntüleniyor:

     **Tüm çıkış dosyaları giriş dosyalarına göre güncel olduğundan hedef "Derleme" atlanır.**

     **Giriş dosyaları: HelloWorld.cs**

     **Çıkış dosyaları: BinMSBuildSample.exe**

     MSBuild son derlemeden bu yana kaynak dosyalardan hiçbiri değişmemiş olduğundan derleme hedefi atlar.

## <a name="c-example"></a>C# örneği

Aşağıdaki örnek, bir C# uygulamasını derleyen ve çıkış dosyası adını içeren bir iletiyi günlüğe kaydeden bir proje dosyasını gösterir.

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

## <a name="visual-basic-example"></a>Visual Basic örnek

Aşağıdaki örnek, bir Visual Basic uygulamasını derleyen ve çıkış dosyası adını içeren bir iletiyi günlüğe kaydeden bir proje dosyasını gösterir.

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

 Visual Studio, bu kılavuzda gösterilen çalışmaların büyük bir fazlasını otomatik olarak yapabiliriz. Proje dosyalarını oluşturmak, Visual Studio, derlemek ve test etmek için MSBuild kullanmayı öğrenmek için bkz. [MSBuild.](../msbuild/walkthrough-using-msbuild.md)

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild genel bakış](../msbuild/msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
