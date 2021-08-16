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
ms.openlocfilehash: 5149f1620fb371bb13b09566b38001cb35cd4da72871cb404a325c076a1619a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264941"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Kod ölçümleri - Bakım dizin aralığı ve anlamı

Soru: Bakım dizini 0 ile 100 arasında olacak şekilde sıfırlandı. Bu nasıl ve neden yapıldı?

Ölçüm başlangıçta aşağıdaki gibi hesaplanmıştır: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

Bu formülün kullanımı 171 ile sınırsız negatif sayı arasında olduğu anlamına geliyor.  Kod 0'a doğru ilerler ve kodun 0 ile bazı negatif değerleri arasındaki farkı korumak oldukça zordur.  Negatif sayıların kullanışlılığını azaltmanın ve ölçümü mümkün olduğunca net tutma isteğinin bir sonucu olarak, 0 veya daha az dizinin hepsini 0 olarak işleye karar verdik ve ardından 171 veya daha az aralığı 0 ile 100 arasında olacak şekilde yeniden tabanına yeniden sildik. Bu nedenle formül şu şekildedir:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Buna ek olarak eşiklerle birlikte tutucu olmaya karar verdik.  Dizin kırmızı gösterse kodla ilgili bir sorun olduğunu yüksek derecede güven derecesiyle ifade etmek istiyoruz.  Bu bize aşağıdaki eşikleri verdi:

Eşikler için bu 0-100 aralığını 80-20 aralığında kesmeye karar verdik ve yalnızca şüpheli olan kodu işaretledık. Aşağıdaki eşikleri kullandık:

- 0-9 = Kırmızı
- 10-19 = Sarı
- 20-100 = Yeşil
