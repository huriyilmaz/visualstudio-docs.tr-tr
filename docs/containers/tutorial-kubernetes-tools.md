---
title: Kubernetes araçları öğretici | Microsoft Dokümanlar
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 931f8c2a6d3be130ef78f59f9b3853d28fad8cd4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444693"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Visual Studio Kubernetes Tools ile başlayın

Visual Studio Kubernetes Tools, Kubernetes'i hedefleyen konteyner uygulamalarının geliştirilmesini kolaylaştırmalarına yardımcı olur. Visual Studio, Dockerfiles ve Helm grafikleri gibi Kubernetes dağıtımını desteklemek için gereken kod olarak yapılandırma dosyalarını otomatik olarak oluşturabilir. Azure Dev Spaces'i kullanarak canlı bir Azure Kubernetes Hizmeti (AKS) kümesinde kodunuzu ayıklayabilir veya Visual Studio'nun içinden doğrudan bir AKS kümesinde yayımlayabilirsiniz.

Bu öğretici, bir projeye Kubernetes desteği eklemek ve AKS'de yayınlamak için Visual Studio'nun kullanılmasını kapsar. AkS'te çalışan projenizi hata ayıklamak ve test etmek için [Azure Dev Spaces'i](/azure/dev-spaces/) kullanmak istiyorsanız, bunun yerine [Azure Dev Spaces öğreticisine](/azure/dev-spaces/get-started-netcore-visualstudio) atlayabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

Bu yeni işlevselliği kullanabilmek için şunları yapmanız gerekir:

::: moniker range="vs-2017"
- Visual Studio [2017'nin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) *ASP.NET ve web geliştirme* iş yüküyle en son sürümü.
- [Visual Studio için Kubernetes araçları](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), ayrı bir indirme olarak kullanılabilir.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) *ASP.NET ve web geliştirme* iş yükü ile.
::: moniker-end
- Docker görüntüleri oluşturmak, yerel olarak çalışan Docker konteynerlerini hata ayıklamak veya AKS'de yayınlamak [istiyorsanız, Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) geliştirme iş istasyonuna (diğer bir yerde Visual Studio'yu çalıştırdığınız) yüklenir. (Azure *not* Dev Spaces kullanarak AKS'de Docker kapsayıcıları oluşturmak ve hata ayıklama için Docker gerekmez.)
::: moniker range="vs-2017"
- Visual Studio'dan AKS'ye yayımlamak isterseniz (Azure Dev Spaces kullanarak AKS'de hata ayıklama için gerekli*değildir):*

    1. [AKS yayımlama araçları](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), ayrı bir indirme olarak kullanılabilir.

    1. Azure Kubernetes Hizmet kümesi. Daha fazla bilgi için [bkz.](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster) Geliştirme iş istasyonunuzdan [kümeye bağlandığından](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) emin olun.

    1. Helm CLI geliştirme iş istasyonunuzun üzerine yüklenir. Daha fazla bilgi için [bkz: Yükleme Helm.](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md)

    1. Komutu `helm init` kullanarak AKS kümenize karşı yapılandırılan miğfer. Bunun nasıl yapılacılaştırılaçılacıyla ilgili daha fazla bilgi için Helm' i nasıl [yapıla](/azure/aks/kubernetes-helm#configure-helm)
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Yeni bir Kubernetes projesi oluşturun

::: moniker range="vs-2017"

Uygun araçları yükledikten sonra Visual Studio'yu başlatın ve yeni bir proje oluşturun. **Bulut**altında, **Kubernetes** proje türü için Konteyner Uygulamasını seçin. Bu proje türünü seçin ve **Tamam'ı**seçin.

![Yeni bir Kubernetes uygulama projesi oluşturma ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Visual Studio başlangıç penceresinde, *Kubernetes*için arama ve **Kubernetes için Konteyner Uygulama**seçin.

![Yeni bir Kubernetes uygulama projesi oluşturma ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Proje adını sağlayın.

![Yeni bir Kubernetes uygulama projesi oluşturma ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Daha sonra oluşturmak için ASP.NET Web uygulaması türü seçebilirsiniz. **Web Uygulaması**seçin. Her zamanki **Docker Destek** seçeneğini etkinleştir seçeneği bu iletişim kutusunda görünmez.  Docker desteği, Kubernetes için bir kapsayıcı uygulaması için varsayılan olarak etkinleştirilir.

::: moniker range="vs-2017"

![Web uygulaması seçiminin ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Web uygulaması seçiminin ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Mevcut bir projeye Kubernetes desteği ekleme

Alternatif olarak, mevcut bir ASP.NET Core web uygulama projesine Kubernetes desteği ekleyebilirsiniz. Bunu yapmak için projeye sağ tıklayın ve**Kapsayıcı Orkestratör Desteği** **Ekle'yi** > seçin.

::: moniker range="vs-2017"

![Kapsayıcı Orkestrator ekle menü öğesinin ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Kapsayıcı Orkestrator ekle menü öğesinin ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

İletişim kutusunda **Kubernetes/Helm'i** seçin ve **Tamam'ı**seçin.

![Kapsayıcı Düzenle iletişim kutusunun ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Visual Studio sizin için neler yaratıyor

**Kubernetes** projesi için yeni bir Konteyner Uygulaması oluşturduktan veya mevcut bir projeye Kubernetes konteyner orkestrator desteği ekledikten sonra, projenizde Kubernetes'e dağıtımı kolaylaştıran bazı ek dosyalar görürsünüz.

::: moniker range="vs-2017"

![Konteyner Orchestrator desteği ekledikten sonra Solution Explorer ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Konteyner Orchestrator desteği ekledikten sonra Solution Explorer ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Eklenen dosyalar şunlardır:

- Bu web uygulaması barındıran bir Docker konteyner görüntü oluşturmanıza olanak sağlayan bir Dockerfile. Göreceğiniz gibi, Visual Studio aracı, Kubernetes'e hata ayıklarken ve dağıtılırken bu Dockerfile'den yararlanır. Doğrudan Docker görüntüsüyle çalışmayı tercih ederseniz, Dockerfile'a sağ tıklayıp **Docker Image Oluştur'u**seçebilirsiniz.

   ![Yapı Docker Image seçeneğinin ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- Bir Miğfer grafiği ve *bir grafik* klasörü. Bu yaml dosyaları, uygulamanın Miğfer grafiğini oluşturan ve kubernetes'e dağıtmak için kullanabileceğiniz. Helm hakkında daha fazla [https://www.helm.sh](https://www.helm.sh)bilgi için bkz.

- *azds.yaml*. Bu, Azure Kubernetes Hizmetinde hızlı ve yinelemeli hata ayıklama deneyimi sağlayan Azure Dev Spaces ayarlarını içerir. Daha fazla bilgi için [Azure Geliştirme Alanları belgelerine](/azure/dev-spaces/azure-dev-spaces)bakın.

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Hizmetinde Yayımla (AKS)

Tüm bu dosyalar yerinde olduğu için, her zaman olduğu gibi uygulama kodunuzu yazmak ve hata ayıklamak için Visual Studio IDE'yi kullanabilirsiniz. [AkS](/azure/dev-spaces/) kümesinde canlı olarak çalışan kodunuzu hızlı bir şekilde çalıştırmak ve hata ayıklamak için Azure Dev Spaces'i de kullanabilirsiniz. Daha fazla bilgi için lütfen [Azure Dev Spaces öğreticisine](/azure/dev-spaces/get-started-netcore-visualstudio) başvurun

Kodunuzu istediğiniz şekilde çalıştırdıktan sonra, doğrudan Visual Studio'dan bir AKS kümesine yayımlayabilirsiniz.

Bunu yapmak için, öncelikle AKS'ye yayımlanmak üzere öğenin altındaki [Ön koşullar](#prerequisites) bölümünde açıklandığı gibi her şeyi yüklediğinizi iki kez kontrol etmeniz ve bağlantılarda verilen tüm komut satırı adımlarını çalıştırmanız gerekir. Ardından, kapsayıcı resminizi Azure Kapsayıcı Kayıt Defteri'ne (ACR) yayımlayan bir yayımlama profili ayarlayın. Ardından AKS, kapsayıcı görüntünüze ACR'den çekerek kümeye dağıtabilir.

1. **Çözüm Gezgini'nde,** *projenize* sağ tıklayın ve **Yayımla'yı**seçin.

   ![Yayımla menü öğesinin ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. **Yayımla** ekranında, yayımlama hedefi olarak **Konteyner Kayıt Defteri'ni** seçin ve konteyner kayıt defterinizi seçmek için istemleri izleyin. Zaten bir kapsayıcı kayıt defteriniz yoksa, Visual Studio'dan bir tane oluşturmak için **Yeni Azure Kapsayıcı Kayıt Defteri Oluştur'u** seçin. Daha fazla bilgi için [bkz.](hosting-web-apps-in-docker.md)

   ![Yayımlama hedef ekranı seçme](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Solution Explorer'a geri dön, *çözümünüzü* sağ tıklatın ve **Azure AKS'ye Yayımla'yı**tıklatın.

   ![Azure AKS menü öğesine Yayımla ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Aboneliğinizi ve AKS kümenizi ve yeni oluşturduğunuz ACR yayımlama profilini seçin. Ardından **Tamam**'a tıklayın.

   ![AKS ekranına Yayın ekranında ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Bu, sizi **Azure AKS'ye Yayımla** ekranına götürür.

5. Sunucuya Helm grafiklerini yüklemek için kullanılan komut satırını güncelleştirmek için **Yapılandırma Miğferi** bağlantısını seçin.

   ![Helm'i Yapılandırışla bağlantısının ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Komut satırının güncelleştirilmesi, farklı bir Kubernetes bağlamı veya grafik adı gibi belirtmek istediğiniz özel komut satırı bağımsız değişkenleri varsa yararlıdır.

   ![Miğfer yapılandırma ekranının ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Dağıtmaya hazır olduğunuzda, uygulamanızı AKS'de yayınlamak için **Yayımla** düğmesini tıklatın.

   ![Azure AKS ekranında yayımlama ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Tebrikler! Artık Tüm Kubernetes uygulama geliştirme için Visual Studio'nun tüm gücünü kullanabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[AKS belgelerini](/azure/aks)okuyarak Azure'daki Kubernetes geliştirme hakkında daha fazla bilgi edinin.

[Azure Dev Spaces belgelerini](/azure/dev-spaces/) okuyarak Azure Geliştirme Alanları hakkında daha fazla bilgi edinin
