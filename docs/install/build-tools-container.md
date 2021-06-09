---
title: Visual Studio Derleme Araçları bir kapsayıcıya yükler
titleSuffix: ''
description: Sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını desteklemek için Visual Studio Derleme Araçları Windows kapsayıcısına yüklemeyi öğrenin.
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dcf28f818760320b215cbff0d3a2eb5ad6d9f623
ms.sourcegitcommit: 55b99dbce29d19e493feae9b8d2fdac73718e4de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873074"
---
# <a name="install-build-tools-into-a-container"></a>Derleme araçlarını bir kapsayıcıya yükler

Sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını desteklemek için bir Windows kapsayıcısına Visual Studio Derleme Araçları yükleyebilirsiniz. Bu makalede, Docker yapılandırma değişikliklerinin yanı sıra bir kapsayıcıya yükleyebileceğiniz [iş yüklerini ve bileşenleri](workload-component-id-vs-build-tools.md) de size kılavuzluk eder.

[Kapsayıcılar](https://www.docker.com/what-container) , yalnızca bir CI/CD sunucu ortamında değil, ancak geliştirme ortamları için de kullanabileceğiniz tutarlı bir yapı sistemini paketlemenize yönelik harika bir yoldur. Örneğin, kodunuzu yazmak için Visual Studio 'Yu veya diğer araçları kullanmaya devam ederken, kaynak kodunuzu özelleştirilmiş bir ortam tarafından oluşturulacak bir kapsayıcıya bağlayabilirsiniz. CI/CD iş akışınız aynı kapsayıcı görüntüsünü kullanıyorsa, kodunuzun tutarlı bir şekilde derlemeinden emin olabilirsiniz. Kapsayıcıları, bir Orchestration sistemiyle birden çok kapsayıcı kullanan mikro hizmetler için ortak olan çalışma zamanı tutarlılığı için de kullanabilirsiniz; Ancak, bu makalenin kapsamı dışındadır.

Kaynak kodunuzu derlemek için ihtiyaç duyduğunuz Visual Studio Derleme Araçları yoksa, bu adımlar diğer Visual Studio ürünleri için de kullanılabilir. Bununla birlikte, Windows kapsayıcıları etkileşimli bir kullanıcı arabirimini desteklemediğine yönelik tüm komutların otomatik olması gerekir.

## <a name="before-you-begin"></a>Başlamadan önce

[Docker](https://www.docker.com/what-docker) ile ilgili bazı benzerlik aşağıdaki gibi kabul edilir. Windows üzerinde Docker çalıştıran bir bilginiz yoksa, [Windows 'Da Docker motorunu yüklemek ve yapılandırmak](/virtualization/windowscontainers/manage-docker/configure-docker-daemon)hakkında bilgi edinin.

Aşağıdaki temel görüntü bir örnektir ve sisteminiz için çalışmayabilir. Ortamınız için hangi temel görüntünün kullanılması gerektiğini öğrenmek için [Windows kapsayıcı sürümü uyumluluğunu](/virtualization/windowscontainers/deploy-containers/version-compatibility) okuyun.

## <a name="create-and-build-the-dockerfile"></a>Dockerfile oluşturma ve derleme

Aşağıdaki örnek Dockerfile dosyasını diskinizdeki yeni bir dosyaya kaydedin. Dosya yalnızca "Dockerfile" olarak adlandırılmışsa varsayılan olarak tanınır.

> [!WARNING]
> Bu örnek Dockerfile yalnızca kapsayıcılara yüklenebilen önceki Windows SDK 'larını dışlar. Önceki sürümler derleme komutunun başarısız olmasına neden olur.

1. Bir komut istemi açın.

1. Yeni dizin oluştur (önerilir):

   ```shell
   mkdir C:\BuildTools
   ```

1. Dizinleri bu yeni dizine Değiştir:

   ```shell
   cd C:\BuildTools
   ```

1. Aşağıdaki içeriği C:\buildtools\dockerfiledizinine kaydedin.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN start /wait C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > İş yükleri ve bileşenlerin listesi için [Visual Studio derleme araçları bileşen dizinine](workload-component-id-vs-build-tools.md)bakın.
   >

   > [!WARNING]
   > Görüntünüzü doğrudan Microsoft/windowsservercore veya mcr.microsoft.com/windows/servercore (bkz. [Microsoft Syndicates Container Catalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)) üzerine temellendiriyor, .NET Framework düzgün şekilde yüklenemeyebilir ve hiçbir yüklemesi hatası belirtilmez. Yönetilen kod, yüklemesi tamamlandıktan sonra çalışmayabilir. Bunun yerine, görüntünüzü [Microsoft/DotNet-Framework: 4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) veya üzeri bir sürüme dayandırın. Ayrıca, 4.7.2 veya üzeri etiketli görüntülerin PowerShell 'i varsayılan olarak kullanabileceğini unutmayın ve bu da `SHELL` `RUN` `ENTRYPOINT` yönergelerin başarısız olmasına neden olur.
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

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > İş yükleri ve bileşenlerin listesi için [Visual Studio derleme araçları bileşen dizinine](workload-component-id-vs-build-tools.md)bakın.
   >

   > [!WARNING]
   > Görüntünüzü doğrudan Microsoft/windowsservercore 'a dayandırırsanız .NET Framework düzgün şekilde yüklenemeyebilir ve hiçbir yüklemesi hatası belirtilmez. Yönetilen kod, yüklemesi tamamlandıktan sonra çalışmayabilir. Bunun yerine, görüntünüzü [Microsoft/DotNet-Framework: 4.8](https://hub.docker.com/r/microsoft/dotnet-framework) veya üzeri bir sürüme dayandırın. Ayrıca, 4,8 veya üzeri etiketli görüntülerin PowerShell 'i varsayılan olarak kullanabileceğini unutmayın. Bu, `SHELL` `RUN` ve yönergelerinin başarısız olmasına neden olur `ENTRYPOINT` .
   >
   > Hangi kapsayıcı işletim SISTEMI sürümlerinin hangi işletim sistemi sürümlerinde desteklendiğini ve bilinen sorunların [kapsayıcılarına yönelik bilinen sorunları](build-tools-container-issues.md) görmek için bkz. [Windows kapsayıcı sürümü uyumluluğu](/virtualization/windowscontainers/deploy-containers/version-compatibility) .

   ::: moniker-end
   
   > [!NOTE]
   > Hata kodu `3010` , yeniden başlatma gerektiren başarıyı göstermek için kullanılır. daha fazla bilgi için bkz. [MsiExec.exe hata iletileri](/windows/win32/msi/error-codes) .

1. Bu dizin içinde aşağıdaki komutu çalıştırın.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Bu komut, Dockerfile 'ı geçerli dizinde 2 GB bellek kullanarak oluşturur. Bazı iş yükleri yüklendiğinde varsayılan 1 GB yeterli değildir; Ancak, yapı gereksinimlerinize bağlı olarak yalnızca 1 GB bellek oluşturabilirsiniz.

   Son görüntü "buildtools2017: latest" olarak etiketlendi, bu nedenle "en son" etiketi, hiçbir etiket belirtilmemişse varsayılan değer olan "buildtools2017" olarak bir kapsayıcıda kolayca çalıştırabilirsiniz. Daha [Gelişmiş bir senaryoda](advanced-build-tools-container.md)Visual Studio derleme araçları 2017 ' nin belirli bir sürümünü kullanmak istiyorsanız, kapsayıcının belirli bir sürümü tutarlı bir şekilde kullanabilmesi için kapsayıcıyı belirli bir Visual Studio derleme numarasıyla ve "en son" ile etiketleyebilirsiniz.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Bu komut, Dockerfile 'ı geçerli dizinde 2 GB bellek kullanarak oluşturur. Bazı iş yükleri yüklendiğinde varsayılan 1 GB yeterli değildir; Ancak, yapı gereksinimlerinize bağlı olarak yalnızca 1 GB bellek oluşturabilirsiniz.

   Son görüntü "buildtools2019: latest" olarak etiketlendi, bu nedenle "en son" etiketi, hiçbir etiket belirtilmemişse varsayılan değer olan "buildtools2019" olarak bir kapsayıcıda kolayca çalıştırabilirsiniz. Daha [Gelişmiş bir senaryoda](advanced-build-tools-container.md)Visual Studio derleme araçları 2019 ' nin belirli bir sürümünü kullanmak istiyorsanız, kapsayıcının belirli bir sürümü tutarlı bir şekilde kullanabilmesi için kapsayıcıyı belirli bir Visual Studio derleme numarasıyla ve "en son" ile etiketleyebilirsiniz.

   ::: moniker-end

## <a name="using-the-built-image"></a>Oluşturulan görüntüyü kullanma

Artık bir görüntü oluşturduğunuza göre, hem etkileşimli hem de otomatik derlemeler yapmak için bunu bir kapsayıcıda çalıştırabilirsiniz. Örnek Geliştirici Komut İstemi kullanır, bu nedenle yolunuza ve diğer ortam değişkenleriniz zaten yapılandırılmıştır.

1. Bir komut istemi açın.

1. Tüm geliştirici ortamı değişkenleri ayarlanmış bir PowerShell ortamı başlatmak için kapsayıcıyı çalıştırın:

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

   > [!NOTE]
   > Docker kapsayıcısı başlatılamazsa, büyük olasılıkla bir Visual Studio yükleme sorunu vardır. Visual Studio Batch komutunu çağıran adımı kaldırmak için Dockerfile 'ı güncelleştirebilirsiniz. Bu, Docker kapsayıcısını başlatıp yükleme hata günlüklerini okumanızı sağlar.
   >
   > Dockerfile dosyanızda, `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` ve `&&` parametrelerini `ENTRYPOINT` komutunu komuttan kaldırın. Komut şu anda olmalıdır `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]` . Sonra, Dockerfile dosyasını yeniden derleyin ve `run` kapsayıcı dosyalarına erişmek için komutunu yürütün. Yükleme hata günlüklerini bulmak için `$env:TEMP` dizine gidin ve `dd_setup_<timestamp>_errors.log` dosyayı bulun.
   >
   > Yükleme sorununu tanımlayıp düzelttikten sonra, `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` ve `&&` parametrelerini komuta geri ekleyebilir `ENTRYPOINT` ve dockerfile dosyanızı yeniden oluşturabilirsiniz.
   >
   > Daha fazla bilgi için bkz. [kapsayıcılar Için bilinen sorunlar](build-tools-container-issues.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)
