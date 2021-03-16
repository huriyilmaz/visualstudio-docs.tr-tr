---
title: Bridge to Kubernetes’in işleyiş biçimi
ms.technology: vs-azure
ms.date: 11/19/2020
ms.topic: conceptual
description: Geliştirme bilgisayarınızı Kubernetes kümenize bağlamak için Kubernetes 'e köprü kullanma işlemlerini açıklar
keywords: Kubernetes, Docker, Kubernetes, Azure, kapsayıcılar için köprü oluşturma
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 49c3081e68baf4f2bf1d0975bcdae7ea25ab90b3
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571551"
---
# <a name="how-bridge-to-kubernetes-works"></a>Bridge to Kubernetes’in işleyiş biçimi

Kubernetes Köprüsü, uygulamanızın veya hizmetlerinizin geri kalanı ile Kubernetes kümenize bağlı olmaya devam ederken geliştirme bilgisayarınızda kodu çalıştırmanızı ve hata ayıklamanıza olanak tanır. Örneğin, birbirine bağlı çok sayıda hizmet ve veritabanına sahip büyük bir mikro hizmet mimariniz varsa, bu bağımlılıkların geliştirme bilgisayarınızda çoğaltılması zor olabilir. Ayrıca, iç döngü geliştirme sırasında her kod değişikliği için Kubernetes kümenize kod oluşturup dağıtmak, bir hata ayıklayıcıyla yavaş, zaman alabilir ve kullanılması zor olabilir.

Kubernetes Köprüsü, doğrudan geliştirme bilgisayarınız ve kümeniz arasında bir bağlantı oluşturmak yerine kodunuzu kümenize derleyip dağıtmak zorunda kalmaktan kaçınır. Hata ayıklama sırasında geliştirme bilgisayarınızı kümenize bağlamak, herhangi bir Docker veya Kubernetes yapılandırması oluşturmadan hizmetinizi tam uygulama bağlamında hızlıca test etmenize ve geliştirmenize olanak sağlar.

Kubernetes Köprüsü, bağlı Kubernetes kümeniz ile geliştirme bilgisayarınız arasında trafiği yeniden yönlendirir. Bu trafik yeniden yönlendirmesi, Kubernetes kümenizde çalışan geliştirme ve hizmetinizdeki kodların aynı Kubernetes kümesinde olduklarından farklı iletişim kurmasına olanak tanır. Kubernetes Köprüsü, geliştirme bilgisayarınızda Kubernetes kümenizde bulunan ortam değişkenlerini ve takılı birimleri de çoğaltmak için bir yol sağlar. Geliştirme bilgisayarınızda ortam değişkenlerine ve bağlı birimlere erişim sağlamak, bu bağımlılıkları el ile çoğaltmadan kodunuzda hızla çalışmanıza olanak sağlar.

> [!WARNING]
> Kubernetes Köprüsü yalnızca geliştirme ve test senaryolarında kullanılmak üzere tasarlanmıştır. Üretim kümeleri veya etkin kullanımda olan canlı hizmetlerle kullanılmak üzere tasarlanmamıştır veya desteklenmez.

## <a name="using-bridge-to-kubernetes"></a>Kubernetes için köprü kullanma

Visual Studio 'da Kubernetes için köprü kullanmak üzere, *ASP.net ve Web geliştirme* iş yükü yüklü ve [Kubernetes uzantısı][btk-extension] 'nın yüklü olduğu Windows 10 ' da [Visual Studio 2019][visual-studio] sürüm 16,7 Preview 4 veya daha yenisi olması gerekir. Kubernetes için köprü kullandığınızda Kubernetes kümenize bir bağlantı kurmak için kümedeki var olan Pod 'a giden ve giden tüm trafiği geliştirme bilgisayarınıza yönlendirme seçeneğiniz vardır.

> [!NOTE]
> Kubernetes için köprü kullanırken, geliştirme bilgisayarınıza yönlendirmek üzere hizmetin adı istenir. Bu seçenek, yeniden yönlendirme için bir pod belirlemek için uygun bir yoldur. Kubernetes kümeniz ile geliştirme bilgisayarınız arasındaki tüm yeniden yönlendirme bir pod içindir.

Kubernetes Köprüsü, kümenize bir bağlantı kurduğunda:

* Hizmeti kümenizdeki yerine, sizin kodunuzda kullanılacak geliştirme bilgisayarınızdaki bağlantı noktasını ve kodunuz için tek seferlik eylem olarak başlatma görevini yapılandırmak isteyip istemediğinizi sorar.
* Küme üzerindeki Pod içindeki kapsayıcıyı, trafiği geliştirme bilgisayarınıza yönlendiren bir uzak Aracı kapsayıcısı ile değiştirir.
* Geliştirme bilgisayarınızdan gelen trafiği kümenizde çalışan uzak aracıya iletmek için [kubectl bağlantı noktasını][kubectl-port-forward] geliştirme bilgisayarınızda ilet olarak çalıştırır.
* Uzak aracıyı kullanarak kümenizdeki ortam bilgilerini toplar. Bu ortam bilgileri ortam değişkenlerini, görünür Hizmetleri, birim takmaları ve gizli takmaları içerir.
* Geliştirme Bilgisayarınızdaki hizmetin, kümede çalışıyor gibi aynı değişkenlere erişebilmesi için Visual Studio 'da ortamı ayarlar.
* Ana bilgisayar dosyanızı, kümenizdeki hizmetleri geliştirme bilgisayarınızda yerel IP adresleriyle eşlenecek şekilde güncelleştirir. Bu ana bilgisayar dosya girdileri, geliştirme bilgisayarınızda çalışan kodun kümenizde çalışan diğer hizmetlere istek yapmasına izin verir. Ana bilgisayar dosyanızı güncelleştirmek için, Kubernetes 'e olan köprü, kümenize bağlanırken geliştirme bilgisayarınızda yönetici erişimi ister.
* Geliştirme bilgisayarınızda kodu çalıştırmaya ve hata ayıklamaya başlar. Gerekirse, Kubernetes 'e olan köprü, şu anda bu bağlantı noktalarını kullanan Hizmetleri veya süreçlerini durdurarak geliştirme bilgisayarınızda gerekli bağlantı noktalarını serbest bırakılır.

Kümenize bir bağlantı kurduktan sonra, kodu kapsayıcı olmadan yerel olarak bilgisayarınızda çalıştırabilir ve hata ayıklama yapabilir ve kod, kümenizin geri kalanıyla doğrudan etkileşime geçebilir. Uzak aracının aldığı tüm ağ trafiği, bağlantı sırasında belirtilen yerel bağlantı noktasına yönlendirilir, böylece yerel olarak çalışan kodunuz bu trafiği kabul edebilir ve işleyebilir. Kümenizin ortam değişkenleri, birimleri ve gizli dizileri, geliştirme bilgisayarınızda çalışan kod için kullanılabilir hale getirilir. Ayrıca, Kubernetes 'e Köprüleyerek geliştirici bilgisayarınıza eklenen ana bilgisayar dosya girişleri ve bağlantı noktası iletimi nedeniyle, kodunuz kümenizdeki hizmet adlarını kullanarak kümenizde çalışan hizmetlere ağ trafiği gönderebilir ve bu trafik kümenizde çalışan hizmetlere iletilir. Geliştirme bilgisayarınız ile kümeniz arasında, bağlandığınız zaman trafik yönlendirilir.

Ayrıca, Kubernetes Köprüsü, dosya aracılığıyla geliştirme bilgisayarınızda bulunan küme içindeki kümelerde bulunan ortam değişkenlerini ve bağlı dosyaları çoğaltmak için bir yol sağlar `KubernetesLocalProcessConfig.yaml` . Bu dosyayı Ayrıca yeni ortam değişkenleri ve birim bağlama oluşturmak için de kullanabilirsiniz.

> [!NOTE]
> Küme bağlantısı süresi (artı 15 dakika) için, Kubernetes Köprüsü, yerel bilgisayarınızda yönetici izinleriyle *Endpointmanager* adlı bir işlem çalıştırır.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>KubernetesLocalProcessConfig. YAML ile ek yapılandırma

`KubernetesLocalProcessConfig.yaml`Dosya, kümedeki yığınlarınızın kullanabildiği ortam değişkenlerini ve bağlı dosyaları çoğaltmanıza olanak sağlar. Ek yapılandırma seçenekleri hakkında daha fazla bilgi için bkz. [Kubernetes Için köprü yapılandırma][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Yalıtımda geliştirmeye yönelik yönlendirme özelliklerini kullanma

Varsayılan olarak, Kubernetes Köprüsü, bir hizmet için tüm trafiği geliştirme bilgisayarınıza yönlendirir. Ayrıca, istekleri yalnızca bir alt etki alanından geliştirme bilgisayarınıza gelen bir hizmete yönlendirmek için yönlendirme özelliklerini kullanma seçeneğiniz de vardır. Bu yönlendirme özellikleri, yalıtımın geliştirilmesi için Kubernetes Köprüsü kullanmanızı ve kümenizdeki diğer trafiği kesintiye uğramaktan kaçınmanızı sağlar.

Aşağıdaki animasyon, yalıtımda aynı kümede çalışan iki geliştirici göstermektedir:

![Animasyonlu GIF, yalıtımı gösteren](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

Yalıtımda çalışmayı etkinleştirdiğinizde Kubernetes Köprüsü, Kubernetes kümenize bağlanılmasına ek olarak aşağıdakileri yapar:

* Kubernetes kümesinin Azure Dev Spaces etkin olmadığını doğrular.
* Seçtiğiniz hizmetinizi aynı ad alanındaki kümede çoğaltır ve bir *Routing.VisualStudio.io/Route-from=SERVICE_NAME* etiketi ve *Routing.VisualStudio.io/Route-on-Header=Kubernetes-Route-as: GENERATED_NAME* ek açıklaması ekler.
* , Kubernetes kümesindeki aynı ad alanında bulunan yönlendirme yöneticisini yapılandırır ve başlatır. Yönlendirme Yöneticisi, ad alanınız içinde yönlendirmeyi yapılandırırken *Routing.VisualStudio.io/Route-from=SERVICE_NAME* label ve  *Routing.VisualStudio.io/Route-on-Header=Kubernetes-Route-as: GENERATED_NAME* ek açıklamalarını aramak için bir etiket seçici kullanır.

Kubernetes Köprüsü, Kubernetes kümenizde Azure Dev Spaces etkinleştirildiğini algılarsa, Kubernetes için köprü kullanabilmeniz için Azure Dev Spaces önce devre dışı bırakmanız istenir.

Yönlendirme Yöneticisi başlatıldığında şunları yapar:

* Alt etki alanı için *GENERATED_NAME* kullanarak ad alanında bulunan tüm gelen parolaları (yük dengeleyici dahil) çoğaltır.
* *GENERATED_NAME* alt etki alanı ile yinelenen giriş ile ilişkili her hizmet için bir haberci Pod oluşturur.
* Yalıtım aşamasında çalıştığınız hizmet için ek bir haberci Pod oluşturur. Bu, alt etki alanı olan isteklerin geliştirme bilgisayarınıza yönlendirilmesine izin verir.
* Her haberci pod için yönlendirme kurallarını, alt etki alanı ile hizmetlerin yönlendirilmesini işleyecek şekilde yapılandırır.

Aşağıdaki diyagramda, Kubernetes Köprüsü kümenize bağlanmadan önce bir Kubernetes kümesi gösterilmektedir:

![Kubernetes Köprüsü olmadan küme diyagramı](media/bridge-to-kubernetes/kubr-cluster.svg)

Aşağıdaki diyagramda, Kubernetes ile aynı küme, yalıtım modunda etkin olarak gösterilmiştir. Burada, yinelenen hizmeti ve yönlendirmeyi destekleyen yinelenen hizmeti ve sorguları yalıtımlara bakabilirsiniz.

![Kubernetes ile Köprü özellikli küme diyagramı](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

Kümede *GENERATED_NAME* alt etki alanı ile bir istek alındığında, isteğe bir *Kubernetes-Route-as = GENERATED_NAME* üst bilgisi eklenir. Haberci Pod, kümede uygun hizmete istek yapan yönlendirmeyi işler. İstek yalıtımda üzerinde çalışılan hizmete yönlendiriliyorsa, bu istek uzak aracı tarafından geliştirme bilgisayarınıza yönlendirilir.

Kümede *GENERATED_NAME* alt etki alanı olmayan bir istek alındığında, isteğe hiçbir üst bilgi eklenmez. Haberci Pod, kümede uygun hizmete istek yapan yönlendirmeyi işler. İstek değiştirilmekte olan hizmete yönlendiriliyorsa, bu istek bunun yerine uzak aracı yerine özgün hizmete yönlendirilir.

> [!IMPORTANT]
> Kümenizdeki her hizmet ek istekler yaparken *Kubernetes-Route-as = GENERATED_NAME* üst bilgisini iletmelidir. Örneğin, *Servicea* bir istek aldığında, yanıt döndürmeden önce *serviceb* 'ye bir istek yapar. Bu örnekte, *Servicea* 'nın isteğinde *Kubernetes-Route-as = GENERATED_NAME* üst bilgisini iletmesi *gerekir.* [ASP.net][asp-net-header]gibi bazı dillerin, üst bilgi yaymayı işleme yöntemlerine sahip olabilir.

Kümenizin bağlantısını kestiğinizde, Kubernetes 'e olan köprü, tüm haberci Pod ve yinelenen hizmeti kaldırır.

> [!NOTE]
> Yönlendirme Yöneticisi dağıtımı ve hizmeti, ad alanınız içinde çalışmaya devam edecektir. Dağıtımı ve hizmeti kaldırmak için, ad alanınız için aşağıdaki komutları çalıştırın.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Tanılama ve günlüğe kaydetme

Kümenize bağlanmak için Kubernetes Köprüsü kullanılırken, kümenizdeki tanılama günlükleri, *Kubernetes klasörüne olan köprüdeki* geliştirme bilgisayarınızın *geçici* dizinine kaydedilir.

## <a name="rbac-authorization"></a>RBAC yetkilendirmesi

Kubernetes, kullanıcılar ve gruplar için izinleri yönetmek üzere rol tabanlı Access Control (RBAC) sağlar. Daha fazla bilgi için bkz. [Kubernetes belgeleri](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) , BIR YAML dosyası oluşturarak ve `kubectl` bunu kümeye uygulamak için kullanarak RBAC özellikli bir küme için izinleri ayarlamanıza olanak sağlar. 

Küme izinlerini ayarlamak için, kendi ad alanınızı ve erişmesi gereken konuları (kullanıcılar ve gruplar) kullanarak aşağıdaki gibi *Permissions. yıml* gıbı bır YAML dosyası oluşturun veya değiştirin `<namespace>` .

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

Şu komutu kullanarak izinleri uygulayın:

```cmd
kubectl -n <namespace> apply -f <yaml file name>
```

## <a name="limitations"></a>Sınırlamalar

Kubernetes Köprüsü aşağıdaki sınırlamalara sahiptir:

* Pod, başarıyla bağlanmak için Kubernetes 'e Köprüsü için bu Pod 'da çalışan tek bir kapsayıcıya sahip olabilir.
* Şu anda, Kubernetes Pod Köprüsü 'nün Linux kapsayıcıları olması gerekir. Windows kapsayıcıları desteklenmez.
* Kubernetes köprüsünün, ana bilgisayar Dosyanızı düzenlemek için geliştirme bilgisayarınızda çalışması için yükseltilmiş izinlere sahip olması gerekir.
* Kubernetes Köprüsü Azure Dev Spaces etkinleştirilmiş kümeler üzerinde kullanılamaz.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Azure Dev Spaces etkinleştirilmiş Kubernetes ve kümeler için köprü oluşturma

Azure Dev Spaces etkinleştirilmiş bir kümede Kubernetes için köprü kullanamazsınız. Azure Dev Spaces etkinleştirilmiş bir kümede Kubernetes için köprü kullanmak istiyorsanız, kümenize bağlanmadan önce Azure Dev Spaces devre dışı bırakmanız gerekir.

## <a name="next-steps"></a>Sonraki adımlar

Yerel geliştirme bilgisayarınıza kümenize bağlanmak için Kubernetes Köprüsü kullanmaya başlamak için bkz. [Kubernetes Için köprü kullanma](bridge-to-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md
