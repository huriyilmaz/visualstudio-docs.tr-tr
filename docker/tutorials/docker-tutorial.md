---
title: 'Öğretici: Docker & ile çalışmaya başlama Visual Studio Code'
description: Visual Studio Code ile Docker ile çalışmanın temellerini kapsayan çok adımlı bir öğretici.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: tutorial
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 75a51f478e4e58700f6025dd6a87fcc38439ed87
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222662"
---
# <a name="tutorial-get-started-with-docker"></a>Öğretici: Docker 'ı kullanmaya başlama

Bu öğreticide, bir veritabanıyla birden çok kapsayıcı kullanma ve Docker Compose kullanma dahil olmak üzere Docker uygulamaları oluşturma ve dağıtma hakkında bilgi edineceksiniz. Ayrıca Kapsayıcılı uygulamanızı Azure 'a dağıtırsınız.

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
