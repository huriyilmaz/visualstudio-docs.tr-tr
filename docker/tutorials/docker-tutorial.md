---
title: 'Öğretici: Kullanmaya başlayın Mac üzerinde Docker & Visual Studio Code ile Windows oluşturma'
description: Docker ile çalışmayla ilgili temel bilgileri kapsayan çok adımlı bir öğretici Visual Studio Code.
ms.prod: vs-code
ms.topic: tutorial
ms.author: mikemort
author: BigMorty
manager: jmartens
ms.reviewer: nebuk89, ghogen
ms.custom: “docker-team-owned”
ms.date: 08/06/2021
ms.openlocfilehash: 7cfdbaf98c0f1465c31eb8c8e490fa24e00364a9
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650124"
---
# <a name="tutorial-get-started-with-docker"></a>Öğretici: Docker Kullanmaya başlayın ile birlikte kullanma

Bu öğreticide, veritabanıyla birden çok kapsayıcı kullanma ve Windows kullanarak Visual Studio Code veya Mac üzerinde Docker uygulamaları oluşturma ve dağıtma hakkında bilgi Docker Compose. Ayrıca kapsayıcılı uygulamanızı Azure'a dağıtın.

Kapsayıcılar, tam işletim sisteminin tam boyutu ve ek yükü olmadan uygulama oluşturmak ve çalıştırmaya bir platform sağlayan sanal makineler (VM) gibi küçük sanallaştırılmış ortamlardır. [Docker,](https://www.docker.com) üçüncü taraf, endüstri standardı bir kapsayıcı sağlayıcısı ve kapsayıcı yönetim sistemidir. Docker Desktop makineniz üzerinde çalışır ve yerel kapsayıcılarınızı yönetir. Visual Studio VS Code gibi geliştirme araçları, kapsayıcılı uygulamalar oluşturmak, kapsayıcılara uygulama dağıtmak ve kapsayıcılar üzerinde çalışan uygulamalarda hata ayıklamak için yerel olarak yüklenmiş bir Docker Desktop hizmetiyle çalışmanızı sağlar.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio Code](https://code.visualstudio.com/download)
- Windows Mac [için](https://docs.docker.com/docker-for-windows/install/) Docker [Desktop.](https://docs.docker.com/docker-for-mac/install/)

## <a name="start-the-tutorial"></a>Öğreticiyi başlatın

Öğreticiye başlamanız için komutunu zaten çalıştırdıysanız tebrikler!  Açılmazsa, bir komut istemi veya bash penceresi açın ve komutu çalıştırın:

```cli
docker run -d -p 80:80 docker/getting-started
```

Kullanılan birkaç bayrak olduğunu fark edesiniz. Bu bilgiler hakkında daha fazla bilgi:

- `-d` - Kapsayıcıyı ayrılmış modda (arka planda) çalıştırma
- `-p 80:80` - konakta 80 olan bağlantı noktasını kapsayıcının 80. bağlantı noktasına eşle
- `docker/getting-started` - kullanmak için görüntü

> [!TIP]
> Tam komutu kısaltmak için tek karakter bayraklarını birleştirebilirsiniz.
> Örneğin yukarıdaki komut şöyle yazabilirsiniz:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>VS Code Uzantısı

Çok ileri gitmeden önce, makineniz üzerinde çalışan kapsayıcıların hızlı bir görünümünü VS Code Docker VS Code Uzantısı'nın vurgulanır. Kapsayıcı günlüklerine hızlı erişim sağlar, kapsayıcının içinde bir kabuk elde eder ve kapsayıcı yaşam döngüsünü (durdurma, kaldırma vb.) kolayca yönetmenizi sağlar.

Uzantıya erişmek için buradaki yönergeleri [izleyin.](https://code.visualstudio.com/docs/containers/overview) Sol tarafta Docker simgesini kullanarak Docker görünümünü açın. Uzantıyı şimdi açarsanız, bu öğreticinin çalıştırlı olduğunu göreceğiz! Kapsayıcı adı `angry_taussig` (aşağıda) rastgele oluşturulmuş bir addır. Bu nedenle büyük olasılıkla farklı bir adınız olacak.

![Docker Uzantısında çalışan öğretici kapsayıcısı](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Kapsayıcı nedir?

Artık bir kapsayıcı çalıştırabilirsiniz, *kapsayıcı* nedir? Basitçe ifade edin; kapsayıcı, makineniz üzerinde konak makinede yer alan diğer tüm işlemlerden yalıtılmış olan başka bir işlemdir. Bu yalıtım, uzun [süredir Linux'ta olan](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504)çekirdek ad alanlarını ve cgroup'ları kullanır. Docker, bu özellikleri kolay ve kolay bir şekilde yaklaşmak için çalıştı.

> [!NOTE]
> **Sıfırdan Kapsayıcı Oluşturma** Kapsayıcıların sıfırdan nasıl derlendiklerini görmek için Aqua Security'den Liz Aqua Security'nin Go'da sıfırdan kapsayıcı oluşturduğu bir video vardır:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Kapsayıcı görüntüsü nedir?

Kapsayıcıyı çalıştırarak yalıtılmış bir dosya sistemi kullanır. Bu özel dosya sistemi bir kapsayıcı görüntüsü **tarafından sağlanır.** Görüntü kapsayıcının dosya sistemi içerdiği için bir uygulamayı çalıştırmak için gereken her şeyi (tüm bağımlılıklar, yapılandırma, betikler, ikili dosyalar gibi) içermesi gerekir. Görüntü ayrıca kapsayıcı için ortam değişkenleri, çalıştıracak varsayılan komut ve diğer meta veriler gibi başka yapılandırmalar da içerir.

Daha sonra katmanlama, en iyi yöntemler ve daha fazlası gibi konuları kapsayan görüntüleri daha derinlemesine inceleeceğiz.

> [!NOTE]
> hakkında bilgi sahibiysiniz, `chroot` kapsayıcıyı genişletilmiş sürümü olarak düşün. `chroot` Dosya sistemi yalnızca görüntüden gelir. Ancak, bir kapsayıcı yalnızca chroot kullanılırken ek yalıtım ek olarak kullanılamaz.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Uygulama](your-application.md)

Bazı kaynaklar:
+ [Docker Cloud Integration](https://github.com/docker/compose-cli)
+ [Örnekler](https://github.com/docker/awesome-compose)
