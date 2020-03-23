---
title: Visual Studio Build Tools'u konteynere yükleyin
titleSuffix: ''
description: Sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını desteklemek için Visual Studio Build Tools'u windows kapsayıcısına nasıl yükleyini öğrenin.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114613"
---
# <a name="install-build-tools-into-a-container"></a>Yapı Araçları'nı bir kapsayıcıya yükleme

Sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını desteklemek için Visual Studio Build Tools'u bir Windows kapsayıcısına yükleyebilirsiniz. Bu makalede, Docker yapılandırma değişikliklerinin gerekli olduğu gibi bir kapsayıcıya yükleyebileceğiniz [iş yükleri ve bileşenleri](workload-component-id-vs-build-tools.md) size yol göstermektedir.

[Kapsayıcılar,](https://www.docker.com/what-container) yalnızca CI/CD sunucu ortamında değil, geliştirme ortamlarında da kullanabileceğiniz tutarlı bir yapı sistemini paketlemenin harika bir yoludur. Örneğin, kodunuzu yazmak için Visual Studio veya diğer araçları kullanmaya devam ederken kaynak kodunuzu özelleştirilmiş bir ortam tarafından oluşturulacak bir kapsayıcıya monte edebilirsiniz. CI/CD iş akışınız aynı kapsayıcı görüntüsünü kullanıyorsa, kodunuzu tutarlı bir şekilde oluşturduğundan emin olabilirsiniz. Bir orkestrasyon sistemi ile birden fazla kapsayıcı kullanarak mikro hizmetler için yaygın olan çalışma zamanı tutarlılığı için kapsayıcılar da kullanabilirsiniz; ancak, bu makalenin kapsamı dışındadır.

Visual Studio Build Tools kaynak kodunuzu oluşturmak için gerekenlere sahip değilse, bu aynı adımlar diğer Visual Studio ürünleri için de kullanılabilir. Ancak, Windows kapsayıcılarının etkileşimli bir kullanıcı arabirimini desteklemediğini, bu nedenle tüm komutların otomatik leştirilmiş olması gerektiğini unutmayın.

## <a name="before-you-begin"></a>Başlamadan önce

[Docker](https://www.docker.com/what-docker) ile bazı aşinalık aşağıda kabul edilebedilir. Windows'da Docker'ı çalıştırmayı zaten bilmiyorsanız, [Windows'da Docker altyapısını nasıl yükleyip yapılandırabileceğiniz](/virtualization/windowscontainers/manage-docker/configure-docker-daemon)hakkında bilgi edinin.

Aşağıdaki temel resim bir örnektir ve sisteminiz için çalışmayabilir. Ortamınız için hangi temel görüntüyü kullanmanız gerektiğini belirlemek için [Windows kapsayıcı sürümü uyumluluğunu](/virtualization/windowscontainers/deploy-containers/version-compatibility) okuyun.

## <a name="create-and-build-the-dockerfile"></a>Dockerfile'ı oluşturma ve oluşturma

Aşağıdaki örnek Dockerfile'ı diskinizdeki yeni bir dosyaya kaydedin. Dosya yalnızca "Dockerfile" olarak adlandırılırsa, varsayılan olarak tanınır.

> [!WARNING]
> Bu örnek Dockerfile, kapsayıcılara yüklenemeyen yalnızca önceki Windows SDK'larını hariç tutar. Önceki sürümler yapı komutu başarısız neden olur.

1. Bir komut istemi açın.

1. Yeni bir dizin oluşturma (önerilir):

   ```shell
   mkdir C:\BuildTools
   ```

1. Dizinleri bu yeni dizinle değiştirin:

   ```shell
   cd C:\BuildTools
   ```

1. Aşağıdaki içeriği C:\BuildTools\Dockerfile dosyasına kaydedin.
 
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
   > Resminizi doğrudan microsoft/windowsservercore veya mcr.microsoft.com/windows/servercore temel lerseniz (bkz. [Microsoft syndicates konteyner kataloğu),](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/).NET Framework düzgün yüklenmeyebilir ve yükleme hatası belirtilmeyebilir. Yönetilen kod yükleme tamamlandıktan sonra çalışmayabilir. Bunun yerine, resminizi [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) veya sonraki temeller. Ayrıca, sürüm 4.7.2 veya daha sonra etiketlenen görüntülerin `SHELL`PowerShell'i `RUN` varsayılan `ENTRYPOINT` olarak kullanabileceğini ve bu görüntülerin ve yönergelerin başarısız lığa neden olacağını unutmayın.
   >
   > Visual Studio 2017 sürüm 15.8 veya daha önceki (herhangi bir ürün) mcr.microsoft.com/windows/servercore:1809 veya daha sonra düzgün bir şekilde yüklenmez. Hata görüntülenmez.
   >
   > Hangi kapsayıcı işletim sistemi sürümlerinin hangi işletim sistemi sürümlerinde destekleneceğini görmek için [Windows kapsayıcı sürümü uyumluluğu](/virtualization/windowscontainers/deploy-containers/version-compatibility) ve bilinen sorunlar için [kapsayıcılar için bilinen sorunları](build-tools-container-issues.md) görün.

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
   > Resminizi doğrudan microsoft/windowsservercore'a temel alarsanız, .NET Framework düzgün yüklenmeyebilir ve yükleme hatası belirtilmeyebilir. Yönetilen kod yükleme tamamlandıktan sonra çalışmayabilir. Bunun yerine, resminizi [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) veya sonraki temeller. Ayrıca, sürüm 4.8 veya daha sonra etiketlenen görüntülerin `SHELL`PowerShell'i `RUN` varsayılan `ENTRYPOINT` olarak kullanabileceğini ve bu nedenle yönergelerin başarısız lığa neden olacağını unutmayın.
   >
   > Hangi kapsayıcı işletim sistemi sürümlerinin hangi işletim sistemi sürümlerinde destekleneceğini görmek için [Windows kapsayıcı sürümü uyumluluğu](/virtualization/windowscontainers/deploy-containers/version-compatibility) ve bilinen sorunlar için [kapsayıcılar için bilinen sorunları](build-tools-container-issues.md) görün.

   ::: moniker-end
   
   > [!NOTE]
   > Hata `3010` kodu, yeniden başlatma nın gerekli olduğu başarıyı belirtmek için kullanılır, daha fazla bilgi için [MsiExec.exe hata iletilerine](/windows/win32/msi/error-codes) bakın.

1. Bu dizin içinde aşağıdaki komutu çalıştırın.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Bu komut, 2 GB bellek kullanarak geçerli dizinde Dockerfile oluşturur. Bazı iş yükleri yüklendiğinde varsayılan 1 GB yeterli değildir; ancak, yapı gereksinimlerinize bağlı olarak yalnızca 1 GB bellekle oluşturabilirsiniz.

   Son resim "buildtools2017:latest" olarak etiketlenir, böylece "en son" etiketi belirtilmemişse varsayılan etiket olduğundan, bir kapta kolayca "buildtools2017" olarak çalıştırabilirsiniz. Visual Studio Build Tools 2017'nin belirli bir sürümünü daha gelişmiş bir [senaryoda](advanced-build-tools-container.md)kullanmak istiyorsanız, kapsayıcıların belirli bir sürümü tutarlı bir şekilde kullanabilmesi için kapsayıcıyı belirli bir Visual Studio yapı numarasının yanı sıra "en son" olarak etiketleyebilirsiniz.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Bu komut, 2 GB bellek kullanarak geçerli dizinde Dockerfile oluşturur. Bazı iş yükleri yüklendiğinde varsayılan 1 GB yeterli değildir; ancak, yapı gereksinimlerinize bağlı olarak yalnızca 1 GB bellekle oluşturabilirsiniz.

   Son resim "buildtools2019:latest" olarak etiketlenir, böylece "en son" etiketi belirtilmemişse varsayılan etiket olduğundan, bir kapta kolayca "buildtools2019" olarak çalıştırabilirsiniz. Visual Studio Build Tools 2019'un belirli bir sürümünü daha gelişmiş bir [senaryoda](advanced-build-tools-container.md)kullanmak istiyorsanız, kapsayıcıların belirli bir sürümü tutarlı bir şekilde kullanabilmesi için kapsayıcıyı belirli bir Visual Studio yapı numarasının yanı sıra "en son" olarak etiketleyebilirsiniz.

   ::: moniker-end

## <a name="using-the-built-image"></a>Yerleşik görüntüyü kullanma

Artık bir görüntü oluşturduğunuza göre, hem etkileşimli hem de otomatik yapılar yapmak için bir kapsayıcıda çalıştırabilirsiniz. Örnek, Geliştirici Komut Komut Ustem'ini kullanır, bu nedenle PATH ve diğer ortam değişkenleriniz zaten yapılandırılmıştır.

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

Bu resmi CI/CD iş akışınız için kullanmak için, sunucuların yalnızca çekmesi gerektiğinden, bu resmi kendi [Azure Kapsayıcı Kayıt Defterinizde](https://azure.microsoft.com/services/container-registry) veya diğer dahili [Docker registry'nizde](https://docs.docker.com/registry/deploying) yayımlayabilirsiniz.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio Build Tools iş yükü ve bileşen ilikleri](workload-component-id-vs-build-tools.md)
