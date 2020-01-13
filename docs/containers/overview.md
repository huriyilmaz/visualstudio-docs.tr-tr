---
title: Windows üzerinde Visual Studio kapsayıcı araçları
description: Docker ile çalışmaya yönelik Visual Studio 'da kullanılabilen araçları öğrenin
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0d5859016a02de259c24c213c6cfef8cb5fce005
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916561"
---
# <a name="container-tools-in-visual-studio"></a>Visual Studio’da Kapsayıcı Araçları

Kapsayıcılarla geliştirmeye yönelik Visual Studio 'ya dahil olan araçların kullanımı kolaydır ve Kapsayıcılı uygulamalar için oluşturma, hata ayıklama ve dağıtımı büyük ölçüde basitleştirir. Tek bir proje için bir kapsayıcı ile çalışabilir veya kapsayıcılar içinde birden fazla hizmet ile çalışmak için Docker Compose, Service Fabric veya Kubernetes ile kapsayıcı düzenleme kullanabilirsiniz.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Prerequisites

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** iş yükü ve/veya **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio 'da Docker desteği

Docker desteği ASP.NET projeleri, ASP.NET Core projeleri ve .NET Core ve .NET Framework konsol projeleri için kullanılabilir.

Visual Studio 'da Docker desteği, müşteri ihtiyaçlarına yanıt olarak bir dizi yayın üzerinden değişmiştir. Bir projeye ekleyebileceğiniz iki farklı Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve Visual Studio sürümüne göre farklılık gösterir. Desteklenen bazı proje türleriyle, tek bir proje için düzenleme kullanmadan yalnızca bir kapsayıcı istiyorsanız, bunu Docker desteği ekleyerek yapabilirsiniz.  Bir sonraki düzey, seçtiğiniz belirli bir Orchestrator için uygun destek dosyaları ekleyen kapsayıcı düzenleme destedir.  

Visual Studio 2017 ile Docker Compose ve Service Fabric kapsayıcı düzenleme hizmetleri olarak kullanabilirsiniz.  Ayrıca, [Kubernetes için Visual Studio Araçları](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)yüklerseniz Kubernetes de kullanabilirsiniz.

> [!NOTE]
> 15,8 ' den önceki bir Visual Studio 2017 sürümünü kullanıyorsanız veya .NET Framework proje şablonunu kullanıyorsanız (.NET Core değil), Docker desteği eklediğinizde, Docker Compose kullanarak düzenleme desteği otomatik olarak eklenir. Docker Compose aracılığıyla kapsayıcı düzenleme desteği, Visual Studio 2017 sürüm 15,0 ' de 15,7 ve .NET Framework projeler için otomatik olarak eklenir.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Prerequisites

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** iş yükü ve/veya **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core ile geliştirme için [.NET Core geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/) .
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Visual Studio 'da Docker desteği

Docker desteği ASP.NET projeleri, ASP.NET Core projeleri ve .NET Core ve .NET Framework konsol projeleri için kullanılabilir.

Visual Studio 'da Docker desteği, müşteri ihtiyaçlarına yanıt olarak bir dizi yayın üzerinden değişmiştir. Bir projeye ekleyebileceğiniz iki farklı Docker desteği düzeyi vardır ve desteklenen seçenekler proje türüne ve Visual Studio sürümüne göre farklılık gösterir. Desteklenen bazı proje türleriyle, tek bir proje için düzenleme kullanmadan yalnızca bir kapsayıcı istiyorsanız, bunu Docker desteği ekleyerek yapabilirsiniz.  Bir sonraki düzey, seçtiğiniz belirli bir Orchestrator için uygun destek dosyaları ekleyen kapsayıcı düzenleme destedir.  

Visual Studio 2019 ile Docker Compose, Kubernetes ve Service Fabric kapsayıcı düzenleme hizmetleri olarak kullanabilirsiniz.

> [!NOTE]
> Tam .NET Framework konsol projesi şablonu kullanıyorsanız, desteklenen seçenek, Proje oluşturulduktan sonra, Service Fabric veya Docker Compose kullanma seçenekleriyle **kapsayıcı Orchestrator desteği ekler** . Proje oluşturma sırasında destek ekleme ve düzenleme olmadan tek bir proje için **Docker desteği ekleme** seçeneği kullanılamaz.

Visual Studio 2019 sürüm 16,4 ve sonraki sürümlerde **kapsayıcılar** penceresi kullanılabilir; Bu, çalışan kapsayıcıları görüntülemenize, kullanılabilir görüntülere gözatmanıza, ortam değişkenlerini, günlüklere ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemini incelemenize, hata ayıklayıcı eklemenize veya kapsayıcı ortamında bir Terminal penceresi açmaya olanak sağlar. Bkz. [Visual Studio 'da kapsayıcıları ve görüntüleri görüntüleme ve tanılama](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Docker desteği ekleme

Aşağıdaki ekran görüntüsünde gösterildiği gibi yeni bir proje oluştururken **Docker desteğini etkinleştir** ' i seçerek proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz:

::: moniker range="vs-2017"
![Visual Studio 'da yeni ASP.NET Core Web uygulaması için Docker desteğini etkinleştir](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Visual Studio 'da yeni ASP.NET Core Web uygulaması için Docker desteğini etkinleştir](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> .NET Framework projeler (.NET Core değil) için yalnızca Windows kapsayıcıları kullanılabilir.

**Çözüm Gezgini**Içinde > **Docker desteği** **Ekle** ' ye tıklayarak mevcut bir projeye Docker desteği ekleyebilirsiniz. **> Docker desteği ekleme** ve **ekleme > kapsayıcı Orchestrator destek** komutları, aşağıdaki ekran görüntüsünde gösterildiği gibi, **Çözüm Gezgini**içindeki bir ASP.NET Core projesi için proje düğümünün sağ tıklama menüsünde (veya bağlam menüsü) bulunur:

![Visual Studio 'da Docker desteği Ekle menü seçeneği](./media/overview/add-docker-support-menu.png)

Docker desteğini eklediğinizde veya etkinleştirdiğinizde, Visual Studio aşağıdakileri projeye ekler:

- *Dockerfile* dosyası
- bir. dockerıgnore dosyası
- Microsoft. VisualStudio. Azure. containers. Tools. targets için bir NuGet paketi başvurusu

::: moniker range=">=vs-2019"
Docker desteği eklediğinizde çözüm şöyle görünür:

![Dockerfile ve. dockerıgnore dosyası ile Çözüm Gezgini 'nin ekran görüntüsü](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Aşağıdaki ekran görüntüsünde gösterildiği gibi bir ASP.NET projesi (.NET Framework, .NET Core projesi değil) için proje oluşturma sırasında Docker desteğini etkinleştirdiğinizde, kapsayıcı düzenleme desteği de eklenir.

![Bir ASP.NET projesi için Docker Compose desteğini etkinleştir](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Docker Compose desteği

Docker Compose kullanarak çok kapsayıcılı bir çözüm oluşturmak istediğinizde, projelerinize kapsayıcı düzenleme desteği ekleyin. Bu, aynı *Docker-Compose. yıml* dosyasında tanımlandıklarında bir kapsayıcı grubunu (bir bütün çözüm veya proje grubu) aynı anda çalıştırmanızı ve hata ayıklamanıza olanak tanır.

Docker Compose kullanarak kapsayıcı düzenleme desteği eklemek için, **Çözüm Gezgini**çözüm veya proje düğümüne sağ tıklayın ve **> kapsayıcı düzenleme desteği ekle**' yi seçin. Sonra kapsayıcıları yönetmek için **Docker Compose** öğesini seçin.

Projenize kapsayıcı düzenleme desteğini ekledikten sonra, burada gösterildiği gibi, projeye bir *Dockerfile* (zaten bir tane yoksa) ve **Çözüm Gezgini**çözüme eklenen bir **Docker-Compose** klasörü görürsünüz:

![Visual Studio 'da Çözüm Gezgini Docker dosyaları](media/overview/docker-support-solution-explorer.png)

*Docker-Compose. yml* zaten varsa, Visual Studio buna yalnızca gerekli olan yapılandırma kodu satırlarını ekler.

Docker Compose kullanarak denetlemek istediğiniz diğer projelerle işlemi tekrarlayın.

## <a name="kubernetes-support"></a>Kubernetes desteği

::: moniker range="vs-2017"
Kubernetes desteği eklemek için [Kubernetes için Visual Studio Araçları](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)' yi çalıştırın.
::: moniker-end

Kubernetes desteğiyle, [Azure Kubernetes Service 'te (aks)](/azure/aks)çalışan yerel projeniz Ile Kubernetes kümesi arasında bir bağlantıyı etkinleştirebilir ve böylece Visual Studio kullanarak aks 'te çalışan hizmetlerinizi değiştirebilir ve hatalarını ayıklayabilirsiniz.  Bu hizmet [Azure dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio)tarafından sağlanır. Azure Dev Spaces Ayrıca, geliştirme amacıyla *dev alanları* adında Kubernetes hizmetlerinizin ayrı dallarını ayarlamanıza olanak tanıyarak, üretim hizmetlerini geliştirme sırasında çalışma sürümlerinden verimli bir şekilde ayırabilmeniz ve farklı değişiklikleri birbirinden düzgün bir şekilde ayrı tutmanız gerekir.

Projelerinize Kubernetes desteği eklemek için, kapsayıcı düzenleme desteği eklediğinizde **Kubernetes/Held** öğesini seçin. Projenize, Kubernetes hizmetlerinizin yapısını açıklayan Azure Dev Spaces ve Held grafiklerini yapılandıran *azds. YAML*dahil olmak üzere birkaç dosya eklenir.

## <a name="service-fabric-support"></a>Service Fabric desteği

Visual Studio 'da Service Fabric araçlarla Azure Service Fabric geliştirebilir ve hata ayıklayın, yerel olarak çalıştırıp hata ayıklayın ve Azure 'a dağıtabilirsiniz.

::: moniker range="vs-2017"
Azure geliştirme iş yükü yüklü olan Visual Studio 2017 sürüm 15,9 ve üzeri, Windows kapsayıcıları ve Service Fabric düzenleme kullanarak Kapsayıcılı mikro hizmetler geliştirmeyi destekler.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019, Windows kapsayıcıları ve Service Fabric düzenleme kullanarak Kapsayıcılı mikro hizmetler geliştirmeyi destekler.
::: moniker-end

Ayrıntılı bir öğretici için bkz. [öğretici: Windows kapsayıcısında bir .NET uygulamasını Azure Service Fabric dağıtma](/azure/service-fabric/service-fabric-host-app-in-a-container).

Azure Service Fabric hakkında daha fazla bilgi için bkz. [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Sürekli teslim ve sürekli tümleştirme (CI/CD)

Visual Studio, otomatik ve sürekli tümleştirme ve hizmet kodunuzda ve yapılandırmanızda yapılan değişikliklerin teslimi için Azure Pipelines ile tümleşir. Başlamak için bkz. [ilk işlem hattınızı oluşturma](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

Service Fabric için bkz. [öğretici: ASP.NET Core uygulamanızı Azure 'A dağıtma Service Fabric Azure DevOps Projeleri kullanarak](/azure/devops-project/azure-devops-project-service-fabric).

Kubernetes için bkz. [Azure Kubernetes hizmetine Docker kapsayıcı uygulaması dağıtma](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops).

## <a name="next-steps"></a>Sonraki adımlar

Hizmetler uygulamasıyla ve kapsayıcılarla çalışma için Visual Studio araçlarının kullanımına ilişkin daha fazla bilgi için aşağıdaki makaleleri okuyun:

[Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama](edit-and-refresh.md)

[Visual Studio 'Yu kullanarak bir kapsayıcı kayıt defterine ASP.NET kapsayıcısını dağıtma](hosting-web-apps-in-docker.md)
