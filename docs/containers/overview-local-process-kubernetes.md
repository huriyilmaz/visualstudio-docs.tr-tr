---
title: Kubernetes ile Yerel İşlem nasıl çalışır?
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Geliştirme bilgisayarınızı Kubernetes kümenize bağlamak için Kubernetes ile yerel Işlem kullanma işlemlerini açıklar
keywords: Kubernetes, Docker, Kubernetes, Azure, kapsayıcılar ile yerel Işlem
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 5b6c07d5987c52d818a35babd16681652ddf5830
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913269"
---
# <a name="how-local-process-with-kubernetes-works"></a>Kubernetes ile Yerel İşlem nasıl çalışır?

Kubernetes ile yerel Işlem, geliştirme bilgisayarınızda kod çalıştırmanıza ve hata ayıklamanıza karşın uygulamanızın veya hizmetlerinizin geri kalanı ile Kubernetes kümenize bağlı olmaya devam etmenize olanak tanır. Örneğin, birbirine bağlı çok sayıda hizmet ve veritabanına sahip büyük bir mikro hizmet mimariniz varsa, bu bağımlılıkların geliştirme bilgisayarınızda çoğaltılması zor olabilir. Ayrıca, iç döngü geliştirme sırasında her kod değişikliği için Kubernetes kümenize kod oluşturup dağıtmak, bir hata ayıklayıcıyla yavaş, zaman alabilir ve kullanılması zor olabilir.

Kubernetes ile yerel Işlem, doğrudan geliştirme bilgisayarınız ve kümeniz arasında bir bağlantı oluşturmak için kodunuzu kümenize derleyip dağıtmak zorunda kalmaktan kaçınır. Hata ayıklama sırasında geliştirme bilgisayarınızı kümenize bağlamak, herhangi bir Docker veya Kubernetes yapılandırması oluşturmadan hizmetinizi tam uygulama bağlamında hızlıca test etmenize ve geliştirmenize olanak sağlar.

Kubernetes ile yerel Işlem, bağlı Kubernetes kümeniz ile geliştirme bilgisayarınız arasında trafiği yeniden yönlendirir. Bu trafik yeniden yönlendirmesi, Kubernetes kümenizde çalışan geliştirme ve hizmetinizdeki kodların aynı Kubernetes kümesinde olduklarından farklı iletişim kurmasına olanak tanır. Kubernetes ile yerel Işlem, geliştirme bilgisayarınızda Kubernetes kümenizde bulunan ortam değişkenlerini ve takılı birimleri de çoğaltmak için bir yol sağlar. Geliştirme bilgisayarınızda ortam değişkenlerine ve bağlı birimlere erişim sağlamak, bu bağımlılıkları el ile çoğaltmadan kodunuzda hızla çalışmanıza olanak sağlar.

> [!WARNING]
> Kubernetes için yerel Işlem yalnızca geliştirme ve test senaryolarında kullanılmak üzere tasarlanmıştır. Üretim kümeleri veya etkin kullanımda olan canlı hizmetlerle kullanılmak üzere tasarlanmamıştır veya desteklenmez.

## <a name="using-local-process-with-kubernetes"></a>Kubernetes ile yerel Işlem kullanma

Visual Studio 'da Kubernetes ile yerel Işlem kullanmak için, *ASP.net ve Web geliştirme* iş yükü ve [Yerel Işlem Kubernetes uzantısı][lpk-extension] yüklü olan Windows 10 ' da [Visual Studio 2019][visual-studio] sürüm 16,7 Preview 4 veya üzeri bir sürüm gerekir. Kubernetes ile yerel Işlem kullandığınızda, Kubernetes kümenize bir bağlantı kurmak için kümedeki mevcut bir pod 'a giden ve giden tüm trafiği geliştirme bilgisayarınıza yönlendirme seçeneğiniz vardır.

> [!NOTE]
> Kubernetes ile yerel Işlem kullanılırken, geliştirme bilgisayarınıza yönlendirmek için hizmetin adı istenir. Bu seçenek, yeniden yönlendirme için bir pod belirlemek için uygun bir yoldur. Kubernetes kümeniz ile geliştirme bilgisayarınız arasındaki tüm yeniden yönlendirme bir pod içindir.

Kubernetes ile yerel Işlem, kümenize bir bağlantı kurduğunda:

* Hizmeti kümenizdeki yerine, sizin kodunuzda kullanılacak geliştirme bilgisayarınızdaki bağlantı noktasını ve kodunuz için tek seferlik eylem olarak başlatma görevini yapılandırmak isteyip istemediğinizi sorar.
* Küme üzerindeki Pod içindeki kapsayıcıyı, trafiği geliştirme bilgisayarınıza yönlendiren bir uzak Aracı kapsayıcısı ile değiştirir.
* Geliştirme bilgisayarınızdan gelen trafiği kümenizde çalışan uzak aracıya iletmek için [kubectl bağlantı noktasını][kubectl-port-forward] geliştirme bilgisayarınızda ilet olarak çalıştırır.
* Uzak aracıyı kullanarak kümenizdeki ortam bilgilerini toplar. Bu ortam bilgileri ortam değişkenlerini, görünür Hizmetleri, birim takmaları ve gizli takmaları içerir.
* Geliştirme Bilgisayarınızdaki hizmetin, kümede çalışıyor gibi aynı değişkenlere erişebilmesi için Visual Studio 'da ortamı ayarlar.  
* Ana bilgisayar dosyanızı, kümenizdeki hizmetleri geliştirme bilgisayarınızda yerel IP adresleriyle eşlenecek şekilde güncelleştirir. Bu ana bilgisayar dosya girdileri, geliştirme bilgisayarınızda çalışan kodun kümenizde çalışan diğer hizmetlere istek yapmasına izin verir. Ana bilgisayar dosyanızı güncelleştirmek için, Kubernetes ile yerel Işlem, kümenize bağlanırken geliştirme bilgisayarınızda yönetici erişimi ister.
* Geliştirme bilgisayarınızda kodu çalıştırmaya ve hata ayıklamaya başlar. Gerekirse, Kubernetes ile yerel Işlem, bu bağlantı noktalarını kullanmakta olan hizmetleri veya işlemleri durdurarak geliştirme bilgisayarınızda gerekli bağlantı noktalarını boşaltır.

Kümenize bir bağlantı kurduktan sonra, kodu kapsayıcı olmadan yerel olarak bilgisayarınızda çalıştırabilir ve hata ayıklama yapabilir ve kod, kümenizin geri kalanıyla doğrudan etkileşime geçebilir. Uzak aracının aldığı tüm ağ trafiği, bağlantı sırasında belirtilen yerel bağlantı noktasına yönlendirilir, böylece yerel olarak çalışan kodunuz bu trafiği kabul edebilir ve işleyebilir. Kümenizin ortam değişkenleri, birimleri ve gizli dizileri, geliştirme bilgisayarınızda çalışan kod için kullanılabilir hale getirilir. Ayrıca, Kubernetes ile yerel Işlem tarafından geliştirici bilgisayarınıza eklenen ana bilgisayar dosya girişleri ve bağlantı noktası iletimi nedeniyle, kodunuz kümenizdeki hizmet adlarını kullanarak kümenizde çalışan hizmetlere ağ trafiği gönderebilir ve bu trafik kümenizde çalışan hizmetlere iletilir. Geliştirme bilgisayarınız ile kümeniz arasında, bağlandığınız zaman trafik yönlendirilir.

Ayrıca, Kubernetes ile yerel Işlem, geliştirme bilgisayarınızda bulunan küme içindeki kümelerde bulunan ortam değişkenlerini ve bağlı dosyaları dosya aracılığıyla çoğaltmak için bir yol sağlar `KubernetesLocalProcessConfig.yaml` . Bu dosyayı Ayrıca yeni ortam değişkenleri ve birim bağlama oluşturmak için de kullanabilirsiniz.

> [!NOTE]
> Küme bağlantısı süresi (artı 15 dakika) için, Kubernetes ile yerel Işlem, yerel bilgisayarınızda yönetici izinleriyle *Endpointmanager* adlı bir işlem çalıştırır.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>KubernetesLocalProcessConfig. YAML ile ek yapılandırma

`KubernetesLocalProcessConfig.yaml`Dosya, kümedeki yığınlarınızın kullanabildiği ortam değişkenlerini ve bağlı dosyaları çoğaltmanıza olanak sağlar. Ek yapılandırma seçenekleri hakkında daha fazla bilgi için bkz. [Kubernetes Ile yerel Işlemi yapılandırma][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Yalıtımda geliştirmeye yönelik yönlendirme özelliklerini kullanma

Varsayılan olarak, Kubernetes ile yerel Işlem, bir hizmet için tüm trafiği geliştirme bilgisayarınıza yönlendirir. Ayrıca, istekleri yalnızca bir alt etki alanından geliştirme bilgisayarınıza gelen bir hizmete yönlendirmek için yönlendirme özelliklerini kullanma seçeneğiniz de vardır. Bu yönlendirme özellikleri, yalıtımında geliştirme yapmak ve kümenizdeki diğer trafiği kesintiye uğramaktan kaçınmak için Kubernetes ile yerel Işlem kullanmanıza imkan sağlar.

Aşağıdaki animasyon, yalıtımda aynı kümede çalışan iki geliştirici göstermektedir:

![Animasyonlu GIF, yalıtımı gösteren](media/local-process-kubernetes/lpk-graphic-isolated.gif)

Yalıtımda çalışmayı etkinleştirdiğinizde, Kubernetes ile yerel Işlem, Kubernetes kümenize bağlanılmasına ek olarak aşağıdakileri yapar:

* Kubernetes kümesinin Azure Dev Spaces etkin olmadığını doğrular.
* Seçtiğiniz hizmetinizi aynı ad alanındaki kümede çoğaltır ve bir *Routing.VisualStudio.io/Route-from=SERVICE_NAME* etiketi ve *Routing.VisualStudio.io/Route-on-Header=Kubernetes-Route-as: GENERATED_NAME* ek açıklaması ekler.
* , Kubernetes kümesindeki aynı ad alanında bulunan yönlendirme yöneticisini yapılandırır ve başlatır. Yönlendirme Yöneticisi, ad alanınız içinde yönlendirmeyi yapılandırırken *Routing.VisualStudio.io/Route-from=SERVICE_NAME* label ve  *Routing.VisualStudio.io/Route-on-Header=Kubernetes-Route-as: GENERATED_NAME* ek açıklamalarını aramak için bir etiket seçici kullanır.

Kubernetes ile yerel Işlem, Kubernetes kümenizde Azure Dev Spaces etkinleştirildiğini algılarsa, Kubernetes ile yerel Işlem kullanabilmeniz için önce Azure Dev Spaces devre dışı bırakmanız istenir.

Yönlendirme Yöneticisi başlatıldığında şunları yapar:
* Ad alanında bulunan tüm gelen verileri alt etki alanı için *GENERATED_NAME* kullanarak çoğaltır. 
* *GENERATED_NAME* alt etki alanı ile yinelenen giriş ile ilişkili her hizmet için bir haberci Pod oluşturur.
* Yalıtım aşamasında çalıştığınız hizmet için ek bir haberci Pod oluşturur. Bu, alt etki alanı olan isteklerin geliştirme bilgisayarınıza yönlendirilmesine izin verir.
* Her haberci pod için yönlendirme kurallarını, alt etki alanı ile hizmetlerin yönlendirilmesini işleyecek şekilde yapılandırır.

Kümede *GENERATED_NAME* alt etki alanı ile bir istek alındığında, öğesine bir *Kubernetes-Route-as = GENERATED_NAME* üst bilgisi eklenir. Haberci Pod, kümede uygun hizmete istek yapan yönlendirmeyi işler. İstek yalıtımda üzerinde çalışılan hizmete yönlendiriliyorsa, bu istek uzak aracı tarafından geliştirme bilgisayarınıza yönlendirilir.

Kümede *GENERATED_NAME* alt etki alanı olmayan bir istek alındığında, isteğe hiçbir üst bilgi eklenmez. Haberci Pod, kümede uygun hizmete istek yapan yönlendirmeyi işler. İstek değiştirilmekte olan hizmete yönlendiriliyorsa, bu istek bunun yerine uzak aracı yerine özgün hizmete yönlendirilir.

> [!IMPORTANT]
> Kümenizdeki her hizmet ek istekler yaparken *Kubernetes-Route-as = GENERATED_NAME* üst bilgisini iletmelidir. Örneğin, *Servicea* bir istek aldığında, yanıt döndürmeden önce *serviceb* 'ye bir istek yapar. Bu örnekte, *Servicea* 'nın isteğinde *Kubernetes-Route-as = GENERATED_NAME* üst bilgisini iletmesi *gerekir.* [ASP.net][asp-net-header]gibi bazı dillerin, üst bilgi yaymayı işleme yöntemlerine sahip olabilir.

Kümenizin bağlantısını kestiğinizde, varsayılan olarak, Kubernetes ile yerel işlem tüm haberci Pod ve yinelenen hizmeti kaldırır. 

> NOTUN Yönlendirme Yöneticisi dağıtımı ve hizmeti, ad alanınız içinde çalışmaya devam edecektir. Dağıtımı ve hizmeti kaldırmak için, ad alanınız için aşağıdaki komutları çalıştırın.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Tanılama ve günlüğe kaydetme

Kümenize bağlanmak için Kubernetes ile yerel Işlem kullanılırken, kümenizdeki tanılama günlükleri, *Kubernetes klasörüyle yerel işlemdeki* geliştirme bilgisayarınızın *geçici* dizinine kaydedilir.

## <a name="limitations"></a>Sınırlamalar

Kubernetes ile yerel Işlem aşağıdaki sınırlamalara sahiptir:

* Kubernetes ile yerel Işlem, tek bir hizmet için trafiği geliştirme bilgisayarınıza yönlendirir. Aynı anda birden çok hizmeti yeniden yönlendirmek için Kubernetes ile yerel Işlem kullanamazsınız.
* Bu hizmete bağlanabilmek için bir hizmetin tek bir pod tarafından desteklenen olması gerekir. Çoğaltmaları olan bir hizmet gibi birden fazla pods içeren bir hizmete bağlanamazsınız.
* Pod, başarıyla bağlanmak için Kubernetes ile yerel Işlem için bu Pod 'da çalışan tek bir kapsayıcıya sahip olabilir. Kubernetes ile yerel işlem, hizmet kafesleri tarafından eklenen sepet kapsayıcıları gibi ek kapsayıcıları olan Pod ile hizmetlere bağlanamaz.
* Kubernetes ile yerel Işlemin, ana bilgisayar Dosyanızı düzenlemek için geliştirme bilgisayarınızda çalışması için yükseltilmiş izinlere ihtiyacı vardır.
* Kubernetes ile yerel Işlem Azure Dev Spaces etkinleştirilmiş kümeler üzerinde kullanılamaz.

### <a name="local-process-with-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Azure Dev Spaces etkinleştirilmiş Kubernetes ve kümeler ile yerel Işlem

Azure Dev Spaces etkinleştirilmiş bir kümede Kubernetes ile yerel Işlem kullanamazsınız. Azure Dev Spaces etkinleştirilmiş bir kümede Kubernetes ile yerel Işlem kullanmak istiyorsanız, kümenize bağlanmadan önce Azure Dev Spaces devre dışı bırakmanız gerekir.

## <a name="next-steps"></a>Sonraki adımlar

Yerel geliştirme bilgisayarınıza kümenize bağlanmak için Kubernetes ile yerel Işlem kullanmaya başlamak için bkz. [Kubernetes Ile yerel Işlem kullanma](local-process-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-local-process-with-kubernetes.md