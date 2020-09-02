---
title: Metin Şablonlarının Güvenliği
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25815bcb7f027501fb849dcd29d14b040c24d7fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591976"
---
# <a name="security-of-text-templates"></a>Metin Şablonlarının Güvenliği
Metin şablonlarında aşağıdaki güvenlik sorunları vardır:

- Metin şablonları rastgele kod ekleme işlemlerine açıktır.

- Konağın bir yönerge işlemcisini bulmak için kullandığı mekanizma güvenli değilse, kötü amaçlı yönerge işlemcisi çalıştırılabilir.

## <a name="arbitrary-code"></a>Rastgele kod
 Bir şablon yazdığınızda, etiketleri içine herhangi bir kod yerleştirebilirsiniz \<# #> . Bu, bir metin şablonu içinden rastgele kodun yürütülmesini sağlar.

 Güvenilen kaynaklardan şablonlar aldığınızdan emin olun. Uygulamanızın son kullanıcılarını, güvenilir kaynaklardan gelmeyen şablonları yürütmek için not aldığınızdan emin olun.

## <a name="malicious-directive-processor"></a>Kötü amaçlı yönerge Işlemcisi
 Metin şablonu altyapısı bir dönüştürme konağından ve şablon metnini bir çıkış dosyasına dönüştürmek için bir veya daha fazla yönerge işlemcisi ile etkileşime girer. Daha fazla bilgi için bkz. [metin şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md).

 Konağın bir yönerge işlemcisini bulmak için kullandığı mekanizma güvenli değilse, kötü amaçlı yönerge işlemcisi çalıştırma riskini çalıştırır. Kötü amaçlı yönerge işlemcisi, şablon çalıştırıldığında modda çalışan bir kod sağlayabilir `FullTrust` . Özel bir metin şablonu dönüştürme Konağı oluşturursanız, yönerge işlemcileri bulmak için altyapının kayıt defteri gibi güvenli bir mekanizma kullanmanız gerekir.
