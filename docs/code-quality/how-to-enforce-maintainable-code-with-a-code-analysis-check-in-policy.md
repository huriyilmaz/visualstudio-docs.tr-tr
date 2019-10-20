---
title: Kod Analizi iade etme ilkesi kullanma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b5a165d2f0f3c17a91775d2d37eadf32307d248
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649420"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Nasıl yapılır: bir kod çözümleme iade ilkesiyle sürdürülebilir kodu zorlama

Geliştiriciler, kodunuzun karmaşıklığını ve bakımlarını ölçmek için kod ölçümleri aracını kullanabilir, ancak iade ilkesinin bir parçası olarak kod ölçümlerini çağıramazsınız. Bununla birlikte, kod ölçüm standartları ile kodunuzun uyumluluğunu doğrulayan kod analizi kurallarını etkinleştirebilir ve bu kuralları iade ilkeleri aracılığıyla zorunlu kılabilirsiniz. Kod ölçümleri hakkında daha fazla bilgi için bkz. [Kod ölçümleri değerleri](../code-quality/code-metrics-values.md).

Bir kod analizi iade ilkesi aracılığıyla sürdürülebilir kodu zorlamak için devralma, sınıf bağlantısı, bakım dizini ve karmaşıklık kuralları derinliğini etkinleştirebilirsiniz. Bu kuralların dört bölümü, kod analizi ilke düzenleyicisinde "Bakımkuralı kuralları" kategorisinde bulunur.

Team Foundation için sürüm denetimi yöneticileri, iade ilkesi gereksinimlerine kod analizi bakım kuralları ekleyebilir. Bu iade ilkeleri, geliştiricilerin bir iade başlatmadan önce Bu kural değişikliklerini temel alan kod analizini çalıştırmasını gerektirir.

## <a name="to-open-the-code-analysis-policy-editor"></a>Kod Analizi Ilke düzenleyicisini açmak için

1. **Takım Gezgini**, projeye sağ tıklayın, **proje ayarları**' na tıklayın ve ardından **kaynak denetimi**' ne tıklayın.

     **Kaynak denetimi** iletişim kutusu görüntülenir.

2. **Iade ilkesi** sekmesinde, **Ekle**' ye tıklayın.

     **Iade Ilkesi Ekle** iletişim kutusu görünür.

3. **Iade ilkesi** listesinde, **Kod Analizi** onay kutusunu seçin ve ardından **Tamam**' a tıklayın.

     **Kod Analizi Ilke Düzenleyicisi** iletişim kutusu görüntülenir.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Kod Analizi bakım kurallarını etkinleştirmek için

1. **Kod Analizi Ilke Düzenleyicisi** iletişim kutusunda, **Kural ayarları**' nın altında, bakım **kuralları** düğümünü genişletin.

2. Aşağıdaki kuralların onay kutularını seçin:

   - Devralma derinliği: **CA1501 AvoidExcessiveInheritance** -Threshold: 5 düzeyden daha derin bir uyarı

   - Karmaşıklık: **CA1502 AvoidExcessiveComplexity** -Threshold: 25 ' ten fazla uyarı

   - Bakım dizini: **CA1505 AvoidUnmaintainableCode** -Threshold: 20 ' den az uyarı

   - Sınıf bağlantısı: **CA1506 AvoidExcessiveClassCoupling** -Threshold: bir sınıf için 80 ' den fazla uyarı ve bir yöntem için 30 ' dan fazla uyarı

     Ayrıca, başarılı bir derlemeyi engellemek için bir kural ihlalini isterseniz, kural açıklamasının yanındaki **uyarıyı hata olarak işle** onay kutusunu seçin.

3. **Tamam**'a tıklayın. Yeni iade ilkesi artık gelecek iadeler için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod ölçüm değerleri](../code-quality/code-metrics-values.md)
- [Kod Analizi iade ilkeleri oluşturma ve kullanma](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
