---
title: 'Docker öğreticisi - Bölüm 10: Buluta dağıtma'
description: Barındırma için bir docker uygulamasını bulut hizmetine dağıtın.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: faa4fe632662a9e57ab6e39573a42ad4e3da4c97
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633494"
---
# <a name="deploy-to-the-cloud"></a>Buluta dağıtma

Artık uygulamayı yerel olarak çalıştırdınıza göre, diğer kişilerin bu uygulamaya erişmesi ve bunu kullanabiliyor olması için uygulamayı bulutta çalıştırmayı düşünebilirsiniz. Bunu yapmak için Docker bağlamlarını kullan kullanırsiniz. Bağlam, şu anda kapsayıcılarla çalıştığınız yerdir. Şu anda yalnızca "varsayılan" bağlamınız olduğu için bir bulut bağlamı eklemeniz ve uygulamanızı buna dağıtmanız gerekir.

## <a name="create-your-cloud-context"></a>Bulut bağlamınızı oluşturma

1. Başlamak için Docker panelinin contexts bölümüne bakarak hangi bağlamlara sahip olduğunu bulabilirsiniz:

   ![Yalnızca varsayılan bağlamı gösterir](media/defaultcontext.png)

Yalnızca yerel çalışma için varsayılan bağlamınızı görüyor gerekir.

1. Buluta dağıtmak için yeni bir ACI bağlamı oluşturmanız gerekir, ancak bunu yapmak için önce Azure hesabı uzantısının Azure kimlik doğrulamasına sahip olması gerekir.

   ![Azure uzantısı ekleme](media/addazureextension.png)

Henüz azure hesabınız yoksa bir Azure hesabı ayarlayabilirsiniz.

1. Artık yeni ACI bağlamınızı oluşturabilirsiniz. Bunu Yapmak için Docker görünümünün **Bağlamlar bölümündeki** artı düğmesine tıklayabilirsiniz.

   ![ACI bağlamınızı oluşturma](media/createnewcontext.png)

Bu, bu kapsayıcıları hangi kaynak grubu altında çalıştırmak istediğinize sorar. Ok tuşlarını kullanarak mevcut bir grubu seçin veya yeni grubu kullanmak için varsayılan seçeneği kullanın.

![Kaynak grubularınızı seçme](media/selectresourcegroup.png)

Artık ACI bağlamınızı listelenmiş olarak görebilir ve geçerli odağınız/kullanım bağlamınız yapmak için buna sağ tıklarsanız:

![Yeni ACI bağlamı seçilebilir](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Bulutta kapsayıcıları çalıştırma

1. Şimdi ACI bağlamınızı kullanın ve kapsayıcıyı çalıştırın.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Bunu çalıştırarak, şimdi bağlamınız içinde kapsayıcıya bakın.

   ![ACI bağlamınız içinde çalışan kapsayıcı](media/contextcontainer.png)

1. Tüm bunların düzgün çalıştığını kontrol etmek için çalışan kapsayıcıya sağ tıklayabilirsiniz ve Tarayıcıda **görüntüle'yi seçebilirsiniz.**

   ![ACI'da genel IP ile kapsayıcı](media/containerinaci.png)

Ayrıca kapsayıcının genel IP'de çalıştığını ve düzgün çalıştığını da görüyorsunuz!

1. Şimdi, nasıl çalıştığını görmek için çalışan kapsayıcımıza göz atabilirsiniz. Kapsayıcı günlüklerine göz atarak başlayabilirsiniz:
 
 ```bash
   docker logs distracted-jackson
   ```

1. Ayrıca, yerel bir kapsayıcıda olduğu gibi kapsayıcınıza da exec çalıştırılabilir.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Son olarak çalışma alanınızı temizlemek ve test kapsayıcısı çalıştırmaya devam etmek için ücret ödemeye gerek olmadığınızdan emin olmak için, çalışan kapsayıcıya sağ tıklar ve Kaldır'ı **seçebilirsiniz.**

## <a name="recap"></a>Özet

Harika, iş yüklerinizi ilk kez başarıyla buluta dağıttınız. Bunların hepsini komut satırıyla ve aynı zamanda çok kapsayıcılı uygulamalarınızı çalıştırmak için kullanarak ve kullanarak ACI `docker run` `docker compose up` bağlamınız içinde de çalıştırabilirsiniz. Kapsayıcılarınızı bulutta çalıştırma hakkında daha fazla bilgi için [ACI](https://docs.docker.com/engine/context/aci-integration/)kullanma ile ilgili genişletilmiş belgeleri okuyun.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Sırada ne var?](whats-next.md)
