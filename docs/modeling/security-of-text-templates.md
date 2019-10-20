---
title: Metin Şablonlarının Güvenliği
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eab987d406d6a2c05c8350aaac9dd1ecfc13e4a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660084"
---
# <a name="security-of-text-templates"></a>Metin Şablonlarının Güvenliği
Metin şablonlarında aşağıdaki güvenlik sorunları vardır:

- Metin şablonları rastgele kod ekleme işlemlerine açıktır.

- Konağın bir yönerge işlemcisini bulmak için kullandığı mekanizma güvenli değilse, kötü amaçlı yönerge işlemcisi çalıştırılabilir.

## <a name="arbitrary-code"></a>Rastgele kod
 Bir şablon yazdığınızda, \< # # > etiketleri içinde herhangi bir kod yerleştirebilirsiniz. Bu, bir metin şablonu içinden rastgele kodun yürütülmesini sağlar.

 Güvenilen kaynaklardan şablonlar aldığınızdan emin olun. Uygulamanızın son kullanıcılarını, güvenilir kaynaklardan gelmeyen şablonları yürütmek için not aldığınızdan emin olun.

## <a name="malicious-directive-processor"></a>Kötü amaçlı yönerge Işlemcisi
 Metin şablonu altyapısı bir dönüştürme konağından ve şablon metnini bir çıkış dosyasına dönüştürmek için bir veya daha fazla yönerge işlemcisi ile etkileşime girer. Daha fazla bilgi için bkz. [metin şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md).

 Konağın bir yönerge işlemcisini bulmak için kullandığı mekanizma güvenli değilse, kötü amaçlı yönerge işlemcisi çalıştırma riskini çalıştırır. Kötü amaçlı yönerge işlemcisi, şablon çalıştırıldığında `FullTrust` modunda çalışan bir kod sağlayabilir. Özel bir metin şablonu dönüştürme Konağı oluşturursanız, yönerge işlemcileri bulmak için altyapının kayıt defteri gibi güvenli bir mekanizma kullanmanız gerekir.