---
title: Bridge to Kubernetes’in işleyiş biçimi
ms.technology: vs-azure
ms.date: 11/19/2020
ms.topic: conceptual
description: Geliştirme bilgisayarınızı Kubernetes kümenize bağlamak için Bridge to Kubernetes kullanma işlemlerini açıklar
keywords: Bridge to Kubernetes, Docker, Kubernetes, Azure, kapsayıcılar
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 838589e0dd81232de25b88989d621a07fb22f972
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043061"
---
# <a name="how-bridge-to-kubernetes-works"></a>Bridge to Kubernetes’in işleyiş biçimi

Bridge to Kubernetes, uygulama veya hizmetlerinizin geri kalanıyla Kubernetes kümenize bağlıyken geliştirme bilgisayarınızda kod çalıştırmanıza ve kodda hata ayıklamanıza olanak sağlar. Örneğin, birbirine bağımlı birçok hizmet ve veritabanına sahip büyük bir mikro hizmet mimariniz varsa, bu bağımlılıkları geliştirme bilgisayarınızda çoğaltmak zor olabilir. Ayrıca, iç döngü geliştirme sırasında her kod değişikliği için Kubernetes kümenize kod oluşturma ve dağıtma yavaş olabilir, zaman alabilir ve hata ayıklayıcıyla birlikte kullanmak zor olabilir.

Bridge to Kubernetes, doğrudan geliştirme bilgisayarınızla kümeniz arasında bağlantı oluşturarak kodunuzu derlemek ve kümenize dağıtmak zorunda kalmamaktır. Hata ayıklama sırasında geliştirme bilgisayarınızı kümenize bağlamak, Herhangi bir Docker veya Kubernetes yapılandırması oluşturmadan hizmetinizi tam uygulama bağlamında hızlı bir şekilde test edin ve geliştirin.

Bridge to Kubernetes, bağlı Kubernetes kümeniz ile geliştirme bilgisayarınız arasındaki trafiği yeniden yönlendirmektedir. Bu trafik yeniden yönlendirmesi, Geliştirme bilgisayarınızda ve Kubernetes kümeniz üzerinde çalışan hizmetlerin aynı Kubernetes kümesinde olduğu gibi iletişim kurmasına olanak sağlar. Bridge to Kubernetes, geliştirme bilgisayarınızda Kubernetes kümenizin podlar tarafından kullanılabilen ortam değişkenlerini ve bağlı birimleri çoğaltmak için bir yol da sağlar. Geliştirme bilgisayarınızda ortam değişkenlerine ve bağlı birimlere erişim sağlamak, bu bağımlılıkları el ile çoğaltmanıza gerek kalmadan kodunuzu hızla çalışmanıza olanak sağlar.

> [!WARNING]
> Bridge to Kubernetes geliştirme ve test senaryolarında kullanılmak üzere tasarlanmıştır. Üretim kümeleriyle veya etkin kullanımda canlı hizmetlerle kullanım için amaçlanmaz veya desteklenmemektedir.

Şu anda desteklenen özellikler ve gelecekteki bir yol haritası hakkında Bridge to Kubernetes yol haritası [Bridge to Kubernetes bulunabilir.](https://github.com/microsoft/mindaro/projects/1)

## <a name="using-bridge-to-kubernetes"></a>Bridge to Kubernetes kullanma

Visual Studio'da Bridge to Kubernetes'yi kullanmak için, Windows 10 ve web geliştirme iş yükünün yüklü olduğu ve Bridge to Kubernetes Uzantısı'nın yüklü olduğu Windows 10 üzerinde çalışan *ASP.NET Visual Studio* [2019][visual-studio] sürüm 16.7 Preview 4 veya [daha yenisi][btk-extension] gerekir. Kubernetes Bridge to Kubernetes bağlantı kurmak için Bridge to Kubernetes'i kullanırsanız, kümede var olan bir poddan geliştirme bilgisayarınıza tüm trafiği yeniden yönlendirme seçeneğiniz vardır.

> [!NOTE]
> Bu Bridge to Kubernetes, geliştirme bilgisayarınıza yeniden yönlendirmek için hizmetin adını girmeniz istenir. Bu seçenek, yeniden yönlendirme için bir pod tanımlamanın kullanışlı bir yolu olur. Kubernetes kümeniz ve geliştirme bilgisayarınız arasındaki tüm yeniden yönlendirme bir pod için kullanılır.

Bu Bridge to Kubernetes kümenize bir bağlantı kurduğunda:

* Hizmeti, kümeniz üzerinde, geliştirme bilgisayarınızda kodunuz için kullanmak üzere bağlantı noktasını ve tek kullanımlık bir eylem olarak kodunuz için başlatma görevini değiştirmek üzere yapılandırmanızı sağlar.
* Kümede pod'daki kapsayıcıyı, trafiği geliştirme bilgisayarınıza yönlendiren bir uzak aracı kapsayıcısı ile değiştirir.
* Geliştirme bilgisayarınızdan kümenizi çalıştıran uzak aracıya trafiği iletmesi için geliştirme bilgisayarınızda [kubectl port-forward][kubectl-port-forward] çalıştırır.
* Uzak aracıyı kullanarak kümenizin ortam bilgilerini toplar. Bu ortam bilgileri ortam değişkenlerini, görünür hizmetleri, birim bağlamalarını ve gizli bağlamaları içerir.
* Geliştirme bilgisayarınızda Visual Studio kümede çalışıyor gibi aynı değişkenlere erişmesi için ortamı yerel ortamda ayarlar.
* Kümeniz üzerinde hizmetleri geliştirme bilgisayarınızda yerel IP adreslerine eşlemek için konak dosyanızı günceller. Bu konaklar dosya girişleri, geliştirme bilgisayarınızda çalışan kodun kümeniz içinde çalışan diğer hizmetlere istekte bulunarak bunları oluşturmasına olanak sağlar. Konaklar dosyanızı güncelleştirmek Bridge to Kubernetes kümenize bağlanırken geliştirme bilgisayarınızda yönetici erişimi istemeniz gerekir.
* Geliştirme bilgisayarınızda kodunuzu çalıştırmaya ve hata ayıklamaya başlar. Gerekirse, Bridge to Kubernetes o anda bu bağlantı noktalarını kullanan hizmetleri veya işlemleri durdurarak gerekli bağlantı noktalarını geliştirme bilgisayarınızda serbest bırakabilirsiniz.

Kümenize bağlantı kurulduktan sonra, kapsayıcıya almadan kodu yerel olarak bilgisayarınızda çalıştırabilir ve hata ayıklarsınız ve kod kümenizin geri kalanıyla doğrudan etkileşime olabilir. Uzak aracı tarafından alınan tüm ağ trafiği bağlantı sırasında belirtilen yerel bağlantı noktasına yeniden yönlendiriliyor. Bu nedenle yerel olarak çalışan kodunuz bu trafiği kabul eder ve işler. Kümenizin ortam değişkenleri, birimleri ve gizli dizileri, geliştirme bilgisayarınızda çalışan kodlar için kullanılabilir. Ayrıca, Bridge to Kubernetes tarafından geliştirici bilgisayarınıza eklenen konak dosya girişleri ve bağlantı noktası iletme nedeniyle, kodunuz kümenizin hizmet adlarını kullanarak kümeniz üzerinde çalışan hizmetlere ağ trafiği gönderebilir ve bu trafik kümeniz içinde çalışan hizmetlere iletebilirsiniz. Trafik, bağlantınız boyunca geliştirme bilgisayarınızla kümeniz arasında yönlendirildi.

Ayrıca, Bridge to Kubernetes ortamı değişkenlerini çoğaltmak için bir yol ve geliştirme bilgisayarınızda kümenizin podlar tarafından kullanılabilen bağlı dosyaları dosya aracılığıyla `KubernetesLocalProcessConfig.yaml` sağlar. Bu dosyayı yeni ortam değişkenleri ve birim bağlamaları oluşturmak için de kullanabilirsiniz.

> [!NOTE]
> Kümeye bağlantı süresi boyunca (ek olarak 15 dakika Bridge to Kubernetes *endpointManager* adlı bir işlemi yerel bilgisayarınızda yönetici izinleriyle çalıştırır.

> [!NOTE]
> Birden çok hizmetle paralel olarak hata ayıkabilirsiniz, ancak hata ayıklamak istediğiniz hizmetler olarak Visual Studio sayıda örnek başlatmalısiniz. Hizmetlerinizin farklı bağlantı noktalarında yerel olarak dinley olduğundan emin olun ve ardından bunları ayrı olarak yapılandırarak hata ayıklar. Bu senaryoda yalıtım desteklenmiyor.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>KubernetesLocalProcessConfig.yaml ile ek yapılandırma

Dosya, `KubernetesLocalProcessConfig.yaml` kümenizin podları tarafından kullanılabilen ortam değişkenlerini ve bağlı dosyaları çoğaltmanıza olanak sağlar. Visual Studio geliştirme Bridge to Kubernetes kubernetesLocalConfig.yaml dosyasının, yeniden yönlendirilen hizmetin proje dosyasıyla aynı dizinde olması gerekir. Ek yapılandırma seçenekleri hakkında daha fazla bilgi için bkz. [Yapılandırma Bridge to Kubernetes.][using-config-yaml]

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Yalıtımlı geliştirme için yönlendirme özelliklerini kullanma

Varsayılan olarak Bridge to Kubernetes, bir hizmetin tüm trafiğini geliştirme bilgisayarınıza yeniden yönlendirmektedir. Ayrıca, istekleri yalnızca bir alt etki alanından kaynaklanan bir hizmete geliştirme bilgisayarınıza yönlendirmek için yönlendirme özelliklerini kullanabilirsiniz. Bu yönlendirme özellikleri, yalıtarak geliştirmek Bridge to Kubernetes kümenizin diğer trafiğini kesintiye neden olmaktan kaçınmak için Bridge to Kubernetes'i kullanmanızı sağlar.

Aşağıdaki animasyon aynı küme üzerinde yalıtarak çalışan iki geliştiriciyi gösterir:

![Yalıtımın yer alan animasyonlu GIF'i](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

Yalıtarak çalışmayı etkinleştir Bridge to Kubernetes Kubernetes kümenize bağlanmaya ek olarak şunları da yapar:

* Kubernetes kümesinde etkin bir Azure Dev Spaces doğrular.
* Seçtiğiniz hizmeti aynı ad alanına kümede çoğaltır ve bir *routing.visualstudio.io/route-from=SERVICE_NAME* etiketi ve *routing.visualstudio.io/route-on-header=kubernetes-route-as ekler: GENERATED_NAME* ek açıklaması.
* Yönlendirme yöneticisini yapılandırarak Kubernetes kümesinde aynı ad alanına başlatır. Yönlendirme yöneticisi, ad alanınıza *yönlendirmeyi yapılandırarak routing.visualstudio.io/route-from=SERVICE_NAME* etiketi ve  *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME* ek açıklamasına bakmak için bir etiket seçici kullanır.

Kubernetes Bridge to Kubernetes kümeniz üzerinde Azure Dev Spaces'ın etkin olduğunu algılarsa, Azure Dev Spaces'yi kullanamadan önce devre dışı bırakmanız Bridge to Kubernetes.

Yönlendirme yöneticisi başlatıldığında şunları yapar:

* Ad alanı içinde bulunan tüm girişleri (yük dengeleyici girişleri dahil) alt *etki alanının GENERATED_NAME* yineler.
* Alt etki alanıyla yinelenen girişlerle ilişkili her hizmet için bir *GENERATED_NAME* oluşturur.
* Yalıtımlı olarak üzerinde çalıştığın hizmet için ek bir faturalama podu oluşturur. Bu, alt etki alanı olan isteklerin geliştirme bilgisayarınıza yönlendirilene izin verir.
* Alt etki alanı olan hizmetler için yönlendirmeyi işlemek üzere her bir faturalama podu için yönlendirme kurallarını yapılandıran.

Aşağıdaki diyagramda, kümenize bağlanamadan önce Bridge to Kubernetes Kubernetes kümesi gösterildi:

![Küme olmadan küme Bridge to Kubernetes](media/bridge-to-kubernetes/kubr-cluster.svg)

Aşağıdaki diyagramda, yalıtım modunda etkinleştirilmiş Bridge to Kubernetes kümeyi gösterir. Burada, yinelenen hizmeti ve yönlendirmeyi yalıtılmış olarak destekleyen faturalama podlarını görebilir.

![Kümenin etkin olduğu Bridge to Kubernetes diyagramı](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

*Kümede* GENERATED_NAME alt etki alanı olan bir istek geldiğinde, i isteğine *bir kubernetes-route-as=GENERATED_NAME* üst bilgisi eklenir. Envoy podları, isteği kümede uygun hizmete yönlendirmeyi ele almaktadır. İstek, yalıtımlı olarak üzerinde çalışan hizmete yönlendirilmesi, uzak aracı tarafından geliştirme bilgisayarınıza yeniden yönlendirilmesidir.

Kümede bir *GENERATED_NAME* alt etki alanı alınarak istekte üst bilgi eklenmez. Envoy podları, isteği kümede uygun hizmete yönlendirmeyi ele almaktadır. İstek, değiştirilen hizmete yönlendirilen istek yerine uzak aracı yerine özgün hizmete yönlendirildi.

> [!IMPORTANT]
> Kümeniz üzerinde yer alan her hizmetin ek istekler yaparken *kubernetes-route-as=GENERATED_NAME* üst bilgilerini iletmesi gerekir. Örneğin, *serviceA bir* istek aldığında, yanıt dönmeden önce *serviceB'ye* bir istek yapar. Bu *örnekte, serviceA'nın* isteğinde *kubernetes-route-as=GENERATED_NAME* üst bilgisini *serviceB'ye iletmesi gerekir.* ASP.NET gibi bazı [dillerde][asp-net-header]üst bilgi yayma işleme yöntemleri olabilir.

Kümenizin bağlantısını keserek varsayılan olarak Bridge to Kubernetes tüm faturalama podlarını ve yinelenen hizmeti kaldırır.

> [!NOTE]
> Yönlendirme yöneticisi dağıtımı ve hizmeti ad alanınız içinde çalışıyor olarak kalır. Dağıtımı ve hizmeti kaldırmak için ad alanınız için aşağıdaki komutları çalıştırın.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Tanılama ve günlüğe kaydetme

Kümenize Bridge to Kubernetes için kümenizi kullanırken, kümenizin tanılama günlükleri Bridge to Kubernetes klasöründe geliştirme bilgisayarınızın *TEMP* *dizinine* kaydedilir.

## <a name="rbac-authorization"></a>RBAC yetkilendirmesi

Kubernetes, kullanıcılar ve gruplara Access Control yönetmek için Rol tabanlı güvenlik (RBAC) sağlar. Bilgi için [bkz. Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) belgeleri YaML dosyası oluşturarak ve bunu kümeye uygulamak için kullanarak RBAC özellikli bir kümenin `kubectl` izinlerini ayarlayın. 

Kümede izinleri ayarlamak için, ve erişim ihtiyacı olan konular (kullanıcılar ve gruplar) için kendi ad alanını kullanarak *permissions.yml* gibi bir YAML dosyası oluşturun `<namespace>` veya bu dosyayı değiştirebilirsiniz.

```yml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: bridgetokubernetes-<namespace>
  namespace: development
subjects:
  - kind: User
    name: jane.w6wn8.k8s.ginger.eu-central-1.aws.gigantic.io
    apiGroup: rbac.authorization.k8s.io
  - kind: Group
    name: dev-admin
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: admin
  apiGroup: rbac.authorization.k8s.io
```

komutunu kullanarak izinleri uygulama:

```cmd
kubectl -n <namespace> apply -f <yaml file name>
```

## <a name="limitations"></a>Sınırlamalar

Bridge to Kubernetes aşağıdaki sınırlamalara sahiptir:

* Bir pod, başarıyla bağlanması için bu podda yalnızca Bridge to Kubernetes kapsayıcıya sahip olabilir.
* Şu anda Bridge to Kubernetes Linux kapsayıcıları olması gerekir. Windows kapsayıcıları desteklenmez.
* Bridge to Kubernetes ana bilgisayar dosyanızı düzenlemek için geliştirme bilgisayarınızda çalıştırmak için yükseltilmiş izinlere ihtiyaç vardır.
* Bridge to Kubernetes, kümeler etkinken Azure Dev Spaces kullanılamaz.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Bridge to Kubernetes etkin kümeler Azure Dev Spaces kümeler

Kümenin etkin olduğu Bridge to Kubernetes kümede kümeyi Azure Dev Spaces. kümenizin etkin olduğu bir Bridge to Kubernetes kullanmak Azure Dev Spaces, kümenize bağlanmadan önce Azure Dev Spaces devre dışı bırakmanız gerekir.

## <a name="next-steps"></a>Sonraki adımlar

Yerel geliştirme bilgisayarınıza Bridge to Kubernetes için kümenizi kullanmaya başlamanız için bkz. [Bridge to Kubernetes.](bridge-to-kubernetes.md)

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md
