---
title: 'Nasıl yapılır: bir kod çözümleme Iade Ilkesiyle sürdürülebilir kodu zorlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660214"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Nasıl yapılır: Bir Kod Çözümleme İade İlkesi ile Bakımı Yapılabilir Kodu Zorlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geliştiriciler, kodunuzun karmaşıklığını ve bakımlarını ölçmek için kod ölçümleri aracını kullanabilir, ancak iade ilkesinin bir parçası olarak kod ölçümlerini çağıramazlar. Ancak, bir ekip kodun kod ölçüm standartlarıyla uyumluluğunu doğrulayan ve iade ilkeleri aracılığıyla kuralları uygulayan kod analizi kurallarını etkinleştirebilir. Kod ölçümleri hakkında daha fazla bilgi için bkz. [kod ölçüm değerleri](../code-quality/code-metrics-values.md).

 Geliştiriciler, kod analizi iade ilkeleri aracılığıyla sürdürülebilir kodu zorlamak için devralma, sınıf bağlantısı, bakım dizini ve karmaşıklık kurallarının derinliğini etkinleştirebilir. Bu kuralların dört bölümü, kod analizi ilke düzenleyicisinde "Bakımkuralı kuralları" kategorisinde bulunur.

 @No__t_0 için sürüm denetimi yöneticileri, iade etme ilkesi gereksinimlerine kod analizi bakım kuralları ekleyebilir. Bu iade ilkeleri, geliştiricilerin bir iade başlatmadan önce Bu kural değişikliklerini temel alan kod analizini çalıştırmasını gerektirir.

### <a name="to-open-the-code-analysis-policy-editor"></a>Kod Analizi Ilke düzenleyicisini açmak için

1. **Takım Gezgini**, takım projesine sağ tıklayın, **Takım Projesi Ayarları**' na tıklayın ve ardından **kaynak denetimi**' ne tıklayın.

     **Kaynak denetimi** iletişim kutusu görüntülenir.

2. **Iade ilkesi** sekmesinde, **Ekle**' ye tıklayın.

     **Iade Ilkesi Ekle** iletişim kutusu görünür.

3. **Iade ilkesi** listesinde, **Kod Analizi** onay kutusunu seçin ve ardından **Tamam**' a tıklayın.

     **Kod Analizi Ilke Düzenleyicisi** iletişim kutusu görüntülenir.

### <a name="to-enable-code-analysis-maintainability-rules"></a>Kod Analizi bakım kurallarını etkinleştirmek için

1. **Kod Analizi Ilke Düzenleyicisi** iletişim kutusunda, **Kural ayarları**' nın altında, bakım **kuralları** düğümünü genişletin.

2. Aşağıdaki kuralların onay kutularını seçin:

    - Devralma derinliği: **CA1501 AvoidExcessiveInheritance** -Threshold: 5 düzeyden daha derin bir uyarı

    - Karmaşıklık: **CA1502 AvoidExcessiveComplexity** -Threshold: 25 ' ten fazla uyarı

    - Bakım dizini: **CA1505 AvoidUnmaintainableCode** -Threshold: 20 ' den az uyarı

    - Sınıf bağlantısı: **CA1506 AvoidExcessiveClassCoupling** -Threshold: bir sınıf için 80 ' den fazla uyarı ve bir yöntem için 30 ' dan fazla uyarı

    - Ayrıca, bir derlemeyi engellemek için bir kural ihlalini isterseniz, kural açıklamasının yanındaki **uyarıyı hata olarak işle** onay kutusunu seçin.

3. **Tamam**'a tıklayın. Yeni iade ilkesi artık gelecek iadeler için geçerlidir.

## <a name="see-also"></a>Ayrıca Bkz.
 Kod [ölçüm değerleri](../code-quality/code-metrics-values.md) [Kod Analizi iade Ilkeleri oluşturma ve kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
