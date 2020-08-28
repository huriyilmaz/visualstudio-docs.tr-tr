---
title: 'Docker öğreticisi-Bölüm 7: Docker Compose kullanma'
description: Docker Compose yüklemeyi ve kullanmayı açıklar.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 81f70612b05920ea58c752a878831f1d6de34098
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039204"
---
# <a name="use-docker-compose"></a>Docker Compose kullanma

[Docker Compose](https://docs.docker.com/compose/) , çok Kapsayıcılı uygulamaların tanımlanması ve paylaşılması için geliştirilmiş bir araçtır. Compose ile, hizmetleri tanımlamak için bir YAML dosyası oluşturabilir ve tek bir komutla, her şeyi açabilir veya parçalara ayırın.

Oluşturma kullanmanın *büyük* avantajı, uygulama yığınınızı bir dosya içinde tanımlayabilir, bunu proje deponuzu kökünde tutabilir (artık sürümdedir) ve başka birinin projenize katkıda bulunmasını kolayca sağlayabilirsiniz. Birisinin yalnızca depoyu kopyalaması ve oluşturma uygulamasını başlatması gerekir. Aslında GitHub/GitLab üzerinde tam olarak bunu yaparken çok sayıda proje görebilirsiniz.

Bu nedenle nasıl başladıysanız?

## <a name="install-docker-compose"></a>Docker Compose yüklensin

Windows veya Mac için Docker Desktop yüklediyseniz, zaten Docker Compose! WITH Docker örneklerinin de Docker Compose zaten yüklü. Bir Linux makineniz varsa, [buradaki yönergeleri](https://docs.docker.com/compose/install/)kullanarak Docker Compose yüklemeniz gerekecektir.

Yükleme sonrasında, aşağıdakileri çalıştırıp sürüm bilgilerini görebilirsiniz.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Oluşturma dosyası oluşturma

1. Uygulama projesinin kökünde adlı bir dosya oluşturun `docker-compose.yml` .

1. Oluşturma dosyasında, şema sürümünü tanımlayarak başlayacağız. Çoğu durumda, en son desteklenen sürümü kullanmak en iyisidir. Geçerli şema sürümleri ve uyumluluk matrisi için [oluşturma dosyası başvurusuna](https://docs.docker.com/compose/compose-file/) bakabilirsiniz.

    ```yaml
    version: "3.7"
    ```

1. Ardından, uygulamanızın bir parçası olarak çalıştırmak istediğiniz hizmetlerin (veya kapsayıcıların) listesini tanımlayın.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Şimdi de bir hizmeti bir seferde oluşturma dosyasına geçirmeye başlayacaksınız.

## <a name="define-the-app-service"></a>App Service tanımlayın

Bunu anımsamak için, uygulama kapsayıcınızı tanımlamak için kullandığınız komuttur ( ` \ ` karakterleri `` ` `` Windows PowerShell 'de değiştirin).

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

1. İlk olarak, hizmet girdisini ve kapsayıcının görüntüsünü tanımlayın. Hizmet için herhangi bir ad seçebilirsiniz. Ad, MySQL hizmeti tanımlanırken yararlı olacak şekilde otomatik olarak bir ağ diğer adı olacak.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Genellikle, sıralamada bir gereksinim olmasa da, tanımınıza yakın komutu görürsünüz `image` . Bu nedenle, devam edin ve dosyaya taşıyın.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. `-p 3000:3000`Hizmeti için öğesini tanımlayarak komutun bölümünü geçirin `ports` . Burada [kısa söz dizimini](https://docs.docker.com/compose/compose-file/#short-syntax-1) kullanacaksınız, ancak daha ayrıntılı bir [uzun sözdizimi](https://docs.docker.com/compose/compose-file/#long-syntax-1) de mevcuttur.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Ardından, ve tanımlarını kullanarak hem çalışma dizinini () hem de `-w /app` birim eşlemesini ( `-v ${PWD}:/app` ) geçirin `working_dir` `volumes` . Birimlerde ayrıca [kısa](https://docs.docker.com/compose/compose-file/#short-syntax-3) ve [uzun](https://docs.docker.com/compose/compose-file/#long-syntax-3) bir sözdizimi vardır.

   Docker Compose birim tanımlarının bir avantajı, geçerli dizinden göreli yollar kullanabilirsiniz.

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

1. Son olarak, anahtarı kullanarak ortam değişkeni tanımlarını geçirin `environment` .

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

Şimdi MySQL hizmetini tanımlamanız zaman. Bu kapsayıcı için kullandığınız komut aşağıda verilmiştir ( ` \ ` karakterleri `` ` `` Windows PowerShell 'de değiştirin):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. İlk olarak, yeni hizmeti tanımlayın ve `mysql` ağ diğer adını otomatik olarak alır. Kullanılacak görüntüyü de belirtin.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Ardından, birim eşlemesini tanımlayın. Kapsayıcıyı ile çalıştırdığınızda `docker run` , adlandırılmış birim otomatik olarak oluşturulmuştur. Ancak, Compose ile çalışırken gerçekleşmez. Üst düzey bölümünde birimi tanımlamanız `volumes:` ve ardından hizmet yapılandırmasında bağlama noktasını belirtmeniz gerekir. Yalnızca birim adını sağlayarak varsayılan seçenekler kullanılır. [Birden çok daha fazla seçenek](https://docs.docker.com/compose/compose-file/#volume-configuration-reference) mevcuttur.

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

1. Son olarak, yalnızca ortam değişkenlerini belirtmeniz yeterlidir.

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

Bu noktada, tamamlanma `docker-compose.yml` şöyle görünmelidir:

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

Artık dosyaya sahip olduğunuza göre `docker-compose.yml` başlayabilirsiniz!

1. İlk olarak, uygulamanın ve veritabanının başka bir kopyasının (ve) çalıştığından emin olun `docker ps` `docker rm -f <ids>` .

1. Komutunu kullanarak uygulama yığınını başlatın `docker-compose up` . `-d`Arka planda her şeyi çalıştırmak için bayrak ekleyin. Alternatif olarak, oluştur dosyanıza sağ tıklayıp VS Code yan çubuk için **Oluştur** seçeneğini belirleyebilirsiniz. 

    ```bash
    docker-compose up -d
    ```

    Bunu çalıştırdığınızda aşağıdakine benzer bir çıktı görmeniz gerekir:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Birimin oluşturulduğunu ve bir ağ olduğunu fark edeceksiniz! Varsayılan olarak, Docker Compose otomatik olarak uygulama yığını için bir ağ oluşturur (Bu nedenle, oluşturma dosyasında bir tane tanımlamadığınız anlamına gelir).

1. Komutunu kullanarak günlüklere bakın `docker-compose logs -f` . Her bir hizmet için günlük kayıtları tek bir akışta görürsünüz. Bu, zamanlamaya göre ilgili sorunları izlemek istediğinizde inanılmaz yararlıdır. `-f`"Bu" bayrak, günlüğün oluşturulduğu gibi canlı çıktılar sağlayacak.

    Henüz yapmadıysanız aşağıdakine benzer bir çıktı görürsünüz:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Hizmet adı, iletileri ayırt etmenize yardımcı olmak için satırın başlangıcında görüntülenir (genellikle renkli). Belirli bir hizmet için günlükleri görüntülemek istiyorsanız, hizmet adını Günlükler komutunun sonuna (örneğin, `docker-compose logs -f app` ) ekleyebilirsiniz.

    > [!TIP]
    > **Uygulamayı başlatmadan önce DB bekleniyor** Uygulama başlatıldığında, gerçekten bir bağlantı kurmaya çalışmadan önce MySQL 'in hazır ve hazır olmasını bekler it.Docker, başka bir kapsayıcının başlatılmasına, çalışmaya ve başka bir kapsayıcıya başlamadan önce herhangi bir yerleşik destek vermez. Düğüm tabanlı projelerde [bekleme-bağlantı noktası](https://github.com/dwmkerr/wait-port) bağımlılığını kullanabilirsiniz. Diğer diller/çerçeveler için benzer projeler de mevcuttur.

1. Bu noktada, uygulamanızı açabiliyor ve çalıştığını görmeniz gerekir. Ve Hey! Tek bir komuta hazırsınız!

## <a name="see-the-app-stack-in-the-docker-extension"></a>Docker uzantısında uygulama yığınına bakın

Docker uzantısına bakarsanız, ' COG ' ve ' Group by ' kullanarak gruplandırma seçeneklerini değiştirebilirsiniz. Bu örnekte, oluşturma projesi adına göre gruplanmış kapsayıcıları görmek istersiniz:

![Oluşturma ile VS uzantısı](media/vs-app-project-collapsed.png)

Ağı görmüyorsanız, oluşturma dosyasında tanımladığınız iki kapsayıcıyı görürsünüz.

![Genişletilmiş oluşturma ile VS uzantısı](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Tümünü koparın

Tamamen ayrılmaya hazırsanız, `docker-compose down` vs Code Docker uzantısı 'ndaki kapsayıcılar listesinden uygulamayı çalıştırın veya sağ tıklayın ve **Oluştur**' u seçin. Kapsayıcılar durdurulur ve ağ kaldırılır.

> [!WARNING]
> **Birimleri kaldırma** Varsayılan olarak, oluşturma dosyanızdaki adlandırılmış birimler çalışırken kaldırılmaz `docker-compose down` . Birimleri kaldırmak istiyorsanız bayrağını eklemeniz gerekir `--volumes` .

Yırtık olduktan sonra, başka bir projeye geçiş yapabilir, çalıştırabilir `docker-compose up` ve bu projeye katkıda bulunmak için hazırsanız! Gerçekten çok daha basit almaz!

## <a name="recap"></a>Özet

Bu bölümde Docker Compose ve çok hizmet uygulamalarının tanımlanmasını ve paylaşılmasını önemli ölçüde basitleştirmeye nasıl yardımcı olduğunu öğrendiniz. Kullanmakta olduğunuz komutları uygun oluşturma biçiminde çevirerek bir oluşturma dosyası oluşturdunuz.

Bu noktada öğreticiyi kaydırmaya başlıyoruz. Bununla birlikte, kullanmakta olduğunuz Dockerfile ile ilgili büyük bir sorun olduğu için görüntü oluşturma hakkında en iyi uygulamalar vardır. Bu nedenle, bir göz atalım!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Görüntü-en iyi uygulamalar oluşturma](image-building-best-practices.md)
