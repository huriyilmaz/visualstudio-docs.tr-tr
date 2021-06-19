---
title: Metin Şablonlarının Güvenliği
description: Rastgele kod ve kötü amaçlı yönerge işlemcileri gibi konular da dahil olmak üzere güvenlik ve metin şablonları hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a740a6f7a4c532a61a5e412c94fa4321c5da707
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385766"
---
# <a name="security-of-text-templates"></a>Metin Şablonlarının Güvenliği
Metin şablonlarının güvenlikle ilgili sorunları vardır:

- Metin şablonları rastgele kod eklemelere karşı savunmasızdır.

- Ana bilgisayar tarafından bir yönerge işlemcisi bulmak için kullanan mekanizma güvenli değildir, kötü amaçlı bir yönerge işlemcisi çalıştırmak olabilir.

## <a name="arbitrary-code"></a>Rastgele Kod
 Şablon yazarak etiketlerin içine herhangi bir kod \<# #> koyabilirsiniz. Bu, bir metin şablonundan rastgele kodun yürütülltülür.

 Güvenilir kaynaklardan şablon edin edindiğinizden emin olun. Uygulamanın son kullanıcılarını güvenilir kaynaklardan gelen şablonları yürütmeleri konusunda uyarmamaya emin olun.

## <a name="malicious-directive-processor"></a>Kötü Amaçlı Yönerge İşlemcisi
 Metin şablonu altyapısı bir dönüştürme ana bilgisayarı ve bir veya daha fazla yönerge işlemcisi ile etkileşim kurarak şablon metnini bir çıkış dosyasına dönüştürmektedir. Daha fazla bilgi için [bkz. Metin Şablonu Dönüştürme İşlemleri.](../modeling/the-text-template-transformation-process.md)

 Ana bilgisayar tarafından bir yönerge işlemcisini bulmak için kullanan mekanizma güvenli değildir, kötü amaçlı yönerge işlemcisi çalıştırma riskini çalıştırır. Kötü amaçlı yönerge işlemcisi, şablon çalıştır olduğunda `FullTrust` modunda çalıştıran kod sağlar. Özel bir metin şablonu dönüştürme ana bilgisayarı oluşturursanız, altyapının yönerge işlemcilerini bulması için kayıt defteri gibi güvenli bir mekanizma kullansanız gerekir.
