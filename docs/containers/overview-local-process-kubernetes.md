---
title: Kubernetes ile Yerel İşlem nasıl çalışır?
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Geliştirme bilgisayarınızı Kubernetes kümenize bağlamak için Kubernetes ile yerel Işlem kullanma işlemlerini açıklar
keywords: Kubernetes, Docker, Kubernetes, Azure, kapsayıcılar ile yerel Işlem
monikerRange: '>=vs-2019'
ms.openlocfilehash: adde9d8ecab93bdb6f0aebbd74730ef60bd80cf6
ms.sourcegitcommit: 510a928153470e2f96ef28b808f1d038506cce0c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86454346"
---
# <a name="how-local-process-with-kubernetes-works"></a>Kubernetes ile Yerel İşlem nasıl çalışır?

Kubernetes ile yerel Işlem, geliştirme bilgisayarınızda kod çalıştırmanıza ve hata ayıklamanıza karşın uygulamanızın veya hizmetlerinizin geri kalanı ile Kubernetes kümenize bağlı olmaya devam etmenize olanak tanır. Örneğin, birbirine bağlı çok sayıda hizmet ve veritabanına sahip büyük bir mikro hizmet mimariniz varsa, bu bağımlılıkların geliştirme bilgisayarınızda çoğaltılması zor olabilir. Ayrıca, iç döngü geliştirme sırasında her kod değişikliği için Kubernetes kümenize kod oluşturup dağıtmak, bir hata ayıklayıcıyla yavaş, zaman alabilir ve kullanılması zor olabilir.

Kubernetes ile yerel Işlem, doğrudan geliştirme bilgisayarınız ve kümeniz arasında bir bağlantı oluşturmak için kodunuzu kümenize derleyip dağıtmak zorunda kalmaktan kaçınır. Hata ayıklama sırasında geliştirme bilgisayarınızı kümenize bağlamak, herhangi bir Docker veya Kubernetes yapılandırması oluşturmadan hizmetinizi tam uygulama bağlamında hızlıca test etmenize ve geliştirmenize olanak sağlar.

Kubernetes ile yerel Işlem, bağlı Kubernetes kümeniz ile geliştirme bilgisayarınız arasında trafiği yeniden yönlendirir. Bu trafik yeniden yönlendirmesi, Kubernetes kümenizde çalışan geliştirme ve hizmetinizdeki kodların aynı Kubernetes kümesinde olduklarından farklı iletişim kurmasına olanak tanır. Kubernetes ile yerel Işlem, geliştirme bilgisayarınızda Kubernetes kümenizde bulunan ortam değişkenlerini ve takılı birimleri de çoğaltmak için bir yol sağlar. Geliştirme bilgisayarınızda ortam değişkenlerine ve bağlı birimlere erişim sağlamak, bu bağımlılıkları el ile çoğaltmadan kodunuzda hızla çalışmanıza olanak sağlar.

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

## <a name="diagnostics-and-logging"></a>Tanılama ve günlüğe kaydetme

Kümenize bağlanmak için Kubernetes ile yerel Işlem kullanılırken, kümenizdeki tanılama günlükleri geliştirme bilgisayarınızın [geçici dizinine][azds-tmp-dir]kaydedilir.

## <a name="limitations"></a>Sınırlamalar

Kubernetes ile yerel Işlem aşağıdaki sınırlamalara sahiptir:

* Kubernetes ile yerel Işlem, tek bir hizmet için trafiği geliştirme bilgisayarınıza yönlendirir. Aynı anda birden çok hizmeti yeniden yönlendirmek için Kubernetes ile yerel Işlem kullanamazsınız.
* Bu hizmete bağlanabilmek için bir hizmetin tek bir pod tarafından desteklenen olması gerekir. Çoğaltmaları olan bir hizmet gibi birden fazla pods içeren bir hizmete bağlanamazsınız.
* Pod, başarıyla bağlanmak için Kubernetes ile yerel Işlem için bu Pod 'da çalışan tek bir kapsayıcıya sahip olabilir. Kubernetes ile yerel işlem, hizmet kafesleri tarafından eklenen sepet kapsayıcıları gibi ek kapsayıcıları olan Pod ile hizmetlere bağlanamaz.
* Kubernetes ile yerel Işlemin, ana bilgisayar Dosyanızı düzenlemek için geliştirme bilgisayarınızda çalışması için yükseltilmiş izinlere ihtiyacı vardır.

## <a name="next-steps"></a>Sonraki adımlar

Yerel geliştirme bilgisayarınıza kümenize bağlanmak için Kubernetes ile yerel Işlem kullanmaya başlamak için bkz. [Kubernetes Ile yerel Işlem kullanma](local-process-kubernetes.md).

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro