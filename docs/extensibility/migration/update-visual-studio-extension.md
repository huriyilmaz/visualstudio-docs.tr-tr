---
title: Bir Visual Studio güncelleştirme
description: Visual Studio uzantınızı Visual Studio 2022'de çalışacak şekilde güncelleştirme hakkında bilgi.
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
ms.openlocfilehash: 71459535085cf8fef56cfdcb0bd01451e91edd87
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001201"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Visual Studio 2022 için Visual Studio uzantısını güncelleştirme

> [!IMPORTANT]
> Bu kılavuzda yer alan öneri, geliştiricilere hem 2019 hem de 2022'de büyük değişiklikler gerektiren uzantıların Visual Studio yöneliktir. Bu gibi durumlarda iki VSIX projesinin ve koşullu derlemenin kullanılması önerilir.
> Birçok uzantı hem Visual Studio 2019 hem de 2022'de bu kılavuzda uzantınızı modernleştirme önerisinde yer alan önerilerin ardından gerekli olmayacak küçük değişikliklerle birlikte çalışabilecektir.
> 2022'Visual Studio uzantınızı deneyin ve uzantınız için en uygun seçeneği değerlendirin.

Bu kılavuzu takip edin ve uzantınızı Visual Studio 2022 ile çalışacak şekilde güncelleştirin. Visual Studio 2022 bir 64 bit uygulamadır ve VS SDK'da bazı yeni değişikliklere neden olur. Bu kılavuz, uzantınızı Visual Studio 2022'nin geçerli önizlemesi ile birlikte çalışarak kullanıcıların Visual Studio 2022 GA'ya ulaşmadan önce yüklemelerine hazır hale Visual Studio adımlarda size yol sağlar.

## <a name="installing"></a>Yükleme

2022 Visual Studio 2022'den [yükleme Visual Studio 2022 indirmeleri.](https://visualstudio.microsoft.com/downloads)

### <a name="extensions-written-in-a-net-language"></a>.NET dilinde yazılmış uzantılar

Yönetilen uzantılar için Visual Studio 2022'ye yönelik VS SDK yalnızca *şu* NuGet:

- [Microsoft.VisualStudio.Sdk](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (17.x sürümleri) meta-paketi, ihtiyacınız olacak başvuru derlemelerinin çoğunu veya hepsini getirir.
- [Microsoft.VSSDK.BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (17.x sürümleri) paketine VSIX projenizin başvurarak 2022 uyumlu bir VSIX Visual Studio oluşturması gerekir.

Yeni değişikliklere başvursanız bile uzantıların  "Herhangi bir CPU" veya "x64" platformuyla derlenmiş olması gerekir. "x86" platformu, Visual Studio 2022'nin 64 bit işlemiyle uyumsuzdur.

### <a name="extensions-written-in-c"></a>C++ ile yazılmış uzantılar

C++ ile derlenmiş uzantılar için VS SDK her zamanki gibi Visual Studio SDK ile kullanılabilir.

Yeni değişikliklere başvursanız bile uzantılar  özellikle Visual Studio 2022 SDK'sı ve amd64 için derlenmiş olması gerekir.

### <a name="update-your-extension-to-visual-studio-2022"></a>Uzantınızı 2022'Visual Studio güncelleştirme

#### <a name="extensions-with-running-code"></a>Kod çalıştıran uzantılar

Çalışan koda sahip *uzantılar* özel olarak 2022'Visual Studio derlenmiş olması gerekir. Visual Studio 2022 özellikle 2022'ye yönelik Visual Studio yüklemez.

Visual Studio 2022 öncesi uzantılarınızı 2022'de Visual Studio öğrenin:

1. [Projelerinizi modernleştirin.](#modernize-your-vsix-project)
1. 2022 [ve daha eski sürümleri hedeflemek](#use-shared-projects-for-multi-targeting) için kaynak kodunuzu paylaşılan Visual Studio yeniden düzenleme.
1. [2022 Visual Studio VSIX](#add-a-visual-studio-2022-target)projesine ve paket/derleme yeniden kırpma [tablomuza bir ekleme.](migrated-assemblies.md)
1. [Gerekli kod ayarlamalarını yapma.](#handle-breaking-api-changes)
1. [2022 Visual Studio test etme.](#test-your-extension)
1. [Visual Studio 2022 uzantınızı yayımlama.](#publish-your-extension)

#### <a name="extensions-without-running-code"></a>Kod çalıştırmadan uzantılar

Çalışan kod (örneğin, proje/öğe şablonları) içeren uzantılar,  iki ayrı VSIX'in üretimi de dahil olmak üzere yukarıdaki adımları izlemesi gerekmez.

Bunun yerine, bir VSIX dosyasında aşağıdaki gibi iki yükleme `source.extension.vsixmanifest` hedefi bildirilecek şekilde değiştirilmelidir:

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
> Visual Studio 2022 kullanarak yeni bir Visual Studio uzantısı yazarsanız ve (ayrıca) Visual Studio 2019 veya önceki bir sürümü hedeflemek için bu kılavuzu [göz atabilirsiniz.](target-previous-versions.md) 

### <a name="msbuild-tasks"></a>MSBuild görevleri

MSBuild görevleri yazarsanız, Visual Studio 2022'de bunların 64 bitlik bir işlemde yüklenme olasılığı çok daha MSBuild.exe. Göreviniz için 32 bit işlem çalıştırmak gerekirse, MSBuild 32 bit bir işlemde yüklemesi MSBuild emin olmak için bu MSBuild belgelerine bakın. [](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters)

## <a name="modernize-your-vsix-project"></a>VSIX projenizi modernleştirme

Uzantınıza Visual Studio 2022 desteği eklemeden önce, devam etmek üzere devam etmek üzere mevcut projenizi temizlemek ve modernleştirmek için bu zamanı önemle öneririz:

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

   VS SDK'sı için benzersiz olmayan bazı derlemeler (örneğin, Newtonsoft.Json.dll), Visual Studio 2022'den önce basit bir başvuru aracılığıyla keşfedilebilir, ancak `<Reference Include="Newtonsoft.Json" />` Visual Studio 2022'de Visual Studio 2022'de bazı Visual Studio çalışma zamanı ve SDK dizinlerini MSBuild'nin varsayılan derleme arama yolundan kaldırmamız nedeniyle paket başvurusu gerektirir.

   Doğrudan derleme başvurularından paket NuGet geçişte, bağımlılıkların geçişli kapanışı otomatik olarak yükleyerek NuGet ek derleme başvuruları ve çözümleyici paketleri topabilirsiniz. Bu genellikle normaldir, ancak derlemeniz sırasında ek uyarıların işaretlenmelerine neden olabilir. Bu uyarıların üzerinden geçerek mümkün olan en iyi şekilde çözüm bulun ve kod içinde bölgeleri kullanarak çözemeyebilirsiniz. `#pragma warning disable <id>`

## <a name="use-shared-projects-for-multi-targeting"></a>Birden çok hedefleme için paylaşılan projeleri kullanma

[Paylaşılan projeler,](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) 2015'te Visual Studio türler. Proje içinde paylaşılan Visual Studio, kaynak kod dosyalarının birden çok proje arasında paylaşılmalarına ve koşullu derleme sembolleri ve benzersiz başvuru kümeleri kullanılarak farklı şekilde derlenmesine olanak sağlar.

Visual Studio 2022 önceki tüm VS sürümlerinden ayrı bir başvuru derlemeleri kümesi gerektirdiğinden, kılavuzumuz uzantınızı kolayca Visual Studio 2022 öncesi ve Visual Studio 2022 (ve sonraki sürümler) için çoklu hedef olarak kullanmak, size kod paylaşımı ve ayrı başvurular vermek için paylaşılan projeleri kullanmaktır.

Visual Studio uzantıları bağlamında, Visual Studio 2022 ve sonrası için bir VSIX projeniz ve Visual Studio 2019 ve önceki sürümler için bir VSIX projeniz olabilir. Bu projelerin her biri yalnızca bir içerir ve paket `source.extension.vsixmanifest` 16.x SDK'sı veya 17.x SDK'sı başvurularını içerir. Bu VSIX projeleri, iki VS sürümü arasında paylaştırılacak tüm kaynak kodunuzu barındıracak yeni bir paylaşılan projeye yönelik paylaşılan proje başvurusuna da sahip olur.

Başlangıç noktası olarak, bu belge için zaten Visual Studio 2019'a yönelik bir VSIX projeniz olduğunu ve uzantının 2022'de Visual Studio istediğiniz varsayabilirsiniz.

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

1. Meta veri dosyaları (sürüm notları, lisans, simgeler ve diğer) ve VSCT dosyaları paylaşılan bir dizine taşınarak VSIX projesine bağlı dosyalar olarak eklenmiştir. Paylaşılan dizinin paylaşılan projeden ayrı olduğunu unutmayın.
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

Bu belgede, paylaşılan projelerde uzantınızı çarpanlara Visual Studio [adımlarını tamamlamış olduğunuz varsayılır.](#use-shared-projects-for-multi-targeting)

Uzantınıza Visual Studio 2022 desteği eklemeye devam edin. Bu adımlar 2019'Visual Studio kullanılarak tamamlanabilirsiniz:

1. Çözümünüze yeni bir VSIX Project ekleyin. Bu, 2022'de Visual Studio projedir. Şablonla birlikte gelen tüm kaynak kodunu kaldırın, ancak *dosyasını olduğu gibi `source.extension.vsixmanifest` kaldırın.*

1. Yeni VSIX projeniz üzerinde, 2019'da hedeflenen VSIX başvurularını Visual Studio paylaşılan projeye bir paylaşılan proje başvurusu ekleyin.

   ![Bir paylaşılan projeye ve iki VSIX projesine sahip bir çözüm](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Yeni VSIX projesinin düzgün şekilde derlemesini doğrulayın. Derleyici hatalarını çözmek için özgün VSIX projeniz ile eşleşmesi için başvurular eklemeniz gerekir.

1. Yönetilen VS uzantıları için, NuGet Paket Yöneticisi kullanarak veya proje dosyasını doğrudan düzenleyerek, 16.x (veya önceki) paket başvurularınızı Visual Studio 2022 hedefli proje dosyanız içinde 17.x paket sürümlerine güncelleştirin:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Bu sürümlerden gerçekten kullanılabilen sürümleri nuget.org. Daha önce kullanılanlar yalnızca tanıtım amaçlıdır.

   Çoğu durumda paket kimlikleri değişmiştir. 2022'de yapılan değişikliklerin listesi için [paket/derleme](migrated-assemblies.md) Visual Studio bakın.

   C++ ile yazılan uzantıların henüz derlen bir SDK'sı yoktur.

1. C++ projeleri için amd64 için derlenmiş olması gerekir. Yönetilen uzantılar için projenizi Herhangi bir CPU için yapıdan hedeflemeye değiştirmeyi göz önünde Visual Studio 2022'de uzantınız her zaman `x64` 64 bitlik bir işlemde yüklenir. `Any CPU` de sorun değil, ancak herhangi bir x64 yerel ikilisi başvurursanız uyarılar üretebilir.

   Uzantınıza yerel modülde sahip olunan tüm bağımlılıkların x86 görüntüsünden amd64 görüntüsüne güncelleştirilmiş olması gerekir.

1. Dosyanızı `source.extension.vsixmanifest` 2022'Visual Studio yansıtacak şekilde düzenleyin. Etiketi `<InstallationTarget>` 2022'Visual Studio yansıtacak şekilde ayarlayın ve amd64 yükünü belirtin:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   Visual Studio 2019'da, bu dosyanın tasarımcısı yeni öğeyi açığa çıkarmaz, bu nedenle bu değişikliğin bir xml düzenleyicisiyle yapılması gerekir. Bu düzenleyiciye, Çözüm Gezgini'da Birlikte Aç `ProductArchitecture` **komutuyla erişebilirsiniz.** 

   Bu `ProductArchitecture` öğe kritiktir. Visual Studio *2022,* uzantınızı olmadan yüklemez.

   | Öğe | Değer | Açıklama |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Bu VSıX tarafından desteklenen platformlar. Büyük/küçük harfe duyarlı değildir. Her öğe için bir platform ve ınstalltarget başına bir öğe. 17,0 'den küçük ürün sürümleri için varsayılan değer x86 'dir ve atlanabilir.  Ürün sürümleri 17,0 ve üzeri için bu öğe gereklidir ve varsayılan değer yoktur. Visual Studio 2022 için bu öğenin yalnızca geçerli içeriği "amd64" olur. |

1. kaynak. extension. valtmanifest ' in Visual Studio 2019 ' i hedeflemesinden (varsa) eşleşmesini sağlamak için gereken diğer ayarlamaları yapın. Uzantınızın farklı bir sürümünü hedef alan 2 farklı sürümüne yayımlıyorsanız, her `Identity` iki uzantı için de VSıX kimliğinin, bildirimin öğesi için farklı olması önemlidir.

bu noktada, Visual Studio 2022 hedefli bir uzantı vsıx 'i vardır. Visual Studio 2022 hedefli vsıx projenizi oluşturmanız ve [görüntülenen tüm derleme sonlarına çalışmanız](#handle-breaking-api-changes)gerekir. Visual Studio 2022 hedefli vsıx projenizde derleme molaları yoksa tebrikler: test etmeye hazırsınız!

## <a name="handle-breaking-api-changes"></a>Son API değişikliklerini işle

Visual Studio 2022 ' de, önceki sürümlerde çalıştırıldığında kodunuzda değişiklik yapılmasını gerektirebilecek [son apı değişiklikleri](breaking-api-list.md) vardır. Kodunuzun her biri için nasıl güncelleştirecağıyla ilgili ipuçları için bu belgeyi gözden geçirin.

kodunuzu uyarlarken, kodunuzun Visual Studio 2022 desteğini eklerken Visual Studio 2022 ' yi desteklemeye devam edebilmesi için [koşullu derlemeyi](#use-conditional-compilation-symbols) kullanmanızı öneririz.

Visual Studio 2022 hedefli uzantı oluşturmayı aldığınızda, [teste](#test-your-extension)devam edin.

## <a name="use-conditional-compilation-symbols"></a>Koşullu derleme sembolleri kullan

aynı kaynak kodunu, hatta aynı dosyayı bile kullanmak istiyorsanız, Visual Studio 2022 ve önceki sürümler için, koşullu derleme kullanmanız gerekebilir. böylece, büyük değişikliklere uyum sağlamak için kodunuzu çatallayabilmenizi sağlayabilirsiniz. koşullu derleme, bir C#, Visual Basic ve C++ dillerinin belirli yerlerde bir bütün olarak apı 'leri konairken birçok kodu paylaşmak için kullanılabilen bir özelliğidir.

Önişlemci yönergelerinin kullanımı ve koşullu derleme sembolleri hakkında daha fazla bilgi Microsoft docs [#if Önişlemci yönergesinde](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)bulunabilir.

daha önce Visual Studio sürümleri hedefleyen projeniz, kodun farklı apı 'leri kullanmak üzere çatalları için kullanılabilecek bir koşullu derleme simgesine sahip olmalıdır. Aşağıdaki görüntüde gösterildiği gibi, proje özellikleri sayfasında koşullu derleme sembolünü ayarlayabilirsiniz:

![Koşullu derleme sembolleri ayarlanıyor](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Varsayılan olarak girdiğiniz sembol yalnızca bir yapılandırmaya uygulanabilir olduğundan, *Tüm* yapılandırmalar için derleme sembolünü ayarladığınızdan emin olun.

### <a name="c-techniques"></a>C \# teknikleri

Daha sonra, `#if` aşağıdaki kodda gösterildiği gibi bu simgeyi bir ön işlemci yönergesi () olarak kullanabilirsiniz. daha sonra, farklı Visual Studio sürümleri arasındaki son değişikliği yapmak için kodunuzun çatalını oluşturabilirsiniz.

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

Bazı durumlarda, `var` türü adlandırmaktan kaçınmak için kullanabilirsiniz, böylece bölgeler gereksinimini ortadan kaldırabilirsiniz `#if` . Yukarıdaki kod parçacığı aynı zamanda şöyle yazılabilir:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

`#if`söz dizimini kullanırken, söz dizimi vurgulamasını ve diğer yardım 'ın uzantısı için bir hedef Visual Studio sürümü ile ilgili olarak dikkat çekmek üzere, sözdizimi vurgulamayı değiştirmek için aşağıda gösterilen belgede dil hizmeti bağlam açılan listesini nasıl kullanabileceğinizi fark edin.

![Paylaşılan bir projede koşullu derleme](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>XAML paylaşım teknikleri

XAML, Önişlemci sembollerine göre içerik özelleştirmeye izin veren bir ön işlemci içermez. Visual Studio 2022 ve önceki sürümler arasında farklı olması gereken iki XAML sayfasının kopyalanması ve saklanması gerekebilir.

ancak bazı durumlarda, Visual Studio 2022 ve önceki sürümlerde ayrı derlemelerde bulunan bir türe başvuru, derlemeye başvuran ad alanını kaldırarak bir XAML dosyasında yine de gösterilebilir.

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Uzantınızı test etme

Visual Studio 2022 ' i hedefleyen bir uzantıyı test etmek için, Visual Studio 2022 ' nin yüklü olması gerekir.
Visual Studio 2022 ' den önceki Visual Studio sürümlerinde 64 bit uzantıları çalıştırameyeceksiniz.

Visual Studio 2022 veya daha önceki bir sürümü hedeflemenize bakılmaksızın uzantılarınızı derlemek ve test etmek için Visual Studio 2022 kullanabilirsiniz. Visual Studio 2022 ' dan bir vsıx projesi başlatırken Visual Studio deneysel bir örneği başlatılır.

uzantıyı desteklemek istediğiniz Visual Studio her sürümü ile test etmenizi kesinlikle öneririz.

Şimdi [uzantınızı yayımlamaya](#publish-your-extension)hazırsınız.

## <a name="publish-your-extension"></a>Uzantınızı yayımlayın

harika, bu nedenle uzantınızın Visual Studio 2022 hedefini eklediniz ve test edildi. Şimdi de dünyanın uzantısını admıire 'e yayımlamaya hazırsınız.

### <a name="visual-studio-marketplace"></a>Visual Studio Market

uzantınızı [Visual Studio market](https://marketplace.visualstudio.com/) 'e yayımlamak, yeni kullanıcıların uzantınızı bulmasını ve yüklemesini sağlamak için harika bir yoldur. uzantınızın 2022 Visual Studio özel olarak hedeflemesini veya eski VS sürümlerini hedeflemesini ister. market, sizin için destek sağlar.

daha sonra market, tek bir market listesine birden çok vsixs yükleyerek Visual Studio 2022 hedefli vsıx ve bir Visual Studio öncesi 2022 vsıx 'i yüklemenizi sağlar. Kullanıcılarınız, VS uzantısı Yöneticisi kullanılırken, yüklemiş oldukları VS sürümü için doğru VSıX 'i otomatik olarak alır.

Visual Studio 2022 ' nin önizleme sürümleri için market, market listeleme başına yalnızca tek bir vsıx dosyasını destekleyecektir. Visual Studio 2022 önizlemedeyken, uzantınızın ayrı bir Visual Studio 2022 yalnızca market listesine sahip olmasını öneririz. bu şekilde, Visual Studio daha önceki sürümlerinde müşterilerinizi etkilemeden Visual Studio 2022 uzantınızı gerektiği şekilde yineleyebilirsiniz. ayrıca, söz konusu ungüvenilirliğin kaynağı temel uzantıınıza göre 2022 Visual Studio olsa da, beklenenleri ayarlamak için uzantıyı ' önizleme ' olarak işaretleyebilirsiniz.

### <a name="custom-installer"></a>Özel yükleyici

uzantınızı yüklemek için bir msı/EXE oluşturursanız ve uzantınızı yüklemek için vsixinstaller.exe oluşturun, Visual Studio 2022 ' deki vsıx yükleyicisinin güncelleştirildiğinden emin olmalısınız. geliştiricilerin, uzantıları Visual Studio 2022 ' ye yüklemek için Visual Studio 2022 ile birlikte gelen vsıx yükleyicisi sürümünü kullanması gerekir. Visual Studio 2022 ' deki vsıx yükleyicisi aynı makinede Visual Studio 2022 ile yan yana yüklenen önceki Visual Studio sürümlerini hedefleyen geçerli uzantıları da yükler.

### <a name="network-share"></a>Ağ paylaşma

Uzantınızı bir LAN veya başka bir şekilde paylaşabilirsiniz. Visual Studio 2022 ve önceden Visual Studio 2022 ' i hedefliyorsanız, kullanıcılarınızın yüklemiş olduğu Visual Studio sürümüne bağlı olarak hangi vsıx 'in yükleneceğini bilmesini sağlamak için, birden çok vnet 'i tek tek paylaşmanız ve dosya adlarını (veya benzersiz klasörlere yerleştirmeniz) gerekir.

### <a name="other-considerations"></a>Diğer önemli noktalar

#### <a name="dependencies"></a>Bağımlılıklar

VSıX, öğe aracılığıyla başka bir VSıX belirtirse `<dependency>` , başvurulan her VSıX VSIX ile aynı hedeflere ve ürün mimarilerine yüklenmesi gerekir. bağımlı bir vsıx Visual Studio hedeflenen yüklemesini desteklemiyorsa vsıx başarısız olur. Bağımlı VSıX 'in sizinkinden daha fazla hedefe göre daha fazla hedef ve mimariyi desteklemesi, ancak daha az olmaması yeterlidir. Bu kısıtlama, bir VSıX 'in bağımlılıklarla dağıtım ve dağıtım yaklaşımının, bağımlılarını yansıtmasının gerektiği anlamına gelir.

## <a name="q--a"></a>Soru-Cevap

**s**: uzantım yalnızca veri (örneğin, şablonlar) sağladığından hiçbir birlikte çalışma değişikliği gerektirmiyor, Visual Studio 2022 de içeren tek bir uzantı oluşturabilir miyim?

Y **: Evet**!  Bunun hakkında daha fazla bilgi için [kodu çalıştırmadan](#extensions-without-running-code) bkz. uzantıları.

**s**: bir NuGet bağımlılığı eski birlikte çalışma derlemelerini getirme ve çakışan sınıflara neden oluyor.

Y **: yinelenen** derlemeleri önlemek için. csproj dosyanıza aşağıdaki satırı ekleyin:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

Bu, paket başvurularının derlemenin eski sürümünün diğer bağımlılıklardan içeri aktarılmasını engeller.

**s**: kaynak dosyalarımı paylaşılan bir projeye geçirdikten sonra komutlarım ve kısayol tuşları Visual Studio çalışmıyor.

Y **: görüntü** iyileştirici örneği için [Adım 2,4](samples.md#step-2---refactor-source-code-into-a-shared-project) , vsct dosyalarını vsct dosyanıza derlenmek üzere bağlantılı öğeler olarak nasıl ekleneceğini gösterir.

## <a name="next-steps"></a>Sonraki adımlar

Bir adım adım örneği, [ımageiyileştiriciyi](samples.md), projenin bağlantılarıyla ve her bir adımla ilgili kod değişikliklerinden izleyin.
