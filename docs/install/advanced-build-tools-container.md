---
title: Kapsayıcılar için gelişmiş örnek
description: Docker kapsayıcıları için gelişmiş bir örnek hakkında bilgi edinin. Bu örnek Dockerfile, microsoft/dotnet-framework görüntüsünün belirli bir sürüm etiketini kullanır.
ms.custom: SEO-VS-2020
ms.date: 09/21/2021
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4b418277dbac0ba6d61b7c426139f74b62f66f0e
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264197"
---
# <a name="advanced-example-for-containers"></a>Kapsayıcılar için gelişmiş örnek

::: moniker range="vs-2017"

Kapsayıcıya Derleme Araçları [](build-tools-container.md) Yükleme'de örnek Dockerfile her zaman en son microsoft/windowsservercore görüntüsünü ve en son Visual Studio Derleme Araçları yükleyicisini temel alan [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) görüntüsünü kullanır. Bu görüntüyü başkalarının çekmesi için [bir Docker](https://azure.microsoft.com/services/container-registry) kayıt defterine yayımlarsanız, bu görüntü birçok senaryoda uygun olabilir. Ancak uygulamada, hangi temel görüntüyü kullanmakta olduğunu, hangi ikili dosyaları indirtiğiniz ve hangi araç sürümlerini yükleytiğiniz hakkında daha yaygın bir şekilde bilgi edinebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2022"

>[!IMPORTANT]
> Visual Studio 2022 şu anda önizlemededir ve [üretim ortamlarında](https://visualstudio.microsoft.com/license-terms/vs2022-prerelease/) kullanım için lisanslı değildir.

::: moniker-end

::: moniker range=">=vs-2019"

Kapsayıcıya Derleme Araçları [](build-tools-container.md) Yükleme'de örnek Dockerfile her zaman en son microsoft/windowsservercore görüntüsünü ve en son Visual Studio Derleme Araçları yükleyicisini temel alan [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) görüntüsünü kullanır. Bu görüntüyü başkalarının çekmesi için [bir Docker](https://azure.microsoft.com/services/container-registry) kayıt defterine yayımlarsanız, bu görüntü birçok senaryoda uygun olabilir. Ancak uygulamada, hangi temel görüntüyü kullanmakta olduğunu, hangi ikili dosyaları indirtiğiniz ve hangi araç sürümlerini yükleytiğiniz hakkında daha yaygın bir şekilde bilgi edinebilirsiniz.

::: moniker-end

Aşağıdaki örnek Dockerfile, microsoft/dotnet-framework görüntüsünün belirli bir sürüm etiketini kullanır. Temel görüntü için belirli bir etiketin kullanımı yaygın bir durum değildir ve görüntüleri oluşturmanın veya yeniden oluşturmanın her zaman aynı temele sahip olduğunu hatırlamayı kolaylaştırır.

> [!NOTE]
> Microsoft/windowsservercore:10.0.14393.1593'e Visual Studio'ı veya buna dayalı herhangi bir görüntüye yük devredebilirsiniz. Bu görüntüde yükleyiciyi bir kapsayıcıda başlatmayla ilgili bilinen sorunlar vardır. Daha fazla bilgi için [bkz. Kapsayıcılar için bilinen sorunlar.](build-tools-container-issues.md)

Aşağıdaki örnek Derleme Araçları'nın en son sürümünü indirir. Derleme Araçları'nın daha sonra bir kapsayıcıya yükleyebilirsiniz önceki bir sürümünü kullanmak için öncelikle bir [düzen oluşturmanız ve](create-an-offline-installation-of-visual-studio.md) [korumaniz](update-a-network-installation-of-visual-studio.md) gerekir.

## <a name="install-script"></a>Betiği yükleme

Yükleme hatası oluştuğunda günlükleri toplamak için, çalışma dizininde aşağıdaki içeriği içeren "Install.cmd" adlı bir toplu iş betiği oluşturun:

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

Çalışma dizininde aşağıdaki içeriğe sahip "Dockerfile" dosyasını oluşturun:

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

RUN `
    # Download the Build Tools bootstrapper.
    curl -SL --output vs_buildtools.exe https://aka.ms/vs/15/release/vs_buildtools.exe `
    `
    # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
    && (start /w C:\TEMP\Install.cmd vs_buildtools.exe --quiet --wait --norestart --nocache `
        --installPath C:\BuildTools `
        --channelUri C:\TEMP\VisualStudio.chman `
        --installChannelUri C:\TEMP\VisualStudio.chman `
        --add Microsoft.VisualStudio.Workload.AzureBuildTools `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
        --remove Microsoft.VisualStudio.Component.Windows81SDK)
    
    # Cleanup
    && del /q vs_buildtools.exe

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 sürüm 15.8 veya önceki sürümler (herhangi bir ürün), mcr \. microsoft \. com windows \/ \/ servercore:1809 veya sonraki sürümlere düzgün yüklenmez. Hiçbir hata görüntülenmez.
   >
   > Daha [fazla bilgi için bkz. Kapsayıcılar](build-tools-container-issues.md) için bilinen sorunlar.

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

RUN `
    # Download the Build Tools bootstrapper.
    curl -SL --output vs_buildtools.exe https://aka.ms/vs/16/release/vs_buildtools.exe `
    `
    # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
    && (start /w C:\TEMP\Install.cmd vs_buildtools.exe --quiet --wait --norestart --nocache modify `
        --installPath "%ProgramFiles(x86)%\Microsoft Visual Studio\2019\BuildTools" `
        --channelUri C:\TEMP\VisualStudio.chman `
        --installChannelUri C:\TEMP\VisualStudio.chman `
        --add Microsoft.VisualStudio.Workload.AzureBuildTools `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
        --remove Microsoft.VisualStudio.Component.Windows81SDK)
    
    # Cleanup
    && del /q vs_buildtools.exe

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

::: moniker range=">=vs-2022"

>[!IMPORTANT]
> Visual Studio 2022 şu anda önizlemededir ve [üretim ortamlarında](https://visualstudio.microsoft.com/license-terms/vs2022-prerelease/) kullanım için lisanslı değildir.

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
ARG CHANNEL_URL=https://aka.ms/vs/17/preview/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

RUN `
    # Download the Build Tools bootstrapper.
    curl -SL --output vs_buildtools.exe https://aka.ms/vs/17/pre/vs_buildtools.exe `
    `
    # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
    && (start /w C:\TEMP\Install.cmd vs_buildtools.exe --quiet --wait --norestart --nocache modify `
        --installPath "%ProgramFiles(x86)%\Microsoft Visual Studio\2022\BuildTools" `
        --channelUri C:\TEMP\VisualStudio.chman `
        --installChannelUri C:\TEMP\VisualStudio.chman `
        --add Microsoft.VisualStudio.Workload.AzureBuildTools `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
        --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
        --remove Microsoft.VisualStudio.Component.Windows81SDK)
    
    # Cleanup
    && del /q vs_buildtools.exe

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Görüntüyü geçerli çalışma dizininde oluşturmak için aşağıdaki komutu çalıştırın:

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

::: moniker range=">=vs-2022"

```shell
docker build -t buildtools2022:17.0 -t buildtools2022:latest -m 2GB .
```

::: moniker-end

İsteğe bağlı olarak, sabit bir görüntüyü korumak için farklı bir temel görüntü veya iç düzenin konumunu belirtmek için komut satırı anahtarını kullanarak ya da her ikisini ya da `FROM_IMAGE` `CHANNEL_URL` bağımsız `--build-arg` değişkenlerini iletir.

> [!TIP]
> İş yüklerinin ve bileşenlerin listesi için bkz. [Visual Studio Derleme Araçları dizini.](workload-component-id-vs-build-tools.md)
>

## <a name="diagnosing-install-failures"></a>Yükleme hatalarını tanılama

Bu örnek belirli araçları indirir ve karmaların eş olduğunu doğrular. Ayrıca, bir yükleme Visual Studio olması durumunda hataları analiz etmek için günlükleri konak makinenize kopyalamanız için en son Visual Studio ve .NET günlük toplama yardımcı programını indirir.

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

::: moniker range=">=vs-2022"

```shell
> docker build -t buildtools2022:17.0 -t buildtools2022:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

Son satır yürütücü tamam olduktan sonra makinenize "%TEMP%\vslogs.zip" ifadesini açın veya Developer Community web [sitesine bir sorun](https://aka.ms/feedback/suggest?space=8) gönderin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Derleme Araçlarını Bir Kapsayıcıya Yükleme](build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)
