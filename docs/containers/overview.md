---
title: Visual Studio Windows Docker için kapsayıcı araçları
description: docker ile çalışmaya yönelik Visual Studio sunulan araçları öğrenin
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 10/27/2021
ms.technology: vs-container-tools
ms.openlocfilehash: 4b9e4925334c80e8ba1b62a8dafe5eb84e756d9b
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662102"
---
# <a name="visual-studio-container-tools-for-docker"></a>Visual Studio Docker için kapsayıcı araçları

docker kapsayıcıları ile geliştirmeye yönelik Visual Studio eklenen araçların kullanımı kolaydır ve kapsayıcılı uygulamalar için oluşturma, hata ayıklama ve dağıtımı büyük ölçüde basitleştirir. tek bir proje için bir kapsayıcı ile çalışabilir veya kapsayıcılar içinde birden fazla hizmet ile çalışmak için Docker Compose veya Service Fabric kapsayıcı düzenleme kullanabilirsiniz.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio Docker desteği

docker desteği ASP.NET projeler, ASP.NET Core projeler, Azure işlevleri ve .net Core ve .NET Framework konsol projeleri için kullanılabilir.

Visual Studio içindeki docker desteği, müşteri ihtiyaçlarına yanıt olarak çok sayıda yayın üzerinden değiştirilmiştir. Bir projeye ekleyebileceğiniz iki farklı Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve Visual Studio sürümüne göre farklılık gösterir. Desteklenen bazı proje türleriyle, tek bir proje için düzenleme kullanmadan yalnızca bir kapsayıcı istiyorsanız, bunu Docker desteği ekleyerek yapabilirsiniz.  Bir sonraki düzey, seçtiğiniz belirli bir Orchestrator için uygun destek dosyaları ekleyen kapsayıcı düzenleme destedir.

Visual Studio 2017 ile Docker Compose ve Service Fabric kapsayıcı düzenleme hizmetleri olarak kullanabilirsiniz.

> [!NOTE]
> 15,8 ' den önceki bir Visual Studio 2017 sürümünü kullanıyorsanız veya .NET Framework projesi şablonunu kullanıyorsanız (.net Core değil), docker desteği eklediğinizde, Docker Compose kullanarak düzenleme desteği otomatik olarak eklenir. 

::: moniker-end

::: moniker range="vs-2019"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core ile geliştirme için [.NET Core geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/) .
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio Docker desteği

docker desteği ASP.NET projeler, ASP.NET Core projeleri ve .net Core ve .NET Framework konsol projeleri için kullanılabilir.

Visual Studio içindeki docker desteği, müşteri ihtiyaçlarına yanıt olarak çok sayıda yayın üzerinden değiştirilmiştir. Bir projeye ekleyebileceğiniz iki farklı Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve Visual Studio sürümüne göre farklılık gösterir. Desteklenen bazı proje türleriyle, tek bir proje için düzenleme kullanmadan yalnızca bir kapsayıcı istiyorsanız, bunu Docker desteği ekleyerek yapabilirsiniz.  Bir sonraki düzey, seçtiğiniz belirli bir Orchestrator için uygun destek dosyaları ekleyen kapsayıcı düzenleme destedir.

Visual Studio 2019 ile, Docker Compose, kubernetes ve Service Fabric kapsayıcı düzenleme hizmetleri olarak kullanabilirsiniz.

> [!NOTE]
> tam .NET Framework konsol projesi şablonu kullanıyorsanız, desteklenen seçenek, proje oluşturulduktan sonra, Service Fabric veya Docker Compose kullanma seçenekleriyle **kapsayıcı Orchestrator desteği ekler** . Proje oluşturma sırasında destek ekleme ve düzenleme olmadan tek bir proje için **Docker desteği ekleme** seçeneği kullanılamaz.

Visual Studio 2019 sürüm 16,4 ve sonraki sürümlerde **kapsayıcılar** penceresi kullanılabilir; bu, çalışan kapsayıcıları görüntülemenize, kullanılabilir görüntülere gözatmanıza, ortam değişkenlerini, günlüklere ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemini incelemenize, bir hata ayıklayıcı eklemenize veya kapsayıcı ortamının içinde bir terminal penceresi açmaya olanak sağlar. Bkz. [kapsayıcılar penceresini kullanma](view-and-diagnose-containers.md).

::: moniker-end

::: moniker range=">=vs-2022"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://www.docker.com/get-docker)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net masaüstü geliştirme** iş yükü yüklü olan [2022 RC Visual Studio](https://visualstudio.microsoft.com/downloads)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio Docker desteği

docker desteği ASP.NET projeler, ASP.NET Core projeleri ve .net Core ve .NET Framework konsol projeleri için kullanılabilir.

Visual Studio içindeki docker desteği, müşteri ihtiyaçlarına yanıt olarak çok sayıda yayın üzerinden değiştirilmiştir. Bir projeye ekleyebileceğiniz iki farklı Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve Visual Studio sürümüne göre farklılık gösterir. Desteklenen bazı proje türleriyle, tek bir proje için düzenleme kullanmadan yalnızca bir kapsayıcı istiyorsanız, bunu Docker desteği ekleyerek yapabilirsiniz.  Bir sonraki düzey, seçtiğiniz belirli bir Orchestrator için uygun destek dosyaları ekleyen kapsayıcı düzenleme destedir.

Visual Studio 2022 ile Docker Compose veya Service Fabric kapsayıcı düzenleme hizmetleri olarak kullanabilirsiniz.

> [!NOTE]
> tam .NET Framework konsol projesi şablonu kullanıyorsanız, desteklenen seçenek, proje oluşturulduktan sonra, Service Fabric veya Docker Compose kullanma seçenekleriyle **kapsayıcı Orchestrator desteği ekler** . Proje oluşturma sırasında destek ekleme ve düzenleme olmadan tek bir proje için **Docker desteği ekleme** seçeneği kullanılamaz.

Visual Studio 2022 ' de **kapsayıcılar** penceresi kullanılabilir; bu, çalışan kapsayıcıları görüntülemenize, kullanılabilir görüntülere gözatmanıza, ortam değişkenlerini, günlüklere ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemini incelemenize, hata ayıklayıcı eklemenize veya kapsayıcı ortamında bir terminal penceresi açmaya olanak sağlar. Bkz. [kapsayıcılar penceresini kullanma](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Docker desteği ekleme

Aşağıdaki ekran görüntüsünde gösterildiği gibi yeni bir proje oluştururken **Docker desteğini etkinleştir** ' i seçerek proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz:

::: moniker range="vs-2017"
![Visual Studio ' de yeni ASP.NET Core web uygulaması için docseçiciler desteğinin nasıl etkinleştirileceğini gösteren ekran görüntüsü.](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range="vs-2019"
![Visual Studio ' de yeni ASP.NET Core web uygulaması için docker desteğinin nasıl etkinleştirileceğini gösteren ekran görüntüsü.](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Visual Studio ' de yeni ASP.NET Core web uygulaması için docker desteğinin nasıl etkinleştirileceğini gösteren ekran görüntüsü.](./media/overview/vs-2022/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> .NET Framework projeler (.net Core değil) için yalnızca Windows kapsayıcılar kullanılabilir.

  >  **Çözüm Gezgini**' de **Docker desteği** Ekle ' ye tıklayarak mevcut bir projeye Docker desteği ekleyebilirsiniz. **> docker desteği ekleme** ve **ekleme > kapsayıcı Orchestrator destek** komutları, aşağıdaki ekran görüntüsünde gösterildiği gibi, **Çözüm Gezgini** içindeki bir ASP.NET Core projesi için proje düğümünün sağ tıklama menüsünde (veya bağlam menüsü) bulunur:

:::moniker range="<=vs-2019"
![Visual Studio Docker desteği menü seçeneğinin nasıl ekleneceğini gösteren ekran görüntüsü.](./media/overview/add-docker-support-menu.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Visual Studio Docker desteği menü seçeneğinin nasıl ekleneceğini gösteren ekran görüntüsü.](./media/overview/vs-2022/add-docker-support.png)
:::moniker-end

docker desteğini eklediğinizde veya etkinleştirdiğinizde, Visual Studio aşağıdakileri projeye ekler:

* *Dockerfile* dosyası
* bir. dockerıgnore dosyası
* Microsoft. VisualStudio. Azure. Containers. Tools. Targets için NuGet paketi başvurusu

Eklediğiniz Dockerfile aşağıdaki koda benzeyecektir. Bu örnekte, proje adlandırılmıştı `WebApplication-Docker` ve Linux kapsayıcıları seçtiniz:

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
> aşağıdaki ekran görüntüsünde gösterildiği gibi bir ASP.NET projesi (.NET Framework, .net Core projesi değil) için proje oluşturma sırasında docker desteğini etkinleştirdiğinizde, kapsayıcı düzenleme desteği de eklenir.

![ASP.NET projesi için docker compose desteğinin nasıl etkinleştirileceğini gösteren ekran görüntüsü.](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="use-the-containers-window"></a>Kapsayıcılar penceresini kullanma

**Kapsayıcılar** penceresi, makinenizde kapsayıcıları ve görüntüleri görüntülemenize ve bunlarla neler olduğunu görmenizi sağlar. Dosya sistemini, bağlı birimleri, ortam değişkenlerini, kullanılan bağlantı noktalarını görüntüleyebilir ve günlük dosyalarını inceleyebilirsiniz.

Hızlı Başlat  (**CTRL** + **Q**) kullanarak ve yazarak kapsayıcılar penceresini açın `containers` . Pencereyi bir yere yerleştirmek için yerleştirme denetimlerini kullanabilirsiniz. Pencerenin genişliği nedeniyle, ekranın alt kısmına yerleştirildiğinde en iyi sonucu verir.

Bir kapsayıcı seçin ve kullanılabilir bilgileri görüntülemek için sekmeleri kullanın. Kullanıma almak için Docker özellikli uygulamanızı çalıştırın, **dosyalar** sekmesini açın ve **uygulama** klasörünü genişleterek dağıtılan uygulamanızı kapsayıcıda görüntüleyin.

:::moniker range="<=vs-2019"
![Kapsayıcılar penceresinin ekran görüntüsü.](media/overview/vs-2019/container-tools-window-2.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresinin ekran görüntüsü.](media/overview/vs-2022/containers-files.png)
:::moniker-end

Daha fazla bilgi için bkz. [kapsayıcılar penceresini kullanma](view-and-diagnose-containers.md).

## <a name="docker-compose-support"></a>Docker Compose desteği

Docker Compose kullanarak çok kapsayıcılı bir çözüm oluşturmak istediğinizde, projelerinize kapsayıcı düzenleme desteği ekleyin. Bu, aynı *Docker-Compose. yıml* dosyasında tanımlandıklarında bir kapsayıcı grubunu (bir bütün çözüm veya proje grubu) aynı anda çalıştırmanızı ve hata ayıklamanıza olanak tanır.

Docker Compose kullanarak kapsayıcı düzenleme desteği eklemek için, **Çözüm Gezgini** çözüm veya proje düğümüne sağ tıklayın ve **> kapsayıcı düzenleme desteği ekle**' yi seçin. Sonra kapsayıcıları yönetmek için **Docker Compose** öğesini seçin.

Projenize kapsayıcı düzenleme desteğini ekledikten sonra, burada gösterildiği gibi, projeye bir *Dockerfile* (zaten bir tane yoksa) ve **Çözüm Gezgini** çözüme eklenen bir **Docker-Compose** klasörü görürsünüz:

:::moniker range="<=vs-2019"
![Visual Studio Çözüm Gezgini Docker dosyalarının ekran görüntüsü.](media/overview/docker-support-solution-explorer.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Visual Studio Çözüm Gezgini Docker dosyalarının ekran görüntüsü.](media/overview/vs-2022/docker-compose-solution-explorer.png)
:::moniker-end

*docker-compose. yml* zaten varsa Visual Studio, yalnızca gerekli olan yapılandırma kodu satırlarını buna ekler.

Docker Compose kullanarak denetlemek istediğiniz diğer projelerle işlemi tekrarlayın.

Çok sayıda hizmetlerle çalışıyorsanız, hata ayıklama oturumunuzda hangi hizmet alt kümesini başlatmak istediğinizi seçerek zaman ve bilgi işlem kaynakları tasarrufu yapabilirsiniz. Bkz. [oluşturma hizmetleri alt kümesini başlatma](launch-profiles.md).

## <a name="service-fabric-support"></a>Service Fabric desteği

Visual Studio Service Fabric araçlarla azure Service Fabric geliştirebilir ve hata ayıklayın, yerel olarak çalıştırıp hata ayıklayın ve azure 'a dağıtabilirsiniz.

::: moniker range="vs-2017"
Visual Studio 2017 sürüm 15,9 ve üzeri Azure geliştirme iş yükü yüklü Windows kapsayıcıları ve düzenleme Service Fabric kullanarak kapsayıcılı mikro hizmetler geliştirmeyi destekler.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 ve üzeri, Windows kapsayıcıları ve düzenleme Service Fabric kullanarak kapsayıcılı mikro hizmetler geliştirmeyi destekler.
::: moniker-end

ayrıntılı bir öğretici için bkz. [öğretici: bir .net uygulamasını Windows kapsayıcısında Azure Service Fabric dağıtma](/azure/service-fabric/service-fabric-host-app-in-a-container).

Azure Service Fabric hakkında daha fazla bilgi için bkz. [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Sürekli teslim ve sürekli tümleştirme (CI/CD)

Visual Studio, otomatik ve sürekli tümleştirme ve hizmet kodunuzda ve yapılandırmanızda yapılan değişikliklerin teslimi için Azure Pipelines ile tümleşir. Çalışmaya başlama için bkz. [İlk işlem hattınızı oluşturma.](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2&preserve-view=true)

Daha Service Fabric [bkz. Öğretici: ASP.NET Core](/azure/devops-project/azure-devops-project-service-fabric)Projelerini kullanarak Service Fabric Azure Azure DevOps dağıtma.

## <a name="next-steps"></a>Sonraki adımlar

Kapsayıcılarla çalışmaya yönelik hizmet uygulama ve Visual Studio hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

[Yerel Docker kapsayıcısındaki uygulamalar için hata ayıklama](edit-and-refresh.md)

[Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma](hosting-web-apps-in-docker.md)
