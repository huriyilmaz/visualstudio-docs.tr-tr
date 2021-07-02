---
title: 'Docker öğreticisi-Bölüm 9: buluta dağıtma'
description: Barındırma için bir bulut hizmetine Docker uygulaması dağıtın.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: da38b7482396b0bf46f5566c0c4a5416c94e83eb
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222831"
---
# <a name="deploy-to-the-cloud"></a>Buluta dağıtın

Uygulamanızı yerel olarak çalıştırdığınıza göre, diğer kişilerin bu uygulamaya erişebilmesi ve onu kullanabilmesi için bulutta çalıştırmayı düşünmek üzere bir başlangıç yapabilirsiniz. Bunu yapmak için Docker bağlamlarını kullanacaksınız. Bağlam, şu anda kapsayıcılarla çalışmakta olduğunuz yerdir. Şu anda yalnızca "varsayılan" içeriğiniz vardır. bu nedenle, bir bulut eklemeniz ve uygulamanızı buna dağıtmanız gerekir.

## <a name="create-your-cloud-context"></a>Bulut bağlamını oluşturma

1. Başlamak için, Docker panelinin bağlamlar bölümüne bakarak sahip olduğunuz bağlamlara bakabilirsiniz:

   ![Yalnızca varsayılan bağlamı gösterir](media/defaultcontext.png)

Yerel iş için yalnızca varsayılan bağlamı görmeniz gerekir.

1. Buluta dağıtmak için yeni bir ACI bağlamı oluşturmanız gerekir, ancak bunu yapmak için önce Azure hesap uzantısının Azure 'da kimlik doğrulaması yapması gerekir.

   ![Azure uzantısı ekleniyor](media/addazureextension.png)

Henüz yoksa bir Azure hesabı ayarlamanız gerekir.

1. Şimdi yeni acı bağlamınızı oluşturabilirsiniz. Bunu, Docker görünümündeki **bağlamlar** bölümünde yer alan artı düğmesine tıklayarak yapabilirsiniz.

   ![ACI bağlamını oluşturma](media/createnewcontext.png)

Bu, altında bu kapsayıcıları çalıştırmak istediğiniz kaynak grubunu sorar. Ok tuşlarını kullanarak var olan bir grubu seçin ya da yeni grubu kullanmak için varsayılan seçeneği kullanın.

![Kaynak grubunuzu seçme](media/selectresourcegroup.png)

Artık ACI bağlamını listelenmiş olarak görebilir ve geçerli odağınızı/kullanımda olan bağlamı açmak için sağ tıklayıp tıklamayı seçebilirsiniz:

![Yeni acı bağlamı seçilebilir](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Kapsayıcıları bulutta çalıştırın

1. Şimdi ACI bağlamını kullanın ve kapsayıcıyı çalıştırın.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Bunu çalıştırmak zorunda kalmadan, artık bağlamınızda kapsayıcıya bakabilirsiniz.

   ![ACı bağlamınızda çalışan kapsayıcı](media/contextcontainer.png)

1. Bunun düzgün şekilde çalıştığından emin olmak için, çalışan kapsayıcıya sağ tıklayıp **Tarayıcıda görüntüle** seçeneğini belirleyebilirsiniz.

   ![Ortak IP ile acı 'de kapsayıcı](media/containerinaci.png)

Ayrıca, kapsayıcının ortak bir IP 'de çalıştığını ve doğru şekilde çalıştığını görebilirsiniz!

1. Şimdi nasıl çalıştığını görmek için çalışan kapsayımıza göz atabilirsiniz. ' İ, kapsayıcı günlüklerine bakarak başlayabilirsiniz:
 
 ```bash
   docker logs distracted-jackson
   ```

1. Ayrıca, yerel bir kapsayıcıda yaptığınız gibi kapsayıcınızı da kullanabilirsiniz.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Son olarak, çalışma alanınızı temizlemek ve test kapsayıcısını çalıştırmaya devam etmek için ücretlendirilmediğinden emin olmak için, çalışan kapsayıcıya sağ tıklayıp **Kaldır**' ı seçmeniz yeterlidir.

## <a name="recap"></a>Özet

Artık iş yükünüzü aldınız ve ilk kez buluta başarıyla dağıttınız. Bunu, komut satırından ve kullanarak ACI bağlamınızın içinden `docker run` ve ayrıca `docker compose up` çok Kapsayıcılı uygulamalarınızı çalıştırmak için kullanarak yapabilirsiniz. Kapsayıcılarınızı bulutta çalıştırma hakkında daha fazla bilgi edinmek için [ACI 'yi kullanma hakkında genişletilmiş belgeleri](https://docs.docker.com/engine/context/aci-integration/)okuyun.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Sıradaki](whats-next.md)
