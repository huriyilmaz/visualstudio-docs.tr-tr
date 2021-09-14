---
title: 'Docker öğreticisi - Bölüm 8: Docker Compose'
description: Uygulama yükleme ve kullanma Docker Compose.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 1609081f364a2a20f983f8d8acd55181a71de42f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633433"
---
# <a name="use-docker-compose"></a>Docker Compose kullanma

[Docker Compose,](https://docs.docker.com/compose/) çok kapsayıcılı uygulamaları tanımlamaya ve paylaşmaya yardımcı olmak için geliştirilmiş bir araçtır. Compose ile, hizmetleri tanımlamak için bir YAML dosyası oluşturabilir ve tek bir komutla her şeyi döndürebilirsiniz veya her şeyi parçalara ayırabilirsiniz.

Compose kullanmanın en büyük avantajı, uygulama yığınınızı bir dosyada tanımlayarak projenizin kökünde tutmanız (artık sürüm denetimli) ve başka birinin projenize katkıda bulunarak kolayca faydalanmanızı sağlamaktır.  Birinin yalnızca sizin repo'larınızı kopyalaması ve oluşturma uygulamasını başlatması gerekir. Aslında, GitHub/GitLab'de tam olarak bunu yaparken çok sayıda proje olduğunu görüyor olabilirsiniz.

Peki, nasıl çalışmaya başladın?

## <a name="install-docker-compose"></a>Yükleme Docker Compose

Docker Desktop'ı Windows veya Mac için yüklemişsinizdir, zaten Docker Compose! Play-with-Docker örneklerinin Docker Compose zaten yüklü. Linux makinesi kullanıyorsanız, buradaki yönergeleri kullanarak Docker Compose yüklemeniz [gerekir.](https://docs.docker.com/compose/install/)

Yüklemeden sonra, aşağıdakini çalıştırarak sürüm bilgilerini görmelisiniz.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Oluşturma dosyasını oluşturma

1. Uygulama projesinin kökünde adlı bir dosya `docker-compose.yml` oluşturun.

1. Oluşturma dosyasında şema sürümünü tanımlayarak başlayacağız. Çoğu durumda desteklenen en son sürümü kullanmak en iyisidir. Geçerli şema sürümleri [ve uyumluluk matrisi için](https://docs.docker.com/compose/compose-file/) Oluştur dosya başvurusuna bakabilirsiniz.

    ```yaml
    version: "3.7"
    ```

1. Ardından, uygulamanın bir parçası olarak çalıştırmak istediğiniz hizmetlerin (veya kapsayıcıların) listesini tanımlayın.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Şimdi de hizmeti aynı anda compose dosyasına iletirsiniz.

## <a name="define-the-app-service"></a>Define the App Service

Unutmayın; bu, uygulama kapsayıcınızı tanımlamak için kullanılan komutdu (uygulama ` \ ` kapsayıcısı içinde `` ` `` ile Windows PowerShell).

```bash
docker run -dp 3000:3000 \
  -w /app -v ${PWD}:/app \
  --network todo-app \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=secret \
  -e MYSQL_DB=todos \
  node:12-alpine \
  sh -c "yarn install && yarn run dev"
```

1. İlk olarak, kapsayıcı için hizmet girişini ve görüntüsünü tanımlayın. Hizmet için istediğiniz adı seçesiniz. Ad otomatik olarak bir ağ diğer adı haline gelecek ve MySQL hizmetini tanımlarken yararlı olacaktır.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Sıralamaya gerek yoktur ancak komutu genellikle `image` tanımın yakınındadır. Bu nedenle bunu dosyaya taşımaya devam edin.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Hizmet `-p 3000:3000` için tanımlayarak komutunun `ports` bölümünü geçirme. Burada kısa söz [dizimi](https://docs.docker.com/compose/compose-file/#short-syntax-1) kullanasınız, ancak daha ayrıntılı bir uzun söz [dizimi de](https://docs.docker.com/compose/compose-file/#long-syntax-1) mevcuttur.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Ardından, ve tanımlarını kullanarak hem çalışma dizinini ( ) hem de `-w /app` birim eşlemesini ( ) `-v ${PWD}:/app` `working_dir` `volumes` geçirebilirsiniz. Birimler de kısa ve [uzun söz](https://docs.docker.com/compose/compose-file/#short-syntax-3) [dizimleri](https://docs.docker.com/compose/compose-file/#long-syntax-3) içerir.

   Birim tanımlarının Docker Compose bir avantajı, geçerli dizinden göreli yolları kullanabileceğinizdir.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Son olarak, anahtarını kullanarak ortam değişkeni tanımlarını `environment` geçirin.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>MySQL hizmetini tanımlama

Şimdi MySQL hizmetini tanımlama zamanı geldi. Bu kapsayıcı için kullanılan komut şu şekildedir (karakterleri ` \ ` aşağıdakiyle değiştirin Windows PowerShell: `` ` ``

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. İlk olarak, yeni hizmeti tanımlayın ve ağ `mysql` diğer adını otomatik olarak alır. Kullanmak istediğiniz görüntüyü de belirtin.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Ardından birim eşlemesini tanımlayın. Kapsayıcıyı ile birlikte `docker run` 2. Ancak Bu durum Compose ile çalıştırılırken olmaz. Birimi üst düzey bölümde tanımlamanız ve ardından hizmet `volumes:` yapılandırmasında bağlama noktası belirtmeniz gerekir. Yalnızca birim adını sağlayarak varsayılan seçenekler kullanılır. Ancak birçok [seçenek daha](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element) vardır.

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Son olarak, yalnızca ortam değişkenlerini belirtmeniz gerekir.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

Bu noktada, tam `docker-compose.yml` şu şekilde olması gerekir:

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Uygulama yığınını çalıştırma

Artık dosyayı sahip `docker-compose.yml` olduğunuza göre başlatabilirsiniz!

1. İlk olarak, uygulamanın ve veritabanının başka bir kopyasının ( ve ) çalıştırılamay olduğundan emin `docker ps` `docker rm -f <ids>` olun.

1. komutunu kullanarak uygulama yığınını `docker-compose up` başlatma. Arka planda `-d` her şeyi çalıştırmak için bayrağını ekleyin. Alternatif olarak, Oluştur dosyanıza sağ tıklayabilirsiniz ve  kenar çubuğu için Oluştur VS Code seçeneğini belirleyin. 

    ```bash
    docker-compose up -d
    ```

    Bunu çalıştıracak olurken aşağıdaki gibi bir çıkış görüyor oluruz:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Birimin ve bir ağın da oluşturulmuş olduğunu fark vardır! Varsayılan olarak, Docker Compose uygulama yığını için özel olarak bir ağ oluşturur (bu nedenle oluşturma dosyasında bir ağ tanımlamadınız).

1. komutunu kullanarak günlüklere `docker-compose logs -f` bakın. Hizmetlerin her biri günlüklerinin tek bir akışa alınarak yenilerini göreceğiz. Bu, zamanlamayla ilgili sorunları izlemek istediğinizde son derece kullanışlıdır. bayrağı `-f` günlüğü "izler" ve bu nedenle oluşturulan canlı çıkışı sağlar.

    Henüz görmüyorsanız aşağıdakine benzer bir çıkışla karşı karşıdan gelirsiniz:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    İletileri ayırt etmeye yardımcı olmak için hizmet adı satırın başında (genellikle renkli) görüntülenir. Belirli bir hizmetin günlüklerini görüntülemek için hizmet adını logs komutunun sonuna ekleyebilirsiniz (örneğin, `docker-compose logs -f app` ).

    > [!TIP]
    > **Uygulamayı başlatmadan önce db'nin beklemesi** Uygulama çalışırken, uygulamaya bağlanmaya çalışmadan önce mySQL'in hazır ve hazır olması için beklemesi gerekir. Docker, başka bir kapsayıcıyı başlatmadan önce başka bir kapsayıcının tamamen açık, çalışıyor ve hazır durumda olacağını beklemek için yerleşik desteke sahip değil. Düğüm tabanlı projeler için bekleme bağlantı [noktası bağımlılığını kullanabilirsiniz.](https://github.com/dwmkerr/wait-port) Diğer diller/çerçeveler için de benzer projeler mevcuttur.

1. Bu noktada, uygulamanızı açıp çalışıyor olarak görüyor olmak gerekir. Ve hey! Tek bir komuta geçtin!

## <a name="see-the-app-stack-in-the-docker-extension"></a>Docker uzantısında uygulama yığınına bakın

Docker uzantısına bakarsanız , 'dişli' ve 'gruplama by' kullanarak gruplama seçeneklerini değiştirebilirsiniz. Bu örnekte Kapsayıcıları Oluştur'a göre gruplandı ve şu Project görüyorsunuz:

![Compose ile VS Uzantısı](media/vs-app-project-collapsed.png)

Ağın aşağı doğru ilerlerken, oluşturma dosyasında tanımlandığı iki kapsayıcıyı görüyorsunuz.

![Compose genişletilmiş VS Uzantısı](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Hepsini parçalara ayır

Tüm dosyaları parçalara ayıracaksanız, docker uzantısının kapsayıcılar listesinde bulunan uygulamaya sağ tıklar veya `docker-compose down` VS Code **Oluştur'u seçmeniz gerekir.** Kapsayıcılar durur ve ağ kaldırılır.

> [!WARNING]
> **Birimleri Kaldırma** Varsayılan olarak, oluşturma dosyanız içinde adlandırılmış birimler çalıştırılırken `docker-compose down` KALDıRLANMAZ. Birimleri kaldırmak için bayrağını eklemeniz `--volumes` gerekir.

Devreden sonra başka bir projeye geçiş yapmak, çalıştırmak `docker-compose up` ve bu projeye katkıda bulunmak için hazır olmak! Aslında bundan çok daha basit bir şey değil!

## <a name="recap"></a>Özet

Bu bölümde, çok hizmetli Docker Compose tanımlamayı ve paylaşmayı önemli ölçüde basitleştirmeye nasıl yardımcı olduğu hakkında bilgi edindi. Kullanmakta olduğunu komutları uygun compose biçimine dönüştürerek bir Compose dosyası oluştursunuz.

Bu noktada, öğreticiyi sarmamaya başlıyorsanız. Ancak, kullanmakta olduğu Dockerfile'da büyük bir sorun olduğu için görüntü binayla ilgili birkaç en iyi uygulama vardır. Şimdi bir göz at bakalım!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Görüntü en iyi yöntemleri](image-building-best-practices.md)
