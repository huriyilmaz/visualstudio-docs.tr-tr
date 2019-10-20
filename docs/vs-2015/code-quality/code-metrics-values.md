---
title: Kod ölçüm değerleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667730"
---
# <a name="code-metrics-values"></a>Kod Ölçüm Değerleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod ölçümleri, geliştiricilerin geliştirdikleri koda daha iyi Öngörüler sağlayan bir yazılım ölçüleri kümesidir. Geliştiriciler kod ölçümlerinden yararlanarak hangi türlerin ve/veya yöntemlerin yeniden çalışması gerektiğini veya daha kapsamlı olarak test edildiğini anlayabilirler. Geliştirme ekipleri potansiyel riskleri tanımlayabilir, projenin geçerli durumunu anlayabilir ve yazılım geliştirme sırasında ilerleme durumunu izleyebilir.

## <a name="software-measurements"></a>Yazılım ölçümleri
 Aşağıdaki listede [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hesapladığı kod ölçümleri sonuçları gösterilmektedir:

- Bakım **dizini** : kodu korumak için göreli kolaylıklar temsil eden 0 ile 100 arasında bir dizin değeri hesaplar. Yüksek bir değer, daha iyi bakım anlamına gelir. Renk kodlu derecelendirmeler kodunuzda sorun noktaları hızlı bir şekilde belirlemek için kullanılabilir. Yeşil derecelendirme 20 ile 100 arasındadır ve kodun iyi bakım yaptığını gösterir. Sarı bir derecelendirme 10 ile 19 arasındadır ve kodun oldukça sürdürülebilir olduğunu gösterir. Kırmızı bir derecelendirme 0 ile 9 arasında bir derecelendirmesidir ve düşük bakım olduğunu gösterir.

- **Döngüsel karmaşıklığı** – kodun yapısal karmaşıklığını ölçer. Program akışındaki farklı kod yollarının sayısı hesaplanarak oluşturulur. Karmaşık denetim akışına sahip bir program, iyi kod kapsamı elde etmek için daha fazla test gerektirecektir ve daha az sürdürülebilir olur.

    > [!NOTE]
    > Bazı durumlarda [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] bir yöntem için döngüsel karmaşıklığı hesaplama, önceki sürümlerden farklıdır. Daha fazla bilgi için bkz. [Kod ölçümleri sorunlarını gidermek](../code-quality/troubleshooting-code-metrics-issues.md)Için "Visual Studio 2010 kod karmaşıklığı hesaplamalarında yapılan değişiklikler" bölümüne bakın.

- **Devralma derinliği** – sınıf hiyerarşisinin köküne genişleyen sınıf tanımlarının sayısını belirtir. Hiyerarşinin daha derin olması, belirli yöntemlerin ve alanların nerede tanımlandığını veya/ve yeniden tanımlanmasını anlamak için daha zor olabilir.

- **Sınıf** bağlantısı: parametreler, yerel değişkenler, dönüş türleri, Yöntem çağrıları, genel veya şablon örneklemeleri, temel sınıflar, arabirim uygulamaları, dış türlerde tanımlı alanlar ve öznitelik aracılığıyla, benzersiz sınıflara yapılan eşlenmeyi ölçer düzenlemenin. İyi yazılım tasarımı, türlerin ve yöntemlerin yüksek düzeyde ve düşük bir eşlencede sahip olması gerektiğini belirler. Yüksek bağlantı, diğer türler üzerinde birçok bağımlılığı nedeniyle yeniden kullanılması zor olan bir tasarımın olduğunu gösterir.

- **Kod satırları** – koddaki yaklaşık satır sayısını gösterir. Sayı, Il kodunu temel alır ve bu nedenle kaynak kodu dosyasındaki tam satır sayısı değildir. Çok yüksek bir sayı, bir tür veya yöntemin çok fazla iş gerçekleştirmeye çalıştığını ve bölünmesi gerektiğini gösterebilir. Ayrıca tür veya yöntemin sürdürmek zor olabileceğini de gösterebilir.

## <a name="anonymous-methods"></a>Anonim Yöntemler
 *Anonim yöntem* yalnızca adı olmayan bir yöntemdir. Anonim yöntemler en sık, bir kod bloğunu temsilci parametresi olarak geçirmek için kullanılır. Yöntem veya erişimci gibi bir üyede belirtilen anonim bir yöntemin ölçüm sonuçları, yöntemi bildiren üyeyle ilişkilendirilir. Bu, yöntemi çağıran üyeyle ilişkili değildir.

 Kod ölçümlerinin anonim yöntemlere nasıl davrandığı hakkında daha fazla bilgi için bkz. [Anonim yöntemler ve kod analizi](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Oluşturulan kod
 Bazı yazılım araçları ve derleyiciler, bir projeye eklenen ve proje geliştiricisinin değiştirmediğinden veya değişmediğinden emin olan kodu oluşturur. Genellikle, kod ölçümleri ölçüm değerlerini hesaplarken oluşturulan kodu yoksayar. Bu, ölçüm değerlerinin geliştiricinin neleri görebileceğini ve değiştirebileceklerini yansıtmalarını sağlar.

 Windows Forms için oluşturulan kod, geliştiricinin görebileceği ve değiştirebildiğinden kod olduğundan yok sayılır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
