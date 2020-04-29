---
title: ASP.NET Core ve tepki verme. js ile Visual Studio kapsayıcı araçları
author: ghogen
description: Visual Studio kapsayıcı araçları 'nı ve Docker for Windows kullanmayı öğrenin
ms.author: ghogen
ms.date: 10/16/2019
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 47bcdd4de4ffd938d6b9aed5a166a863873f526b
ms.sourcegitcommit: ddd99f64a3f86508892a6d61e8a33c88fb911cc4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82255551"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Hızlı başlangıç: Visual Studio 'da bir tepki verme tek sayfalı uygulamayla Docker kullanma

Visual Studio ile, yanıt verme. js tek sayfalı uygulama gibi istemci tarafı JavaScript ve bunları Azure Container Registry (ACR), Docker Hub 'ı Azure App Service ya da kendi kapsayıcı kayıt defterinizde yayımlamak gibi Kapsayıcılı ASP.NET Core uygulamalarını kolayca oluşturabilir, ayıklayabilir ve çalıştırabilirsiniz. Bu makalede ACR 'ye yayımlanacak.

## <a name="prerequisites"></a>Ön koşullar

::: moniker range="vs-2017"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** iş yükü ve/veya **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Windows kapsayıcıları, Windows 10 sürüm 1903 veya üzeri için, bu makalede başvurulan Docker görüntülerini kullanmak için.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** iş yükü ve/veya **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 2,2 ile geliştirme için [.net core 2,2 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Windows kapsayıcıları, Windows 10 sürüm 1903 veya üzeri için, bu makalede başvurulan Docker görüntülerini kullanmak için.
::: moniker-end

## <a name="installation-and-setup"></a>Yükleme ve kurulum

Docker yüklemesi için ilk olarak [Windows Için Docker Desktop](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)'taki bilgileri gözden geçirin: yüklemeden önce bilmeniz gerekenler. Sonra [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)'ı yükler.

## <a name="create-a-project-and-add-docker-support"></a>Proje oluşturun ve Docker desteği ekleyin

::: moniker range="vs-2017"
1. **ASP.NET Core Web uygulaması** şablonunu kullanarak yeni bir proje oluşturun.
1. **Tepki verme. js**' yi seçin. **Docker desteğini etkinleştir**' i seçemezsiniz ancak endişelenmeyin, projeyi oluşturduktan sonra bu desteği ekleyebilirsiniz.

   ![Yeni tepki verme. js projesinin ekran görüntüsü](media/container-tools-react/vs2017/new-react-project.png)

1. Proje düğümüne sağ tıklayın ve projenize bir dockerfile eklemek için **Docker desteği** **Ekle** > ' yi seçin.

   ![Docker desteği ekleme](media/container-tools-react/vs2017/add-docker-support.png)

1. Kapsayıcı türünü seçin ve **Tamam**' ı tıklatın.
::: moniker-end
::: moniker range=">=vs-2019"
1. **ASP.NET Core Web uygulaması** şablonunu kullanarak yeni bir proje oluşturun.
1. **Tepki verme. js**' yi seçin ve **Oluştur**' a tıklayın. **Docker desteğini etkinleştir**' i seçemezsiniz ancak endişelenmeyin, daha sonra bu desteği ekleyebilirsiniz.

   ![Yeni tepki verme. js projesinin ekran görüntüsü](media/container-tools-react/vs2019/new-react-project.png)

1. Proje düğümüne sağ tıklayın ve projenize bir dockerfile eklemek için **Docker desteği** **Ekle** > ' yi seçin.

   ![Docker desteği ekleme](media/container-tools-react/vs2017/add-docker-support.png)

1. Kapsayıcı türünü seçin.
::: moniker-end

Bir sonraki adım, Linux kapsayıcıları veya Windows kapsayıcıları kullanıyor olmanıza bağlı olarak farklılık görür.

## <a name="modify-the-dockerfile-linux-containers"></a>Dockerfile 'ı (Linux kapsayıcıları) değiştirme

Bir *Dockerfile*, son bir Docker görüntüsü oluşturmaya yönelik tarif, projede oluşturulur. İçindeki komutları anlamak için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

Projede *Dockerfile dosyasını* açın ve kapsayıcıda Node. js 10. x yüklemek için aşağıdaki satırları ekleyin. Düğüm paketi Yöneticisi *NPM. exe* ' nin yüklemesini sonraki adımlarda kullanılan temel görüntüye eklemek için ilk bölüme bu satırları eklediğinizden emin olun.

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Dockerfile* artık şuna benzer görünmelidir:

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

Yukarıdaki *Dockerfile* , [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel alır ve projenizi oluşturup kapsayıcıya ekleyerek temel görüntüyü değiştirmeye yönelik yönergeler içerir.

Yeni proje iletişim kutusunun **https Için Yapılandır** onay kutusu Işaretlendiğinde, *dockerfile* iki bağlantı noktasını kullanıma sunar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) gösterilir.

## <a name="modify-the-dockerfile-windows-containers"></a>Dockerfile 'ı (Windows kapsayıcıları) değiştirme

Proje düğümüne çift tıklayarak proje dosyasını açın ve aşağıdaki özelliği `<PropertyGroup>` öğesinin bir alt öğesi olarak ekleyerek proje dosyasını (*. csproj) güncelleştirin:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Dockerfile dosyasını aşağıdaki satırları ekleyerek güncelleştirin. Bu, düğümü ve NPM 'yi kapsayıcıya kopyalayacak.

   1. Dockerfile 'ın ilk satırına Ekle ``# escape=` ``
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

   1. Tüm Dockerfile artık şuna benzer görünmelidir:

      ```
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

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

1. Öğesini kaldırarak. dockerıgnore dosyasını güncelleştirin `**/bin`.

## <a name="debug"></a>Hata ayıklama

Araç çubuğundaki hata ayıklama açılır listesinden **Docker** ' ı seçin ve uygulamada hata ayıklamayı başlatın. Bir sertifikaya güvenmek üzere bir istem içeren bir ileti görebilirsiniz. devam etmek için sertifikaya güvenmeyi seçin.  İlk kez oluşturduğunuzda Docker temel görüntüleri indirir, bu nedenle biraz daha uzun sürebilir.

**Çıkış** penceresinde **kapsayıcı araçları** seçeneği hangi eylemlerin gerçekleştireceğinizi gösterir. *NPM. exe*ile ilişkili yükleme adımlarını görmeniz gerekir.

Tarayıcı, uygulamanın giriş sayfasını gösterir.

::: moniker range="vs-2017"
   ![Çalışan uygulamanın ekran görüntüsü](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Çalışan uygulamanın ekran görüntüsü](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

*Sayaç* sayfasına gidip **artırma** düğmesine tıklayarak sayaç için istemci tarafı kodunu test edin.

Menü **araçları**> NuGet Paket Yöneticisi, **Paket Yöneticisi konsolu**' ndan **Paket Yöneticisi konsolu 'nu** (PMC) açın.

Uygulamanın elde edilen Docker görüntüsü *dev*olarak etiketlendi. Görüntü, *Microsoft/DotNet* temel görüntüsünün *2,2-aspnetcore-Runtime* etiketine dayalıdır. `docker images` Komutunu **Paket Yöneticisi konsolu** (PMC) penceresinde çalıştırın. Makinedeki görüntüler görüntülenir:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Geliştirme** görüntüsü, uygulama ikililerini ve diğer içerikleri Içermez. **hata ayıklama** yapılandırmalarında, yinelemeli düzenleme ve hata ayıklama deneyimi sağlamak için birim bağlama kullanılır. Tüm içerikleri içeren bir üretim görüntüsü oluşturmak için **yayın** yapılandırmasını kullanın.

`docker ps` Komutu PMC 'de çalıştırın. Uygulamanın, kapsayıcıyı kullanarak çalıştığını unutmayın:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsünü tamamladıktan sonra uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılır öğesini değiştirerek uygulamayı **serbest bırakın** ve oluşturun.
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedefi Yayımla iletişim kutusunda **Container Registry** sekmesini seçin.
1. **Yeni Azure Container Registry oluştur** ' u seçin ve **Yayımla**' ya tıklayın.
1. **Yeni Azure Container Registry oluştur ' a**istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[ISTEYIN](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio 'nun Azure Container Registry oluştur iletişim kutusu][0]

1. **Oluştur**' a tıklayın.

   ![Başarılı yayımlamayı gösteren ekran görüntüsü](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Sonraki adımlar

Artık kapsayıcıyı, kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir konağa çekebilirsiniz, örneğin [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Ek kaynaklar

* [Visual Studio ile kapsayıcı geliştirme](/visualstudio/containers)
* [Docker ile Visual Studio geliştirme sorunlarını giderme](troubleshooting-docker-errors.md)
* [Visual Studio kapsayıcı araçları GitHub deposu](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end