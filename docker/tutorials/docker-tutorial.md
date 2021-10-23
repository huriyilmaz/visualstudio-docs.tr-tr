---
title: "öğretici: Windows veya Mac 'te docker & Visual Studio Code kullanmaya başlama"
description: Visual Studio Code ile Docker ile çalışmanın temellerini kapsayan çok adımlı bir öğretici.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: tutorial
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: c4b1bd4a05c7c8a95a457c18be248cb40a0f94a2
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130211460"
---
# <a name="tutorial-get-started-with-docker"></a>Öğretici: Docker 'ı kullanmaya başlama

bu öğreticide, bir veritabanı ile birden çok kapsayıcı kullanma ve Docker Compose kullanma dahil olmak üzere Visual Studio Code kullanarak Windows veya Mac 'te docker uygulamaları oluşturma ve dağıtma hakkında bilgi edineceksiniz. Ayrıca Kapsayıcılı uygulamanızı Azure 'a dağıtırsınız.

Kapsayıcılar, uygulama oluşturmaya ve çalıştırmaya yönelik bir platform sağlayan sanal makineler (VM 'Ler) gibi kompakt sanallaştırılmış ortamlardır, ancak tam işletim sisteminin tam boyutunu ve ek yükünü ortadan kaldırır. [Docker](https://www.docker.com) , üçüncü taraf, sektör standardı kapsayıcı sağlayıcısı ve kapsayıcı yönetim sistemidir. Docker Desktop makinenizde çalışır ve yerel Kapsayıcılarınızı yönetir. Visual Studio ve VS Code gibi geliştirme araçları, kapsayıcılı uygulamalar oluşturmak, kapsayıcılara uygulama dağıtmak ve kapsayıcılarınızdan çalışan uygulamalarda hata ayıklamak için yerel olarak yüklenen bir docker Desktop hizmeti ile çalışmanıza olanak sağlayan uzantılar sunmaktadır.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio Code](https://code.visualstudio.com/download)
- [Windows](https://docs.docker.com/docker-for-windows/install/) veya [Mac](https://docs.docker.com/docker-for-mac/install/)için docker Desktop.

## <a name="start-the-tutorial"></a>Öğreticiyi başlatın

Öğreticiyi kullanmaya başlamak için komutunu zaten çalıştırırsanız Tebrikler!  Aksi takdirde, bir komut istemi veya bash penceresi açın ve şu komutu çalıştırın:

```cli
docker run -d -p 80:80 docker/getting-started
```

Kullanılan birkaç bayrak görürsünüz. Bunlar hakkında daha fazla bilgi aşağıda verilmiştir:

- `-d` -kapsayıcıyı ayrılmış modda çalıştırın (arka planda)
- `-p 80:80` -Konağın 80 bağlantı noktasını kapsayıcıda bağlantı noktası 80 ' e eşleyin
- `docker/getting-started` -kullanılacak resim

> [!TIP]
> Tam komutu kısaltmak için tek karakter bayraklarını birleştirebilirsiniz.
> Örnek olarak, yukarıdaki komutu şöyle yazılabilir:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>VS Code uzantısı

çok uzakta geçmeden önce, makinenizde çalışan kapsayıcıların hızlı bir görünümünü sağlayan docker VS Code uzantısını vurgulamak istiyoruz. Kapsayıcı günlüklerine hızlı erişim sağlar, kapsayıcının içindeki bir kabuğu almanızı sağlar ve kapsayıcı yaşam döngüsünü (durdurma, kaldırma, vb.) kolayca yönetmenizi sağlar.

Uzantıya erişmek için [buradaki](https://code.visualstudio.com/docs/containers/overview)yönergeleri izleyin. Sol taraftaki Docker simgesini kullanarak Docker görünümünü açın. Uzantıyı şimdi açarsanız, bu öğreticiyi çalıştırıyor olursunuz! Kapsayıcı adı ( `angry_taussig` aşağıdaki) rastgele oluşturulmuş bir addır. Bu nedenle muhtemelen büyük olasılıkla farklı bir ada sahip olacaksınız.

![Docker uzantısında çalışan öğretici kapsayıcısı](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Kapsayıcı nedir?

Artık bir kapsayıcı çalıştırdığınıza göre, *kapsayıcı nedir?* Yalnızca bir kapsayıcı, makinenizde ana makinedeki diğer işlemlerden yalıtılmış başka bir işlemdir. Bu yalıtım, Linux 'ta uzun bir süredir bulunan [çekirdek ad alanları ve cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504)özelliklerinden yararlanır. Docker bu özellikleri ulaşılabilir ve kullanımı kolay hale getirmek için çalıştı.

> [!NOTE]
> **Sıfırdan kapsayıcılar oluşturma** Kapsayıcıların sıfırdan nasıl oluşturulduğunu görmek isterseniz, deniz mavisi güvenlik 'teki Liz, go 'dan sıfırdan bir kapsayıcı oluşturan bir videoya sahiptir:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Kapsayıcı görüntüsü nedir?

Bir kapsayıcı çalıştırırken, yalıtılmış bir dosya sistemi kullanır. Bu özel dosya sistemi bir **kapsayıcı görüntüsü** tarafından sağlanır. Görüntü kapsayıcının dosya sistemini içerdiğinden, bir uygulamayı çalıştırmak için gereken her şeyi içermesi gerekir-tüm bağımlılıklar, yapılandırma, betikler, ikili dosyalar, vb. Görüntü Ayrıca, kapsayıcı için ortam değişkenleri, çalıştırılacak varsayılan komut ve diğer meta veriler gibi diğer yapılandırmaları da içerir.

Daha sonra, katman, en iyi uygulamalar ve daha fazlası gibi konuları kapsayan görüntüleri daha ayrıntılı bir şekilde inceleyeceğiz.

> [!NOTE]
> `chroot`' İ tanıyorsanız, bir kapsayıcıyı genişletilmiş bir sürümü olarak düşünün `chroot` . Dosya sistemi yalnızca görüntüden geliyor. Ancak, bir kapsayıcı yalnızca chroot kullanılırken kullanılabilir ek yalıtım ekler.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Uygulama](your-application.md)
