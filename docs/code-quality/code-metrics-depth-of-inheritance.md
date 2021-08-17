---
title: Kod ölçümleri - Devralma derinliği
ms.date: 1/8/2021
description: Kod ölçümleri için devralma ölçümlerinin derinliği hakkında bilgi Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 6b212f349435f395df9e3acb8a802f51de949f63ae2c494dc30fb08c7091c517
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121405580"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>Kod ölçümleri - Devralma derinliği (DIT)

Bu makalede, nesne odaklı analiz için özel olarak tasarlanmış ölçümlerden biri hakkında bilgi edinmek için: Devralma Derinliği. Devralma ağacının derinliği (DIT) olarak da adlandırılan devralma derinliği, "düğümden ağacın köküne kadar olan en uzun uzunluk" [CK olarak tanımlanır.](#ck) Bunu basit bir örnekle de görmektesiniz. Yeni bir Sınıf Kitaplığı projesi oluşturun ve herhangi bir kod yazmadan önce Çözüm için Kod Ölçümlerini >'i seçerek **kod ölçümlerini hesap edin.**

![Devralma derinliği örneği 1](media/depth-of-inheritance-example-1.png)

Tüm sınıflar'dan `System.Object` devralınmalarından bu yana derinlik şu anda 1'tir. Bu sınıftan devralınır ve yeni sınıfı incelersanız, sonucu görebilir:

![Devralma derinliği örneği 2](media/depth-of-inheritance-example-2.png)

Ağaçtaki düğüm ne kadar düşük olursa ( bu durumda), devralma `Class2` derinliğinin o kadar yüksek olduğunu fark ettik. Çocuk oluşturmaya devam eder ve derinliğin istediğiniz kadar artmasına neden olur.

## <a name="assumptions"></a>Varsayımlar

Devralma derinliği, CK üç temel varsayıma [dayanır:](#ck)

1. Hiyerarşide bir sınıf ne kadar derine inerse, devralınacak yöntem sayısı o kadar fazladır ve bu da davranışını tahmin etmek daha zor hale gelir.

2. Daha derin ağaçlarda daha fazla sınıf ve yöntem söz konusu olduğu için tasarım karmaşıklığı daha fazladır.

3. Ağaçtaki daha derin sınıflar devralınan yöntemleri yeniden kullanabilir.

1. ve 2. varsayımlar, derinlik için daha yüksek bir sayıya sahip olmak kötü olduğunu söyler. Sona ererse iyi durumda olursanız; ancak, 3 varsayımı daha yüksek bir derinlik sayısının olası kod yeniden kullanımı için iyi olduğunu gösterir.

## <a name="analysis"></a>Analiz

Derinlik ölçümlerini şu şekilde okuyabilirsiniz:

- Derinlik için düşük sayı

  Derinlik için düşük bir sayı daha az karmaşıklık anlamına gelir, ancak devralma aracılığıyla daha az kod yeniden kullanma olasılığı da vardır.

- Derinlik için yüksek sayı

  Derinlik için yüksek bir sayı, devralma aracılığıyla kodun yeniden kullanılması olasılığının daha yüksek olduğunu, ancak kodda hata olasılığının daha yüksek olduğunu da gösterir.

## <a name="code-analysis"></a>Kod Çözümleme

Kod analizi, Bakım kuralları kategorisini içerir. Daha fazla bilgi için [bkz. Bakım kuralları.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Eski kod analizini kullanırken, Genişletilmiş Tasarım Kılavuzu kural kümesi bir bakım alanı içerir:

![Devralma tasarımı yönergeleri kural kümelerinin derinliği](media/depth-of-inheritance-design-guidelines.png)

Bakım alanı, devralmaya bir kuraldır:

![Devralma bakımı kuralının derinliği](media/depth-of-inheritance-maintainability-rule.png)

Bu kural, devralma derinliği 6 veya daha yüksek olduğunda bir uyarı gösterir, bu nedenle aşırı devralmayı önlemeye yardımcı olmak iyi bir kuraldır. Kural hakkında daha fazla bilgi edinmek için bkz. [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501).

## <a name="putting-it-all-together"></a>Hepsini Bir Araya Koyma

DIT için yüksek değerler, hata riskinin de yüksek olduğu anlamına gelir, düşük değerler hata riskini azaltır. DIT için yüksek değerler, devralma aracılığıyla kodun yeniden kullanılması için daha büyük bir potansiyel olduğunu gösterir, düşük değerler ise devralmadan yararlanan daha az kod yeniden kullanımı önerir. Yeterli veri olmaması nedeniyle şu anda DIT değerleri için kabul edilen bir standart yoktur. Kısa süre önce yapılan çalışmalar bile [Shatnawi](#shatnawi)ölçümü için standart bir sayı olarak kullanılmaktadır. Bunu desteklemek için ampirik bir kanıt yoktur, ancak birçok kaynak DIT'nin üst sınır olarak 5 veya 6 olması gerektiğini önerir. Örneğin, [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) bkz. .

## <a name="citations"></a>Alıntı

### <a name="ck"></a>Ck

Chidamber, S. R. & ZamanEr, C. F. (1994). Nesne Odaklı Tasarım için Ölçüm Paketi (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 20, Hayır. 6). 14 Mayıs 2011, University of Pittsburgh web sitesinden alındı: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Şurdan

Subramanyam, R. & Ancak, M. S. (2003). Object-Oriented Tasarım Karmaşıklığı için CK Ölçümlerinin Ampirik Analizi: Yazılım Hatalarının Etkileri (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 29, Hayır. 4). 14 Mayıs 2011 tarihinde alındı, ilk olarak University of Massachusetts University web sitesinden edinildi [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi, R. (2010). Open-Source Sistemlerindeki Object-Oriented Ölçümlerinin Kabul Edilebilir Risk Düzeylerinin Nicel Bir Araştırma (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 36, Hayır. 2).