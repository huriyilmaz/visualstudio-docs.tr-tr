---
title: Visual Studio Windows'de Kapsayıcı Araçları
description: Docker ile çalışmak için Visual Studio araçlar hakkında bilgi edinebilirsiniz
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-container-tools
ms.openlocfilehash: 1e957efcc3a9663d01c7bc0ffde14fb44c23bc6db1a9db45d9b8968dc2753b9f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121294579"
---
# <a name="container-tools-in-visual-studio"></a>Visual Studio’da Kapsayıcı Araçları

Kapsayıcılarla geliştirmeye Visual Studio araçlar kolayca kullanılabilir ve kapsayıcılı uygulamalar için bina, hata ayıklama ve dağıtım büyük ölçüde basitleştirir. Kapsayıcılarla tek bir proje için çalışabilirsiniz veya kapsayıcılarda birden çok hizmetle çalışmak için Docker Compose, Service Fabric veya Kubernetes ile kapsayıcı düzenlemesini kullanabilirsiniz.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET Core** platformlar arası geliştirme iş yükünün yüklü olduğu [2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sürümü
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme sürümüne kaydolma.](https://azure.microsoft.com/offers/ms-azr-0044p/)

## <a name="docker-support-in-visual-studio"></a>Visual Studio'de Docker desteği

Docker desteği, ASP.NET projelerinde, ASP.NET Core projelerinde ve .NET Core ve .NET Framework konsol projelerinde kullanılabilir.

Visual Studio'da Docker desteği, müşteri ihtiyaçlarına yanıt olarak bir dizi yayında değişti. Projeye ek olarak iki Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve projenin sürümüne göre Visual Studio. Desteklenen bazı proje türlerinde, tek bir proje için kapsayıcıyı yalnızca düzenlemeyi kullanmadan kullanmak için Docker desteği ekleyerek bunu kullanabilirsiniz.  Sonraki düzey, seçtiğiniz belirli bir orchestrator için uygun destek dosyalarını ekleyen kapsayıcı düzenleme desteğidir.

2017 Visual Studio ile kapsayıcı düzenleme hizmetleri olarak Docker Compose Service Fabric ve kapsayıcıları kullanabilirsiniz.  Kubernetes için yükleme Visual Studio Araçları [Kubernetes'i de kullanabilirsiniz.](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)

> [!NOTE]
> 15.8'den önceki bir Visual Studio 2017 sürümünü kullanıyorsanız veya .NET Framework proje şablonunu kullanıyorsanız (.NET Core değil), Docker desteği eklerken, Docker Compose kullanarak düzenleme desteği otomatik olarak eklenir. Docker Compose aracılığıyla kapsayıcı düzenleme desteği, Visual Studio 2017 sürüm 15.0'dan 15.7'ye ve .NET Framework projelerine eklenir.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET Core** platformlar arası geliştirme iş yükünün yüklü olduğu [2019](https://visualstudio.microsoft.com/downloads) sürümü
* [.NET Core ile geliştirme](https://dotnet.microsoft.com/download/dotnet-core/) için .NET Core Geliştirme Araçları.
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme sürümüne kaydolma.](https://azure.microsoft.com/offers/ms-azr-0044p/)

## <a name="docker-support-in-visual-studio"></a>Visual Studio'de Docker desteği

Docker desteği, ASP.NET projelerinde, ASP.NET Core projelerinde ve .NET Core ve .NET Framework konsol projelerinde kullanılabilir.

Visual Studio'da Docker desteği, müşteri ihtiyaçlarına yanıt olarak bir dizi yayında değişti. Projeye ek olarak iki Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve projenin sürümüne göre Visual Studio. Desteklenen bazı proje türlerinde, tek bir proje için kapsayıcıyı yalnızca düzenlemeyi kullanmadan kullanmak için Docker desteği ekleyerek bunu kullanabilirsiniz.  Sonraki düzey, seçtiğiniz belirli bir orchestrator için uygun destek dosyalarını ekleyen kapsayıcı düzenleme desteğidir.

Visual Studio 2019'da kapsayıcı düzenleme Docker Compose kubernetes ve Service Fabric hizmetleri kullanabilirsiniz.

> [!NOTE]
> Tam .NET Framework konsol proje şablonunu kullanıyorsanız, desteklenen seçenek Proje oluşturmadan sonra Kapsayıcı **Orchestrator** desteği ekle seçeneğidir ve Service Fabric veya Docker Compose. Proje oluşturma ve Düzenleme olmadan **tek bir proje için Docker** desteği ekleme seçenekleri kullanılamaz.

Visual Studio 2019 sürüm 16.4 ve sonraki  sürümlerde çalışan kapsayıcıları görüntülemenize, kullanılabilir görüntülere göz atmanıza, ortam değişkenlerini, günlükleri ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemi incelemenize, hata ayıklayıcı eklemenize veya kapsayıcı ortamının içinde bir terminal penceresi açmanıza olanak sağlayan Kapsayıcılar penceresi kullanılabilir. Bkz. [Kapsayıcıları ve görüntüleri görüntüleme ve tanılama Visual Studio.](view-and-diagnose-containers.md)

::: moniker-end

### <a name="adding-docker-support"></a>Docker desteği ekleme

Aşağıdaki ekran görüntüsünde gösterildiği gibi, yeni bir proje oluştururken Docker Desteğini Etkinleştir'i seçerek proje oluşturma sırasında **Docker** desteğini etkinleştirebilirsiniz:

::: moniker range="vs-2017"
![Visual Studio'de yeni ASP.NET Core web uygulaması için Docker Desteğini Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Visual Studio'de yeni ASP.NET Core web uygulaması için Docker Desteğini Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Diğer .NET Framework (.NET Core değil) için yalnızca Windows kapsayıcılar kullanılabilir.

docker desteğini mevcut projeye eklemek için Çözüm Gezgini'de  >  **Docker Desteği** **Ekle'yi Çözüm Gezgini.** **> Docker** Desteği Ekle ve **> Kapsayıcı Orchestrator** Desteği komutları, aşağıdaki ekran görüntüsünde gösterildiği gibi **Çözüm Gezgini'daki** bir ASP.NET Core projesinin proje düğümünün sağ tıklama menüsünde (veya bağlam menüsünde) bulunur:

![Visual Studio'da Docker Desteği ekle menü Visual Studio](./media/overview/add-docker-support-menu.png)

Docker desteğini ekleyen veya etkinleştiren Visual Studio projeye şunları ekler:

- *Dockerfile* dosyası
- .dockerignore dosyası
- Microsoft.VisualStudio.Azure.Containers.Tools.Targets'a NuGet paket başvurusu

::: moniker range=">=vs-2019"
Docker desteği eklensin mi çözüm aşağıdaki gibi olur:

![Dockerfile ve .dockerignore dosyasıyla çözüm gezgininin ekran görüntüsü](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Aşağıdaki ekran görüntüsünde gösterildiği gibi bir ASP.NET projesi (.NET Framework, .NET Core projesi değil) için proje oluşturma sırasında Docker desteğini etkinleştirecek olurken kapsayıcı düzenleme desteği de eklenir.

![Bir ASP.NET projesi için Docker compose desteğini etkinleştirme](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Docker Compose desteği

Docker Compose kullanarak çok kapsayıcılı bir çözüm oluşturmak Docker Compose projelerinize kapsayıcı düzenleme desteği ekleyin. Bu, aynı *docker-compose.yml* dosyasında tanımlandıklarında bir kapsayıcı grubunu (tam çözüm veya proje grubu) aynı anda çalıştırmanız ve bunların hatasını ayıklamanıza olanak sağlar.

Docker Compose kullanarak kapsayıcı düzenleme desteği eklemek için, Çözüm Gezgini'de çözüme veya proje düğümüne sağ tıklayın ve **Kapsayıcı** **Düzenleme Desteği'> ekle'yi seçin.** Ardından **kapsayıcıları Docker Compose** için yeni bir sunucu seçin.

Projenize kapsayıcı düzenleme desteği ekledikten sonra, burada gösterildiği gibi projeye eklenmiş bir *Dockerfile* (zaten orada bir tane yoksa) ve **Çözüm Gezgini'de** çözüme bir **docker-compose** klasörü eklenir:

![Visual Studio'de Çözüm Gezgini'daki Docker Visual Studio](media/overview/docker-support-solution-explorer.png)

*docker-compose.yml* zaten Visual Studio gerekli yapılandırma kodu satırlarını ekler.

Bu işlemi, Docker Compose kullanarak kontrol etmek istediğiniz diğer projelerle Docker Compose.

## <a name="kubernetes-support"></a>Kubernetes desteği

::: moniker range="vs-2017"
Kubernetes desteği eklemek için [Kubernetes Visual Studio Araçları yükleme.](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)
::: moniker-end

Kubernetes desteğiyle, yerel projeniz ile [Azure Kubernetes Service (AKS)](/azure/aks)içinde çalışan bir Kubernetes kümesi arasında bağlantı etkinleştirebilirsiniz ve böylece Visual Studio kullanarak çalışan hizmetlerinizi değiştirebilir ve hata ayıklaması Visual Studio.  Bu hizmet, tarafından [Bridge to Kubernetes.](/visualstudio/bridge/overview-bridge-to-kubernetes)

## <a name="service-fabric-support"></a>Service Fabric desteği

Service Fabric araçlarıyla Visual Studio, Azure Service Fabric için geliştirme ve hata ayıklama, yerel olarak çalıştırma ve hata ayıklama ve Azure'a dağıtma.

::: moniker range="vs-2017"
Azure Visual Studio iş yükünün yüklü olduğu 2017 sürüm 15.9 ve sonraki sürümler, Windows kapsayıcılarını kullanarak kapsayıcılı mikro hizmetler geliştirmeyi ve Service Fabric destekler.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019, kapsayıcılı kapsayıcıları kullanarak kapsayıcılı mikro Windows geliştirmeyi ve Service Fabric destekler.
::: moniker-end

Ayrıntılı bir öğretici için [bkz. Öğretici: Azure'da](/azure/service-fabric/service-fabric-host-app-in-a-container)bir Windows kapsayıcıda .NET uygulaması Service Fabric.

Azure Service Fabric hakkında daha fazla bilgi için [bkz. Service Fabric.](/azure/service-fabric)

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Sürekli teslim ve sürekli tümleştirme (CI/CD)

Visual Studio, otomatik ve sürekli tümleştirme Azure Pipelines değişikliklerin hizmet kodunuz ve yapılandırmanıza teslimi için Azure Pipelines ile tümleştirilmiştir. Çalışmaya başlama için bkz. [İlk işlem hattınızı oluşturma.](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2&preserve-view=true)

Daha Service Fabric [bkz. Öğretici: ASP.NET Core Projelerini](/azure/devops-project/azure-devops-project-service-fabric)kullanarak Service Fabric Azure Azure DevOps dağıtma.

Kubernetes için [bkz. Docker kapsayıcı uygulamasını](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops&preserve-view=true)Azure Kubernetes Service.

## <a name="next-steps"></a>Sonraki adımlar

Kapsayıcılarla çalışmaya yönelik hizmet uygulama ve Visual Studio hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

[Yerel Docker kapsayıcısındaki uygulamalar için hata ayıklama](edit-and-refresh.md)

[Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma](hosting-web-apps-in-docker.md)
