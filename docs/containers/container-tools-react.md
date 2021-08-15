---
title: Visual Studio ASP.NET Core ve React.js ile Kapsayıcı Araçları
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Visual Studio Container Tools ve Docker ile kapsayıcılı bir React SPA uygulaması oluşturma
ms.author: ghogen
ms.date: 02/21/2021
ms.technology: vs-container-tools
ms.topic: quickstart
ms.openlocfilehash: c009686029355fdb5c9e1d371a4d0a071bec2fc282d5fbc441bd099d52b89dba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121348444"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Hızlı Başlangıç: Docker'ı React tek sayfalı bir uygulamayla Visual Studio

Visual Studio ile, React.js tek sayfalı uygulama gibi istemci tarafı JavaScript'e sahip olanlar da dahil olmak üzere kapsayıcılı ASP.NET Core uygulamalarını kolayca derleme, hata ayıklama ve çalıştırmanın yanı sıra bunları Azure Container Registry (ACR), Docker Hub, Azure App Service veya kendi kapsayıcı kayıt defterinize yayımlayabilirsiniz. Bu makalede, ACR'de yayımlayız.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET Core** platformlar arası geliştirme iş yükünün yüklü olduğu [2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sürümü
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme sürümüne kaydolma.](https://azure.microsoft.com/offers/ms-azr-0044p/)
* [Node.js](https://nodejs.org/en/download/)
* Bu Windows docker görüntülerini Windows 10 için 1809 veya sonraki bir sürümü kullanın.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET Core** platformlar arası geliştirme iş yükünün yüklü olduğu [2019](https://visualstudio.microsoft.com/downloads) sürümü
* [.NET Core 3.1 ile geliştirme](https://dotnet.microsoft.com/download/dotnet-core/3.1) için .NET Core 3.1 Geliştirme Araçları.
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme sürümüne kaydolma.](https://azure.microsoft.com/offers/ms-azr-0044p/)
* [Node.js](https://nodejs.org/en/download/)
* Bu Windows docker görüntülerini Windows 10 için 1809 veya sonraki bir sürümü kullanın.
::: moniker-end

## <a name="installation-and-setup"></a>Yükleme ve kurulum

Docker yüklemesi için önce [Docker Desktop for Windows: Yüklemeden önce neleri bilmek gerekir? bağlantısına bakın.](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) Ardından [Docker Desktop'ı yükleyin.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="create-a-project-and-add-docker-support"></a>Proje oluşturma ve Docker desteği ekleme

::: moniker range="vs-2017"
1. ASP.NET Core Web Uygulaması **şablonunu kullanarak yeni bir proje** oluşturun.
1. Öğesini **React.js.** Docker Desteğini **Etkinleştir'i** seçesiniz, ancak endişelenmeyin, projeyi oluşturduk sonra bu desteği ekleyin.

   ![Yeni React.js görüntüsü](media/container-tools-react/vs-2017/new-react-project.png)

1. Proje düğümüne sağ tıklayın ve  Projenize > **dockerfile eklemek** için Docker Desteği Ekle'yi seçin.

   ![Docker desteği ekleme](media/container-tools-react/vs-2017/add-docker-support.png)

1. Kapsayıcı türünü seçin ve Tamam'a **tıklayın.**
::: moniker-end

::: moniker range=">=vs-2019"

1. ASP.NET Core **şablonuyla React.jsproje** oluşturun.

   ![Yeni bir React.js oluşturma ekran görüntüsü](media/container-tools-react/vs-2019/create-reactjs-project.png)

1. Ek **bilgiler ekranında** Docker Desteğini Etkinleştir'i seçesiniz, ancak endişelenmeyin, bu desteği daha sonra ekebilirsiniz. 

   ![Yeni bir React.js projesi oluşturma ekran görüntüsü - Ek bilgi ekranı](media/container-tools-react/vs-2019/new-react-project-additional-information.png)

1. Proje düğümüne sağ tıklayın ve  Projenize > **dockerfile eklemek** için Docker Desteği Ekle'yi seçin.

   ![Docker desteği ekleme](media/container-tools-react/vs-2017/add-docker-support.png)

1. Kapsayıcı türünü seçin.
::: moniker-end

Sonraki adım, Linux kapsayıcıları mı yoksa linux kapsayıcıları mı kullandığınıza bağlı olarak Windows farklıdır.

## <a name="modify-the-dockerfile-linux-containers"></a>Dockerfile'ı değiştirme (Linux kapsayıcıları)

Projede son bir Docker görüntüsü oluşturma tarifi olan *Dockerfile* oluşturulur. Içindeki komutları [anlamak için Dockerfile](https://docs.docker.com/engine/reference/builder/) başvurusuna bakın.

Projede *Dockerfile dosyasını* açın ve kapsayıcıya 10.x Node.js aşağıdaki satırları ekleyin. Hem temel görüntüye hem de bölümüne Node paket yöneticisinin yüklemesini *eklemeknpm.exe* bu satırları ilk bölüme de eklemeniz `build` gerekir.

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Dockerfile şimdi* aşağıdakine benzer şekilde görünüyor:

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication-ReactSPA/WebApplication-ReactSPA.csproj", "WebApplication-ReactSPA/"]
RUN dotnet restore "WebApplication-ReactSPA/WebApplication-ReactSPA.csproj"
COPY . .
WORKDIR "/src/WebApplication-ReactSPA"
RUN dotnet build "WebApplication-ReactSPA.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-ReactSPA.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-ReactSPA.dll"]
```

Yukarıdaki *Dockerfile,* mcr.microsoft.com/dotnet/core/aspnet [](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) görüntüsünü temel almaktadır ve projenizi oluşturma ve kapsayıcıya ekleyerek temel görüntüyü değiştirme yönergelerini içerir.

Yeni proje iletişim kutusunun HTTPS için **yapılandır** onay kutusu işaretli olduğunda *Dockerfile iki bağlantı* noktasını kullanıma sağlar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) kullanıma hazır olur.

## <a name="modify-the-dockerfile-windows-containers"></a>Dockerfile'ı değiştirme (Windows kapsayıcıları)

Proje düğümüne çift tıklayarak proje dosyasını açın ve aşağıdaki özelliği öğenin alt öğesi olarak ekleyerek proje dosyasını (*.csproj) `<PropertyGroup>` güncelleştirin:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Aşağıdaki satırları ekleyerek Dockerfile dosyasını güncelleştirin. Bu, node ve npm'yi kapsayıcıya kopyalar.

   1. ``# escape=` ``Dockerfile dosyasının ilk satırına ekleyin
   1. Önce aşağıdaki satırları ekleyin `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   2. Önce ve sonra aşağıdaki satırı ekleyin `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   3. Dockerfile dosyasının tam olarak şöyle olması gerekir:

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

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

   4. .dockerignore dosyasını kaldırarak `**/bin` güncelleştirin.

## <a name="debug"></a>Hata Ayıklama

Araç çubuğundaki hata ayıklama açılan **menüsünden Docker'ı** seçin ve uygulamada hata ayıklamaya başlayabilirsiniz. Bir sertifikaya güvenme hakkında bir istem ile bir ileti alabilirsiniz; devam etmek için sertifikaya güvenmeyi seçin.  docker, ilk kez temel görüntüleri indirdiği için biraz daha uzun sürebilir.

Çıkış **penceresindeki** Kapsayıcı **Araçları seçeneği** hangi eylemlerin gerçekleştir olduğunu gösterir. ile ilişkili yükleme adımlarını *npm.exe.*

Tarayıcı, uygulamanın giriş sayfasını gösterir.

::: moniker range="vs-2017"
   ![Çalışan uygulamanın ekran görüntüsü](media/container-tools-react/vs-2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Çalışan uygulamanın ekran görüntüsü](media/container-tools-react/vs-2019/running-app.png)
::: moniker-end

Sayaç sayfasına gidin ve *Artır* düğmesine tıklayarak sayaç için istemci tarafı kodunu test **edin.**

**Konsol'Paket Yöneticisi Araçlar** menüsünden> NuGet Paket Yöneticisi **Konsolu'nu** (PMC) **Paket Yöneticisi açın.**

Uygulamanın sonuçta elde edilen Docker görüntüsü geliştirme olarak *etiketlenir.* Görüntü, *dotnet/core/aspnet* temel görüntüsünün *3.1* etiketine dayalıdır. Paket Yöneticisi `docker images` **Console** (PMC) penceresinde komutunu çalıştırın. Makinede görüntüler görüntülenir:

```console
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
webapplicationreact1                   dev                 09be6ec2405d        2 hours ago         352MB
mcr.microsoft.com/dotnet/core/aspnet   3.1                 e3559b2d50bb        10 days ago         207MB
```

> [!NOTE]
> Geliştirme **görüntüsü** uygulama ikililerini ve diğer içeriği içermez çünkü **Hata** ayıklama yapılandırmaları, birim bağlamayı kullanarak yeniden düzenleme ve hata ayıklama deneyimi sağlar. Tüm içerikleri içeren bir üretim görüntüsü oluşturmak için Yayın **yapılandırmasını** kullanın.

`docker ps`PMC'de komutunu çalıştırın. Uygulamanın kapsayıcıyı kullanarak çalıştır):

```console
CONTAINER ID        IMAGE                      COMMAND               CREATED             STATUS              PORTS                                           NAMES
56d1b1008c89        webapplicationreact1:dev   "tail -f /dev/null"   2 hours ago         Up 2 hours          0.0.0.0:32771->80/tcp, 0.0.0.0:32770->443/tcp   WebApplication-React1
```

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsü tamamlandıktan sonra, uygulamanın üretim görüntüsünü oluşturabilirsiniz.

:::moniker range="vs-2017"

1. Yapılandırma açılan listesinde Yayın'a **ve** uygulamayı derlemeye devam edin.
1. Içinde projenize sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**
1. Hedefi yayımla iletişim kutusunda **Container Registry.**
1. Yeni **Oluştur'u Azure Container Registry** yayımla'ya **tıklayın.**
1. Create a new Azure Container Registry ( yeni bir **oluştur) içinde istediğiniz Azure Container Registry.**

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio Azure Container Registry oluştur iletişim kutusu](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

1. **Oluştur**’u seçin.

   ![Başarılı yayımlamayı gösteren ekran görüntüsü](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range=">=vs-2019"

1. Yapılandırma açılır öğesini değiştirerek uygulamayı **serbest bırakın** ve oluşturun.
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedefi Yayımla iletişim kutusunda **Docker Container Registry** öğesini seçin.

   ![Docker Container Registry seçin](media/container-tools-react/vs-2019/publish-dialog1.png)

1. Sonra **Azure Container Registry** öğesini seçin.

   ![Azure Container Registry seçin](media/container-tools-react/vs-2019/publish-dialog-acr.png)

1. **Yeni Azure Container Registry oluştur ' a** tıklayın.
1. **Yeni Azure Container Registry oluştur** ekranında istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio Azure Container Registry oluştur iletişim kutusu](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. **Oluştur**' u ve ardından **son**' u seçin.

   ![Yeni bir ACR seçin veya oluşturun](media/container-tools-react/vs-2019/publish-dialog2.png)

   Yayımlama işlemi sona erdiğinde, yayınlama ayarlarını gözden geçirebilir ve gerektiğinde düzenleyebilir veya **Yayımla** düğmesini kullanarak görüntüyü yeniden yayımlayabilirsiniz.

   ![Başarılı yayımlamayı gösteren ekran görüntüsü](media/container-tools-react/vs-2019/publish-finished.png)

   **Yayımla** iletişim kutusunu kullanarak yeniden başlamak için, bu sayfadaki **Sil** bağlantısını kullanarak yayımlama profilini silin ve sonra yeniden **Yayımla** ' yı seçin.
:::moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Artık kapsayıcıyı, kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir konağa çekebilirsiniz, örneğin [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Ek kaynaklar

* [Visual Studio ile kapsayıcı geliştirme](./index.yml)
* [Docker ile Visual Studio geliştirme sorunlarını giderme](troubleshooting-docker-errors.md)
* [Visual Studio kapsayıcı araçları GitHub deposu](https://github.com/Microsoft/DockerTools)

