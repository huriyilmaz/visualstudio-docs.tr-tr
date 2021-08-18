---
title: 'Docker öğreticisi - Bölüm 7: Çok kapsayıcılı uygulamalar'
description: Kapsayıcılar arasında ağ oluşturma ve MySQL veritabanı için kapsayıcı ekleme.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: a006435b6513d3cecf87f61c576dd253e3a68ef6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045521"
---
# <a name="multi-container-apps"></a>Birden çok kapsayıcılı uygulamalar

Bu noktaya kadar tek kapsayıcılı uygulamalarla çalışıyordunız. Ancak şimdi uygulama yığınına MySQL eksersiniz. Aşağıdaki soru genellikle "MySQL nerede çalıştıracak? Aynı kapsayıcıya mı yükleyeceğiz yoksa ayrı mı çalıştırabilirsiniz?" Genel olarak, **her kapsayıcı tek bir şey yapar ve bunu iyi yapar.** Birkaç neden:

- API'leri ve ön uçları veritabanlarından farklı ölçeklendirmek zorunda olma ihtimali yüksek
- Ayrı kapsayıcılar sürümü ve güncelleştirme sürümlerini yalıtımlı olarak sağlar
- Veritabanı için yerel olarak bir kapsayıcı kullanabilirsiniz ancak üretimde veritabanı için yönetilen bir hizmet kullanmak da iyi olabilir. Bu şekilde veritabanı altyapınızı uygulamanıza gönderebilirsiniz.
- Birden çok işlem çalıştırılacaksa bir işlem yöneticisi gerekir (kapsayıcı yalnızca bir işlem başlatır), bu da kapsayıcı başlatma/kapatma işlemlerine karmaşıklık getirir.

Ayrıca bunun başka nedenleri de vardır. Bu nedenle, uygulamayı şu şekilde çalışacak şekilde güncelleştirebilirsiniz:

![MySQL kapsayıcıya bağlı Todo Uygulaması](media/multi-app-architecture.png)

## <a name="container-networking"></a>Kapsayıcı ağ iletişimi

Kapsayıcıların varsayılan olarak yalıtımlı bir şekilde çalıştırı ve aynı makinede bulunan diğer işlemler veya kapsayıcılar hakkında hiçbir şey bilmiyor olduğunu unutmayın. Peki, bir kapsayıcının başka bir kapsayıcıyla konuşmasına nasıl izin ve ardından? Yanıt ağ **iletişimidir.** Artık ağ mühendisi (ray!) olmak zorunda değilsiniz. Bu kuralı unutmayın...

> [!NOTE]
> İki kapsayıcı aynı ağ üzerinde ise, iletişimde olabilir. Böyle bir şey yoksa, bunu geri alazlar.

## <a name="start-mysql"></a>MySQL'i başlatma

Bir kapsayıcıyı ağa koymanın iki yolu vardır: en başında ata veya var olan bir kapsayıcıyı bağla. Şimdilik önce ağı oluşturacak ve başlangıçta MySQL kapsayıcısı ekleyebilirsiniz.

1. Ağı oluşturun.

    ```bash
    docker network create todo-app
    ```

1. MySQL kapsayıcısı başlatma ve ağ ekleme. Ayrıca veritabanını başlatmak için veritabanının [(MySQL](https://hub.docker.com/_/mysql/)Docker Hub listesinin "Ortam Değişkenleri" bölümüne bakın) birkaç ortam değişkeni tanımlayacağız (karakterlerini ` \ ` `` ` `` Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Bayrağını belirttiğinizi de `--network-alias` göreceğiz. Birazdan bu şekilde devam etmek istiyorum.

    > [!TIP]
    > Burada bir birim adı kullanmakta ve bu adı MySQL'in verilerini depo bulunduğu yere `todo-mysql-data` `/var/lib/mysql` bağlamayı fark vardır. Ancak, hiçbir zaman bir komutta hiç komutunuz `docker volume create` olmadı. Docker adlandırılmış bir birim kullanmak istediğinizi tanır ve sizin için otomatik olarak bir birim oluşturur.

1. Veritabanının çalıştığını onaylamak için veritabanına bağlanarak veritabanının çalıştığını doğrulayın.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Parola istemi geldiğinde gizli **yazın.** MySQL kabuğunda veritabanlarını listelenin ve veritabanını gördüğünüzden emin `todos` olun.

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

    Yaşasın! Veritabanınız `todos` hazır ve kullanıma hazır!

## <a name="connect-to-mysql"></a>Bağlan MySQL'e

Artık MySQL'in çalışıyor olduğunu biliyorsunuz. Şimdi bunu kullanabiliriz! Ancak soru şu: Nasıl? Aynı ağ üzerinde başka bir kapsayıcı çalıştırsanız kapsayıcıyı nasıl bulursunuz (her kapsayıcının kendi IP adresi olduğunu unutmayın)?

Bunu çözmek için, ağ sorunlarını gidermek veya hata ayıklamak için yararlı olan birçok  araçla birlikte bir çok araçla birlikte gelir ve bu kapsayıcıyı [kullanılaka/netshoot](https://github.com/nicolaka/netshoot) kapsayıcısını kullanabilirsiniz.

1. Görüntüyü kullanarak yeni bir kapsayıcı `nicolaka/netshoot` başlatma. Bunu aynı ağa bağdan emin olun.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Kapsayıcının içinde, kullanışlı `dig` bir DNS aracı olan komutunu kullanın. ana bilgisayar adı için IP adresine `mysql` bakın.

    ```bash
    dig mysql
    ```

    Bunun gibi bir çıkışla da ...

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

    "CEVAPLA BÖLÜMÜNDE" olarak çözümlene bir kayıt (IP adresinizin büyük olasılıkla `A` `mysql` farklı bir değeri `172.23.0.2` olur) olduğunu görüyorsunuz. Normalde geçerli bir ana bilgisayar adı olmayabilir ancak Docker bu sorunu ağ diğer adı olan kapsayıcının IP adresine çözümlemiştir (daha önce kullanılan bayrağı `mysql` `--network-alias` unutmayın).)

    Bunun anlamı... Yalnızca adlı bir ana bilgisayara bağlanmanız gerekiyor `mysql` ve bu da veritabanıyla iletişim kuracak! Bundan çok daha basit olamaz!

## <a name="run-your-app-with-mysql"></a>MySQL ile uygulama çalıştırma

Todo uygulaması, MySQL bağlantı ayarlarını belirtmek için birkaç ortam değişkeninin ayarını destekler. Bunlar:

- `MYSQL_HOST` - çalışan MySQL sunucusunun ana bilgisayar adı
- `MYSQL_USER` - bağlantı için kullanmak üzere kullanıcı adı
- `MYSQL_PASSWORD` - bağlantı için kullanmak üzere parola
- `MYSQL_DB` - bağlandıktan sonra kullanmak üzere veritabanı

> [!WARNING]
> **Ortam Değişkenleri Ayarlar Bağlantı Bağlantısını Ayarlama** Bağlantı ayarlarını ayarlamak için ortam değişkenlerini kullanmak genellikle geliştirme için uygun bir durumdur ancak üretim ortamında uygulama çalıştırmanız önerilmez. Bunun neden olduğunu anlamak [için bkz. Gizli veriler için neden ortam değişkenlerini kullanmamalısınız?](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/)
> Daha güvenli bir mekanizma, kapsayıcı düzenleme çerçeveniz tarafından sağlanan gizli destek kullanmaktır. Çoğu durumda, bu gizli diziler çalışan kapsayıcıya dosya olarak monte edilir. Birçok uygulama (MySQL görüntüsü ve todo uygulaması dahil) ayrıca dosyayı içeren bir dosyaya işaret etmek için son eke sahip env vars'ı `_FILE` da destekler.
> Örneğin, var ayarı uygulamanın bağlantı parolası olarak başvurulan `MYSQL_PASSWORD_FILE` dosyanın içeriğini kullanmana neden olur. Docker, bu env değişkenlerini desteklemek için hiçbir şey yapmaz. Uygulamanıza değişkenin bakarak dosya içeriğinin nasıl elde olduğunu bilmek gerekir.

Tüm bu açıklamalarla, geliştirme için hazır kapsayıcınızı başlatabilirsiniz!

1. Yukarıdaki ortam değişkenlerini belirtin ve kapsayıcıyı uygulama ağınıza ` \ ` `` ` `` Windows PowerShell.

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

1. Kapsayıcının günlüklerine () `docker logs <container-id>` bakarsanız, MySQL veritabanını kullanmakta olduğunu belirten bir ileti görüyorsanız.

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

1. Uygulamayı tarayıcınızda açın ve todo listenize birkaç öğe ekleyin.

1. Bağlan MySQL veritabanına geri alır ve öğelerin veritabanına yazıldığı kanıtlayabilir. Parolanın gizli olduğunu **unutmayın.**

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    MySQL kabuğunda aşağıdakini çalıştırın:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Açıkça görülüyor ki tablo, öğeleriniz olduğundan farklı görünüyor. Ancak burada depolanmış olduğunu görüyoruz!

Docker uzantısına hızlı bir şekilde göz atarak iki uygulama kapsayıcısı çalıştırabilirsiniz. Ancak, bunların tek bir uygulamada birlikte gruplandıklarının gerçek bir göstergesi yoktur. Kısa süre içinde bunu nasıl daha iyi halelay diye bakacağız!

![İki gruplanmamış uygulama kapsayıcısını gösteren Docker Uzantısı](media/vs-multi-container-app.png)

## <a name="recap"></a>Özet

Bu noktada, artık verilerini ayrı bir kapsayıcıda çalışan bir dış veritabanında depolar. Kapsayıcı ağı hakkında biraz bilgi edindi ve DNS kullanılarak hizmet bulmanın nasıl gerçekleştirileileceğini öğrendin.

Ancak, bu uygulamayı başlatmak için ihtiyacınız olan her şeye biraz bunalmış gibi hissetmeye başlama ihtimaline sahipsiniz. Bir ağ oluşturmanız, kapsayıcıları başlatmanız, tüm ortam değişkenlerini belirtmeniz, bağlantı noktalarını açığa çıkarmanız ve daha fazlası gerekir! Anımsanacak çok şey vardır ve bu da kesinlikle işleri başka birine iletken daha zor hale geliyor.

Sonraki bölümde bu konu hakkında Docker Compose. Bu Docker Compose, uygulama yığınlarınızı çok daha kolay bir şekilde paylaşabilir ve başkalarının tek (ve basit) bir komutla bunları döndürmesine izin veebilirsiniz!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Using Docker Compose](use-docker-compose.md)
