---
title: Metin Şablonlarının Güvenliği
description: Rastgele kod ve kötü amaçlı yönerge işlemcileri gibi konular da dahil olmak üzere güvenlik ve metin şablonları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11352eb33070d3401516948cc01c4b9bd7ab4f95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893327"
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
