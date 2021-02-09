---
title: Kapsayıcılar için gelişmiş örnek
description: Docker kapsayıcıları için gelişmiş bir örnek hakkında bilgi edinin. Bu örnek Dockerfile, Microsoft/DotNet-Framework görüntüsünün belirli bir sürüm etiketini kullanır.
ms.custom: SEO-VS-2020
ms.date: 03/25/2020
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d8b2148dced2d08d04c73091375f91ab37732274
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868744"
---
# <a name="advanced-example-for-containers"></a>Kapsayıcılar için gelişmiş örnek

::: moniker range="vs-2017"

[Derleme araçlarını bir kapsayıcıya yükleyen](build-tools-container.md) örnek Dockerfile, her zaman en son Microsoft/windowsservercore görüntüsüne ve en son Visual Studio derleme araçları yükleyiciye göre [Microsoft/DotNet-Framework: 4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) görüntüsünü kullanır. Bu görüntüyü başkalarının çekmesini sağlamak için bir [Docker kayıt defterine](https://azure.microsoft.com/services/container-registry) yayımlarsanız, bu görüntü pek çok senaryo için sorunsuz olabilir. Bununla birlikte, uygulamada hangi temel görüntü, hangi ikililerin indirileceği ve hangi araç sürümlerinin yükleneceğini öğrenmek daha yaygındır.

::: moniker-end

::: moniker range="vs-2019"

[Derleme araçlarını bir kapsayıcıya yükleyen](build-tools-container.md) örnek Dockerfile, her zaman en son Microsoft/windowsservercore görüntüsüne ve en son Visual Studio derleme araçları yükleyiciye göre [Microsoft/DotNet-Framework: 4.8](https://hub.docker.com/r/microsoft/dotnet-framework) görüntüsünü kullanır. Bu görüntüyü başkalarının çekmesini sağlamak için bir [Docker kayıt defterine](https://azure.microsoft.com/services/container-registry) yayımlarsanız, bu görüntü pek çok senaryo için sorunsuz olabilir. Bununla birlikte, uygulamada hangi temel görüntü, hangi ikililerin indirileceği ve hangi araç sürümlerinin yükleneceğini öğrenmek daha yaygındır.

::: moniker-end

Aşağıdaki örnek Dockerfile, Microsoft/DotNet-Framework görüntüsünün belirli bir sürüm etiketini kullanır. Temel görüntü için belirli bir etiket kullanılması çok önemlidir ve görüntülerin oluşturulması veya yeniden derlenmesi her zaman aynı şekilde olduğunu unutmayı kolaylaştırır.

> [!NOTE]
> Visual Studio 'Yu Microsoft/windowsservercore: 10.0.14393.1593 veya buna bağlı herhangi bir görüntüye yükleyemezsiniz. Bu, yükleyiciyi bir kapsayıcıda Başlatan bilinen sorunları içerir. Daha fazla bilgi için bkz. [kapsayıcılar Için bilinen sorunlar](build-tools-container-issues.md).

Aşağıdaki örnek, derleme araçlarının en son sürümünü indirir. Daha sonra bir kapsayıcıya yükleyebileceğiniz derleme araçlarının önceki bir sürümünü kullanmak istiyorsanız, önce bir düzen [oluşturmanız](create-an-offline-installation-of-visual-studio.md) ve [korumanız](update-a-network-installation-of-visual-studio.md) gerekir.

## <a name="install-script"></a>Betiği yükler

Bir Install hatası oluştuğunda günlükleri toplamak için, çalışma dizinine aşağıdaki içeriği içeren "Install. cmd" adlı bir Batch betiği oluşturun:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

Çalışma dizininde, "Dockerfile" öğesini aşağıdaki içerikle oluşturun:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image.
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/runtime:4.8
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 sürüm 15,8 veya önceki bir sürümü (herhangi bir ürün), MCR \. Microsoft \. com \/ Windows \/ ServerCore: 1809 veya üzeri üzerine düzgün şekilde yüklemez. Bir hata görüntülenmiyor.
   >
   > Daha fazla bilgi için bkz. [kapsayıcıların bilinen sorunları](build-tools-container-issues.md) .

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Görüntüyü geçerli çalışma dizininde derlemek için aşağıdaki komutu çalıştırın:

::: moniker range="vs-2017"

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

::: moniker-end

::: moniker range="vs-2019"

```shell
docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
```

::: moniker-end

İsteğe bağlı olarak, `FROM_IMAGE` `CHANNEL_URL` `--build-arg` farklı bir temel görüntü veya sabit bir görüntünün bakımını yapmak için bir iç düzenin konumunu belirtmek üzere komut satırı anahtarını kullanarak ya da her ikisini veya her ikisini de geçirin.

   > [!TIP]
   > İş yükleri ve bileşenlerin listesi için [Visual Studio derleme araçları bileşen dizinine](workload-component-id-vs-build-tools.md)bakın.
   >

## <a name="diagnosing-install-failures"></a>Yüklemesi başarısızlıklarını tanılama

Bu örnek, belirli araçları indirir ve karmaların eşleştiğini doğrular. Ayrıca en son Visual Studio ve .NET günlük toplama yardımcı programını indirir, böylece bir yüklemesi hatası oluşursa, hatayı çözümlemek için günlükleri ana makinenize kopyalayabilirsiniz.

::: moniker range="vs-2017"

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range="vs-2019"

```shell
> docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

Son satır yürütmeyi tamamladıktan sonra makinenizde "% TEMP% \vslogs.zip" öğesini açın veya [Geliştirici topluluğu](https://aka.ms/feedback/suggest?space=8) Web sitesinde bir sorun gönderin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Derleme Araçlarını Bir Kapsayıcıya Yükleme](build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)
