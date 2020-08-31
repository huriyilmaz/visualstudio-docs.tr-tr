---
title: 'Docker öğreticisi-4. Bölüm: verilerinizi kalıcı hale getirme'
description: Bir veritabanındaki verileri kalıcı hale getirme ve bir birim bağlayarak dizinleri bir kapsayıcıya paylaşma hakkında bilgi edinin.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 34b3cb9465c1efb946260917d755729e25c4e259
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89178414"
---
# <a name="persist-your-data"></a>Verilerinizi kalıcı hale getirme

Fark etmediğiniz durumlarda, kapsayıcıyı her başlattığınızda yapılacaklar listesi temizlenir. Bunun nedeni nedir? Kapsayıcının nasıl çalıştığını görelim.

## <a name="the-containers-filesystem"></a>Kapsayıcının dosya sistemi

Bir kapsayıcı çalıştırıldığında, dosya sistemi için bir görüntüden çeşitli katmanları kullanır. Her kapsayıcı Ayrıca dosya oluşturmak, güncelleştirmek veya kaldırmak için kendi "karalama alanını" alır. Aynı görüntüyü kullanıyor *olsalar bile* , herhangi bir değişiklik başka bir kapsayıcıda görülmez.

### <a name="see-this-in-practice"></a>Bu uygulamada, bkz.

Bunu eylemde görmek için iki kapsayıcıyı başlatacak ve her birinde bir dosya oluşturacaksınız. Ne göreceğiniz, bir kapsayıcıda oluşturulan dosyaların başka bir kapsayıcıda kullanılabilir olmadığı şeydir.

1. `ubuntu` `/data.txt` 1 ile 10000 arasında rastgele bir sayı ile adlı bir dosya oluşturacak bir kapsayıcı başlatın.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Komutu hakkında merak ediyorsanız, bash kabuğu başlatılıyor ve iki komut (bunun neden olduğu `&&` ) çağrılıyor. İlk bölüm tek bir rastgele sayı seçer ve bunu öğesine yazar `/data.txt` . İkinci komut, kapsayıcının çalışmasını sağlamak için yalnızca bir dosya izliyor.

1. Bunu, kapsayıcıyı almak için kullanarak çıktıyı görebileceğiniz doğrulayın `exec` . Bunu yapmak için VS Code uzantısını açın ve **kabuk Ekle** seçeneğine tıklayın. Bu `exec` , vs Code terminali içindeki kapsayıcıda bir kabuğu açmak için kullanılır.

    ![CLı 'yi Ubuntu kapsayıcısına VS Code açın](media/attach_shell.png)

    Ubuntu kapsayıcısında bir kabuğu çalıştıran bir Terminal görürsünüz. Dosyanın içeriğini görmek için aşağıdaki komutu çalıştırın `/data.txt` . Bu terminali daha sonra yeniden kapatın.

    ```bash
    cat /data.txt
    ```

    Komut satırını tercih ediyorsanız, `docker exec` komutunu kullanarak aynı şekilde gerçekleştirebilirsiniz. Kapsayıcının KIMLIĞINI ( `docker ps` almak için kullanın) almanız ve aşağıdaki komutla içeriğini almanız gerekir.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Rastgele bir sayı görmeniz gerekir!

1. Şimdi başka bir `ubuntu` kapsayıcı (aynı görüntü) başlatın ve aynı dosyaya sahip olmadığınız görürsünüz.

    ```bash
    docker run -it ubuntu ls /
    ```

    Ve göz atın! `data.txt`Orada dosya yok! Bunun nedeni, yalnızca ilk kapsayıcının karalama alanına yazılmasından kaynaklanır.

1. Devam edin ve komutu kullanarak ilk kapsayıcıyı kaldırın `docker rm -f` .

## <a name="container-volumes"></a>Kapsayıcı birimleri

Önceki deneyle her bir kapsayıcının her başlatıldığında görüntü tanımından başlayacağını gördünüz. Kapsayıcılar dosya oluşturabilir, güncelleştirebilir ve silebilir, bu değişiklikler kapsayıcı kaldırıldığında ve tüm değişiklikler o kapsayıcıya yalıtılarak kaybedilir. Birimlerle, tüm bunu değiştirebilirsiniz.

[Birimler](https://docs.docker.com/storage/volumes/) , kapsayıcının belirli dosya sistemi yollarını konak makinesine geri bağlama yeteneği sağlar. Kapsayıcıda bir dizin bağlanmışsa, bu dizindeki değişiklikler de ana makinede görülür. Aynı dizini kapsayıcının yeniden başlatmaları arasında bağlarsanız, aynı dosyaları görürsünüz.

İki ana birim türü vardır. Sonunda her ikisini de kullanacaksınız, ancak **adlandırılmış birimlerle**başlayacaksınız.

## <a name="persist-your-todo-data"></a>Todo verilerinizi kalıcı hale getirin

Varsayılan olarak, ToDo uygulaması verilerini adresinde bir [SQLite veritabanına](https://www.sqlite.org/index.html) depolar `/etc/todos/todo.db` . SQLite hakkında bilginiz yoksa, hiç kimse yok! Yalnızca tüm verilerin tek bir dosyada depolandığı ilişkisel bir veritabanıdır. Büyük ölçekli uygulamalar için en iyi yöntem olmasa da, küçük tanıtımlar için geçerlidir. Bunu daha sonra gerçek bir veritabanı altyapısına geçme hakkında konuşacağız.

Veritabanı tek bir dosya haline getirilebileceği takdirde, bu dosyayı konakta kalıcı hale getirebiliyor ve bir sonraki kapsayıcının kullanımına sunmak istiyorsanız, en son kaldığınız yeri çekebilmelidir. Bir birim oluşturup (genellikle "bağlama" olarak adlandırılır) verileri verilerin depolandığı dizine ekleyerek, verileri kalıcı hale getirebilirsiniz. Kapsayıcı `todo.db` dosyaya yazarken, birimdeki konakta kalıcı hale getirilir.

Belirtildiği gibi, **adlandırılmış bir birim**kullanacaksınız. Adlandırılmış bir birimi yalnızca bir veri demeti olarak düşünün. Docker, diskteki fiziksel konumu korur ve yalnızca birimin adını hatırlamanız gerekir. Birimi her kullandığınızda Docker doğru verilerin sağlandığından emin olur.

1. Komutunu kullanarak bir birim oluşturun `docker volume create` .

    ```bash
    docker volume create todo-db
    ```

1. Kalıcı Birim kullanılmadan çalışmaya devam ettiği için, panoda (veya ile) Todo uygulama kapsayıcısını bir kez daha durdurun `docker rm -f <id>` .

1. Todo uygulama kapsayıcısını başlatın, ancak `-v` bir birim bağlama belirtmek için bayrağı ekleyin. adlandırılmış birimi kullanacaksınız ve ' a bağlayacaksınız. Bu, `/etc/todos` yolda oluşturulan tüm dosyaları yakalar.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Kapsayıcı başlatıldıktan sonra, uygulamayı açın ve yapılacaklar listenize birkaç öğe ekleyin.

    ![Yapılacaklar listesine eklenen öğeler](media/items-added.png)

1. ToDo uygulaması için kapsayıcıyı kaldırın. Panoyu veya `docker ps` kimliği almak Için panoyu kullanın ve ardından `docker rm -f <id>` kaldırın.

1. Yukarıdaki komutu kullanarak yeni bir kapsayıcı başlatın.

1. Uygulamayı açın. Öğelerinizi hala listenizde görmeniz gerekir!

1. Listenizi kullanıma alırken kapsayıcıyı kaldırın.

Yaşasın! Artık verilerin nasıl kalıcı hale getirileceğini öğrendiniz!

> [!TIP]
> Adlandırılmış birimler ve BIND takmaları (bir dakika içinde konuşduğumuz), varsayılan bir Docker motoru yüklemesi tarafından desteklenen iki ana birim türü olmakla kalmaz, NFS, SFTP, NetApp ve daha fazlasını desteklemek için kullanılabilecek birçok birim sürücü eklentisi vardır! Bu, özellikle de Sısınma, Kubernetes ve benzeri bir kümelenmiş ortamda kapsayıcı çalıştırmaya başladığınızda önemli olur.

## <a name="dive-into-your-volume"></a>Haciminizi inceleyin

Çok sayıda kişi sıklıkla "adlandırılmış bir birim kullandığım sırada Docker *gerçekten* verileri depoluyor mu?" sorusu ister. Kullanmak istiyorsanız `docker volume inspect` komutunu kullanabilirsiniz.

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

, `Mountpoint` Verilerin depolandığı diskteki gerçek konumdur. Çoğu makinede, konaktan bu dizine erişmek için kök erişiminizin olması gerektiğini unutmayın. Ancak, bu nerede!

> [!NOTE]
> **Doğrudan Docker Desktop üzerinde birim verilerine erişme** Docker Desktop 'ta çalışırken Docker komutları aslında makinenizde küçük bir VM içinde çalışmaktadır. *Bağlamanoktası* dizininin gerçek içeriğine bakmak isterseniz, önce VM 'nin içini almanız gerekir. WSL 2 ' de bu, bir WSL 2 içinde yer alabilir ve dosya Gezgini aracılığıyla erişilebilir.

## <a name="recap"></a>Özet

Bu noktada, yeniden başlatmalara devam eden çalışan bir uygulamanız var! Bu uygulamayı, yatırımlarınızın dışına gösterebilirsiniz ve sizi vizyonunuzu yakalayabilirler!

Ancak, daha önce her değişiklik için görüntüleri yeniden oluşturma işlemi biraz zaman alır. Değişiklikler yapmak için daha iyi bir yol var mı? BIND takmaları (daha önce sunduğumuz için), daha iyi bir yoldur! Şimdi bu görünüme göz atalım!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [BIND takar kullanma](use-bind-mounts.md)
