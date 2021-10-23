---
title: mevcut bir uygulama MSBuild 15 ' e güncelleştiriliyor | Microsoft Docs
description: uygulamanızın Visual Studio veya MSBuild.exe içinde yapılan yapı derlemeleriyle ilgili programsal yapıların nasıl yapıldığını nasıl sağlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2b804bccce4bea0345cac86d269e8fbcb14eb777
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130211954"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>MSBuild 15 için mevcut bir uygulamayı güncelleştirme

15,0 ' dan önceki MSBuild sürümlerinde, MSBuild genel derleme önbelleğinden (GAC) yüklendi ve MSBuild uzantıları kayıt defterine yüklendi. bu, tüm uygulamaların aynı MSBuild sürümünü kullandı ve aynı araç kümelerine erişimi vardı, ancak farklı Visual Studio sürümlerinin yan yana yüklemelerini engelledi.

daha hızlı, daha küçük ve yan yana yüklemeyi desteklemek için Visual Studio 2017 ve üzeri sürümler artık GAC 'ye MSBuild ve kayıt defterini değiştirir. ne yazık ki bu, projeleri değerlendirmek veya oluşturmak için MSBuild apı 'sini kullanmak isteyen uygulamaların, Visual Studio yüklemeye örtük olarak dayanmadığını gösterir.

## <a name="use-msbuild-from-visual-studio"></a>Visual Studio MSBuild kullanın

uygulamanızdaki programsal yapıların Visual Studio veya *MSBuild.exe* içinde yapılan yapılardan eşleştiğinden emin olmak için, Visual Studio MSBuild derlemeleri yükleyin ve Visual Studio bulunan sdk 'leri kullanın. Microsoft. Build. Locator NuGet paketi bu işlemi basitleştirir. MSBuild, belirli derlemeler (microsoft. build derlemeleri) için bağlama yeniden yönlendirmeleri gerektirir, ancak Microsoft. Build. Locator paketine başvurdıysanız, uygulamanızın 15.1.0.0 sürümüne gereken bağlama yeniden yönlendirmelerini otomatik olarak kullanmasını sağlayabilirsiniz. bu sürüm MSBuild 15. x, 16. x ve 17. x sürümüne yeniden yönlendirmeleri bağlama.

## <a name="use-microsoftbuildlocator"></a>Microsoft. Build. Locator kullanın

*Microsoft.Build.Locator.dll* uygulamanızla birlikte yeniden dağıtırsanız, diğer MSBuild derlemelerini dağıtmanız gerekmez.

projeyi 15 MSBuild kullanmak üzere güncelleştirmek ve konumlandırıcı apı 'si, projenizde aşağıda açıklanan birkaç değişiklik yapılmasını gerektirir. Bir projeyi güncelleştirmek için gereken değişikliklere bir örnek görmek için bkz. [MSBuildLocator deposundaki örnek bir projeye yapılan işlemeler](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>MSBuild başvurularını değiştirme

MSBuild merkezi bir konumdan yüklendiğinden emin olmak için derlemelerini uygulamanızla dağıtmamalıdır.

projenizi, merkezi bir konumdan MSBuild yüklemeden kaçınmak üzere değiştirme mekanizması MSBuild nasıl başvurdığınıza bağlıdır.

#### <a name="use-nuget-packages-preferred"></a>NuGet paketlerini kullanma (tercih edilen)

bu yönergelerde, [packagereference stili NuGet başvurularını](/nuget/consume-packages/package-references-in-project-files)kullandığınızı varsayalım.

proje dosyanızı, NuGet paketlerinden MSBuild derlemelere başvuracak şekilde değiştirin. `ExcludeAssets=runtime`derlemelerin yalnızca derleme zamanında gerekli olduğunu ve çıkış dizinine kopyalanmayacağını NuGet söyleyeceğinizi belirtin.

MSBuild paketlerin büyük ve küçük sürümü, desteklemek istediğiniz en düşük Visual Studio sürümüne eşit veya ondan daha az olmalıdır. örneğin, Visual Studio 2017 ve sonraki sürümleri desteklemek istiyorsanız, paket sürümüne başvurun `15.1.548` .

Örneğin, bu XML 'yi kullanabilirsiniz:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Uzantı derlemelerini kullanma

NuGet paketlerini kullanamıyoruz Visual Studio ile dağıtılan MSBuild derlemelerine başvurabilirsiniz. MSBuild doğrudan başvuru yaparsanız, ' ye ayarlayarak çıkış dizininize kopyalanmadığından emin olun `Copy Local` `False` . Proje dosyasında, bu ayar aşağıdaki kodla aynı şekilde görünür:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Bağlama yeniden yönlendirmeleri

Uygulamanızın 15.1.0.0 sürümüne gereken bağlama yeniden yönlendirmelerini otomatik olarak kullandığından emin olmak için Microsoft. Build. Locator paketine başvurun. hem MSBuild 15 hem de 16 MSBuild, bu sürüm için yeniden yönlendirmeleri bağlamayı destekler.

### <a name="ensure-output-is-clean"></a>Çıktının temiz olduğundan emin olun

Bir sonraki adımda eklenen *Microsoft.Build.Locator.dll* dışında herhangi bir *Microsoft. Build. \*.dll* derlemesi içermediğinden emin olmak için projenizi derleyin ve çıkış dizinini inceleyin.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Microsoft. Build. Locator için paket başvurusu Ekle

[Microsoft. Build. Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/)için NuGet paketi başvurusu ekleyin.

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

`ExcludeAssets=runtime`Microsoft. Build. Locator paketi için belirtmeyin.

### <a name="register-instance-before-calling-msbuild"></a>MSBuild çağrılmadan önce örneği Kaydet

> [!IMPORTANT]
> `Microsoft.Build`msbuildlocator öğesini çağıran yöntemdeki MSBuild türlerine (ad alanından) başvuramaz. Örneğin, bunu yapabilirsiniz:
>
> ```csharp
> void ThisWillFail()
> {
>     MSBuildLocator.RegisterDefaults();
>     Project p = new Project(SomePath); // Could be any MSBuild type
>     // Code that uses the MSBuild type
> }
> ```
>
> Bunun yerine şunu yapmanız gerekir:
>
> ```csharp
> void MethodThatDoesNotDirectlyCallMSBuild()
> {
>     MSBuildLocator.RegisterDefaults();
>     MethodThatCallsMSBuild();
> }
> 
> void MethodThatCallsMSBuild()
> {
>     Project p = new Project(SomePath);
>     // Code that uses the MSBuild type
> }
> ```

Konumlandırıcı API 'sine çağrı eklemenin en kolay yolu,

```csharp
MSBuildLocator.RegisterDefaults();
```

uygulamanızın başlangıç kodunda.

MSBuild yüklemesi üzerinde daha ayrıntılı denetim isterseniz, `MSBuildLocator.QueryVisualStudioInstances()` el ile geçirilecek bir sonuç seçebilirsiniz `MSBuildLocator.RegisterInstance()` , ancak bu genellikle gerekli değildir.
