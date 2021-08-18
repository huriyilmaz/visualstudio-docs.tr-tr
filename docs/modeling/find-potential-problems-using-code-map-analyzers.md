---
title: Kod haritası çözümleyicilerini kullanarak olası sorunları bulma
description: Aşırı karmaşık olabilecek veya geliştirme gerektirebilecek kodu tanımanıza yardımcı olması için kod haritaları üzerinde Çözümleyicileri nasıl çalıştırabileceğinizi öğrenin.
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
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 89bc637364a6925c201d2e6fa7061bab2b51d10d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040339"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Kod haritası çözümleyicilerini kullanarak olası sorunları bulma

Aşırı karmaşık olabilecek veya geliştirme gerektirebilecek kodu tanımlamanızı sağlamak için kod haritaları üzerinde çözümleyiciler çalıştırın. Örneğin, bu Çözümleyicileri kullanabilirsiniz:

|**Olan kodu bulmak için**|**Bu alanı inceleyerek**|
|-|-|
|Döngüler veya dairesel bağımlılıklar|Bunları basitleştirebilir ve bu döngüleri bölebilir olup olmayacağını düşünebilirsiniz.|
|Çok fazla bağımlılık|Bunlar çok fazla işlev gerçekleştiriyor veya bu alanların değiştirilmesini belirlemede etkiler. İyi biçimlendirilmiş bir kod eşlemesi, en az sayıda bağımlılığı gösterecektir. Kodu korumak, değiştirmek, test etmek ve yeniden kullanmak daha kolay hale getirmek için, bu alanların daha açık bir şekilde tanımlanması veya benzer işlevleri gerçekleştiren kodu birleştirebilmeniz için yeniden düzenleme yapıp yapamayacağını göz önünde bulundurun.|
|Bağımlılık yok|Bunlar gereklidir veya bu kodu kaldırmanız gerekip gerekmediğini belirtir.|

## <a name="analyze-code-maps"></a>Kod eşlemelerini çözümle

Harita araç çubuğunda, **Düzen**  >  **Çözümleyicileri**' ni ve ardından çalıştırmak istediğiniz çözümleyici 'yi seçin:

|**Analyzer**|**Olan düğümleri belirlemek için**|
|-|-|
|**Döngüsel başvurular Çözümleyicisi**|Birbirini dairesel bağımlılıklardır. **Note:**  Grupları genişlettiğinizde, **Genel türler** grubundaki döngüsel bağımlılıklar haritada gösterilmez.|
|**Hub Çözümleyicisi bulma**|Yüksek oranda bağlı düğümlerin üst %25 ' i<br /><br /> **Haritadaki tüm diğer düğümleri gizlemek için**<br /><br /> -Haritanın kısayol menüsünü açın, **Gelişmiş**' i seçin, Seç ' i **seçin** ve **seçimini gizleyin**.<br />     Harita seçilmemiş düğümleri gizler ve çözümleyici yeni düğümleri hub olarak tanımlar.|
|**Başvurulmayan düğümler Çözümleyicisi**|Diğer düğümlerden başvuruları yoktur. **Dikkat:**  Kodun kullanılmadığını varsaymadan önce bu durumların her birini doğrulayın. XAML bağımlılıkları ve çalışma zamanı bağımlılıkları gibi belirli bağımlılıklar kodda statik olarak bulunamaz.|

Kod Haritası Çözümleyicileri, uygulandıktan sonra çalışmaya devam edecektir. Eşlemeyi değiştirirseniz, uygulanan tüm çözümleyiciler, güncelleştirilmiş Haritayı otomatik olarak yeniden işler. Bir çözümleyici çalıştırmayı durdurmak için harita araç çubuğunda **Düzen**  >  **Çözümleyicileri**' ni seçin. Seçili çözümleyici 'yi devre dışı bırakın.

> [!TIP]
> Çok büyük bir haritanız varsa, bir çözümleyici çalıştırmak yetersiz bellek özel durumuna neden olabilir. Bu durumda, kapsamını daraltmak için haritayı düzenleyin veya daha küçük bir tane oluşturun ve ardından çözümleyici 'yi çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
