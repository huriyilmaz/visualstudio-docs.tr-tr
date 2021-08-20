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
ms.openlocfilehash: bf9d46dfab13f1aa2a412aeee27db7487370b931
ms.sourcegitcommit: 7c06c7e4f0a69d90b21dcf4d5c5b5caa17464bf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2021
ms.locfileid: "122464852"
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

1. Meta veri dosyaları (sürüm notları, lisans, simgeler vb.) ve VSCT dosyaları, paylaşılan bir dizine taşınmalı ve VSıX projesine bağlı dosyalar olarak eklenmelidir.
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

Visual Studio 2022 ' i hedefleyen bir uzantıyı test etmek için Visual Studio 2022 Preview ' in yüklü olması gerekir.
Visual Studio 2022 Preview ' dan önce Visual Studio sürümlerinde 64 bit uzantıları çalıştırameyeceksiniz.

Visual Studio 2022 veya daha önceki bir sürümü hedeflemenize bakılmaksızın uzantılarınızı derlemek ve test etmek için Visual Studio 2022 Preview ' i kullanabilirsiniz. Visual Studio 2022 ' dan bir vsıx projesi başlatırken Visual Studio deneysel bir örneği başlatılır.

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
