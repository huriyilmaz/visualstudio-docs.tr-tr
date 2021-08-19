---
title: Mevcut bir uygulamayı 15 MSBuild güncelleştirme| Microsoft Docs
description: Uygulamanıza bağlı program aracılığıyla derlemelerin uygulama veya uygulama içinde yapılan derlemeler ile eş Visual Studio emin MSBuild.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 53fa2e2631bff2eb3fd9438a97f190b9766a1407
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142578"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>MSBuild 15 için mevcut bir uygulamayı güncelleştirme

MSBuild 15.0'dan önceki sürümlerinde, MSBuild Genel Derleme Önbelleği'nde (GAC) yüklendi ve MSBuild uzantıları kayıt defterine yüklendi. Bu, tüm uygulamaların aynı MSBuild sürümünü kullandığı ve aynı Araç Kümeleri'ne erişimi olduğundan emin oldu, ancak farklı sürümlerinin yan yana yüklemelerini Visual Studio.

Daha hızlı, daha küçük ve yan yana yüklemeyi desteklemek için Visual Studio 2017 ve sonraki sürümler artık GAC'MSBuild veya kayıt defterinin yerini alamaz. Ne yazık ki bu durum, MSBuild API'sini kullanarak projeleri değerlendirmek veya derlemek isteyen uygulamaların yükleme işlemini örtülü olarak Visual Studio anlamına gelir.

## <a name="use-msbuild-from-visual-studio"></a>MSBuild'den Visual Studio

Uygulamanıza yönelik programlı derlemelerin Visual Studio veya *MSBuild.exe* içinde yapılan derlemeler ile eşleştir olduğundan emin olmak için, Visual Studio'den MSBuild derlemelerini yük Visual Studio. Microsoft.Build.Locator NuGet paketi bu işlemi kolaylaştırıyor.

## <a name="use-microsoftbuildlocator"></a>Microsoft.Build.Locator kullanma

Uygulamanıza yenidenMicrosoft.Build.Locator.dll *dağıtırsanız,* diğer dağıtım derlemelerini dağıtmanız MSBuild gerekir.

Bir projeyi MSBuild 15 ve bulucu API'sini kullanmak için güncelleştirmek için projeniz üzerinde aşağıda açıklanan birkaç değişiklik gerekir. Projeyi güncelleştirmek için gereken değişikliklerin bir örneğini görmek için [MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15)deposundaki örnek projeye yapılan işlemelere bakın.

### <a name="change-msbuild-references"></a>Veri MSBuild değiştirme

Merkezi bir konumdan MSBuild emin olmak için derlemelerini uygulamanıza dağıtmanız gerekir.

Projenizi merkezi bir konumdan MSBuild şekilde değiştirme mekanizması, projenize nasıl başvurdu MSBuild.

#### <a name="use-nuget-packages-preferred"></a>NuGet paketlerini kullanma (tercih edilen)

Bu yönergelerde [PackageReference stilinde başvurular için NuGet varsayabilirsiniz.](/nuget/consume-packages/package-references-in-project-files)

Proje dosyalarınızı, kendi derleme paketlerinden MSBuild için proje NuGet değiştirme. Derlemelere NuGet derlemelerin yalnızca derleme zamanında gerektiğini ve çıkış dizinine kopyalanmaması `ExcludeAssets=runtime` gerektiğini belirtmek için belirtin.

MSBuild paketlerinin ana ve ikincil sürümü, desteklemek istediğiniz en düşük sürümden Visual Studio veya bu sürüme eşit olmalı. Örneğin, 2017 ve Visual Studio sürümlerini desteklemek isterseniz, paket sürümüne `15.1.548` başvurun.

Örneğin, bu XML'yi kullanabilirsiniz:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Uzantı derlemelerini kullanma

Uygulama paketlerini kullana NuGet, MSBuild dağıtılmış derlemelere Visual Studio. Doğrudan bir MSBuild başvurursanız, ayarına göre çıkış dizininize kopyalanmay olduğundan emin `Copy Local` `False` olun. Proje dosyasında bu ayar aşağıdaki koda benzer:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Bağlama yeniden yönlendirmeleri

Microsoft.Build.Locator paketine başvurarak, uygulamanın gerekli bağlama yönlendirmelerini otomatik olarak 15.1.0.0 sürümüne yeniden yönlendirmesini kullandığına emin olun. Bu sürüme yapılan bağlama yönlendirmeleri hem MSBuild 15 hem de 16 MSBuild destekler.

### <a name="ensure-output-is-clean"></a>Çıkışın temiz olduğundan emin olmak

Projenizi derleme ve çıkış dizinini inceler ve bir sonraki adımda eklenenMicrosoft.Build.Locator.dlldışında ** *microsoft.Build. \*.dll* derlemeleri içermemesini sağlar.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Microsoft.Build.Locator için paket başvurusu ekleme

[Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/)için bir NuGet paketi başvurusu ekleyin.

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

`ExcludeAssets=runtime`Microsoft.Build.Locator paketi için belirtme.

### <a name="register-instance-before-calling-msbuild"></a>MSBuild çağırmadan önce örneği MSBuild

> [!IMPORTANT]
> MSBuildLocator MSBuild yönteminde herhangi bir tür türüne (ad `Microsoft.Build` alanından) başvuramazsınız. Örneğin, bunu olamaz:
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
> Bunun yerine, bunu yapmak gerekir:
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

Bulucu API'sini çağırmanın en basit yolu çağrısı eklemektir

```csharp
MSBuildLocator.RegisterDefaults();
```

uygulama başlatma kodunda.

Veri yüklemesi üzerinde daha ince denetim MSBuild, öğesinin el ile geçiş için bir sonucu seçebilirsiniz, ancak bu `MSBuildLocator.QueryVisualStudioInstances()` `MSBuildLocator.RegisterInstance()` genellikle gerekli değildir.
