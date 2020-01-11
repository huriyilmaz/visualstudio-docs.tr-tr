---
title: Kod ölçümlerini Hesapla
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece5c08ca3aa4a9f5e5329dbf6d5fd6c9087d085
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886411"
---
# <a name="code-metrics-values"></a>Kod ölçüm değerleri

Artan karmaşıklık modern yazılım uygulamaları, kodu güvenilir ve sürdürülebilir hale getirme zorluk da artırır. Kod ölçümleri, geliştiricilere, geliştirdikleri daha iyi bir anlayış kod sağlayan yazılım ölçü kümesidir. Kod ölçümleri avantajlarından yararlanarak, geliştiriciler hangi türleri ve/veya yöntemleri yeniden işledi veya daha kapsamlı test anlayabilirsiniz. Geliştirme ekipleri olası riskleri belirlemek, bir proje geçerli durumunu anlamanıza ve yazılım geliştirme sırasında ilerlemeyi.

Geliştiriciler Visual Studio, karmaşıklığı ve bakımı, yönetilen kodun ölçüm kod ölçümleri verileri üretme için kullanabilirsiniz. Bütün bir çözüm ya da tek bir proje için kod ölçümleri verileri oluşturulabilir.

Visual Studio'da kod ölçümleri verileri üretme hakkında daha fazla bilgi için bkz: [nasıl yapılır: kod ölçümleri verileri üretme](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Yazılım ölçümleri

Aşağıdaki liste, kodu Visual Studio hesaplar ölçümleri sonuçları gösterir:

- **Bakım dizini** -0 ile 100 arasında göreceli bir kolayca kod bakım temsil eden dizin değeri hesaplar. Yüksek bir değer daha iyi bakım anlamına gelir. Renk kodlu derecelendirmeleri, hızlı bir şekilde kodunuzda sorunlu noktaları tanımlamak için kullanılabilir. Yeşil bir derecelendirme 20 ile 100 arasında ve kod iyi bakım sahip olduğunu gösterir. Sarı bir derecelendirme 10 ile 19 arasında ve kod oldukça sürdürülebilir olduğunu gösterir. Kırmızı derecesi 0 ile 9 arasında bir derecelendirme ve düşük bakım belirtir. Daha fazla bilgi için, bakım [dizini aralığına ve anlamı](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) blog gönderisine bakın.

- **Döngüsel karmaşıklık** -kod yapısal karmaşıklığını ölçer. Program akışını farklı kod yollarında sayısını hesaplayarak oluşturulur. Karmaşık denetim akışına sahip bir program, iyi kod kapsamı elde etmek için daha fazla test gerektirir ve daha az sürdürülebilir. Daha fazla bilgi için bkz. [Döngüsel karmaşıklığı Için Vikipedi girişi](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Devralma derinliği** -bir diğerinden kalıtımla alan farklı sınıfların sayısını, taban sınıfına geri doğru bir şekilde gösterir. Devralma derinliği, bir temel sınıftaki bir değişikliğin devralınan sınıflarından herhangi birini etkileyebileceğinden, sınıf bağlantısı 'na benzer. Bu sayı arttıkça, devralım ve temel sınıf için mümkün olan en yüksek değişiklik, önemli bir değişikliğe neden olur. Devralma derinliği için, düşük bir değer iyidir ve yüksek bir değer hatalı olur.

- **Sınıf bağlantısından** -bağlantı parametreleri, yerel değişkenler, dönüş türleri, yöntem çağrılarını, genel veya şablon örneklemeleri, temel sınıflar, arabirim uygulamalarını, dış türlerinde tanımlanan alanların benzersiz sınıflarına ölçer ve özniteliği düzenleme. İyi yazılım tasarımı, türleri ve yöntemleri uyumun yüksek olması sahip ve eşlenmesiyle düşük olduğunu belirler. Yüksek bağlantısından yeniden kullanabilir ve diğer türleri, birçok bağımlılıkları nedeniyle korumak zor bir tasarımın belirtisidir. Daha fazla bilgi için bkz. [ders](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) Web günlüğü gönderisi sınıfı.

::: moniker range=">=vs-2019"

- **Kaynak kodu satırları** -boş satırlar da dahil olmak üzere kaynak dosyanızda bulunan kaynak kodu satırlarının tam sayısını gösterir. Bu ölçüm, Visual Studio 2019 sürüm 16,4 ve Microsoft. CodeAnalysis. Metiği ('nın 2.9.5 sürümüyle) sürümünden itibaren kullanılabilir.

- **Yürütülebilir kod satırları** -yürütülebilir kod satırlarının veya işlemlerin yaklaşık sayısını gösterir. Bu, çalıştırılabilir koddaki işlem sayısı sayısıdır. Bu ölçüm, Visual Studio 2019 sürüm 16,4 ve Microsoft. CodeAnalysis. Metiği ('nın 2.9.5 sürümüyle) sürümünden itibaren kullanılabilir. Bu değer genellikle, eski modda kullanılan MSIL yönergesi tabanlı ölçüm olan önceki ölçüm ve **kod satırları**için yakın bir eşleşmedir.
::: moniker-end
::: moniker range="vs-2017"

- **Kod satırlarını** -yaklaşık kod içinde satır sayısını belirtir. Sayısı IL kodunu alır ve bu nedenle satır kaynak kodu dosyasının tam sayı değil. Yüksek bir sayı, bir tür veya yöntemin çok fazla iş gerçekleştirmeye çalıştığını ve bölünmesi gerektiğini gösterebilir. Ayrıca, tür veya yöntem korumak zor olabilir gösterebilir.

   > [!NOTE]
   > [Komut satırı sürüm](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) IL yerine kaynak kodunu analiz için kodunu gerçek kod satırlarını ölçümleri araç sayar.
::: moniker-end

## <a name="anonymous-methods"></a>Anonim yöntemler

Bir *anonim yöntem* ada sahip bir yöntem. Anonim yöntemler, en sık temsilcinin parametre olarak bir kod bloğu geçirmek için kullanılır. Yöntem veya erişimci gibi bir üyede tanımlanmış anonim bir yöntem için kod ölçümleri sonuçları, yöntemi bildiren üyeyle ilişkilendirilir. Bunlar, bu yöntemi çağıran bir üye ile ilişkili değildir.

## <a name="generated-code"></a>Oluşturulan kod

Bazı yazılım araçları ve derleyicileri, bir projeye eklenir ve proje Geliştirici görmezsiniz veya değiştirme kod oluşturur. Çoğunlukla, ölçüm değerleri hesaplarken kod ölçümleri oluşturulmuş kodu yoksayar. Bu, hangi geliştirici bakın ve değiştirme yansıtacak şekilde ölçüm değerleri sağlar.

Geliştirici bakın ve değiştirme kodu olduğundan Windows Forms için oluşturulan kodu yok sayıldı değil.

## <a name="next-steps"></a>Sonraki adımlar

- [Nasıl yapılır: kod ölçümleri verileri üretme](../code-quality/how-to-generate-code-metrics-data.md)
- [Kod ölçümleri sonuçları penceresini kullanma](../code-quality/working-with-code-metrics-data.md)
