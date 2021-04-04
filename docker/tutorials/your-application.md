---
title: 'Docker öğreticisi-1. Bölüm: Yapılacaklar listesi örnek uygulamasını derleme ve çalıştırma'
description: Node.js 'de çalışan yapılacaklar listesi örnek uygulamasına genel bakış.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 1b92792cf9db0090c52f583754e56c306e6d7234
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082584"
---
# <a name="build-and-run-the-todo-sample-app"></a>Todo örnek uygulamasını derleyin ve çalıştırın

Bu öğreticinin geri kalanında Node.js ' de çalışan basit bir yapılacaklar listesi Yöneticisi ile çalışmaya başlayacaksınız. Node.js konusunda bilgi sahibi değilseniz endişelenmeyin! Gerçek bir JavaScript deneyimi gerekmez!

Bu noktada, geliştirme ekibiniz oldukça küçüktür ve MVP 'nizi (en az uygulanabilir ürün) kanıtlamak için yalnızca bir uygulama oluşturmaktır. Nasıl çalıştığını ve büyük bir ekip, birden çok geliştirici ve benzeri için nasıl çalışacağınızı düşünmenize gerek kalmadan ne yapabileceğinize ilişkin bilgi almak istiyorsunuz.

![Todo List Manager ekran görüntüsü](media/todo-list-sample.png)

## <a name="get-the-app"></a>Uygulamayı alın

Uygulamayı çalıştırmadan önce, makinenizde uygulama kaynak kodunu almanız gerekir. Gerçek projeler için genellikle depoyu kopyalacaksınız. Ancak, bu öğretici için, uygulamayı içeren bir ZIP dosyası oluşturduk.

1. Yerel makinede Docker for Windows veya Docker Community Edition 'ın yüklü olduğundan emin olun. [Docker for Windows yükleme belgelerine](https://docs.docker.com/docker-for-windows/install/)bakın. Yüklemesi işlemi, örneği içeren ZIP dosyasını localhost adresinde kullanılabilir hale getirir.

1. [ZIP 'ı indirin](https://github.com/docker/getting-started/tree/master/app). ZIP dosyasını açın ve içeriği ayıkladığınızdan emin olun.

1. Ayıkladıktan sonra, en sevdiğiniz kod düzenleyicinizi kullanarak projeyi açın. Düzenleyicinizde ihtiyacınız varsa [Visual Studio Code](https://code.visualstudio.com/)kullanabilirsiniz. `package.json`Ve iki alt dizin görmeniz gerekir ( `src` ve `spec` ).

    ![Yüklenen uygulama ile açılan Visual Studio Code ekran görüntüsü](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Uygulamanın kapsayıcı görüntüsünü oluşturma

Uygulamayı derlemek için, kullanmanız gerekir `Dockerfile` . Dockerfile, yalnızca bir kapsayıcı görüntüsü oluşturmak için kullanılan yönergelerin metin tabanlı bir betiğinden oluşur. Daha önce Dockerfiles oluşturduysanız aşağıdaki Dockerfile dosyasında birkaç kusuru görebilirsiniz. Ancak endişelenmeyin! Bunlar üzerinden devam edeceğiz.

1. `Dockerfile`Aşağıdaki içeriklerle dosyayla aynı klasörde adlı bir dosya oluşturun `package.json` .

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Lütfen dosyanın `Dockerfile` benzer bir dosya uzantısına sahip olup olmadığını denetleyin `.txt` . Bazı düzenleyiciler bu dosya uzantısını otomatik olarak ekleyebilir ve bu, bir sonraki adımda hata oluşmasına neden olur.

1. Daha önce yapmadıysanız, bir Terminal açın ve `app` ile dizine gidin `Dockerfile` . Şimdi komutunu kullanarak kapsayıcı görüntüsünü oluşturun `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Alternatif olarak, Dockerfile dosyasına sağ tıklayıp **resim oluştur...** öğesini seçip, ardından istemde etiketi belirtebilirsiniz.

    Bu komut, yeni bir kapsayıcı görüntüsü oluşturmak için Dockerfile 'ı kullandı. Çok sayıda "katman" indirdiğini fark etmiş olabilirsiniz. Bunun nedeni, görüntüden başlamasını istediğiniz oluşturucuyu istedik `node:12-alpine` . Ancak makinenizde bu olduğundan, bu görüntünün indirilmesi gerekir.

    Görüntü indirildikten sonra uygulamanıza kopyalanıp `yarn` uygulamanızın bağımlılıklarını yüklemek için kullanılır. `CMD`Yönerge, bu görüntüden bir kapsayıcı başlatılırken çalıştırılacak varsayılan komutu belirtir.

    Son olarak, `-t` bayrak resminizi etikettir. Bunu, son görüntü için yalnızca insan tarafından okunabilen bir ad olarak düşünün. Görüntüyü adlandırdığınızda `getting-started` , bir kapsayıcıyı çalıştırdığınızda söz konusu görüntüye başvurabilirsiniz.

    `.`Komutun sonunda, `docker build` Docker 'ın geçerli dizinde ' i araması gerektiğini söyler `Dockerfile` .

## <a name="starting-an-app-container"></a>Uygulama kapsayıcısı başlatılıyor

Artık bir görüntünüz olduğuna göre uygulamayı çalıştırın! Bunu yapmak için `docker run` komutunu kullanın (daha önce bu tarihten itibaren hatırlayın).

1. Komutunu kullanarak kapsayıcınızı başlatın `docker run` ve yeni oluşturduğunuz görüntünün adını belirtin:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    `-d`Ve bayrakları hatırlayın `-p` mı? Yeni kapsayıcıyı "ayrılmış" modda (arka planda) çalıştırıyorsunuz ve konağın bağlantı noktası 3000 ile kapsayıcının bağlantı noktası 3000 arasında bir eşleme oluşturuyorsunuz. Bağlantı noktası eşlemesi olmadan uygulamaya erişemezsiniz.

1. Birkaç saniye sonra Web tarayıcınızı ' e açın [http://localhost:3000](http://localhost:3000) .
    Uygulamayı görmeniz gerekir!

    ![Boş Todo listesi](media/todo-list-empty.png)

1. Devam edin ve bir öğe veya iki tane ekleyin ve beklendiği gibi çalıştığını görün. Öğeleri tamamen işaret edebilir ve öğeleri kaldırabilirsiniz. Ön uçlarınız öğeleri arka uçta başarıyla depoladığını! Oldukça hızlı ve kolay, kuh?

Bu noktada, hepsi sizin tarafınızdan oluşturulmuş birkaç öğe içeren çalışan bir Todo List Manager olmalıdır! Şimdi birkaç değişiklik yapalim ve Kapsayıcılarınızı yönetme hakkında bilgi edinin.

VS Code uzantıya hızlı bir görünüm alırsanız, şu anda çalışan iki kapsayıcınızı görmeniz gerekir (Bu öğretici ve daha önce oluşturduğunuz uygulama kapsayıcısı)!

![Eğitim ve uygulama kapsayıcıları çalıştıran Docker uzantısı](media/vs-two-containers.png)

## <a name="recap"></a>Özet

Bu kısa bölümde bir kapsayıcı görüntüsü oluşturma ve bunu yapmak için bir Dockerfile oluşturma hakkında temel bilgileri öğrendiniz. Bir görüntü oluşturduktan sonra kapsayıcıyı başlatmış ve çalışan uygulamayı gördünüz!

Ardından, uygulamada bir değişiklik yaparsınız ve çalışan uygulamayı yeni bir görüntüyle nasıl güncelleştireceğinizi öğreneceksiniz. Bu şekilde, diğer birkaç yararlı komut öğreneceksiniz.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Uygulamanızı güncelleştirme](update-your-app.md)
