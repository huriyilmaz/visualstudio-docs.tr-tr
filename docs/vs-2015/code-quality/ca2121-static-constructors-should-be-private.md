---
title: 'CA2121: statik oluşturucular özel olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f95b33e1391ca755a6c0df261fa2bd05bd3c7a0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544319"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Statik oluşturucular özel olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Türün özel olmayan bir statik Oluşturucusu vardır.

## <a name="rule-description"></a>Kural Tanımı
 Sınıf oluşturucusu olarak da bilinen statik bir Oluşturucu, bir türü başlatmak için kullanılır. Sistem, türünün ilk örneğinin oluşturulmasından önce statik oluşturucuyu çağırır veya herhangi bir statik üyeye başvurur. Statik Oluşturucu çağrıldığında kullanıcının denetimi yoktur. Statik oluşturucu özel değilse, sistem dışındaki kod tarafından çağrılabilir. Oluşturucu içinde gerçekleştirilen işlemlere bağlı olarak bu, beklenmeyen davranışlara neden olabilir.

 Bu kural C# ve Visual Basic .NET derleyicileri tarafından zorlanır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İhlaller genellikle aşağıdaki eylemlerden biri nedeniyle oluşur:

- Türü için bir statik Oluşturucu tanımladınız ve özel hale gelmedi.

- Programlama dili derleyicisi, türüne varsayılan bir statik Oluşturucu ekledi ve özel hale gelmedi.

  İlk ihlalin türünü onarmak için statik oluşturucuyu özel yapın. İkinci türü onarmak için, türünüz için bir özel statik oluşturucu ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu ihlalleri engellemez. Yazılım tasarımınız statik bir oluşturucuya açık bir çağrı gerektiriyorsa, tasarımın ciddi kusurlar içermesi ve incelenmesi gerekir.
