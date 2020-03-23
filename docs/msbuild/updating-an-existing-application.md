---
title: Varolan bir uygulamayı MSBuild 15'e güncelleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d4e7d84768307964b495e8c5e97e7731b0622a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597145"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>MSBuild 15 için varolan bir uygulamayı güncelleştirme

MSBuild'in 15.0'dan önceki sürümlerinde, MSBuild Global Assembly Önbelleğinden (GAC) yüklendi ve kayıt defterine MSBuild uzantıları yüklendi. Bu, tüm uygulamaların MSBuild'in aynı sürümünü kullanmasını ve aynı Araç Kümelerine erişmesini sağladı, ancak Visual Studio'nun farklı sürümlerinin yan yana kurulumlarını engelledi.

Daha hızlı, daha küçük ve yan yana kurulumu desteklemek için Visual Studio 2017 ve sonraki sürümler artık MSBuild'i GAC'ye yerleştirmez veya kayıt defterini değiştirir. Ne yazık ki, bu, projeleri değerlendirmek veya oluşturmak için MSBuild API'sını kullanmak isteyen uygulamaların Visual Studio yüklemesine dolaylı olarak güvenilemeyecekleri anlamına gelir.

## <a name="use-msbuild-from-visual-studio"></a>Visual Studio'dan MSBuild'i kullanma

Uygulama maç yapılarınızın Visual Studio veya *MSBuild.exe*içinde yapılmasını sağlamak için, Visual Studio'dan MSBuild montajları yükleyin ve Visual Studio'da bulunan SDK'ları kullanın. Microsoft.Build.Locator NuGet paketi bu işlemi kolaylaştırır.

## <a name="use-microsoftbuildlocator"></a>Microsoft.Build.Locatator'ı kullanma

*Microsoft.Build.Locator.dll'yi* uygulamanızla yeniden dağıtırsanız, diğer MSBuild derlemelerini dağıtmanız gerekmez.

MSBuild 15 ve yer bulucu API kullanmak için bir proje güncelleştirme, projenizde birkaç değişiklik gerektirir, aşağıda açıklanan. Bir projeyi güncelleştirmek için gereken değişikliklerin bir örneğini görmek için, [MSBuildLocator deposundaki örnek bir projeye yapılan taahhütlere](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15)bakın.

### <a name="change-msbuild-references"></a>MSBuild başvurularını değiştirme

MSBuild'in merkezi bir konumdan yük aldığından emin olmak için, derlemelerini uygulamanızla dağıtmamanız gerekir.

MSBuild'in merkezi bir konumdan yüklenmesinden kaçınmak için projenizi değiştirme mekanizması, MSBuild'e nasıl başvurulmaya bağlı.

#### <a name="use-nuget-packages-preferred"></a>NuGet paketlerini kullanın (tercih edilen)

Bu yönergeler, [PackageReference tarzı NuGet referanslarını](/nuget/consume-packages/package-references-in-project-files)kullandığınızı varsayar.

Proje dosyanızı(lar) NuGet paketlerinden MSBuild derlemelerine başvurmak için değiştirin. NuGet'e derlemelerin yalnızca oluşturma zamanında gerekli olduğunu ve çıktı dizinine kopyalanmaması gerektiğini belirtmek için belirtin. `ExcludeAssets=runtime`

MSBuild paketlerinin ana ve küçük sürümü, desteklemek istediğiniz Visual Studio'nun minimum sürümünden daha az veya eşit olmalıdır. Örneğin, Visual Studio 2017 ve sonraki sürümlerini desteklemek `15.1.548`istiyorsanız, başvuru paketi sürümü .

Örneğin, bu XML kullanabilirsiniz:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Uzantı derlemelerini kullanma

NuGet paketlerini kullanamıyorsanız, Visual Studio ile dağıtılan MSBuild derlemelerine başvuruda bulunabilirsiniz. MSBuild'e doğrudan başvurursanız, ''ye ayarlayarak `Copy Local` çıktı dizininize `False`kopyalanmaydığından emin olun. Proje dosyasında, bu ayar aşağıdaki kod gibi görünür:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Bağlama yönlendirmeleri

Uygulamanızın gerekli bağlama yönlendirmelerini otomatik olarak kullandığından emin olmak için Microsoft.Build.Locator paketine başvurun, sürüm 15.1.0.0'a yönlendirin. Bağlama bu sürüme yönlendirir hem MSBuild 15 hem de MSBuild 16'yı destekler.

### <a name="ensure-output-is-clean"></a>Çıktının temiz olduğundan emin olun

Projenizi oluşturun ve microsoft.build içermediğinden emin olmak için çıktı dizinini *inceleyin.\* * *microsoft.build.locator.dll*dışındaki dll derlemeleri, bir sonraki adımda eklendi.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Microsoft.Build.Locator için paket başvurusu ekleme

[Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/)için bir NuGet paketi başvurusu ekleyin.

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Microsoft.Build.Locator paketi için belirtmeyin. `ExcludeAssets=runtime`

### <a name="register-instance-before-calling-msbuild"></a>MSBuild'i aramadan önce örneği kaydet

MSBuild kullanan herhangi bir yöntemi çağırmadan önce Konumbelirleyici API'sine bir çağrı ekleyin.

Aramayı Konum belirleyici API'ye eklemenin en basit yolu,

```csharp
MSBuildLocator.RegisterDefaults();
```

uygulama başlangıç kodunuzda.

MSBuild yükleme üzerinde ince taneli kontrol istiyorsanız, `MSBuildLocator.QueryVisualStudioInstances()` `MSBuildLocator.RegisterInstance()` el ile geçmek için bir sonucu seçebilirsiniz, ancak bu genellikle gerekli değildir.
