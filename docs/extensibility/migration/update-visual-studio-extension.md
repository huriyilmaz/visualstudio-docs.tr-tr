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
ms.openlocfilehash: 2aa92605ab40e51429542465a26e485a8167ef04
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128432682"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Visual Studio 2022 için Visual Studio uzantısını güncelleştirme

> [!IMPORTANT]
> bu kılavuzdaki öneri, büyük değişiklikler gerektiren uzantılara geçiş yapmak için Visual Studio 2019 ve 2022 ' de çalışır. Bu durumlarda iki VSıX projesi ve koşullu derleme olması önerilir.
> birçok uzantı, bu kılavuzda uzantınızı modernleştirmede gerekli olan küçük değişiklikler ile hem Visual Studio 2019 hem de 2022 üzerinde çalışabilir.
> uzantınızı Visual Studio 2022 ' de deneyin ve uzantınız için en uygun seçeneği değerlendirin.

bu kılavuzu izleyerek uzantınızı Visual Studio 2022 Preview ile çalışacak şekilde güncelleştirebilirsiniz. Visual Studio 2022 Preview, 64 bitlik bir uygulamadır ve VS SDK 'sında bazı önemli değişiklikler sunar. bu kılavuzda 2022 Visual Studio, uzantınızın Visual Studio 2022 ' nin güncel önizlemesiyle çalışmasını sağlamak için gereken adımlarda size yol gösterilir.

## <a name="installing"></a>Yükleme

[Visual Studio 2022 önizleme indirmelerinde](https://visualstudio.microsoft.com/vs/preview/vs2022)Visual Studio 2022 preview ' ü yükler.

### <a name="extensions-written-in-a-net-language"></a>.NET dilinde yazılan uzantılar

yönetilen uzantılar için Visual Studio 2022 ' i hedefleyen VS SDK *yalnızca* NuGet açık:

- [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (17. x sürümleri) meta paketi, ihtiyacınız olan başvuru derlemelerinin çoğunu veya tümünü sağlar.
- [Microsoft. vssdk. buildtools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (17. x sürümleri) paketine, Visual Studio 2022 uyumlu bir vsıx oluşturmak için vsıx projenizden başvurulmalıdır.

Herhangi bir son değişikliğe başvurmasa bile, uzantıların "herhangi bir CPU" veya "x64" platformu ile derlenmesi *gerekir* . "x86" platformu Visual Studio 2022 64-bit işlemiyle uyumsuzdur.

### <a name="extensions-written-in-c"></a>C++ dilinde yazılan uzantılar

C++ ile derlenen uzantılar için VS SDK, her zamanki gibi yüklü Visual Studio SDK 'sı ile kullanılabilir.

herhangi bir bölme değişikliğine başvurmasa bile, uzantıların özellikle Visual Studio 2022 SDK ve amd64 için derlenmesi *gerekir* .

### <a name="update-your-extension-to-visual-studio-2022"></a>uzantınızı Visual Studio 2022 olarak güncelleştirin

#### <a name="extensions-with-running-code"></a>Çalışan kod içeren uzantılar

kod çalıştıran uzantılar özellikle Visual Studio 2022 için *derlenmelidir* . Visual Studio 2022, özellikle Visual Studio 2022 ' i hedeflemeyen herhangi bir uzantıyı yüklemez.

pre-Visual Studio 2022 uzantılarınızı Visual Studio 2022 ' e nasıl geçirebileceğinizi öğrenin:

1. [Modernleştirin](#modernize-your-vsix-project).
1. Visual Studio 2022 ve daha eski sürümleri hedeflemeye olanak tanımak için [kaynak kodunuzu paylaşılan bir projeye yeniden düzenleyin](#use-shared-projects-for-multi-targeting) .
1. [Visual Studio 2022 hedefli bir vsıx projesi](#add-a-visual-studio-2022-target)ve [paket/derleme yeniden eşleme tablosu](migrated-assemblies.md)ekleyin.
1. [Gerekli kod ayarlamaları yapılıyor](#handle-breaking-api-changes).
1. [Visual Studio 2022 uzantınızı test etme](#test-your-extension).
1. [Visual Studio 2022 uzantınızı yayımlıyoruz](#publish-your-extension).

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
> *yeni* bir Visual Studio uzantısı yazıyorsanız Visual Studio 2022 Preview ' i kullanarak ve (ayrıca) Visual Studio 2019 veya önceki bir sürümü hedeflemek istiyorsanız, [bu kılavuza](target-previous-versions.md)göz atın.

### <a name="msbuild-tasks"></a>MSBuild görevleri

MSBuild görevleri yazardıysanız, Visual Studio 2022 ' de, 64 bit MSBuild.exe sürecinde yüklenebilecekleri çok daha büyük olduğunu unutmayın. göreviniz çalıştırmak için 32 bitlik bir işlem gerektiriyorsa, MSBuild bir 32 bit işleme MSBuild emin olmak için [bu belgeye](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) başvurun.

## <a name="modernize-your-vsix-project"></a>VSıX projenize modernleştirin

uzantınızı Visual Studio 2022 desteği eklemeden önce, bu süreyi daha sonra modernleştirin ve aşağıdakiler de dahil olmak üzere mevcut projenizi temizlemek ve için yapmanız önemle önerilir:

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
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" Version="..." />
   >```

   hedeflediğiniz Visual Studio en düşük sürümü ile eşleşen paket sürümlerini seçtiğinizden emin olun.

   VS SDK 'ya özgü olmayan bazı derlemeler (örneğin, Newtonsoft.Json.dll) Visual Studio 2022 ' den önceki basit bir başvuru aracılığıyla bulunabilir `<Reference Include="Newtonsoft.Json" />` , ancak Visual Studio 2022 ' de Visual Studio 2022 ' de bir paket başvurusu gerektirdiğinden Visual Studio 'nin varsayılan derleme arama yolundan bazı MSBuild çalışma zamanı ve SDK dizinlerini kaldırdık.

   doğrudan derleme başvurularından NuGet paket başvurularına geçiş yapmak için, bağımlılıkların geçişli kapanışının otomatik olarak yüklenmesi NuGet nedeniyle ek derleme başvuruları ve çözümleyici paketleri alabilirsiniz. Bu genellikle Tamam, ancak derleme sırasında ek uyarıların işaretlenme oluşmasına neden olabilirler. Bu uyarılarla çalışın ve olabildiğince fazla çözümleyin ve kod içi bölgeleri kullanarak çözemezsiniz bu uyarıları gizlemeyi göz önünde bulundurun `#pragma warning disable <id>` .

## <a name="use-shared-projects-for-multi-targeting"></a>Çoklu hedefleme için paylaşılan projeler kullanma

[paylaşılan projeler](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) Visual Studio 2015 ' de tanıtılan bir proje türüdür. Visual Studio paylaşılan projeler, kaynak kodu dosyalarının birden fazla proje arasında paylaşılmasını ve koşullu derleme sembollerini ve benzersiz başvuru kümelerini kullanarak farklı şekilde derlenme olanağı sağlar.

Visual Studio 2022, önceki tüm VS sürümlerinden farklı bir başvuru derlemeleri kümesi gerektirdiğinden, kılavuzumuz, uzantınızı kolayca Visual Studio 2022 ve Visual Studio 2022 (ve sonraki sürümler) olarak çok hedeflemek için, kod paylaşımı, ancak ayrı başvurular sağlamak üzere paylaşılan projeler kullanmaktır.

Visual Studio uzantıları bağlamında, Visual Studio 2022 ve üzeri için bir vsıx projesine ve Visual Studio 2019 ve daha önceki bir vsıx projesine sahip olabilirsiniz. Bu projelerin her biri yalnızca bir içerir `source.extension.vsixmanifest` ve paketin 16. x SDK veya 17. x SDK 'sı ile başvuruları vardır. Bu VSıX projeleri, iki VS sürümü içinde paylaşılabilen tüm kaynak kodunuzu barındıracak yeni bir paylaşılan projeye paylaşılan bir proje başvurusu da olur.

başlangıç noktası olarak, bu belge için Visual Studio 2019 ' i hedefleyen ve uzantınızın Visual Studio 2022 ' de çalışmasını istediğiniz bir vsıx projeniz olduğunu varsayacağız.

bu adımların tümü, Visual Studio 2019 ile tamamlanabilir.

1. Daha önce yapmadıysanız, bu güncelleştirme işlemindeki adımları kolaylaştırmak için [projelerinizi modernleştirin](#modernize-your-vsix-project) .

1. VS SDK 'ya başvuran mevcut her proje için çözümünüze yeni bir paylaşılan proje ekleyin.
   ![yeni Project komutu ekle ](media/update-visual-studio-extension/add-new-project.png)
    ![ yeni proje şablonu](media/update-visual-studio-extension/new-shared-project-template.png)

1. Her VS SDK 'ya başvuran projeden, paylaşılan proje karşılığına bir başvuru ekleyin.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Paylaşılan proje başvurusu Ekle" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Tüm kaynak kodu (. cs,. resx dahil), her VS SDK 'ya başvuran projeden paylaşılan proje karşılığına taşıyın.
`source.extension.vsixmanifest`Dosyayı VSIX projesinde bırakın.
   ![Paylaşılan proje tüm kaynak dosyalarını içerir](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Meta veri dosyaları (sürüm notları, lisans, simgeler vb.) ve VSCT dosyaları, paylaşılan bir dizine taşınmalı ve VSıX projesine bağlı dosyalar olarak eklenmelidir. Paylaşılan dizinin paylaşılan projeden ayrı olduğunu unutmayın.
   ![Meta verileri ve VSCT dosyalarını bağlı dosyalar olarak ekleme](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - Meta veri dosyaları için, Buildavction ' ı olarak ayarlayın `Content` ve VSIX 'te öğesini olarak ayarlayın `true` .

      ![Veri dosyalarını VSıX 'e Ekle](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - VSCT dosyaları için, Buildavction öğesini olarak ayarlayın `VSCTCompile` ve VSIX 'e dahil etmeyin.
      bu ayarın desteklenmediğinden Visual Studio şikayet edebilir, ancak projeyi kaldırarak ve olarak değiştirerek derleme eylemini el ile değiştirebilirsiniz `Content``VSCTCompile`

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

projeniz artık Visual Studio 2022 desteğine eklenmeye hazırdır.

## <a name="add-a-visual-studio-2022-target"></a>Visual Studio 2022 hedefi ekleme

bu belge, [Visual Studio uzantınızı paylaşılan projelerle çarpan](#use-shared-projects-for-multi-targeting)adımları tamamladığınızı varsayar.

Visual Studio 2019 kullanılarak tamamlanabilmesi için bu adımlarla uzantınızı Visual Studio 2022 desteği eklemeye devam edin:

1. çözümünüze yeni bir vsıx Project ekleyin. bu, Visual Studio 2022 ' i hedefleyen proje olacaktır. Şablonla gelen tüm kaynak kodlarını kaldırın, ancak *`source.extension.vsixmanifest` dosyayı saklayın*.

1. yeni vsıx projenizde, Visual Studio 2019-hedefleme vsıx 'in başvurduğu paylaşılan projeye paylaşılan bir proje başvurusu ekleyin.

   ![Paylaşılan bir projeye ve iki VSıX projesine sahip bir çözüm](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Yeni VSıX projesinin düzgün bir şekilde yapılandırıldığını doğrulayın. Derleyici hatalarını çözmek için özgün VSıX projenizle eşleşecek başvurular eklemeniz gerekebilir.

1. yönetilen VS uzantıları için, paket başvurularınızı 16. x (veya önceki bir sürümü) ile Visual Studio 2022 hedefli proje dosyanızdaki 17. x paket sürümlerine güncelleştirin NuGet Paket Yöneticisi veya doğrudan proje dosyasını düzenleyebilirsiniz:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Nuget.org ' dan gerçekten kullanılabilir olan sürümleri kullanacaksınız. Daha önce kullanılan görevler yalnızca tanıtım amaçlıdır.

   Çoğu durumda, paket kimlikleri değişmiştir. Visual Studio 2022 ' deki değişikliklerin listesi için [paket/derleme eşleme tablosuna](migrated-assemblies.md) bakın.

   C++ dilinde yazılan uzantılar henüz ile derlemek için kullanılabilir SDK 'ye sahip değil.

1. C++ projeleri için, bunların AMD64 için derlenmesi gerekir. yönetilen uzantılar için, uygulamanızı herhangi bir CPU için derlemeden hedefleme olarak değiştirmeyi düşünün `x64` . Visual Studio 2022 ' de, uzantınızın her zaman 64 bit işleme yüklendiğini gösterir. `Any CPU` oldukça iyidir, ancak yalnızca x64 yerel ikili dosyalara başvuru yaparsanız uyarılar üretebilir.

   Uzantınızın yerel bir modülde sahip olabileceği tüm bağımlılıkların x86 görüntüsünden AMD64 görüntüsüne güncelleştirilmeleri gerekir.

1. `source.extension.vsixmanifest`dosyanızı Visual Studio 2022 hedeflemesini yansıtacak şekilde düzenleyin. `<InstallationTarget>`etiketi Visual Studio 2022 yansıtacak şekilde ayarlayın ve amd64 yükünü belirtin:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   Visual Studio 2019 ' de, bu dosyanın tasarımcısı yeni öğeyi kullanıma sunmadığından, `ProductArchitecture` bu değişikliğin, **Çözüm Gezgini** **birlikte aç** komutuyla erişebileceğiniz bir xml düzenleyicisi ile yapılması gerekir.

   Bu `ProductArchitecture` öğe kritiktir. Visual Studio 2022, *uzantınız* olmadan yüklenmez.

   | Öğe | Değer | Açıklama |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Bu VSIX tarafından desteklenen platformlar. Büyük/büyük/büyük harfe duyarlı değildir. Öğe başına bir platform ve InstallTarget başına bir öğe. 17.0'dan küçük ürün sürümleri için varsayılan değer x86'dır ve atlanabilir.  Ürün sürümleri 17.0 ve daha büyük için bu öğe gereklidir ve varsayılan değer yoktur. 2022 Visual Studio için bu öğe için tek geçerli içerik "amd64" şeklindedir. |

1. Source.extension.vsixmanifest içinde, 2019'un 2019'a ait olanla (varsa) eşleşmesi için gereken diğer tüm ayarlamaları Visual Studio olun. Her biri farklı bir VS sürümünü hedef alan uzantının 2 farklı sürümünü yayımlarsanız, bildirimin öğesinde VSIX kimliğinin her iki uzantı için de farklı olduğu `Identity` önemlidir.

Bu noktada, 2022 Visual Studio VSIX uzantınız vardır. 2022 Visual Studio VSIX projenizi derlemeniz ve görünen [derleme sonları üzerinde çalışmanız gerekir.](#handle-breaking-api-changes) Visual Studio 2022 hedefli VSIX projeniz için derleme sonları yoksa, tebrikler: Test etmeye hazırsın!

## <a name="handle-breaking-api-changes"></a>Api değişikliklerini bozmayı işleme

2022'de Visual Studio API değişiklikleri var ve önceki sürümlerde çalışmalarından itibaren kodunuz üzerinde değişiklik gerektirabiliyor. [](breaking-api-list.md) Kodunuzu her biri için güncelleştirme ipuçları için bu belgeyi gözden geçirebilirsiniz.

Kodunuzu uyarlarken, kodunuzun [](#use-conditional-compilation-symbols) 2022 öncesi 2022 öncesi desteğine devam etmek için koşullu derlemeyi Visual Studio 2022'ye Visual Studio öneririz.

2022 hedefli uzantı Visual Studio için teste devam [edin.](#test-your-extension)

## <a name="use-conditional-compilation-symbols"></a>Koşullu derleme sembolleri kullanma

Visual Studio 2022 ve önceki sürümler için aynı kaynak kodu, hatta aynı dosyayı kullanmak isterseniz, hataya neden olan değişikliklere uyum sağlamak için kodunuzun bir hataya neden olması için koşullu derlemeyi kullanmanız gerekir. Koşullu derleme, C#, Visual Basic ve C++ dillerinin bir özelliğidir ve belirli yerlerde farklı API'leri bulundurarak çoğu kodu paylaşmak için kullanılabilir.

Ön işlemci yönergelerinin ve koşullu derleme sembollerinin kullanımı hakkında daha fazla bilgi için bkz. Microsoft docs [#if yönergesi.](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)

Daha önceki sürümleri hedef alan Visual Studio, daha sonra farklı API'leri kullanmak üzere kodun birikişini yapmak için kullanılan bir koşullu derleme simgesine ihtiyaç olacaktır. Aşağıdaki görüntüde gösterildiği gibi, proje özellikleri sayfasında koşullu derleme simgesini ayarlayın:

![Koşullu derleme simgelerini ayarlama](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Varsayılan olarak, girersiniz sembolü *yalnızca* bir yapılandırma için geçerli olduğundan, tüm yapılandırmalar için derleme sembolünü ayardan emin olun.

### <a name="c-techniques"></a>C \# teknikleri

Daha sonra bu simgeyi aşağıdaki kodda gösterildiği gibi bir ön işlemci yönergesi ( `#if` ) olarak kullanabilirsiniz. Daha sonra farklı sürümler arasındaki hataya neden olan değişiklikle başa olmak için kodunuzun Visual Studio sabilirsiniz.

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

Bazı durumlarda, türünü adlandırmayı `var` önlemek ve bu sayede bölgelere ihtiyaçtan kaçınmak için `#if` kullanabilirsiniz. Yukarıdaki kod parçacığı şu şekilde de yazabilirsiniz:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

Söz dizimi kullanılırken, aşağıda gösterilen belgede dil hizmeti bağlam açılır listesinden söz dizimi vurgulamayı nasıl değiştirerek kullanabileceğinizi ve diğer dil hizmetinin uzantımızın bir hedef Visual Studio sürümüne odaklanmaya odaklanması için sunduğu diğer yardımlara dikkat `#if` edin.

![Paylaşılan projede koşullu derleme](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>XAML paylaşım teknikleri

XAML'de, içeriği ön işlemci sembollerine göre özelleştirmeye olanak sağlayan bir ön işlemci yoktur. İçeriklerinin 2022 ve önceki sürümler arasında farklı olması gereken iki XAML Visual Studio kopyalayıp bakımının gerçek olması gerekebilir.

Ancak bazı durumlarda, Visual Studio 2022 ve önceki sürümler arasında ayrı derlemelerde var olan bir türe yapılan bir başvuru, derlemeye başvuran ad alanını kaldırarak bir XAML dosyasında temsil edilebilir:

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Uzantınızı test etmek

2022'yi Visual Studio uzantıyı test etmek için 2022 Preview Visual Studio yüklemeniz gerekir.
2022 Preview'dan önce Visual Studio sürümlerinde 64 bit Visual Studio çalıştıramayacaksanız.

Uzantılarınızı 2022'Visual Studio veya önceki bir sürümü hedeflese de test etmek için Visual Studio 2022 Preview sürümünü kullanabilirsiniz. Visual Studio 2022'den bir VSIX projesi başlatan deneysel Visual Studio örneği başlatacak.

Uzantının desteklemeyi Visual Studio sürümüyle test etmeyi kesinlikle öneririz.

Artık uzantınızı [yayımlamaya hazır olursanız.](#publish-your-extension)

## <a name="publish-your-extension"></a>Uzantınızı yayımlama

Harika, bu nedenle uzantınıza bir Visual Studio 2022 hedefi eklediniz ve test ettiniz. Artık uzantıyı dünya için yayımlamaya hazır olursanız.

### <a name="visual-studio-marketplace"></a>Visual Studio Market

Uzantınızı Visual Studio [Market'te yayımlamak,](https://marketplace.visualstudio.com/) yeni kullanıcıların uzantınızı bulup yüklemelerini almak için harika bir yol sağlar. Uzantınız 2022'Visual Studio veya eski VS sürümlerini de hedeflese de Market sizi desteklemek için oradadır.

Gelecekte Market, tek bir Market listelemesine birden çok VSIX yüklemenizi sağlayarak Visual Studio 2022 hedefli VSIX'inizi ve 2022 öncesi VSIX Visual Studio karşıya yüklemenizi sağlar. Kullanıcılarınız, VS uzantısı yöneticisini kullanırken, yüklemiş olduğu VS sürümü için doğru VSIX'i otomatik olarak alır.

Visual Studio 2022'nin önizleme yayınlarında Market, Market listelemesi başına yalnızca tek bir VSIX dosyasını destekleyecektir. 2022 Visual Studio sürümü önizlemededir ancak uzantınız için ayrı bir Visual Studio 2022 yalnızca Market listelemeniz gerekir. Bu şekilde, 2022 Visual Studio 2022 uzantınızı, önceki sürümlerde müşterileriniz etkilenmeden Visual Studio. Ayrıca, güvenilirliğin kaynağı 2022'de olsa temel uzantınıza göre daha az güvenilir olacağını Visual Studio olarak da uzantıyı 'önizleme' olarak işaret görebilirsiniz.

### <a name="custom-installer"></a>Özel yükleyici

Uzantınızı yüklemek için bir MSI/EXE derlemeniz ve uzantınızı yüklemek için vsixinstaller.exe oluşturması (bir parçası) varsa, Visual Studio 2022'deki VSIX yükleyicinin güncelleştirilmiş olduğunu bilirsiniz. Geliştiricilerin, Visual Studio 2022'ye uzantı yüklemek için Visual Studio 2022 ile birlikte gelen VSIX yükleyicisi sürümünü kullanmaları gerekir. Visual Studio 2022'deki VSIX yükleyicisi, aynı makinede Visual Studio 2022 ile yan yana yüklü olan önceki Visual Studio sürümlerini hedef alan geçerli uzantıları da yükleyecek.

### <a name="network-share"></a>Ağ paylaşımı

Uzantınızı LAN veya başka bir yolla paylaşabilirsiniz. Visual Studio 2022 ve Visual Studio 2022 öncesi sürümlere yönelikse, size birden çok VSIX'i ayrı ayrı paylaşmanız ve kullanıcılarınıza hangi VSIX'in yüklendiklerine göre yüklenecekleri VSIX hakkında bilgi vermeleri (veya benzersiz klasörlere yer vermeleri) Visual Studio gerekir.

### <a name="other-considerations"></a>Diğer önemli noktalar

#### <a name="dependencies"></a>Bağımlılıklar

VSIX'iniz öğesi aracılığıyla bağımlılık olarak başka bir VSIX belirtirse, başvurulan her VSIX'in VSIX'iniz ile aynı hedeflere ve ürün `<dependency>` mimarilerine yüklemesi gerekir. Bağımlı bir VSIX hedeflenen yüklemesini desteklemezse Visual Studio VSIX'iniz başarısız olur. Bağımlı VSIX'in sizinkilerden daha fazla hedefi ve mimariyi desteklemesi sorun değildir. Bu kısıtlama, bağımlılıkları olan bir VSIX'in dağıtım ve dağıtım yaklaşımının bağımlılarınkileri yansıtması gerektiği anlamına gelir.

## <a name="q--a"></a>Soru-Cevap

**S:** Uzantım herhangi bir birlikte çalışma değişikliği gerektirmez çünkü yalnızca veri sağlar (örneğin, şablonlar), 2022'de de Visual Studio uzantı oluşturabilir miyim?

**A:** Evet!  Bu [konuda daha fazla bilgi için bkz.](#extensions-without-running-code) Kod çalıştırmadan uzantılar.

**S:** NuGet bir bağımlılık, eski birlikte çalışma derlemelerini getirmek ve sınıfların çatıştırmasına neden olmaktır.

**Bir**: Derlemelerin yinelen etmesini önlemek için .csproj dosyanıza aşağıdaki satırı ekleyin:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

Bu, paket başvurularının derlemenin eski sürümünü diğer bağımlılıklardan içeri aktarmasını önler.

**S:** Kaynak dosyalarım paylaşılan bir projeye Visual Studio komutlarım ve kısayol tuşlarım çalışmaıyor.

**A:** [Görüntü İyileştirici örneğinin 2.4.](samples.md#step-2---refactor-source-code-into-a-shared-project) adımı, VSCT dosyalarının VSCT dosyanıza derlenmiş şekilde bağlı öğeler olarak nasıl ekli olduğunu gösterir.

## <a name="next-steps"></a>Sonraki adımlar

Her adım için proje bağlantılarını ve kod değişikliklerini içeren [imageOptimizer](samples.md)adım adım örneğini izleyin.
