---
title: Visual Studio üzerinde Docker için kapsayıcı araçları Windows
description: Docker ile çalışmak için Visual Studio araçlar hakkında bilgi edinebilirsiniz
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 10/27/2021
ms.technology: vs-container-tools
ms.openlocfilehash: fb6902e196143e54704ff669c3ef8cc01e8644b9
ms.sourcegitcommit: 3766c051f9a8b35106b16f751db7fecde0b92254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137951552"
---
# <a name="visual-studio-container-tools-for-docker"></a>Docker Visual Studio Kapsayıcı Araçları

Docker kapsayıcıları Visual Studio geliştirmeye yönelik araçlar kolayca kullanılabilir ve kapsayıcılı uygulamalar için bina, hata ayıklama ve dağıtım büyük ölçüde basitleştirir. Tek bir proje için bir kapsayıcıyla çalışabilirsiniz veya kapsayıcılarda birden çok hizmetle çalışmak Docker Compose veya Service Fabric ile kapsayıcı düzenlemesini kullanabilirsiniz.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme **,** **Azure** Araçları iş yükü ve/veya **.NET Core** platformlar arası geliştirme iş yükünün yüklü olduğu [2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sürümü
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme için kaydolma](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio'da Docker desteği

Docker desteği, ASP.NET, ASP.NET Core projeleri, Azure İşlevleri ve .NET Core ve .NET Framework konsol projeleri için kullanılabilir.

Visual Studio'de Docker desteği, müşteri ihtiyaçlarına yanıt olarak bir dizi yayında değişti. Projeye ek olarak iki Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve projenin sürümüne göre Visual Studio. Desteklenen bazı proje türlerinde, tek bir proje için kapsayıcıyı yalnızca düzenlemeyi kullanmadan kullanmak için Docker desteği ekleyerek bunu kullanabilirsiniz.  Sonraki düzey, seçtiğiniz belirli bir orchestrator için uygun destek dosyalarını ekleyen kapsayıcı düzenleme desteğidir.

2017 Visual Studio ile kapsayıcı düzenleme hizmetleri olarak Docker Compose Service Fabric hizmetleri kullanabilirsiniz.

> [!NOTE]
> 15.8'den önceki bir Visual Studio 2017 sürümünü kullanıyorsanız veya .NET Framework proje şablonunu kullanıyorsanız (.NET Core değil), Docker desteği eklerken, Docker Compose kullanarak düzenleme desteği otomatik olarak eklenir. 

::: moniker-end

::: moniker range="vs-2019"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio, **Azure** Araçları iş yükü ve/veya **.NET Core platformlar** arası geliştirme iş yükünün yüklü olduğu [2019](https://visualstudio.microsoft.com/downloads) sürümü 
* [.NET Core ile geliştirme için .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) Geliştirme Araçları.
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme için kaydolma](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio'da Docker desteği

Docker desteği, ASP.NET projelerinde, ASP.NET Core projelerinde ve .NET Core ve .NET Framework konsol projelerinde kullanılabilir.

Visual Studio'de Docker desteği, müşteri ihtiyaçlarına yanıt olarak bir dizi yayında değişti. Projeye ek olarak iki Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve projenin sürümüne göre Visual Studio. Desteklenen bazı proje türlerinde, tek bir proje için kapsayıcıyı yalnızca düzenlemeyi kullanmadan kullanmak için Docker desteği ekleyerek bunu kullanabilirsiniz.  Sonraki düzey, seçtiğiniz belirli bir orchestrator için uygun destek dosyalarını ekleyen kapsayıcı düzenleme desteğidir.

Visual Studio 2019'da kapsayıcı düzenleme Docker Compose kubernetes ve Service Fabric hizmetleri kullanabilirsiniz.

> [!NOTE]
> Tam .NET Framework konsol proje şablonunu kullanıyorsanız, desteklenen seçenek Proje oluşturma sonrasında Kapsayıcı **Orchestrator** Desteği Ekle'dir ve Service Fabric veya Docker Compose. Proje oluşturma ve Düzenleme olmadan **tek bir proje için Docker** desteği ekleme seçenekleri kullanılamaz.

Visual Studio 2019 sürüm 16.4 ve sonraki sürümlerde çalışan kapsayıcıları görüntülemenize, kullanılabilir  görüntülere göz atmanıza, ortam değişkenlerini, günlükleri ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemi incelemenize, hata ayıklayıcı eklemenize veya kapsayıcı ortamının içinde bir terminal penceresi açmanıza olanak sağlayan Kapsayıcılar penceresi kullanılabilir. Bkz [. Kapsayıcıları Kullanma penceresi](view-and-diagnose-containers.md).

::: moniker-end

::: moniker range=">=vs-2022"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://www.docker.com/get-docker)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET** masaüstü geliştirme iş yükünün yüklü olduğu [2022](https://visualstudio.microsoft.com/downloads) sürümü 
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme için kaydolma](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio'da Docker desteği

Docker desteği, ASP.NET projelerinde, ASP.NET Core projelerinde ve .NET Core ve .NET Framework konsol projelerinde kullanılabilir.

Visual Studio'de Docker desteği, müşteri ihtiyaçlarına yanıt olarak bir dizi yayında değişti. Projeye ek olarak iki Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve projenin sürümüne göre Visual Studio. Desteklenen bazı proje türlerinde, tek bir proje için kapsayıcıyı yalnızca düzenlemeyi kullanmadan kullanmak için Docker desteği ekleyerek bunu kullanabilirsiniz.  Sonraki düzey, seçtiğiniz belirli bir orchestrator için uygun destek dosyalarını ekleyen kapsayıcı düzenleme desteğidir.

Visual Studio 2022'de kapsayıcı düzenleme Docker Compose Service Fabric hizmet olarak kullanabilirsiniz.

> [!NOTE]
> Tam .NET Framework konsol proje şablonunu kullanıyorsanız, desteklenen seçenek Proje oluşturma sonrasında Kapsayıcı **Orchestrator** desteği ekle seçeneğidir ve Service Fabric veya Docker Compose. Proje oluşturma ve Düzenleme olmadan **tek bir proje için Docker** desteği ekleme seçenekleri kullanılamaz.

Visual Studio 2022'de çalışan kapsayıcıları görüntülemenizi, kullanılabilir görüntülere göz atmanıza, ortam değişkenlerini, günlükleri ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemi incelemenize, hata ayıklayıcı eklemenize veya kapsayıcı ortamının içinde bir terminal penceresi açmanıza olanak sağlayan Kapsayıcılar penceresi kullanılabilir. Bkz [. Kapsayıcıları Kullanma penceresi](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Docker desteği ekleme

Aşağıdaki ekran görüntüsünde gösterildiği gibi, yeni bir proje oluştururken Docker Desteğini Etkinleştir'i seçerek proje oluşturma sırasında **Docker** desteğini etkinleştirebilirsiniz:

::: moniker range="vs-2017"
![Yeni web uygulaması için DockerS Desteği'nin ASP.NET Core ekran görüntüsü Visual Studio.](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range="vs-2019"
![Yeni web uygulaması için Docker Desteği'nin ASP.NET Core ekran görüntüsü Visual Studio.](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Yeni web uygulaması için Docker Desteği'nin ASP.NET Core ekran görüntüsü Visual Studio.](./media/overview/vs-2022/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Diğer .NET Framework (.NET Core değil) için yalnızca Windows kapsayıcılar kullanılabilir.

Mevcut bir projeye Docker desteği eklemek için uygulama içinde **EkleDocker** >  **Desteği'Çözüm Gezgini**. **> Docker** Desteği ekle ve **> Kapsayıcı Orchestrator** Desteği ekle komutları, aşağıdaki ekran görüntüsünde gösterildiği gibi **Çözüm Gezgini'daki** bir ASP.NET Core projesi için proje düğümünün sağ tıklama menüsünde (veya bağlam menüsünde) bulunur:

:::moniker range="<=vs-2019"
![Uygulamanın içinde Docker Desteği menü seçeneğinin nasıl ek Visual Studio.](./media/overview/add-docker-support-menu.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Uygulamanın içinde Docker Desteği menü seçeneğinin nasıl ek Visual Studio.](./media/overview/vs-2022/add-docker-support.png)
:::moniker-end

Docker desteğini eklerken veya etkinleştirirken Visual Studio projeye şunları ekler:

* *Dockerfile* dosyası
* .dockerignore dosyası
* Microsoft.VisualStudio.Azure.Containers.Tools.Targets'a NuGet paket başvurusu

Ekley istediğiniz Dockerfile aşağıdaki koda benzer. Bu örnekte proje olarak adlandırılmış ve Linux `WebApplication-Docker`kapsayıcılarını seçmişsiniz:

:::moniker range="<=vs-2019"

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["WebApplication-Docker/WebApplication-Docker.csproj", "WebApplication-Docker/"]
RUN dotnet restore "WebApplication-Docker/WebApplication-Docker.csproj"
COPY . .
WORKDIR "/src/WebApplication-Docker"
RUN dotnet build "WebApplication-Docker.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-Docker.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-Docker.dll"]
```

:::moniker-end
:::moniker range=">=vs-2022"

```dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["WebApplication-Docker/WebApplication-Docker.csproj", "WebApplication-Docker/"]
RUN dotnet restore "WebApplication-Docker/WebApplication-Docker.csproj"
COPY . .
WORKDIR "/src/WebApplication-Docker"
RUN dotnet build "WebApplication-Docker.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-Docker.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-Docker.dll"]
```

:::moniker-end
::: moniker range="vs-2017"
> [!NOTE]
> Aşağıdaki ekran görüntüsünde gösterildiği gibi bir ASP.NET projesi (.NET Framework, .NET Core projesi değil) için proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz. Kapsayıcı orchestrator desteği de eklenir.

![Bir proje için Docker compose desteğini etkinleştirmeyi ASP.NET görüntüsü.](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="use-the-containers-window"></a>Kapsayıcılar penceresini kullanma

**Kapsayıcılar** penceresi, makineniz üzerinde kapsayıcıları ve görüntüleri görüntülemenizi ve neler olduğunu görmenizi sağlar. Dosya sistemi, bağlı birimler, ortam değişkenleri, kullanılan bağlantı noktaları ve günlük dosyalarını inceleyebilirsiniz.

Hızlı **başlatmayı** (**CtrlQ**) kullanarak ve **yazarak Kapsayıcılar**+ penceresini açın`containers`. Pencereyi bir yere koymak için yerleştirme denetimlerini kullanabilirsiniz. Pencerenin genişliği nedeniyle en iyi çalışma, ekranın en altına yerleştirildi.

Bir kapsayıcı seçin ve kullanılabilir bilgileri görüntülemek için sekmeleri kullanın. Bunu kontrol etmek için Docker özellikli uygulamanızı çalıştırın, Dosyalar sekmesini açın ve  dağıtılan uygulamanızı kapsayıcıda görmek  için uygulama klasörünü genişletin.

:::moniker range="<=vs-2019"
![Kapsayıcılar penceresinin ekran görüntüsü.](media/overview/vs-2019/container-tools-window-2.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresinin ekran görüntüsü.](media/overview/vs-2022/containers-files.png)
:::moniker-end

Daha fazla bilgi için bkz [. Kapsayıcılar penceresini kullanma](view-and-diagnose-containers.md).

## <a name="docker-compose-support"></a>Docker Compose desteği

Docker Compose kullanarak çok kapsayıcılı bir çözüm oluşturmak Docker Compose projelerinize kapsayıcı orchestrator desteği ekleyin. Bu, aynı *docker-compose.yml* dosyasında tanımlandıklarında bir kapsayıcı grubunu (tam çözüm veya proje grubu) aynı anda çalıştırmanız ve bunların hatasını ayıklamanıza olanak sağlar.

Docker Compose kullanarak kapsayıcı orchestrator desteği eklemek için, Çözüm Gezgini'de proje düğümüne sağ **tıklayın ve Kapsayıcı** **> Ekle'yi seçin**. Ardından **kapsayıcıları Docker Compose** için yeni bir sunucu seçin.

Projenize kapsayıcı orchestrator desteği ekledikten sonra, burada gösterildiği gibi projeye eklenmiş bir *Dockerfile* (zaten orada bir tane yoksa) ve **Çözüm Gezgini'de** çözüme bir **docker-compose** klasörü eklenir:

:::moniker range="<=vs-2019"
![Çözüm Gezgini'daki Docker Visual Studio.](media/overview/docker-support-solution-explorer.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Çözüm Gezgini'daki Docker Visual Studio.](media/overview/vs-2022/docker-compose-solution-explorer.png)
:::moniker-end

*docker-compose.yml* zaten Visual Studio gerekli yapılandırma kodu satırlarını ekler.

Bu işlemi, Docker Compose kullanarak kontrol etmek istediğiniz diğer projelerle Docker Compose.

Çok sayıda hizmetle çalışıyorsanız, hata ayıklama oturumda hangi hizmet alt kümesini başlatmak istediğinizi seçerek zamandan ve işlem kaynaklarında tasarruf sabilirsiniz. Bkz [. Oluşturma hizmetlerinin bir alt kümesini başlatma](launch-profiles.md).

## <a name="service-fabric-support"></a>Service Fabric desteği

Service Fabric araçlarıyla Visual Studio, Azure Service Fabric için geliştirme ve hata ayıklama, yerel olarak çalıştırma ve hata ayıklama ve Azure'a dağıtma.

::: moniker range="vs-2017"
Azure Visual Studio iş yükünün yüklü olduğu 2017 sürüm 15.9 ve sonraki sürümler, Windows kapsayıcılarını kullanarak kapsayıcılı mikro hizmetler geliştirmeyi ve Service Fabric düzenlemeyi destekler.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 ve sonraki bir yıl, Windows kapsayıcıları kullanarak kapsayıcılı mikro hizmetler geliştirmeyi ve Service Fabric destekler.
::: moniker-end

Ayrıntılı bir öğretici için bkz[. Öğretici: Bir .NET uygulamasını azure Windows kapsayıcıya Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Azure Service Fabric hakkında daha fazla bilgi için bkz[. Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Sürekli teslim ve sürekli tümleştirme (CI/CD)

Visual Studio, otomatik ve sürekli tümleştirme Azure Pipelines değişikliklerin hizmet kodunuz ve yapılandırmanıza teslimi için Azure Pipelines ile tümleştirilmiştir. Başlamak için bkz. [ilk işlem hattınızı oluşturma](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2&preserve-view=true).

Service Fabric için bkz. [öğretici: ASP.NET Core uygulamanızı Azure Service Fabric Azure DevOps projelerini kullanarak dağıtma](/azure/devops-project/azure-devops-project-service-fabric).

## <a name="next-steps"></a>Sonraki adımlar

hizmet uygulamasıyla ilgili diğer ayrıntılar ve kapsayıcılarla çalışma için Visual Studio araçlarının kullanımı hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

[Yerel Docker kapsayıcısındaki uygulamalar için hata ayıklama](edit-and-refresh.md)

[Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma](hosting-web-apps-in-docker.md)
