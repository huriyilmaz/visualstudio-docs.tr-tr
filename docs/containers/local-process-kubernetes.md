---
title: Visual Studio ile Kubernetes ile yerel Işlem kullanma (Önizleme)
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Geliştirme bilgisayarınızı bir Kubernetes kümesine bağlamak için Visual Studio ile Kubernetes ile yerel Işlem kullanmayı öğrenin
keywords: Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, kapsayıcılar ile yerel Işlem
monikerRange: '>=vs-2019'
ms.openlocfilehash: fd2e456f1ffdaaea90c0594b73d5367e51c8f655
ms.sourcegitcommit: debf31a8fb044f0429409bd0587cdb7d5ca6f836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87134002"
---
# <a name="use-local-process-with-kubernetes-preview"></a>Kubernetes ile yerel Işlem kullanma (Önizleme)

Kubernetes ile yerel Işlem, geliştirme bilgisayarınızda kod çalıştırmanıza ve hata ayıklamanıza karşın uygulamanızın veya hizmetlerinizin geri kalanı ile Kubernetes kümenize bağlı olmaya devam etmenize olanak tanır. Örneğin, birbirine bağlı çok sayıda hizmet ve veritabanına sahip büyük bir mikro hizmet mimariniz varsa, bu bağımlılıkların geliştirme bilgisayarınızda çoğaltılması zor olabilir. Ayrıca, iç döngü geliştirme sırasında her kod değişikliği için Kubernetes kümenize kod oluşturup dağıtmak, bir hata ayıklayıcıyla yavaş, zaman alabilir ve kullanılması zor olabilir.

Kubernetes ile yerel Işlem, doğrudan geliştirme bilgisayarınız ve kümeniz arasında bir bağlantı oluşturmak için kodunuzu kümenize derleyip dağıtmak zorunda kalmaktan kaçınır. Hata ayıklama sırasında geliştirme bilgisayarınızı kümenize bağlamak, herhangi bir Docker veya Kubernetes yapılandırması oluşturmadan hizmetinizi tam uygulama bağlamında hızlıca test etmenize ve geliştirmenize olanak sağlar.

Kubernetes ile yerel Işlem, bağlı Kubernetes kümeniz ile geliştirme bilgisayarınız arasında trafiği yeniden yönlendirir. Bu trafik yeniden yönlendirmesi, Kubernetes kümenizde çalışan geliştirme ve hizmetinizdeki kodların aynı Kubernetes kümesinde olduklarından farklı iletişim kurmasına olanak tanır. Kubernetes ile yerel Işlem, geliştirme bilgisayarınızda Kubernetes kümenizde bulunan ortam değişkenlerini ve takılı birimleri de çoğaltmak için bir yol sağlar. Geliştirme bilgisayarınızda ortam değişkenlerine ve bağlı birimlere erişim sağlamak, bu bağımlılıkları el ile çoğaltmadan kodunuzda hızla çalışmanıza olanak sağlar.

Bu kılavuzda, Kubernetes ile yerel Işlem kullanarak, geliştirme bilgisayarınızda çalışan Kubernetes kümeniz ve kodunuz arasında trafiği yeniden yönlendirme hakkında bilgi edineceksiniz. Bu kılavuz Ayrıca, bir Kubernetes kümesinde birden fazla mikro hizmet içeren büyük bir örnek uygulama dağıtmaya yönelik bir betik sağlar.

> [!IMPORTANT]
> Bu özellik şu anda önizleme sürümündedir. Önizlemeler, [ek kullanım koşullarını][preview-terms] kabul etmeniz şartıyla kullanımınıza sunulur. Bu özelliğin bazı yönleri genel kullanıma açılmadan önce değişebilir.

## <a name="before-you-begin"></a>Başlamadan önce

Bu kılavuz, geliştirme bilgisayarınızı bir Kubernetes kümesine bağlamayı göstermek için [Bisiklet paylaşma örnek uygulamasını][bike-sharing-github] kullanır. Zaten bir Kubernetes kümesinde çalışan bir uygulamanız varsa, aşağıdaki adımları izleyerek kendi hizmetlerinizin adlarını da kullanabilirsiniz.

### <a name="prerequisites"></a>Önkoşullar

* Azure aboneliği. Azure aboneliğiniz yoksa [ücretsiz hesap](https://azure.microsoft.com/free) oluşturabilirsiniz.
* [Yüklü Azure CLI][azure-cli].
* *Azure geliştirme* iş yükü yüklüyken [Visual Studio 2019][visual-studio] sürüm 16,7 Preview 4 veya üzeri Windows 10 üzerinde çalışıyor.
* [Kubernetes uzantısı Için yerel işlem yüklendi][lpk-extension].

Ayrıca, .NET konsol uygulamaları için *Microsoft. VisualStudio. Azure. Kubernetes. Tools. targets* NuGet paketini yükler.

## <a name="create-a-kubernetes-cluster"></a>Kubernetes kümesi oluşturma

[Desteklenen bir bölgede][supported-regions]aks kümesi oluşturma. Aşağıdaki komutlar *Myresourcegroup* adlı bir kaynak grubu ve *myaks*adlı bir aks kümesi oluşturur.

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
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

Yükleme komut dosyasının çıktısında görüntülenecek olan genel URL 'sini açarak kümenizi çalıştıran örnek uygulamaya gidin.

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
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

Visual Studio 'da [Bisiklet paylaşma örnek uygulamasından][bike-sharing-github] *mindaro/Samples/Bıkesharingapp/rezervationengine/App. csproj* öğesini açın.

Projenizde, aşağıda gösterildiği gibi başlatma ayarları açılır listesinden *Kubernetes Ile yerel işlem* ' i seçin.

![Kubernetes ile yerel Işlem seçin](media/local-process-kubernetes/choose-local-process.png)

*Kubernetes Ile yerel işlem*' in yanındaki Başlat düğmesine tıklayın. *Kubernetes iletişim kutusuyla yerel işlemde* :

* Aboneliğinizi seçin.
* Kümeniz için *Myaks* ' i seçin.
* Ad alanınız için *geliştirme* ' yı seçin.
* Hizmetin yeniden yönlendirileceği *rezervationengine* ' i seçin.
* Başlatma profili için *uygulama* ' yı seçin.
* `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`Tarayıcınızı başlatmak için URL 'yi seçin.

![Kubernetes kümesi ile yerel Işlem seçin](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> Yalnızca tek bir pod içeren hizmetleri yeniden yönlendirebilirsiniz.

Kaydet ' e tıklayın *ve hata ayıklamayı başlatın*.

Kubernetes kümesindeki tüm trafik, bu, geliştirme bilgisayarınızda çalışan uygulamanızın sürümüne *rezervationengine* hizmeti için yeniden yönlendirilir. Kubernetes ile yerel Işlem, uygulamanın tüm giden trafiğini Kubernetes kümenize geri yönlendirir.

> [!NOTE]
> *Kubernetesdnsmanager* 'ın yükseltilmiş çalışmasına ve hosts dosyanızı değiştirmesine izin vermeniz istenir.

Geliştirme Bilgisayarınız, durum çubuğu, *rezervationengine* hizmetine bağlı olduğunu gösterdiğinde bağlanır.

![Geliştirme bilgisayarı bağlı](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> Subesquent başlatıldığında, *Kubernetes iletişim kutusuyla yerel işlem* istenmez. Bu ayarları proje özelliklerindeki *hata ayıklama* bölmesinde güncelleştirebilirsiniz.

Geliştirme Bilgisayarınız bağlandıktan sonra, değiştirmek istediğiniz hizmet için trafik geliştirme bilgisayarınıza yeniden yönlendirmeye başlar.

## <a name="set-a-break-point"></a>Kesme noktası ayarlama

[BikesHelper.cs][bikeshelper-cs-breakpoint] açın ve imlecinizi buraya yerleştirmek için, 26. satırdaki herhangi bir yere tıklayın. *F9* tuşuna basarak bir kesme noktası ayarlayın veya *Hata Ayıkla* 'Yı tıklattıktan sonra *kesme noktasını değiştirin*.

Ortak URL 'YI açarak örnek uygulamaya gidin. Kullanıcı olarak *Aurelia Briggs (müşteri)* öğesini seçin ve ardından kiralamak istediğiniz bir bisiklet seçin. *Kiralık bisiklet*' e tıklayın. Visual Studio 'ya dönün ve 26. satırı gözlemleyin. Ayarladığınız kesme noktası 26. satırdaki hizmeti duraklattı. Hizmeti sürdürmek için *F5* 'e basın veya *Hata Ayıkla* 'Ya tıkladıktan sonra *devam edin*. Tarayıcınıza geri dönün ve bisiklet bir şekilde yeniden kullandığınızı gösteren sayfayı doğrulayın.

İmlecinizi 26. satıra koyarak `BikesHelper.cs` ve *F9*tuşuna basarak kesme noktasını kaldırın.

> [!NOTE]
> Varsayılan olarak, hata ayıklama görevinin durdurulması geliştirme bilgisayarınızı Kubernetes kümenizdeki bağlantısını da keser. Hata ayıklama seçeneklerinin *Kubernetes hata ayıklama araçları* bölümünde *false* olarak *hata ayıkladıktan sonra bağlantıyı kesmeyi* değiştirerek bu davranışı değiştirebilirsiniz. Bu ayar güncelleştirildikten sonra, hata ayıklamayı durdurup başlattığınızda geliştirme Bilgisayarınız bağlı kalır. Geliştirme bilgisayarınızı sizin kümenize kesmek için, araç çubuğundaki *bağlantıyı kes* düğmesine tıklayın.
>
> Visual Studio, kümeyle olan bağlantıyı aniden sonlandırıyorsa veya sonlandırıyorsa, Kubernetes ile yerel Işleme bağlanmadan önce yeniden yönlendiriyorsunuz hizmeti özgün durumuna geri yüklenemez. Bu sorunu gidermek için [sorun giderme kılavuzu][troubleshooting]'na bakın.

## <a name="using-logging-and-diagnostics"></a>Günlüğe kaydetme ve tanılama kullanma

Tanılama günlüklerini, `Azure Dev Spaces` [geliştirme bilgisayarınızın *geçici* dizininde][azds-tmp-dir]bulunan dizinde bulabilirsiniz.

## <a name="remove-the-sample-application-from-your-cluster"></a>Örnek uygulamayı kümeinizden kaldırma

Örnek uygulamayı kümeinizden kaldırmak için, belirtilen betiği kullanın.

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Sonraki adımlar

Yerel Işlemin Kubernetes 'in nasıl çalıştığını öğrenin.

> [!div class="nextstepaction"]
> [Kubernetes ile Yerel İşlem nasıl çalışır?](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro