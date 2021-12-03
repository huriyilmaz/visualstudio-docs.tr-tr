---
title: Visual Studio uzantısını güncelleştirme
description: Visual Studio uzantınızı Visual Studio 2022 ile çalışacak şekilde güncelleştirmeyi öğrenin.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: 7969f08bef0a746df72de6a4582a06f7bdc1e685
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133514590"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Visual Studio 2022 için Visual Studio uzantısını güncelleştirme

> [!IMPORTANT]
> bu makaledeki öneri, Visual Studio 2019 ve Visual Studio 2022 ' de büyük değişiklikler yapılmasını gerektiren uzantıları geçirmede geliştiricilere rehberlik edebilir. Bu durumlarda, iki VSıX projeniz ve koşullu derlemeniz olması önerilir.
>
> çoğu uzantı, bu makalede uzantınızı modernleştirmede gerekli olan küçük değişikliklerle birlikte Visual Studio 2019 ve Visual Studio 2022 ' de çalışır. uzantınızı Visual Studio 2022 ' de deneyin ve uzantınız için en uygun seçeneği değerlendirin.

Visual Studio 2022, 64 bitlik bir uygulamadır ve Visual Studio SDK 'sında bazı önemli değişiklikler sunar. bu makalede, uzantınızı Visual Studio 2022 ' in güncel önizlemesine sahip olacak şekilde yapmanız gereken adımlarda adım adım açıklanmaktadır. uzantınız daha sonra, Visual Studio 2022 genel kullanıma ulaşmadan önce kullanıcıların yüklemesi için hazır hale gelir.

## <a name="install-visual-studio-and-compile-extensions"></a>Visual Studio yükleyip derleme uzantıları

[Visual Studio 2022 indirmelerden](https://visualstudio.microsoft.com/downloads)Visual Studio 2022 ' ü yükler.

### <a name="extensions-written-in-a-net-language"></a>.NET dilinde yazılan uzantılar

yönetilen uzantılar için Visual Studio 2022 ' i hedefleyen Visual Studio SDK yalnızca NuGet yöneliktir:

- [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (17. x sürümleri) metapackage, ihtiyacınız olan başvuru derlemelerinin çoğunu veya tümünü getirir.
- [Microsoft. vssdk. buildtools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (17. x sürümleri) paketine, Visual Studio 2022 uyumlu bir vsıx oluşturmak için vsıx projenizden başvurulmalıdır.

Herhangi bir son değişikliğe başvuramasanız bile, uzantıların **herhangi BIR CPU** veya **x64** platformu ile derlenmesi *gerekir* . **x86** platformu Visual Studio 2022 ' deki 64-bit işlemle uyumlu değildir.

### <a name="extensions-written-in-c"></a>C++ dilinde yazılan uzantılar

C++ ile derlenen uzantılar için Visual Studio SDK, her zamanki gibi yüklü Visual Studio SDK ile kullanılabilir.

herhangi bir bölme değişikliğine başvurmasa bile, uzantıların özellikle Visual Studio 2022 SDK ve AMD64 için derlenmesi *gerekir* .

### <a name="extensions-with-running-code"></a>Çalışan kod içeren uzantılar

kod çalıştıran uzantılar özellikle Visual Studio 2022 için *derlenmelidir* . Visual Studio 2022, Visual Studio önceki bir sürümünü hedefleyen herhangi bir uzantıyı yüklemez.

daha önceki Visual Studio sürümleri için uzantılarınızı Visual Studio 2022 ' ye nasıl geçirebileceğinizi öğrenin:

1. [Modernleştirin](#modernize-your-vsix-project).
1. Visual Studio 2022 ve daha eski sürümleri hedeflemeye olanak tanımak için [kaynak kodunuzu paylaşılan bir projeye yeniden düzenleyin](#use-shared-projects-for-multi-targeting) .
1. [Visual Studio 2022 hedefli bir vsıx projesi](#add-a-visual-studio-2022-target) ve bir [paket/derleme yeniden eşleme tablosu](migrated-assemblies.md)ekleyin.
1. [Gerekli kod ayarlamalarını yapın](#handle-breaking-api-changes).
1. [Visual Studio 2022 uzantınızı Test edin](#test-your-extension).
1. [Visual Studio 2022 uzantınızı yayımlayın](#publish-your-extension).

### <a name="extensions-without-running-code"></a>Kod çalıştırmadan uzantılar

Çalışan herhangi bir kod içermeyen uzantılar (örneğin, proje veya öğe şablonları), iki ayrı VSIXs üretimi dahil olmak üzere önceki adımları izlemek için gerekli *değildir* .

Bunun yerine, bir VSıX `source.extension.vsixmanifest` dosyasını, dosyasının iki yükleme hedefi bildirdiği şekilde değiştirin:

```xml
<Installation>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0,17.0)">
      <ProductArchitecture>x86</ProductArchitecture>
   </InstallationTarget>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
</Installation>
```

Bu makaledeki adımları, paylaşılan projeler ve birden çok VNET kullanımı ile ilgili adımları atlayabilirsiniz. [Sınamaya](#test-your-extension)devam edebilirsiniz.

> [!NOTE]
> Visual Studio 2022 kullanarak *yeni* bir Visual Studio uzantısı yazıyorsanız ve ayrıca Visual Studio 2019 veya önceki bir sürümü hedeflemek istiyorsanız, [bu kılavuza](target-previous-versions.md)bakın.

### <a name="msbuild-tasks"></a>MSBuild görevleri

MSBuild görevleri yazardıysanız, Visual Studio 2022 ' de, bunun büyük olasılıkla 64 bit MSBuild.exe bir işleme yüklenebilecekleri hakkında farkında olun. göreviniz çalıştırmak için 32 bitlik bir işlem gerektiriyorsa, MSBuild [görevlerinizi ve görevleri yapılandırma](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) bölümüne, görevi 32 bit bir işleme yüklenmesini sağlamak için bkz..

## <a name="modernize-your-vsix-project"></a>VSıX projenize modernleştirin

uzantınızı Visual Studio 2022 desteği eklemeden önce, var olan projenizi temizlemeniz ve modernleştirin önerilir:

1. [packages.config ' den ' `PackageReference` ye geçirin ](/nuget/consume-packages/migrate-packages-config-to-package-reference).

1. tüm doğrudan Visual Studio SDK derleme başvurularını öğelerle değiştirin `PackageReference` :

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > Meta paket için *çok sayıda* derleme başvurularını yalnızca *bir* `PackageReference` örnekle değiştirebilirsiniz:
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" Version="..." />
   >```

   hedeflediğinizden Visual Studio en düşük sürümü ile eşleşen paket sürümlerini seçtiğinizden emin olun.

Visual Studio SDK 'sı için benzersiz olmayan bazı derlemeler (örneğin, *Newtonsoft.Json.dll*), 2022 Visual Studio önce basit bir başvuru aracılığıyla bulunabilir `<Reference Include="Newtonsoft.Json" />` . ancak Visual Studio 2022 ' de, bunun yerine bir paket başvurusu gerekir. bunun nedeni, bazı Visual Studio çalışma zamanının ve SDK dizinlerinin MSBuild varsayılan derleme arama yolundan kaldırıldığı nedenidir.

doğrudan derleme başvurularından NuGet paket başvurularına geçiş yapmak için, NuGet otomatik olarak bağımlılıkların geçişli kapatılmasını yüklediği için ek derleme başvuruları ve çözümleyici paketleri alabilirsiniz. Bu genellikle Tamam, ancak derlemeniz sırasında ek uyarılara neden olabilir. Bu uyarılarla çalışın ve olabildiğince fazla çözün. `#pragma warning disable <id>`Giderebileceğiniz uyarıları bastırmak için kod içi bölgeleri kullanmayı düşünün.

## <a name="use-shared-projects-for-multi-targeting"></a>Çoklu hedefleme için paylaşılan projeler kullanma

[paylaşılan projeler](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) Visual Studio 2015 ' de tanıtılan bir proje türüdür. Visual Studio paylaşılan projeler, kaynak kodu dosyalarının birden fazla proje arasında paylaşılmasını ve koşullu derleme sembolleri ve benzersiz başvuru kümelerini kullanarak farklı şekilde oluşturulması için etkinleştirir.

Visual Studio 2022, önceki Visual Studio sürümlerinden farklı bir başvuru derlemeleri kümesi gerektirir. bu nedenle, uzantınızı Visual Studio 2022, önceki sürümleri ve sonraki sürümleri için kolayca çok hedeflemek üzere paylaşılan projeler kullanmanızı öneririz. Bu teknik size kod paylaşımı, ancak ayrı başvurular verecektir.

Visual Studio uzantıları bağlamında, Visual Studio 2022 ve üzeri için bir vsıx projesine ve Visual Studio 2019 ve daha önceki bir vsıx projesine sahip olabilirsiniz. Bu projelerin her biri yalnızca bir `source.extension.vsixmanifest` örnek ve paketin 16. x SDK 'sı ya da 17. x SDK 'sine başvurduğu bir örnek içerir. bu vsıx projeleri ayrıca, iki Visual Studio sürümünde paylaşılabilen tüm kaynak kodunuzu barındıracak yeni bir paylaşılan projeye paylaşılan bir proje başvurusu da olur.

bu bölümde, Visual Studio 2019 ' i hedefleyen ve uzantınızın Visual Studio 2022 ' de çalışmasını istediğiniz bir vsıx projeniz zaten var.

bu adımların tümünü Visual Studio 2019 ' i kullanarak tamamlayabilirsiniz:

1. Daha önce yapmadıysanız, bu güncelleştirme işlemindeki adımları kolaylaştırmak için [projelerinizi modernleştirin](#modernize-your-vsix-project) .

1. Visual Studio SDK 'ya başvuran mevcut her proje için çözümünüze yeni bir paylaşılan proje ekleyin. çözüme sağ tıklayın ve sonra   >  **yeni Project** ekle ' yi seçin.

   ![Yeni proje ekleme seçimlerini gösteren ekran görüntüsü.](media/update-visual-studio-extension/add-new-project.png)

1. **yeni proje ekle** iletişim kutusunda **paylaşılan proje**' yi arayın ve ardından **paylaşılan Project** şablonunu seçin.

   ![paylaşılan Project şablonunu aramayı ve seçmeyi gösteren ekran görüntüsü.](media/update-visual-studio-extension/new-shared-project-template.png)

1. Visual Studio her bir SDK 'ya başvuran projeden, paylaşılan projesine karşılık gelen bir başvuru ekleyin.

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Paylaşılan proje başvurusu ekleme seçimlerini gösteren ekran görüntüsü." lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. tüm kaynak kodunu ( *. cs* ve *. resx* dosyaları dahil), her Visual Studio SDK 'ya başvuran projeden paylaşılan proje karşılığına taşıyın.
*Kaynak. Extension. valtmanifest* dosyasını VSIX projesinde bırakın.

   ![Tüm kaynak dosyalarını içeren paylaşılan bir projeyi gösteren ekran görüntüsü.](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Meta veri dosyalarını (örneğin, sürüm notları, lisans ve simgeler) ve VSCT dosyalarını paylaşılan bir dizine taşıyın. Sonra VSıX projesine bağlı dosyalar olarak ekleyin. Paylaşılan dizinin paylaşılan projeden ayrı olduğunu unutmayın.

   ![Meta veri ve V S C 'ler dosyalarını bağlı dosyalar olarak ekleme seçimlerini gösteren ekran görüntüsü.](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
   
   - Meta veri dosyaları için **derleme eylemini** **içerik** olarak ayarlayın. **VSIX** 'i **true** olarak ayarlayın.

     ![V S I X 'te meta veri dosyaları dahil gösteren ekran görüntüsü.](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)

   - VSCT dosyaları için, **derleme eylemini** **Vsctcompile** olarak ayarlayın. **VSIX 'Te** **false** olarak ayarlayın. 
   
     ![Bir V S C T dosyasının seçili özelliklerini gösteren ekran görüntüsü.](media/update-visual-studio-extension/build-linked-vsct-files.png)
   
     bu ayarın desteklenmediğini Visual Studio şikayet ediyorsanız, projeyi kaldırarak ve ' ye değiştirerek yapı eylemini el ile değiştirebilirsiniz `Content` `VSCTCompile` :

     ```diff
     -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
     -  <Link>VSIXProject1Package.vsct</Link>
     -</Content>
     +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
     +  <Link>VSIXProject1Package.vsct</Link>
     +  <ResourceName>Menus.ctmenu</ResourceName>
     +</VSCTCompile>
     ```

1. Herhangi bir hata sunmadığınızdan emin olmak için projenizi derleyin.

projeniz artık Visual Studio 2022 desteğine eklenmeye hazırdır.

## <a name="add-a-visual-studio-2022-target"></a>Visual Studio 2022 hedefi ekleme

bu bölüm, [Visual Studio uzantınızı paylaşılan projelerle çarpanlara katmada](#use-shared-projects-for-multi-targeting)kullanılan adımları tamamladığınızı varsayar.

aşağıdaki adımları kullanarak uzantınızı Visual Studio 2022 desteği ekleyin. bunları, Visual Studio 2019 kullanarak tamamlayabilirsiniz.

1. Çözümünüze yeni bir VSıX projesi ekleyin. bu proje 2022 Visual Studio hedeflenecek. Şablonla gelen tüm kaynak kodlarını kaldırın, ancak *Source. Extension. valtmanifest* dosyasını saklayın.

1. yeni vsıx projenizde, Visual Studio 2019-hedef vsıx 'in başvurduğu paylaşılan projeye bir başvuru ekleyin.

   ![Paylaşılan bir proje ve iki V S ı X projesi içeren bir çözüm gösteren ekran görüntüsü.](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Yeni VSıX projesinin düzgün bir şekilde yapılandırıldığını doğrulayın. Derleyici hatalarını çözmek için özgün VSıX projenizle eşleşecek başvurular eklemeniz gerekebilir.

1. yönetilen Visual Studio uzantıları için, paket başvurularınızı 16. x (veya önceki bir sürümü) ile Visual Studio 2022 hedefli proje dosyanızdaki 17. x paket sürümlerine güncelleştirin. Proje NuGet Paket Yöneticisi doğrudan düzenleyin:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Önceki kodda gösterilen sürümler yalnızca tanıtım amaçlıdır. Kodunda, NuGet web sitesinde [bulunan NuGet kullanın.](https://www.nuget.org/) 

   Çoğu durumda paket kimlikleri değişmiştir. 2022'de Visual Studio listesi için [paket/derleme eşleme tablosuna bakın.](migrated-assemblies.md)

   C++ ile yazılmış uzantıların henüz derlen bir SDK'sı yoktur.

1. C++ projeleri için uzantıların AMD64 için derlenmiş olması gerekir. Yönetilen uzantılar için projenizi Herhangi bir **CPU** için yapıdan **x64'ü hedeflemeye değiştirmeyi göz önünde bulundurarak.** Bu değişiklik, Visual Studio 2022'de uzantının her zaman 64 bit bir işlemde yüklemesini sağlar. **Herhangi bir CPU** da iyidir, ancak herhangi bir x64 yerel ikilisi başvurursanız uyarılar üretebilir.

   Uzantınıza yerel modülde sahip olabileceği tüm bağımlılıkların x86 görüntüsünden AMD64 görüntüsüne güncelleştirilmiş olması gerekir.

1. *Source.extension.vsixmanifest* dosyanızı 2022'de Visual Studio düzenleyin. Etiketi `<InstallationTarget>` 2022'Visual Studio ayarlayın. `ProductArchitecture`Amd64 yükünü belirtmek için öğesini ayarlayın.

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   > [!IMPORTANT]
   > Bu Visual Studio 2019'da, bu dosyanın tasarımcısı yeni öğeyi açığa `ProductArchitecture` çıkarmaz. Bu değişikliği yapmak için bir XML düzenleyicisi kullan gerekir. XML düzenleyicisine erişmek için, Çözüm Gezgini'ye gidin ve Birlikte **Aç komutunu** seçin.
   >
   > öğesi `ProductArchitecture` kritiktir. Visual Studio 2022, uzantınız olmadan yüklenmez.

   | Öğe | Değer | Açıklama |
   | - | - | - |
   | `ProductArchitecture` | `x86`, `amd64` | Bu VSIX'in desteklediği platformlar. Büyük/büyük/büyük harfe duyarlı değildir. Öğe başına bir platform ve örnek başına bir öğe `InstallationTarget` kullanın. 17.0'dan küçük ürün sürümleri için varsayılan değerdir `x86` ve atlanabilir. 17.0 ve sonraki ürün sürümleri için bu öğe gereklidir ve varsayılan değer yoktur. 2022 Visual Studio için, bu öğe için tek geçerli içerik `amd64` olur. |

1. *Source.extension.vsixmanifest* içinde 2019'da (varsa) hedefle Visual Studio diğer ayarlamaları da yapabilirsiniz. 

   Her biri farklı bir Visual Studio sürümünü hedef alan uzantının iki sürümünü yayımlarsanız, bildirimin öğesinde VSIX kimliğinin her uzantı için farklı `Identity` olduğundan emin olun.

Bu noktada, 2022 Visual Studio VSIX uzantınız vardır. 2022 Visual Studio VSIX projenizi derlemeniz ve görünen [derleme sonları üzerinde çalışmanız gerekir.](#handle-breaking-api-changes) Visual Studio 2022 hedefli VSIX projeniz için derleme sonları yoksa tebrikler! Test için hazır mısınız?

## <a name="handle-breaking-api-changes"></a>Yeni API değişikliklerini işleme

Hataya neden olan API değişiklikleri, uygulamanın önceki sürümlerinde Visual Studio. Kodunuzu güncelleştirme hakkında ipuçları için bkz. [2022'de api Visual Studio.](breaking-api-list.md)

Kodunuzu uyarlarken koşullu derlemeyi [kullanmanızı öneririz.](#use-conditional-compilation-symbols) Kodunuz daha sonra 2022'Visual Studio için destek eklerken önceki sürümleri desteklemeye devam Visual Studio olabilir.

2022 hedefli uzantı Visual Studio için test işlemine devam [edin.](#test-your-extension)

## <a name="use-conditional-compilation-symbols"></a>Koşullu derleme sembolleri kullanma

2022 ve önceki sürümler için aynı kaynak kodu, hatta aynı dosyayı Visual Studio, koşullu derlemeyi kullanmanız gerekir. Daha sonra hataya neden olan değişikliklere uyum sağlamak için kodunuzun bir hataya neden olabilir. Koşullu derleme C#, Visual Basic ve C++ dillerinin bir özelliğidir. Belirli yerlerde farklı API'ler kullanılırken çoğu kodu paylaşmak için kullanılabilir.

Ön işlemci yönergelerinin ve koşullu derleme sembollerinin kullanımı hakkında daha fazla bilgi için bkz. [C# önişlemci yönergeleri.](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)

Önceki sürümleri hedef alan Visual Studio bir koşullu derleme simgesi gerekir. Bu simge daha sonra farklı API'leri kullanmak üzere kodun biriktiri için kullanılabilir. Koşullu derleme simgesini proje özellikleri sayfasından belirtebilirsiniz:

![Koşullu derleme simgesi girme kutusunu gösteren ekran görüntüsü.](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Tüm Yapılandırmalar için derleme simgesini **ayardan emin olun.** Varsayılan olarak, girersiniz simgesi yalnızca bir yapılandırma için geçerli olabilir.

### <a name="c-techniques"></a>C \# teknikleri

Derleme sembolünü, aşağıdaki kodda gösterildiği gibi önişlemci yönergesi () `#if` olarak kullanabilirsiniz. Daha sonra, yeni sürümler arasındaki hataya neden olan bir değişiklikle başa Visual Studio.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Dev16
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

Bazı durumlarda, türünü `var` adlandırmayı önlemek ve bölgelere ihtiyaçtan kaçınmak için `#if` kullanabilirsiniz. Yukarıdaki kod parçacığı şu şekilde de yazleştirilebilir:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

Söz dizimi kullanırken, dil hizmeti bağlamı için açılan listeyi kullanarak söz dizimi `#if` vurgulamayı nasıl değiştirebilirsiniz? Diğer açılan liste, dil hizmetinin bu uzantıya göre bir hedef sürüme Visual Studio dikkat çekmelerine yardımcı olur.

![Paylaşılan projede koşullu derlemeyi gösteren ekran görüntüsü.](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>XAML paylaşım teknikleri

XAML'de içeriği ön işlemci sembollerine göre özelleştirmeye olanak sağlayan bir ön işlemci yoktur. İçeriği 2022 ve önceki sürümler arasında farklılık Visual Studio XAML sayfalarını kopyalamanız ve korumanız gerekir.

Bazı durumlarda, Visual Studio 2022 ve önceki sürümler arasında ayrı derlemelerde var olan bir türe başvuru yine de bir XAML dosyasında gösterilebilir. Derlemeye başvurulan ad alanını kaldırın:

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Uzantınızı test etmek

2022'Visual Studio bir uzantıyı test etmek için 2022'de Visual Studio gerekir. Önceki sürümlerde 64 bit uzantılar çalıştıra Visual Studio.

Uzantılarınızı 2022'Visual Studio 2022 veya önceki bir sürümü hedeflese Visual Studio ve test etmek için kullanabilirsiniz. Visual Studio 2022'den bir VSIX projesi Visual Studio açılır.

Uzantının desteklemesi istediğiniz her bir Visual Studio sürümüyle test etmek kesinlikle önerilir.

## <a name="publish-your-extension"></a>Uzantınızı yayımlama

Uzantınıza bir Visual Studio 2022 hedefi eklediniz ve test ettiniz. Artık uzantıyı dünya için yayımlamaya hazır olursanız.

### <a name="visual-studio-marketplace"></a>Visual Studio Market

Uzantınızı [Market'Visual Studio yayımlamak,](https://marketplace.visualstudio.com/) yeni kullanıcıların uzantınızı bulup yüklemesi için harika bir yol sağlar. Uzantınız 2022'Visual Studio 2022'ye veya daha eski Visual Studio sürümleri de hedeflese de Market sizi desteklemek için oradadır.

Gelecekte Market birden çok VSIX'i tek bir Market listelemesine yüklemenizi sağlayacaktır. Ardından 2022 Visual Studio VSIX ve önceki bir sürüm için VSIX'i karşıya Visual Studio. Kullanıcılarınız, Visual Studio uzantısı yöneticisini kullanırken, yüklemiş olduğu sürüm için doğru VSIX'Visual Studio alır.

### <a name="custom-installer"></a>Özel yükleyici

Uzantınızı yüklemek için bir MSI veya EXE dosyası derlemeniz ve uzantınızı yüklemek için (bir parçası) ortaya `vsixinstaller.exe` çıktınız, Visual Studio 2022'deki VSIX yükleyicinin güncelleştirilmiş olduğunu bilirsiniz. Geliştiricilerin bu sürüme uzantı yüklemek için Visual Studio 2022 ile birlikte gelen VSIX yükleyici sürümünü Visual Studio. 

Visual Studio 2022'deki VSIX yükleyicisi, aynı makinede Visual Studio 2022 ile mevcut olan önceki Visual Studio sürümlerini hedef alan geçerli uzantıları da yüklür.

### <a name="network-share"></a>Ağ paylaşımı

Uzantınızı LAN veya başka bir yolla paylaşabilirsiniz. 2022 Visual Studio önceki sürümleri hedefle ediyorsanız, birden çok VSIX'inizi ayrı ayrı paylaşmanız gerekir. Kullanıcılarınızı hangi VSIX'in yüklemiş olduklarının sürümüne göre yüklemelerine yardımcı olacak dosya Visual Studio (veya benzersiz klasörlere yer) verme.

### <a name="dependencies"></a>Bağımlılıklar

VSIX'iniz diğer VSIX'leri öğesi aracılığıyla bağımlılıklar olarak belirtirse, başvurulan her VSIX'in VSIX'iniz ile aynı hedeflere ve ürün `<dependency>` mimarilerine yüklenmiş olması gerekir. Bağımlı bir VSIX hedeflenen yüklemesini desteklemezse Visual Studio VSIX'iniz başarısız olur. 

Bağımlı VSIX'in sizinkilerden daha fazla hedefi ve mimariyi desteklemesi sorun değildir. Bu kısıtlama, bağımlılıkları olan bir VSIX'in dağıtım ve dağıtım yaklaşımının bağımlılarınkileri yansıtması gerektiği anlamına gelir.

## <a name="q--a"></a>Soru-Cevap

**S:** Uzantım yalnızca veri sağladığı için (örneğin şablonlar) birlikte çalışabilirlik değişiklikleri gerektirmez. 2022'de aynı zamanda Visual Studio oluşturabilir miyim?

**A:** Evet! Bu [konuda bilgi için bkz. Kod](#extensions-without-running-code) çalıştırmadan uzantılar.

**S:** NuGet bir bağımlılık, eski birlikte çalışabilirlik derlemelerini getirmek ve sınıfların çatıştırıcısına neden olmaktır. Ne yapmalıyım?

Y **: yinelenen** derlemeleri önlemek için *. csproj* dosyanıza aşağıdaki satırı ekleyin:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

Bu kod, paket başvurularının, derlemenin eski sürümünün diğer bağımlılıklardan içeri aktarılmasını engeller.

**s**: kaynak dosyalarımı paylaşılan bir projeye geçirdikten sonra komutlarım ve kısayol tuşları Visual Studio çalışmayı durdurdu. Ne yapmalıyım?

Y **: görüntü** iyileştirici örneği için [Adım 2,4](samples.md#step-2---refactor-source-code-into-a-shared-project) , vsct dosyalarını vsct dosyanıza derlenmek üzere bağlantılı öğeler olarak nasıl ekleneceğini gösterir.

## <a name="next-steps"></a>Sonraki adımlar

Bir adım adım örneği, [ımageiyileştiriciyi](samples.md), projenin bağlantılarıyla ve her bir adımla ilgili kod değişikliklerinden izleyin.
