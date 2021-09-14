---
title: Kod Analizi iade etme ilkesi kullanma
ms.date: 11/04/2016
description: Kodun devralma, sınıf bağlantısı, bakım ve karmaşıklık standartlarıyla uyumlu olduğunu doğrulamak için bir kod analizi iade ilkesi kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 4188a9d12daa5294e6771d3a1b4fc4a37b044521
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631958"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Nasıl yapılır: bir kod çözümleme iade ilkesiyle sürdürülebilir kodu zorlama

Geliştiriciler, kodunuzun karmaşıklığını ve bakımlarını ölçmek için kod ölçümleri aracını kullanabilir, ancak iade ilkesinin bir parçası olarak kod ölçümlerini çağıramazsınız. ancak, kod ölçüm standartları ile kodunuzun uyumluluğunu doğrulayan Code Analysis kuralları etkinleştirebilir ve bu kuralları iade ilkeleri aracılığıyla zorlayabilirsiniz. Kod ölçümleri hakkında daha fazla bilgi için bkz. [Kod ölçümleri değerleri](../code-quality/code-metrics-values.md).

Code Analysis bir iade ilkesi aracılığıyla sürdürülebilir kodu zorlamak için devralma, sınıf bağlantısı, bakım dizini ve karmaşıklık kuralları derinliğini etkinleştirebilirsiniz. bu kuralların dört bölümü, Code Analysis ilkesi düzenleyicisinde "bakımkuralı kuralları" kategorisinin altında bulunur.

Team Foundation için sürüm denetimi yöneticileri, iade ilkesi gereksinimlerine Code Analysis bakım kuralları ekleyebilir. bu iade ilkeleri, geliştiricilerin bir iade başlatmadan önce bu kural değişikliklerine göre Code Analysis çalıştırmasını gerektirir.

## <a name="to-open-the-code-analysis-policy-editor"></a>Code Analysis ilke düzenleyicisini açmak için

1. **Takım Gezgini**, projeye sağ tıklayın, **Project Ayarlar**' a ve ardından **kaynak denetimi**' ne tıklayın.

     **Kaynak denetimi** iletişim kutusu görüntülenir.

2. **Iade ilkesi** sekmesinde, **Ekle**' ye tıklayın.

     **Iade Ilkesi Ekle** iletişim kutusu görünür.

3. **iade ilkesi** listesinde **Code Analysis** onay kutusunu seçin ve ardından **tamam**' a tıklayın.

     **Code Analysis ilke düzenleyicisi** iletişim kutusu görüntülenir.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Kod Analizi bakım kurallarını etkinleştirmek için

1. **Code Analysis ilke düzenleyicisi** iletişim kutusunda, **kural Ayarlar** altında, bakım **kuralları** düğümünü genişletin.

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
