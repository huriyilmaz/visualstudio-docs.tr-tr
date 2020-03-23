---
title: Linting R kodu
description: Visual Studio'nun r için geliştirme linting desteği ile nasıl çalışılır, linter seçenekleri de dahil olmak üzere.
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: aecf9d95fb8a3b2cda659e2694bff145424e150b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970750"
---
# <a name="lint-r-code-in-visual-studio"></a>Visual Studio'da Lint R kodu

Linter, olası hataları, biçimlendirme sorunlarını ve sahte beyaz alan gibi diğer kod gürültüsünü ortaya çıkarmak için kodu analiz eder. Linter kullanmak, tanımlayıcıların nasıl adverildiği gibi belirli kodlama kurallarını da teşvik eder. Bu tür sözleşmeler takımlar ve diğer işbirlikçi durumlarda yararlıdır.

R Tools for Visual Studio (RTVS), bu makalede açıklanan çeşitli seçenekler aracılığıyla kontrol edilen R için yerleşik bir linter sağlar. Bu seçenekler **Araçlar** > **Seçenekleri** > Metin**Editörü** > **R** > **Lint**bulunur.

Tiftik varsayılan olarak devre dışı bırakılır. Tiftik etkinleştirmek **için, True için** >  **True**Tüm**Etkinleştir metif** seçeneğini ayarlayın.

Etkinleştirildiğinde, siz yazarken linter düzenleyicide çalışır. Sorunlar yeşil dalgalı olarak görünür. Aşağıdaki grafikte, örneğin, RTVS bir atama `=` yerine `<-` kullanımı, işlev bağımsız değişkenleri etrafında boşluk eksikliği, Pascal durumda ve büyük harf tanımlayıcıları kullanımı ve bir yarı nokta kullanımı da dahil olmak üzere altı tiftik sorunları belirlemiştir. Bir sorunun üzerinde gezinmek bir açıklama sağlar.

![R kodu için linter çıktı örnekleri](media/linting-01.png)

Genellikle bir proje veya dosyanın gereksinimlerine bağlı olarak linter seçeneklerini değiştirirsiniz. Örneğin, Pascal-case tanımlayıcıları yerine `=` çevrimiçi `<-` bir kurstan örnek kod kullanabilirsiniz. Varsayılan linter seçenekleri bu gibi durumlarda bayrak çünkü bu tür kod sık linter uyarıları gösterir. Bu kodla çalışırken, her örneği düzeltmek için zaman harcamak yerine seçenekleri devre dışı bırakabilirsiniz.

## <a name="assignment-group"></a>Atama grubu

| Seçenek | Varsayılan değer | Tiftik etkisi |
| --- | --- | --- |
| **Zorlamak\<-** | **True** | Atama `<-` için ne zaman kullanılmadığını tanımlar. |

## <a name="naming-group"></a>Adlandırma grubu

Bu seçenekler, farklı adlandırma kuralları kullanan tanımlayıcıları işaretleyin:

| Seçenek | Varsayılan değer | Tiftik etkisi |
| --- | --- | --- |
| **Bayrak camelCase** | **False** | CamelCase kullanan tanımlayıcıları bayraklar. |
| **Uzun adları işaretleme** | **False** | Adları **Max ad uzunluğu** ayarını aşan tanımlayıcıları bayraklar. |
| **Birden çok noktayı işaretleme** | **True** | Birden çok nokta kullanan tanımlayıcıları bayraklar. |
| **Bayrak PascalCase** | **True** | PascalCase kullanan tanımlayıcıları bayraklar. |
| **Bayrak snake_case** | **False** | Alt çizer kullanan bayraklar tanımlayıcıları. |
| **Bayrak BÜYÜK HARF** | **True** | Tüm kapakları kullanan tanımlayıcıları bayraklar. |
| **Maksimum ad uzunluğu** | **32** | **Bayrak uzun adlar** ayarı ile uygulanan uzunluk. |

## <a name="spacing-group"></a>Aralık grubu

Bu seçenekler, bunların tümü varsayılan olarak **True** olarak ayarlanır, linter'in boşluk sorunlarını tanımladığı yeri denetler: işlev adlarından sonra, virgüllerin etrafında, işleçlerin etrafında, kıvırcık konumları açma ve kapatma, önce boşluk (ve içindeki boşluk ()

## <a name="statements-group"></a>İfadeler grubu

| Seçenek | Varsayılan değer | Tiftik etkisi |
| --- | --- | --- |
| **Birden çok** | **True** | Birden çok deyimin aynı satırda ne zaman olduğunu tanımlar. |
| **Noktalı virgül** | **True** | Yarım kolon kullanımlarını tanımlar. |

## <a name="text-group"></a>Metin grubu

| Seçenek | Varsayılan değer | Tiftik etkisi |
| --- | --- | --- |
| **Çizgi uzunluğu sınırı** | **False** | Linter bayraklarının Max satır **uzunluğu** seçeneğinden daha uzun çizgiler olup olmadığını ayarlar. |
| **Maksimum çizgi uzunluğu** | **80** | **Satır uzunluğu sınırı** seçeneği tarafından uygulanan çizgi uzunluğunu ayarlar. |

## <a name="whitespace-group"></a>Beyaz uzay grubu

Hepsi varsayılan olarak **True** olarak ayarlanmış olan bu seçenekler, linter'in beyaz alan sorunlarını tanımladığı yeri denetler: sekmelerin kullanımı, çift tırnak kullanımı, boş satırları izleme ve beyaz alanı takip etme.