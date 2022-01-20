---
title: Docker öğreticisi - Sırada ne var?
description: Cloud Native Computing Foundation projelerini kullanarak Docker uygulamalarını düzenlemeyle genişletme seçeneklerini açıklar.
ms.prod: vs-code
ms.topic: tutorial
ms.author: mikemort
author: BigMorty
manager: jmartens
ms.reviewer: nebuk89, ghogen
ms.custom: “docker-team-owned”
ms.date: 08/06/2021
ms.openlocfilehash: 2e1e5fc6df071a6e28d4bae426d7b43a19eda0ba
ms.sourcegitcommit: 2a8c7de72f952203289459736107c875837bb07e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137109990"
---
# <a name="whats-next"></a>Sırada ne var?

Öğreticinizi tamamlasanız da kapsayıcılar hakkında daha fazla bilgi edinmek için çok daha fazlasını bulabilirsiniz!
Burada derinlemesine bakış atacak değil, sonraki adımlara göz atacak birkaç başka alan daha var!

## <a name="container-orchestration"></a>Kapsayıcı düzenleme

Kapsayıcıları üretimde çalıştırma zordur. Bir makinede oturum açmak ve yalnızca veya çalıştırmak `docker run` `docker-compose up` istemiyorsiniz. Neden olmasın? Kapsayıcılar sonlanıyorsa ne olur? Çeşitli makineler arasında nasıl ölçeklendirin? Kapsayıcı düzenlemesi bu sorunu çözer. Kubernetes, Swarm, Tamam ve AKS gibi araçların hepsi bu sorunun çözülmesine yardımcı olur ve hepsi biraz farklı şekillerde olur.

Genel fikir, beklenen durumu alan "yöneticilerin" **olmasıdır.** Bu durum "Web uygulamam için iki örnek çalıştırmak ve 80 bağlantı noktasını göstermek istiyorum" olabilir. Yöneticiler daha sonra kümedeki tüm makinelere bakar ve işi "çalışan" düğümlerine devreder. Yöneticiler değişiklikleri (kapsayıcıyı bırakma gibi) izler ve ardından gerçek durumu beklenen **durumu yansıtmak** için çalışır.

## <a name="cloud-native-computing-foundation-projects"></a>Cloud Native Computing Foundation projeleri

ŞUNDAN BAĞıMSıZ bir evdir: Kubernetes, Prometheus, Envoy, Linkerd, NATS ve daha fazlası dahil olmak üzere çeşitli açık kaynak projeleri için satıcıdan bağımsız bir evdir! Burada, dereceli [ve küküvlenmiş projeleri ve](https://www.cncf.io/projects/) TÜM [ŞURUBF Yatayı'nın tamamını burada görüntüabilirsiniz.](https://landscape.cncf.io/) İzleme, günlüğe kaydetme, güvenlik, görüntü kayıt defterleri, mesajlaşma ve daha fazlası ile ilgili sorunları çözmeye yardımcı olacak çok sayıda proje vardır!

Bu nedenle kapsayıcı ortamını ve buluta özel uygulama geliştirmeyi yeni başladıysanız hoş geldiniz! Lütfen toplulukla bağlantı kurarak soru sorun ve öğrenmeye devam edin! Size sahip olmak için heyecanlanıyoruz!

## <a name="working-with-docker-in-vs-code"></a>VS Code'de Docker ile çalışma

VS Code Docker uzantısını kullanma hakkında daha fazla bilgi edinmek için:

- [VS Code Docker Uzantısına genel bakış](https://code.visualstudio.com/docs/containers/overview)
- [Kullanmaya başlayın ile Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Python kullanmaya başlama](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Kullanmaya başlayın Net Core ile birlikte](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Kapsayıcılı uygulamalarda hata ayıklama](https://code.visualstudio.com/docs/containers/debug-common)
