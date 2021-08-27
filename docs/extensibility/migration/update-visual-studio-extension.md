---
title: Bir Visual Studio güncelleştirme
description: Visual Studio 2022 ile çalışacak şekilde Visual Studio öğrenin.
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
ms.openlocfilehash: bc76fa880814b0ae50ca6ad25d3f38849818b7d0
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980647"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Visual Studio 2022 için Visual Studio uzantısını güncelleştirme

> [!IMPORTANT]
> Bu kılavuzda yer alan öneri, geliştiricilere hem 2019 hem de 2022'de büyük değişiklikler gerektiren uzantıların Visual Studio yöneliktir. Bu gibi durumlarda iki VSIX projesinin ve koşullu derlemenin kullanılması önerilir.
> Birçok uzantı hem Visual Studio 2019 hem de 2022'de bu kılavuzda uzantınızı modernleştirme önerisinde yer alan önerilerin ardından gerekli olmayacak küçük değişikliklerle birlikte çalışabilecektir.
> 2022'Visual Studio uzantınızı deneyin ve uzantınız için en uygun seçeneği değerlendirin.

Bu kılavuzu takip edin ve uzantınızı Visual Studio 2022 Preview ile çalışacak şekilde güncelleştirin. Visual Studio 2022 Preview, 64 bitlik bir uygulamadır ve VS SDK'da bazı yeni değişikliklere neden olur. Bu kılavuz, uzantınızı Visual Studio 2022'nin geçerli önizlemesi ile birlikte çalışarak kullanıcıların 2022'ye ulaşmadan önce yüklemelerine hazır hale Visual Studio adımlarda size yol sağlar.

## <a name="installing"></a>Yükleme

2022 Preview indirmelerinden Visual Studio [2022 Preview'Visual Studio yükleyin.](https://visualstudio.microsoft.com/vs/preview/vs2022)

### <a name="extensions-written-in-a-net-language"></a>.NET dilinde yazılmış uzantılar

Yönetilen uzantılar için Visual Studio 2022'ye yönelik VS SDK yalnızca şu *NuGet:*

- [Microsoft.VisualStudio.Sdk](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (17.x sürümleri) meta-paketi, ihtiyacınız olacak başvuru derlemelerinin çoğunu veya hepsini getirir.
- [Microsoft.VSSDK.BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (17.x sürümleri) paketine VSIX projenizin başvurarak 2022 uyumlu bir VSIX Visual Studio oluşturması gerekir.

Yeni değişikliklere başvursanız bile uzantıların  "Herhangi bir CPU" veya "x64" platformuyla derlenmiş olması gerekir. "x86" platformu, Visual Studio 2022'nin 64 bit işlemiyle uyumsuzdur.

### <a name="extensions-written-in-c"></a>C++ ile yazılmış uzantılar

C++ ile derlenmiş uzantılar için VS SDK her zamanki gibi Visual Studio SDK ile kullanılabilir.

Yeni değişikliklere başvurulmasanız bile uzantılar özellikle Visual Studio 2022 SDK'sı ve amd64 için derlenmiş olması gerekir. 

### <a name="update-your-extension-to-visual-studio-2022"></a>Uzantınızı Visual Studio 2022'ye güncelleştirme

#### <a name="extensions-with-running-code"></a>Kod çalıştıran uzantılar

Çalışan koda sahip *uzantılar* özel olarak 2022'Visual Studio derlenmiş olması gerekir. Visual Studio 2022 özellikle 2022'ye hedef Visual Studio uzantı yüklemez.

Visual Studio 2022 öncesi uzantılarınızı 2022'de Visual Studio öğrenin:

1. [Projelerinizi modernleştirin.](#modernize-your-vsix-project)
1. 2022 [ve daha eski](#use-shared-projects-for-multi-targeting) sürümleri hedeflemek için kaynak kodunuzu paylaşılan Visual Studio yeniden düzenleme.
1. [2022 Visual Studio VSIX](#add-a-visual-studio-2022-target)projesine ve paket/derleme yeniden ekleme [tablomuza bir ekleyin.](migrated-assemblies.md)
1. [Gerekli kod ayarlamalarını yapma.](#handle-breaking-api-changes)
1. [Visual Studio 2022 uzantınızı test etme.](#test-your-extension)
1. [Visual Studio 2022 uzantınızı yayımlama.](#publish-your-extension)

#### <a name="extensions-without-running-code"></a>Kod çalıştırmadan uzantılar

Çalışan kod (örneğin, proje/öğe şablonları) içeren uzantılar,  iki ayrı VSIX'in üretimi de dahil olmak üzere yukarıdaki adımları izlemesi gerekmez.

Bunun yerine, bir VSIX dosyasının aşağıdaki gibi iki yükleme `source.extension.vsixmanifest` hedefi bildirilecek şekilde değiştirilmiş olması gerekir:

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

Paylaşılan projeleri ve birden çok VSIX'i kullanma hakkında bu makaledeki adımları atlayabilirsiniz. Teste devam [edebilirsiniz!](#test-your-extension)

> [!NOTE]
> Visual Studio 2022 Preview kullanarak yeni bir *Visual Studio* uzantısı yazarsanız ve (ayrıca) Visual Studio 2019 veya önceki bir sürümü hedeflemek için bu kılavuzu [göz atabilirsiniz.](target-previous-versions.md)

### <a name="msbuild-tasks"></a>MSBuild görevleri

MSBuild görevleri yazarsanız, Visual Studio 2022'de bunların 64 bitlik bir işlemde yüklenme olasılığı çok daha MSBuild.exe. Göreviniz için 32 bit işlem çalıştırmak gerekirse, [görevinizi](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) 32 bit bir MSBuild yüklemek için MSBuild emin olmak için bu MSBuild belgelerine bakın.

## <a name="modernize-your-vsix-project"></a>VSIX projenizi modernleştirme

Uzantınıza Visual Studio 2022 desteği eklemeden önce aşağıdakiler dahil olmak üzere mevcut projenizi temizlemenizi ve modernleştirmenizi kesinlikle öneririz:

1. [packages.config'a geçiş. `PackageReference` ](/nuget/consume-packages/migrate-packages-config-to-package-reference)

1. Tüm doğrudan derleme VS SDK'sı derleme başvurularını PackageReference öğeleriyle değiştirin.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > Birçok derleme *başvurularını* meta paketimize *yalnızca bir* PackageReference ile değiştirebilirsiniz:
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" Version="..." />
   >```

   Hedeflemekte olduğu en düşük sürümle Visual Studio emin olun.

   VS SDK'ya özgü olmayan bazı derlemeler (örneğin, Newtonsoft.Json.dll), Visual Studio 2022'den önce basit bir başvuru aracılığıyla keşfedilebilir, ancak `<Reference Include="Newtonsoft.Json" />` Visual Studio 2022'de Visual Studio 2022'de bazı Visual Studio çalışma zamanı ve SDK dizinlerini MSBuild'nin varsayılan derleme arama yolundan kaldırmamız nedeniyle paket başvurusu gerektirir.

   Doğrudan derleme başvurularından paket NuGet geçişte, bağımlılıkların geçişli kapanışı otomatik olarak yükleyerek NuGet ek derleme başvuruları ve çözümleyici paketleri topabilirsiniz. Bu genellikle normaldir, ancak derlemeniz sırasında ek uyarıların işaretlenmelerine neden olabilir. Bu uyarıların üzerinden geçerek mümkün olan en iyi şekilde çözüm bulun ve kod içinde bölgeleri kullanarak çözemeyebilirsiniz. `#pragma warning disable <id>`

## <a name="use-shared-projects-for-multi-targeting"></a>Birden çok hedefleme için paylaşılan projeleri kullanma

[Paylaşılan projeler,](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) 2015'te Visual Studio türler. Proje içinde paylaşılan Visual Studio, kaynak kod dosyalarının birden çok proje arasında paylaşılmalarına ve koşullu derleme sembolleri ve benzersiz başvuru kümeleri kullanılarak farklı şekilde derlenmesine olanak sağlar.

Visual Studio 2022 tüm önceki VS sürümlerinden ayrı bir başvuru derlemeleri kümesi gerektirdiğinden, kılavuzumuz uzantınızı 2022 öncesi ve Visual Studio Visual Studio 2022 (ve sonraki sürümler) için kolayca çoklu hedefleyeceksiniz; size kod paylaşımı, ancak ayrı başvurular vermek için paylaşılan projeleri kullanmaktır.

Visual Studio uzantıları bağlamında, Visual Studio 2022 ve sonrası için bir VSIX projeniz ve Visual Studio 2019 ve önceki sürümler için bir VSIX projeniz olabilir. Bu projelerin her biri yalnızca bir içerir ve paket `source.extension.vsixmanifest` 16.x SDK'sı veya 17.x SDK'sı başvurularını içerir. Bu VSIX projeleri, iki VS sürümü arasında paylaştırılacak tüm kaynak kodunuzu barındıracak yeni bir paylaşılan projeye yönelik paylaşılan proje başvurusuna da sahip olur.

Başlangıç noktası olarak, bu belge için zaten Visual Studio 2019'a yönelik bir VSIX projeniz olduğunu ve uzantının 2022'de Visual Studio varsayabilirsiniz.

Bu adımların hepsi 2019 Visual Studio tamamlanır.

1. Henüz bunu yapmadıysanız, bu [güncelleştirme işleminin sonraki adımlarını](#modernize-your-vsix-project) kolaylaştırmak için projelerinizi modernleştirin.

1. VS SDK'ya başvurulan mevcut her proje için çözümünüze yeni bir paylaşılan proje ekleyin.
   ![Yeni proje Project ](media/update-visual-studio-extension/add-new-project.png)
    ![ Yeni proje şablonu ekle](media/update-visual-studio-extension/new-shared-project-template.png)

1. Vs SDK'ya başvuran her projeden paylaşılan proje karşılıklarına bir başvuru ekleyin.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Paylaşılan proje başvurusu ekleme" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Tüm kaynak kodu (.cs, .resx dahil) vs SDK'ya başvuran her projeden paylaşılan proje karşılıklarına taşıma.
Dosyayı `source.extension.vsixmanifest` VSIX projesinde bırakın.
   ![Paylaşılan proje tüm kaynak dosyaları içeriyor](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Meta veri dosyaları (sürüm notları, lisans, simgeler ve diğer) ve VSCT dosyaları paylaşılan bir dizine taşınarak VSIX projesine bağlı dosyalar olarak eklenmiştir.
   ![Meta verileri ve VSCT dosyalarını bağlantılı dosyalar olarak ekleme](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - Meta veri dosyaları için BuildAction'i olarak `Content` ayarlayın ve VSIX'e dahil edin'i olarak `true` ayarlayın.

      ![VSIX'e meta veri dosyaları dahil edin](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - VSCT dosyaları için BuildAction olarak ayarlayın `VSCTCompile` ve VSIX'e dahil etmeyebilirsiniz.
      Visual Studio ayarın destek olmadığını şikayet ediyor olabilir, ancak projeyi kaldırıp olarak değiştirerek derleme eylemlerini el ile `Content` değiştirebilirsiniz`VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![VSCT dosyalarını VSCTCompile olarak ayarlama](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. Herhangi bir yeni hata oluşturmamanızı onaylamak için projelerinizi derleme.

Projeniz artık 2022 Visual Studio eklemeye hazırdır.

## <a name="add-a-visual-studio-2022-target"></a>2022 Visual Studio ekleme

Bu belgede, paylaşılan projelerde uzantınızı çarpanlara [Visual Studio adımlarını tamamlamış olduğunuz varsayılır.](#use-shared-projects-for-multi-targeting)

Uzantınıza Visual Studio 2022 desteği eklemeye devam edin. Bu adımlar 2019'da Visual Studio tamamlanabilirsiniz:

1. Çözümünüze yeni bir VSIX Project ekleyin. Bu, 2022'de Visual Studio projedir. Şablonla birlikte gelen tüm kaynak kodunu kaldırın, ancak *dosyasını olduğu gibi `source.extension.vsixmanifest` kaldırın.*

1. Yeni VSIX projeniz üzerinde, 2019'da hedeflenen VSIX başvurularını Visual Studio paylaşılan projeye bir paylaşılan proje başvurusu ekleyin.

   ![Bir paylaşılan projeye ve iki VSIX projesine sahip bir çözüm](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Yeni VSIX projesinin düzgün şekilde derlemesini doğrulayın. Derleyici hatalarını çözmek için özgün VSIX projeniz ile eşleşmesi için başvurular eklemeniz gerekir.

1. Yönetilen VS uzantıları için, NuGet Paket Yöneticisi kullanarak veya doğrudan proje dosyasını düzenleyerek paket başvurularınızı 16.x (veya önceki) sürümlerden Visual Studio 2022 hedefli proje dosyanız içinde 17.x paket sürümlerine güncelleştirin:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Bu sürümlerden gerçekten kullanılabilen sürümleri nuget.org. Daha önce kullanılanlar yalnızca tanıtım amaçlıdır.

   Çoğu durumda paket kimlikleri değişmiştir. 2022'de yapılan değişikliklerin listesi için [paket/derleme](migrated-assemblies.md) Visual Studio bakın.

   C++ ile yazılan uzantıların henüz derlen bir SDK'sı yoktur.

1. C++ projeleri için amd64 için derlenmiş olması gerekir. Yönetilen uzantılar için projenizi Herhangi bir CPU için yapıdan hedeflemeye değiştirmeyi göz önünde bulundurarak uzantınız her zaman 64 bitlik bir işlemde `x64` Visual Studio 2022'de yansıtın. `Any CPU` de sorun değil, ancak herhangi bir x64 yerel ikililerine başvurursanız uyarılar üretebilir.

   Uzantınıza yerel modülde sahip olunan tüm bağımlılıkların x86 görüntüsünden amd64 görüntüsüne güncelleştirilmiş olması gerekir.

1. Dosyanızı `source.extension.vsixmanifest` 2022'Visual Studio yansıtacak şekilde düzenleyin. Etiketi `<InstallationTarget>` 2022'Visual Studio yansıtacak şekilde ayarlayın ve amd64 yükünü işaret edin:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   Visual Studio 2019'da, bu dosyanın tasarımcısı yeni öğeyi açığa çıkarmaz, bu nedenle bu değişikliğin Çözüm Gezgini'daki Birlikte Aç komutuyla erişebilirsiniz bir xml düzenleyicisiyle `ProductArchitecture` **yapılması gerekir.** 

   Bu `ProductArchitecture` öğe kritiktir. Visual Studio 2022, *uzantınız* olmadan yüklenmez.

   | Öğe | Değer | Açıklama |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Bu VSIX tarafından desteklenen platformlar. Büyük/büyük/büyük harfe duyarlı değildir. Öğe başına bir platform ve InstallTarget başına bir öğe. 17.0'dan küçük ürün sürümleri için varsayılan değer x86'dır ve atlanabilir.  Ürün sürümleri 17.0 ve daha büyük için bu öğe gereklidir ve varsayılan değer yoktur. 2022 Visual Studio için bu öğe için tek geçerli içerik "amd64" şeklindedir. |

1. Source.extension.vsixmanifest içinde, 2019'un (varsa) hedefle Visual Studio diğer ayarlamaları da yapabilirsiniz. Her biri farklı bir VS sürümünü hedef alan uzantının 2 farklı sürümünü yayımlarsanız, bildirimin öğesinde VSIX kimliğinin her iki uzantı için de farklı olduğu `Identity` önemlidir.

Bu noktada, 2022 Visual Studio VSIX uzantınız vardır. 2022 Visual Studio VSIX projenizi derlemeniz ve görünen [derleme sonları üzerinde çalışmanız gerekir.](#handle-breaking-api-changes) Visual Studio 2022 hedefli VSIX projeniz için derleme sonları yoksa, tebrikler: Test etmeye hazırsın!

## <a name="handle-breaking-api-changes"></a>Api değişikliklerini bozmayı işleme

Visual Studio 2022'de, önceki sürümlerde çalışmalarından itibaren kodunuz üzerinde değişiklik gerektiren [hataya](breaking-api-list.md) neden olan API değişiklikleri vardır. Kodunuzu her biri için güncelleştirme ipuçları için bu belgeyi gözden geçirebilirsiniz.

Kodunuzu uyarlarken, kodunuzun [](#use-conditional-compilation-symbols) 2022 öncesi 2022 öncesi desteğine devam etmek için koşullu derlemeyi Visual Studio 2022'ye Visual Studio öneririz.

2022 hedefli uzantı Visual Studio için teste devam [edin.](#test-your-extension)

## <a name="use-conditional-compilation-symbols"></a>Koşullu derleme sembolleri kullanma

Visual Studio 2022 ve önceki sürümler için aynı kaynak kodu, hatta aynı dosyayı kullanmak isterseniz, hataya neden olan değişikliklere uyum sağlamak için kodunuzun bir hataya neden olması için koşullu derlemeyi kullanmanız gerekir. Koşullu derleme, C#, Visual Basic ve C++ dillerinin bir özelliğidir ve belirli yerlerde farklı API'leri bulundurarak çoğu kodu paylaşmak için kullanılabilir.

Ön işlemci yönergelerinin ve koşullu derleme sembollerinin kullanımı hakkında daha fazla bilgi, önişlemci yönergesi #if Microsoft [belgesinde bulunabilir.](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)

Daha önceki sürümleri hedef alan Visual Studio, daha sonra kodun farklı API'leri kullanmak üzere hataya neden olması için kullanılan bir koşullu derleme simgesine ihtiyaç olacaktır. Aşağıdaki görüntüde gösterildiği gibi, proje özellikleri sayfasında koşullu derleme simgesini ayarlayın:

![Koşullu derleme simgelerini ayarlama](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Varsayılan olarak, girersiniz sembolü *yalnızca* bir yapılandırma için geçerli olduğundan, tüm yapılandırmalar için derleme sembolünü ayardan emin olun.

### <a name="c-techniques"></a>C \# teknikleri

Daha sonra bu simgeyi aşağıdaki kodda gösterildiği gibi bir ön işlemci yönergesi ( `#if` ) olarak kullanabilirsiniz. Daha sonra farklı sürümler arasındaki hataya neden olan değişiklikle başa başa olmak için kodunuzun Visual Studio sabilirsiniz.

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

Söz dizimi kullanılırken, aşağıda gösterilen belgede dil hizmeti bağlam açılır listesinde söz dizimi vurgulamayı değiştirmek için nasıl kullanabileceğinizi ve diğer dil hizmetinin uzantımızın bir hedef Visual Studio sürümüne odaklanmaya odaklanması için sunduğu diğer yardımlara dikkat `#if` edin.

![Paylaşılan projede koşullu derleme](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>XAML paylaşım teknikleri

XAML'de, içeriği ön işlemci sembollerine göre özelleştirmeye olanak sağlayan bir ön işlemci yoktur. İçeriklerinin 2022 ve önceki sürümler arasında Visual Studio iki XAML sayfası kopyalayıp bakımının gerçek olması gerekebilir.

Ancak bazı durumlarda, Visual Studio 2022 ve önceki sürümler arasında ayrı derlemelerde var olan bir türe yapılan bir başvuru, derlemeye başvurulan ad alanı kaldırılarak bir XAML dosyasında yine de gösterilebilir:

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

Uzantınızı Visual Studio [Market'te yayımlamak,](https://marketplace.visualstudio.com/) yeni kullanıcıların uzantınızı bulup yüklemesi için harika bir yol sağlar. Uzantınız 2022'Visual Studio veya eski VS sürümlerini de hedeflese de Market sizi desteklemek için oradadır.

Gelecekte Market, tek bir Market listelemesine birden çok VSIX yüklemenizi sağlayarak Visual Studio 2022 hedefli VSIX'inizi ve 2022 öncesi VSIX Visual Studio karşıya yüklemenizi sağlar. Kullanıcılarınız, VS uzantısı yöneticisini kullanırken, yüklemiş olduğu VS sürümü için doğru VSIX'i otomatik olarak alır.

Visual Studio 2022'nin önizleme yayınlarında Market, Market başına yalnızca tek bir VSIX dosyasını destekleyecektir. 2022 Visual Studio önizlemede olduğu için uzantınız için ayrı bir Visual Studio 2022 Yalnızca Market listelemeniz gerekir. Böylece, 2022 Visual Studio 2022 uzantınızı, önceki sürümlerde müşterileriniz etkilenmeden Visual Studio. Ayrıca, güvenilirliğin kaynağı 2022'de olsa temel uzantınıza göre daha az güvenilir olacağını Visual Studio olarak da uzantıyı 'önizleme' olarak işaret görebilirsiniz.

### <a name="custom-installer"></a>Özel yükleyici

Uzantınızı yüklemek için bir MSI/EXE derlemeniz ve uzantınızı yüklemek vsixinstaller.exe (bir parçası) oluşturmak için bir MSI/EXE derlemeniz, Visual Studio 2022'deki VSIX yükleyicinin güncelleştirilmiş olduğunu bilirsiniz. Geliştiricilerin, Visual Studio 2022'ye uzantı yüklemek için Visual Studio 2022 ile birlikte gelen VSIX Visual Studio gerekir. Visual Studio 2022'deki VSIX yükleyicisi, aynı makinede Visual Studio 2022 ile yan yana yüklü olan önceki Visual Studio Visual Studio sürümlerini hedef alan geçerli uzantıları da yükleyecek.

### <a name="network-share"></a>Ağ paylaşımı

Uzantınızı LAN veya başka bir yolla paylaşabilirsiniz. Visual Studio 2022 ve önceki sürümler Visual Studio 2022'ye yönelikse, size tek tek birden çok VSIX paylaşmanız ve kullanıcılarınıza hangi VSIX'in yüklemiş olduğu sürümüne göre yüklenecekleri vsIX'i Visual Studio dosya adı (veya benzersiz klasörlere yer verme) gerekir.

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
