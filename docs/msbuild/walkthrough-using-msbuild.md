---
title: 'Walkthrough: MSBuild kullanma | Microsoft Dokümanlar'
ms.date: 03/20/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 310fa3b6795a5e340dcd9c7fa40cb27807c132ba
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072547"
---
# <a name="walkthrough-use-msbuild"></a>Walkthrough: MSBuild'i kullan

MSBuild, Microsoft ve Visual Studio için bir yapı platformudur. Bu izlenecek yol MSBuild'ın yapı taşlarını tanıtır ve MSBuild projelerini nasıl yazacağınızı, değiştireceğinizi ve hatalarını ayıklayacağınızı gösterir. Şu konularda bilgi edineceksiniz:

- Bir proje dosyasını oluşturma ve işleme.

- Yapı özelliklerinin kullanılması

- Yapı öğelerinin kullanılması.

MSBuild'i Visual Studio'dan veya **Komut Penceresinden**çalıştırabilirsiniz. Bu izlenecek yolda, Visual Studio kullanarak bir MSBuild proje dosyası oluşturun. Visual Studio'daki proje dosyasını düzenlemesi ve projeyi oluşturmak ve sonuçları incelemek için **Komut Penceresi'ni** kullanırsınız.

## <a name="create-an-msbuild-project"></a>MSBuild projesi oluşturma

 Visual Studio proje sistemi MSBuild'i temel alır. Bu, Visual Studio kullanarak yeni bir proje dosyası oluşturmayı kolaylaştırır. Bu bölümde, bir Visual C# proje dosyası oluşturun. Bunun yerine bir Visual Basic proje dosyası oluşturmayı seçebilirsiniz. Bu anlatım bağlamında, iki proje dosyası arasındaki fark önemsizdir.

**Bir proje dosyası oluşturmak için**

1. Visual Studio'u açın ve bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **winforms**yazın, ardından **yeni bir Windows Forms App (.NET Framework) oluştur'u**seçin. Görünen iletişim kutusunda **Oluştur'u**seçin.

    **Ad** kutusuna `BuildApp` yazın. Çözüm için bir **Konum** girin, örneğin, *D:\\*. **Çözüm**, **Çözüm Adı** ( BuildApp ) ve **Framework**için varsayılanları kabul**edin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni Proje** iletişim kutusunun sol bölmesinde, **Visual C#** > Windows**Desktop'ı**genişletin, ardından Windows **Forms App'ı (.NET Framework)** seçin. Sonra **Tamam'ı**seçin.

    **Ad** kutusuna `BuildApp` yazın. Çözüm için bir **Konum** girin, örneğin, *D:\\*. **Çözüm için dizini oluştur** (seçili), Kaynak **Denetimine Ekle** (seçili değil) ve Çözüm **Adı** **(BuildApp)** için varsayılan ları kabul edin.
    ::: moniker-end

1. Proje dosyasını oluşturmak için **Tamam** veya **Oluştur'u** tıklatın.

## <a name="examine-the-project-file"></a>Proje dosyasını inceleme

 Önceki bölümde, bir Visual C# proje dosyası oluşturmak için Visual Studio'yu kullandınız. Proje dosyası **Solution Explorer'da** BuildApp adlı proje düğümü ile temsil edilir. Proje dosyasını incelemek için Visual Studio kod düzenleyicisini kullanabilirsiniz.

**Projeyi dosyasını incelemek için**

1. **Solution Explorer'da**proje düğümü **BuildApp'ı**tıklatın.

1. **Özellikler** tarayıcısında, Project **File** özelliğinin *BuildApp.csproj*olduğuna dikkat edin. Tüm proje dosyaları sonek *proj*ile adlandırılır. Visual Basic projesi oluşturmuş olsaydınız, proje dosyasının adı *BuildApp.vbproj*olurdu.

1. Proje düğümüne tekrar sağ tıklayın, ardından **BuildApp.csproj'u Düzelt'i**tıklatın. 

     Proje dosyası kod düzenleyicisinde görüntülenir.

>[!NOTE]
> C++ gibi bazı proje türleri için, proje dosyasını açıp düzenlemesi için projeyi boşaltmanız (proje dosyasına sağ tıklayın ve **Projeyi Boşalt'ı**seçin) gerekir.

## <a name="targets-and-tasks"></a>Hedefler ve görevler

Proje dosyaları kök düğümü [Project](../msbuild/project-element-msbuild.md)ile XML biçimlendirilmiş dosyalardır.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Yeni .NET Core (SDK tarzı) `Sdk` projelerin bir özniteliği vardır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Proje SDK tarzı bir proje değilse, Proje öğesindeki xmlns ad alanını belirtmeniz gerekir. `ToolsVersion` Yeni bir projede varsa, "15.0" olmalıdır.

Bir uygulama oluşturma işi [Hedef](../msbuild/target-element-msbuild.md) ve [Görev](../msbuild/task-element-msbuild.md) öğeleri ile yapılır.

- Görev, işin en küçük birimdir; başka bir deyişle yapının "atom" öğesidir. Görevler, girdileri ve çıktıları olabilen bağımsız yürütülebilir bileşenlerdir. Şu anda proje dosyasında başvurulan veya tanımlanan görev yoktur. Aşağıdaki bölümlerde proje dosyasına görevler ekleyin. Daha fazla bilgi için [Görevler](../msbuild/msbuild-tasks.md) konusuna bakın.

- Hedef, görevlerin adlandırılmış bir dizisidir. Daha fazla bilgi için [Hedefler](../msbuild/msbuild-targets.md) konusuna bakın.
- [bu görevlerin adlandırılmış bir dizi olabilir, ama kritik olarak, inşa edilecek veya yapılacak bir şey temsil eder, bu yüzden hedef odaklı bir şekilde tanımlanmalıdır]

Varsayılan hedef proje dosyasında tanımlı değildir. Bunun yerine, içe aktarılan projelerde belirtilir. [İçe Aktarma](../msbuild/import-element-msbuild.md) öğesi içe aktarılan projeleri belirtir. Örneğin, bir C# projesinde varsayılan hedef *Microsoft.CSharp.targets*dosyasından alınır.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

İçe aktarılan dosyalar, başvuruldukları proje dosyasına etkili biçimde dahil edilir.

SDK tarzı projcts, SDK özniteliği bu dosyayı örtülü olarak içe aktarılmak için neden olduğundan, bu alma elemanı görmüyorum.

MSBuild, bir yapının hedeflerini izler ve her bir hedefin birden kereden fazla oluşturulmamasını sağlar.

## <a name="add-a-target-and-a-task"></a>Hedef ve görev ekleme

 Proje dosyasına bir hedef ekleyin. Bir ileti yazdıran hedefe bir görev ekleyin.

**Bir hedef ve bir görev eklemek için**

1. İçeri aktarma deyiminden hemen sonra proje dosyanıza şu satırları ekleyin:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    Bu, HelloWorld adlı bir hedef oluşturur. Proje dosyasını düzenlerken IntelliSense desteğine sahip olduğunuza dikkat edin.

2. Sonuç bölümün aşağıdaki şekilde gözükmesi için HelloWorld hedefine satırlar ekleyin:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Proje dosyasını kaydedin.

İleti görevi, MSBuild ile birlikte gelen birçok görevden biridir. Kullanılabilir görevlerin ve kullanım bilgilerinin tam listesi için [Görev başvurusuna](../msbuild/msbuild-task-reference.md)bakın.

İleti görevi Metin özniteliğinin dize değerini giriş olarak alır ve çıktı aygıtında görüntüler (veya varsa bir veya daha fazla günlüklere yazar). HelloWorld hedefi İleti görevini iki kere yürütür: ilki "Hello" iletisini ve diğeri ise "World" iletisini görüntülemek için.

## <a name="build-the-target"></a>Hedefi oluşturun

Bu projeyi Visual Studio'dan oluşturmaya çalışırsanız, tanımladığınız hedefi oluşturmaz. Bunun nedeni Visual Studio'nun, hala içe aktarılan *.targets* dosyasındaki varsayılan hedefi seçmesidir.

Yukarıda tanımlanan HelloWorld hedefini oluşturmak için Visual Studio için **Geliştirici Komut Komut Komut Ustem'den** MSBuild çalıştırın. Hedefi seçmek için -hedef veya -t komut satırı anahtarını kullanın.

> [!NOTE]
> Aşağıdaki **bölümlerde** **Geliştirici Komut İstemi** komut u stem komutu olarak adlandırılacaktır.

**Hedefi oluşturmak için:**

1. Komut **Penceresini**aç.

   (Windows 10) Görev çubuğundaki arama kutusunda, aracın adını yazmaya başlayın, `dev` örneğin `developer command prompt`. Bu, arama deseninizle eşleşen yüklü uygulamaların bir listesini getirir.

   El ile bulmanız gerekiyorsa, dosya<*visualstudio yükleme klasörü\>\<sürümünde* *LaunchDevCmd.bat*>\Common7\Tools klasörüdür.

2. Komut penceresinden, proje dosyasını içeren klasöre gidin, bu durumda, *D:\BuildApp\BuildApp*.

3. Komut anahtarı `-t:HelloWorld`ile msbuild çalıştırın. Bu, HelloWorld hedefini seçer ve oluşturur:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. **Komut penceresindeki**çıkışı inceleyin. "Hello" ve "World" satırlarını görmeniz gerekir:

    ```output
    Hello
    World
    ```

> [!NOTE]
> Bunun yerine `The target "HelloWorld" does not exist in the project` görürseniz, büyük olasılıkla kod düzenleyicisinde proje dosyasını kaydetmeyi unuttunuz. Dosyayı kaydedin ve yeniden deneyin.

 Kod düzenleyicisi ve komut penceresi arasında değişerek proje dosyasını değiştirebilir ve sonuçları hızlı bir şekilde görebilirsiniz.

## <a name="build-properties"></a>Özellikler oluşturma

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

 string değerini vererek TargetFrameworkVersion adlı özelliği tanımlar "v4.5".

 Yapı özellikleri herhangi bir zamanda yeniden tanımlanabilir. Eğer

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 Daha sonra proje dosyasında veya proje dosyasında daha sonra içe aktarılan dosyada görünür, ardından TargetFrameworkVersion "v3.5" yeni değerini alır.

## <a name="examine-a-property-value"></a>Özellik değerini inceleme

 Bir özelliğin değerini almak için, özelliğin `PropertyName` adı nerede aşağıdaki sözdizimini kullanın:

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

1. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Çıktıyı inceleyin. Şu iki satırı görmeniz gerekir (.NET Framework sürümünüz farklı olabilir):

    ::: moniker range=">=vs-2019"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2019\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end
    ::: moniker range="vs-2017"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end

### <a name="conditional-properties"></a>Koşullu özellikler

Gibi `Configuration` birçok özellik koşullu olarak tanımlanır, yani özellik `Condition` öğesinde öznitelik görünür. Koşullu özellikler, yalnızca koşul "doğru" olarak değerlendirilirse tanımlanır veya yeniden tanımlanır. Tanımlanmamış özelliklere boş bir dizenin varsayılan değeri verildiğini unutmayın. Örneğin,

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

"Yapılandırma Özelliği henüz tanımlanmamış ise tanımlayın ve 'Hata Ayıkla' değerini verin" anlamına gelir.

Neredeyse tüm MSBuild öğeleri bir Koşul özniteliğine sahiptir. Koşul özniteliğini kullanma hakkında daha fazla tartışma için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.

### <a name="reserved-properties"></a>Ayrılmış özellikler

MSBuild, proje dosyası ve MSBuild ikili dosyaları hakkındaki bilgileri depolamak için bazı özellik adlarını saklar. MSBuildToolsPath ayrılmış bir özellik örneğidir. Ayrılmış özelliklere, diğer tüm özellikler gibi $ gösterimi ile başvurulur. Daha fazla bilgi için [bkz: Proje dosyasının adını veya konumunu ve](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) [MSBuild ayrılmış ve iyi bilinen özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)başvurun.

### <a name="environment-variables"></a>Ortam değişkenleri

Proje dosyalarındaki ortam değişkenlerine yapı özellikleriyle aynı şekilde başvurabilirsiniz. Örneğin, proje dosyanızda PATH ortam değişkenini kullanmak için $(Yol) işaretini kullanın. Proje, ortam değişkeniyle ile aynı ada sahip bir özellik tanımı içeriyorsa projedeki özellik, ortam değişkeninin değerini geçersiz kılar. Daha fazla bilgi için [bkz: Yapıdaki ortam değişkenlerini kullanın.](../msbuild/how-to-use-environment-variables-in-a-build.md)

## <a name="set-properties-from-the-command-line"></a>Komut satırındaki özellikleri ayarlama

Özellikler komut satırında -özellik veya -p komut satırı anahtarı kullanılarak tanımlanabilir. Komut satırından alınan özellik değerleri, proje dosyasında ve ortam değişkenlerinde ayarlanan özellik değerlerini geçersiz kılar.

**Komut satırından özellik değeri ayarlamak için:**

1. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. Çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    ```output
    Configuration is Release.
    ```

MSBuild, Yapılandırma özelliğini oluşturur ve bu özelliğe "Yayın" değerini verir.

## <a name="special-characters"></a>Özel karakterler

Belirli karakterlerin MSBuild proje dosyalarında özel anlamı vardır. Bu karakterler örnekleri noktalı virgülleri (;) ve yıldız işaretlerini (*) içerir. Bu özel karakterleri bir proje dosyasında edebi olarak kullanabilmek için, xx>\<karakterin ASCII hexadecimal değerini temsil ettiği \<sözdizimi % xx> kullanılarak belirtilmelidir.

İleti görevini, Yapılandırma özelliğinin değerini daha okunabilir yapmak için özel karakterlerle gösterecek şekilde değiştirin.

**İleti görevinde özel karakterler kullanmak için:**

1. Kod düzenleyicisinden her iki İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. Proje dosyasını kaydedin.

1. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    ```output
    $(Configuration) is "Debug"
    ```

Daha fazla bilgi için [MSBuild özel karakterleri](../msbuild/msbuild-special-characters.md)bakın.

## <a name="build-items"></a>Öğeler oluşturma

Öğe, yapı sistemine girdi olarak kullanılan ve genellikle bir dosya adı olan bir bilgi parçasıdır. Örneğin, kaynak dosyalarını temsil eden bir öğe koleksiyonu öğeleri bir araya derlemek için Derleme adlı bir göreve geçirilebilir.

Tüm öğeler ItemGroup öğelerinin alt öğeleridir. Öğe adı alt öğenin adıdır ve öğe değeri alt öğeye ait Dahil Etme özniteliğinin değeridir. Aynı ada sahip öğelerin değeri bu adda öğe türlerine toplanır.  Örneğin,

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

iki öğe içeren bir öğe grubunu tanımlar. Derleme öğesinin iki değeri vardır: *Program.cs* ve *Özellikler\AssemblyInfo.cs.*

Aşağıdaki kod, virgülle ayrılmış şekilde her iki dosyayı tek bir Dahil Etme özniteliğinde bildirerek aynı öğe türünü oluşturur.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

> [!NOTE]
> Dosya yolları, proje dosyası içe aktarılan proje dosyası olsa bile MSBuild proje dosyasını içeren klasörle görecelidir. [İçe Aktarma](import-element-msbuild.md) ve [Görev Kullanma](usingtask-element-msbuild.md) öğelerini kullanırken bunun birkaç istisnası vardır.

## <a name="examine-item-type-values"></a>Madde türü değerlerini inceleme

 Bir öğe türünün değerlerini almak için, ItemType'ın öğe türünün adı olduğu aşağıdaki söz dizimini kullanın:

```xml
@(ItemType)
```

Proje dosyasındaki Derleme öğe türünü incelemek için şu söz dizimini kullanın.

**Madde türü değerlerini incelemek için:**

1. Kod düzenleyicisinden HelloWorld hedef görevini şu kodla değiştirin:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. Proje dosyasını kaydedin.

1. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Çıktıyı inceleyin. Şu uzun satırı görmeniz gerekir:

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

3. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Çıktıyı inceleyin. Şu satırları görmeniz gerekir:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Ekle, Hariç Tut ve joker karakterler

 Öğe türüne öğe eklemek için\*\*Ekle özniteliği ile "*", " "ve "?" joker lerini kullanabilirsiniz. Örneğin,

```xml
<Photos Include="images\*.jpeg" />
```

 *resimler* klasöründe dosya uzantısı *.jpeg* ile tüm dosyaları Fotoğraflar öğesi türüne eklerken,

```xml
<Photos Include="images\**\*.jpeg" />
```

 *resimler* klasörüne dosya uzantısı *.jpeg* ve tüm alt klasörleri ile tüm dosyaları Fotoğraflar öğe türüne ekler. Daha fazla örnek için [bkz: Oluşturmak için dosyaları seçin.](../msbuild/how-to-select-the-files-to-build.md)

 Öğeler bildirildiğinde öğe türüne eklenir, buna dikkat edin. Örneğin,

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 *.jpeg* veya *.gif*dosya uzantısı ile resimler klasöründeki tüm dosyaları içeren Fotoğraf adlı bir öğe türü oluşturur. *.jpeg* Bu aşağıdaki satıra eşdeğerdir:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Hariç Tutma özniteliği ile bir öğe türünden bir öğeyi dışlayabilirsiniz. Örneğin,

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 adları *dize Tasarımcısı*içeren dosyalar dışında, dosya uzantısı *.cs* ile tüm dosyaları Derleme öğesi türüne ekler. Daha fazla örnek için [bkz: Dosyaları yapıdan hariç tut.](../msbuild/how-to-exclude-files-from-the-build.md)

Hariç Tutma özniteliği, sadece Dahil Etme özniteliği tarafından her iki öğeyi de içeren item öğesine eklenen öğeleri etkiler. Örneğin,

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

önceki öğe öğesine eklenen dosya *Form1.cs*hariç tutmaz.

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

4. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Madde meta verileri

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

**Madde meta verilerini incelemek için:**

1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Proje dosyasını kaydedin.

3. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Çıktıyı inceleyin. Şu satırları görmeniz gerekir:

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

"Compile.DependentUpon" ifadesinin birkaç kez nasıl görüntülendiğine dikkat edin. Meta verilerin hedef içinde bu söz dizimi ile kullanımı "toplu işleme" ile sonuçlanır. Toplu işleme, hedef içindeki görevlerin her bir benzersiz meta veri değeri için bir kez çalıştırıldığı anlamına gelir. Bu ise ortak "for döngüsü" programlama yapısına eşdeğer olan MSBuild komut dosyasıdır. Daha fazla bilgi için [Toplu İşlem'e](../msbuild/msbuild-batching.md)bakın.

### <a name="well-known-metadata"></a>Bilinen meta veriler

 Öğe bir öğe listesine eklendiğinde bu öğe, bazı iyi bilinen meta verilere atanır. Örneğin, %(Filename) herhangi bir öğenin dosya adını döndürür. İyi bilinen meta verilerin tam listesi için, [bilinen öğe meta verilerine](../msbuild/msbuild-well-known-item-metadata.md)bakın.

**Tanınmış meta verileri incelemek için:**

1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Proje dosyasını kaydedin.

3. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Çıktıyı inceleyin. Şu satırları görmeniz gerekir:

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Yukarıdaki iki örneği karşılaştırarak, Derleme öğe türündeki her öğe DependentUpon meta verisine sahip değilken tüm öğelerin iyi bilinen Dosya Adı meta verisine sahip olduğunu görebilirsiniz.

### <a name="metadata-transformations"></a>Meta veri dönüşümleri

 Öğe listeleri yeni öğe listelerine dönüştürülebilir. Madde listesini dönüştürmek için, ItemType>'nin öğe türünün adı, \< \<MetadataName>'nin meta verilerin adı olduğu aşağıdaki sözdizimini kullanın:

```xml
@(ItemType -> '%(MetadataName)')
```

Örneğin kaynak dosyalarının öğe listesi, `@(SourceFiles -> '%(Filename).obj')` gibi bir ifade kullanılarak bir nesne dosyaları koleksiyonuna dönüştürülebilir. Daha fazla bilgi için [Transforms'a](../msbuild/msbuild-transforms.md)bakın.

**Meta verileri kullanarak öğeleri dönüştürmek için:**

1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Proje dosyasını kaydedin.

3. Komut **Penceresinden,** bu satırı girin ve çalıştırın:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Bu söz diziminde ifade edilen meta verilerin toplu işlemeye neden olmadığını unutmayın.

## <a name="next-steps"></a>Sonraki adımlar

 Basit bir proje dosyasını adım adım nasıl oluşturabilirsiniz öğrenmek [için, Walkthrough'u deneyin: MSBuild proje dosyasını sıfırdan oluşturma.](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild'e genel bakış](../msbuild/msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
