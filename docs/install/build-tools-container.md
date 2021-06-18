---
title: Kapsayıcıya Visual Studio Derleme Araçları yükleme
titleSuffix: ''
description: Sürekli tümleştirme ve sürekli Visual Studio Derleme Araçları (CI/CD) iş akışlarını desteklemek için bir Windows kapsayıcısı içine uygulama yükleme hakkında bilgi alın.
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
ms.openlocfilehash: e29e780d146fec63bc1375ed16f72067f9b4ccee
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307641"
---
# <a name="install-build-tools-into-a-container"></a>Kapsayıcıya Derleme Araçları yükleme

Windows kapsayıcısı Visual Studio Derleme Araçları sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını desteklemek için bu kapsayıcıyı yükleyebilirsiniz. Bu makale, hangi Docker yapılandırma değişikliklerinin gerekli [](workload-component-id-vs-build-tools.md) olduğu ve bir kapsayıcıya yükleyebilirsiniz iş yüklerinin ve bileşenlerin yanı sıra size yol gösterir.

[Kapsayıcılar,](https://www.docker.com/what-container) yalnızca CI/CD sunucusu ortamında değil, geliştirme ortamları için de kullanabileceğiniz tutarlı bir derleme sistemini paketleyenin harika bir yoludur. Örneğin, kodunuzu yazmak için Visual Studio veya diğer araçları kullanmaya devam ederken, özelleştirilmiş bir ortam tarafından Visual Studio kapsayıcıya kaynak kodunuzu bağlamanız gerekir. CI/CD iş akışınız aynı kapsayıcı görüntüsünü kullanıyorsa kodunuzun tutarlı bir şekilde derlemesi konusunda emin olabilirsiniz. Çalışma zamanı tutarlılığı için kapsayıcıları da kullanabilirsiniz. Bu, bir düzenleme sistemiyle birden çok kapsayıcı kullanan mikro hizmetler için yaygındır; ancak, bu makalenin kapsamının dışındadır.

Kaynak Visual Studio Derleme Araçları oluşturmak için gerekenler yoksa, aynı adımlar diğer yazılım ürünleri için Visual Studio kullanılabilir. Ancak, Windows kapsayıcılarının etkileşimli bir kullanıcı arabirimini desteklemez, bu nedenle tüm komutların otomatik olması gerektiğini unutmayın.

## <a name="before-you-begin"></a>Başlamadan önce

Docker ile ilgili [bazı bilindikler](https://www.docker.com/what-docker) aşağıda varsayılır. Docker'ı Windows üzerinde çalıştırma hakkında bilginiz yoksa, Windows'da Docker altyapısını yükleme [ve yapılandırma hakkında bilgi okuyun.](/virtualization/windowscontainers/manage-docker/configure-docker-daemon)

Aşağıdaki temel görüntü bir örnektir ve sisteminiz için çalışmayabilirsiniz. Ortamınız [için hangi temel görüntüyü kullanmanız](/virtualization/windowscontainers/deploy-containers/version-compatibility) gerektiğini belirlemek üzere Windows kapsayıcı sürümü uyumluluğu makalesini okuyun.

## <a name="create-and-build-the-dockerfile"></a>Dockerfile oluşturma ve derleme

Aşağıdaki örnek Dockerfile dosyasını diskiniz üzerinde yeni bir dosyaya kaydedin. Dosya yalnızca "Dockerfile" olarak adlandırılmışsa varsayılan olarak tanınır.

> [!WARNING]
> Bu örnek Dockerfile yalnızca kapsayıcılara yüklenemey önceki Windows SDK'lerini dışlar. Önceki sürümler derleme komutunun başarısız olmasına neden olur.

1. Bir komut istemi açın.

1. Yeni dizin oluşturma (önerilir):

   ```shell
   mkdir C:\BuildTools
   ```

1. Dizinleri şu yeni dizinle değiştir:

   ```shell
   cd C:\BuildTools
   ```

1. Aşağıdaki içeriği C:\BuildTools\Dockerfile dizinine kaydedin.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   RUN `
       # Download the Build Tools bootstrapper.
       curl -SL --output vs_buildtools.exe https://aka.ms/vs/15/release/vs_buildtools.exe `
       `
       # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
       && (start /w vs_buildtools.exe --quiet --wait --norestart --nocache `
           --installPath C:\BuildTools `
           --add Microsoft.VisualStudio.Workload.AzureBuildTools `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
           --remove Microsoft.VisualStudio.Component.Windows81SDK `
           || IF "%ERRORLEVEL%"=="3010" EXIT 0) `
       `
       # Cleanup
       && del /q vs_buildtools.exe

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > İş yüklerinin ve bileşenlerin listesi için bkz. [Visual Studio Derleme Araçları dizini.](workload-component-id-vs-build-tools.md)
   >

   > [!WARNING]
   > Görüntülerinizi doğrudan microsoft/windowsservercore veya mcr.microsoft.com/windows/servercore temel alırsanız (bkz. [Microsoft syndicates kapsayıcı](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)kataloğu), .NET Framework düzgün yüklenmeyebilir ve yükleme hatası belirtemeyebilir. Yükleme tamamlandıktan sonra yönetilen kod çalıştırılamayabilirsiniz. Bunun yerine görüntülerinizi [microsoft/dotnet-framework:4.7.2 veya sonraki bir sürümü](https://hub.docker.com/r/microsoft/dotnet-framework) temel edin. Ayrıca, sürüm 4.7.2 veya sonraki sürümlerde etiketlenen görüntülerin varsayılan olarak PowerShell kullanabileceğini ve yönergelerinin başarısız olmasına `SHELL` `RUN` neden olabileceğini `ENTRYPOINT` unutmayın.
   >
   > Visual Studio 2017 sürüm 15.8 veya önceki sürümler (herhangi bir ürün) mcr.microsoft.com/windows/servercore:1809 yüklemez. Hiçbir hata görüntülenmez.
   >
   > Hangi [kapsayıcı işletim sistemi sürümlerinin](/virtualization/windowscontainers/deploy-containers/version-compatibility) hangi konak işletim sistemi sürümlerinde destek olduğunu ve bilinen sorunlar için kapsayıcılar için bilinen sorunları görmek için bkz. Windows kapsayıcı sürümü uyumluluğu. [](build-tools-container-issues.md)
   
   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   RUN `
       # Download the Build Tools bootstrapper.
       curl -SL --output vs_buildtools.exe https://aka.ms/vs/16/release/vs_buildtools.exe `
       `
       # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
       && (start /w vs_buildtools.exe --quiet --wait --norestart --nocache modify `
           --installPath "%ProgramFiles(x86)%\Microsoft Visual Studio\2019\BuildTools" `
           --add Microsoft.VisualStudio.Workload.AzureBuildTools `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
           --remove Microsoft.VisualStudio.Component.Windows81SDK `
           || IF "%ERRORLEVEL%"=="3010" EXIT 0) `
       `
       # Cleanup
       && del /q vs_buildtools.exe

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > İş yüklerinin ve bileşenlerin listesi için bkz. [Visual Studio Derleme Araçları dizini.](workload-component-id-vs-build-tools.md)
   >

   > [!WARNING]
   > Görüntülerinizi doğrudan microsoft/windowsservercore'a temel alırsanız, .NET Framework düzgün yüklenmeyebilir ve yükleme hatası belirtemeyebilir. Yükleme tamamlandıktan sonra yönetilen kod çalıştırılamayabilirsiniz. Bunun yerine görüntülerinizi [microsoft/dotnet-framework:4.8 veya sonraki bir sürümüne](https://hub.docker.com/r/microsoft/dotnet-framework) temel edin. Ayrıca, sürüm 4.8 veya sonraki sürümlerde etiketlenen görüntülerin varsayılan olarak PowerShell kullanabileceğini ve yönergelerinin başarısız `SHELL` `RUN` `ENTRYPOINT` olmasına neden olabileceğini unutmayın.
   >
   > Hangi [kapsayıcı işletim sistemi sürümlerinin](/virtualization/windowscontainers/deploy-containers/version-compatibility) hangi konak işletim sistemi sürümlerinde destek olduğunu ve bilinen sorunlar için kapsayıcılar için bilinen sorunları görmek için bkz. Windows kapsayıcı sürümü uyumluluğu. [](build-tools-container-issues.md)

   ::: moniker-end
   
   > [!NOTE]
   > Hata `3010` kodu, yeniden başlatma gerektiğinde başarılı olduğunu belirtmek için kullanılır. Daha [ fazla bilgiMsiExec.exe hata iletilerine](/windows/win32/msi/error-codes) bakın.

1. Bu dizinde aşağıdaki komutu çalıştırın.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Bu komut, 2 GB bellek kullanarak geçerli dizinde Dockerfile'ı derlemek için kullanılır. Bazı iş yükleri yüklenirken varsayılan 1 GB yeterli değildir; ancak, derleme gereksinimlerinize bağlı olarak yalnızca 1 GB bellekle derleme yapabiliyorsunuz.

   Son görüntü "buildtools2017:latest" olarak etiketlenir; böylece bir kapsayıcıda "buildtools2017" olarak kolayca çalıştırabilirsiniz çünkü etiket belirtilmezse "latest" etiketi varsayılandır. Daha gelişmiş bir senaryoda Visual Studio Derleme Araçları 2017'nin belirli bir sürümünü kullanmak için [kapsayıcıyı](advanced-build-tools-container.md)belirli bir Visual Studio derleme numarasıyla ve "en son" sayıyla etiketleyebilirsiniz. Böylece kapsayıcılar belirli bir sürümü tutarlı bir şekilde kullanabilir.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Bu komut, 2 GB bellek kullanarak geçerli dizinde Dockerfile'ı derlemek için kullanılır. Bazı iş yükleri yüklenirken varsayılan 1 GB yeterli değildir; ancak, derleme gereksinimlerinize bağlı olarak yalnızca 1 GB bellekle derleme yapabiliyorsunuz.

   Son görüntü "buildtools2019:latest" olarak etiketlenir; böylece bir kapsayıcıda "buildtools2019" olarak kolayca çalıştırabilirsiniz çünkü etiket belirtilmezse "latest" etiketi varsayılandır. Daha gelişmiş bir senaryoda Visual Studio Derleme Araçları 2019'un belirli bir sürümünü kullanmak için [kapsayıcıyı](advanced-build-tools-container.md)belirli bir Visual Studio derleme numarasıyla ve "en son" olarak etiketleyebilirsiniz. Böylece kapsayıcılar belirli bir sürümü tutarlı bir şekilde kullanabilir.

   ::: moniker-end

## <a name="using-the-built-image"></a>Yerleşik görüntüyü kullanma

Artık bir görüntü oluşturduğunuza göre, hem etkileşimli hem de otomatik derlemeler yapmak için görüntüyü bir kapsayıcıda çalıştırabilirsiniz. Örnek, Geliştirici Komut İstemi kullandığı için PATH ve diğer ortam değişkenleriniz zaten yapılandırılmıştır.

1. Bir komut istemi açın.

1. Tüm geliştirici ortamı değişkenleri ayarlanmış bir PowerShell ortamı başlatmak için kapsayıcıyı çalıştırın:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Bu görüntüyü CI/CD iş akışınız için kullanmak üzere, sunucuların yalnızca çekmesi [Azure Container Registry](https://azure.microsoft.com/services/container-registry) kendi iş akışınıza veya diğer iç [Docker](https://docs.docker.com/registry/deploying) kayıt defterinize yayımlayın.

   > [!NOTE]
   > Docker kapsayıcısı başlatılamezse büyük olasılıkla bir Visual Studio sorunu vardır. Visual Studio batch komutunu çağıran adımı kaldırmak için Dockerfile'ı güncelleştirebilirsiniz. Bu, Docker kapsayıcısını başlatmaya ve yükleme hata günlüklerini okumaya olanak sağlar.
   >
   > Dockerfile dosyanıza komutundan `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` ve parametrelerini `ENTRYPOINT` kaldırın. Komutun artık olması `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]` gerekir. Ardından Dockerfile dosyasını yeniden oluşturarak kapsayıcı `run` dosyalarına erişmek için komutunu yürütün. Yükleme hata günlüklerini bulmak için dizinine `$env:TEMP` gidin ve dosyayı `dd_setup_<timestamp>_errors.log` bulun.
   >
   > Yükleme sorunu tanımdan ve düzeltdikten sonra, komutuna ve parametrelerini ekleyebilir ve Dockerfile dosyanızı `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` yeniden `ENTRYPOINT` yapılandırabilirsiniz.
   >
   > Daha fazla bilgi için [bkz. Kapsayıcılar için bilinen sorunlar.](build-tools-container-issues.md)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)
