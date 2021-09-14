---
title: Docker öğreticisi - Sırada ne var
description: Cloud Native Computing Foundation projelerini kullanarak Docker uygulamalarını düzenleme ile genişletme seçeneklerini açıklar.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6ba31a6d250123d4d54fa1071e9ef662aea7dae8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633417"
---
# <a name="whats-next"></a>Sırada ne var?

Öğreticinizi tamamlasanız da kapsayıcılar hakkında daha fazla bilgi edinmek için çok daha fazlasını bulabilirsiniz!
Burada derine inersiniz, ancak bir sonraki adıma göz atacak birkaç alan daha vardır!

## <a name="container-orchestration"></a>Kapsayıcı düzenleme

Kapsayıcıları üretimde çalıştırma zordur. Bir makinede oturum açmak ve yalnızca veya çalıştırmak `docker run` `docker-compose up` istemiyorsiniz. Neden olmasın? Kapsayıcılar sonlanıyorsa ne olur? Çeşitli makineler arasında nasıl ölçeklendirin? Kapsayıcı düzenlemesi bu sorunu çözer. Kubernetes, Swarm, Yer ve AKS gibi araçların hepsi bu sorunun çözülmesine yardımcı olur ve hepsi biraz farklı şekillerde olur.

Genel fikir, beklenen durumu alan "yöneticilerin" **olmasıdır.** Bu durum "Web uygulamam için iki örnek çalıştırmak ve 80 bağlantı noktasını göstermek istiyorum" olabilir. Yöneticiler daha sonra kümedeki tüm makinelere bakar ve işi "çalışan" düğümlerine devreder. Yöneticiler değişiklikleri (kapsayıcıyı bırakma gibi) izler ve ardından gerçek durumu beklenen **durumu yansıtmak** için çalışır.

## <a name="cloud-native-computing-foundation-projects"></a>Cloud Native Computing Foundation projeleri

ŞUNDAN BAĞıMSıZ bir evdir: Kubernetes, Prometheus, Envoy, Linkerd, NATS ve daha fazlası dahil olmak üzere çeşitli açık kaynak projeleri için satıcıdan bağımsız bir evdir! Burada, dereceli [ve küküvlenmiş projeleri ve](https://www.cncf.io/projects/) TÜM [ŞURUBF Yatayı'nın tamamını burada görüntüabilirsiniz.](https://landscape.cncf.io/) İzleme, günlüğe kaydetme, güvenlik, görüntü kayıt defterleri, mesajlaşma ve daha fazlası ile ilgili sorunları çözmeye yardımcı olacak çok sayıda proje vardır!

Bu nedenle kapsayıcı ortamını ve buluta özel uygulama geliştirmeyi yeni başladıysanız hoş geldiniz! Lütfen toplulukla bağlantı kurarak soru sorun ve öğrenmeye devam edin! Size sahip olmak için heyecanlanıyoruz!

## <a name="working-with-docker-in-vs-code"></a>VS Code'de Docker ile çalışma

VS Code Docker uzantısını kullanma hakkında daha fazla bilgi edinmek için:

- [VS Code Docker Uzantısına genel bakış](https://code.visualstudio.com/docs/containers/overview)
- [Kullanmaya başlayın ile Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Python kullanmaya başlama](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Kullanmaya başlayın NET Core ile birlikte](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Kapsayıcılı uygulamalarda hata ayıklama](https://code.visualstudio.com/docs/containers/debug-common)
