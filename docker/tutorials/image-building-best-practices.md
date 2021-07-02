---
title: 'Docker öğreticisi - Bölüm 8: Görüntü katmanlama'
description: Docker görüntülerde görüntü katmanlarını inceleme ve yönetme.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8f669baf6f3275f54c7e4a6ff2b31f9c260b2bb9
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222675"
---
# <a name="image-layering"></a>Görüntü katmanlama

Bir görüntüyü neyin yaptığını bakabilirsiniz, biliyor mmusunuz? komutunu `docker image history` kullanarak, bir görüntü içinde her katmanı oluşturmak için kullanılan komutu görüntüye bakabilirsiniz.

1. Öğreticide `docker image history` daha önce oluşturduğunuz görüntüdeki katmanları görmek için komutunu `getting-started` kullanın.

    ```bash
    docker image history getting-started
    ```

    Aşağıdakine benzer bir çıkış alasınız (tarihler/kimlikler farklı olabilir).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Satırların her biri görüntüde bir katmanı temsil eder. Buradaki görüntüde en alttaki temel, en üstte en yeni katman gösterilir. Bunu kullanarak her katmanın boyutunu hızla görebilir ve büyük görüntüleri tanılamaya yardımcı olursunuz.

1. Birkaç satırın kesiliyor olduğunu fark vardır. Bayrağı `--no-trunc` eklersiniz, tam çıkışı alırsınız (evet, kesilmemiş bayrağı kullanarak izinsiz çıkış alırsınız).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Katman önbelleğe alma

Katmanlamanın nasıl bir işlem olduğunu gördünüz. Kapsayıcı görüntüleriniz için derleme sürelerini azaltmaya yardımcı olmak için öğrenmeniz gereken önemli bir ders vardır.

> Katman değiştiktan sonra tüm aşağı akış katmanlarının da yeniden oluşturulması gerekir

Şimdi bir kez daha kullanmakta olduğu Dockerfile'a bakalım...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Görüntü geçmişi çıkışına geri dönüp Dockerfile dosyasındaki her komutun görüntüde yeni bir katmana sahip olduğunu görüyorsunuz. Görüntüde değişiklik yaptıktan sonra yarn bağımlılıklarını yeniden yüklemek zorunda olduğunu hatırlayabilirsiniz. Bunu düzeltmenin bir yolu var mı? Her derlemede aynı bağımlılıkların etrafından gönderi yapmak pek anlamlı değildir, değil mi?

Bunu düzeltmek için Bağımlılıkların önbelleğe alınmasını desteklemek üzere Dockerfile dosyanızı yeniden yapılandırırsiniz. Düğüm tabanlı uygulamalar için bu bağımlılıklar dosyasında `package.json` tanımlanır. Peki önce yalnızca bu dosyayı kopyalayıp bağımlılıkları yüklemiş  ve ardından diğer her şeyi kopyalarsanız ne olur? Ardından, yalnızca üzerinde bir değişiklik varsa yarn bağımlılıklarını yeniden `package.json` oluşturun. Mantıklı?

1. Dockerfile dosyasını ilk kopyada `package.json` kopyalamak, bağımlılıkları yüklemek ve ardından içinde diğer her şeyi kopyalamak için güncelleştirin.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. kullanarak yeni bir görüntü `docker build` derleme.

    ```bash
    docker build -t getting-started .
    ```

    Aşağıdaki gibi bir çıkış görüyor gerekir...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Tüm katmanların yeniden oluşturulmuş olduğunu görüyorsunuz. Dockerfile'ı biraz değiştirdiğiniz için mükemmel bir sorun değil.

1. Şimdi dosyada bir değişiklik `src/static/index.html` (örneğin , `<title>` "The Awesome Todo App" olarak değiştir) olarak değiştirebilirsiniz.

1. Docker görüntüsünü şimdi yeniden kullanarak `docker build` derleme. Bu kez çıkışınız biraz farklı görünüyor olabilir.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    İlk olarak, derlemenin çok daha hızlı olduğunu fark etmek gerekir! 1-4. adımların da olduğunu da `Using cache` göreceğiz. İşte bu kadar! Derleme önbelleğini kullanıyorsanız. Bu görüntüyü ve güncelleştirmeleri itip çekmek de çok daha hızlı olacaktır. Yaşasın!

## <a name="multi-stage-builds"></a>Çok aşamalı derlemeler

Bu öğreticide çok fazla incelemeye gerek yok ancak çok aşamalı derlemeler, görüntü oluşturmak için birden çok aşamayı kullanmaya yardımcı olan inanılmaz güçlü bir araçtır. Bunlar için çeşitli avantajlar vardır:

- Derleme zamanı bağımlılıklarını çalışma zamanı bağımlılıklarından ayırma
- Yalnızca uygulamanın çalışması için *gerekenleri göndererek* genel görüntü boyutunu azaltma

### <a name="maventomcat-example"></a>Maven/Tomcat örneği

Java tabanlı uygulamalar derlerken, kaynak kodu Java bytecode'a derlemek için bir JDK gerekir. Ancak bu JDK üretimde gerekli değildir. Ayrıca, uygulamayı derlemeye yardımcı olmak için Maven veya Gradle gibi araçları kullanıyor da olabilirsiniz.
Bunlar son görüntüde de gerekli değildir. Çok aşamalı derlemeler yardımcı olur.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

Bu örnekte, Maven kullanarak gerçek `build` Java derlemesi gerçekleştirmek için bir aşama (adlı) 2. aşama 2. İkinci aşama ('den `FROM tomcat` başlayarak), aşamanın dosyalarına `build` kopyalar. Son görüntü yalnızca oluşturulan son aşamadır (bayrağı kullanılarak geçersiz `--target` kılınabilir).

### <a name="react-example"></a>React örnek

Uygulama React, JS kodunu (genellikle JSX), SASS stil sayfaları ve daha fazlasını statik HTML, JS ve CSS'de derlemek için bir Node ortamına ihtiyacınız vardır. Sunucu tarafı işleme yapmıyorsanız üretim derlemesi için node ortamına bile ihtiyacınız yok. Statik kaynakları neden statik bir nginx kapsayıcısı içinde gönderm yok?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Burada, derlemeyi gerçekleştirmek (katman önbelleğini en üst düzeye çıkarmak) ve çıkışı nginx kapsayıcısı içine kopyalamak için `node:12` bir görüntü kullanıyorsanız. Harika, değil mi?

## <a name="recap"></a>Özet

Görüntülerin nasıl yapılandırıldıklarının biraz anlaşılmasıyla, görüntüleri daha hızlı bir şekilde derlemek ve daha az değişiklik göndererek bunu yapabilirsiniz. Çok aşamalı derlemeler, derleme zamanı bağımlılıklarını çalışma zamanı bağımlılıklarından ayırarak genel görüntü boyutunu azaltmaya ve son kapsayıcı güvenliğini artırmaya da yardımcı olur.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Buluta dağıtma](deploy-to-cloud.md)