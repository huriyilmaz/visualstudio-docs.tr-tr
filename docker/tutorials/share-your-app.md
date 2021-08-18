---
title: 'Docker öğreticisi - 2. Bölüm: Uygulamanızı paylaşma'
description: Kayıt defterini kullanarak Docker görüntülerinin nasıl Docker Hub açıklar.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 0367ca6b2ab6219ab50030df0b80a6aed213854f
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334431"
---
# <a name="share-your-app"></a>Uygulamalarınızı paylaşma

Artık bir görüntü oluşturduk, şimdi de paylaşacağız! Docker görüntülerini paylaşmak için bir Docker kayıt defteri kullanacağız. Varsayılan kayıt Docker Hub ve kullanılan tüm görüntülerin nereden geliyor olduğu.

## <a name="create-a-repo"></a>Bir repo oluşturma

Bir görüntüyü itmek için öncelikle görüntü üzerinde bir Docker Hub.

1. Oturum [Docker Hub](https://hub.docker.com/signup/msftedge?utm_source=msftedge) ve gerekirse oturum aç'a gidin.

1. Depo **Oluştur düğmesine** tıklayın.

1. Repo adı olarak `getting-started` kullanın. Görünürlüğün olduğundan emin `Public` olun.

1. Oluştur **düğmesine** tıklayın!

Sayfanın sağ tarafına bakarsanız Docker komutları adlı bir **bölüm görebilirsiniz.** Bu, bu repoya itmek için çalıştırması gereken örnek bir komut verir.

![Push örneğiyle Docker komutu](media/push-command.png)

## <a name="push-the-image"></a>Görüntüyü gönderme

1. Komut satırına, komut satırına gördüğünüz push komutunu Docker Hub. Komutunuz "docker" değil ad alanını kullanır.

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Neden başarısız oldu? Push komutu docker/getting-started adlı bir görüntü arıyor ama bulamadı. 'i `docker image ls` çalıştırsanız da bir tane görmeyersiniz.

    Bunu düzeltmek için, başka bir ad vermek için var olan görüntülerinizi "etiketlemeniz" gerekir.

1. komutunu kullanarak Docker Hub oturum `docker login -u <username>` açma.

1. Görüntüye `docker tag` yeni bir ad vermek için komutunu `getting-started` kullanın. Docker kimliğiniz `<username>` ile değiştirmeyin.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Şimdi push komutunu yeniden deneyin. Değeri Docker Hub kopya ediyorsanız, görüntü adına etiket eklemeden bölümünü `tagname` bırakın. Etiket belirtmezseniz Docker adlı bir etiket `latest` kullanır.

    ```bash
    docker push <username>/getting-started
    ```

    Komut satırı yerine Docker görünümünün **Görüntüler** bölümünde görüntü etiketine sağ tıklar ve **Push...** seçeneğini ve ardından Bağlan **registry...** öğesini ve ardından öğesini **Docker Hub.**

## <a name="run-the-image-on-a-new-instance"></a>Görüntüyü yeni bir örnekte çalıştırma

Artık görüntünüz yerleşik ve kayıt defterine ekli olduğu için uygulamayı bu kapsayıcı görüntüsünü daha önce hiç görene yeni bir örnekte çalıştırmayı deneyin! Bunu yapmak için Docker ile Oynat'ı kullan kullanırsiniz.

1. Docker ile [oynatmak için tarayıcınızı açın.](http://play-with-docker.com)

1. Docker Hub oturum açın.

1. Oturum açtıktan sonra sol kenar çubuğundaki "+ Yenİ ÖRNEK EKLE" bağlantısına tıklayın. (Görmüyorsanız tarayıcınızı biraz daha genişletin.) Birkaç saniye sonra tarayıcınızda bir terminal penceresi açılır.

    ![Docker ile yeni örnek ekleme ile oynatma](media/pwd-add-new-instance.png)

1. Terminalde yeni bir şekilde itilmiş olan uygulamayı başlatabilirsiniz.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Görüntünün çek olduğunu ve sonunda başlat gerektiğini görüyoruz!

1. Geldiğinde 3000 rozetine tıklayın ve değişikliklerinizi kullanarak uygulamayı görüyorsanız! Yaşasın! 3000 rozeti göster yoksa Bağlantı Noktasını Aç düğmesine  tıklayabilirsiniz ve 3000 yazın.

## <a name="recap"></a>Özet

Bu bölümde, görüntüleri kayıt defterine iterek paylaşmayı öğrendiniz. Ardından yepyeni bir örnekle birlikte yeni bir görüntü çalıştırabilirsiniz. İşlem hattının görüntüyü oluşturarak bir kayıt defterine iterek üretim ortamının görüntünün en son sürümünü kullanabileceği CI işlem hatlarında bu durum oldukça yaygındır.

Artık bunu anlayana kadar, son bölümün sonunda uygulamayı yeniden başlattıktan sonra tüm todo listesi öğelerinizi kaybettiğinizi hatırlayın. Bu kesinlikle harika bir kullanıcı deneyimi değildir, bu nedenle verileri yeniden başlatmalarda nasıl kalıcı olarak kalıcı olarak bulundurabilirsiniz?

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Veritabanınızı kalıcı olarak kalıcı olarak oluşturma](persist-your-data.md)
