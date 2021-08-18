---
title: MSBuild kullanma
description: Bir proje dosyasının öğeler, MSBuild, özellikler, hedefler ve görevler gibi çeşitli bölümlerini öğrenin.
ms.date: 07/28/2021
ms.topic: conceptual
ms.custom: contperf-fy21q2
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 1fdd31e296050585044186e31158f893a45b095b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040066"
---
# <a name="walkthrough-use-msbuild"></a>Adım adım kılavuz: MSBuild

MSBuild, Microsoft ve Visual Studio için bir yapı platformudur. Bu izlenecek yol MSBuild'ın yapı taşlarını tanıtır ve MSBuild projelerini nasıl yazacağınızı, değiştireceğinizi ve hatalarını ayıklayacağınızı gösterir. Şu konularda bilgi edineceksiniz:

- Bir proje dosyasını oluşturma ve işleme.

- Yapı özelliklerinin kullanılması

- Yapı öğelerinin kullanılması.

komutlarını MSBuild veya Visual Studio Penceresinden **çalıştırabilirsiniz.** Bu izlenecek yolda, Visual Studio kullanarak bir MSBuild proje dosyası oluşturun. Proje dosyasını proje dosyasında Visual Studio ve projeyi **derlemek ve** sonuçları incelemek için Komut Penceresi'ne tıklayın.

## <a name="install-msbuild"></a>Yükleme MSBuild

::: moniker range="vs-2017"

Başka bir Visual Studio zaten yüklü MSBuild. MSBuild 15'i Visual Studio olmayan bir sisteme yüklemek için Visual Studio eski indirmeler'e [gidin,](https://visualstudio.microsoft.com/vs/older-downloads/) **Visual Studio 2017'yi** genişletin ve **İndir düğmesini** seçin. Visual Studio aboneliğiniz varsa, oturum açma ve **Visual Studio 2017** için Derleme Araçları'nın en son sürümünü indirme bağlantısını bulun. Visual Studio aboneliğiniz yoksa derleme araçlarının en son sürümünü yükleyebilirsiniz. Bu sayfada, sayfanın 2019 sürümüne geçmek için sürüm seçiciyi kullanın ve yükleme yönergelerini izleyin.
::: moniker-end

::: moniker range=">=vs-2019"
Başka bir Visual Studio zaten yüklü MSBuild. Visual Studio 2019 ve sonraki bir sürümü ile, Visual Studio klasörüne yüklenir. Windows 10 üzerinde tipik bir varsayılan yükleme MSBuild.exe, *MSBuild\Current\Bin* konumundaki yükleme klasörünün altındadır.

MSBuild olmayan bir sisteme yüklemek için Visual Studio indirmeler'e [Visual Studio'a](https://visualstudio.microsoft.com/downloads/) gidin ve Tüm İndirmeler'e inin **ve** ardından Visual Studio **2019** için Araçlar'ı genişletin. **MSBuild içeren Visual Studio 2019** için Derleme Araçları'.NET Core SDK. [](/dotnet/core/sdk#acquiring-the-net-core-sdk)

Yükleyicide, kullanmakta MSBuild iş yüklerinin seçili olduğundan emin olun ve Yükle'yi **seçin.**

![Yükleme MSBuild](media/walkthrough-using-msbuild/installation-msbuild-tools.png)

::: moniker-end

## <a name="create-an-msbuild-project"></a>MSBuild oluşturma

 Visual Studio proje sistemi MSBuild'i temel alır. Bu, Visual Studio kullanarak yeni bir proje dosyası oluşturmayı kolaylaştırır. Bu bölümde, bir Visual C# proje dosyası oluşturun. Bunun yerine bir Visual Basic proje dosyası oluşturmayı seçebilirsiniz. Bu anlatım bağlamında, iki proje dosyası arasındaki fark önemsizdir.

**Bir proje dosyası oluşturmak için**

1. Visual Studio açın ve proje oluşturun:

    ::: moniker range=">=vs-2019"
    Arama kutusuna **winforms yazın** ve ardından Yeni bir Windows Forms Uygulaması **(.NET Framework) seçin.** Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**

    Yeni **Project** kutusuna `BuildApp` yazın. Çözüm **için** bir Konum girin, örneğin *D: \\*.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni Project iletişim kutusunun **sol** bölmesinde **Visual C#** Windows Desktop'ı genişletin ve Windows Forms Uygulaması  >   **(.NET Framework) öğesini seçin.** Ardından **Tamam'ı seçin.**

    **Ad** kutusuna `BuildApp` yazın. Çözüm **için** bir Konum girin, örneğin *D: \\*. Çözüm için dizin oluştur **(seçili),** Kaynak Denetimine Ekle (seçili **değil)** ve Çözüm Adı ( BuildApp ) için **varsayılan** **değerleri kabul eder.**
    ::: moniker-end

1. Proje **dosyasını oluşturmak** için **Tamam'a** veya Oluştur'a tıklayın.

## <a name="examine-the-project-file"></a>Proje dosyasını inceleme

 Önceki bölümde, bir Visual C# proje dosyası oluşturmak için Visual Studio'yu kullandınız. Proje dosyası, BuildApp **Çözüm Gezgini** proje düğümü tarafından temsil edilen dosyadır. Proje dosyasını incelemek için Visual Studio kod düzenleyicisini kullanabilirsiniz.

**Projeyi dosyasını incelemek için**

1. Içinde **Çözüm Gezgini** proje düğümü **BuildApp 'e tıklayın.**

1. Özellikler **tarayıcısında,** Dosya Project *BuildApp.csproj* olduğunu unutmayın.  Tüm proje dosyaları proj soneki *ile adlandırılmıştır.* Yeni bir proje Visual Basic proje dosyası adı *BuildApp.vbproj olur.*

1. Proje düğümüne yeniden sağ tıklayın ve ardından **BuildApp.csproj'u Düzenle'ye tıklayın.** 

     Proje dosyası kod düzenleyicisinde görüntülenir.

>[!NOTE]
> Proje dosyasını açıp düzenlemeden önce C++ gibi bazı proje türleri için projeyi kaldırmanız (proje dosyasına sağ tıklar ve Projeyi **kaldır'ı** seçin) gerekir.

## <a name="targets-and-tasks"></a>Hedefler ve görevler

Project, xml biçimli dosyalardır ve kök düğümü [Project.](../msbuild/project-element-msbuild.md)

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Daha yeni .NET Core (SDK stili) projelerin bir özniteliği `Sdk` vardır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Proje SDK stilinde bir proje yoksa, xmlns ad alanını Project belirtebilirsiniz. Yeni `ToolsVersion` bir projede mevcutsa, yeni proje sürümüyle MSBuild gerekir. MSBuild sürümünü bilmiyorsanız, aşağıdaki komut satırı çıkışından (örneğin, 16.0) ilk iki sayıdan edinebilirsiniz:

```console
MSBuild -ver
```

Uygulama bina işi Hedef ve Görev [öğeleriyle](../msbuild/target-element-msbuild.md) [yapılır.](../msbuild/task-element-msbuild.md)

- Görev, işin en küçük birimdir; başka bir deyişle yapının "atom" öğesidir. Görevler, girdileri ve çıktıları olabilen bağımsız yürütülebilir bileşenlerdir. Şu anda proje dosyasında başvurulan veya tanımlanan görev yoktur. Aşağıdaki bölümlerde proje dosyasına görevler ekleyin. Daha fazla bilgi için Görevler [konu başlığına](../msbuild/msbuild-tasks.md) bakın.

- Hedef, görevlerin adlandırılmış bir dizisidir. Daha fazla bilgi için Hedefler [konu başlığına](../msbuild/msbuild-targets.md) bakın.
- [Bu, adlandırılmış bir görev dizisi olabilir, ancak kritik olarak, yapılması veya yapılması gereken bir şeyi temsil eder, bu nedenle hedef odaklı bir şekilde tanımlanmalıdır]

Varsayılan hedef proje dosyasında tanımlanmamıştır. Bunun yerine, içe aktarılan projelerde belirtilir. İçeri [Aktarma](../msbuild/import-element-msbuild.md) öğesi içeri aktarılan projeleri belirtir. Örneğin, bir C# projesinde varsayılan hedef *Microsoft.CSharp.targets dosyasından içe aktarılır.*

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

İçe aktarılan dosyalar, başvuruldukları proje dosyasına etkili biçimde dahil edilir.

SDK stili projelerde, SDK özniteliği bu dosyanın örtülü olarak içeri aktarılmış olmasına neden olduğu için bu içeri aktarma öğesini görmüyorsanız.

MSBuild, bir yapının hedeflerini izler ve her bir hedefin birden kereden fazla oluşturulmamasını sağlar.

## <a name="add-a-target-and-a-task"></a>Hedef ve görev ekleme

 Proje dosyasına bir hedef ekleyin. Bir ileti yazdıran hedefe bir görev ekleyin.

**Bir hedef ve bir görev eklemek için**

1. Bu satırları Proje dosyasına, Import deyiminden veya açılış öğesinden hemen sonra Project ekleyin.

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    Bu, HelloWorld adlı bir hedef oluşturur. Proje dosyasını düzenlerken IntelliSense desteğine sahip olduğunu unutmayın.

2. Sonuç bölümün aşağıdaki şekilde gözükmesi için HelloWorld hedefine satırlar ekleyin:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Proje dosyasını kaydedin.

İleti görevi, MSBuild ile birlikte gelen birçok görevden biridir. Kullanılabilir görevlerin ve kullanım bilgilerinin tam listesi için bkz. [Görev başvurusu.](../msbuild/msbuild-task-reference.md)

İleti görevi Metin özniteliğinin dize değerini giriş olarak alır ve çıkış cihazında görüntüler (veya varsa bir veya daha fazla günlüğe yazar). HelloWorld hedefi İleti görevini iki kere yürütür: ilki "Hello" iletisini ve diğeri ise "World" iletisini görüntülemek için.

## <a name="build-the-target"></a>Hedefi oluşturma

Bu projeyi bir Visual Studio, tanımlandığı hedefi oluşturmaz. Bunun nedeni Visual Studio varsayılan hedefi seçmesidir. Bu, yine de içe aktarılan *.targets dosyasındaki hedeftir.*

Yukarıda MSBuild HelloWorld **Geliştirici Komut İstemi** oluşturmak Visual Studio için Visual Studio hedeften aşağıdakini çalıştırın. Hedefi seçmek için -target veya -t komut satırı anahtarını kullanın.

> [!NOTE]
> Aşağıdaki bölümlerde Geliştirici Komut İstemi  **Penceresi olarak** başvurabilirsiniz.

**Hedefi oluşturmak için:**

1. Komut **Penceresini açın.**

   (Windows 10) Görev çubuğundaki arama kutusuna veya gibi aracın adını yazmaya `dev` `developer command prompt` başlayın. Bu, arama deseninize uyan yüklü uygulamaların listesini getirir.

   Dosyayı el ile bulmanız gerekirse,  dosya *visualstudioLaunchDevCmd.bat\> \Common7\Tools<* klasöründe bulunur.

2. Komut penceresinden proje dosyasını içeren klasöre (bu durumda *D:\BuildApp\BuildApp) gidin.*

3. komut anahtarıyla msbuild'i `-t:HelloWorld` çalıştırın. Bu, HelloWorld hedefini seçer ve oluşturur:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. çıkışını **Komut penceresi.** "Hello" ve "World" satırlarını görmeniz gerekir:

    ```output
    Hello
    World
    ```

> [!NOTE]
> Bunun yerine büyük `The target "HelloWorld" does not exist in the project` olasılıkla proje dosyasını kod düzenleyicisine kaydetmeyi unuttuyabilirsiniz. Dosyayı kaydedin ve yeniden deneyin.

 Kod düzenleyicisi ve komut penceresi arasında değişerek proje dosyasını değiştirebilir ve sonuçları hızlı bir şekilde görebilirsiniz.

## <a name="build-properties"></a>Derleme özellikleri

 Yapı özellikleri, yapıya rehberlik eden ad-değer çiftleridir. Birkaç yapı özelliği proje dosyasının üst kısmında zaten tanımlanmıştır:

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 Tüm özellikler PropertyGroup öğelerinin alt öğeleridir. Özelliğin adı alt öğenin adıdır ve özelliğinin değeri alt öğenin metin öğesidir. Örneğin,

```xml
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
```

 TargetFrameworkVersion adlı özelliği tanımlar ve "v4.5" dize değerini verir.

 Yapı özellikleri herhangi bir zamanda yeniden tanımlanabilir. Eğer

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 Daha sonra proje dosyasında veya proje dosyasında daha sonra içe aktarılan dosyada görünür, ardından TargetFrameworkVersion "v3.5" yeni değerini alır.

## <a name="examine-a-property-value"></a>Özellik değerini inceleme

 Bir özelliğin değerini almak için, özelliğin adı olan `PropertyName` aşağıdaki sözdizimini kullanın:

```xml
$(PropertyName)
```

Proje dosyasındaki bazı özellikleri incelemek için şu söz dizimini kullanın.

**Bir özellik değerini incelemek için**

1. Kod düzenleyicisinden HelloWorld hedefini şu kodla değiştirin:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

1. Proje dosyasını kaydedin.

1. Komut Penceresinde **şu** satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Çıkışı inceleyin. Bu iki satırı görüyor gerekir (çıkışınız farklı olabilir):

    ::: moniker range="=vs-2022"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files\Microsoft Visual Studio\2022\MSBuild\Current\Bin\amd64
    ```

    ::: moniker-end

    ::: moniker range="vs-2019"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2019\MSBuild\16.0\Bin
    ```

    ::: moniker-end
    ::: moniker range="vs-2017"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end

### <a name="conditional-properties"></a>Koşullu özellikler

gibi birçok `Configuration` özellik koşullu olarak tanımlanır, yani özniteliği özellik `Condition` öğesinde görünür. Koşullu özellikler, yalnızca koşul "doğru" olarak değerlendirilirse tanımlanır veya yeniden tanımlanır. Tanımlanmamış özelliklere boş bir dizenin varsayılan değeri verildiğini unutmayın. Örneğin,

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

"Yapılandırma Özelliği henüz tanımlanmamış ise tanımlayın ve 'Hata Ayıkla' değerini verin" anlamına gelir.

Neredeyse tüm MSBuild öğeleri bir Koşul özniteliğine sahiptir. Condition özniteliğini kullanma hakkında daha fazla tartışma için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)

### <a name="reserved-properties"></a>Ayrılmış özellikler

MSBuild, proje dosyası ve MSBuild ikili dosyaları hakkındaki bilgileri depolamak için bazı özellik adlarını saklar. MSBuildToolsPath ayrılmış bir özellik örneğidir. Ayrılmış özelliklere, diğer tüm özellikler gibi $ gösterimi ile başvurulur. Daha fazla bilgi için [bkz. Nasıl kullanılır: Proje](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) dosyasının adına veya konumuna başvurun ve MSBuild iyi [bilinen özelliklere bakın.](../msbuild/msbuild-reserved-and-well-known-properties.md)

### <a name="environment-variables"></a>Ortam değişkenleri

Proje dosyalarındaki ortam değişkenlerine yapı özellikleriyle aynı şekilde başvurabilirsiniz. Örneğin, proje dosyanızda PATH ortam değişkenini kullanmak için $(Yol) işaretini kullanın. Proje, ortam değişkeniyle ile aynı ada sahip bir özellik tanımı içeriyorsa projedeki özellik, ortam değişkeninin değerini geçersiz kılar. Daha fazla bilgi için, [bkz. How to: Use environment variables in a build](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Komut satırı özelliklerini ayarlama

Özellikler, -property veya -p komut satırı anahtarı kullanılarak komut satırı üzerinde tanımlanabilir. Komut satırından alınan özellik değerleri, proje dosyasında ve ortam değişkenlerinde ayarlanan özellik değerlerini geçersiz kılar.

**Komut satırına bir özellik değeri ayarlamak için:**

1. Komut Penceresinde **şu** satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. Çıkışı inceleyin. Şu satırı görmeniz gerekir:

    ```output
    Configuration is Release.
    ```

MSBuild, Yapılandırma özelliğini oluşturur ve bu özelliğe "Yayın" değerini verir.

## <a name="special-characters"></a>Özel karakterler

Belirli karakterlerin MSBuild proje dosyalarında özel anlamı vardır. Bu karakterler örnekleri noktalı virgülleri (;) ve yıldız işaretlerini (*) içerir. Bu özel karakterleri bir proje dosyasında değişmez değer olarak kullanmak için , karakterin ASCII onaltılık değerini temsil eden % söz dizimi kullanılarak \<xx> \<xx> belirtilmelidir.

İleti görevini, Yapılandırma özelliğinin değerini daha okunabilir yapmak için özel karakterlerle gösterecek şekilde değiştirin.

**İleti görevsinde özel karakterler kullanmak için:**

1. Kod düzenleyicisinden her iki İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. Proje dosyasını kaydedin.

1. Komut Penceresinde **şu** satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Çıkışı inceleyin. Şu satırı görmeniz gerekir:

    ```output
    $(Configuration) is "Debug"
    ```

Daha fazla bilgi için [bkz. MSBuild karakterleri.](../msbuild/msbuild-special-characters.md)

## <a name="build-items"></a>Derleme öğeleri

Öğe, yapı sistemine girdi olarak kullanılan ve genellikle bir dosya adı olan bir bilgi parçasıdır. Örneğin, kaynak dosyalarını temsil eden bir öğe koleksiyonu öğeleri bir araya derlemek için Derleme adlı bir göreve geçirilebilir.

Tüm öğeler ItemGroup öğelerinin alt öğeleridir. Öğe adı alt öğenin adıdır ve öğe değeri alt öğeye ait Dahil Etme özniteliğinin değeridir. Aynı ada sahip öğelerin değeri bu adda öğe türlerine toplanır.  Örneğin,

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

iki öğe içeren bir öğe grubunu tanımlar. Derleme öğe türünün iki değeri vardır: *Program.cs* ve *Properties\AssemblyInfo.cs*.

Aşağıdaki kod, virgülle ayrılmış şekilde her iki dosyayı tek bir Dahil Etme özniteliğinde bildirerek aynı öğe türünü oluşturur.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

> [!NOTE]
> Dosya yolları, proje dosyası içe aktarılan bir proje MSBuild bile dosya yollarını içeren klasöre göredir. Bunun için import ve [UsingTask](usingtask-element-msbuild.md) öğelerini kullanma gibi [bazı](import-element-msbuild.md) özel durumlar vardır.

## <a name="examine-item-type-values"></a>Öğe türü değerlerini inceleme

 Bir öğe türünün değerlerini almak için, ItemType'ın öğe türünün adı olduğu aşağıdaki söz dizimini kullanın:

```xml
@(ItemType)
```

Proje dosyasındaki Derleme öğe türünü incelemek için şu söz dizimini kullanın.

**Öğe türü değerlerini incelemek için:**

1. Kod düzenleyicisinden HelloWorld hedef görevini şu kodla değiştirin:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. Proje dosyasını kaydedin.

1. Komut Penceresinde **şu** satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Çıkışı inceleyin. Şu uzun satırı görmeniz gerekir:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Bir öğe türünün değerleri varsayılan olarak virgüllerle ayrılır.

Bir öğe türünün ayracını değiştirmek için, ItemType'ın öğe türü ve Ayırıcı'nın bir veya daha fazla ayırma karakterinin dizesi olduğu aşağıdaki söz dizimini kullanın:

```xml
@(ItemType, Separator)
```

Her satırda bir tane Derleme öğesi görüntülemek için taşıma dönüşlerini ve satır beslemelerini (%0A%0D) kullanmak üzere İleti görevini değiştirin.

**Her satırda bir tane öğe türü değeri görüntülemek için**

1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. Proje dosyasını kaydedin.

3. Komut Penceresinde **şu** satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Çıkışı inceleyin. Şu satırları görmeniz gerekir:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Dahil, Dışla ve joker karakterler

 Öğe türüne öğe eklemek için Include özniteliğiyle "*", " " " ve "?" joker \* \* karakterlerini kullanabilirsiniz. Örneğin,

```xml
<Photos Include="images\*.jpeg" />
```

 *resimler* klasöründeki *. jpeg* uzantılı tüm dosyaları fotoğraflar öğe türüne ekler, ancak

```xml
<Photos Include="images\**\*.jpeg" />
```

 *resimler* klasöründe ve tüm alt klasörlerindeki *. jpeg* uzantılı tüm dosyaları fotoğraflar öğe türüne ekler. Daha fazla örnek için bkz. [nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).

 Öğeler bildirildiğinde öğe türüne eklenir, buna dikkat edin. Örneğin,

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 *. jpeg* veya *.gif* dosya uzantısına sahip *resimler* klasöründeki tüm dosyaları içeren fotoğraf adlı bir öğe türü oluşturur. Bu aşağıdaki satıra eşdeğerdir:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Hariç Tutma özniteliği ile bir öğe türünden bir öğeyi dışlayabilirsiniz. Örneğin,

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 adları dize *tasarımcısını* içeren dosyalar dışında, *. cs* dosya uzantısına sahip tüm dosyaları derleme öğesi türüne ekler. Daha fazla örnek için bkz. [nasıl yapılır: derlemeden dosyaları dışarıda bırakma](../msbuild/how-to-exclude-files-from-the-build.md).

Hariç Tutma özniteliği, sadece Dahil Etme özniteliği tarafından her iki öğeyi de içeren item öğesine eklenen öğeleri etkiler. Örneğin,

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

önceki öğe öğesine eklenen *Form1. cs* dosyasını dışlayamazsınız.

**Öğeleri dahil etmek ve dışlamak için**

1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. İçe Aktarma öğesinden hemen sonra şu öğe grubunu ekle:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Proje dosyasını kaydedin.

4. **Komut penceresinden** şu satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Çıkışı inceleyin. Şu satırı görmeniz gerekir:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Öğe meta verileri

 Öğeler, İçe Aktarma ve Hariç Tutma özniteliklerinden toplanan bilgilere ek olarak meta verileri içerebilir. Bu meta veriler, öğeler hakkında yalnızca öğe değerinden daha fazla bilgi gerektiren görevler tarafından kullanılabilir.

 Öğe meta verileri, öğenin bir alt öğesi olarak meta verilerin adı ile bir öğe oluşturularak proje dosyasında bildirilir. Bir öğe sıfır veya daha fazla meta veri değerine sahip olabilir. Örneğin aşağıdaki CSFile öğesi, "Fr" değeri olan Kültür meta verisine sahiptir:

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Bir öğe türünün meta veri değerini almak için, ItemType'ın öğe türün adı olduğu ve MetaDataName'in meta veri adı olduğu aşağıdaki söz dizimini kullanın:

```xml
%(ItemType.MetaDataName)
```

**Öğe meta verilerini incelemek için:**

1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Proje dosyasını kaydedin.

3. **Komut penceresinden** şu satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Çıkışı inceleyin. Şu satırları görmeniz gerekir:

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

"Compile.DependentUpon" ifadesinin birkaç kez nasıl görüntülendiğine dikkat edin. Meta verilerin hedef içinde bu söz dizimi ile kullanımı "toplu işleme" ile sonuçlanır. Toplu işleme, hedef içindeki görevlerin her bir benzersiz meta veri değeri için bir kez çalıştırıldığı anlamına gelir. Bu ise ortak "for döngüsü" programlama yapısına eşdeğer olan MSBuild komut dosyasıdır. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

### <a name="well-known-metadata"></a>İyi bilinen meta veriler

 Öğe bir öğe listesine eklendiğinde bu öğe, bazı iyi bilinen meta verilere atanır. Örneğin, %(Filename) herhangi bir öğenin dosya adını döndürür. İyi bilinen meta verilerin tam bir listesi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).

**İyi bilinen meta verileri incelemek için:**

1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Proje dosyasını kaydedin.

3. **Komut penceresinden** şu satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Çıkışı inceleyin. Şu satırları görmeniz gerekir:

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Yukarıdaki iki örneği karşılaştırarak, Derleme öğe türündeki her öğe DependentUpon meta verisine sahip değilken tüm öğelerin iyi bilinen Dosya Adı meta verisine sahip olduğunu görebilirsiniz.

### <a name="metadata-transformations"></a>Meta veri dönüştürmeleri

 Öğe listeleri yeni öğe listelerine dönüştürülebilir. Bir öğe listesini dönüştürmek için aşağıdaki sözdizimini kullanın; burada \<ItemType> öğe türünün adıdır ve \<MetadataName> meta verilerin adıdır:

```xml
@(ItemType -> '%(MetadataName)')
```

Örneğin kaynak dosyalarının öğe listesi, `@(SourceFiles -> '%(Filename).obj')` gibi bir ifade kullanılarak bir nesne dosyaları koleksiyonuna dönüştürülebilir. Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).

**Meta verileri kullanarak öğeleri dönüştürmek için:**

1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Proje dosyasını kaydedin.

3. **Komut penceresinden** şu satırı girin ve yürütün:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Çıkışı inceleyin. Şu satırı görmeniz gerekir:

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Bu söz diziminde ifade edilen meta verilerin toplu işlemeye neden olmadığını unutmayın.

## <a name="next-steps"></a>Sonraki adımlar

 tek seferde bir adım basit proje dosyası oluşturmayı öğrenmek için [izlenecek yolu deneyin: sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild genel bakış](../msbuild/msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
