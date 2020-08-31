---
title: 'Docker öğreticisi-5. Bölüm: görüntü katmanı'
description: Docker görüntülerinde görüntü katmanlarını İnceleme ve yönetme.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89178423"
---
# <a name="image-layering"></a>Resim katmanlama

Bir görüntü oluşturan neye bakabileceğinizi biliyoruz. Komutunu kullanarak `docker image history` , bir görüntü içindeki her bir katmanı oluşturmak için kullanılan komutu görebilirsiniz.

1. `docker image history` `getting-started` Öğreticide daha önce oluşturduğunuz görüntüdeki katmanları görmek için komutunu kullanın.

    ```bash
    docker image history getting-started
    ```

    Aşağıdakine benzer bir çıktı almalısınız (tarihler/kimlikler farklı olabilir).

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

    Her satır görüntüdeki bir katmanı temsil eder. Burada görüntülenen ekran, en üstteki katman olan temeli altta gösterir. Bunu kullanarak, büyük görüntüleri tanılamanıza yardımcı olacak şekilde her katmanın boyutunu da hızla görebilirsiniz.

1. Birçok satırı kesildiğine dikkat edin. `--no-trunc`Bayrağı eklerseniz, tam çıktıyı alırsınız (Evet, kesilen çıktıyı almak için kesilmiş bir bayrak kullanırsınız).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Katman önbelleğe alma

Katmanlanmayı işlem sırasında gördüğünüze göre, kapsayıcı görüntüleriniz için derleme sürelerini azaltmayı öğrenmek için önemli bir ders vardır.

> Bir katman değiştiğinde, tüm aşağı akış katmanlarının de yeniden oluşturulması gerekir

Bir kez daha kullandığınız Dockerfile dosyasına bakalım...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Görüntü geçmişi çıktısına geri dönerek Dockerfile 'daki her komutun görüntüde yeni bir katman haline geldiğini görürsünüz. Görüntüde bir değişiklik yaptığınızda Yarn bağımlılıklarının yeniden yüklenmesi gerektiğini unutmayın. Bunu çözmek için bir yol var mı? Her derleme sırasında aynı bağımlılıklara, doğru bir şekilde gönderim yapmak çok mantıklı değil mi?

Bunu gidermek için, Dockerfile ' ı yeniden yapılandırabilir ve bağımlılıkların önbelleğe alınmasını desteklemeye yardımcı olabilirsiniz. Düğüm tabanlı uygulamalar için bu bağımlılıklar `package.json` dosyada tanımlanmıştır. Bu nedenle, yalnızca bu dosyayı ilk olarak kopyaladıysanız, bağımlılıkları yükledikten *sonra* başka her şeye de kopyalayabilirsiniz. Daha sonra, ' de bir değişiklik olduysa Yarn bağımlılıklarını yeniden oluşturursunuz `package.json` . Anlamlı olsun?

1. Dockerfile 'ı ilk kez kopyalamak için güncelleştirin `package.json` , bağımlılıkları yükler ve sonra ' de diğer her şeyi kopyalayın.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Kullanarak yeni bir görüntü oluşturun `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Aşağıdakine benzer bir çıktı görmeniz gerekir...

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

    Tüm katmanların yeniden oluşturulmuş olduğunu görürsünüz. Dockerfile 'ı tam olarak bir bit olarak değiştirdiğiniz için mükemmel bir şekilde iyidir.

1. Şimdi dosyada bir değişiklik yapın `src/static/index.html` ( `<title>` "başar ToDo uygulaması" olarak değiştirin).

1. Docker görüntüsünü şimdi yeniden kullanarak oluşturun `docker build` . Bu kez, çıktın biraz farklı görünmesi gerekir.

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

    İlk olarak, yapılandırmanın çok daha hızlı olduğunu fark etmelisiniz! Ayrıca, 1-4 adımların tümünün olduğunu görürsünüz `Using cache` . Bu nedenle Hooray! Yapı önbelleğini kullanıyorsunuz. Bu görüntü ve güncelleştirmelerin gönderilmesi ve çekmesi çok daha hızlı olacaktır. Yaşasın!

## <a name="multi-stage-builds"></a>Çoklu aşamalı derlemeler

Bu öğreticide çok fazla bilgi veremedik. çok aşamalı derlemeler, bir görüntü oluşturmak için birden çok aşamanın kullanılmasına yardımcı olan inanılmaz güçlü bir araçtır. Bunların çeşitli avantajları vardır:

- Çalışma zamanı bağımlılıklarından derleme zamanı bağımlılıklarını ayır
- *Yalnızca* uygulamanızın çalışması için gereken öğeleri göndererek genel görüntü boyutunu küçültün

### <a name="maventomcat-example"></a>Maven/Tomcat örneği

Java tabanlı uygulamalar derlerken, kaynak kodu Java bayt koduna derlemek için bir JDK gerekir. Ancak, bu JDK üretimde gerekli değildir. Ayrıca, uygulama oluşturmaya yardımcı olmak için Maven veya Gradle gibi araçlar da kullanabilirsiniz.
Bunlar ayrıca son resimde gerekli değildir. Çoklu aşamalı derleme yardımı.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

Bu örnek `build` , Maven kullanarak gerçek Java derlemesini gerçekleştirmek için bir aşama (çağrıldı) kullanır. İkinci aşama (başlangıç), `FROM tomcat` aşamadaki dosyalardaki kopyalardır `build` . Son görüntü yalnızca oluşturulmakta olan son aşamadır (bayrak kullanılarak geçersiz kılınabilir `--target` ).

### <a name="react-example"></a>Tepki verme örneği

Tepki veren uygulamalar oluştururken, JS kodunu (genellikle JSX), SASS stil sayfalarını ve daha fazlasını statik HTML, JS ve CSS 'ye derlemek için bir düğüm ortamına ihtiyacınız vardır. Sunucu tarafı işleme yapmadıysanız, üretim derlemesi için bir düğüm ortamına bile gerek kalmaz. Statik kaynaklar neden statik bir NGINX kapsayıcısına yollanmıyor?

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

Burada, `node:12` derlemeyi gerçekleştirmek için bir görüntü kullanıyorsunuz (katman önbelleğini en üst düzeye çıkarır) ve sonra çıktıyı NGINX kapsayıcısına kopyalarsınız. Serin, kuh?

## <a name="recap"></a>Özet

Görüntülerin nasıl yapılandırıldığı hakkında biraz anlamak için, görüntüleri daha hızlı oluşturup daha az değişiklik gönderebilirsiniz. Çok aşamalı derlemeler Ayrıca, çalışma zamanı bağımlılıklarından yapı süresi bağımlılıklarını ayırarak, genel görüntü boyutunu azaltmaya ve son kapsayıcı güvenliğini artırmaya yardımcı olur.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Buluta dağıtma](deploy-to-cloud.md)