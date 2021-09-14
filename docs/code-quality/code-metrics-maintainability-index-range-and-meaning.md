---
title: Kod ölçümleri - Bakım dizin aralığı ve anlamı
ms.date: 1/8/2021
description: Visual Studio'da kod ölçümleri için bakım dizin aralığı ölçümü hakkında Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 8ab6115dd0c0a17bf6bb302d7c160e969d11773e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632061"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Kod ölçümleri - Bakım dizin aralığı ve anlamı

Soru: Bakım dizini 0 ile 100 arasında olacak şekilde sıfırlandı. Bu nasıl ve neden yapıldı?

Ölçüm başlangıçta aşağıdaki gibi hesaplanmıştır: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

Bu formülün kullanımı 171 ile sınırsız negatif sayı arasında olduğu anlamına geliyor.  Kod 0'a doğru ilerler ve kodun 0 ile bazı negatif değerleri arasındaki farkı korumak oldukça zordur.  Negatif sayıların kullanışlılığının azaltılmasının ve ölçümü mümkün olduğunca net tutma isteğinin bir sonucu olarak, 0 veya daha az dizinin hepsini 0 olarak işleye karar verdik ve ardından 171 veya daha az aralığı 0 ile 100 arasında olacak şekilde yeniden tabanına yeniden sildik. Bu nedenle formül şu şekildedir:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Buna ek olarak eşiklerle birlikte tutucu olmaya karar verdik.  Dizin kırmızı gösterse kodla ilgili bir sorun olduğunu yüksek derecede güven derecesiyle ifade etmek istiyoruz.  Bu bize aşağıdaki eşikleri verdi:

Eşikler için, gürültü düzeyini düşük tutmak için bu 0-100 aralığını 80-20 arasında kesmeye karar verdik ve yalnızca şüpheli olan kodu işaretledık. Aşağıdaki eşikleri kullandık:

- 0-9 = Kırmızı
- 10-19 = Sarı
- 20-100 = Yeşil
