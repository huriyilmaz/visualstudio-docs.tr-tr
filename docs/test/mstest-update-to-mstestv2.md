---
title: MSTestV2'ye güncelleştirme
description: MSTestV1'den MSTestV2'ye güncelleştirmeyi öğrenin
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 5acdcce6616b931e2b0e867baaf8cee9ed845fab028fdad07866f2308e130c41
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315141"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>MSTestV1'den MSTestV2'ye yükseltme

*.csproj* dosyanıza başvurulan MSTest sürümünü MSTestV1'den MSTestV2'ye yeniden hedefleerek test projenizi yükseltebilirsiniz. MSTestV1'in tüm özellikleri MSTestV2'ye getirilemezse, hataları çözmek için bazı değişiklikler gerekebilir. Hangi [özelliklerin artık çalışmaymayacak olduğunu anlamak için bkz. MSTestV2'de](#mstestv1-features-that-are-not-supported-in-mstestv2) destek görmeyen MSTestV1 özellikleri. Bunlardan bazılarının testlerden kaldırılması gerekiyor olabilir.

1. Birim testi projenizin Microsoft.VisualStudio.QualityTools.UnitTestFramework derleme başvurularını kaldırın.
2. NuGet [MsTest.TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) ve nuget.org üzerinde [MSTest.TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) paketleri dahil olmak üzere MSTestV2'ye paket başvurularını nuget.org. NuGet Paket Yöneticisi Konsolu'NuGet Paket Yöneticisi aşağıdaki komutlarla paketleri yükleyebilirsiniz:

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Eski stil csproj örneği

MSTestV1'i hedef alan *örnek .csproj:*

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

MsTestV2'yi hedef alan *örnek .csproj:*

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> Kodlanmış UI testleri veya Web Yükü Testleri olan test projeleri MSTestV2 ile uyumlu değildir. Bu proje türleri kullanım dışıdır. Kodlanmış UI [Testi'nin kullanımdan nasıl kullanım dışı](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) bırakıldı ve [Web Yük Testi'nin kullanımdan nasıl kullanım dışı bırakıldı hakkında daha fazla bilgi edinebilirsiniz.](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)

### <a name="sdk-style-csproj-net-core-and-net-5"></a>SDK stili csproj (.NET Core ve .NET 5)

*.csproj'niz* daha yeni SDK stili *.csproj* ise büyük olasılıkla zaten MSTestV2'yi kullanıyorsanız. MSTestV2 ve [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) Bağdaştırıcısı için [](https://www.nuget.org/packages/MSTest.TestAdapter/) NuGet paketlerini NuGet.

Örnek:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>Neden MSTestV2'ye Yükseltin?

2016'da MSTestV2 ile MSTest çerçevesini geliştirmek için bir sonraki adımı yayınlamıştık. Bu değişiklik hakkında daha fazla bilgi için duyuru [blog gönderisini okuyabilirsiniz.](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/)

* MSTestV2 daha kolay elde edilir ve güncelleştirilir çünkü bir NuGet [paketi olarak teslim edilir.](https://www.nuget.org/packages/MSTest.TestFramework/)
* MSTestV2 açık [kaynaktır.](https://github.com/microsoft/testfx)
* Tekdüz uygulama platformu desteği – MSTestV2, .NET Framework, .NET Core, ASP.NET Core ve UWP genelinde tekdüz uygulama platformu desteği sunan yakınsandı bir uygulamadır. [Daha fazla bilgi için:](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* Uygulama tamamen platformlar arasıdır (Windows, Linux, Mac). [Daha fazla bilgi için:](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2, .NET Framework 4.5.0 ve sonraki, .NET Core 1.0 ve sonraki (Universal Windows Apps 10+), ASP.NET Core 1.0 ve sonraki ve sonraki bir 1.0 ve sonraki bir 1.
* Tekdüz, tek bir son kullanıcı genişletilebilirlik mekanizması sağlar. [Daha fazla bilgi için:](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* Tüm `DataRow` MSTest tabanlı test projeleri için tekdüz bir destek sağlar. [Daha fazla bilgi için:](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Özniteliğin `TestCategory` bir sınıf veya derleme düzeyine yerleştirilmesini sağlar. [Daha fazla bilgi için:](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Başka bir derlemede tanımlanan temel sınıflardan test yöntemleri artık keşfedildi ve türetilmiş Test sınıfından çalıştırıldı. Bu değişiklik türetilmiş test sınıfı türleriyle tutarlı bir davranış getirir. Uyumluluk nedeniyle bu davranış gerekli değilse, aşağıdaki çalıştırma ayarları kullanılarak yeniden değiştirilebilir:

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Testlerin derleme içinde paralel yürütülmesi yoluyla paralel yürütme [üzerinde daha ince denetim](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) sağlar. Bu, testleri bir derleme içinde paralel olarak çalıştırmayı sağlar.
* bir `TestCleanup` üzerinde `TestClass` yöntemi, karşılık gelen yöntemi başarısız olsa bile `TestInitialize` çağrılır. [Sorun ayrıntıları.](https://github.com/Microsoft/testfx/issues/250)
* ve tarafından alınan `AssemblyInitialize` `ClassInitialize` süre, test süresine göre sayılmaz. Bu değişiklik, test zamanlaması üzerindeki etkilerini sınırlar.
* Çalıştırılamaz olan testler, dosyada bağdaştırıcı düğümünün bir parçası olan etiket aracılığıyla başarısız olarak `MapNotRunnableToFailed` `.runsettings` işaretlenebilir.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>MSTestV2'de desteklenen MSTestV1 özellikleri

*   Testler "Sıralı Test" içine ek olamaz.
*   Bağdaştırıcı bir *.testsettings* dosyası aracılığıyla yapılandırılmayı desteklemez. Test çalıştırması [ *yapılandırması için yeni .runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) dosyasını kullanın.
*   Bağdaştırıcı, *.vsmdi* dosyası olarak belirtilen test listelerini desteklemez.
*   "Kodlanmış UI Test Project" ve "Web Performansı ve Yük Testi Project" türleri desteklenmiyor. Kodlanmış UI [Testi'nin kullanımdan nasıl kullanım dışı](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) bırakıldı ve [Web Yük Testi'nin kullanımdan nasıl kullanım dışı bırakıldı hakkında daha fazla bilgi edinebilirsiniz.](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalıştırmalarını ile yapılandırma `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Kodunuzu birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
