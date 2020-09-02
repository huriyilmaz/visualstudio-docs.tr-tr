---
title: NPM paketlerini package.jsile yapılandırma
description: package.jskullanarak NPM paket sürümlerini belirtin
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67692370"
---
# <a name="packagejson-configuration"></a>package.json yapılandırması

Çok sayıda NPM paketi olan bir Node.js uygulaması geliştiriyorsanız, bir veya daha fazla paket güncelleştirildikten sonra projenizi oluştururken uyarı veya hatalara çalışmak yaygın bir şekilde çalışmaz. Bazen sürüm çakışması sonuçları veya paket sürümü kullanım dışı bırakılmıştır. İşte [package.jsdosya üzerinde](https://docs.npmjs.com/files/package.json) yapılandırmanıza ve uyarılar veya hatalar gördüğünüzde neler olduğunu anlamanıza yardımcı olacak birkaç hızlı ipucu. Bu, * üzerindepackage.js* için kapsamlı bir kılavuz değildir ve yalnızca NPM paketi sürümü oluşturma ' ya odaklanmıştır.

NPM paketi sürüm oluşturma sistemi katı kurallara sahiptir. Sürüm biçimi buradan aşağıda verilmiştir:

```
[major].[minor].[patch]
```

Bir 5.2.1 sürümü ile uygulamanızdaki bir paketiniz olduğunu varsayalım. Ana sürüm 5 ' tir, ikincil sürüm 2 ' dir ve Düzeltme Eki 1 ' dir.

* Ana sürüm güncelleştirmesinde, paket geriye dönük olarak uyumsuz olan yeni özellikleri, yani son değişiklikleri içerir.
* Küçük bir sürüm güncelleştirmesinde, önceki paket sürümleriyle geriye dönük olarak uyumlu olan pakete yeni özellikler eklenmiştir.
* Bir yama güncelleştirmesinde, bir veya daha fazla hata düzeltmesi dahildir. Hata düzeltmeleri her zaman geriye dönük olarak uyumludur.

Bu, bazı NPM paketi özelliklerinin bağımlılıklara sahip olduğunu belirtmekte bir değer. Örneğin, WebPack ile TypeScript derleyici paketinin (TS-Loader) yeni bir özelliğini kullanmak için, WebPack NPM paketini ve WebPack-CLI paketini de güncelleştirmeniz gerekir.

NPM, paket sürümü oluşturmayı yönetmeye yardımcı olmak için * üzerindepackage.js*kullanabileceğiniz çeşitli gösterimleri destekler. Uygulamanızda kabul etmek istediğiniz paket güncelleştirmelerinin türünü denetlemek için bu gösterimleri kullanabilirsiniz.

Yanıt kullandığınızı **ve tepki verme ve** **tepki verme-Dom** NPM paketini dahil etmeniz gerektiğini varsayalım. Bunu, *package.js* dosyadaki çeşitli yollarla belirtebilirsiniz. Örneğin, bir paketin tam sürümünün kullanımını aşağıda gösterildiği gibi belirtebilirsiniz.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Önceki gösterimi kullanarak, NPM her zaman belirtilen tam sürümü alır, 16.4.2.

Düzeltme Eki güncelleştirmelerine yönelik güncelleştirmeleri sınırlandırmak için özel bir gösterim (hata düzeltmeleri) kullanabilirsiniz. Bu örnekte:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

NPM 'ye düzeltme eki eklendiğinde yalnızca bir paketi güncelleştirmesi gerektiğini bildirmek için tilde (~) karakterini kullanın. Bu nedenle, NPM, 16.4.3 (veya 16.4.4, vb.) için yanıt 16.4.2 güncelleştirebilir, ancak büyük veya küçük sürümde bir güncelleştirmeyi kabul etmez. Bu nedenle 16.4.2, 16.5.0 olarak güncellenmez.

Ayrıca, NPM 'nin ikincil sürüm numarasını güncelleştirecan belirtmek için şapka işareti (^) sembolünü de kullanabilirsiniz.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Bu gösterimi kullanarak, NPM, 16.5.0 (veya 16.5.1, 16.6.0, vb.) için yanıt 16.4.2 güncelleştirebilir, ancak ana sürüme yönelik bir güncelleştirmeyi kabul etmez. Bu nedenle 16.4.2, 17.0.0 olarak güncellenmez.

NPM, paketleri güncelleştirdiğinde, tüm iç içe paketler dahil olmak üzere uygulamanızda kullanılan gerçek NPM paket sürümlerini listeleyen bir *package-lock.js* dosya oluşturur. *package.js* , uygulamanıza yönelik doğrudan bağımlılıkları denetliyorsa, iç içe bağımlılıkları (belirli bir NPM paketi için gereken diğer NPM paketleri) denetlemez. Diğer geliştiricilerin ve Test edicilerin, iç içe geçmiş paketler dahil olmak üzere kullandığınız tam paketleri kullanmakta olduğundan emin olmanız gerekiyorsa, geliştirme döngünüzdeki dosya *package-lock.js* kullanabilirsiniz. Daha fazla bilgi için NPM belgelerindeki [package-lock.js](https://docs.npmjs.com/files/package-lock.json) bölümüne bakın.

Visual Studio için, dosyadaki *package-lock.js* projenize eklenmez, ancak proje klasöründe bulabilirsiniz.
