---
title: 'Docker öğreticisi - 5. Bölüm: Bağlama bağlamalarını kullanma'
description: Konakta bağlama noktasını kontrol etmek için bağlama bağlamaları kullanmayı açıklar.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: ad3737ccfa4b0dae8ad427bd79e4adeb2756795b
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222766"
---
# <a name="use-bind-mounts"></a>Bağlamaları kullanma

Önceki bölümde, verileri veritabanınıza kalıcı yapmak için adlandırılmış **birim hakkında** bilgi öğrendiniz ve bu birimi kullandınız. Verilerin nerede depolandığı konusunda endişelenmenize gerek olmadığınız için, adlandırılmış birimler yalnızca verileri *depolamak* için harikadır.

Bağlama **bağlamaları ile** konakta tam bağlama noktası denetiminde olur. Verileri kalıcı yapmak için bunu kullanabilirsiniz, ancak genellikle kapsayıcılara ek veri sağlamak için kullanılır. Uygulama üzerinde çalışırken bağlama kullanarak kaynak kodu kapsayıcıya bağarak kod değişikliklerini görebilir, yanıt ve değişiklikleri hemen görebilir.

Düğüm tabanlı uygulamalar için [nodemon, dosya](https://npmjs.com/package/nodemon) değişikliklerini izlemek ve sonra uygulamayı yeniden başlatmak için harika bir araçtır. Diğer dil ve çerçevelerin çoğunda eşdeğer araçlar vardır.

## <a name="quick-volume-type-comparisons"></a>Hızlı birim türü karşılaştırmaları

Bağlama bağlamaları ve adlandırılmış birimler, Docker altyapısıyla birlikte gelen iki ana birim t t'tir. Ancak, diğer kullanım durumlarını[(SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp,](https://netappdvp.readthedocs.io/en/stable/) [S3](https://github.com/elementar/docker-s3-volume)ve daha fazlası) desteklemek için ek birim sürücüleri kullanılabilir.

| Özellik | Adlandırılmış Birimler | Bağlama bağlamaları |
| -------- | ------------- | ----------- |
| Konak Konumu | Docker seçer | Denetimi siz sağlar |
| Bağlama Örneği `-v` (kullanarak) | my-volume:/usr/local/data | /path/to/data:/usr/local/data |
| Yeni birimi kapsayıcı içeriğiyle doldurmak | Yes | Hayır |
| Birim Sürücülerini Destekler | Yes | Hayır |

## <a name="start-a-dev-mode-container"></a>Geliştirme modu kapsayıcısı başlatma

Geliştirme iş akışını desteklemek için kapsayıcınızı çalıştırmak için aşağıdaki adımları gerçekleştirin:

- Kaynak kodunuzu kapsayıcıya bağlama
- "Geliştirme" bağımlılıkları da dahil olmak üzere tüm bağımlılıkları yükleme
- Dosya sistemi değişikliklerini izlemek için nodemon başlatma

1. Daha önce çalışan kapsayıcılar `getting-started` olmadığınızdan emin olun.

1. Aşağıdaki komutu çalıştırın ` \ ` (dizedeki karakterleri `` ` `` ile Windows PowerShell). Daha sonra neler olduğunu öğrenirsiniz:

    ```bash
    docker run -dp 3000:3000 \
        -w /app \
        -v "%cd%:/app" \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` - öncekiyle aynı. Ayrılmış (arka plan) modunda çalıştırın ve bağlantı noktası eşlemesi oluşturun
    - `-w /app` - "çalışma dizinini" veya komutun çalıştıracak geçerli dizini ayarlar
    - `-v "%cd%:/app"` - geçerli dizini kapsayıcıda konaktan dizinine `/app` bağlama
    - `node:12-alpine` - kullanmak için görüntü. Bunun Dockerfile dosyasından uygulamanıza temel görüntü olduğunu unutmayın
    - `sh -c "yarn install && yarn run dev"` - komutu. Kullanarak bir kabuk başlatan (alpine'da yok) ve tüm bağımlılıkları yüklemek için `sh` `bash` `yarn install` çalıştırarak ve ardından çalıştırarak  `yarn run dev` . içinde bakarsanız `package.json` betiğin başlat `dev` olduğunu `nodemon` göreceğiz.

1. kullanarak günlükleri `docker logs -f <container-id>` izleyebilirsiniz. Bunu gördüğünüzde gitmeye hazır olduğunu bilirsiniz:

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

    Günlükleri izlemeyi bitirerek çıkışa `Ctrl` + `C` çıkın.

1. Şimdi uygulamada bir değişiklik yapma. Dosyada `src/static/js/app.js` Öğe Ekle düğmesini Yalnızca **Ekle** olarak **değiştirebilirsiniz.** Bu değişiklik 109. satırda olacak.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Sayfayı yenileyin (veya açın) ve değişikliğin neredeyse anında tarayıcıya yansıtıldı olduğunu görebilirsiniz. Node sunucusunun yeniden başlatılması birkaç saniye sürebilir, bu nedenle bir hata alırsanız birkaç saniye sonra yenilemeyi deneyin.

    ![Ekle düğmesi için güncelleştirilmiş etiketin ekran görüntüsü](media/updated-add-button.png)

1. Yapmak için herhangi bir değişiklik yapabilirsiniz. Bitirin, kapsayıcıyı durdurun ve kullanarak yeni görüntünizi derlemeniz `docker build -t getting-started .` gerekir.

Bağlama bağlamaları, yerel *geliştirme* kurulumları için çok yaygındır. Bunun avantajı, geliştirme makinesinin tüm derleme araçlarına ve ortamlara sahip olması gerekmamadır. Tek bir `docker run` komutla geliştirme ortamı çekilir ve kullanıma hazır olur. Komutlarınızı basitleştirmenize Docker Compose (zaten çok sayıda bayrak alasınız) bu adımlardan biri hakkında daha fazla bilgi edinebilirsiniz.

## <a name="recap"></a>Özet

Bu noktada veritabanınızı kalıcı olarak bulundurarak yatırımcıların ve kurucuların ihtiyaçlarına ve taleplerine hızla yanıt veebilirsiniz. Yaşasın! Peki tahmin edin ne olacak? Harika haberlerle karşılandınız!

**Projeniz gelecekteki geliştirme için seçildi!**

Üretime hazırlanmak için veritabanınızı SQLite'da çalışırken biraz daha iyi ölçeklendirilen bir şeye geçirmeniz gerekir. Kolaylık olması için ilişkisel bir veritabanı kullanmaya devam ediyor ve mySQL'i kullanmak için uygulamanıza geçiş yapmak gerekiyor. Ancak MySQL'i nasıl çalıştırmalısınız? Kapsayıcıların birbirine konuşmasına nasıl izin vesersiniz? Bir sonraki adım bu olacak!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Birden çok kapsayıcılı uygulamalar](multi-container-apps.md)