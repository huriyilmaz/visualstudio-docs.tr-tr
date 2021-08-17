---
title: Kod analizi iade ilkesi kullanma
ms.date: 11/04/2016
description: Kodun devralma, sınıf eşleştirme, bakım ve karmaşıklık standartlarına uygun olduğunu doğrulamak için kod analizi iade ilkesi kullanmayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091311"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Nasıl olur: Kod analizi iade ilkesiyle korunabilir kodu zorlama

Geliştiriciler kodlarının karmaşıklığını ve sürdürülebilirliğini ölçmek için Kod Ölçümleri aracını kullanabilir ancak iade ilkesi kapsamında Kod Ölçümlerini çağıramaz. Bununla birlikte, Code Analysis ölçüm standartlarıyla uyumluluğunu doğrular ve iade ilkeleri aracılığıyla kuralları zorunlu bulunduran kurallar etkinleştirebilirsiniz. Kod ölçümleri hakkında daha fazla bilgi için [bkz. Kod ölçümleri değerleri.](../code-quality/code-metrics-values.md)

Devralma Derinliği, Sınıf Eşleştirmesi, Bakım Dizini ve Karmaşıklık kurallarını etkinleştirerek bir iade ilkesi aracılığıyla sürdürülebilir Code Analysis zorabilirsiniz. Bu kuralların dördü de ilke düzenleyicisinin "Bakım Kuralları" kategorisinde Code Analysis bulunur.

Team Foundation için sürüm denetimi yöneticileri, Code Analysis ilkesi gereksinimlerine Bakım Kuralları'nın gereksinimlerini ekleyebilir. Bu iade ilkeleri, geliştiricilerin bir iade Code Analysis önce bu kural değişikliklerine göre değişikliklerini çalıştırmalarını gerektirir.

## <a name="to-open-the-code-analysis-policy-editor"></a>Code Analysis İlkesi düzenleyicisini açmak için

1. Içinde **Takım Gezgini,** projeye sağ tıklayın, Project Ayarlar **ve** ardından Kaynak **Denetimi'ne tıklayın.**

     Kaynak **Denetimi iletişim** kutusu görüntülenir.

2. Iade **İlkesi sekmesinde Ekle'ye** **tıklayın.**

     Iade **İlkesi Ekle iletişim** kutusu görüntülenir.

3. **İlkeyi Iade Edin listesinde,** İlkeler **onay Code Analysis** ve ardından Tamam'a **tıklayın.**

     İlke **Code Analysis Düzenleyici** iletişim kutusu görüntülenir.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Kod analizi bakım kurallarını etkinleştirmek için

1. İlke **Code Analysis iletişim kutusundaki** Kural Ayarlar **altında** Bakım Kuralları **düğümünü** genişletin.

2. Aşağıdaki kuralların onay kutularını seçin:

   - Devralma Derinliği: **CA1501 AvoidExcessiveInheritance** - Eşik: 5'den fazla derin düzeyde uyarı

   - Karmaşıklık: **CA1502 AvoidExcessiveComplexity** - Eşik: 25'in üzerinde uyarı

   - Bakım Dizini: **CA1505 AvoidUnmaintainableCode** - Eşik: 20'den az uyarı

   - Sınıf Bağlantısı: **CA1506 AvoidExcessiveClassCoupling** - Eşik: Bir sınıf için 80'den fazla ve bir yöntem için 30'dan fazla uyarı

     Ayrıca, başarılı bir derlemeyi önlemek için bir kural  ihlali yapmak istemiyorsanız, kural açıklamasının yanındaki Uyarıyı Hata Olarak Davran onay kutusunu seçin.

3. **Tamam**'a tıklayın. Yeni iade ilkesi artık gelecekteki iadeler için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod ölçümleri değerleri](../code-quality/code-metrics-values.md)
- [Kod analizi iade ilkelerini oluşturma ve kullanma](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
