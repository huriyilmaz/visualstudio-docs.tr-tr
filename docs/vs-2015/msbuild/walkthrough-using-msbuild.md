---
title: 'İzlenecek yol: MSBuild kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6e77934f8e565800eb4a7a753df4beb3b003fbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796882"
---
# <a name="walkthrough-using-msbuild"></a>İzlenecek yol: MSBuild Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild, Microsoft ve Visual Studio için bir yapı platformudur. Bu izlenecek yol MSBuild'ın yapı taşlarını tanıtır ve MSBuild projelerini nasıl yazacağınızı, değiştireceğinizi ve hatalarını ayıklayacağınızı gösterir. Şu konularda bilgi edineceksiniz:  
  
- Bir proje dosyasını oluşturma ve işleme.  
  
- Yapı özelliklerinin kullanılması  
  
- Yapı öğelerinin kullanılması.  
  
  MSBuild'ı Visual Stuido'dan veya Komut Penceresi'nden çalıştırabilirsiniz. Bu izlenecek yolda, Visual Studio kullanarak bir MSBuild proje dosyası oluşturun. Visual Studio'da proje dosyasını düzenleyin ve projeyi oluşturmak ve sonuçları incelemek için bir Komut Penceresi kullanın.  
  
## <a name="creating-an-msbuild-project"></a>MSBuild Projesi Oluşturma  
 Visual Studio proje sistemi MSBuild'i temel alır. Bu, Visual Studio kullanarak yeni bir proje dosyası oluşturmayı kolaylaştırır. Bu bölümde, bir Visual C# proje dosyası oluşturun. Bunun yerine bir Visual Basic proje dosyası oluşturmayı seçebilirsiniz. Bu anlatım bağlamında, iki proje dosyası arasındaki fark önemsizdir.  
  
#### <a name="to-create-a-project-file"></a>Bir proje dosyası oluşturmak için  
  
1. Visual Studio'yu açın.  
  
2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.  
  
3. **Yeni proje** iletişim kutusunda, Visual C# proje türünü seçin ve sonra **Windows Forms uygulama** şablonunu seçin. **Ad** kutusuna `BuildApp` yazın. Çözüm için bir **konum** (örneğin,) girin `D:\` . **Çözüm için dizin oluştur** (seçili), **kaynak denetimine Ekle** (seçili değil) ve **çözüm adı** () için varsayılanları kabul edin `BuildApp` .  
  
     Proje dosyasını oluşturmak için **Tamam** ' ı tıklatın.  
  
## <a name="examining-the-project-file"></a>Proje Dosyasını İnceleme  
 Önceki bölümde, bir Visual C# proje dosyası oluşturmak için Visual Studio'yu kullandınız. Proje dosyası, BuildApp adlı proje düğümü tarafından **Çözüm Gezgini** temsil edilir. Proje dosyasını incelemek için Visual Studio kod düzenleyicisini kullanabilirsiniz.  
  
#### <a name="to-examine-the-project-file"></a>Projeyi dosyasını incelemek için  
  
1. **Çözüm Gezgini**, BuildApp proje düğümüne tıklayın.  
  
2. **Özellikler** tarayıcısında **Proje dosyası** özelliğinin BuildApp. csproj olduğuna dikkat edin. Tüm proje dosyaları "proj" soneki ile adlandırılır. Daha önce bir Visual Basic projesi oluşturduysanız, proje dosyası adı BuildApp.vbproj olur.  
  
3. Proje düğümüne sağ tıklayın ve ardından **Projeyi Kaldır**' a tıklayın.  
  
4. Proje düğümüne tekrar sağ tıklayın ve ardından **BuildApp. csproj Düzenle**' ye tıklayın.  
  
     Proje dosyası kod düzenleyicisinde görüntülenir.  
  
## <a name="targets-and-tasks"></a>Hedefler ve Görevler  
 Proje dosyaları, kök düğümü [PROJESIYLE](../msbuild/project-element-msbuild.md)XML biçimli dosyalardır.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Project ToolsVersion="12.0" DefaultTargets="Build"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Proje öğesinde, xmlns ad alanını belirtmeniz gerekir.  
  
 Uygulama oluşturma işi [hedef](../msbuild/target-element-msbuild.md) ve [görev](../msbuild/task-element-msbuild.md) öğeleriyle yapılır.  
  
- Görev, işin en küçük birimdir; başka bir deyişle yapının "atom" öğesidir. Görevler, girdileri ve çıktıları olabilen bağımsız yürütülebilir bileşenlerdir. Şu anda proje dosyasında başvurulan veya tanımlanan görev yoktur. Aşağıdaki bölümlerde proje dosyasına görevler ekleyin. Daha fazla bilgi için [Görevler](../msbuild/msbuild-tasks.md) konusuna bakın.  
  
- Hedef, görevlerin adlandırılmış bir dizisidir. Şu anda, proje dosyasının sonunda HTML yorumlarında bulunan iki hedef vardır: BeforeBuild ve AfterBuild.  
  
  ```  
  <Target Name="BeforeBuild">  
  </Target>  
  <Target Name="AfterBuild">  
  </Target>  
  ```  
  
   Daha fazla bilgi için [hedefler](../msbuild/msbuild-targets.md) konusuna bakın.  
  
  Proje düğümü, oluşturulacak olan varsayılan hedefi seçen isteğe bağlı bir DefaultTargets özniteliğine sahiptir, bu durumda bu öznitelik Yapı'dır.  
  
```  
<Project ToolsVersion="12.0" DefaultTargets="Build" ...  
```  
  
 Yapı hedefi proje dosyasında tanımlı değildir. Bunun yerine, [Içeri aktarma](../msbuild/import-element-msbuild.md) öğesi kullanılarak Microsoft. CSharp. targets dosyasından içeri aktarılır.  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 İçe aktarılan dosyalar, başvuruldukları proje dosyasına etkili biçimde dahil edilir.  
  
 MSBuild, bir yapının hedeflerini izler ve her bir hedefin birden kereden fazla oluşturulmamasını sağlar.  
  
## <a name="adding-a-target-and-a-task"></a>Bir Hedef ve Bir Görev Ekleme  
 Proje dosyasına bir hedef ekleyin. Bir ileti yazdıran hedefe bir görev ekleyin.  
  
#### <a name="to-add-a-target-and-a-task"></a>Bir hedef ve bir görev eklemek için  
  
1. İçeri aktarma deyiminden hemen sonra proje dosyanıza şu satırları ekleyin:  
  
   ```  
   <Target Name="HelloWorld">  
   </Target>  
   ```  
  
    Bu, HelloWorld adlı bir hedef oluşturur. Proje dosyasını düzenlerken, IntelliSense desteğine sahip olduğunuzdan emin olun.  
  
2. Sonuç bölümün aşağıdaki şekilde gözükmesi için HelloWorld hedefine satırlar ekleyin:  
  
   ```  
   <Target Name="HelloWorld">  
     <Message Text="Hello"></Message>  <Message Text="World"></Message>  
   </Target>  
   ```  
  
3. Proje dosyasını kaydedin.  
  
   İleti görevi, MSBuild ile birlikte gelen birçok görevden biridir. Kullanılabilir görevlerin ve kullanım bilgilerinin tüm listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).  
  
   İleti görevi Metin özniteliğinin dize değerini girdi olarak alır ve bu değeri çıktı cihazında gösterir. HelloWorld hedefi İleti görevini iki kere yürütür: ilki "Hello" iletisini ve diğeri ise "World" iletisini görüntülemek için.  
  
## <a name="building-the-target"></a>Hedefi Oluşturma  
 Yukarıda tanımlanan HelloWorld hedefini oluşturmak için **Visual Studio komut Isteminden** MSBuild 'i çalıştırın. Hedefi seçmek için /target veya /t komut satırı anahtarını kullanın.  
  
> [!NOTE]
> Aşağıdaki bölümlerde **komut penceresi** olarak **Visual Studio komut istemine** başvuracağız.  
  
#### <a name="to-build-the-target"></a>Hedefi oluşturmak için  
  
1. **Başlat**' a ve ardından **tüm programlar**' a tıklayın. **Visual Studio Araçları** klasöründe **Visual Studio komut istemi** ' ni bulup tıklayın.  
  
2. Komut penceresinden proje dosyasını içeren klasöre gidin, bu durumda D:\BuildApp\BuildApp.  
  
3. /t:HelloWorld komut anahtarı ile msbuild'i çalıştırın. Bu, HelloWorld hedefini seçer ve oluşturur:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4. **Komut penceresi**çıktıyı inceleyin. "Hello" ve "World" satırlarını görmeniz gerekir:  
  
    ```  
    Hello  
    World  
    ```  
  
> [!NOTE]
> Bunun yerine, `The target "HelloWorld" does not exist in the project` büyük olasılıkla proje dosyasını kod düzenleyicisinde kaydetmeyi unuttunuz demektir. Dosyayı kaydedin ve yeniden deneyin.  
  
 Kod düzenleyicisi ve komut penceresi arasında değişerek proje dosyasını değiştirebilir ve sonuçları hızlı bir şekilde görebilirsiniz.  
  
> [!NOTE]
> /t komut anahtarı olmadan msbuild'i çalıştırırsanız msbuild, Proje öğesinin DefaultTarget özniteliği tarafından verilen hedefi, bu durumda "Yapı"yı oluşturur. Bu, BuildApp.exe Windows Formları uygulamasını oluşturur.  
  
## <a name="build-properties"></a>Yapı Özellikleri  
 Yapı özellikleri, yapıya rehberlik eden ad-değer çiftleridir. Birkaç yapı özelliği proje dosyasının üst kısmında zaten tanımlanmıştır:  
  
```  
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
  
```  
<TargetFrameworkVersion>v12.0</TargetFrameworkVersion>  
```  
  
 "v12.0" dize değerini vererek TargetFrameworkVersion adlı özelliği tanımlar.  
  
 Yapı özellikleri herhangi bir zamanda yeniden tanımlanabilir. Eğer  
  
```  
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
```  
  
 Daha sonra proje dosyasında veya proje dosyasında daha sonra içe aktarılan dosyada görünür, ardından TargetFrameworkVersion "v3.5" yeni değerini alır.  
  
## <a name="examining-a-property-value"></a>Bir Özellik Değerini İnceleme  
 Özelliğin değerini almak için özellik adının PropertyName'in olduğu aşağıdaki söz dizimini kullanın:  
  
```  
$(PropertyName)  
```  
  
 Proje dosyasındaki bazı özellikleri incelemek için şu söz dizimini kullanın.  
  
#### <a name="to-examine-a-property-value"></a>Bir özellik değerini incelemek için  
  
1. Kod düzenleyicisinden HelloWorld hedefini şu kodla değiştirin:  
  
    ```  
    <Target Name="HelloWorld">  
      <Message Text="Configuration is $(Configuration)" />  
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />  
    </Target>  
    ```  
  
2. Proje dosyasını kaydedin.  
  
3. **Komut penceresinden**şu satırı girin ve yürütün:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4. Çıkışı inceleyin. Şu iki satırı görmeniz gerekir (.NET Framework sürümünüz farklı olabilir):  
  
    ```  
    Configuration is Debug  
    MSBuildToolsPath is C:\Program Files\MSBuild\12.0\bin  
    ```  
  
> [!NOTE]
> Bu satırları görmüyorsanız, büyük olasılıkla kod düzenleyicisinde proje dosyasını kaydetmeyi unuttunuz demektir. Dosyayı kaydedin ve yeniden deneyin.  
  
### <a name="conditional-properties"></a>Koşullu Özellikler  
 Yapılandırma gibi birçok özellik koşullu olarak tanımlanmıştır, yani Koşul özniteliği özellik öğesi içinde görünür. Koşullu özellikler, yalnızca koşul "doğru" olarak değerlendirilirse tanımlanır veya yeniden tanımlanır. Tanımlanmamış özelliklere boş bir dizenin varsayılan değeri verildiğini unutmayın. Örneğin,  
  
```  
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 "Yapılandırma Özelliği henüz tanımlanmamış ise tanımlayın ve 'Hata Ayıkla' değerini verin" anlamına gelir.  
  
 Neredeyse tüm MSBuild öğeleri bir Koşul özniteliğine sahiptir. Koşul özniteliğini kullanma hakkında daha fazla tartışma için bkz. [koşullar](../msbuild/msbuild-conditions.md).  
  
### <a name="reserved-properties"></a>Ayrılmış Özellikler  
 MSBuild, proje dosyası ve MSBuild ikili dosyaları hakkındaki bilgileri depolamak için bazı özellik adlarını saklar. MSBuildToolsPath ayrılmış bir özellik örneğidir. Ayrılmış özelliklere, diğer tüm özellikler gibi $ gösterimi ile başvurulur. Daha fazla bilgi için bkz. [nasıl yapılır: proje dosyasının adına veya konumuna başvurma](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) ve özel olarak [bilinen MSBuild ve tanınmış Özellikler](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
### <a name="environment-variables"></a>Ortam Değişkenleri  
 Proje dosyalarındaki ortam değişkenlerine yapı özellikleriyle aynı şekilde başvurabilirsiniz. Örneğin, proje dosyanızda PATH ortam değişkenini kullanmak için $(Yol) işaretini kullanın. Proje, ortam değişkeniyle ile aynı ada sahip bir özellik tanımı içeriyorsa projedeki özellik, ortam değişkeninin değerini geçersiz kılar. Daha fazla bilgi için bkz. [nasıl yapılır: bir derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="setting-properties-from-the-command-line"></a>Komut Satırı'ndan Özellikleri Ayarlama  
 Özellikler, /property veya /p komut satırı anahtarı kullanılarak komut satırında tanımlanabilir. Komut satırından alınan özellik değerleri, proje dosyasında ve ortam değişkenlerinde ayarlanan özellik değerlerini geçersiz kılar.  
  
#### <a name="to-set-a-property-value-from-the-command-line"></a>Komut satırından bir özellik değerini ayarlamak için  
  
1. **Komut penceresinden**şu satırı girin ve yürütün:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release  
   ```  
  
2. Çıkışı inceleyin. Şu satırı görmeniz gerekir:  
  
   ```  
   Configuration is Release.  
   ```  
  
   MSBuild, Yapılandırma özelliğini oluşturur ve bu özelliğe "Yayın" değerini verir.  
  
## <a name="special-characters"></a>Özel Karakterler  
 Belirli karakterlerin MSBuild proje dosyalarında özel anlamı vardır. Bu karakterler örnekleri noktalı virgülleri (;) ve yıldız işaretlerini (*) içerir. Bu özel karakterlerin bir proje dosyasında sabit değer olarak kullanılması için, xx'in ASCII onaltılık değerini temsil ettiği %xx söz dizimi kullanılarak belirtilmeleri gerekir.  
  
 İleti görevini, Yapılandırma özelliğinin değerini daha okunabilir yapmak için özel karakterlerle gösterecek şekilde değiştirin.  
  
#### <a name="to-use-special-characters-in-the-message-task"></a>İleti görevinde özel karakterler kullanmak için  
  
1. Kod düzenleyicisinden her iki İleti görevini şu satır ile değiştirin:  
  
   ```  
   <Message Text="%24(Configuration) is %22$(Configuration)%22" />  
   ```  
  
2. Proje dosyasını kaydedin.  
  
3. **Komut penceresinden**şu satırı girin ve yürütün:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Çıkışı inceleyin. Şu satırı görmeniz gerekir:  
  
   ```  
   $(Configuration) is "Debug"  
   ```  
  
   Daha fazla bilgi için bkz. [MSBuild özel karakterler](../msbuild/msbuild-special-characters.md).  
  
## <a name="build-items"></a>Yapı Öğeleri  
 Öğe, yapı sistemine girdi olarak kullanılan ve genellikle bir dosya adı olan bir bilgi parçasıdır. Örneğin, kaynak dosyalarını temsil eden bir öğe koleksiyonu öğeleri bir araya derlemek için Derleme adlı bir göreve geçirilebilir.  
  
 Tüm öğeler ItemGroup öğelerinin alt öğeleridir. Öğe adı alt öğenin adıdır ve öğe değeri alt öğeye ait Dahil Etme özniteliğinin değeridir. Aynı ada sahip öğelerin değeri bu adda öğe türlerine toplanır.  Örneğin,  
  
```  
<ItemGroup>  
    <Compile Include="Program.cs" />  
    <Compile Include="Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 iki öğe içeren bir öğe grubunu tanımlar. Derleme öğe türü iki değere sahiptir: "Program.cs" ve "Properties\AssemblyInfo.cs".  
  
 Aşağıdaki kod, virgülle ayrılmış şekilde her iki dosyayı tek bir Dahil Etme özniteliğinde bildirerek aynı öğe türünü oluşturur.  
  
```  
<ItemGroup>  
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).  
  
> [!NOTE]
> Dosya yolları MSBuild proje dosyasını içeren klasörle ilişkilidir.  
  
## <a name="examining-item-type-values"></a>Öğe Türü Değerlerini İnceleme  
 Bir öğe türünün değerlerini almak için, ItemType'ın öğe türünün adı olduğu aşağıdaki söz dizimini kullanın:  
  
```  
@(ItemType)  
```  
  
 Proje dosyasındaki Derleme öğe türünü incelemek için şu söz dizimini kullanın.  
  
#### <a name="to-examine-item-type-values"></a>Öğe türü değerlerini incelemek için  
  
1. Kod düzenleyicisinden HelloWorld hedef görevini şu kodla değiştirin:  
  
   ```  
   <Target Name="HelloWorld">  
     <Message Text="Compile item type contains @(Compile)" />  
   </Target>  
   ```  
  
2. Proje dosyasını kaydedin.  
  
3. **Komut penceresinden**şu satırı girin ve yürütün:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Çıkışı inceleyin. Şu uzun satırı görmeniz gerekir:  
  
   ```  
   Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs  
   ```  
  
   Bir öğe türünün değerleri varsayılan olarak virgüllerle ayrılır.  
  
   Bir öğe türünün ayracını değiştirmek için, ItemType'ın öğe türü ve Ayırıcı'nın bir veya daha fazla ayırma karakterinin dizesi olduğu aşağıdaki söz dizimini kullanın:  
  
```  
@(ItemType, Separator)  
```  
  
 Her satırda bir tane Derleme öğesi görüntülemek için taşıma dönüşlerini ve satır beslemelerini (%0A%0D) kullanmak üzere İleti görevini değiştirin.  
  
#### <a name="to-display-item-type-values-one-per-line"></a>Her satırda bir tane öğe türü değeri görüntülemek için  
  
1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:  
  
    ```  
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />  
    ```  
  
2. Proje dosyasını kaydedin.  
  
3. **Komut penceresinden**şu satırı girin ve yürütün:  
  
     `msbuild buildapp.csproj /t:HelloWorld`  
  
4. Çıkışı inceleyin. Şu satırları görmeniz gerekir:  
  
    ```  
    Compile item type contains Form1.cs  
    Form1.Designer.cs  
    Program.cs  
    Properties\AssemblyInfo.cs  
    Properties\Resources.Designer.cs  
    Properties\Settings.Designer.cs  
    ```  
  
### <a name="include-exclude-and-wildcards"></a>Dahil Etme, Hariç Tutma ve Joker Karakterler  
 \* \* Öğe türüne öğe eklemek için Include özniteliğiyle birlikte "*", "" ve "?" joker karakterlerini kullanabilirsiniz. Örneğin,  
  
```  
<Photos Include="images\*.jpeg" />  
```  
  
 resimler klasöründeki ".jpeg" dosya uzantılı tüm dosyaları Fotoğraflar öğe türüne ekler  
  
```  
<Photos Include="images\**.jpeg" />  
```  
  
 resimler klasöründeki ve tüm alt klasörlerindeki ".jpeg" uzantılı tüm dosyaları Fotoğraflar öğe türüne ekler. Daha fazla örnek için bkz. [nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).  
  
 Öğeler bildirildiğinde öğe türüne eklenir, buna dikkat edin. Örneğin,  
  
```  
<Photos Include="images\*.jpeg" />  
<Photos Include="images\*.gif" />  
```  
  
 görüntü klasöründeki ".jpeg" veya ".gif" dosya uzantısına sahip tüm dosyaları içeren Fotoğraflar olarak adlandırılmış bir öğe türü oluşturur. Bu aşağıdaki satıra eşdeğerdir:  
  
```  
<Photos Include="images\*.jpeg;images\*.gif" />  
```  
  
 Hariç Tutma özniteliği ile bir öğe türünden bir öğeyi dışlayabilirsiniz. Örneğin,  
  
```  
<Compile Include="*.cs" Exclude="*Designer*">  
```  
  
 adı "Tasarımcı" dizesini içeren dosyalar dışında ".cs" dosya uzantısına sahip tüm dosyaları Derleme öğe türüne ekler. Daha fazla örnek için bkz. [nasıl yapılır: derlemeden dosyaları dışarıda bırakma](../msbuild/how-to-exclude-files-from-the-build.md).  
  
 Hariç Tutma özniteliği, sadece Dahil Etme özniteliği tarafından her iki öğeyi de içeren item öğesine eklenen öğeleri etkiler. Örneğin,  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 önceki item öğesine eklenen Form1.cs dosyasını dışlamaz.  
  
##### <a name="to-include-and-exclude-items"></a>Öğeleri dahil etmek ve dışlamak için  
  
1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:  
  
    ```  
    <Message Text="Compile item type contains @(XFiles)" />  
    ```  
  
2. İçe Aktarma öğesinden hemen sonra şu öğe grubunu ekle:  
  
    ```  
    <ItemGroup>  
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />  
    </ItemGroup>  
    ```  
  
3. Proje dosyasını kaydedin.  
  
4. **Komut penceresinden**şu satırı girin ve yürütün:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
5. Çıkışı inceleyin. Şu satırı görmeniz gerekir:  
  
    ```  
    Compile item type contains Form1.cs;Program.cs;Properties/Resources.resx  
    ```  
  
## <a name="item-metadata"></a>Öğe meta verileri  
 Öğeler, İçe Aktarma ve Hariç Tutma özniteliklerinden toplanan bilgilere ek olarak meta verileri içerebilir. Bu meta veriler, öğeler hakkında yalnızca öğe değerinden daha fazla bilgi gerektiren görevler tarafından kullanılabilir.  
  
 Öğe meta verileri, öğenin bir alt öğesi olarak meta verilerin adı ile bir öğe oluşturularak proje dosyasında bildirilir. Bir öğe sıfır veya daha fazla meta veri değerine sahip olabilir. Örneğin aşağıdaki CSFile öğesi, "Fr" değeri olan Kültür meta verisine sahiptir:  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Bir öğe türünün meta veri değerini almak için, ItemType'ın öğe türün adı olduğu ve MetaDataName'in meta veri adı olduğu aşağıdaki söz dizimini kullanın:  
  
```  
%(ItemType.MetaDataName)  
```  
  
#### <a name="to-examine-item-metadata"></a>Öğenin meta verilerini incelemek için  
  
1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:  
  
   ```  
   <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />  
   ```  
  
2. Proje dosyasını kaydedin.  
  
3. **Komut penceresinden**şu satırı girin ve yürütün:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Çıkışı inceleyin. Şu satırları görmeniz gerekir:  
  
   ```  
   Compile.DependentUpon:  
   Compile.DependentUpon: Form1.cs  
   Compile.DependentUpon: Resources.resx  
   Compile.DependentUpon: Settings.settings  
   ```  
  
   "Compile.DependentUpon" ifadesinin birkaç kez nasıl görüntülendiğine dikkat edin. Meta verilerin hedef içinde bu söz dizimi ile kullanımı "toplu işleme" ile sonuçlanır. Toplu işleme, hedef içindeki görevlerin her bir benzersiz meta veri değeri için bir kez çalıştırıldığı anlamına gelir. Bu ise ortak "for döngüsü" programlama yapısına eşdeğer olan MSBuild komut dosyasıdır. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.  
  
### <a name="well-known-metadata"></a>İyi Bilinen Meta Veriler  
 Öğe bir öğe listesine eklendiğinde bu öğe, bazı iyi bilinen meta verilere atanır. Örneğin, %(Filename) herhangi bir öğenin dosya adını döndürür. İyi bilinen meta verilerin tam bir listesi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).  
  
##### <a name="to-examine-well-known-metadata"></a>İyi bilinen meta verileri incelemek için  
  
1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:  
  
   ```  
   <Message Text="Compile Filename: %(Compile.Filename)" />  
   ```  
  
2. Proje dosyasını kaydedin.  
  
3. **Komut penceresinden**şu satırı girin ve yürütün:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Çıkışı inceleyin. Şu satırları görmeniz gerekir:  
  
   ```  
   Compile Filename: Form1  
   Compile Filename: Form1.Designer  
   Compile Filename: Program  
   Compile Filename: AssemblyInfo  
   Compile Filename: Resources.Designer  
   Compile Filename: Settings.Designer  
   ```  
  
   Yukarıdaki iki örneği karşılaştırarak, Derleme öğe türündeki her öğe DependentUpon meta verisine sahip değilken tüm öğelerin iyi bilinen Dosya Adı meta verisine sahip olduğunu görebilirsiniz.  
  
### <a name="metadata-transformations"></a>Meta Veri Dönüşümleri  
 Öğe listeleri yeni öğe listelerine dönüştürülebilir. Bir öğe listesini dönüştürmek için ItemType'ın öğe türünün adı olduğu ve MetadataName'in meta veri adı olduğu aşağıdaki söz dizimini kullanın:  
  
```  
@(ItemType -> '%(MetadataName)')  
```  
  
 Örneğin kaynak dosyalarının öğe listesi, `@(SourceFiles -> '%(Filename).obj')` gibi bir ifade kullanılarak bir nesne dosyaları koleksiyonuna dönüştürülebilir. Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).  
  
##### <a name="to-transform-items-using-metadata"></a>Meta verileri kullanarak öğeleri dönüştürmek için  
  
1. Kod düzenleyicisinden İleti görevini şu satır ile değiştirin:  
  
   ```  
   <Message Text="Backup files: @(Compile->'%(filename).bak')" />  
   ```  
  
2. Proje dosyasını kaydedin.  
  
3. **Komut penceresinden**şu satırı girin ve yürütün:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Çıkışı inceleyin. Şu satırı görmeniz gerekir:  
  
   ```  
   Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak  
   ```  
  
   Bu söz diziminde ifade edilen meta verilerin toplu işlemeye neden olmadığını unutmayın.  
  
## <a name="whats-next"></a>Sırada Ne Var?  
 Tek seferde bir adım basit proje dosyası oluşturmayı öğrenmek için [Izlenecek yolu deneyin: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
[MSBuild genel bakış](msbuild.md)  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)
