---
title: Metin şablonlarının güvenliği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24a90d4e7af351fc4ba5807d2af7830edede9cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671221"
---
# <a name="security-of-text-templates"></a>Metin Şablonlarının Güvenliği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonlarında aşağıdaki güvenlik sorunları vardır:

- Metin şablonları rastgele kod ekleme işlemlerine açıktır.

- Konağın bir yönerge işlemcisini bulmak için kullandığı mekanizma güvenli değilse, kötü amaçlı yönerge işlemcisi çalıştırılabilir.

## <a name="arbitrary-code"></a>Rastgele kod
 Bir şablon yazdığınızda, \< # # > etiketleri içinde herhangi bir kod yerleştirebilirsiniz. Bu, bir metin şablonu içinden rastgele kodun yürütülmesini sağlar.

 Güvenilen kaynaklardan şablonlar aldığınızdan emin olun. Uygulamanızın son kullanıcılarını, güvenilir kaynaklardan gelmeyen şablonları yürütmek için not aldığınızdan emin olun.

## <a name="malicious-directive-processor"></a>Kötü amaçlı yönerge Işlemcisi
 Metin şablonu altyapısı bir dönüştürme konağından ve şablon metnini bir çıkış dosyasına dönüştürmek için bir veya daha fazla yönerge işlemcisi ile etkileşime girer. Daha fazla bilgi için bkz. [metin şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md).

 Konağın bir yönerge işlemcisini bulmak için kullandığı mekanizma güvenli değilse, kötü amaçlı yönerge işlemcisi çalıştırma riskini çalıştırır. Kötü amaçlı yönerge işlemcisi, şablon çalıştırıldığında `FullTrust` modunda çalışan bir kod sağlayabilir. Özel bir metin şablonu dönüştürme Konağı oluşturursanız, yönerge işlemcileri bulmak için altyapının kayıt defteri gibi güvenli bir mekanizma kullanmanız gerekir.
