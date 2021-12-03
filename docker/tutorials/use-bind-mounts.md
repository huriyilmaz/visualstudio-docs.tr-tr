---
title: 'Docker öğreticisi - Bölüm 6: Bağlamaları kullanma'
description: Konakta bağlama noktasını kontrol etmek için bağlama bağlamaları kullanmayı açıklar.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 43343781f0fd88396fa301776b85ac00154ad6c3
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133514304"
---
# <a name="use-bind-mounts"></a>Bağlamaları kullanma

Önceki bölümde, verileri veritabanınıza kalıcı yapmak için adlandırılmış **birim hakkında** bilgi öğrendiniz ve bu birimi kullandınız. Verilerin nerede depolandığı konusunda endişelenmenize gerek olmadığınız için adlandırılmış birimler yalnızca verileri *depolamak* için harikadır.

Bağlama **bağlamaları ile** konakta tam bağlama noktası denetiminde olur. Verileri kalıcı yapmak için bunu kullanabilirsiniz, ancak genellikle kapsayıcılara ek veri sağlamak için kullanılır. Uygulama üzerinde çalışırken bağlamayı kullanarak kaynak kodu kapsayıcıya bağarak kod değişikliklerini görebilir, yanıt ve değişiklikleri hemen görebilir.

Düğüm tabanlı uygulamalar için [nodemon, dosya](https://npmjs.com/package/nodemon) değişikliklerini izlemek ve sonra uygulamayı yeniden başlatmak için harika bir araçtır. Diğer dillerin ve çerçevelerin çoğunda eşdeğer araçlar vardır.

## <a name="quick-volume-type-comparisons"></a>Hızlı birim türü karşılaştırmaları

Bağlama bağlamaları ve adlandırılmış birimler, Docker altyapısıyla birlikte gelen iki ana birim t t'leridir. Ancak, diğer kullanım durumlarını[(SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph,](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/) [NetApp,](https://netappdvp.readthedocs.io/en/stable/) [S3](https://github.com/elementar/docker-s3-volume)ve daha fazlası) desteklemek için ek birim sürücüleri kullanılabilir.

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

1. klasöründe `app` aşağıdaki komutu çalıştırın (karakterleri ile değiştirin ` \ ` `` ` `` Windows PowerShell). Daha sonra neler olduğunu öğrenirsiniz:

    ```bash
    docker run -dp 3000:3000 -w /app -v ${PWD}:/app node:12-alpine sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` - öncekiyle aynı. Ayrılmış (arka plan) modunda çalıştırma ve bağlantı noktası eşlemesi oluşturma
    - `-w /app` - kapsayıcının içinde çalışma dizini
    - `-v ${PWD}:/app"` - geçerli dizini kapsayıcıda konaktan dizinine `/app` bağlama
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

    Günlükleri izlemeyi bitirerek çıkışa basarak çıkışa `Ctrl` + `C` çıkın.

1. Şimdi uygulamada bir değişiklik yapma. Dosyada `src/static/js/app.js` Öğe Ekle düğmesini Basitçe **Ekle** olarak **değiştirebilirsiniz.** Bu değişiklik 109. satırda olacak.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Sayfayı yenileyin (veya açın) ve değişikliğin neredeyse anında tarayıcıya yansıtıldı olduğunu görüyor olun. Node sunucusunun yeniden başlatılması birkaç saniye sürebilir, bu nedenle bir hata alırsanız birkaç saniye sonra yenilemeyi deneyin.

    ![Ekle düğmesi için güncelleştirilmiş etiketin ekran görüntüsü](media/updated-add-button.png)

1. Yapmak için herhangi bir değişiklik yapabilirsiniz. Bitirin, kapsayıcıyı durdurun ve kullanarak yeni görüntünizi derlemeniz `docker build -t getting-started .` gerekir.

Bağlama bağlamaları, yerel *geliştirme* kurulumları için çok yaygındır. Bunun avantajı, geliştirme makinesinin tüm derleme araçlarına ve ortamlara sahip olması gerekmamadır. Tek bir `docker run` komutla geliştirme ortamı çekilir ve kullanıma hazır olur. Komutlarınızı basitleştirmenize Docker Compose (zaten çok sayıda bayrak alasınız) bu adımlardan biri hakkında bilgi edinebilirsiniz.

## <a name="recap"></a>Özet

Bu noktada veritabanınızı kalıcı olarak bulundurarak yatırımcıların ve kurucuların ihtiyaçlarına ve taleplerine hızla yanıt veebilirsiniz. Yaşasın! Peki tahmin edin ne olacak? Harika haberlerle karşılandınız!

**Projeniz gelecekteki geliştirme için seçildi!**

Üretime hazırlanmak için veritabanınızı SQLite'da çalışırken biraz daha iyi ölçeklendirilen bir şeye geçirmeniz gerekir. Kolaylık olması için ilişkisel bir veritabanı kullanmaya devam ediyor ve mySQL'i kullanmak için uygulamanıza geçiş yapmak gerekiyor. Ancak MySQL'i nasıl çalıştırmalısınız? Kapsayıcıların birbirine nasıl konuşmasına izin vesersiniz? Bundan sonra bu konuda bilgi edinmek için bir sonraki adıma kadar devam etmeyi öğreneceğiz!

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Birden çok kapsayıcılı uygulamalar](multi-container-apps.md)
