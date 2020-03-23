---
title: Kapsayıcılar için gelişmiş örnek
description: ''
ms.date: 07/03/2019
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b0a88815c4a2853270b539a3e012297b681af62e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114949"
---
# <a name="advanced-example-for-containers"></a>Kapsayıcılar için gelişmiş örnek

::: moniker range="vs-2017"

[Bir kapsayıcı içine Install Build Tools](build-tools-container.md) örnek Dockerfile her zaman [microsoft/ dotnet-framework kullanır:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) görüntü en son microsoft / windowsservercore görüntü ve en son Visual Studio Build Tools yükleyici dayalı. Bu görüntüyü başkalarının çekmesi için Docker [kayıt defterine](https://azure.microsoft.com/services/container-registry) yayınlarsanız, bu görüntü birçok senaryo için uygun olabilir. Ancak, uygulamada hangi temel görüntüyü kullandığınız, hangi ikili leri indirdiğiniz ve hangi araç sürümlerini yüklediğiniz hakkında daha belirgin olmak daha yaygındır.

::: moniker-end

::: moniker range="vs-2019"

[Bir kapsayıcı içine Install Build Tools](build-tools-container.md) örnek Dockerfile her zaman microsoft / [dotnet-framework kullanır:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) görüntü en son microsoft / windowsservercore görüntü ve en son Visual Studio Build Tools yükleyici dayalı. Bu görüntüyü başkalarının çekmesi için Docker [kayıt defterine](https://azure.microsoft.com/services/container-registry) yayınlarsanız, bu görüntü birçok senaryo için uygun olabilir. Ancak, uygulamada hangi temel görüntüyü kullandığınız, hangi ikili leri indirdiğiniz ve hangi araç sürümlerini yüklediğiniz hakkında daha belirgin olmak daha yaygındır.

::: moniker-end

Aşağıdaki örnek Dockerfile, microsoft/dotnet framework görüntüsünün belirli bir sürüm etiketini kullanır. Temel görüntü için belirli bir etiket kullanmak olağandır ve görüntüleri oluşturmanın veya yeniden oluşturmanın her zaman aynı temele sahip olduğunu hatırlamayı kolaylaştırır.

> [!NOTE]
> Visual Studio'yu microsoft/windowsservercore:10.0.14393.1593 veya yüklücvericiyi bir kapsayıcıda başlatırken sorun çıkaran herhangi bir görüntüye yükleyemezsiniz. Daha fazla bilgi [için, kapsayıcılar için bilinen sorunlara](build-tools-container-issues.md)bakın.

Aşağıdaki örnek, Yapı Araçları'nın en son sürümünden indirilir. Daha sonra bir kapsayıcıya yükleyebileceğiniz Yapı Araçları'nın önceki bir sürümünü kullanmak istiyorsanız, önce bir düzen [oluşturmanız](create-an-offline-installation-of-visual-studio.md) ve [korumanız](update-a-network-installation-of-visual-studio.md) gerekir.

## <a name="install-script"></a>Komut dosyalarını yükleme

Yükleme hatası oluştuğunda günlükleri toplamak için, çalışma dizininde aşağıdaki içeriği içeren "Install.cmd" adlı bir toplu iş komut dosyası oluşturun:

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

## <a name="dockerfile"></a>Dockerdosyası

Çalışma dizininde, aşağıdaki içeriği içeren "Dockerfile"ı oluşturun:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:3eaa3ba18f45e6561f32d8dd927045413f1dd043d7d29fb581f5cb3c6f7d7481
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 sürüm 15.8 veya daha önceki (herhangi\.bir\.\/ürün) mcr microsoft com windows\/servercore:1809 veya daha sonra düzgün yüklenmez. Hata görüntülenmez.
   >
   > Daha fazla bilgi [için kapsayıcılar için bilinen sorunlara](build-tools-container-issues.md) bakın.

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
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

İsteğe bağlı olarak, `CHANNEL_URL` sabit `--build-arg` bir görüntüyü korumak için farklı bir temel görüntü veya dahili düzenin konumunu belirtmek için komut satırı anahtarını kullanarak bağımsız değişkenlerden birini veya her ikisini `FROM_IMAGE` de geçirin.

## <a name="diagnosing-install-failures"></a>Yükleme hatalarının tanılanması

Bu örnek, belirli araçları karşıdan yükler ve karların eşleşeceğini doğrular. Ayrıca en son Visual Studio ve .NET günlük toplama yardımcı programını indirir, böylece yükleme hatası oluşursa, hatayı çözümlemek için günlükleri ana makinenize kopyalayabilirsiniz.

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

Son satır yürütmeyi tamamladıktan sonra, makinenizde "%TEMP%\vslogs.zip" açın veya [Geliştirici Topluluğu](https://developercommunity.visualstudio.com) web sitesinde bir sorun gönderin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Derleme Araçlarını Bir Kapsayıcıya Yükleme](build-tools-container.md)
* [Kapsayıcılar için Bilinen Sorunlar](build-tools-container-issues.md)
* [Visual Studio Build Tools iş yükü ve bileşen ilikleri](workload-component-id-vs-build-tools.md)
