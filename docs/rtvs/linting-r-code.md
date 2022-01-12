---
title: R kodu
description: kter seçenekleri de dahil olmak üzere R için Visual Studio derleme desteğiyle çalışma.
ms.date: 07/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: beeee863cec001eb78f1eba7c18488d65b418178
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135751035"
---
# <a name="lint-r-code-in-visual-studio"></a>Visual Studio LINT R kodu

Bir şifre, olası hataları, biçimlendirme sorunlarını ve sursuz boşluk gibi diğer kod gürültülerini ortaya çıkarmak için kodu analiz eder. Bir lter kullanılması, tanımlayıcıların nasıl adlandırıldığı gibi belirli kodlama kurallarının da sağlanmasına yardımcı olur. Bu tür kurallar takımlar ve diğer işbirliği durumları içinde faydalıdır.

Visual Studio için R Araçları (rtvs), bu makalede açıklanan çeşitli seçeneklerle denetlenen, R için yerleşik bir yerleşik olarak sunulur. Bu seçenekler **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **R**  >  **Lint**' te bulunur.

LINT varsayılan olarak devre dışıdır. Lint 'i etkinleştirmek için, **Tüm**  >  **Enable Lint** seçeneğini **true** olarak ayarlayın.

Etkinleştirildiğinde, bir düzenleyici, yazarken düzenleyicide çalışır. Sorunlar yeşil dalgalı çizgiler gibi görünür. Aşağıdaki grafikte, örneğin, RTVS, `=` `<-` atama için yerine kullanılması, işlev bağımsız değişkenlerinde boşluk olmaması, Pascal büyük/küçük harf tanımlayıcıları kullanımı ve noktalı virgülden kullanımı dahil olmak üzere altı LINT sorunu tanımlamıştır. Bir sorunun üzerine gelindiğinde bir açıklama sağlanır.

![R kodu için kodsuz çıkış örnekleri](media/linting-01.png)

Genellikle bir proje ya da dosyanın ihtiyaçlarına bağlı olarak, bu seçenekleri değiştirirsiniz. Örneğin, çevrimiçi bir kursta örnek kod, `=` `<-` Pascal-case tanımlayıcılarıyla birlikte yerine kullanılabilir. Bu tür kodlar, bu durumları işaret ettiğinden sık kullanılan uyarıları gösterir. Bu kodla çalışırken, her örneği düzeltme süresini harcama yerine seçenekleri devre dışı bırakabilirsiniz.

## <a name="assignment-group"></a>Atama grubu

| Seçenek | Varsayılan değer | LINT efekti |
| --- | --- | --- |
| **Zorlamayı \<-** | **True** | `<-`Atama için ne zaman kullanılmadığını tanımlar. |

## <a name="naming-group"></a>Adlandırma grubu

Bu seçenekler, farklı adlandırma kuralları kullanan tanımlayıcılara bayrak ekleyin:

| Seçenek | Varsayılan değer | LINT efekti |
| --- | --- | --- |
| **CamelCase 'i işaretle** | **False** | CamelCase kullanan bayraklar tanımlayıcıları. |
| **Uzun adları işaretle** | **False** | Adları **en büyük ad uzunluğu** ayarını aşan bayrak tanımlayıcıları. |
| **Birden çok noktaya bayrak Ekle** | **True** | Birden çok nokta kullanan bayraklar tanımlayıcıları. |
| **PascalCase 'i işaretle** | **True** | PascalCase kullanan bayraklar tanımlayıcıları. |
| **Bayrak snake_case** | **False** | Alt çizgi kullanan bayraklar tanımlayıcıları. |
| **BÜYÜK harf işareti** | **True** | Tüm Cap 'leri kullanan bayraklar tanımlayıcıları. |
| **En fazla ad uzunluğu** | **32** | **Uzun adları işaretle** ayarıyla uygulanan uzunluk. |

## <a name="spacing-group"></a>Aralık grubu

Hepsi varsayılan olarak **true** olarak ayarlanan bu seçenekler, her birinin boşluk sorunlarını belirlediği yerleri denetler: işlev adlarından sonra, işlecin etrafında, büyük konumlarda boşluk, açma ve kapatma, kaşlı konumlar, (ve içinde boşluk).

## <a name="statements-group"></a>Deyim grubu

| Seçenek | Varsayılan değer | LINT efekti |
| --- | --- | --- |
| **Birden çok** | **True** | Aynı satırda birden çok deyim olduğunu tanımlar. |
| **Noktalı virgülle** | **True** | Noktalı virgüllerle kullanımları tanımlar. |

## <a name="text-group"></a>Metin grubu

| Seçenek | Varsayılan değer | LINT efekti |
| --- | --- | --- |
| **Satır uzunluğu sınırı** | **False** | Lint aracıdır 'ın çizgileri **en fazla satır uzunluğu** seçeneğinden daha uzun olup olmayacağını ayarlar. |
| **En fazla satır uzunluğu** | **80** | Satır uzunluğu **sınırı** seçeneği tarafından uygulanan satır uzunluğunu ayarlar. |

## <a name="whitespace-group"></a>Boşluk grubu

Hepsi varsayılan olarak **true** olarak ayarlanan bu seçenekler, her birinin boşluk sorunlarını tanımladığı konumu denetler: sekmelerin kullanımı, çift tırnak işareti, sondaki boş satırlar ve sondaki boşluk.