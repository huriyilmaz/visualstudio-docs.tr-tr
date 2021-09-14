---
title: Standart kod analizi iade ilkelerini oluşturma/güncelleştirme
description: Kod analizinin bir Azure DevOps projesinde tüm kod projelerinde çalıştırıla Azure DevOps öğrenin. Bkz. Proje kodu analizi iade ilkesi yapılandırma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 70442184ae7a8ce36657ce9c2dbc8887f9d3b9e7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631970"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Nasıl yapılır: Standart Kod Çözümleme İade İlkeleri Oluşturma veya Güncelleme

Kod analizi iade ilkesi kullanılarak bir Azure DevOps projesinde tüm kod projelerinde kod analizinin çalışmasına gerek vardır. Kod analizi gerektirerek kod tabanına iade olan kodun kalitesini geliştirebilirsiniz.

> [!NOTE]
> Bu özellik yalnızca Team Foundation Server.

Kod analizi iade ilkeleri proje ayarlarında ayarlanır ve her kod projesine uygulanır. Kod analizi çalıştırmaları, kod projesinin proje (.xxproj) dosyasındaki kod projeleri için yapılandırılır. Kod analizi çalıştırmaları yerel bilgisayarda gerçekleştirilir. Bir kod analizi iade ilkesi etkinleştirdikten sonra, iade edilen bir kod projesinde yer alan dosyaların son düzenlemelerinden sonra derlenmiş olması ve en azından proje ayarlarındaki kuralların değişikliklerin yapılmış olduğu bilgisayarda gerçekleştiriliyor olması gerekir.

- Yönetilen kod için, kod analizi kurallarının bir alt kümesini içeren bir *kural kümesi* belirterek iade ilkesi ayarlayın.

- C/C++ kodu için, Visual Studio 2017 sürüm 15.6 ve önceki sürümlerde iade ilkesi tüm kod analizi kurallarının çalıştırnmalarını gerektirir. Ön işlemci yönergelerini, tek tek kod projeleri için belirli kuralları devre dışı bırakmak için ön işlemci yönergeleri Azure DevOps ebilirsiniz. 15.7 ve üzerinde çalıştıracak kuralları belirtmek için **/analyze:ruleset** kullanabilirsiniz. Daha fazla bilgi için, [bkz. Using Rule Sets to Specify the C++ Rules to Run](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

Yönetilen kod için bir iade ilkesi belirttikten sonra, takım üyeleri kod projeleri için kod analizi ayarlarını proje ilkesi Azure DevOps eşitler.

## <a name="to-open-the-check-in-policy-editor"></a>Iade ilke düzenleyicisini açmak için

1. Bu Takım Gezgini proje adına sağ tıklayın, öğesinin üzerine **gelin ve Project Ayarlar** Denetimi'ne **tıklayın.**

1. Kaynak **Denetimi iletişim** kutusunda, Iade İlkesi **sekmesini** seçin.

1. Aşağıdakilerden birini yapın:

    - Yeni **bir** iade ilkesi oluşturmak için Ekle'ye tıklayın.

    - İlkeyi değiştirmek **için Code Analysis** Türü listesinde var **olan** yeni öğeye çift tıklayın.

## <a name="to-set-policy-options"></a>İlke seçeneklerini ayarlamak için

Aşağıdaki seçenekleri belirleyin veya silin:

|Seçenek|Açıklama|
|------------|-----------------|
|**Yalnızca geçerli çözümün parçası olan dosyaları içermek için iadeyi zorunlu kılın.**|Kod analizi yalnızca çözüm ve proje yapılandırma dosyalarında belirtilen dosyalarda çalışmasına neden olabilir. Bu ilke, bir çözümün parçası olan tüm kodun analiz edilir.|
|**C/C++ Code Analysis zorlama (/analiz)**|Tüm C veya C++ projelerinin iade için kod analizini çalıştırmak için /analyze derleyici seçeneğiyle derlenmiş olması gerekir.|
|**Yönetilen Code Analysis için uygulama uygulama**|Tüm yönetilen projelerin iade için kod analizi ve derleme çalıştırması gerekir.|

## <a name="to-specify-a-managed-rule-set"></a>Yönetilen kural kümesi belirtmek için

Bu **kuralı çalıştır kümesi listesinden** aşağıdaki yöntemlerden birini kullanın:

- Bir Microsoft standart kural kümesi seçin.

- seçeneğine tıklayarak bir özel kural kümesi **\<Select Rule Set from Source Control...>** seçin. Ardından kaynak denetim tarayıcısında kural kümesi sürüm denetim yolunu yazın. Sürüm denetim yolunun söz dizimi şöyledir:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Özel iade ilkesi kural kümesi oluşturma ve uygulama hakkında daha fazla bilgi için bkz. Yönetilen Kod için [Özel Iade İlkeleri Uygulama.](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Kod için Özel Kod Analizi İade İlkelerini Uygulama](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
