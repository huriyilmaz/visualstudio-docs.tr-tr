---
title: Docker öğreticisi-sonraki
description: Bulut Yerel Bilgi Işlem altyapısı projelerini kullanarak, düzenleme ile Docker uygulamalarını genişletme seçeneklerini açıklar.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6e1e8d23628c746c892a20e1769a7c157a425fc6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045443"
---
# <a name="whats-next"></a>Sırada ne var?

Öğreticinizi bitirseniz de kapsayıcılar hakkında daha fazla bilgi edinmek için çok daha fazla şey vardır!
Buraya göz atacağız, ancak daha sonra bakabilmeniz için birkaç diğer alan aşağıda verilmiştir!

## <a name="container-orchestration"></a>Kapsayıcı düzenleme

Üretimde çalışan kapsayıcılar zor. Bir makinede oturum açmak istemezsiniz ve yalnızca bir `docker run` veya çalıştırın `docker-compose up` . Neden olmasın? Kapsayıcılar ne olursa olsun? Birçok makine genelinde nasıl ölçeklendirebilirsiniz? Kapsayıcı düzenlemesi Bu sorunu çözer. Kubernetes, Sısınma, Nomad ve AKS gibi araçlar, bu sorunu çözmek için biraz farklı yollarla yardımcı olur.

Genel fikir, **beklenen durumu** alan "yöneticileriniz" olacaktır. Bu durum "Web uygulamamın iki örneğini çalıştırmak istiyorum ve 80 numaralı bağlantı noktasını kullanıma sunmalıyım" olabilir. Yöneticiler daha sonra kümedeki makinelere bakar ve "çalışan" düğümlerine iş temsilcisini devredebilir. Yöneticiler değişiklikleri (örneğin, bir kapsayıcı çıkma) ve **gerçek durumu** beklenen durumu yansıtacak şekilde çalışır.

## <a name="cloud-native-computing-foundation-projects"></a>Bulut Yerel Bilgi Işlem altyapısı projeleri

CNCF, Kubernetes, Prometheus, Envoy, Linkerd, NAT 'ler ve daha fazlası dahil olmak üzere çeşitli açık kaynaklı projeler için satıcı tarafsız bir giriş. [Şu şekilde dereceli ve yer lanan projeleri](https://www.cncf.io/projects/) ve tüm [cncf 'leri burada](https://landscape.cncf.io/)görüntüleyebilirsiniz. İzleme, günlüğe kaydetme, güvenlik, görüntü kayıt defterleri, mesajlaşma ve daha birçok konuda sorunları çözmeye yardımcı olacak çok sayıda proje vardır!

Bu nedenle, yatay ve buluta yerel uygulama geliştirmeye yönelik yeni bir sürümüne sahip değilseniz hoş geldiniz! Lütfen topluluğa bağlanın, soru sorun ve öğrenimi koruyun! Size heyecanlanıyoruz!

## <a name="working-with-docker-in-vs-code"></a>VS Code Docker ile çalışma

VS Code docker uzantısını kullanma hakkında daha fazla bilgi edinin:

- [VS Code Docker uzantısına genel bakış](https://code.visualstudio.com/docs/containers/overview)
- [Node.jskullanmaya başlayın ](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Python kullanmaya başlama](https://code.visualstudio.com/docs/containers/quickstart-python)
- [.NET Core ile çalışmaya başlama](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Kapsayıcılı uygulamalarda hata ayıklama](https://code.visualstudio.com/docs/containers/debug-common)
