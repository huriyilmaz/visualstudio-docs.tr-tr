---
title: Windows'da Visual Studio Konteyner Araçları
description: Docker ile çalışmak için Visual Studio'da bulunan araçları tanıyın
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0d5859016a02de259c24c213c6cfef8cb5fce005
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75916561"
---
# <a name="container-tools-in-visual-studio"></a>Visual Studio’da Kapsayıcı Araçları

Kapsayıcılarla geliştirme için Visual Studio'da bulunan araçların kullanımı kolaydır ve kapsayıcı uygulamalar için bina, hata ayıklama ve dağıtımı büyük ölçüde kolaylaştırır. Tek bir proje için bir kapsayıcıyla çalışabilir veya konteynerlerde birden çok hizmetle çalışmak için Docker Compose, Service Fabric veya Kubernetes ile konteyner orkestrasyonu kullanabilirsiniz.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Web **Geliştirme,** **Azure Araçları** iş yükü ve/veya **.NET Core çapraz platform geliştirme** iş yükü yüklü
* Azure Kapsayıcı Kayıt Defteri'nde yayımlamak için bir Azure aboneliği. [Ücretsiz deneme sürümü için kaydolun.](https://azure.microsoft.com/offers/ms-azr-0044p/)

## <a name="docker-support-in-visual-studio"></a>Visual Studio'da Docker desteği

ASP.NET projeler, ASP.NET Core projeleri ve .NET Core ve .NET Framework konsol projeleri için Docker desteği mevcuttur.

Visual Studio Docker desteği müşteri ihtiyaçlarına yanıt olarak bültenleri bir dizi üzerinde değişti. Bir projeye ekleyebileceğiniz iki Docker desteği düzeyi vardır ve desteklenen seçenekler projenin türüne ve Visual Studio sürümüne göre değişir. Desteklenen bazı proje türleri ile, sadece tek bir proje için bir kapsayıcı istiyorsanız, orkestrasyon kullanmadan, Docker desteği ekleyerek bunu yapabilirsiniz.  Bir sonraki düzey, seçtiğiniz belirli orkestratör için uygun destek dosyaları ekleyen konteyner orkestrasyon desteğidir.  

Visual Studio 2017 ile Docker Compose ve Service Fabric'i konteyner orkestrasyon hizmeti olarak kullanabilirsiniz.  [Kubernetes için Visual Studio Araçlarını](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)yüklerseniz Kubernetes'i de kullanabilirsiniz.

> [!NOTE]
> Visual Studio 2017'nin 15.8'den önce bir sürümünü kullanıyorsanız veya .NET Framework proje şablonu (.NET Core değil) kullanıyorsanız, Docker desteği eklerken Docker Compose'u kullanarak orkestrasyon desteği otomatik olarak eklenir. Docker Compose aracılığıyla konteyner orkestrasyon desteği Visual Studio 2017 sürümleri 15.0 ile 15.7 ve .NET Framework projelerine otomatik olarak eklenir.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) Web **Geliştirme,** **Azure Araçları** iş yükü ve/veya **.NET Core çapraz platform geliştirme** iş yükü yüklü
* .NET Core ile geliştirme için [.NET Çekirdek Geliştirme Araçları.](https://dotnet.microsoft.com/download/dotnet-core/)
* Azure Kapsayıcı Kayıt Defteri'nde yayımlamak için bir Azure aboneliği. [Ücretsiz deneme sürümü için kaydolun.](https://azure.microsoft.com/offers/ms-azr-0044p/)

## <a name="docker-support-in-visual-studio"></a>Visual Studio'da Docker desteği

ASP.NET projeler, ASP.NET Core projeleri ve .NET Core ve .NET Framework konsol projeleri için Docker desteği mevcuttur.

Visual Studio Docker desteği müşteri ihtiyaçlarına yanıt olarak bültenleri bir dizi üzerinde değişti. Bir projeye ekleyebileceğiniz iki Docker desteği düzeyi vardır ve desteklenen seçenekler projenin türüne ve Visual Studio sürümüne göre değişir. Desteklenen bazı proje türleri ile, sadece tek bir proje için bir kapsayıcı istiyorsanız, orkestrasyon kullanmadan, Docker desteği ekleyerek bunu yapabilirsiniz.  Bir sonraki düzey, seçtiğiniz belirli orkestratör için uygun destek dosyaları ekleyen konteyner orkestrasyon desteğidir.  

Visual Studio 2019 ile Docker Compose, Kubernetes ve Service Fabric'i konteyner orkestrasyon hizmeti olarak kullanabilirsiniz.

> [!NOTE]
> Tam .NET Framework konsolu proje şablonu kullanıyorsanız, desteklenen seçenek, Hizmet Kumaşı veya Docker Compose'u kullanma seçenekleriyle birlikte proje oluşturulduktan sonra **Kapsayıcı Orchestrator desteği** ekle seçeneğidir. Proje oluşturmada destek ekleme ve düzenleme olmadan tek bir proje için **Docker desteği ekleme** seçeneği kullanılamaz.

Visual Studio 2019 sürüm 16.4 ve sonraki sürümlerinde, **kapsayıcılar** penceresi kullanılabilir, çalışan kapsayıcıları görüntülemenize, kullanılabilir görüntülere göz atmanıza, ortam değişkenlerine, günlüklere ve bağlantı noktası eşlemelerine göz atmanıza, dosya sistemini incelemenize, hata ayıklayıcı eklemenize veya kapsayıcı ortamının içinde bir terminal penceresi açmanıza olanak tanır. [Bkz. Visual Studio'da kapsayıcıları ve görüntüleri görüntüleyin ve tanılayın.](view-and-diagnose-containers.md)

::: moniker-end

### <a name="adding-docker-support"></a>Docker desteği ekleme

Aşağıdaki ekran görüntüsünde gösterildiği gibi, yeni bir proje oluştururken **Docker Desteğini Etkinleştir'i** seçerek proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz:

::: moniker range="vs-2017"
![Visual Studio'da yeni ASP.NET Core web uygulaması için Docker Desteği etkinleştirin](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Visual Studio'da yeni ASP.NET Core web uygulaması için Docker Desteği etkinleştirin](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> .NET Framework projeleri için (.NET Core değil), yalnızca Windows kapsayıcıları kullanılabilir.

**Çözüm Gezgini'nde**Docker Desteği **Ekle'yi** > seçerek varolan bir projeye**Docker desteği** ekleyebilirsiniz. > **Docker Desteği Ekle** ve Ekle > Kapsayıcı **Orchestrator Destek** komutları, aşağıdaki ekran görüntüsünde gösterildiği **gibi, Solution Explorer'daki**ASP.NET Çekirdek projesi için proje düğümünün sağ tıklama menüsünde (veya bağlam menüsünde) yer alır:

![Visual Studio'da Docker Destek menüsü ekle seçeneği](./media/overview/add-docker-support-menu.png)

Docker desteği eklediğinizde veya etkinleştirdiğinizde, Visual Studio projeye aşağıdakileri ekler:

- *Dockerfile* dosyası
- bir .dockerignore dosyası
- Microsoft.VisualStudio.Azure.Containers.Tools.Targets için bir NuGet paketi başvurusu

::: moniker range=">=vs-2019"
Docker desteği eklediğinizde çözüm şuna benzer:

![Dockerfile ve .dockerignore dosyası ile çözüm gezgininin ekran görüntüsü](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Aşağıdaki ekran görüntüsünde gösterildiği gibi, ASP.NET bir proje (.NET Core projesi değil,.NET Framework) için proje oluşturma sırasında Docker desteğini etkinleştirdiğinizde, konteyner düzenleme desteği de eklenir.

![ASP.NET bir proje için Docker'ın destek oluşturmasını etkinleştirme](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Docker Compose desteği

Docker Compose'u kullanarak çok kapsayıcılı bir çözüm oluşturmak istediğinizde, projelerinize konteyner düzenleme desteği ekleyin. Bu, aynı *docker-compose.yml* dosyasında tanımlanmışsa, bir kapsayıcı grubunu (tüm çözüm veya proje grubu) aynı anda çalıştırmanızı ve hata ayıklamanızı sağlar.

Docker Compose'u kullanarak konteyner düzenleme desteği eklemek için **Solution Explorer'daki**çözüm veya proje düğümüne sağ tıklayın ve **> Kapsayıcı Düzenleme Desteği Ekle'yi**seçin. Ardından, konteynerleri yönetmek için **Docker Compose'u** seçin.

Projenize kapsayıcı düzenleme desteği ekledikten sonra, projeye bir *Dockerfile* eklenmiştir (zaten bir tane yoksa) ve **Çözüm Gezgini'nde**çözüme eklenen bir **docker-compose** klasörü burada gösterildiği gibi:

![Visual Studio'da Solution Explorer'da Docker dosyaları](media/overview/docker-support-solution-explorer.png)

*Docker-compose.yml* zaten varsa, Visual Studio sadece yapılandırma kodu gerekli satırları ekler.

Docker Compose'u kullanarak kontrol etmek istediğiniz diğer projelerle işlemi yineleyin.

## <a name="kubernetes-support"></a>Kubernetes desteği

::: moniker range="vs-2017"
Kubernetes desteği eklemek [için, Kubernetes için Visual Studio Araçlarını](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)yükleyin.
::: moniker-end

Kubernetes desteği ile, yerel projeniz ile [Azure Kubernetes Hizmeti 'nde (AKS)](/azure/aks)çalışan bir Kubernetes kümesi arasında bağlantı kurabilir ve bu nedenle Visual Studio'yı kullanarak AKS'de çalışan hizmetlerinizi değiştirebilir ve hata ayıklayabilirsiniz.  Bu hizmet [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio)tarafından sağlanmaktadır. Azure Dev Alanları ayrıca geliştirme amacıyla *geliştirme alanları* olarak adlandırılan Kubernetes hizmetlerinizin ayrı dallarını kurmanıza olanak tanır, böylece üretim hizmetlerini geliştirme deki çalışma sürümlerinden verimli bir şekilde yalıtabilir ve farklı değişiklikleri birbirinden temiz bir şekilde ayrı tutabilirsiniz.

Projelerinize Kubernetes desteği eklemek için konteyner orkestrasyon desteği eklerken **Kubernetes/Helm'i** seçin. Azure Dev Spaces'i yapılandıran *azds.yaml*ve Kubernetes hizmetlerinizin yapısını açıklayan Miğfer grafikleri dahil olmak üzere projenize çeşitli dosyalar eklenir.

## <a name="service-fabric-support"></a>Service Fabric desteği

Visual Studio'daki Service Fabric araçlarıyla Azure Hizmet Kumaşı için hata ayıklama geliştirebilir ve hata ayıklayabilir, yerel olarak çalıştırabilir ve hata ayıklayabilir ve Azure'a dağıtabilirsiniz.

::: moniker range="vs-2017"
Visual Studio 2017 sürüm 15.9 ve daha sonra Azure geliştirme iş yükü yüklü windows kapsayıcılar ve Service Fabric orkestrasyon kullanarak kapsayıcı mikro hizmetler geliştirme destekler.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019, Windows kapları ve Service Fabric orkestrasyonu kullanarak konteynermikro hizmetlerinin geliştirilmesini destekler.
::: moniker-end

Ayrıntılı bir öğretici için [Bkz. Öğretici: Bir .NET uygulamasını Windows kapsayıcısında Azure Hizmet Kumaşı'na dağıtın.](/azure/service-fabric/service-fabric-host-app-in-a-container)

Azure Hizmet Kumaşı hakkında daha fazla bilgi için [Hizmet Kumaşı'na](/azure/service-fabric)bakın.

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Sürekli teslimat ve sürekli entegrasyon (CI/CD)

Visual Studio, servis kodunuzda ve yapılandırmanızda yapılan değişikliklerin otomatik ve sürekli entegrasyonu ve teslimi için Azure Boru Hatları ile kolayca entegre edilmiştir. Başlamak için [bkz.](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)

Hizmet Kumaşı için [Bkz. Öğretici: Azure DevOps Projelerini kullanarak ASP.NET Core uygulamanızı Azure Hizmet Kumaşı'na dağıtın.](/azure/devops-project/azure-devops-project-service-fabric)

Kubernetes için, [Azure Kubernetes Hizmetine Docker konteyner uygulaması dağıt'a](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops)bakın.

## <a name="next-steps"></a>Sonraki adımlar

Hizmet uygulaması ve kapsayıcılarla çalışmak için Visual Studio araçlarının kullanımı hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

[Yerel Docker kapsayıcısındaki uygulamalar için hata ayıklama](edit-and-refresh.md)

[Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma](hosting-web-apps-in-docker.md)
