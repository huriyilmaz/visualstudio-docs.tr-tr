---
title: npm paketlerini package.json ile yapılandır
description: package.json kullanarak npm paket sürümlerini belirtin
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 652ff7b0380fc03a3f9c8155a2f8696d9dfee5b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "67692370"
---
# <a name="packagejson-configuration"></a>package.json yapılandırması

Çok sayıda npm paketi içeren bir Düğüm.js uygulaması geliştiriyorsanız, projenizi oluştururken bir veya daha fazla paket güncelleştirilmişse uyarılar veya hatalarla karşılaştığınızda sık rastlanan bir durum değildir. Bazen, bir sürüm çakışma sonuçları veya bir paket sürümü amortismana kalmıştır. Burada, [package.json](https://docs.npmjs.com/files/package.json) dosyanızı yapılandırmanıza ve uyarılar veya hatalar gördüğünüzde neler olup bittiğini anlamanıza yardımcı olacak birkaç hızlı ipucu verilmiştir. Bu *package.json* için tam bir rehber değildir ve sadece npm paket sürümü odaklanmıştır.

npm paket sürüm sisteminin katı kuralları vardır. Sürüm biçimi burada aşağıdaki gibidir:

```
[major].[minor].[patch]
```

Uygulamanızda 5.2.1 sürümü içeren bir paket olduğunu varsayalım. Ana sürüm 5, küçük sürüm 2 ve yama 1'dir.

* Büyük bir sürüm güncelleştirmesinde, paket geriye doğru uyumsuz, yani değişiklikleri bozan yeni özellikler içerir.
* Küçük bir sürüm güncelleştirmesinde, önceki paket sürümleriyle geriye dönük olarak uyumlu olan pakete yeni özellikler eklendi.
* Bir yama güncelleştirmesinde, bir veya daha fazla hata düzeltmesi dahildir. Hata düzeltmeleri her zaman geriye dönük uyumludur.

Bazı npm paket özelliklerinin bağımlılıkları olduğunu belirtmekte fayda var. Örneğin, Webpack ile TypeScript derleyici paketinin (ts-loader) yeni bir özelliğini kullanmak için, webpack npm paketini ve webpack-cli paketini güncellemeniz de mümkündür.

Paket sürümünü yönetmenize yardımcı olmak için npm, *package.json'da*kullanabileceğiniz birkaç gösterimi destekler. Bu gösterimleri, uygulamanızda kabul etmek istediğiniz paket güncelleştirmelerinin türünü denetlemek için kullanabilirsiniz.

Diyelim ki React kullanıyorsunuz ve **react** ve **react-dom** npm paketini eklemeniz gerekiyor. Bunu *paket.json* dosyanızda çeşitli şekillerde belirtebilirsiniz. Örneğin, paketin tam sürümünü aşağıdaki gibi belirtebilirsiniz.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Önceki gösterimi kullanarak, npm her zaman belirtilen tam sürümü, 16.4.2 alırsınız.

Güncelleştirmeleri yama güncelleştirmeleri (hata düzeltmeleri) ile sınırlamak için özel bir gösterim kullanabilirsiniz. Bu örnekte:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

npm'e bir paketi yalnızca yamalı olduğunda güncellemesini söylemek için tilde (~) karakterini kullanırsınız. Yani, npm tepki 16.4.2 16.4.3 (veya 16.4.4, vb) güncelleyebilirsiniz, ancak büyük veya küçük sürümü için bir güncelleştirme kabul etmez. Yani, 16.4.2 16.5.0 güncelleştirilmeyecektir.

NPM'nin küçük sürüm numarasını güncelleştirebileceğini belirtmek için caret (^) simgesini de kullanabilirsiniz.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Bu gösterimi kullanarak, npm react 16.4.2 ile 16.5.0 (veya 16.5.1, 16.6.0, vb.) güncelleyebilir, ancak ana sürümiçin bir güncelleştirme kabul etmez. Yani, 16.4.2 17.0.0 güncelleştirilmeyecek.

nPM paketleri güncellediğinde, uygulamanızda kullanılan tüm iç içe paketler de dahil olmak üzere gerçek npm paket sürümlerini listeleyen bir *paket-lock.json* dosyası oluşturur. *package.json* uygulamanız için doğrudan bağımlılıkları kontrol ederken, iç içe geçen bağımlılıkları (belirli bir npm paketinin gerektirdiği diğer npm paketleri) denetlemez. Diğer geliştiricilerin ve sınayıcıların iç içe geçen paketler de dahil olmak üzere kullandığınız tam paketleri kullandığından emin olmanız gerekiyorsa, geliştirme döngünüzdeki *package-lock.json* dosyasını kullanabilirsiniz. Daha fazla bilgi için npm belgelerinde [package-lock.json'a](https://docs.npmjs.com/files/package-lock.json) bakın.

Visual Studio için *package-lock.json* dosyası projenize eklenmez, ancak proje klasöründe bulabilirsiniz.
