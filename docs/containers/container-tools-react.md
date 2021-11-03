---
title: Visual Studio ASP.NET Core ve React.js kapsayıcı araçları
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Visual Studio kapsayıcı araçları ve docker ile kapsayıcılı React SPA uygulaması oluşturmayı öğrenin
ms.author: ghogen
ms.date: 10/25/2021
ms.technology: vs-container-tools
ms.topic: quickstart
ms.openlocfilehash: 0476cbe027b43e1c9f3be7f26a1b039de3a01319
ms.sourcegitcommit: 141efad8a6a303737bdc563a4f48964411f342eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "131249692"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>hızlı başlangıç: Visual Studio React tek sayfalı bir uygulamayla docker kullanın

Visual Studio ile, React.js tek sayfalı uygulama gibi istemci tarafı JavaScript ve bunları Azure Container Registry, docker Hub 'ı, Azure App Service veya kendi kapsayıcı kayıt defterinizde yayımlamak gibi kapsayıcılı ASP.NET Core uygulamalarını kolayca oluşturabilir, ayıklayabilir ve çalıştırabilirsiniz. Bu makalede, Azure Container Registry yayımlanacak.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Windows kapsayıcılar için, Windows 10 sürüm 1809 veya üzeri için, bu makalede başvurulan docker görüntülerini kullanın.
::: moniker-end
::: moniker range="vs-2019"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 3,1 ile geliştirme için [.net core 3,1 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/3.1) .
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Windows kapsayıcılar için, Windows 10 sürüm 1809 veya üzeri için, bu makalede başvurulan docker görüntülerini kullanın.
::: moniker-end
::: moniker range=">=vs-2022"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2022](https://visualstudio.microsoft.com/vs/preview/)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Windows kapsayıcılar için, Windows 10 sürüm 1809 veya üzeri için, bu makalede başvurulan docker görüntülerini kullanın.

::: moniker-end

## <a name="installation-and-setup"></a>Yükleme ve kurulum

docker yüklemesi için önce docker Desktop 'taki bilgileri gözden geçirin [Windows: yüklemeden önce bilmeniz gerekenler](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Sonra [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)'ı yükler.

## <a name="create-a-project-and-add-docker-support"></a>Proje oluşturun ve Docker desteği ekleyin

::: moniker range="vs-2017"

1. **ASP.NET Core Web uygulaması** şablonunu kullanarak yeni bir proje oluşturun.

1. **React.js** seçin. **Docker desteğini etkinleştir**' i seçemezsiniz ancak endişelenmeyin, projeyi oluşturduktan sonra bu desteği ekleyebilirsiniz.

   ![Yeni React.js projesinin ekran görüntüsü.](media/container-tools-react/vs-2017/new-react-project.png)

1. Proje düğümüne sağ tıklayın ve  > projenize bir dockerfile eklemek için **Docker desteği** Ekle ' yi seçin.

   ![Docker desteği Ekle menü öğesinin ekran görüntüsü.](media/container-tools-react/vs-2017/add-docker-support.png)

1. Kapsayıcı türünü seçin ve **Tamam**' ı tıklatın.
::: moniker-end

::: moniker range="vs-2019"

1. **React.jsşablonuyla ASP.NET Core** kullanarak yeni bir proje oluşturun.

   ![Yeni React.js projesi oluşturma ekranının ekran görüntüsü.](media/container-tools-react/vs-2019/create-reactjs-project.png)

1. **Ek bilgi** ekranında **Docker desteğini etkinleştir**' i seçemezsiniz ancak endişelenmeyin, daha sonra bu desteği ekleyebilirsiniz.

   ![Yeni React.js projesi oluşturma için ekran görüntüsü-ek bilgi ekranı.](media/container-tools-react/vs-2019/new-react-project-additional-information.png)

1. Proje düğümüne sağ tıklayın ve  > projenize bir dockerfile eklemek için **Docker desteği** Ekle ' yi seçin.

   ![Docker desteği Ekle menü öğesinin ekran görüntüsü.](media/container-tools-react/vs-2017/add-docker-support.png)

1. Kapsayıcı türünü seçin.
::: moniker-end
::: moniker range=">=vs-2022"

1. **React.jsşablonuyla ASP.NET Core** kullanarak yeni bir proje oluşturun.

   ![Yeni React.js projesi oluşturma ekranının ekran görüntüsü.](media/container-tools-react/vs-2022/create-reactjs-project.png)

1. **Ek bilgi** ekranında **Docker desteğini etkinleştir**' i seçemezsiniz ancak endişelenmeyin, daha sonra bu desteği ekleyebilirsiniz.

   ![Yeni React.js projesi oluşturma için ekran görüntüsü-ek bilgi ekranı.](media/container-tools-react/vs-2022/react-project-additional-information.png)

1. Proje düğümüne sağ tıklayın ve  > projenize bir dockerfile eklemek için **Docker desteği** Ekle ' yi seçin.

   ![Docker desteği Ekle menü öğesinin ekran görüntüsü.](media/container-tools-react/vs-2022/add-docker-support.png)

1. Kapsayıcı türünü seçin.
:::moniker-end

bir sonraki adım, Linux kapsayıcıları veya Windows kapsayıcıları kullanıp kullanmayacağınızı bağlı olarak farklılık görür.

## <a name="modify-the-dockerfile-linux-containers"></a>Dockerfile 'ı (Linux kapsayıcıları) değiştirme

Bir *Dockerfile*, son bir Docker görüntüsü oluşturmaya yönelik tarif, projede oluşturulur. İçindeki komutları anlamak için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

Projede *Dockerfile dosyasını* açın ve aşağıdaki satırları, kapsayıcıya, Node.js 14. x ve belirli gerekli düğüm kitaplıklarını yüklemek için ekleyin. Düğüm paketi Yöneticisi *npm.exe* yüklemesini temel görüntüye ve bölümüne eklemek için, bu satırları her ikisi de ilk bölüme eklediğinizden emin olun `build` .

```Dockerfile
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y libpng-dev libjpeg-dev curl libxi6 build-essential libgl1-mesa-glx
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs
```

*Dockerfile* artık şuna benzer görünmelidir:

:::moniker range="<=vs-2019"

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y libpng-dev libjpeg-dev curl libxi6 build-essential libgl1-mesa-glx
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y libpng-dev libjpeg-dev curl libxi6 build-essential libgl1-mesa-glx
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["ReactSPA/ReactSPA.csproj", "ReactSPA/"]
RUN dotnet restore "ReactSPA/ReactSPA.csproj"
COPY . .
WORKDIR "/src/ReactSPA"
RUN dotnet build "ReactSPA.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ReactSPA.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ReactSPA.dll"]
```

:::moniker-end
:::moniker range=">=vs-2022"

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y libpng-dev libjpeg-dev curl libxi6 build-essential libgl1-mesa-glx
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y libpng-dev libjpeg-dev curl libxi6 build-essential libgl1-mesa-glx
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["ReactSPA/ReactSPA.csproj", "ReactSPA/"]
RUN dotnet restore "ReactSPA/ReactSPA.csproj"
COPY . .
WORKDIR "/src/ReactSPA"
RUN dotnet build "ReactSPA.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ReactSPA.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ReactSPA.dll"]
```

:::moniker-end

Önceki *Dockerfile* , [MCR.Microsoft.com/DotNet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) görüntüsünü temel alır ve projenizi oluşturup kapsayıcıya ekleyerek temel görüntüyü değiştirmeye yönelik yönergeler içerir.

Yeni proje iletişim kutusunun **https Için Yapılandır** onay kutusu Işaretlendiğinde, *dockerfile* iki bağlantı noktasını kullanıma sunar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) gösterilir.

## <a name="modify-the-dockerfile-windows-containers"></a>dockerfile 'ı (Windows kapsayıcıları) değiştirme

Proje düğümüne çift tıklayarak proje dosyasını açın ve aşağıdaki özelliği öğesinin bir alt öğesi olarak ekleyerek proje dosyasını (*. csproj) güncelleştirin `<PropertyGroup>` :

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Dockerfile dosyasını aşağıdaki satırları ekleyerek güncelleştirin. Bu, düğümü ve NPM 'yi kapsayıcıya kopyalayacak.

   1. ``# escape=` ``Dockerfile 'ın ilk satırına Ekle
   1. Önce aşağıdaki satırları ekleyin `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      ENV NODE_VERSION=14.16.0
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v$($env:NODE_VERSION)/node-v$($env:NODE_VERSION)-win-x64.zip"; `
          Expand-Archive nodejs.zip -DestinationPath C:\; `
          Rename-Item "C:\node-v$($env:NODE_VERSION)-win-x64" c:\nodejs
      ```

   1. Aşağıdaki satırı önce ve sonra ekleyin `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. Tüm Dockerfile artık şuna benzer görünmelidir:

      :::moniker range="<=vs-2019"

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      ENV NODE_VERSION=14.16.0
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v$($env:NODE_VERSION)/node-v$($env:NODE_VERSION)-win-x64.zip"; \
          Expand-Archive nodejs.zip -DestinationPath C:\; \
          Rename-Item "C:\node-v$($env:NODE_VERSION)-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplicationReact1/WebApplicationReact1.csproj", "WebApplicationReact1/"]
      RUN dotnet restore "WebApplicationReact1/WebApplicationReact1.csproj"
      COPY . .
      WORKDIR "/src/WebApplicationReact1"
      RUN dotnet build "WebApplicationReact1.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplicationReact1.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplicationReact1.dll"]
      ```

      :::moniker-end
      :::moniker range=">=vs-2022"
      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      ENV NODE_VERSION=14.16.0
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v$($env:NODE_VERSION)/node-v$($env:NODE_VERSION)-win-x64.zip"; \
          Expand-Archive nodejs.zip -DestinationPath C:\; \
          Rename-Item "C:\node-v$($env:NODE_VERSION)-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:6.0 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:6.0 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplicationReact1/WebApplicationReact1.csproj", "WebApplicationReact1/"]
      RUN dotnet restore "WebApplicationReact1/WebApplicationReact1.csproj"
      COPY . .
      WORKDIR "/src/WebApplicationReact1"
      RUN dotnet build "WebApplicationReact1.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplicationReact1.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplicationReact1.dll"]
      ```

      ::: moniker-end

   1. Öğesini kaldırarak. dockerıgnore dosyasını güncelleştirin `**/bin` .

## <a name="debug"></a>Hata Ayıklama

:::moniker range=">=vs-2022"
Hata ayıklama için varsayılan URL 'YI ayarlayın. Başlat düğmesinin yanındaki açılan menüyü kullanabilir ve **hata ayıklama özellikleri**' ni seçebilirsiniz. **Profili Başlat** iletişim kutusunda, **Docker** ' ı seçin ve daha `/weatherforecast` önce var olan özellikleri eklemek için URL 'yi düzenleyin.
:::moniker-end

Araç çubuğundaki hata ayıklama açılır listesinden **Docker** ' ı seçin ve uygulamada hata ayıklamayı başlatın. Bir sertifikaya güvenmek üzere bir istem içeren bir ileti görebilirsiniz. devam etmek için sertifikaya güvenmeyi seçin.  İlk kez oluşturduğunuzda Docker temel görüntüleri indirir, bu nedenle biraz daha uzun sürebilir.

**Çıkış** penceresinde **kapsayıcı araçları** seçeneği hangi eylemlerin gerçekleştireceğinizi gösterir. *npm.exe* ilişkili yükleme adımlarını görmeniz gerekir.

Tarayıcı, uygulamanın giriş sayfasını gösterir.

   ::: moniker range="vs-2017"
   ![Çalışan uygulamanın ekran görüntüsü.](media/container-tools-react/vs-2017/running-app.png)
   ::: moniker-end
   ::: moniker range="vs-2019"
   ![Çalışan uygulamanın ekran görüntüsü.](media/container-tools-react/vs-2019/running-app.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Çalışan uygulamanın ekran görüntüsü.](media/container-tools-react/vs-2022/running-app.png)
   ::: moniker-end

:::moniker range="<=vs-2019"
*Sayaç* sayfasına gidip **artırma** düğmesine tıklayarak sayaç için istemci tarafı kodunu test edin.

menü **araçları**> NuGet Paket Yöneticisi, **Paket Yöneticisi konsolundan** **Paket Yöneticisi konsolunu** (PMC) açın.

Uygulamanın elde edilen Docker görüntüsü *dev* olarak etiketlendi. Görüntü, *DotNet/Core/ASPNET* temel görüntüsünün *3,1* etiketine dayalıdır. `docker images` **Paket Yöneticisi konsolu** (PMC) penceresinde komutu çalıştırın. Makinedeki görüntüler görüntülenir:

```console
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
webapplicationreact1                   dev                 09be6ec2405d        2 hours ago         352MB
mcr.microsoft.com/dotnet/core/aspnet   3.1                 e3559b2d50bb        10 days ago         207MB
```

> [!NOTE]
> **Geliştirme** görüntüsü, uygulama ikililerini ve diğer içerikleri Içermez. **hata ayıklama** yapılandırmalarında, yinelemeli düzenleme ve hata ayıklama deneyimi sağlamak için birim bağlama kullanılır. Tüm içerikleri içeren bir üretim görüntüsü oluşturmak için **yayın** yapılandırmasını kullanın.

`docker ps`Komutu PMC 'de çalıştırın. Uygulamanın, kapsayıcıyı kullanarak çalıştığını unutmayın:

```console
CONTAINER ID        IMAGE                      COMMAND               CREATED             STATUS              PORTS                                           NAMES
56d1b1008c89        webapplicationreact1:dev   "tail -f /dev/null"   2 hours ago         Up 2 hours          0.0.0.0:32771->80/tcp, 0.0.0.0:32770->443/tcp   WebApplication-ReactSPA
```

:::moniker-end

:::moniker range=">=vs-2022"

**Kapsayıcılar** araç penceresini açın.   >  daha sonra **diğer Windows** kapsayıcıları görüntüle ' nin altındaki menüde bulunabilir  >  veya **Ctrl** + **Q** tuşlarına basabilir ve `containers` arama kutusuna yazmaya başlayabilir, sonra da sonuçlardan **kapsayıcılar** penceresi ' ni seçin. Pencere geldiğinde, düzenleyiciyi düzenleyici bölmesinin altındaki en alta yerleştirin.

**Kapsayıcılar** penceresi, çalışan kapsayıcıları gösterir ve bunlarla ilgili bilgileri görüntülemenize olanak sağlar. Ortam değişkenlerini, etiketleri, bağlantı noktalarını, birimleri, dosya sistemini ve günlükleri görüntüleyebilirsiniz. Araç çubuğu düğmeleri kapsayıcı içinde bir Terminal (kabuk istemi) oluşturmanıza, hata ayıklayıcıyı iliştirmenizi veya kullanılmayan kapsayıcıları ayıklamaya olanak sağlar. Bkz. [kapsayıcılar penceresini kullanma](view-and-diagnose-containers.md).

![Kapsayıcılar penceresinin ekran görüntüsü.](media/container-tools-react/vs-2022/container-tools-window.png)

**Dosyalar** sekmesine tıklayın ve `app` yayımlanan uygulama dosyalarınızı görmek için klasörü genişletin.

Ayrıca, görüntüleri görüntüleyebilir ve bunlarla ilgili bilgileri inceleyebilirsiniz. **Görüntüler** sekmesini seçin, projeniz için bir tane bulun ve ardından bir görüntüyle ilgili bilgileri içeren bir JSON dosyasını görüntülemek için **Ayrıntılar** sekmesini seçin.

![Resimleri ve ayrıntıları gösteren kapsayıcılar penceresinin ekran görüntüsü.](media/container-tools-react/vs-2022/container-tools-window-images-details.png)

> [!NOTE]
> **Geliştirme** görüntüsü, uygulama ikililerini ve diğer içerikleri Içermez. **hata ayıklama** yapılandırmalarında, yinelemeli düzenleme ve hata ayıklama deneyimi sağlamak için birim bağlama kullanılır. Tüm içerikleri içeren bir üretim görüntüsü oluşturmak için **yayın** yapılandırmasını kullanın.

:::moniker-end

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsünü tamamladıktan sonra uygulamanın üretim görüntüsünü oluşturabilirsiniz.

:::moniker range="vs-2017"

1. Yapılandırma açılır öğesini değiştirerek uygulamayı **serbest bırakın** ve oluşturun.
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedefi Yayımla iletişim kutusunda **Container Registry**' yi seçin.
1. **Yeni Azure Container Registry oluştur** ' u seçin ve **Yayımla**' ya tıklayın.
1. **Yeni Azure Container Registry oluştur ' a** istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio Azure Container Registry oluştur iletişim kutusunun ekran görüntüsü.](media/hosting-web-apps-in-docker/vs-azure-container-registry-provisioning-dialog.png)

1. **Oluştur**’u seçin.

   ![Başarılı yayımlama işlemini gösteren ekran görüntüsü.](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range="vs-2019"

1. Yapılandırma açılır öğesini değiştirerek uygulamayı **serbest bırakın** ve oluşturun.
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedefi Yayımla iletişim kutusunda **Docker Container Registry** öğesini seçin.

   ![Docker Container Registry seçin.](media/container-tools-react/vs-2019/publish-dialog1.png)

1. Sonra **Azure Container Registry** öğesini seçin.

   ![Azure Container Registry seçin.](media/container-tools-react/vs-2019/publish-dialog-azure-container-registry.png)

1. **Yeni Azure Container Registry oluştur ' a** tıklayın.
1. **Yeni Azure Container Registry oluştur** ekranında istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio Azure Container Registry oluştur iletişim kutusunun ekran görüntüsü.](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. **Oluştur**' u ve ardından **son**' u seçin.

   ![Seç veya yeni Azure Container Registry oluştur ' u gösteren ekran görüntüsü.](media/container-tools-react/vs-2019/publish-dialog2.png)

   Yayımlama işlemi sona erdiğinde, yayınlama ayarlarını gözden geçirebilir ve gerektiğinde düzenleyebilir veya **Yayımla** düğmesini kullanarak görüntüyü yeniden yayımlayabilirsiniz.

   ![Başarılı yayımlama işlemini gösteren ekran görüntüsü.](media/container-tools-react/vs-2019/publish-finished.png)

   **Yayımla** iletişim kutusunu kullanarak yeniden başlamak için, bu sayfadaki **Sil** bağlantısını kullanarak yayımlama profilini silin ve sonra yeniden **Yayımla** ' yı seçin.
:::moniker-end

:::moniker range=">=vs-2022"

1. Yapılandırma açılır öğesini değiştirerek uygulamayı **serbest bırakın** ve oluşturun.
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedefi Yayımla iletişim kutusunda **Docker Container Registry** öğesini seçin.

   ![Docker Container Registry seçin seçeneğini gösteren ekran görüntüsü.](media/container-tools-react/vs-2022/publish-dialog-1.png)

1. Sonra **Azure Container Registry** öğesini seçin.

   ![Azure Container Registry seçin seçeneğini gösteren ekran görüntüsü.](media/container-tools-react/vs-2022/publish-dialog-azure-container-registry.png)

1. **Yeni Azure Container Registry oluştur ' a** tıklayın.
1. **Yeni Azure Container Registry oluştur** ekranında istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio Azure Container Registry oluştur iletişim kutusunun ekran görüntüsü.](media/container-tools-react/vs-2022/azure-container-registry-details.png)

1. **Oluştur**' u ve ardından **son**' u seçin.

   ![Seç veya yeni Azure Container Registry oluştur ' u gösteren ekran görüntüsü.](media/container-tools-react/vs-2022/publish-dialog-2.png)

   Yayımlama işlemi sona erdiğinde, yayınlama ayarlarını gözden geçirebilir ve gerektiğinde düzenleyebilir veya **Yayımla** düğmesini kullanarak görüntüyü yeniden yayımlayabilirsiniz.

   :::image type="content" alt-text="Başarılı yayımlamayı gösteren ekran görüntüsü" source="media/container-tools-react/vs-2022/publish-succeeded.png" lightbox="media/container-tools-react/vs-2022/publish-succeeded.png":::

   **Yayımla** iletişim kutusunu kullanarak yeniden başlamak için, bu sayfadaki **Sil** bağlantısını kullanarak yayımlama profilini silin ve sonra yeniden **Yayımla** ' yı seçin.
:::moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Artık kapsayıcıyı, kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir konağa çekebilirsiniz, örneğin [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Ek kaynaklar

* [Visual Studio ile kapsayıcı geliştirme](./index.yml)
* [Docker ile Visual Studio geliştirme sorunlarını giderme](troubleshooting-docker-errors.md)
* [Visual Studio kapsayıcı araçları GitHub deposu](https://github.com/Microsoft/DockerTools)

