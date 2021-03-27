---
title: Visual Studio aracılığıyla Kubernetes Köprüsü kullanma
titleSuffix: ''
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: quickstart
description: Geliştirme bilgisayarınızı bir Kubernetes kümesine bağlamak için Visual Studio ile Kubernetes için Bridge 'i nasıl kullanacağınızı öğrenin
keywords: Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, kapsayıcılar için köprü oluşturma
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: fdcf31d062fe2be72709979f0892e6a7f535024a
ms.sourcegitcommit: 2049ec99f1439ec91d002853226934b067b1ee70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105635046"
---
# <a name="use-bridge-to-kubernetes"></a>Kubernetes için köprü kullanma

Kubernetes için köprüyü, geliştirme bilgisayarınızda çalışan Kubernetes kümeniz ve kodunuz arasında yeniden yönlendirmek için kullanabilirsiniz. Bu kılavuz Ayrıca, bir Kubernetes kümesinde birden fazla mikro hizmet içeren büyük bir örnek uygulama dağıtmaya yönelik bir betik sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

Bu kılavuz, geliştirme bilgisayarınızı bir Kubernetes kümesine bağlamayı göstermek için [ToDo uygulaması örnek uygulamasını][todo-app-github] kullanır. Zaten bir Kubernetes kümesinde çalışan bir uygulamanız varsa, aşağıdaki adımları izleyerek kendi hizmetlerinizin adlarını da kullanabilirsiniz.

Bu örnek, Kubernetes 'in herhangi bir Kubernetes kümesinde basit bir YAPıLACAKLAR uygulamasının mikro hizmet sürümünü geliştirmek için nasıl kullanılabileceğini gösterir. Bu örnek, Visual Studio 'yu kullanarak [Todomvc](http://todomvc.com)tarafından sunulan koddan uyarlanmıştır. Bu adımlar herhangi bir Kubernetes kümesiyle birlikte çalışmalıdır.

TODO uygulaması örneği, kalıcı depolama sağlayan bir ön uç ve arka uçta oluşur. Bu genişletilmiş örnek, bir istatistik bileşeni ekler ve uygulamayı özellikle bir dizi mikro hizmete ayırır:

- Ön uç, kalıcı hale getirmek ve YAPıLACAKLAR öğelerini güncelleştirmek için Database-API ' i çağırır;
- Veritabanı-API hizmeti, TODO öğelerini kalıcı hale getirmek için bir Mongo veritabanını kullanır;
- Ön uç, bir Kbbitmq kuyruğuna olay ekleme, tamamlanma ve silme olaylarını yazar;
- Bir istatistik çalışanı, Kbbitmq kuyruğundan olayları alır ve Redsıs önbelleğini güncelleştirir;
- Bir istatistik API 'SI, ön uçta görüntülenecek önbelleğe alınmış istatistikleri kullanıma sunar.

Tüm bu genişletilmiş TODO uygulaması, ilişkili altı bileşenden oluşur.

### <a name="prerequisites"></a>Önkoşullar

- bir Kubernetes kümesi
- [Visual Studio 2019][visual-studio] sürüm 16,7 Preview 4 veya üzeri Windows 10 üzerinde çalışıyor.
- [Kubernetes uzantısının yüklendiği köprü][btk-extension].

## <a name="check-the-cluster"></a>Kümeyi denetleyin

Bir komut istemi açın ve kubectl 'nin yüklü olduğundan ve yolun üzerine, kullanmak istediğiniz kümenin kullanılabildiğini ve hazır olduğunu ve bağlamını bu kümeye ayarlamayı denetleyin.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

Burada {Context-Name}, Todo-App örneği için kullanmak istediğiniz küme bağlamının adıdır.

## <a name="deploy-the-application"></a>Uygulamayı dağıtma

[Mindaro](https://github.com/Microsoft/mindaro) deposunu kopyalayın ve geçerli çalışma klasörüyle *örnekler/Todo-App* ile bir komut penceresi açın.

Örnek için bir ad alanı oluşturun.

```cmd
kubectl create namespace todo-app
```

Ardından, dağıtım bildirimini Uygula:

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Bu, türü bir hizmet kullanarak ön ucu kullanıma sunan basit bir dağıtımdır `LoadBalancer` . Tüm yığınların çalıştırılmasını ve hizmetin dış IP 'si için `frontend` kullanılabilir olmasını bekleyin.

MiniKube ile test ediyorsanız, `minikube tunnel` bir dış IP 'yi çözümlemek için kullanmanız gerekir. AKS veya başka bir bulut tabanlı Kubernetes sağlayıcısı kullanıyorsanız, otomatik olarak bir dış IP atanır. `frontend`Hizmeti çalışır duruma gelene kadar beklemek üzere izlemek için aşağıdaki komutu kullanın:

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Dış IP ve yerel bağlantı noktasını (bağlantı noktası (ler) sütunundaki ilk sayı) kullanarak uygulamaya gidin.

```
http://{external-ip}:{local-port}
```

Çalışan uygulamayı tarayıcıda test edin. Todo öğelerini eklerken, tamamladıktan ve sildikten sonra, istatistik sayfasının beklenen ölçümler ile güncelleştirdiğine dikkat edin.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Kümenize bağlanın ve bir hizmette hata ayıklayın

Visual Studio 'da *samples\todo-app\database-api\database-api.csproj* açın. Projede, aşağıda gösterildiği gibi başlatma ayarları açılır listesinden **Kubernetes 'e bağla** ' yı seçin.

![Kubernetes için köprü seçin](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

*Kubernetes Köprüsü*' nün yanındaki Başlat düğmesine tıklayın. **Kubernetes Köprüsü için profil oluştur** iletişim kutusunda:

- Kümenizin adını seçin.
- Ad alanınız için *Todo-App* ' i seçin.
- Yeniden yönlendirileceği hizmetin *veritabanı-API 'sini* seçin.
- Daha önce tarayıcınızı başlatmak için kullandığınız URL 'yi seçin, http://{external-IP}: {local-port}

![Kubernetes kümesine köprü seçin](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Yalıtılmış olarak çalıştırmak isteyip istemediğinizi seçin, bu da kümeyi kullanan diğer kişilerin değişiklikleriniz tarafından etkilenmeyeceğini belirtir. Bu yalıtım modu, isteklerinizi etkilenen her hizmetin kopyasına yönlendirerek ve diğer tüm trafiği normal şekilde yönlendirerek gerçekleştirilir. Bu [şekilde, Kubernetes Köprüsü 'Nün nasıl çalıştığı][btk-overview-routing]hakkında daha fazla açıklama bulabilirsiniz.

**Tamam**'a tıklayın. Kubernetes kümesindeki tüm trafik, *veritabanı-API* hizmeti için geliştirme bilgisayarınızda çalışan uygulamanızın sürümüne yeniden yönlendirilir. Kubernetes Köprüsü Ayrıca uygulamadaki tüm giden trafiği Kubernetes kümenize geri yönlendirir.

> [!NOTE]
> *Endpointmanager* 'ın yükseltilmiş çalışmasına ve hosts dosyanızı değiştirmesine izin vermeniz istenir.

Geliştirme Bilgisayarınız, durum çubuğu hizmete bağlı olduğunuz zaman görüntülenir `database-api` .

![Geliştirme bilgisayarı bağlı](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Sonraki başlangıçlarda, **Kubernetes Için köprü oluştur** iletişim kutusuna sorulmayacaktır. Bu ayarları proje özelliklerindeki **hata ayıklamada** güncelleştirebilirsiniz.

Geliştirme Bilgisayarınız bağlandıktan sonra, değiştirmek istediğiniz hizmet için trafik geliştirme bilgisayarınıza yeniden yönlendirmeye başlar.

> [!NOTE]
> Hata ayıklama profilini daha sonra düzenlemek için örneğin, farklı bir Kubernetes hizmeti ile test etmek istiyorsanız, hata ayıklama özelliklerini **Hata Ayıkla**' yı seçin  >  ve **Değiştir** düğmesine tıklayın.

## <a name="set-a-break-point"></a>Kesme noktası ayarlama

MongoHelper. cs dosyasını açın ve imlecinizi buraya yerleştirmek için CreateTask yönteminde satır 68 ' de bir yere tıklayın. *F9* tuşuna basarak veya **hata ayıklama**  >  **geçiş kesme noktası** seçeneğini belirleyerek bir kesme noktası ayarlayın.

Ortak URL 'YI (ön uç hizmeti için dış IP adresi) açarak örnek uygulamaya gidin. Hizmeti sürdürmek için **F5** tuşuna basın veya devam **Ayıkla**' ya tıklayın  >  .

Kesme noktası ile imlecinizi çizgiye yerleştirerek kesme noktasını kaldırın ve **F9** tuşuna basın.

> [!NOTE]
> Varsayılan olarak, hata ayıklama görevinin durdurulması geliştirme bilgisayarınızı Kubernetes kümenizdeki bağlantısını da keser.  `false` **Araç** seçenekleri iletişim kutusunun **Kubernetes hata ayıklama araçları** bölümünde öğesine hata ayıkladıktan sonra bağlantı kesmeyi değiştirerek bu davranışı değiştirebilirsiniz  >   . Bu ayar güncelleştirildikten sonra, hata ayıklamayı durdurup başlattığınızda geliştirme Bilgisayarınız bağlı kalır. Geliştirme bilgisayarınızı sizin kümenize kesmek için, araç çubuğundaki **bağlantıyı kes** düğmesine tıklayın.
>
>![Kubernetes hata ayıklama seçeneklerinin ekran görüntüsü](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Ek yapılandırma

Kubernetes Köprüsü, herhangi bir ek yapılandırma olmadan yönlendirme trafiğini işleyebilir ve ortam değişkenlerini çoğaltebilirler. Kubernetes kümenizdeki kapsayıcıya bağlanmış herhangi bir dosyayı ConfigMap dosyası gibi indirmeniz gerekiyorsa, `KubernetesLocalProcessConfig.yaml` Bu dosyaları geliştirme bilgisayarınıza indirmek için bir oluşturabilirsiniz. Daha fazla bilgi için, [Kubernetes Köprüsü için ile birlikte ek yapılandırma Için KubernetesLocalProcessConfig. YAML kullanma][kubernetesLocalProcessConfig-yaml]konusuna bakın.

## <a name="using-logging-and-diagnostics"></a>Günlüğe kaydetme ve tanılama kullanma

Tanılama günlüklerini, `Bridge to Kubernetes` geliştirme bilgisayarınızın *geçici* dizininde bulunan dizinde bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Kubernetes ile köprünün nasıl çalıştığını öğrenin.

> [!div class="nextstepaction"]
> [Bridge to Kubernetes’in işleyiş biçimi](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation