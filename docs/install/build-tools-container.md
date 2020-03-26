---
title: Visual Studio Build Tools'u konteynere yükleyin
titleSuffix: ''
description: Sürekli tümleştirme ve sürekli teslim (CI/CD) iş akışlarını desteklemek için Visual Studio Build Tools'u windows kapsayıcısına nasıl yükleyini öğrenin.
ms.date: 03/25/2020
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
ms.openlocfilehash: 61ec972bd5e361c4417e49092de5976000a6da5f
ms.sourcegitcommit: dfa9476b69851c28b684ece66980bee735fef8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80273900"
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

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
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
   > İş yükleri ve bileşenlerlistesi için [Visual Studio Build Tools bileşen dizinine](workload-component-id-vs-build-tools.md)bakın.
   >

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
   > İş yükleri ve bileşenlerlistesi için [Visual Studio Build Tools bileşen dizinine](workload-component-id-vs-build-tools.md)bakın.
   >

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

   > [!NOTE]
   > Docker konteyneri başlamazsa, büyük olasılıkla Visual Studio yükleme sorunu vardır. Visual Studio toplu komutunu çağıran adımı kaldırmak için Dockerfile'yi güncelleştirebilirsiniz. Bu, Docker kapsayıcısını başlatmanızı ve yükleme hatası günlüklerini okumanızı sağlar.
   >
   > Dockerfile dosyanızda, komutu `&&` ve `ENTRYPOINT` parametreleri `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` kaldırın. Komut şimdi olmalıdır `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]`. Ardından, Dockerfile'ı yeniden `run` oluşturun ve kapsayıcı dosyalarına erişmek için komutu çalıştırın. Yükleme hatası günlüklerini bulmak için `$env:TEMP` dizine gidin `dd_setup_<timestamp>_errors.log` ve dosyayı bulun.
   >
   > Yükleme sorununu tanımlayıp düzelttinden `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` sonra, `&&` `ENTRYPOINT` komuta ve parametrelere geri ekleyebilir ve Dockerfile'ınızı yeniden oluşturabilirsiniz.
   >
   > Daha fazla bilgi [için, kapsayıcılar için bilinen sorunlara](build-tools-container-issues.md)bakın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio Build Tools iş yükü ve bileşen ilikleri](workload-component-id-vs-build-tools.md)
