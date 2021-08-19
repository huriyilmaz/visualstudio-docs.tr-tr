---
title: 'Docker öğreticisi - 5. Bölüm: Verilerinizi kalıcı yapma'
description: Bir birim takarak veritabanındaki verileri kalıcı yapmayı ve dizinleri kapsayıcıda paylaşmayı öğrenin.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 36c7a2dbada3dd1f23b45019dc0690f3ba1ab5f1
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334472"
---
# <a name="persist-your-data"></a>Verilerinizi kalıcı olarak kalıcı olarak koruma

Fark etmeyebilirsiniz; kapsayıcıyı her başlatmada todo listesi temizlenir. Bu neden? Şimdi kapsayıcının nasıl çalıştığına bakalım.

## <a name="the-containers-filesystem"></a>Kapsayıcının dosya sistemi

Kapsayıcı çalıştır geldiğinde, dosya sistemi için bir görüntüdeki çeşitli katmanları kullanır. Her kapsayıcının dosyaları oluşturmak, güncelleştirmek veya kaldırmak için kendi "karalama alanı" da olur. Aynı görüntüyü kullansalar bile herhangi bir *değişiklik başka* bir kapsayıcıda görülmez.

### <a name="see-this-in-practice"></a>Uygulamada buna bakın

Bunu uygulamalı olarak görmek için iki kapsayıcı başlatacak ve her kapsayıcıda bir dosya oluşturabilirsiniz. Bir kapsayıcıda oluşturulan dosyaların başka bir kapsayıcıda mevcut olmadığını göreceğiz.

1. 1 `ubuntu` ile 10000 arasında rastgele bir sayı ile adlı bir `/data.txt` dosya oluşturacak bir kapsayıcıyı başlatma.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Komutu merak ediyor olabilir, bir bash kabuğu başlatıyor ve iki komutu (neden komutu var) `&&` başlatıyorsunuz? İlk bölüm tek bir rastgele sayı seçer ve bunu 'a `/data.txt` yazar. İkinci komut, kapsayıcıyı çalıştırmaya devam etmek için bir dosyayı izlemektir.

1. Kapsayıcıya almak için kullanarak çıkışı `exec` gördüğünüzi onaylar. Bunu yapmak için, VS Code uzantısını açın ve Kabuk Ekle **seçeneğine** tıklayın. Bu, `exec` terminalde kapsayıcıda bir kabuk açmak için VS Code kullanılır.

    ![VS Code CLI'sini ubuntu kapsayıcısı içine açma](media/attach_shell.png)

    Ubuntu kapsayıcısı içinde kabuk çalıştıran bir terminali görüyorsunuz. Dosyanın içeriğini görmek için aşağıdaki komutu `/data.txt` çalıştırın. Daha sonra bu terminali tekrar kapatın.

    ```bash
    cat /data.txt
    ```

    Komut satırı tercih ederseniz komutunu kullanarak `docker exec` da aynı komutu kullanabilirsiniz. Kapsayıcının kimliğini (almak için `docker ps` kullanın) ve aşağıdaki komutla içeriği alasiniz.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Rastgele bir sayı görüyor gerekir!

1. Şimdi başka `ubuntu` bir kapsayıcıyı (aynı görüntü) başlatarak aynı dosyaya sahip olmadığınız bir durumla karşı karşınız.

    ```bash
    docker run -it ubuntu ls /
    ```

    Ve şuna bakın! Dosya `data.txt` yok! Bunun nedeni yalnızca ilk kapsayıcı için sıfırdan alana yazıldığıdır.

1. Devam edin ve komutunu kullanarak ilk kapsayıcıyı `docker rm -f` kaldırın.

## <a name="container-volumes"></a>Kapsayıcı birimleri

Önceki denemede her kapsayıcının her başlatıldığında görüntü tanımından başlat olduğunu görmüştük. Kapsayıcılar dosyaları oluşturabilir, güncelleştire ve silebilir ancak kapsayıcı kaldırıldığı zaman bu değişiklikler kaybolur ve tüm değişiklikler bu kapsayıcıya yalıtılır. Birimlerle bunların hepsini değiştirebilirsiniz.

[Birimler,](https://docs.docker.com/storage/volumes/) kapsayıcının belirli dosya sistemi yollarını konak makineye geri bağlama olanağı sağlar. Kapsayıcıda bir dizin bağlı ise, konak makinede bu dizinde yapılan değişiklikler de görülür. Aynı dizini kapsayıcı yeniden başlatmaları arasında bağlarsanız aynı dosyaları da görebilirsiniz.

İki ana birim türü vardır. sonunda her ikisini de kullanır, ancak adlandırılmış birimlerle **başlayacaktır.**

## <a name="persist-your-todo-data"></a>Todo verilerinizi kalıcı olarak koruma

Varsayılan olarak, todo uygulaması verilerini bir [SQLite](https://www.sqlite.org/index.html) Veritabanında `/etc/todos/todo.db` depolar. SQLite hakkında bilginiz yoksa endişelenmeyin! Yalnızca tüm verilerin tek bir dosyada depolandığı ilişkisel bir veritabanıdır. Bu, büyük ölçekli uygulamalar için en iyi uygulama olsa da, küçük tanıtımlar için çalışır. Bunu daha sonra gerçek bir veritabanı altyapısına değiştirme hakkında konuşacağız.

Veritabanının tek bir dosya olmasıyla, bu dosyayı konakta kalıcı hale gelip sonraki kapsayıcı için kullanılabilir hale geliyorsanız, en son kalan dosyayı alabilecektir. Bir birim oluşturarak ve verileri depolandığı dizine iliştirerek (genellikle "bağlama" olarak adlandırılır), verileri kalıcı olarak bulundurabilirsiniz. Kapsayıcı dosyaya `todo.db` yazdığında birim içinde konakta kalıcı olur.

Daha önce de belirtildiği gibi, adlı bir birim **kullan kullanırsiniz.** Adlandırılmış birimi bir veri demeti olarak düşünebilirsiniz. Docker diskte fiziksel konumun bakımını yapar ve yalnızca birimin adını hatırlamamız gerekir. Birimi her kullanımında Docker doğru verilerin sağ olduğundan emin olur.

1. komutunu kullanarak birim `docker volume create` oluşturun.

    ```bash
    docker volume create todo-db
    ```

1. Docker görünümünde (veya ile) todo uygulama kapsayıcısını bir kez daha durdurun çünkü hala kalıcı birimi `docker rm -f <id>` kullanmadan çalışıyor.

1. Todo uygulaması kapsayıcısı'nı başlatma, ancak birim `-v` bağlaması belirtmek için bayrağını ekleyin. Adlandırılmış birimi kullanır ve yolunda oluşturulan tüm `/etc/todos` dosyaları yakalayan birimine bağlarsiniz.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Kapsayıcı başladıktan sonra uygulamayı açın ve todo listenize birkaç öğe ekleyin.

    ![Todo listesine eklenen öğeler](media/items-added.png)

1. Todo uygulaması için kapsayıcıyı kaldırın. Kimliği almak ve ardından kaldırmak için Docker görünümünü veya `docker ps` `docker rm -f <id>` kullanın.

1. Yukarıdan aynı komutu kullanarak yeni bir kapsayıcı başlatabilirsiniz.

1. Uygulamayı açın. Öğelerinizin hala listelerde olduğunu görüyor gerekir!

1. Listenizi denetlemeyi bitirin ve kapsayıcıyı kaldırın.

Yaşasın! Şimdi verilerin nasıl kalıcı olduğunu öğrendiniz!

> [!TIP]
> Adlandırılmış birimler ve bağlamalar (bir dakika içinde bahsedecek), varsayılan Docker altyapısı yüklemesi tarafından desteklenen iki ana birim türüyken NFS, SFTP, NetApp ve daha fazlasını desteklemek için birçok birim sürücüsü eklentisi vardır! Bu durum özellikle Swarm, Kubernetes gibi kümelenmiş bir ortamdaki birden çok konakta kapsayıcı çalıştırmaya başladıktan sonra önemlidir.

## <a name="dive-into-your-volume"></a>Biriminizi inceleme

Birçok kişi sıklıkla "Adlandırılmış birim kullanılırken *Docker* verilerimi gerçekten nerede depolar?" sorusunu sorar. Bilmek için komutunu `docker volume inspect` kullanabilirsiniz.

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

`Mountpoint`, diskte verilerin depolandığı gerçek konumtur. Çoğu makinede bu dizine konaktan erişmek için kök erişiminizin olması gerekir. Ancak tam da bu şekildedir!

> [!NOTE]
> **Birim verilerine doğrudan Docker Desktop'ta erişme** Docker Desktop'ta çalışırken Docker komutları aslında makinenizin küçük bir VM'sinde çalışıyor. *Mountpoint* dizininin gerçek içeriklerini görmek için öncelikle VM'nin içine girebilirsiniz. WSL 2'de, bu bir WSL 2 dağıtım içindedir ve bu dağıtıma Dosya Gezgini.

## <a name="recap"></a>Özet

Bu noktada, yeniden başlatmalara dayanacak, işleve sahip bir uygulamanız var! Bunu yatırımcılara gösterebilir ve vizyonunu yakalayacaklarını umarız!

Ancak daha önce her değişiklik için görüntülerin yeniden oluşturmanın uzun zaman alan bir süre olduğunu görmüştük. Değişiklik yapmak için daha iyi bir yol olması gerekir, değil mi? Bağlama bağlamaları (daha önce ima ettiysek) daha iyi bir yol vardır! Şimdi buna göz at bakalım!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Bağlamaları kullanma](use-bind-mounts.md)
