---
title: Visual Studio Windows kapsayıcı araçları
description: docker ile çalışmaya yönelik Visual Studio sunulan araçları öğrenin
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-container-tools
ms.openlocfilehash: 29f3c4aa7b1cc72a5404b91227248e8a5739edc2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098027"
---
# <a name="container-tools-in-visual-studio"></a>Visual Studio’da Kapsayıcı Araçları

kapsayıcılarla geliştirmeye yönelik Visual Studio dahil olan araçların kullanımı kolaydır ve kapsayıcılı uygulamalar için oluşturma, hata ayıklama ve dağıtımı büyük ölçüde basitleştirir. tek bir proje için bir kapsayıcı ile çalışabilir veya kapsayıcılar içinde birden fazla hizmet ile çalışmak için Docker Compose, Service Fabric veya kubernetes ile kapsayıcı düzenleme kullanabilirsiniz.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio Docker desteği

docker desteği ASP.NET projeler, ASP.NET Core projeleri ve .net Core ve .NET Framework konsol projeleri için kullanılabilir.

Visual Studio içindeki docker desteği, müşteri ihtiyaçlarına yanıt olarak çok sayıda yayın üzerinden değiştirilmiştir. Bir projeye ekleyebileceğiniz iki farklı Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve Visual Studio sürümüne göre farklılık gösterir. Desteklenen bazı proje türleriyle, tek bir proje için düzenleme kullanmadan yalnızca bir kapsayıcı istiyorsanız, bunu Docker desteği ekleyerek yapabilirsiniz.  Bir sonraki düzey, seçtiğiniz belirli bir Orchestrator için uygun destek dosyaları ekleyen kapsayıcı düzenleme destedir.

Visual Studio 2017 ile Docker Compose ve Service Fabric kapsayıcı düzenleme hizmetleri olarak kullanabilirsiniz.  kubernetes [için Visual Studio Araçları](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)yüklüyorsanız kubernetes ' i de kullanabilirsiniz.

> [!NOTE]
> 15,8 ' den önceki bir Visual Studio 2017 sürümünü kullanıyorsanız veya .NET Framework projesi şablonunu kullanıyorsanız (.net Core değil), docker desteği eklediğinizde, Docker Compose kullanarak düzenleme desteği otomatik olarak eklenir. Docker Compose aracılığıyla kapsayıcı düzenleme desteği, Visual Studio 2017 sürüm 15,0 ' de 15,7 ve .NET Framework projeleri için otomatik olarak eklenir.

::: moniker-end

::: moniker range=">=vs-2019"

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

Visual Studio 2019 sürüm 16,4 ve sonraki sürümlerde **kapsayıcılar** penceresi kullanılabilir; bu, çalışan kapsayıcıları görüntülemenize, kullanılabilir görüntülere gözatmanıza, ortam değişkenlerini, günlüklere ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemini incelemenize, bir hata ayıklayıcı eklemenize veya kapsayıcı ortamının içinde bir terminal penceresi açmaya olanak sağlar. Bkz. [Visual Studio kapsayıcıları ve görüntüleri görüntüleme ve tanılama](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Docker desteği ekleme

Aşağıdaki ekran görüntüsünde gösterildiği gibi yeni bir proje oluştururken **Docker desteğini etkinleştir** ' i seçerek proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz:

::: moniker range="vs-2017"
![Visual Studio yeni ASP.NET Core web uygulaması için docker desteğini etkinleştir](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Visual Studio yeni ASP.NET Core web uygulaması için docker desteğini etkinleştir](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> .NET Framework projeler (.net Core değil) için yalnızca Windows kapsayıcılar kullanılabilir.

  >  **Çözüm Gezgini**' de **Docker desteği** Ekle ' ye tıklayarak mevcut bir projeye Docker desteği ekleyebilirsiniz. **> docker desteği ekleme** ve **ekleme > kapsayıcı Orchestrator destek** komutları, aşağıdaki ekran görüntüsünde gösterildiği gibi, **Çözüm Gezgini** içindeki bir ASP.NET Core projesi için proje düğümünün sağ tıklama menüsünde (veya bağlam menüsü) bulunur:

![Visual Studio Docker desteği menü seçeneği ekleme](./media/overview/add-docker-support-menu.png)

docker desteğini eklediğinizde veya etkinleştirdiğinizde, Visual Studio aşağıdakileri projeye ekler:

- *Dockerfile* dosyası
- bir. dockerıgnore dosyası
- Microsoft. VisualStudio. Azure. Containers. Tools. Targets için NuGet paketi başvurusu

::: moniker range=">=vs-2019"
Docker desteği eklediğinizde çözüm şöyle görünür:

![Dockerfile ve. dockerıgnore dosyası ile Çözüm Gezgini 'nin ekran görüntüsü](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> aşağıdaki ekran görüntüsünde gösterildiği gibi bir ASP.NET projesi (.NET Framework, .net Core projesi değil) için proje oluşturma sırasında docker desteğini etkinleştirdiğinizde, kapsayıcı düzenleme desteği de eklenir.

![ASP.NET projesi için docker compose desteğini etkinleştir](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Docker Compose desteği

Docker Compose kullanarak çok kapsayıcılı bir çözüm oluşturmak istediğinizde, projelerinize kapsayıcı düzenleme desteği ekleyin. Bu, aynı *Docker-Compose. yıml* dosyasında tanımlandıklarında bir kapsayıcı grubunu (bir bütün çözüm veya proje grubu) aynı anda çalıştırmanızı ve hata ayıklamanıza olanak tanır.

Docker Compose kullanarak kapsayıcı düzenleme desteği eklemek için, **Çözüm Gezgini** çözüm veya proje düğümüne sağ tıklayın ve **> kapsayıcı düzenleme desteği ekle**' yi seçin. Sonra kapsayıcıları yönetmek için **Docker Compose** öğesini seçin.

Projenize kapsayıcı düzenleme desteğini ekledikten sonra, burada gösterildiği gibi, projeye bir *Dockerfile* (zaten bir tane yoksa) ve **Çözüm Gezgini** çözüme eklenen bir **Docker-Compose** klasörü görürsünüz:

![Visual Studio Çözüm Gezgini Docker dosyaları](media/overview/docker-support-solution-explorer.png)

*docker-compose. yml* zaten varsa Visual Studio, yalnızca gerekli olan yapılandırma kodu satırlarını buna ekler.

Docker Compose kullanarak denetlemek istediğiniz diğer projelerle işlemi tekrarlayın.

## <a name="kubernetes-support"></a>Kubernetes desteği

::: moniker range="vs-2017"
kubernetes desteği eklemek için, [kubernetes için Visual Studio Araçları](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)yüklemesini yapın.
::: moniker-end

Kubernetes desteğiyle, [Azure Kubernetes Service (AKS)](/azure/aks)içinde çalışan yerel projeniz Ile Kubernetes kümesi arasında bir bağlantıyı etkinleştirebilir ve bu sayede Visual Studio kullanarak Hizmetleri değiştirebilir ve hatalarını ayıklayabilirsiniz.  Bu hizmet, [Kubernetes Köprüsü](/visualstudio/bridge/overview-bridge-to-kubernetes)tarafından sağlanır.

## <a name="service-fabric-support"></a>Service Fabric desteği

Visual Studio Service Fabric araçlarla azure Service Fabric geliştirebilir ve hata ayıklayın, yerel olarak çalıştırıp hata ayıklayın ve azure 'a dağıtabilirsiniz.

::: moniker range="vs-2017"
Visual Studio 2017 sürüm 15,9 ve üzeri Azure geliştirme iş yükü yüklü Windows kapsayıcıları ve düzenleme Service Fabric kullanarak kapsayıcılı mikro hizmetler geliştirmeyi destekler.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019, Windows kapsayıcıları ve düzenleme Service Fabric kullanarak kapsayıcılı mikro hizmetlerin geliştirilmesini destekler.
::: moniker-end

ayrıntılı bir öğretici için bkz. [öğretici: bir .net uygulamasını Windows kapsayıcısında Azure Service Fabric dağıtma](/azure/service-fabric/service-fabric-host-app-in-a-container).

Azure Service Fabric hakkında daha fazla bilgi için bkz. [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Sürekli teslim ve sürekli tümleştirme (CI/CD)

Visual Studio, otomatik ve sürekli tümleştirme ve hizmet kodunuzda ve yapılandırmanızda yapılan değişikliklerin teslimi için Azure Pipelines ile tümleşir. Başlamak için bkz. [ilk işlem hattınızı oluşturma](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2&preserve-view=true).

Service Fabric için bkz. [öğretici: ASP.NET Core uygulamanızı Azure Service Fabric Azure DevOps projelerini kullanarak dağıtma](/azure/devops-project/azure-devops-project-service-fabric).

Kubernetes için bkz. [Azure Kubernetes hizmetine Docker kapsayıcı uygulaması dağıtma](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops&preserve-view=true).

## <a name="next-steps"></a>Sonraki adımlar

hizmet uygulamasıyla ilgili diğer ayrıntılar ve kapsayıcılarla çalışma için Visual Studio araçlarının kullanımı hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

[Yerel Docker kapsayıcısındaki uygulamalar için hata ayıklama](edit-and-refresh.md)

[Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma](hosting-web-apps-in-docker.md)
