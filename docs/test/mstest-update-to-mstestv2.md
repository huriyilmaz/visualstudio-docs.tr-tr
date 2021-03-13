---
title: MSTestV2 'ye Güncelleştir
description: MSTestV1 'den MSTestV2 'ye güncelleştirme hakkında bilgi edinin
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366260"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>MSTestV1 'den MSTestV2 'ye yükseltme

MSTestV1 to MSTestV2 ' den *. csproj* Içinde başvurulan MSTest sürümünü yeniden hedefleyerek test projenizi yükseltebilirsiniz. MSTestV1 'deki tüm özellikler MSTestV2 'e doğru bir şekilde getirilmediğinden, hataları çözmek için bazı değişiklikler yapılması gerekebilir. Artık hangi özelliklerin işlev görmemesi gerektiğini anlamak için [MSTestV2 'de desteklenmeyen MSTestV1 özelliklerine](#mstestv1-features-that-are-not-supported-in-mstestv2) bakın. Bunlardan bazılarının testlerinizin kaldırılması gerekebilir.

1. Birim testi projenizden Microsoft. VisualStudio. QualityTools. UnitTestFramework öğesine yönelik derleme başvurusunu kaldırın.
2. Nuget.org üzerinde [MSTest. TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) ve [MSTest. TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) paketleri de dahil olmak üzere MSTestV2 'e NuGet paket başvurularını ekleyin. Aşağıdaki komutları kullanarak, NuGet Paket Yöneticisi konsoluna paket yükleyebilirsiniz:

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Eski stil csproj örneği

MSTestV1 hedefleme örnek *. csproj* :

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

Sample *. csproj* artık MSTestV2 hedefleniyor:

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> Kodlanmış UI testleri veya Web yük testleri olan test projeleri, MSTestV2 ile uyumlu değildir. Bu proje türleri kullanım dışı bırakıldı. [KODLANMıŞ UI testi kullanımdan](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) kaldırma ve [Web yük testi](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)kullanım dışı bırakma hakkında daha fazla bilgi edinin.

### <a name="sdk-style-csproj-net-core-and-net-5"></a>SDK stili csproj (.NET Core ve .NET 5)

*. Csproj* 'niz daha yeni *SDK stili ise* , büyük olasılıkla zaten MSTestV2 kullanıyor olabilirsiniz. [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) ve [MSTestV2 bağdaştırıcısı](https://www.nuget.org/packages/MSTest.TestAdapter/) için NuGet paketlerini NuGet üzerinde bulabilirsiniz.

Örnek:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>Neden MSTestV2 sürümüne yükseltilir?

2016 ' de, MSTestV2 ile MSTest çerçevesini gelişen bir sonraki adımı yayımladık. Bu değişiklik hakkında daha fazla bilgi için duyuru [blog gönderisine](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/)erişebilirsiniz.

* MSTestV2, bir [NuGet paketi](https://www.nuget.org/packages/MSTest.TestFramework/)olarak teslim edildiği için daha kolay alınmış ve güncelleştirilmiş.
* MSTestV2 [açık kaynaktır](https://github.com/microsoft/testfx).
* Tekdüzen uygulama platformu desteği – MSTestV2, .NET Framework, .NET Core, ASP.NET Core ve UWP genelinde tek başına uygulama platformu desteği sunan yakınsama uygulamasıdır. [Daha fazla bilgi edinin](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* Uygulama, tam platformlar arası bir platformdur (Windows, Linux, Mac). [Daha fazla bilgi edinin](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2, .NET Framework 4.5.0 ve üzeri, .NET Core 1,0 ve üzeri (Evrensel Windows uygulamaları 10 +), ASP.NET Core 1,0 ve üzeri ve .NET 5 ve üzeri hedeflemeyi destekler.
* Tekdüzen, tek bir son kullanıcı genişletilebilirlik mekanizması sağlar. [Daha fazla bilgi edinin](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* `DataRow`Tüm MSTest tabanlı test projeleri için Tekdüzen desteği sağlar. [Daha fazla bilgi edinin](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* `TestCategory`Özniteliği bir sınıf veya derleme düzeyinde yerleştirmeyi sunar. [Daha fazla bilgi edinin](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Başka bir derlemede tanımlanan temel sınıflardan test yöntemleri artık türetilmiş test sınıfından keşfedilir ve çalıştırılır. Bu değişiklik, türetilmiş test sınıfı türleriyle tutarlı bir davranış gösterir. Bu davranış uyumluluk nedenleriyle gerekmiyorsa, aşağıdaki çalışma ayarları kullanılarak geri değiştirilebilir:

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Testlerin [derleme içi paralel yürütmesi](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) aracılığıyla paralel yürütme üzerinde daha ayrıntılı denetim sağlar. Bu, testlerin bir bütünleştirilmiş kod içinde paralel olarak çalıştırılmasına izin vermez.
* `TestCleanup`Bir üzerinde yöntemi `TestClass` karşılık gelen yöntemi başarısız olsa bile çağrılır `TestInitialize` . [Sorun ayrıntıları](https://github.com/Microsoft/testfx/issues/250).
* Tarafından geçen süre `AssemblyInitialize` ve `ClassInitialize` Test süresine doğru sayılmaz. Bu değişiklik, test zaman aşımına uğramasını kısıtlar.
* Çalıştırılabilir olmayan testler `MapNotRunnableToFailed` , dosyadaki bağdaştırıcı düğümünün bir parçası olan etiketi aracılığıyla başarısız olarak işaretlenecek şekilde yapılandırılabilir `.runsettings` .

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>MSTestV2 'de desteklenmeyen MSTestV1 özellikleri

*   Testler bir "sıralı teste" dahil edilemez.
*   Bağdaştırıcı bir *. testsettings* dosyası aracılığıyla yapılandırılmasını desteklemiyor. Test çalıştırması yapılandırması için yeni [ *. runsettings* dosyasını](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) kullanın.
*   Bağdaştırıcı, *. vsmdi* dosyası olarak belirtilen test listelerini desteklemiyor.
*   "Kodlanmış UI test projesi" ve "Web performansı ve yük testi projesi" türleri desteklenmez. [KODLANMıŞ UI testi kullanımdan](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) kaldırma ve [Web yük testi](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)kullanım dışı bırakma hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

- [İle test çalıştırmalarını yapılandırma `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
