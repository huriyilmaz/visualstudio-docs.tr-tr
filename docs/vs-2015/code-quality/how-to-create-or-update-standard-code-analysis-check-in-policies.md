---
title: 'Nasıl yapılır: standart kod analizi Iade Ilkeleri oluşturma veya güncelleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8016032a0ea8d1b8c62b2dfc2bbdf72251590c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661773"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Nasıl yapılır: Standart Kod Çözümleme İade İlkeleri Oluşturma veya Güncelleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi iade etme ilkesini kullanarak, bir takım projesindeki tüm kod projelerinde kod analizinin çalıştırılmasını isteyebilirsiniz. Kod analizini zorunlu kılmak, kod tabanına işaretlenmiş kodun kalitesini iyileştirebilir.

> [!NOTE]
> Bu özellik yalnızca Team Foundation Server kullanıyorsanız kullanılabilir.

 Kod Analizi iade ilkeleri takım projesi ayarlarında ayarlanır ve takım projesindeki her bir kod projesi için geçerlidir. Kod Analizi çalıştırmaları, kod projesi için proje (. xxproj) dosyasındaki kod projeleri için yapılandırılır. Kod Analizi çalıştırmaları yerel bilgisayarda gerçekleştirilir. Bir kod analizi iade ilkesini etkinleştirdiğinizde, iade edilecek bir kod projesindeki dosyaların son Düzenlemeden sonra derlenmesi gerekir ve en azından içeren bir kod analizi çalıştıraldıktan sonra, değişikliklerin yapıldığı bilgisayarda takım projesi ayarlarındaki kuralların gerçekleştirilmesi gerekir.

- Yönetilen kod için, kod analizi kurallarının bir alt kümesini içeren bir *kural kümesi* belirterek iade ilkesini ayarlarsınız.

- C/C++ kodu için, iade ilkesi tüm kod analizi kurallarının çalıştırılmasını gerektirir. Takım projenizdeki bireysel kod projeleri için belirli kuralları devre dışı bırakmak üzere, ön işlemci yönergeleri ekleyebilirsiniz.

  Yönetilen kod için bir iade ilkesi belirttikten sonra, ekip üyeleri kod projeleri için kod analizi ayarlarını takım projesi ilkesi ayarlarına eşitleyebilir.

### <a name="to-open-the-check-in-policy-editor"></a>İade İlkesi düzenleyicisini açmak için

1. Takım Gezgini, takım projesi adına sağ tıklayın, **Takım Projesi Ayarları**' nın üzerine gelin ve **kaynak denetimi**' ne tıklayın.

2. **Kaynak denetimi** iletişim kutusunda, **iade ilkesi** sekmesini seçin.

3. Şunlardan birini yapın:

    - Yeni bir iade ilkesi oluşturmak için **Ekle** ' ye tıklayın.

    - İlkeyi değiştirmek için **Ilke türü** listesindeki mevcut **Kod Analizi** öğesine çift tıklayın.

### <a name="to-set-policy-options"></a>İlke seçeneklerini ayarlamak için

- Aşağıdaki seçenekleri seçin veya temizleyin:

    |Seçenek|Açıklama|
    |------------|-----------------|
    |**İade etme yalnızca geçerli çözümün parçası olan dosyaları içerecek şekilde zorla.**|Kod Analizi, yalnızca çözüm ve proje yapılandırma dosyalarında belirtilen dosyalarda çalıştırılabilir. Bu ilke, bir çözümün parçası olan tüm kodların çözümlenme garantisi sağlar.|
    |**C/C++ Kod analizini zorla (/Analyze)**|Tüm C veya C++ projelerinin, iade etmeden önce kod analizini çalıştırmak için/analyze derleyici seçeneğiyle birlikte oluşturulması gerekir.|
    |**Yönetilen kod için kod analizini zorla**|Tüm yönetilen projelerin, iade etmeden önce kod analizini ve derlemeyi çalıştırmasını gerektirir.|

-

### <a name="to-specify-a-managed-rule-set"></a>Yönetilen bir kural kümesi belirtmek için

- **Bu kural kümesini Çalıştır** listesinde, aşağıdaki yöntemlerden birini kullanın:

  - Bir Microsoft standart kural kümesi seçin.

  - Özel bir kural kümesi seçmek için, ' a tıklayın **\<Select Rule Set from Source Control...>** ve ardından kaynak denetimi tarayıcısına kural kümesinin sürüm denetim yolunu yazın. Sürüm denetimi yolunun sözdizimi şöyledir:

  - **$/** `TeamProjectName` **/** `VersionControlPath`

  - Özel bir iade ilkesi kural kümesi oluşturma ve uygulama hakkında daha fazla bilgi için bkz. [yönetilen kod Için özel Iade Ilkeleri uygulama](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod Analizi İade İlkeleri Oluşturma ve Kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
