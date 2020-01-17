---
title: Visual Studio derleme araçları bir kapsayıcıya yükleme
titleSuffix: ''
description: Visual Studio derleme araçları, sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını destekleyen bir Windows kapsayıcısına yüklemeyi öğrenin.
ms.date: 07/03/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 53049d37f23a72adb337cdad629f4c689c83707e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114613"
---
# <a name="install-build-tools-into-a-container"></a>Derleme araçları bir kapsayıcıya yükleme

Visual Studio derleme araçları, sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını destekleyen bir Windows kapsayıcısına yükleyebilirsiniz. Bu makalede hangi Docker yapılandırma değişikliklerini ne yanı sıra gerekli aracılığıyla kılavuzları [iş yüklerinin ve bileşenlerin](workload-component-id-vs-build-tools.md) bir kapsayıcıda yükleyebilirsiniz.

[Kapsayıcıları](https://www.docker.com/what-container) yalnızca bir CI/CD sunucu ortamında, ancak geliştirme ortamları için kullanabileceğiniz bir tutarlı yapı sistemi paketlemek için harika bir yoludur. Örneğin, kaynak kodunuzu kodunuzu yazmak için Visual Studio veya diğer araçları kullanmaya devam ederken, özelleştirilmiş bir ortamı tarafından oluşturulacak bir kapsayıcıya bağlayabilir. CI/CD akışınızı aynı kapsayıcı görüntüsü kullanıyorsa, tutarlı bir şekilde, kodunuzun derlendiğinden güvenli yaslayabilirsiniz. Kapsayıcıları, birden çok kapsayıcı bir düzenleme sistemi ile kullanarak mikro hizmetler için ortak olan çalışma zamanı tutarlılık için de kullanabilirsiniz; Ancak, bu makalenin kapsamı dışındadır olur.

Visual Studio derleme araçları, kaynak kodunuzu derlemek için ihtiyacınız yoksa, aynı adımları diğer Visual Studio ürünleri için kullanılabilir. Ancak, komutların otomatik şekilde Windows kapsayıcıları etkileşimli bir kullanıcı arabirimi desteklemediğini unutmayın.

## <a name="before-you-begin"></a>Başlamadan önce

[Docker](https://www.docker.com/what-docker) ile ilgili bazı benzerlik aşağıdaki gibi kabul edilir. Windows üzerinde Docker çalıştıran bir bilginiz yoksa, [Windows 'Da Docker motorunu yüklemek ve yapılandırmak](/virtualization/windowscontainers/manage-docker/configure-docker-daemon)hakkında bilgi edinin.

Aşağıdaki temel görüntü bir örnektir ve sisteminiz için çalışmayabilir. Ortamınız için hangi temel görüntünün kullanılması gerektiğini öğrenmek için [Windows kapsayıcı sürümü uyumluluğunu](/virtualization/windowscontainers/deploy-containers/version-compatibility) okuyun.

## <a name="create-and-build-the-dockerfile"></a>Oluşturma ve Dockerfile'ı oluşturma

Aşağıdaki örnek Dockerfile, disk üzerinde yeni bir dosyaya kaydedin. Dosya yalnızca "Dockerfile" ise, varsayılan olarak kabul edilir.

> [!WARNING]
> Bu örnek Dockerfile yalnızca kapsayıcılara yüklenebilen önceki Windows SDK 'larını dışlar. Önceki sürümler derleme komutunun başarısız olmasına neden olur.

1. Bir komut istemi açın.

1. (Önerilen) yeni bir dizin oluşturun:

   ```shell
   mkdir C:\BuildTools
   ```

1. Bu yeni dizine dizinleri değiştirin:

   ```shell
   cd C:\BuildTools
   ```

1. Aşağıdaki içeriğe C:\BuildTools\Dockerfile için kaydedin.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Görüntünüzü doğrudan Microsoft/windowsservercore veya mcr.microsoft.com/windows/servercore (bkz. [Microsoft Syndicates Container Catalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)) üzerine temellendiriyor, .NET Framework düzgün şekilde yüklenemeyebilir ve hiçbir yüklemesi hatası belirtilmez. Yönetilen kod, yüklemesi tamamlandıktan sonra çalışmayabilir. Bunun yerine, görüntünüzü [Microsoft/DotNet-Framework: 4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) veya üzeri bir sürüme dayandırın. Ayrıca, 4.7.2 veya üzeri etiketli görüntülerin PowerShell 'i varsayılan `SHELL`olarak kullanabileceğini unutmayın; bu, `RUN` ve `ENTRYPOINT` yönergelerinin başarısız olmasına neden olur.
   >
   > Visual Studio 2017 sürüm 15,8 veya önceki sürümleri (herhangi bir ürün) mcr.microsoft.com/windows/servercore:1809 veya sonraki bir sürüme düzgün şekilde yüklemez. Bir hata görüntülenmiyor.
   >
   > Hangi kapsayıcı işletim SISTEMI sürümlerinin hangi işletim sistemi sürümlerinde desteklendiğini ve bilinen sorunların [kapsayıcılarına yönelik bilinen sorunları](build-tools-container-issues.md) görmek için bkz. [Windows kapsayıcı sürümü uyumluluğu](/virtualization/windowscontainers/deploy-containers/version-compatibility) .

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Görüntünüzü doğrudan Microsoft/windowsservercore 'a dayandırırsanız .NET Framework düzgün şekilde yüklenemeyebilir ve hiçbir yüklemesi hatası belirtilmez. Yönetilen kod, yüklemesi tamamlandıktan sonra çalışmayabilir. Bunun yerine, görüntünüzü [Microsoft/DotNet-Framework: 4.8](https://hub.docker.com/r/microsoft/dotnet-framework) veya üzeri bir sürüme dayandırın. Ayrıca, 4,8 veya üzeri etiketli resimlerin, `RUN` ve `ENTRYPOINT` yönergelerinin başarısız olmasına neden olacak varsayılan `SHELL`PowerShell 'i kullanabileceğini de unutmayın.
   >
   > Hangi kapsayıcı işletim SISTEMI sürümlerinin hangi işletim sistemi sürümlerinde desteklendiğini ve bilinen sorunların [kapsayıcılarına yönelik bilinen sorunları](build-tools-container-issues.md) görmek için bkz. [Windows kapsayıcı sürümü uyumluluğu](/virtualization/windowscontainers/deploy-containers/version-compatibility) .

   ::: moniker-end
   
   > [!NOTE]
   > Hata kodu `3010`, yeniden başlatma gerektiren başarıyı göstermek için kullanılır, daha fazla bilgi için bkz. [msiexec. exe hata iletileri](/windows/win32/msi/error-codes) .

1. Bu dizinin içinde aşağıdaki komutu çalıştırın.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Bu komut Dockerfile 2 GB bellek kullanarak geçerli dizinde oluşturur. Bazı iş yükleri yüklendiğinde varsayılan 1 GB yeterli değildir; Ancak, yapı gereksinimlerinize bağlı olarak yalnızca 1 GB bellek oluşturabilirsiniz.

   Son görüntü etiketli "buildtools2017:latest" olduğundan, hiçbir etiket belirtilirse "son" etiketi varsayılan olduğundan kolayca bir kapsayıcıda "buildtools2017" çalıştırabilirsiniz. Daha belirli bir Visual Studio derleme araçları 2017 sürümüne kullanmak istiyorsanız [Gelişmiş senaryo](advanced-build-tools-container.md), bunun yerine belirli bir kapsayıcıda etiketi Visual Studio, sayı olarak "son" belirli bir kapsayıcı kullanabilmeniz için derleme Sürüm tutarlı bir şekilde.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Bu komut Dockerfile 2 GB bellek kullanarak geçerli dizinde oluşturur. Bazı iş yükleri yüklendiğinde varsayılan 1 GB yeterli değildir; Ancak, yapı gereksinimlerinize bağlı olarak yalnızca 1 GB bellek oluşturabilirsiniz.

   Son görüntü "buildtools2019: latest" olarak etiketlendi, bu nedenle "en son" etiketi, hiçbir etiket belirtilmemişse varsayılan değer olan "buildtools2019" olarak bir kapsayıcıda kolayca çalıştırabilirsiniz. Daha [Gelişmiş bir senaryoda](advanced-build-tools-container.md)Visual Studio derleme araçları 2019 ' nin belirli bir sürümünü kullanmak istiyorsanız, kapsayıcının belirli bir sürümü tutarlı bir şekilde kullanabilmesi için kapsayıcıyı belirli bir Visual Studio derleme numarasıyla ve "en son" ile etiketleyebilirsiniz.

   ::: moniker-end

## <a name="using-the-built-image"></a>Oluşturulan görüntüyü kullanarak

Görüntü oluşturduğunuza göre etkileşimli ve otomatik yapılara yapmak için bir kapsayıcı içinde çalıştırabilirsiniz. Örneğin, yol ve diğer ortam değişkenlerine zaten yapılandırılmış Geliştirici komut istemi kullanır.

1. Bir komut istemi açın.

1. Kapsayıcı tüm geliştirici ile bir PowerShell ortamı başlatmak için ayarlanan ortam değişkenlerine çalıştırın:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Bu görüntüyü CI/CD iş akışınız için kullanmak üzere, sunucuların yalnızca çekmesini gerektiren [Azure Container Registry](https://azure.microsoft.com/services/container-registry) veya diğer Iç [Docker kayıt defterinizde](https://docs.docker.com/registry/deploying) yayımlayabilirsiniz.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)
