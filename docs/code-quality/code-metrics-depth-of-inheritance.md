---
title: Kod ölçümleri-devralma derinliği
ms.date: 1/8/2021
description: Visual Studio ' deki kod ölçümleri için devralma ölçümünün derinliği hakkında bilgi edinin.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: c08a35a622eeb30a51b4dea2ab4914b0105b01cd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632066"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>Kod ölçümleri-devralmanın derinliği (DıT)

Bu makalede, nesne odaklı analiz için özel olarak tasarlanan ölçülerden biri hakkında bilgi edinirsiniz: devralma derinliği. Devralma ağacının (DıT) derinliği olarak da adlandırılan devralma derinliği [, "düğümden](#ck)ağacın köküne kadar olan en fazla uzunluk" olarak tanımlanır. Bunu basit bir örnekle görebilirsiniz. Yeni bir sınıf kitaplığı projesi oluşturun ve herhangi bir kod yazmadan önce kod ölçümlerini **analiz edin > çözüm Için kod ölçümlerini hesapla**' yı seçin.

![Devralma örneği 1](media/depth-of-inheritance-example-1.png)

Tüm sınıflar öğesinden devraldığı `System.Object` için Derinlik 1 ' dir. Bu sınıftan devralması ve yeni sınıfı incelerseniz, sonucu görebilirsiniz:

![Devralma örneği 2 derinliği](media/depth-of-inheritance-example-2.png)

Ağaçtaki düğüm ( `Class2` Bu durumda) altında, devralma derinliğine göre daha yüksek olduğuna dikkat edin. Alt öğe oluşturmaya devam edebilir ve derinliğin istediğiniz kadar artmasına neden olabilirsiniz.

## <a name="assumptions"></a>Varsayımlar

Devralma derinliği üç [temel varsayımda](#ck)belirlenir:

1. Hiyerarşide daha derin bir sınıf, büyük olasılıkla devraldığı yöntemlerin sayısı artar ve bu da davranışını tahmin etmeye daha zor hale gelir.

2. Daha derin ağaçlar daha fazla sınıf ve yöntem dahil olduğundan daha fazla tasarım karmaşıklığı içerir.

3. Ağaçtaki daha derin sınıfların devralınan yöntemleri yeniden kullanmak için daha büyük bir olasılığı vardır.

Varsayımlar 1 ve 2, derinlik için daha yüksek bir sayı olmasının hatalı olduğunu söyler. Bu, sona erdiği, iyi bir şekildir; Ancak, varsayım 3, olası kod yeniden kullanımı için derinlik için daha yüksek bir sayının iyi olduğunu gösterir.

## <a name="analysis"></a>Analiz

Derinlik ölçüsünü şu şekilde okuyabilirsiniz:

- Derinlik için düşük sayı

  Derinlik açısından düşük bir sayı daha az karmaşıklık anlamına gelir ancak devralma yoluyla daha az kod yeniden kullanımı olasılığı vardır.

- Derinlik için yüksek sayı

  Derinlik açısından yüksek bir sayı, devralma yoluyla kod yeniden kullanımı için daha fazla olasılık, aynı zamanda koddaki hataların büyük bir olasılığı daha yüksektir.

## <a name="code-analysis"></a>Kod Çözümleme

Kod Analizi bir bakım kuralları kategorisi içerir. Daha fazla bilgi için bkz. [Bakımlamama kuralları](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Eski Kod analizini kullanırken, genişletilmiş tasarım kılavuz kuralı kümesi bir bakım alanı içerir:

![Devralma tasarım yönergeleri kural kümelerinin derinliği](media/depth-of-inheritance-design-guidelines.png)

Bakım alanının içinde, devralma için bir kuraldır:

![Devralma bakımınızın derinliği](media/depth-of-inheritance-maintainability-rule.png)

Bu kural, devralma derinliği 6 veya daha büyük olduğunda bir uyarı verir, bu nedenle aşırı devralmayı önlemeye yardımcı olmak için iyi bir kuraldır. Kural hakkında daha fazla bilgi edinmek için bkz. [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501).

## <a name="putting-it-all-together"></a>Tümünü bir araya getirme

DıT için yüksek değerler, hatalara yönelik potansiyel olarak yüksek olması anlamına gelir, düşük değerler hatalara karşı olası değeri azaltır. DıT için yüksek değerler devralma yoluyla kod yeniden kullanımı için daha fazla potansiyel bir değer gösteriyorsa, düşük değerler devralmadan faydalanabilir daha az kod yeniden kullanımı önerir. Yeterli veri olmaması nedeniyle, DıT değerleri için şu anda kabul edilmeyen standart yok. Kısa süre önce gerçekleştirilen çalışmalar, bu ölçüm [Shatnawi](#shatnawi)için standart bir sayı olarak kullanılabilecek, önemli bir sayıyı belirlemede yeterli veri bulamadı. Bunu desteklemeye yönelik bir empırik kanıt olmasa da, birkaç kaynak, 5 veya 6 ' dan bir DıT 'in üst sınır olmasını önerir. Örneğin, bkz [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) ..

## <a name="citations"></a>Alıntı

### <a name="ck"></a>STOKLAMA

Oyduklik, S. R. & Kemerer, C. F. (1994). Nesne odaklı tasarıma yönelik bir ölçüm paketi (yazılım mühendisliğinde IEEE Işlemleri, Vol. 20, hayır. 6). University of the Yatsburgh Web sitesinden 14 Mayıs 2011 ' den alınır: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Krishnan

Subkmanyam, R. & Krishnan, M. S. (2003). Object-Oriented tasarım karmaşıklığı için CK ölçüm Analizi: yazılım bozuklukları (yazılım mühendisliğinde IEEE Işlemleri, ses. 29, hayır) için etkiler. 4). İlk olarak University of Massachusetts Dartağız Web sitesi 'nden edinilen 14 Mayıs 2011 ' i alındı [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi, R. (2010). Open-Source sistemlerdeki Object-Oriented ölçümlerinin kabul edilebilir risk düzeyleri (yazılım mühendisliğinde IEEE Işlemleri, Vol. 36, hayır) için bir nicel araştırması. 2).