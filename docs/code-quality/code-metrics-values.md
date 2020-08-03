---
title: Kod ölçümlerini hesapla
ms.date: 11/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.codemetrics.toolwindow
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 841b73bbb0c1f226e4a31a812bf8745bda1f118c
ms.sourcegitcommit: e359b93c93c6ca316c0d8b86c2b6e566171fd1ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507878"
---
# <a name="code-metrics-values"></a>Kod ölçüm değerleri

Modern yazılım uygulamalarının artan karmaşıklığı, kodun güvenilir ve sürdürülebilir hale getirilmesi zorluklarını de artırır. Kod ölçümleri, geliştiricilerin geliştirdikleri koda daha iyi Öngörüler sağlayan bir yazılım ölçüleri kümesidir. Geliştiriciler kod ölçümlerinden yararlanarak hangi türlerin ve/veya yöntemlerin yeniden çalışması gerektiğini veya daha kapsamlı olarak test edildiğini anlayabilirler. Geliştirme ekipleri potansiyel riskleri tanımlayabilir, projenin geçerli durumunu anlayabilir ve yazılım geliştirme sırasında ilerleme durumunu izleyebilir.

Geliştiriciler, yönetilen kodların karmaşıklığını ve bakımlarını ölçen kod ölçüm verileri oluşturmak için Visual Studio 'Yu kullanabilir. Tüm çözüm veya tek bir proje için kod ölçüm verileri oluşturulabilir.

Visual Studio 'da kod ölçüm verileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kod ölçümleri verileri oluşturma](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Yazılım ölçümleri

Aşağıdaki listede, Visual Studio 'Nun hesapladığı kod ölçümleri sonuçları gösterilmektedir:

- Bakım **dizini** -kodu korumanın göreli kolaylığını temsil eden 0 ile 100 arasında bir dizin değeri hesaplar. Yüksek bir değer, daha iyi bakım anlamına gelir. Renk kodlu derecelendirmeler kodunuzda sorun noktaları hızlı bir şekilde belirlemek için kullanılabilir. Yeşil derecelendirme 20 ile 100 arasındadır ve kodun iyi bakım yaptığını gösterir. Sarı bir derecelendirme 10 ile 19 arasındadır ve kodun oldukça sürdürülebilir olduğunu gösterir. Kırmızı bir derecelendirme 0 ile 9 arasında bir derecelendirmesidir ve düşük bakım olduğunu gösterir. Daha fazla bilgi için, bakım [dizini aralığına ve anlamı](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) blog gönderisine bakın.

- **Döngüsel karmaşıklığı** -kodun yapısal karmaşıklığını ölçer. Program akışındaki farklı kod yollarının sayısı hesaplanarak oluşturulur. Karmaşık denetim akışına sahip bir program, iyi kod kapsamı elde etmek için daha fazla test gerektirir ve daha az sürdürülebilir. Daha fazla bilgi için bkz. [Döngüsel karmaşıklığı Için Vikipedi girişi](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Devralma derinliği** -bir diğerinden kalıtımla alan farklı sınıfların sayısını, taban sınıfına geri doğru bir şekilde gösterir. Devralma derinliği, bir temel sınıftaki bir değişikliğin devralınan sınıflarından herhangi birini etkileyebileceğinden, sınıf bağlantısı 'na benzer. Bu sayı arttıkça, devralım ve temel sınıf için mümkün olan en yüksek değişiklik, önemli bir değişikliğe neden olur. Devralma derinliği için, düşük bir değer iyidir ve yüksek bir değer hatalı olur.

- **Sınıf** bağlantısı-parametreler, yerel değişkenler, dönüş türleri, Yöntem çağrıları, genel veya şablon örneklemeleri, temel sınıflar, arabirim uygulamaları, dış türlerde tanımlı alanlar ve öznitelik dekorasyonu aracılığıyla benzersiz sınıflara yapılan eşlenmeyi ölçer. İyi yazılım tasarımı, türlerin ve yöntemlerin yüksek düzeyde ve düşük bir eşlencede sahip olması gerektiğini belirler. Yüksek bağlantı, diğer türler üzerinde birçok bağımlılığı nedeniyle yeniden kullanılması zor olan bir tasarımın olduğunu gösterir. Daha fazla bilgi için bkz. [ders](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) Web günlüğü gönderisi sınıfı.

::: moniker range=">=vs-2019"

- **Kaynak kodu satırları** -boş satırlar da dahil olmak üzere kaynak dosyanızda bulunan kaynak kodu satırlarının tam sayısını gösterir. Bu ölçüm, Visual Studio 2019 sürüm 16,4 ve Microsoft. CodeAnalysis. ölçümlerini ('nın 2.9.5 sürümüyle) ile başlayarak kullanılabilir.

- **Yürütülebilir kod satırları** -yürütülebilir kod satırlarının veya işlemlerin yaklaşık sayısını gösterir. Bu, çalıştırılabilir koddaki işlem sayısı sayısıdır. Bu ölçüm, Visual Studio 2019 sürüm 16,4 ve Microsoft. CodeAnalysis. ölçümlerini ('nın 2.9.5 sürümüyle) ile başlayarak kullanılabilir. Bu değer genellikle, eski modda kullanılan MSIL yönergesi tabanlı ölçüm olan önceki ölçüm ve **kod satırları**için yakın bir eşleşmedir.
::: moniker-end
::: moniker range="vs-2017"

- **Kod satırları** -koddaki yaklaşık satır sayısını gösterir. Sayı, Il kodunu temel alır ve bu nedenle kaynak kodu dosyasındaki tam satır sayısı değildir. Yüksek bir sayı, bir tür veya yöntemin çok fazla iş gerçekleştirmeye çalıştığını ve bölünmesi gerektiğini gösterebilir. Ayrıca tür veya yöntemin sürdürmek zor olabileceğini de gösterebilir.

   > [!NOTE]
   > Kod ölçümleri aracının [komut satırı sürümü](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) , Il yerine kaynak kodu analiz ettiğinden gerçek kod satırlarını sayar.
::: moniker-end

## <a name="anonymous-methods"></a>Anonim Yöntemler

*Anonim yöntem* yalnızca adı olmayan bir yöntemdir. Anonim yöntemler en sık, bir kod bloğunu temsilci parametresi olarak geçirmek için kullanılır. Yöntem veya erişimci gibi bir üyede tanımlanmış anonim bir yöntem için kod ölçümleri sonuçları, yöntemi bildiren üyeyle ilişkilendirilir. Bu, yöntemi çağıran üyeyle ilişkili değildir.

## <a name="generated-code"></a>Oluşturulan kod

Bazı yazılım araçları ve derleyiciler, bir projeye eklenen ve proje geliştiricisinin değiştirmediğinden veya değişmediğinden emin olan kodu oluşturur. Genellikle, kod ölçümleri ölçüm değerlerini hesaplarken oluşturulan kodu yoksayar. Bu, ölçüm değerlerinin geliştiricinin neleri görebileceğini ve değiştirebileceklerini yansıtmalarını sağlar.

Windows Forms için oluşturulan kod, geliştiricinin görebileceği ve değiştirebildiğinden kod olduğundan yok sayılır.

## <a name="next-steps"></a>Sonraki adımlar

- [Nasıl yapılır: kod ölçümleri verileri oluşturma](../code-quality/how-to-generate-code-metrics-data.md)
- [Kod ölçümleri sonuçları penceresini kullanın](../code-quality/working-with-code-metrics-data.md)
