---
title: Visual Studio aracılığıyla Kubernetes Köprüsü kullanma
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Geliştirme bilgisayarınızı bir Kubernetes kümesine bağlamak için Visual Studio ile Kubernetes için Bridge 'i nasıl kullanacağınızı öğrenin
keywords: Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, kapsayıcılar için köprü oluşturma
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: 23d060489a13aa8e02316e253d9367e9e3372bbe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859638"
---
# <a name="use-bridge-to-kubernetes"></a>Kubernetes için köprü kullanma

Kubernetes için köprüyü, geliştirme bilgisayarınızda çalışan Kubernetes kümeniz ve kodunuz arasında yeniden yönlendirmek için kullanabilirsiniz. Bu kılavuz Ayrıca, bir Kubernetes kümesinde birden fazla mikro hizmet içeren büyük bir örnek uygulama dağıtmaya yönelik bir betik sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

Bu kılavuz, geliştirme bilgisayarınızı bir Kubernetes kümesine bağlamayı göstermek için [Bisiklet paylaşma örnek uygulamasını][bike-sharing-github] kullanır. Zaten bir Kubernetes kümesinde çalışan bir uygulamanız varsa, aşağıdaki adımları izleyerek kendi hizmetlerinizin adlarını da kullanabilirsiniz.

### <a name="prerequisites"></a>Önkoşullar

* Azure aboneliği. Azure aboneliğiniz yoksa [ücretsiz hesap](https://azure.microsoft.com/free) oluşturabilirsiniz.
* [Yüklü Azure CLI][azure-cli].
* *Azure geliştirme* iş yükü yüklüyken [Visual Studio 2019][visual-studio] sürüm 16,7 Preview 4 veya üzeri Windows 10 üzerinde çalışıyor.
* [Kubernetes uzantısının yüklendiği köprü][btk-extension].

Ayrıca, .NET konsol uygulamaları için *Microsoft. VisualStudio. Azure. Kubernetes. Tools. targets* NuGet paketini yükler.

## <a name="create-a-kubernetes-cluster"></a>Kubernetes kümesi oluşturma

[Desteklenen bir bölgede][supported-regions]aks kümesi oluşturma. Aşağıdaki komutlar *Myresourcegroup* adlı bir kaynak grubu ve *myaks* adlı bir aks kümesi oluşturur.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Örnek uygulamayı yükler

Örnek uygulamayı, belirtilen betiği kullanarak kümenize yükler. [Azure Cloud Shell][azure-cloud-shell]kullanarak bu betiği çalıştırabilirsiniz.

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Yükleme komut dosyasının çıktısında görüntülenecek olan genel URL 'sini açarak kümenizi çalıştıran örnek uygulamaya gidin.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

Yukarıdaki örnekte, genel URL olur `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` .

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Kümenize bağlanın ve bir hizmette hata ayıklayın

Geliştirme bilgisayarınızda, [az aks Get-Credentials][az-aks-get-credentials]komutunu kullanarak Kubernetes ' e bağlanmak Için KUBERNETES CLI indirin ve yapılandırın.

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

GitHub 'daki [bisiklet paylaşımı örnek uygulama][bike-sharing-github] deposundan, bir depoyu yerel olarak kopyalamak ve Visual Studio 'daki klasörü açmak Için yeşil **kod** düğmesindeki açılan menüyü kullanın ve **Visual Studio 'da aç** ' ı seçin. Ardından,   >  *Samples/bıkesharingapp/rezervationengine* klasöründe **app. csproj** projesini açmak için dosya **Aç projesini** kullanın.

Projenizde, aşağıda gösterildiği gibi başlatma ayarları açılır listesinden **Kubernetes 'e bağla** ' yı seçin.

![Kubernetes için köprü seçin](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

*Kubernetes Köprüsü*' nün yanındaki Başlat düğmesine tıklayın. **Kubernetes Köprüsü için profil oluştur** iletişim kutusunda:

* Aboneliğinizi seçin.
* Kümeniz için *Myaks* ' i seçin.
* Ad alanınız için *bikeapp* ' i seçin.
* Hizmetin yeniden yönlendirileceği *rezervationengine* ' i seçin.
* Başlatma profili için *uygulama* ' yı seçin.
* `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`Tarayıcınızı başlatmak için URL 'yi seçin.

![Kubernetes kümesine köprü seçin](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> Yalnızca tek bir pod içeren hizmetleri yeniden yönlendirebilirsiniz.

Yalıtılmış olarak çalıştırmak isteyip istemediğinizi seçin, bu da kümeyi kullanan diğer kişilerin değişiklikleriniz tarafından etkilenmeyeceğini belirtir. Bu yalıtım modu, isteklerinizi etkilenen her hizmetin kopyasına yönlendirerek ve diğer tüm trafiği normal şekilde yönlendirerek gerçekleştirilir. Bu [şekilde, Kubernetes Köprüsü 'Nün nasıl çalıştığı][btk-overview-routing]hakkında daha fazla açıklama bulabilirsiniz.

Kaydet ' e tıklayın **ve hata ayıklamayı başlatın**.

Kubernetes kümesindeki tüm trafik, bu, geliştirme bilgisayarınızda çalışan uygulamanızın sürümüne *rezervationengine* hizmeti için yeniden yönlendirilir. Kubernetes Köprüsü Ayrıca uygulamadaki tüm giden trafiği Kubernetes kümenize geri yönlendirir.

> [!NOTE]
> *Endpointmanager* 'ın yükseltilmiş çalışmasına ve hosts dosyanızı değiştirmesine izin vermeniz istenir.

Geliştirme Bilgisayarınız, durum çubuğu hizmete bağlı olduğunuz zaman görüntülenir `reservationengine` .

![Geliştirme bilgisayarı bağlı](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Sonraki başlangıçlarda, **Kubernetes Için köprü oluştur** iletişim kutusuna sorulmayacaktır. Bu ayarları proje özelliklerindeki **hata ayıklamada** güncelleştirebilirsiniz.

Geliştirme Bilgisayarınız bağlandıktan sonra, değiştirmek istediğiniz hizmet için trafik geliştirme bilgisayarınıza yeniden yönlendirmeye başlar.

## <a name="set-a-break-point"></a>Kesme noktası ayarlama

[BikesHelper.cs][bikeshelper-cs-breakpoint] açın ve imlecinizi buraya yerleştirmek için, 26. satırdaki herhangi bir yere tıklayın. *F9* tuşuna basarak veya **hata ayıklama**  >  **geçiş kesme noktası** seçeneğini belirleyerek bir kesme noktası ayarlayın.

Ortak URL 'YI açarak örnek uygulamaya gidin. Kullanıcı olarak **Aurelia Briggs (müşteri)** öğesini seçin ve ardından kiralamak istediğiniz bir bisiklet seçin. **Kira bisikleti** seçin. Visual Studio 'ya dönün ve 26. satırı gözlemleyin. Ayarladığınız kesme noktası 26. satırdaki hizmeti duraklattı. Hizmeti sürdürmek için **F5** tuşuna basın veya devam **Ayıkla**' ya tıklayın  >  . Tarayıcınıza geri dönün ve bisiklet bir şekilde yeniden kullandığınızı gösteren sayfayı doğrulayın.

İmlecinizi 26. satıra koyarak `BikesHelper.cs` ve **F9** tuşuna basarak kesme noktasını kaldırın.

> [!NOTE]
> Varsayılan olarak, hata ayıklama görevinin durdurulması geliştirme bilgisayarınızı Kubernetes kümenizdeki bağlantısını da keser. Hata ayıklama  `false` seçeneklerinin **Kubernetes hata ayıklama araçları** bölümünde öğesine hata ayıkladıktan sonra bağlantı kesmeyi değiştirerek bu davranışı değiştirebilirsiniz. Bu ayar güncelleştirildikten sonra, hata ayıklamayı durdurup başlattığınızda geliştirme Bilgisayarınız bağlı kalır. Geliştirme bilgisayarınızı sizin kümenize kesmek için, araç çubuğundaki **bağlantıyı kes** düğmesine tıklayın.

## <a name="additional-configuration"></a>Ek yapılandırma

Kubernetes Köprüsü, herhangi bir ek yapılandırma olmadan yönlendirme trafiğini işleyebilir ve ortam değişkenlerini çoğaltebilirler. Kubernetes kümenizdeki kapsayıcıya bağlanmış herhangi bir dosyayı ConfigMap dosyası gibi indirmeniz gerekiyorsa, `KubernetesLocalProcessConfig.yaml` Bu dosyaları geliştirme bilgisayarınıza indirmek için bir oluşturabilirsiniz. Daha fazla bilgi için, [Kubernetes Köprüsü için ile birlikte ek yapılandırma Için KubernetesLocalProcessConfig. YAML kullanma][kubernetesLocalProcessConfig-yaml]konusuna bakın.

## <a name="using-logging-and-diagnostics"></a>Günlüğe kaydetme ve tanılama kullanma

Tanılama günlüklerini, `Bridge to Kubernetes` geliştirme bilgisayarınızın *geçici* dizininde bulunan dizinde bulabilirsiniz. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Örnek uygulamayı kümeinizden kaldırma

Örnek uygulamayı kümeinizden kaldırmak için, belirtilen betiği kullanın.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Sonraki adımlar

Kubernetes ile köprünün nasıl çalıştığını öğrenin.

> [!div class="nextstepaction"]
> [Bridge to Kubernetes’in işleyiş biçimi](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/overview.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation