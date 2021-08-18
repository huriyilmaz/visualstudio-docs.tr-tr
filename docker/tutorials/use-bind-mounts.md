---
title: 'Docker öğreticisi-Bölüm 6: BIND takar kullanma'
description: Ana bilgisayar üzerindeki bağlama noktasını denetlemek için bağlama bağlamalarından nasıl kullanılacağını açıklar.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 52b8869cd5e83df81953c2d396a787a36a3268276f9843044ba3334e9401fd2b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349136"
---
# <a name="use-bind-mounts"></a>BIND bağlama kullanma

Önceki bölümde, verileri veritabanınızda kalıcı hale getirmek için adlandırılmış bir **birimi** öğrenmiş ve kullandınız. Verilerin *nerede* depolandığını merak etmeniz gerekmiyorsa, yalnızca verileri depolamak istiyorsanız adlandırılmış birimler harika olur.

**BIND** bağlamalarla, konaktaki kesin bağlama noktasını denetlersiniz. Bunu verileri kalıcı hale getirmek için kullanabilirsiniz, ancak genellikle kapsayıcılara daha fazla veri sağlamak için kullanılır. Uygulama üzerinde çalışırken, kod değişikliklerini görmek, yanıt vermek ve değişiklikleri hemen görmenizi sağlamak için kaynak kodu kapsayıcıya bağlamak üzere bir bağlama bağlama kullanabilirsiniz.

Düğüm tabanlı uygulamalar için [nodemon](https://npmjs.com/package/nodemon) , dosya değişikliklerini izlemek ve sonra uygulamayı yeniden başlatmak için harika bir araçtır. Birçok diğer dil ve çerçeve için eşdeğer araçlar vardır.

## <a name="quick-volume-type-comparisons"></a>Hızlı birim türü karşılaştırmaları

BIND ve adlandırılmış birimleri bağlayın, Docker altyapısıyla birlikte gelen iki ana birim türüdür. Ancak, diğer kullanım örneklerini desteklemek için ek birim sürücüleri mevcuttur ([SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume)ve daha fazlası).

| Özellik | Adlandırılmış birimler | BIND takar |
| -------- | ------------- | ----------- |
| Ana bilgisayar konumu | Docker seçer | Kontrol edersiniz |
| Bağlama örneği (kullanarak `-v` ) | My-Volume:/usr/local/Data | /Path/to/Data:/usr/local/Data |
| Yeni birimi kapsayıcı içeriğiyle doldurur | Yes | Hayır |
| Birim sürücülerini destekler | Yes | Hayır |

## <a name="start-a-dev-mode-container"></a>Geliştirme modu kapsayıcısını başlatma

Bir geliştirme iş akışını desteklemek üzere kapsayıcınızı çalıştırmak için şunları yapın:

- Kaynak kodunuzu kapsayıcıya bağlama
- "Dev" bağımlılıkları da dahil olmak üzere tüm bağımlılıkları yükler
- Dosya sistemi değişikliklerini izlemek için nodemon 'i başlatın

1. Çalışan bir önceki Kapsayıcınız olmadığından emin olun `getting-started` .

1. Aşağıdaki komutu çalıştırın ( ` \ ` karakterleri Windows PowerShell ile değiştirin `` ` `` ). Daha sonra neler olduğunu öğreneceksiniz:

    ```bash
    docker run -dp 3000:3000 \
        -w /app \
        -v "%cd%:/app" \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` -daha önce olduğu gibi. Ayrılmış (arka plan) modda çalıştır ve bir bağlantı noktası eşlemesi oluştur
    - `-w /app` -"çalışma dizini" veya komutun çalıştırılacağı geçerli dizini ayarlar
    - `-v "%cd%:/app"` -Geçerli dizini kapsayıcıdaki konaktan `/app` dizine bağlayın
    - `node:12-alpine` -kullanılacak resim. Bunun, Dockerfile 'dan uygulamanız için temel görüntü olduğunu unutmayın.
    - `sh -c "yarn install && yarn run dev"` -komutu. `sh`(Alçam yok) kullanarak bir kabuk başlatıyoruz `bash` ve `yarn install` *Tüm* bağımlılıkları yüklemek ve ardından çalıştırmak için çalışıyor `yarn run dev` . ' A bakarsanız, `package.json` `dev` betiğin başlatıldığını görüyoruz `nodemon` .

1. Kullanarak günlükleri izleyebilirsiniz `docker logs -f <container-id>` . Şunu gördüğünüzde başlamaya hazırsınız:

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Günlükleri izlemeyi tamamladıktan sonra, vurarak çıkış yapın `Ctrl` + `C` .

1. Şimdi uygulamada bir değişiklik yapın. `src/static/js/app.js`Dosyasında, **Ekle**' yi tek yapmanız gereken **öğe Ekle** düğmesini değiştirin. Bu değişiklik 109. satırda olacaktır.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Yalnızca sayfayı yenilemeniz (veya açmanız) ve değişikliğin tarayıcıda neredeyse hemen yansıtıldığını görmeniz gerekir. Düğüm sunucusunun yeniden başlatılması birkaç saniye sürebilir, bu nedenle bir hata alırsanız birkaç saniye sonra yenilemeyi deneyin.

    ![Ekle düğmesi için güncelleştirilmiş etiketin ekran görüntüsü](media/updated-add-button.png)

1. Yapmak istediğiniz başka herhangi bir değişikliği yapmak için ücretsizdir. İşiniz bittiğinde kapsayıcıyı durdurun ve kullanarak yeni görüntünüzü oluşturun `docker build -t getting-started .` .

BIND takmaları kullanmak yerel geliştirme kurulumları için *çok* yaygındır. Avantajı, geliştirme makinesinin tüm derleme araçlarının ve ortamların yüklü olması gerekmez. Tek bir `docker run` komutla, geliştirme ortamı çekilir ve gönderilmeye hazırdır. Gelecekteki bir adımda Docker Compose hakkında bilgi edineceksiniz. Bu, komutlarınızı basitleştirmeye yardımcı olur (zaten çok sayıda bayrak alıyorsunuz).

## <a name="recap"></a>Özet

Bu noktada, veritabanınızı kalıcı hale getirebilirsiniz ve yatırımlarınızın ve temellerinizin ihtiyaçlarına ve taleplerine hızlı bir şekilde yanıt verebilirsiniz. Yaşasın! Ancak neleri tahmin edin? Harika haberler aldınız!

**Projeniz gelecekte geliştirme için seçildi!**

Üretime hazırlanmak için, veritabanınızı SQLite ' dan biraz daha iyi ölçeklenebilen bir şeye geçirmeniz gerekir. Kolaylık olması için, ilişkisel bir veritabanıyla birlikte tutulacak ve uygulamanızı MySQL kullanacak şekilde değiştireceksiniz. Ancak, MySQL 'i nasıl çalıştırmanız gerekir? Kapsayıcıların birbirleriyle iletişim kurmasına nasıl izin verirsiniz? Bu ileri hakkında bilgi edineceksiniz!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Birden çok kapsayıcılı uygulamalar](multi-container-apps.md)