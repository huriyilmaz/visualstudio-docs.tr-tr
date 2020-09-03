---
title: Kubernetes araçları öğreticisi | Microsoft Docs
ms.date: 06/08/2018
ms.topic: tutorial
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 7778019e73119a4b8b1a5842bb7a8c04ef017143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913306"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Visual Studio Kubernetes araçlarını kullanmaya başlama

Visual Studio Kubernetes araçları, Kubernetes 'i hedefleyen Kapsayıcılı uygulamaların geliştirilmesini kolaylaştırmaya yardımcı olur. Visual Studio, Dockerfiles ve Held grafikleri gibi Kubernetes dağıtımını desteklemek için gereken yapılandırma olarak yapılandırma dosyalarını otomatik olarak oluşturabilir. Azure Dev Spaces kullanarak canlı bir Azure Kubernetes hizmeti (AKS) kümesinde kodunuzda hata ayıklayın veya doğrudan Visual Studio içinden bir AKS kümesinde yayımlayabilirsiniz.

Bu öğreticide, bir projeye Kubernetes desteği eklemek ve AKS 'de yayımlamak için Visual Studio kullanımı ele alınmaktadır. Birincil olarak [Azure dev Spaces](/azure/dev-spaces/) kullanarak projenizi hata ayıklamakta ve test etmek için kullanmak istiyorsanız, bunun yerine [Azure dev Spaces öğreticiye](/azure/dev-spaces/get-started-netcore-visualstudio) atlayabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

Bu yeni işlevsellikten yararlanmak için şunlar gerekir:

::: moniker range="vs-2017"
- *ASP.net ve Web geliştirme* iş yüküyle [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ' nin en son sürümü.
- [Visual Studio Için Kubernetes araçları](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), ayrı bir indirme olarak sunulmaktadır.
::: moniker-end
::: moniker range="vs-2019"
- *ASP.net ve Web geliştirme* iş yüküyle [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) .
::: moniker-end
- Geliştirme iş istasyonunuzda yüklü [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) (yani, Visual Studio 'yu çalıştırdığınız), Docker görüntülerini derlemek, yerel olarak çalışan Docker kapsayıcılarında hata ayıklamak veya aks 'de yayımlamak istiyorsanız. (Azure Dev Spaces kullanarak AKS 'te Docker Kapsayıcıları oluşturmak ve hatalarını ayıklamak için Docker gerekli *değildir* .)
::: moniker range="vs-2017"
- Visual Studio 'dan AKS 'e yayınlamak istiyorsanız (Azure Dev Spaces kullanarak AKS 'de hata ayıklama için gerekli*değildir* ):

    1. [Aks yayımlama araçları](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), ayrı bir indirme olarak kullanılabilir.

    1. Bir Azure Kubernetes hizmet kümesi. Daha fazla bilgi için bkz. [AKS kümesi oluşturma](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Geliştirme iş istasyonunuzdan [kümeye bağlandığınızdan](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) emin olun.

    1. Geliştirme iş istasyonunuza yüklenen Held CLı. Daha fazla bilgi için bkz. [Held 'Yi yükleme](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md).

    1. Komutunu kullanarak AKS kümenize göre yapılandırılmış helk `helm init` . Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [Held 'yi yapılandırma](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Yeni bir Kubernetes projesi oluşturma

::: moniker range="vs-2017"

Uygun araçları yükledikten sonra Visual Studio 'Yu başlatın ve yeni bir proje oluşturun. **Bulut**altında **Kubernetes proje türü için kapsayıcı uygulamasını** seçin. Bu proje türünü seçin ve **Tamam**' ı seçin.

![Yeni bir Kubernetes uygulama projesi oluşturma ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Visual Studio başlangıç penceresinde *Kubernetes*' i arayın ve **Kubernetes için kapsayıcı uygulamasını**seçin.

![Yeni bir Kubernetes uygulama projesi oluşturma ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Proje adını belirtin.

![Yeni bir Kubernetes uygulama projesi oluşturma ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Sonra, oluşturulacak ASP.NET Core Web uygulaması türünü seçebilirsiniz. **Web uygulaması**' nı seçin. Her zamanki **Docker desteğini etkinleştir** seçeneği bu iletişim kutusunda görünmüyor.  Docker desteği, Kubernetes için bir kapsayıcı uygulaması için varsayılan olarak etkindir.

::: moniker range="vs-2017"

![Web uygulaması seçiminin ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Web uygulaması seçiminin ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Var olan bir projeye Kubernetes desteği ekleme

Alternatif olarak, var olan bir ASP.NET Core Web uygulaması projesine Kubernetes desteği ekleyebilirsiniz. Bunu yapmak için projeye sağ tıklayın ve **Add**  >  **kapsayıcı Orchestrator desteği**Ekle ' yi seçin.

::: moniker range="vs-2017"

![Kapsayıcı Orchestrator menü öğesi Ekle ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Kapsayıcı Orchestrator menü öğesi Ekle ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

İletişim kutusunda **Kubernetes/HELI** ' yi seçin ve **Tamam**' ı seçin.

![Kapsayıcı Orchestrator Ekle iletişim kutusunun ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Sizin için Visual Studio tarafından oluşturulan

**Kubernetes projesi için yeni bir kapsayıcı uygulaması** oluşturduktan veya var olan bir projeye Kubernetes kapsayıcı Orchestrator desteği eklendikten sonra, projenizde Kubernetes 'e dağıtımı kolaylaştıran bazı ek dosyalar görürsünüz.

::: moniker range="vs-2017"

![Kapsayıcı Orchestrator desteği eklendikten sonra Çözüm Gezgini ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Kapsayıcı Orchestrator desteği eklendikten sonra Çözüm Gezgini ekran görüntüsü](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Eklenen dosyalar şunlardır:

- Bu Web uygulamasını barındıran bir Docker kapsayıcı görüntüsü oluşturmanıza olanak sağlayan bir Dockerfile. Gördüğünüz gibi, Visual Studio Araçları hata ayıklarken ve Kubernetes 'e dağıtıldığında bu Dockerfile 'ı kullanır. Docker görüntüsüyle doğrudan çalışmayı tercih ediyorsanız Dockerfile dosyasına sağ tıklayıp **Docker görüntüsü oluştur**' u seçebilirsiniz.

   ![Build Docker Image seçeneğinin ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- HELI grafiği ve bir *grafik* klasörü. Bu YAML dosyaları, uygulama için Kubernetes 'e dağıtmak için kullanabileceğiniz helk grafiğini yapar. Held hakkında daha fazla bilgi için bkz [https://www.helm.sh](https://www.helm.sh) ..

- *AZD. YAML*. Bu, Azure Kubernetes hizmetinde hızlı ve yinelemeli bir hata ayıklama deneyimi sağlayan Azure Dev Spaces için ayarları içerir. Daha fazla bilgi için [Azure dev Spaces belgelerine](/azure/dev-spaces/azure-dev-spaces)bakın.

:::moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Azure Kubernetes hizmeti 'ne (AKS) yayımlama

Tüm bu dosyalar yerinde olduğunda, her zaman sahip olduğunuz gibi uygulama kodunuzu yazmak ve hatalarını ayıklamak için Visual Studio IDE 'yi kullanabilirsiniz. Ayrıca, bir AKS kümesinde canlı çalışan kodunuzda hızlı bir şekilde çalıştırmak ve hata ayıklamak için [Azure dev Spaces](/azure/dev-spaces/) de kullanabilirsiniz. Daha fazla bilgi için lütfen [Azure dev Spaces öğreticisine](/azure/dev-spaces/get-started-netcore-visualstudio) başvurun

Kodunuzun istediğiniz şekilde çalışmasını tamamladıktan sonra doğrudan Visual Studio 'dan bir AKS kümesine yayımlayabilirsiniz.

Bunu yapmak için ilk olarak, AKS 'de yayımlama için öğenin altındaki [Önkoşullar](#prerequisites) bölümünde açıklandığı gibi her şeyi ve bağlantılarınızda verilen tüm komut satırı adımlarını kullanarak bir kez daha yüklemeniz gerekir. Ardından, kapsayıcı görüntünüzü yayımlayan bir yayımlama profili ayarlayın Azure Container Registry (ACR). Daha sonra AKS, kendi kapsayıcı görüntünüzü ACR 'den çekebilir ve kümeye dağıtabilir.

1. **Çözüm Gezgini**, *projenize* sağ tıklayın ve **Yayımla**' yı seçin.

   ![Yayımla menü öğesinin ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. **Yayımla** ekranında, Yayımla hedefi olarak **Container Registry** öğesini seçin ve kapsayıcı kayıt defterinizi seçmek için istemleri izleyin. Henüz bir kapsayıcı kayıt defteriniz yoksa, Visual Studio 'dan bir tane oluşturmak için **yeni Azure Container Registry oluştur** ' u seçin. Daha fazla bilgi için bkz. [Azure Container Registry kapsayıcınızı yayımlama](hosting-web-apps-in-docker.md).

   ![Bir Yayımla hedefi seç ekranının ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Çözüm Gezgini geri dönüp *çözümünüze* sağ tıklayıp **Azure aks ' e Yayımla**' ya tıklayın.

   ![Azure AKS 'de Yayımla menü öğesinde yayımlama ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Aboneliğinizi ve AKS kümenizi, yeni oluşturduğunuz ACR yayımlama profiliyle birlikte seçin. Daha sonra, **Tamam**'a tıklayın.

   ![AKS 'de Yayımla ekranında ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Bu sizi **Azure AKS 'e Yayımla** ekranına götürür.

5. Sunucuya Held grafiklerini yüklemek için kullanılan komut satırını güncelleştirmek için **Held bağlantısını yapılandır** bağlantısını seçin.

   ![Held bağlantısını yapılandır bağlantısının ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Farklı bir Kubernetes bağlamı veya grafik adı gibi, belirtmek istediğiniz özel komut satırı bağımsız değişkenleri varsa komut satırını güncelleştirmek yararlı olur.

   ![Helb yapılandırma ekranının ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Dağıtmaya hazırsanız uygulamanızı AKS 'de yayımlamak için **Yayımla** düğmesine tıklayın.

   ![Azure AKS 'de Yayımla ekranında ekran görüntüsü](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Tebrikler! Artık tüm Kubernetes uygulama geliştirme için Visual Studio 'nun tam gücünden yararlanabilirsiniz.

## <a name="remove-kubernetes-support"></a>Kubernetes desteğini kaldır

1. **Çözüm Gezgini**, **Özellikler**altında *launchSettings.jsüzerinde*açın.

1. **Kubernetes içindeki bölüm kapsayıcısını**silin.

1. Docker Compose 'a geri geçiş yapıyorsanız bu projeyi **Çözüm Gezgini**seçin, sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

1. Seçim Ayrıca, makalenin önceki bölümlerinde bahsedildiği gibi listelenen diğer yapıtları de (örneğin, **grafikler** klasörü ve *AZD. YAML*) silebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Aks belgelerini](/azure/aks)okuyarak Azure 'Da Kubernetes geliştirme hakkında daha fazla bilgi edinin.

[Azure dev Spaces belgelerini](/azure/dev-spaces/) okuyarak Azure dev Spaces hakkında daha fazla bilgi edinin
