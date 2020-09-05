---
title: 'Docker öğreticisi-3. kısım: uygulamanızı paylaşma'
description: Docker Hub kayıt defteri kullanılarak Docker görüntülerinin nasıl paylaşılacağını açıklar.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 46f91b3bf163f3847492a7727fa72a39908d441c
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89485543"
---
# <a name="share-your-app"></a>Uygulamanızı paylaşma

Şimdi bir görüntü oluşturduğumuz için paylaşalım! Docker görüntülerini paylaşmak için bir Docker kayıt defteri kullanmanız gerekir. Varsayılan kayıt defteri Docker Hub ' dır ve kullandığımız tüm görüntülerin geldiği yerdir.

## <a name="create-a-repo"></a>Depo oluşturma

Önce bir görüntüyü göndermek için, Docker Hub 'da bir depo oluşturmanız gerekir.

1. [Docker Hub ' a](https://hub.docker.com) gidin ve gerekirse oturum açın.

1. **Depo oluştur** düğmesine tıklayın.

1. Depo adı için öğesini kullanın `getting-started` . Görünürlüğün olduğundan emin olun `Public` .

1. **Oluştur** düğmesine tıklayın!

Sayfanın sağ tarafına bakarsanız **Docker komutları**adlı bir bölüm görürsünüz. Bu, bu depoya göndermek için çalıştırmanız gereken örnek bir komut verir.

![Push örneği ile Docker komutu](media/push-command.png)

## <a name="push-the-image"></a>Görüntüyü gönder

1. Komut satırında, Docker Hub 'da gördüğünüz Push komutunu çalıştırmayı deneyin. Komutunuza "Docker" değil, ad alanınızı kullanmayacağınızı unutmayın.

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Neden başarısız oldu? Push komutu Docker/Başlarken adlı bir görüntü arıyor, ancak bir tane bulamadı. `docker image ls`Öğesini çalıştırırsanız, bunlardan birini görmezsiniz.

    Bunu yapmak için, daha önce derlediğiniz mevcut görüntünüzü başka bir ad vermek üzere "etiketliyoruz" olmanız gerekir.

1. Komutunu kullanarak Docker Hub 'da oturum açın `docker login -u <username>` .

1. `docker tag` `getting-started` Görüntüye yeni bir ad vermek için komutunu kullanın. `<username>`Docker Kimliğiniz ile takas ettiğinizden emin olun.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Şimdi Push komutunu yeniden deneyin. Değeri Docker Hub 'ından kopyalıyorsanız, `tagname` görüntü adına bir etiket eklemediğiniz için bölümü bırakabilirsiniz. Bir etiket belirtmezseniz Docker adlı bir etiket kullanır `latest` .

    ```bash
    docker push <username>/getting-started
    ```

    Komut satırı yerine, Docker görünümündeki **görüntüler** bölümünde görüntü etiketine sağ tıklayıp **Push..**. ' ı ve sonra da **Docker Hub**' **ı seçin.**

## <a name="run-the-image-on-a-new-instance"></a>Görüntüyü yeni bir örnekte Çalıştır

Artık görüntünüz bir kayıt defterine oluşturulup itilmiş olduğuna göre, uygulamayı bu kapsayıcı görüntüsünü hiç görmeyen yepyeni bir örnek üzerinde çalıştırmayı deneyin! Bunu yapmak için Docker ile Play 'i kullanacaksınız.

1. [Docker Ile oynamak](http://play-with-docker.com)için tarayıcınızı açın.

1. Docker Hub hesabınızla oturum açın.

1. Oturum açtıktan sonra sol taraftaki çubukta "+ yenı örnek Ekle" bağlantısına tıklayın. (Görmüyorsanız, tarayıcınızı biraz daha geniş yapın.) Birkaç saniye sonra tarayıcınızda bir Terminal penceresi açılır.

    ![Docker ile oynat yeni örnek Ekle](media/pwd-add-new-instance.png)

1. Terminalde, tekrar gönderilmiş uygulamanızı başlatın.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Görüntünün çekilmesine ve sonunda başlayıp başlamadığını görmeniz gerekir!

1. 3000 rozet üzerine tıkladığınızda uygulamayı yaptığınız değişikliklerle birlikte görmeniz gerekir! Yaşasın! 3000 rozet görünmüyorsa, **bağlantı noktasını aç** düğmesine tıklayıp 3000 yazın.

## <a name="recap"></a>Özet

Bu bölümde, görüntüleri bir kayıt defterine göndererek nasıl paylaşacağınızı öğrendiniz. Daha sonra yepyeni bir örneğe gitti ve yeni gönderilen görüntüyü çalıştırabileceksiniz. Bu, işlem hattının görüntüyü oluşturup bir kayıt defterine gönderilmesi ve ardından üretim ortamının görüntünün en son sürümünü kullanabilmesi için CI işlem hatları içinde oldukça yaygındır.

Artık bu iletişime, son bölümün sonunda uygulamayı yeniden başlattığınızda, yapılacaklar listesi öğelerinizin tümünü kaybettiğiniz geri çektiniz. Harika bir kullanıcı deneyimi değildir, bu nedenle verileri yeniden başlatmalar arasında nasıl kalıcı hale getirebileceğinizi öğreneceksiniz!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Veritabanınızı kalıcı hale getirme](persist-your-data.md)