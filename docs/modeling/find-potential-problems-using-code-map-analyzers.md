---
title: Kod haritası çözümleyicilerini kullanarak olası sorunları bulma
description: Aşırı karmaşık veya geliştirme gerektiren kodu tanımlamanıza yardımcı olması için kod eşlemeleri üzerinde çözümleyicileri nasıl çalıştırabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8817e50ae96a27f6b3b76e28262390271c1fdf4c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388860"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Kod haritası çözümleyicilerini kullanarak olası sorunları bulma

Aşırı karmaşık veya geliştirme gerektiren kodu tanımlamanıza yardımcı olması için kod eşlemeleri üzerinde çözümleyicileri çalıştırın. Örneğin, şu çözümleyicileri kullanabilirsiniz:

|**Şu kodu bulmak için:**|**Olup olmadığını görmek için bu alanları inceleme**|
|-|-|
|Döngüler veya döngüsel bağımlılıklar|Bunları basitleştirebilir ve bu döngüleri bozabilir olup olmadığınızı göz önünde bulundurabilirsiniz.|
|Çok fazla bağımlılık var|Çok fazla işlev gerçekleştirmektedir veya bu alanların değiştirilmesinin etkisini belirlemek için kullanılır. İyi oluşturulmuş bir kod haritası en az sayıda bağımlılık gösterir. Kodun bakımını, değişikliklerini, testlerini ve yeniden kullanmalarını kolaylaştırmak için, bu alanları daha net tanımlanmış olacak şekilde yeniden düzenlemeyi veya benzer işlevleri gerçekleştiren kodu birleştirip birleştiremeyeceknizi düşünün.|
|Bağımlılık yok|Bunlar gereklidir veya bu kodu kaldırmanız gerekip gerek yoktur.|

## <a name="analyze-code-maps"></a>Kod haritalarını analiz etme

Harita araç çubuğunda Düzen **Çözümleyicileri'ne**  >  ve ardından çalıştırmak istediğiniz çözümleyiciyi seçin:

|**Analyzer**|**Şu düğümleri tanımlamak için:**|
|-|-|
|**Döngüsel Başvuru Çözümleyicisi**|Birbirlerine döngüsel bağımlılıklar olması. **Not:**  Genel Türler grubunda yer **alan döngüsel** bağımlılıklar, grubu genişleten haritada gösterilmez.|
|**Hub'ları Bul Çözümleyicisi**|Yüksek oranda bağlı düğümlerin ilk %25'inde yer almaktadır<br /><br /> **Haritada diğer tüm düğümleri gizlemek için**<br /><br /> - Haritanın kısayol menüsünü açın, Gelişmiş, **Seç,** **Seçimi** **Kaldır'ı gizle'yi seçin.**<br />     Harita, seçilmemiş düğümleri gizler ve çözümleyici yeni düğümleri hub olarak tanımlar.|
|**Bağlantı Olmayan Düğüm Çözümleyicisi**|Başka hiçbir düğümden başvuru yok. **Dikkat:**  Kodun kullanılmadı olduğunu varsaymadan önce bu durumların her biri doğrulayın. XAML bağımlılıkları ve çalışma zamanı bağımlılıkları gibi bazı bağımlılıklar kodda statik olarak bulunamaz.|

Kod eşlemesi çözümleyicileri, bunları uygulatktan sonra çalışmaya devam eder. Eşlemeyi değiştirirsiniz, uygulanan çözümleyiciler güncelleştirilmiş eşlemeyi otomatik olarak yeniden işler. Çözümleyici çalıştırmayı durdurmak için harita araç çubuğunda Düzen **Çözümleyicileri'ne**  >  **tıklayın.** Seçilen çözümleyiciyi kapatın.

> [!TIP]
> Çok büyük bir haritanız varsa, çözümleyiciyi çalıştırmanız yetersiz bellek özel durumuna neden olabilir. Bu durumda, kapsamını azaltmak veya daha küçük bir tane oluşturmak için eşlemeyi düzenleyin ve ardından çözümleyiciyi çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
