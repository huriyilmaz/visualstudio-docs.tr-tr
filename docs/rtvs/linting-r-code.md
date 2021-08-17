---
title: R kodu linting
description: Lint seçenekleri Visual Studio R için derleme lint desteğiyle çalışma.
ms.date: 07/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 7a278c5ad35b31bd5c0606d64a9fb16d03534229
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075924"
---
# <a name="lint-r-code-in-visual-studio"></a>Visual Studio'de Lint R kodu

Linter olası hataları, biçimlendirme sorunlarını ve kötü amaçlı boşluk gibi diğer kod kirliliğini ortaya çıkarmak için kodu analiz eder. Linter kullanmak, tanımlayıcıların nasıl adlandırılmış olduğu gibi belirli kodlama kurallarına teşvik etmek için de yardımcı olur. Bu tür kuralların ekipler ve işbirliğine dayalı diğer durumlar için faydalı olduğu durumlar vardır.

Visual Studio için R Araçları (RTVS), R için yerleşik bir linter sağlar. Bu, davranışı bu makalede açıklanan çeşitli seçenekler aracılığıyla denetlenmektedir. Bu seçenekler Araçlar Seçenekler Metin **Düzenleyici**  >    >    >  **R**  >  **Lint içinde bulunur.**

Lint varsayılan olarak devre dışıdır. Lint'i etkinleştirmek için Tüm  >  **Lint etkinleştir seçeneğini** True olarak **ayarlayın.**

Etkinleştirildiğinde, siz yazarak linter düzenleyicide çalışır. Sorunlar yeşil geçişler olarak görünür. Aşağıdaki grafikte RTVS atama yerine yerine kullanımı, işlev bağımsız değişkenlerinin çevresinde boşluk olmaması, Pascal büyük/küçük harf ve büyük harf tanımlayıcılarının kullanımı ve noktalı virgül kullanımı gibi altı lint sorunu tespit `=` `<-` etti. Bir sorunun üzerine gelindiğinde bir açıklama yer alır.

![R kodu için linter çıkışı örnekleri](media/linting-01.png)

Linter seçeneklerini genellikle bir projenin veya dosyanın gereksinimlerine bağlı olarak değiştirirsiniz. Örneğin, çevrimiçi bir kurstan alınan örnek kod, `=` `<-` Pascal-case tanımlayıcıları yerine kullanabilir. Varsayılan linter seçenekleri bu tür durumlara bayrak asma nedeniyle bu tür kodlar sık sık linter uyarıları gösterir. Bu kodla çalışırken, her örneği düzeltmek için zaman harcamak yerine seçenekleri devre dışı abilirsiniz.

## <a name="assignment-group"></a>Atama grubu

| Seçenek | Varsayılan değer | Lint etkisi |
| --- | --- | --- |
| **Zorlamak \<-** | **True** | Atama `<-` için kullanılmama zamanlarını tanımlar. |

## <a name="naming-group"></a>Adlandırma grubu

Bu seçenekler farklı adlandırma kuralları kullanan tanımlayıcıları bayrakla belirtir:

| Seçenek | Varsayılan değer | Lint etkisi |
| --- | --- | --- |
| **camelCase bayrağı** | **False** | camelCase kullanan tanımlayıcıları bayraklar. |
| **Uzun adları bayrakla bayrakla bayrakla** | **False** | Adları En fazla ad uzunluğu ayarını aşan **tanımlayıcıları bayraklar.** |
| **Birden çok noktaya bayrak** | **True** | Birden çok nokta kullanan tanımlayıcıları bayraklar. |
| **PascalCase bayrağı** | **True** | PascalCase kullanan tanımlayıcıları bayraklar. |
| **Bayrak snake_case** | **False** | Alt çizgi kullanan tanımlayıcıları bayraklar. |
| **BÜYÜK HARF bayrağı** | **True** | Tüm uçları kullanan tanımlayıcıları bayraklar. |
| **Maksimum ad uzunluğu** | **32** | Uzun adlar bayrağı **ayarıyla uygulanan** uzunluk. |

## <a name="spacing-group"></a>Aralık grubu

Varsayılan olarak **True** olarak ayarlanmış olan bu seçenekler, linter'ın boşluk sorunlarını nerede tanımları olduğunu kontrol edin: işlev adlarının ardından, virgüller çevresinde, işleçler çevresinde, küme konumlarını açma ve kapatma, önceki boşluk (ve içindeki boşluk () .

## <a name="statements-group"></a>Deyimler grubu

| Seçenek | Varsayılan değer | Lint etkisi |
| --- | --- | --- |
| **Birden çok** | **True** | Birden çok deyimin aynı satırda olduğunu tanımlar. |
| **Noktalı virgül** | **True** | Noktalı virgül kullanımlarını tanımlar. |

## <a name="text-group"></a>Metin grubu

| Seçenek | Varsayılan değer | Lint etkisi |
| --- | --- | --- |
| **Satır uzunluğu sınırı** | **False** | Linter'ın satırları Maksimum satır uzunluğu seçeneğinden daha uzun **olarak işaretleyin.** |
| **En fazla satır uzunluğu** | **80** | Satır uzunluğu sınırı seçeneği tarafından **uygulanan satır uzunluğunu** ayarlar. |

## <a name="whitespace-group"></a>Boşluk grubu

Varsayılan olarak True olarak ayarlanmış  olan bu seçenekler, linter'ın boşluk sorunlarını tanımlarını kontrol etmek için kullanılır: sekme kullanımı, çift tırnak kullanımı, sonda boş satırlar ve sonda boşluk.