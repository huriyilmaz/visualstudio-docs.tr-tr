---
title: Visual Studio uzantısını güncelleştirme
description: Visual Studio uzantınızı Visual Studio 2022 ile çalışacak şekilde güncelleştirmeyi öğrenin.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 514c9654a741e4e1e565f0cb2becdbe3157fab0c
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308797"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Visual Studio 2022 için Visual Studio uzantısı 'nı güncelleştirme

Bu kılavuzu izleyerek uzantınızı Visual Studio 2022 Preview ile çalışacak şekilde güncelleştirebilirsiniz. Visual Studio 2022 Preview, 64 bitlik bir uygulamadır ve VS SDK 'sında bazı önemli değişiklikler sunar. Bu kılavuz, uzantınızın Visual Studio 2022 ' un güncel önizlemesine sahip olması için gereken adımlarda size kılavuzluk eder. bu nedenle, uzantınızın, Visual Studio 2022 GA 'ye ulaşmadan önce yüklenmesi için hazırsanız.

## <a name="installing"></a>Yükleme

Visual Studio [2022 Preview İndirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022)' nden visual Studio 2022 Preview ' i yükler.

### <a name="extensions-written-in-a-net-language"></a>.NET dilinde yazılan uzantılar

Yönetilen Uzantılar için Visual Studio 2022 ' i hedefleyen VS SDK *yalnızca* NuGet üzerinde çalışır:

- [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (17. x sürümleri) meta paketi, ihtiyacınız olan başvuru derlemelerinin çoğunu veya tümünü sağlar.
- [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (17. x sürümleri) paketine, Visual Studio 2022 uyumlu bir VSIX oluşturmak için VSIX projenizden başvurulmalıdır.

Uzantılar "Any CPU" veya "x64" platformu ile *derlenmelidir* . "X86" platformu, Visual Studio 2022 64-bit işlemiyle uyumsuzdur.

### <a name="extensions-written-in-c"></a>C++ dilinde yazılan uzantılar

C++ ile derlenen uzantılar için VS SDK, her zamanki gibi yüklü Visual Studio SDK 'Sı ile birlikte kullanılabilir.

Uzantılar özellikle Visual Studio 2022 SDK ve AMD64 için derlenmiş *olmalıdır* .

### <a name="update-your-extension-to-visual-studio-2022"></a>Uzantınızı Visual Studio 2022 'ye güncelleştirme

#### <a name="extensions-with-running-code"></a>Çalışan kod içeren uzantılar

Kod çalıştıran uzantılar özellikle Visual Studio 2022 için derlenmiş *olmalıdır* . Visual Studio 2022, özellikle Visual Studio 2022 ' i hedeflemeyen herhangi bir uzantıyı yüklemez.

Visual Studio 2022 uzantılarınızı Visual Studio 2022 ' e geçirmeyi öğrenin:

1. [Modernleştirin](#modernize-your-vsix-project).
1. Visual Studio 2022 ve daha eski sürümleri hedeflemeye olanak tanımak için [kaynak kodunuzu paylaşılan bir projeye yeniden düzenleyin](#use-shared-projects-for-multi-targeting) .
1. [Visual Studio 2022 hedefli BIR VSIX projesi](#add-a-visual-studio-2022-target)ve [paket/derleme yeniden eşleme tablosu](migrated-assemblies.md)ekleyin.
1. [Gerekli kod ayarlamaları yapılıyor](#handle-breaking-api-changes).
1. [Visual Studio 2022 uzantınızı test etme](#test-your-extension).
1. [Visual Studio 2022 uzantınızı yayımlama](#publish-your-extension).

#### <a name="extensions-without-running-code"></a>Kod çalıştırmadan uzantılar

Çalışan herhangi bir kod içermeyen uzantılar (örneğin, proje/öğe şablonları) iki ayrı VSIXs üretimi dahil yukarıdaki adımları takip etmek için gerekli *değildir* .

Bunun yerine, bir VSıX, `source.extension.vsixmanifest` dosyasının aşağıdaki gibi iki yükleme hedefi bildirdiği şekilde değiştirilmelidir:

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

Bu makaledeki adımları, paylaşılan projeler ve birden çok VNET kullanımı ile ilgili adımları atlayabilirsiniz. [Sınamaya](#test-your-extension)devam edebilirsiniz!

> [!NOTE]
> Visual Studio 2022 Preview kullanarak *Yeni* bir Visual Studio uzantısı yazıyorsanız ve (Ayrıca) visual Studio 2019 veya önceki bir sürümü hedeflemek istiyorsanız, [bu kılavuza](target-previous-versions.md)göz atın.

### <a name="msbuild-tasks"></a>MSBuild görevleri

MSBuild görevlerini yazardıysanız, Visual Studio 2022 ' de, 64 bit MSBuild.exe işleminde yüklenebilecekleri çok daha büyük olduğunu unutmayın. Göreviniz çalıştırmak için 32 bitlik bir işlem gerektiriyorsa, MSBuild 'in, görevi 32 bit bir işleme yüklemeyi bildiğinden emin olmak için [Bu MSBuild belgelerine](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) başvurun.

## <a name="modernize-your-vsix-project"></a>VSıX projenize modernleştirin

Uzantınızı Visual Studio 2022 desteği eklemeden önce, aşağıdaki gibi, mevcut projenizi temizlemek ve modernleştirin için bu sürenin daha fazla olması önerilir:

1. [packages.config ' den ' `PackageReference` ye geçirin ](/nuget/consume-packages/migrate-packages-config-to-package-reference).

1. Herhangi bir doğrudan derleme VS SDK derleme başvurularını PackageReference öğeleriyle değiştirin.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > *Çok sayıda* derleme başvurularını metapackage 'imize yalnızca *bir* packagereference ile değiştirebilirsiniz:
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" >Version="..." />
   >```

   Hedeflediğiniz en düşük Visual Studio sürümü ile eşleşen paket sürümlerini seçtiğinizden emin olun.

   VS SDK 'ya özgü olmayan bazı derlemeler (örneğin, Newtonsoft.Json.dll), Visual Studio 2022 ' den önceki basit bir başvuru aracılığıyla bulunabilir `<Reference Include="Newtonsoft.Json" />` , 2022 ancak Visual studio 2022 ' de bir paket başvurusu gerektirdiğinden, Visual studio ' de MSBuild 'in varsayılan derleme arama yolundan bazı Visual Studio çalışma zamanını ve SDK dizinlerini kaldırdık.

   Doğrudan derleme başvurularından NuGet paket başvurularına geçiş yapmak için ek derleme başvuruları ve çözümleyici paketleri, NuGet 'in geçişli kapanışının otomatik olarak yüklenmesini sağlar. Bu genellikle Tamam, ancak derleme sırasında ek uyarıların işaretlenme oluşmasına neden olabilirler. Bu uyarılarla çalışın ve olabildiğince fazla çözümleyin ve kod içi bölgeleri kullanarak çözemezsiniz bu uyarıları gizlemeyi göz önünde bulundurun `#pragma warning disable <id>` .

## <a name="use-shared-projects-for-multi-targeting"></a>Çoklu hedefleme için paylaşılan projeler kullanma

[Paylaşılan projeler](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) , Visual Studio 2015 ' de tanıtılan bir proje türüdür. Visual Studio 'daki paylaşılan projeler, kaynak kodu dosyalarının birden fazla proje arasında paylaşılmasını ve koşullu derleme sembolleri ile benzersiz başvuru kümelerini kullanarak farklı şekilde derlenme olanağı sağlar.

Visual Studio 2022, önceki tüm VS sürümlerinden farklı bir başvuru derlemeleri kümesi gerektirdiğinden kılavuzumuz, uzantınızı kolayca Visual Studio 2022 ve Visual Studio 2022 (ve sonraki sürümler) için daha kolay bir şekilde hedeflemek üzere paylaşılan projeleri kullanarak, kod paylaşımı, ancak ayrı başvurular sağlar.

Visual Studio uzantıları bağlamında, Visual Studio 2022 ve üzeri için bir VSıX projeniz ve Visual Studio 2019 ve önceki sürümleri için bir VSıX projesi olabilir. Bu projelerin her biri yalnızca bir içerir `source.extension.vsixmanifest` ve paketin 16. x SDK veya 17. x SDK 'sı ile başvuruları vardır. Bu VSıX projeleri, iki VS sürümü içinde paylaşılabilen tüm kaynak kodunuzu barındıracak yeni bir paylaşılan projeye paylaşılan bir proje başvurusu da olur.

Başlangıç noktası olarak, bu belgede, Visual Studio 2019 ' i hedefleyen ve uzantınızın Visual Studio 2022 ' de çalışmasını istediğiniz bir VSıX projeniz zaten var olduğunu varsayacağız.

Bu adımların tümü, Visual Studio 2019 ile tamamlanabilir.

1. Daha önce yapmadıysanız, bu güncelleştirme işlemindeki adımları kolaylaştırmak için [projelerinizi modernleştirin](#modernize-your-vsix-project) .

1. VS SDK 'ya başvuran mevcut her proje için çözümünüze yeni bir paylaşılan proje ekleyin.
   ![Yeni Proje Ekle komutu ](media/update-visual-studio-extension/add-new-project.png)
    ![ Yeni proje şablonu](media/update-visual-studio-extension/new-shared-project-template.png)

1. Her VS SDK 'ya başvuran projeden, paylaşılan proje karşılığına bir başvuru ekleyin.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Paylaşılan proje başvurusu Ekle" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Tüm kaynak kodu (. cs,. resx dahil), her VS SDK 'ya başvuran projeden paylaşılan proje karşılığına taşıyın.
`source.extension.vsixmanifest`Dosyayı VSIX projesinde bırakın.
   ![Paylaşılan proje tüm kaynak dosyalarını içerir](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Meta veri dosyaları (sürüm notları, lisans, simgeler vb.) ve VSCT dosyaları, paylaşılan bir dizine taşınmalı ve VSıX projesine bağlı dosyalar olarak eklenmelidir.
   ![Meta verileri ve VSCT dosyalarını bağlı dosyalar olarak ekleme](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - Meta veri dosyaları için, Buildavction ' ı olarak ayarlayın `Content` ve VSIX 'te öğesini olarak ayarlayın `true` .

      ![Veri dosyalarını VSıX 'e Ekle](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - VSCT dosyaları için, Buildavction öğesini olarak ayarlayın `VSCTCompile` ve VSIX 'e dahil etmeyin.
      Visual Studio bu ayarın desteklenmediğinden şikayet edebilir, ancak projeyi kaldırarak ve olarak değiştirerek derleme eylemini el ile değiştirebilirsiniz `Content``VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![VSCT dosyalarını VSCTCompile olarak ayarla](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. Yeni bir hata sunmadığından emin olmak için projenizi derleyin.

Projeniz artık Visual Studio 2022 desteği eklemek için hazırdır.

## <a name="add-a-visual-studio-2022-target"></a>Visual Studio 2022 hedefi ekleme

Bu belgede, [Visual Studio uzantınızı paylaşılan projelerle çarpan](#use-shared-projects-for-multi-targeting)adımları tamamladığınız varsayılmaktadır.

Uzantınızın Visual Studio 2022 desteğini Visual Studio 2019 kullanılarak tamamlanmış olan bu adımlarla eklemeye devam edin:

1. Çözümünüze yeni bir VSıX projesi ekleyin. Bu, Visual Studio 2022 ' i hedefleyen proje olacaktır. Şablonla gelen tüm kaynak kodlarını kaldırın, ancak *`source.extension.vsixmanifest` dosyayı saklayın*.

1. Yeni VSıX projenizde, Visual Studio 2019-hedef VSıX 'in başvurduğu paylaşılan projeye paylaşılan bir proje başvurusu ekleyin.

   ![Paylaşılan bir projeye ve iki VSıX projesine sahip bir çözüm](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Yeni VSıX projesinin düzgün bir şekilde yapılandırıldığını doğrulayın. Derleyici hatalarını çözmek için özgün VSıX projenizle eşleşecek başvurular eklemeniz gerekebilir.

1. Yönetilen VS uzantıları için, paket başvurularınızı 16. x (veya önceki bir sürümü) ile Visual Studio 2022 hedefli proje dosyanızdaki 17. x paket sürümlerine, NuGet paket yöneticisini kullanarak veya doğrudan proje dosyasını düzenledikten sonra güncelleştirin:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Nuget.org ' dan gerçekten kullanılabilir olan sürümleri kullanacaksınız. Daha önce kullanılan görevler yalnızca tanıtım amaçlıdır.

   Çoğu durumda, paket kimlikleri değişmiştir. Visual Studio 2022 ' deki değişikliklerin bir listesi için [paket/derleme eşleme tablosuna](migrated-assemblies.md) bakın.

   C++ dilinde yazılan uzantılar henüz ile derlemek için kullanılabilir SDK 'ye sahip değil.

1. C++ projeleri için, bunların AMD64 için derlenmesi gerekir. Yönetilen Uzantılar için, `x64` Visual Studio 2022 ' de uzantınızın her zaman 64-bit bir işlemde yüklediği her türlü CPU için projenizi hedeflemeye göre değiştirmeyi düşünün. `Any CPU` oldukça iyidir, ancak yalnızca x64 yerel ikili dosyalara başvuru yaparsanız uyarılar üretebilir.

   Uzantınızın yerel bir modülde sahip olabileceği tüm bağımlılıkların x86 görüntüsünden AMD64 görüntüsüne güncelleştirilmeleri gerekir.

1. `source.extension.vsixmanifest`Dosyanızı Visual Studio 2022 hedeflemesini yansıtacak şekilde düzenleyin. Etiketi, `<InstallationTarget>` Visual Studio 2022 ' i yansıtacak şekilde ayarlayın ve AMD64 yükünü belirtin:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   Visual Studio 2019 ' de, bu dosyanın Tasarımcısı yeni öğeyi kullanıma sunmadığından, `ProductArchitecture` Bu değişikliğin **Çözüm Gezgini**' de **birlikte Aç** komutuyla erişebileceğiniz bir XML Düzenleyicisi ile yapılması gerekir.

   Bu `ProductArchitecture` öğe kritiktir. Visual Studio *2022,* uzantınızı olmadan yüklemez.

   | Öğe | Değer | Açıklama |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Bu VSıX tarafından desteklenen platformlar. Büyük/küçük harfe duyarlı değildir. Her öğe için bir platform ve ınstalltarget başına bir öğe. 17,0 'den küçük ürün sürümleri için varsayılan değer x86 'dir ve atlanabilir.  Ürün sürümleri 17,0 ve üzeri için bu öğe gereklidir ve varsayılan değer yoktur. Visual Studio 2022 için yalnızca bu öğe için geçerli içerik "amd64" ' dir. |

1. Kaynak. Extension. valtmanifest ' in, Visual Studio 2019 (varsa) hedefi ile eşleşecek şekilde eşleşmesini sağlamak için gereken diğer ayarlamaları yapın. `Identity`Her iki uzantı için de, bildirimin öğesi IÇINDEKI VSıX kimliğinin aynı olması önemlidir.

Bu noktada, Visual Studio 2022 hedefli bir uzantı VSıX 'i vardır. Visual Studio 2022 hedefli VSıX projenizi oluşturmanız ve [görüntülenen tüm derleme sonlarına çalışmanız](#handle-breaking-api-changes)gerekir. Visual Studio 2022 hedefli VSıX projenizde derleme molaları yoksa tebrikler: test etmeye hazırsınız!

## <a name="handle-breaking-api-changes"></a>Son API değişikliklerini işle

Visual Studio 2022 ' de, önceki sürümlerde çalıştırıldığında kodunuzda değişiklik yapılmasını gerektirebilecek [son API değişiklikleri](breaking-api-list.md) vardır. Kodunuzun her biri için nasıl güncelleştirecağıyla ilgili ipuçları için bu belgeyi gözden geçirin.

Kodunuzu uyarlarken, Visual Studio 2022 için destek eklerken kodunuzun Visual Studio 2022 ' i desteklemeye devam edebilmesi için [koşullu derlemeyi](#use-conditional-compilation-symbols) kullanmanızı öneririz.

Visual Studio 2022 hedefli uzantı oluşturmayı aldığınızda, [teste](#test-your-extension)devam edin.

## <a name="use-conditional-compilation-symbols"></a>Koşullu derleme sembolleri kullan

Visual Studio 2022 ve önceki sürümleri için aynı kaynak kodu da aynı dosya olarak kullanmak istiyorsanız, büyük değişikliklere uyum sağlamak için kodunuzun çatalını kullanabilmek üzere koşullu derlemeyi kullanmanız gerekebilir. Koşullu derleme, bir C#, Visual Basic ve C++ dillerinin belirli yerlerde bir bütün olarak API 'Leri konairken birçok kodu paylaşmak için kullanılabilen bir özelliğidir.

Önişlemci yönergelerinin kullanımı ve koşullu derleme sembolleri hakkında daha fazla bilgi Microsoft docs [#if Önişlemci yönergesinde](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)bulunabilir.

Daha önceki Visual Studio sürümlerini hedefleyen projenizde, kodu farklı API 'Leri kullanmak için çatalla kullanılabilecek bir koşullu derleme simgesi gerekir. Aşağıdaki görüntüde gösterildiği gibi, proje özellikleri sayfasında koşullu derleme sembolünü ayarlayabilirsiniz:

![Koşullu derleme sembolleri ayarlanıyor](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Varsayılan olarak girdiğiniz sembol yalnızca bir yapılandırmaya uygulanabilir olduğundan, *Tüm* yapılandırmalar için derleme sembolünü ayarladığınızdan emin olun.

### <a name="c-techniques"></a>C \# teknikleri

Daha sonra, `#if` aşağıdaki kodda gösterildiği gibi bu simgeyi bir ön işlemci yönergesi () olarak kullanabilirsiniz. Daha sonra, farklı Visual Studio sürümleri arasındaki önemli değişikliğe göre kodunuzun çatalını oluşturabilirsiniz.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Visual Studio 2019
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

Bazı durumlarda, `var` türü adlandırmaktan kaçınmak için kullanabilirsiniz, böylece bölgeler gereksinimini ortadan kaldırabilirsiniz `#if` . Yukarıdaki kod parçacığı aynı zamanda şöyle yazılabilir:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

`#if`Söz dizimini kullanırken, söz dizimi vurgulamasını ve diğer yardım 'ın uzantısı için bir hedef Visual Studio sürümü ile ilgili olarak dikkat edilmesi için sunulan belgedeki dil hizmeti bağlam açılan listesini aşağıda gösterildiği şekilde nasıl kullanabileceğinizi fark edebilirsiniz.

![Paylaşılan bir projede koşullu derleme](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>XAML paylaşım teknikleri

XAML, Önişlemci sembollerine göre içerik özelleştirmeye izin veren bir ön işlemci içermez. Visual Studio 2022 ve önceki sürümler arasında farklı olması gereken iki XAML sayfasını kopyalayıp sürdürmek gerekli olabilir.

Ancak bazı durumlarda, Visual Studio 2022 ve önceki sürümlerde ayrı derlemelerde bulunan bir türe başvuru, derlemeye başvuran ad alanını kaldırarak bir XAML dosyasında yine de gösterilebilir.

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Uzantınızı test etme

Visual Studio 2022 ' i hedefleyen bir uzantıyı test etmek için Visual Studio 2022 Preview ' in yüklü olması gerekir.
Visual Studio 2022 Preview 'dan önce Visual Studio sürümlerinde 64 bit uzantıları çalıştırameyeceksiniz.

Visual Studio 2022 veya daha önceki bir sürümü hedeflemenize bakılmaksızın uzantılarınızı derlemek ve test etmek için Visual Studio 2022 Preview ' i kullanabilirsiniz. Visual Studio 2022 'den bir VSıX projesi başlatırken, Visual Studio 'nun deneysel bir örneği başlatılır.

Her Visual Studio sürümü ile test etmenizi kesinlikle öneririz.

Şimdi [uzantınızı yayımlamaya](#publish-your-extension)hazırsınız.

## <a name="publish-your-extension"></a>Uzantınızı yayımlayın

Harika, bu nedenle uzantınızın bir Visual Studio 2022 hedefini eklediniz ve test edilmiştir. Şimdi de dünyanın uzantısını admıire 'e yayımlamaya hazırsınız.

### <a name="visual-studio-marketplace"></a>Visual Studio Market

Uzantınızı [Visual Studio Market](https://marketplace.visualstudio.com/) yayımlamak, yeni kullanıcıların uzantınızı bulmasını ve yüklemesini sağlamak için harika bir yoldur. Uzantınızın Visual Studio 2022 ' i özel olarak hedeflemesini veya eski VS sürümlerini hedeflemesini ister. Market, sizin için destek sağlar.

Daha sonra Market, birden fazla VNET 'i tek bir market listesine karşıya yükleyerek Visual Studio 2022 hedefli VSıX ve bir Visual Studio 2022 VSıX 'i yüklemenizi sağlar. Kullanıcılarınız, VS uzantısı Yöneticisi kullanılırken, yüklemiş oldukları VS sürümü için doğru VSıX 'i otomatik olarak alır.

Visual Studio 2022 ' nin önizleme sürümleri için Market, Market listeleme başına yalnızca tek bir VSıX dosyasını destekleyecektir. Visual Studio 2022 önizlemedeyken, uzantınızın ayrı bir Visual Studio 2022 Market listesine sahip olmanız önerilir. Böylece, Visual Studio 2022 uzantınızı, Visual Studio 'nun önceki sürümlerinde müşterilerinizi etkilemeden istediğiniz şekilde yineleyebilirsiniz. Ayrıca, söz konusu ungüvenilirliğin kaynağı, temel uzantıınıza göre Visual Studio 2022 olsa da, beklenenleri ayarlamak için uzantıyı ' Önizleme ' olarak işaretleyebilirsiniz.

### <a name="custom-installer"></a>Özel yükleyici

Uzantınızı yüklemek için bir MSI/EXE oluşturursanız ve uzantınızı yüklemek için vsixinstaller.exe oluşturma işlemi yapıyorsanız, Visual Studio 2022 ' deki VSıX yükleyicisinin güncelleştirildiğinden emin olmalısınız. Geliştiricilerin Visual Studio 2022 ' ye uzantı yüklemek için Visual Studio 2022 ile birlikte gelen VSıX yükleyicisi sürümünü kullanması gerekir. Visual Studio 2022 ' deki VSıX yükleyicisi, Visual Studio 'nun aynı makinede Visual Studio 2022 ile yan yana yüklenen önceki sürümlerini hedefleyen ilgili uzantıları da yükler.

### <a name="network-share"></a>Ağ paylaşma

Uzantınızı bir LAN veya başka bir şekilde paylaşabilirsiniz. Visual Studio 2022 ' i ve Visual Studio 2022 ' i hedefliyorsanız, kullanıcılarınızın yüklemiş olduğu Visual Studio sürümüne bağlı olarak hangi VSıX 'in yükleneceğini bilmelerini sağlamak için, birden çok VNET 'i tek tek paylaşmanız ve bunlara dosya adları vermeniz (veya benzersiz klasörlere yerleştirmeniz) gerekir.

### <a name="other-considerations"></a>Diğer önemli noktalar

#### <a name="dependencies"></a>Bağımlılıklar

VSıX, öğe aracılığıyla başka bir VSıX belirtirse `<dependency>` , başvurulan her VSıX VSIX ile aynı hedeflere ve ürün mimarilerine yüklenmesi gerekir. Bağımlı bir VSıX hedeflenen Visual Studio yüklemesini desteklemiyorsa VSıX başarısız olur. Bağımlı VSıX 'in sizinkinden daha fazla hedefe göre daha fazla hedef ve mimariyi desteklemesi, ancak daha az olmaması yeterlidir. Bu kısıtlama, bir VSıX 'in bağımlılıklarla dağıtım ve dağıtım yaklaşımının, bağımlılarını yansıtmasının gerektiği anlamına gelir.

## <a name="q--a"></a>Soru-Cevap

**S**: uzantım yalnızca veri sağladığından (örneğin, şablonlar), Visual Studio 2022 'i de içeren tek bir uzantı oluşturabilir miyim?

Y **: Evet**!  Bunun hakkında daha fazla bilgi için [kodu çalıştırmadan](#extensions-without-running-code) bkz. uzantıları.

**S**: bir NuGet bağımlılığı eski birlikte çalışma derlemelerini getiriyor ve çakışan sınıflara neden oluyor.

Y **: yinelenen** derlemeleri önlemek için. csproj dosyanıza aşağıdaki satırı ekleyin:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

Bu, paket başvurularının derlemenin eski sürümünün diğer bağımlılıklardan içeri aktarılmasını engeller.

**S**: kaynak dosyalarımı paylaşılan bir projeye geçirdikten sonra Komutlarım ve kısayol tuşları Visual Studio 'da çalışmıyor.

Y **: görüntü** iyileştirici örneği için [Adım 2,4](samples.md#step-2---refactor-source-code-into-a-shared-project) , vsct dosyalarını vsct dosyanıza derlenmek üzere bağlantılı öğeler olarak nasıl ekleneceğini gösterir.

## <a name="next-steps"></a>Sonraki adımlar

Bir adım adım örneği, [ımageiyileştiriciyi](samples.md), projenin bağlantılarıyla ve her bir adımla ilgili kod değişikliklerinden izleyin.
