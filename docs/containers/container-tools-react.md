---
title: ASP.NET Core ve React.js ile Visual Studio Konteyner Araçları
author: ghogen
description: Windows için Visual Studio Konteyner Araçlarını ve Docker'ı nasıl kullanacağınızı öğrenin
ms.author: ghogen
ms.date: 10/16/2019
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: af859c1c06820aa477869f6968e9c652bd525de6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75916743"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Quickstart: Visual Studio'da Tek Sayfalık Tepki Uygulamasıyla Docker'ı Kullanın

Visual Studio ile, React.js tek sayfalı uygulama gibi istemci tarafındaki JavaScript uygulamaları da dahil olmak üzere konteynerASP.NET Core uygulamaları kolayca oluşturabilir, hata ayıklayabilir ve çalıştırabilir ve bunları Azure Konteyner Kayıt Defteri (ACR), Docker Hub, Azure Uygulama Hizmeti veya kendi uygulamalarınızda yayınlayabilirsiniz konteyner kayıt defteri. Bu makalede, ACR'de yayınlayacağız.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Web **Geliştirme,** **Azure Araçları** iş yükü ve/veya **.NET Core çapraz platform geliştirme** iş yükü yüklü
* Azure Kapsayıcı Kayıt Defteri'nde yayımlamak için bir Azure aboneliği. [Ücretsiz deneme sürümü için kaydolun.](https://azure.microsoft.com/offers/ms-azr-0044p/)
* [Node.js](https://nodejs.org/en/download/)
* Windows kapsayıcıları için, Windows 10 sürüm 1903 veya daha sonraki, bu makalede başvurulan Docker görüntüleri kullanmak için.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) Web **Geliştirme,** **Azure Araçları** iş yükü ve/veya **.NET Core çapraz platform geliştirme** iş yükü yüklü
* [.NET Core 2.2 Geliştirme Araçları](https://dotnet.microsoft.com/download/dotnet-core/2.2) .NET Core 2.2 ile
* Azure Kapsayıcı Kayıt Defteri'nde yayımlamak için bir Azure aboneliği. [Ücretsiz deneme sürümü için kaydolun.](https://azure.microsoft.com/offers/ms-azr-0044p/)
* [Node.js](https://nodejs.org/en/download/)
* Windows kapsayıcıları için, Windows 10 sürüm 1903 veya daha sonraki, bu makalede başvurulan Docker görüntüleri kullanmak için.
::: moniker-end

## <a name="installation-and-setup"></a>Kurulum ve kurulum

Docker yüklemesi için, windows için Docker Desktop'daki bilgileri ilk olarak gözden [geçirin: Yüklemeden önce bilinmesi gerekenler.](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) Ardından, [Docker Desktop'ı](https://hub.docker.com/editions/community/docker-ce-desktop-windows)yükleyin.

## <a name="create-a-project-and-add-docker-support"></a>Proje oluşturun ve Docker desteği ekleyin

::: moniker range="vs-2017"
1. ASP.NET Çekirdek Web **Uygulaması** şablonu kullanarak yeni bir proje oluşturun.
1. **React.js'yi**seçin. **Docker Desteğini Etkinleştir'i**seçemezsiniz, ancak endişelenmeyin, projeyi oluşturduktan sonra bu desteği ekleyebilirsiniz.

   ![Yeni React.js projesinin ekran görüntüsü](media/container-tools-react/vs2017/new-react-project.png)

1. Proje düğümüne sağ tıklayın ve projenize Docker dosyası eklemek için **Docker Desteği** **Ekle'yi** > seçin.

   ![Docker desteği ekleme](media/container-tools-react/vs2017/add-docker-support.png)

1. Kapsayıcı türünü seçin ve **Tamam'ı**tıklatın.
::: moniker-end
::: moniker range=">=vs-2019"
1. ASP.NET Çekirdek Web **Uygulaması** şablonu kullanarak yeni bir proje oluşturun.
1. **React.js'yi**seçin ve **Oluştur'u**tıklatın. **Docker Desteğini Etkinleştir'i**seçemezsiniz, ancak endişelenmeyin, bu desteği daha sonra ekleyebilirsiniz.

   ![Yeni React.js projesinin ekran görüntüsü](media/container-tools-react/vs2019/new-react-project.png)

1. Proje düğümüne sağ tıklayın ve projenize Docker dosyası eklemek için **Docker Desteği** **Ekle'yi** > seçin.

   ![Docker desteği ekleme](media/container-tools-react/vs2017/add-docker-support.png)

1. Kapsayıcı türünü seçin.
::: moniker-end

Bir sonraki adım, Linux kapsayıcıları veya Windows kapsayıcıları kullanıyorsanız bağlı olarak farklıdır.

## <a name="modify-the-dockerfile-linux-containers"></a>Dockerfile'ı değiştirin (Linux kapsayıcıları)

Bir *Dockerfile*, son docker görüntü oluşturmak için tarifi, projeoluşturulur. İçindeki komutların anlaşılması için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

Projede *Dockerfile'ı* açın ve konteynıra Düğüm.js 10.x yüklemek için aşağıdaki satırları ekleyin. Sonraki adımlarda kullanılan temel görüntüye Düğüm paket yöneticisi *npm.exe* yüklemeeklemek için, ilk bölümde bu satırları eklemek için emin olun.

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Dockerfile* şimdi böyle bir şey bakmak gerekir:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

Önceki *Dockerfile* [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) resmine dayanır ve projenizi oluşturarak ve kapsayıcıya ekleyerek temel görüntüyü değiştirmek için yönergeler içerir.

Yeni proje iletişim kutusunun HTTPS için **Yapılandırma** onay kutusu işaretlendiğinde, *Dockerfile* iki bağlantı noktasını ortaya çıkarır. Bir bağlantı noktası HTTP trafiği için kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretlenmezse, HTTP trafiği için tek bir bağlantı noktası (80) açığa çıkarır.

## <a name="modify-the-dockerfile-windows-containers"></a>Dockerfile'ı değiştirme (Windows kapsayıcıları)

Proje düğümüne çift tıklayarak proje dosyasını açın ve öğenin alt öğesi olarak aşağıdaki özelliği ekleyerek proje dosyasını `<PropertyGroup>` (*.csproj) güncelleştirin:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Aşağıdaki satırları ekleyerek Dockerfile'ı güncelleştirin. Bu, düğümü ve npm'yi kapsayıcıya kopyalar.

   1. Dockerfile'ın ilk satırına ekleme ``# escape=` ``
   1. Önce aşağıdaki satırları ekleyin`FROM … base`

      ```
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. Aşağıdaki satırı önce ve sonra ekleyin`FROM … build`

      ```
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. Tam Dockerfile şimdi bu gibi bir şey bakmak gerekir:

      ```
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      RUN Expand-Archive nodejs.zip -DestinationPath C:\; `
      RUN Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplication7/WebApplication37.csproj", "WebApplication37/"]
      RUN dotnet restore "WebApplication7/WebApplication7.csproj"
      COPY . .
      WORKDIR "/src/WebApplication37"
      RUN dotnet build "WebApplication37.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplication37.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplication37.dll"]
      ```

1. .dockerignore dosyasını kaldırarak `**/bin`güncelleştirin.

## <a name="debug"></a>Hata ayıklama

Araç çubuğundaki hata ayıklama açılır tarihinden **Docker'ı** seçin ve uygulamayı hata ayıklamaya başlayın. Bir sertifikaya güvenme yle ilgili bir istem içeren bir ileti görebilirsiniz; devam edecek sertifikaya güvenmeyi seçin.  İlk oluşturduğunuzda, docker temel görüntüleri indirir, bu nedenle biraz daha uzun sürebilir.

**Çıktı** penceresindeki **Kapsayıcı Araçları** seçeneği, hangi eylemlerin gerçekleştiğini gösterir. *Npm.exe*ile ilişkili yükleme adımlarını görmeniz gerekir.

Tarayıcı, uygulamanın ana sayfasını gösterir.

::: moniker range="vs-2017"
   ![Çalışan uygulamanın ekran görüntüsü](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Çalışan uygulamanın ekran görüntüsü](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

*Sayaç* sayfasına gezinmeyi deneyin ve Artış düğmesini tıklatarak sayaç için istemci tarafı kodunu test **edin.**

Paket **Yöneticisi Konsolu** 'nuGet Package Manager, Package Manager Console> **menüden** Paket **Yöneticisi Konsolu'nu**(PMC) açın.

Uygulamanın ortaya çıkan Docker görüntüsü *dev*olarak etiketlenir. Görüntü, *microsoft/dotnet* taban görüntüsünün *2.2-aspnetcore-runtime* etiketine dayanmaktadır. Paketi `docker images` **Yöneticisi Konsolu** (PMC) penceresinde komutu çalıştırın. Makinedeki görüntüler görüntülenir:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Hata ayıklama** yapılandırmaları yinelemeli düzenleme ve hata ayıklama deneyimini sağlamak için ses montajını kullandığından, **dev** görüntüsü uygulama ikililerini ve diğer içerikleri içermez. Tüm içerikleri içeren bir üretim görüntüsü oluşturmak için **Release** yapılandırmasını kullanın.

PMC'de komutu çalıştırın. `docker ps` Uygulamanın kapsayıcıyı kullanarak çalıştığını fark edin:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>Docker resimlerini yayımla

Uygulamanın geliştirme ve hata ayıklama döngüsü tamamlandıktan sonra, uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılır düşüşünü **Release** olarak değiştirin ve uygulamayı oluşturun.
1. **Çözüm Gezgini'nde** projenize sağ tıklayın ve **Yayımla'yı**seçin.
1. Yayımlama hedef iletişim **kutusunda, Kapsayıcı Kayıt Defteri** sekmesini seçin.
1. **Yeni Azure Kapsayıcı Kayıt Defteri Oluştur'u** seçin ve **Yayımla'yı**tıklatın.
1. **Yeni bir Azure Kapsayıcı Kayıt Defteri Oluştur'da**istediğiniz değerleri doldurun.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Konteyner kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizi oluşturacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | Standart | Konteyner kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya konteyner kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir Konum seçin. |

    ![Visual Studio's oluşturmak Azure Konteyner Kayıt Defteri iletişim kutusu][0]

1. **Oluştur'u**tıklatın.

   ![Başarılı yayımlamayı gösteren ekran görüntüsü](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Sonraki adımlar

Artık kapsayıcıyı kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir ana bilgisayara çekebilirsiniz (örneğin [Azure Kapsayıcı Örnekleri).](/azure/container-instances/container-instances-tutorial-deploy-app)

## <a name="additional-resources"></a>Ek kaynaklar

* [Visual Studio ile konteyner geliştirme](/visualstudio/containers)
* [Docker ile Visual Studio geliştirme sorunlarını giderme](troubleshooting-docker-errors.md)
* [Görsel Stüdyo Konteyner Araçları GitHub deposu](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end