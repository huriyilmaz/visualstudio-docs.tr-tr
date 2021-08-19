---
title: 'Docker öğreticisi-3. kısım: uygulamanızı güncelleştirme'
description: Bir Docker uygulamasının nasıl güncelleştirileceğini açıklar.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 0ce798b3264eedea5826df0ca2076c7fbc6ee4c6
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334310"
---
# <a name="update-the-app"></a>Uygulamayı güncelleştirme

Küçük bir özellik isteği olarak, hiçbir yapılacaklar listesi öğesi olmadığında ürün ekibinin "boş metni" değiştirmesi istenir. Bunlar, aşağıdaki gibi geçiş yapmak istiyor:

> Henüz Yapılacaklar öğeleriniz yok! Yukarıya bir tane ekleyin!

Oldukça basit, doğru mu? Değişikliği yapalim.

## <a name="update-the-source-code"></a>Kaynak kodu güncelleştirme

1. `src/static/js/app.js`Dosyasında yeni boş metni kullanmak için 56 satırını güncelleştirin.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Daha önce kullandığınız komutu kullanarak görüntünün güncelleştirilmiş sürümünü oluşturun.

    ```bash
    docker build -t getting-started .
    ```

1. Güncelleştirilmiş kodu kullanarak yeni bir kapsayıcı başlatın.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Uh oh!** Büyük olasılıkla aşağıdakine benzer bir hata gördük (kimlikler farklı olacak):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Ne oldu? Eski Kapsayıcınız çalışmaya devam ettiğinden yeni kapsayıcı başlatılamadı. Bunun bir sorun olmasının nedeni, kapsayıcının ana bilgisayarın bağlantı noktası 3000 ' i kullandığından ve makinede yalnızca bir işlem (kapsayıcı dahil) belirli bir bağlantı noktasını dinleyebileceğinden oluşur. Bu hatayı onarmak için eski kapsayıcıyı kaldırın.

## <a name="replace-the-old-container"></a>Eski kapsayıcıyı Değiştir

Bir kapsayıcıyı kaldırmak için öncelikle durdurulması gerekir. Durduktan sonra, kaldırılabilir. Eski kapsayıcıyı kaldırabilmeniz için kullanabileceğiniz iki yol vardır. En rahat olan yolu seçebilirsiniz.

### <a name="remove-a-container-using-the-cli"></a>CLı kullanarak kapsayıcıyı kaldırma

1. Komutunu kullanarak kapsayıcının KIMLIĞINI alın `docker ps` .

    ```bash
    docker ps
    ```

1. `docker stop`Kapsayıcıyı durdurmak için komutunu kullanın.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Kapsayıcı durdurulduktan sonra, komutunu kullanarak kaldırabilirsiniz `docker rm` .

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Komutuna "zorla" bayrağını ekleyerek tek bir komutta kapsayıcıyı durdurabilir ve kaldırabilirsiniz `docker rm` . Örnek: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>Docker görünümünü kullanarak kapsayıcıyı kaldırma

VS Code uzantısını açarsanız, iki tıklamayla bir kapsayıcıyı kaldırabilirsiniz! Kapsayıcı KIMLIĞINI aramak ve kaldırmak zorunda kalmadan kesinlikle çok daha kolay.

1. Uzantı açıldığında kapsayıcıya gidin ve sağ tıklayın.

1. **Kaldır** seçeneğine tıklayın.

1. Kaldırmayı onaylayın ve işiniz bitti!

![Docker görünümü-kapsayıcıyı kaldırma](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Güncelleştirilmiş uygulama kapsayıcısını Başlat

1. Şimdi, güncelleştirilmiş uygulamanızı başlatın.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Üzerinde tarayıcınızı yenileyin [http://localhost:3000](http://localhost:3000) ve güncelleştirilmiş yardım metninizi görmeniz gerekir!

![Güncelleştirilmiş boş metinle güncelleştirilmiş uygulama](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Özet

Bir güncelleştirme derlemenize rağmen, fark etmiş olabileceğiniz iki şey vardır:

- Yapılacaklar listenizdeki tüm mevcut öğeler kayboldu! Bu çok iyi bir uygulama değildir! Kısa süre içinde konuşacağız.
- Bu tür küçük bir değişikliğe yönelik *birçok* adım vardır. Yaklaşan bir bölümde, her değişiklik yaptığınızda yeni bir kapsayıcı oluşturmak ve başlatmak gerekmeden kod güncelleştirmelerini nasıl görebileceğinizi öğreneceksiniz.

Kalıcılık hakkında bilgi edinmek için bu görüntüleri başkalarıyla nasıl paylaşacağınızı hızlıca görürsünüz.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Uygulamanızı paylaşma](share-your-app.md)
