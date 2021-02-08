---
title: 'Docker öğreticisi-Bölüm 6: çok Kapsayıcılı uygulamalar'
description: Kapsayıcılar arasında ağ ayarlama ve MySQL veritabanı için kapsayıcı ekleme.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 0c8c9fb4072da071ba06d5dc371e85db8291353a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841789"
---
# <a name="multi-container-apps"></a>Birden çok kapsayıcılı uygulamalar

Bu noktaya kadar, tek Kapsayıcılı uygulamalarla çalıştık. Ancak artık uygulama yığınına MySQL ekleyeceksiniz. Aşağıdaki soru genellikle "MySQL 'in çalıştırılacağı yerdir. Aynı kapsayıcıya yüklensin mi veya ayrı olarak çalıştırın mi? " Genel olarak, **her kapsayıcının tek bir şey yapması ve iyi hale gelmelidir.** Birkaç neden:

- API 'Leri ve ön uçları veritabanlarından farklı ölçeklendirmeniz iyi bir şansınız vardır
- Ayrı kapsayıcılar, sürüm ve güncelleştirme sürümlerini yalıtımına sağlar
- Veritabanına yerel olarak bir kapsayıcı kullanabilir, ancak üretimde veritabanı için yönetilen bir hizmet kullanmak isteyebilirsiniz. Veritabanı altyapısını uygulamanız ile birlikte göndermek istemezsiniz.
- Birden çok işlemi çalıştırmak için bir işlem yöneticisi gerekir (kapsayıcı yalnızca bir işlem başlatır), bu da kapsayıcı başlatması/kapatması için karmaşıklık ekler.

Ve başka nedenler de vardır. Bu nedenle, uygulamanızı şöyle çalışacak şekilde güncelleşyirsiniz:

![MySQL kapsayıcısına bağlı ToDo uygulaması](media/multi-app-architecture.png)

## <a name="container-networking"></a>Kapsayıcı ağ iletişimi

Varsayılan olarak, kapsayıcıların yalıtımda çalıştırılacağını ve aynı makinedeki diğer süreçler veya kapsayıcılar hakkında hiçbir şey olmadığını unutmayın. Bu nedenle, bir kapsayıcının birbirleriyle nasıl iletişim kurmasına nasıl izin verirsiniz? Yanıt **ağ**. Şimdi bir ağ mühendisi (Hooray!) olmanız gerekmez. Bu kuralı unutmayın...

> [!NOTE]
> Aynı ağ üzerinde iki kapsayıcı varsa, birbirleriyle iletişim kurabilir. Aksi takdirde, bunlar olamaz.

## <a name="start-mysql"></a>MySQL 'i Başlat

Bir ağ üzerinde kapsayıcı yerleştirmek için iki yol vardır: başlangıçta atayın veya var olan bir kapsayıcıyı bağlayın. Şimdilik, önce ağı oluşturacak ve MySQL kapsayıcısını başlangıçta iliştirecaksınız.

1. Ağı oluşturun.

    ```bash
    docker network create todo-app
    ```

1. Bir MySQL kapsayıcısı başlatın ve ağı bağlayın. Ayrıca, veritabanının veritabanını başlatmak için kullanacağı bazı ortam değişkenlerini tanımlayacağız ( [MySQL Docker Hub listesinin](https://hub.docker.com/_/mysql/)"ortam değişkenleri" bölümüne bakın) ( ` \ ` karakterleri `` ` `` Windows PowerShell 'de ile değiştirin).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Ayrıca, bayrağını belirttireceksiniz `--network-alias` . Yalnızca bir süre içinde bu duruma geri döneceğiz.

    > [!TIP]
    > Burada bir birim adı kullandığınızı `todo-mysql-data` ve burada `/var/lib/mysql` MySQL 'in verilerini depoladığı yerde olduğunu fark edeceksiniz. Ancak, hiçbir şekilde bir komut çalıştırmayın `docker volume create` . Docker, adlandırılmış bir birimi kullanmak istediğinizi algılar ve sizin için otomatik olarak bir tane oluşturur.

1. Veritabanının çalışır duruma sahip olduğunuzu doğrulamak için veritabanına bağlanın ve bağlandığını doğrulayın.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Parola istemi geldiğinde **gizli** yazın. MySQL kabuğu 'nda veritabanlarını listeleyin ve veritabanını gördiğinizi doğrulayın `todos` .

    ```cli
    mysql> SHOW DATABASES;
    ```

    Şuna benzer bir çıkış görmelisiniz:

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    Yaşasın! `todos`Veritabanınız var ve kullanıma hazırlanıyor!

## <a name="connect-to-mysql"></a>MySQL 'e Bağlan

Şimdi MySQL 'in çalışır durumda olduğunu öğrenmiş olduğunuza göre şunu kullanalım! Ancak, bu soru... oluşturulacağı? Aynı ağ üzerinde başka bir kapsayıcı çalıştırırsanız, kapsayıcıyı nasıl bulursunuz (her kapsayıcının kendi IP adresi olduğunu unutmayın)?

Bunu yapmak için, sorun giderme veya ağ sorunlarını ayıklama için yararlı olan *çok* sayıda araç ile birlikte gelen [nicolaka/netmake](https://github.com/nicolaka/netshoot) kapsayıcısını kullanacaksınız.

1. Görüntüyü kullanarak yeni bir kapsayıcı başlatın `nicolaka/netshoot` . Aynı ağa bağlandığınızdan emin olun.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Kapsayıcının içinde, `dig` yararlı BIR DNS aracı olan komutunu kullanın. Ana bilgisayar adının IP adresini arayın `mysql` .

    ```bash
    dig mysql
    ```

    Bu, şöyle bir çıkış alacaksınız...

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    "Yanıt bölümünde" `A` olarak çözümlenen bir kayıt görürsünüz `mysql` `172.23.0.2` (IP adresiniz muhtemelen farklı bir değere sahip olacaktır). `mysql`Normalde geçerli bir ana bilgisayar adı değil, Docker bu ağ diğer adına sahip olan KAPSAYıCıNıN IP adresine çözümlenemiyor ( `--network-alias` daha önce kullandığınız bayrağı hatırlayın).

    Bunun anlamı... Uygulamanız yalnızca adlı bir konağa bağlanmalıdır `mysql` ve veritabanıyla iletişim kurabilir! Bundan çok daha basit almaz!

## <a name="run-your-app-with-mysql"></a>Uygulamanızı MySQL ile çalıştırma

ToDo uygulaması, MySQL bağlantı ayarlarını belirtmek için birkaç ortam değişkeni ayarını destekler. Bunlar:

- `MYSQL_HOST` -çalışan MySQL sunucusu için ana bilgisayar adı
- `MYSQL_USER` -bağlantı için kullanılacak Kullanıcı adı
- `MYSQL_PASSWORD` -bağlantı için kullanılacak parola
- `MYSQL_DB` -bağlandıktan sonra kullanılacak veritabanı

> [!WARNING]
> **Ortam değişkenleri aracılığıyla bağlantı ayarlarını ayarlama** Bağlantı ayarlarını yapmak için ortam değişkenlerini kullanmak genellikle geliştirme için uygun olsa da, üretimde uygulamalar çalıştırılırken kesinlikle önerilmez. Nedenini anlamak için [neden gizli veriler için ortam değişkenlerini kullanmamalısınız](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/)? bölümüne bakın.
> Daha güvenli bir mekanizma, kapsayıcı düzenleme çatısı tarafından sunulan gizli dizi desteğini kullanmaktır. Çoğu durumda, bu gizlilikler çalışan kapsayıcıya dosya olarak bağlanır. Birçok uygulama görürsünüz (MySQL görüntüsü ve ToDo uygulaması dahil) `_FILE` , dosyayı içeren bir dosyayı işaret etmek için bir sonek ile env VARS 'i de destekliyoruz.
> Örnek olarak, `MYSQL_PASSWORD_FILE` var ayarı uygulamanın başvurulan dosyanın içeriğini bağlantı parolası olarak kullanmasına neden olur. Docker, bu env VARS 'i desteklemek için hiçbir şey yapmaz. Uygulamanızın değişkeni araması ve dosya içeriğini alması için bilmeleri gerekir.

Açıklanacak şekilde, dev-Ready kapsayıcınızı başlatın!

1. Yukarıdaki ortam değişkenlerinin her birini belirtin ve kapsayıcıyı uygulama ağınıza bağlayın ( ` \ ` karakterleri `` ` `` Windows PowerShell 'de değiştirin).

    ```bash hl_lines="3 4 5 6 7"
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

1. Kapsayıcının () günlüklerine bakarsanız `docker logs <container-id>` , MySQL veritabanını kullandığını belirten bir ileti görmeniz gerekir.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. Uygulamayı tarayıcınızda açın ve yapılacaklar listenize birkaç öğe ekleyin.

1. MySQL veritabanına bağlanın ve öğelerin veritabanına yazıldığını kanıtlayın. Parolanın **gizli** olduğunu unutmayın.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    MySQL kabuğu 'nda aşağıdakileri çalıştırın:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Kuşkusuz, tablonuz, öğeleriniz içerdiğinden farklı görünecektir. Ancak, burada depolanan öğeleri görmeniz gerekir!

Docker uzantısına hızlı bir bakış yaparsanız, çalışan iki uygulama Kapsayıcınız olduğunu görürsünüz. Ancak, tek bir uygulamada birlikte gruplandırıldığının gerçek bir göstergesi yoktur. Daha kısa bir süre sonra nasıl yapılacağını göreceksiniz!

![İki Gruplandırılmamış uygulama kapsayıcısı gösteren Docker uzantısı](media/vs-multi-container-app.png)

## <a name="recap"></a>Özet

Bu noktada, artık verilerini ayrı bir kapsayıcıda çalışan bir dış veritabanında depolayan bir uygulamanız vardır. Kapsayıcı ağı hakkında biraz bilgi edindiniz ve hizmet bulmanın DNS kullanarak nasıl gerçekleştirilebileceğini gördünüz.

Ancak, bu uygulamayı başlatmak için ihtiyacınız olan her şeye göre biraz daha az bir fikir sunmaktan en iyi şansınız vardır. Bir ağ oluşturmanız, kapsayıcıları başlatmanız, tüm ortam değişkenlerini belirtmeniz, bağlantı noktalarını açığa çıkarmak ve daha birçok şey yapmanız gerekir! Bu çok büyük bir şeydir ve başka bir kişiye daha zor bir şekilde geçiş yapmayı zorlaştırır.

Sonraki bölümde Docker Compose hakkında konuşacağız. Docker Compose, uygulama yığınlarınızı çok daha kolay bir şekilde paylaşabilir ve başkalarının bunları tek bir (ve basit) komutla dönmesini sağlayabilirsiniz!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Docker Compose kullanma](use-docker-compose.md)
