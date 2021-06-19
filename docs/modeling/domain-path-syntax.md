---
title: Etki Alanı Yolu Sözdizimi
description: Etki Alanı Yolu Söz Dizimi ve DSL Tanımları'nın modelde belirli öğeleri bulmak için XPath'e benzer bir söz dizimi kullanma hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 69dfd02dca5ead65d4f36303e547aaeba04cde98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389104"
---
# <a name="domain-path-syntax"></a>Etki Alanı Yolu Sözdizimi
DSL Tanımları, modelde belirli öğeleri bulmak için XPath'e benzer bir söz dizimi kullanır.

 Normalde bu söz dizimi ile doğrudan çalışmak zorunda olmazsiniz. DSL Ayrıntıları'nde veya Özellikler penceresi, aşağı oka tıklar ve yol düzenleyicisini kullanabilirsiniz. Ancak, düzenleyiciyi kullandıktan sonra yol bu formda alanında görünür.

 Etki alanı yolu aşağıdaki formu alır:

 *RelationshipName.PropertyName/! Rolü*

 ![CommentReferencesSubjects başvuru ilişkisi](../modeling/media/dsl_reference.png)

 Söz dizimi, modelin ağacından çapraz geçiştir. Örneğin, yukarıdaki çizimde **commentReferencesSubjects** etki alanı ilişkisi bir **Subjects rolüne** sahip. Yol segmenti **/! Subjectt,** yolun **Subjects** rolü aracılığıyla erişilen öğelerde tamam olduğunu belirtir.

 Her segment bir etki alanı ilişkisinin adıyla başlar. Geçiş bir öğeden bir ilişkiye ise yol kesimi *Relationship.PropertyName olarak görünür.* Atlama bir öğenin bağlantısından geliyorsa yol segmenti *İlişki/! olarak görünür. RoleName*.

 Eğik çizgi, bir yolun söz dizimlerini birbirinden ayrıdır. Her yol kesimi, bir öğeden bir bağlantıya (bir ilişkinin örneği) veya bir öğenin bağlantısından atlar. Yol kesimleri sıklıkla çiftler halinde görüntülenir. Bir yol segmenti bir öğeden bir bağlantıya atlayı, sonraki segment ise diğer uçta öğeye bağlantıdan bir atlamayı temsil eder. (Herhangi bir bağlantı, bir ilişkinin kaynağı veya hedefi de olabilir).

 Öğeden bağlantıya atlama için kullanabileceğiniz ad, rolün `Property Name` değeridir. Öğeye bağlantı atlaması için kullanabileceğiniz ad, hedef rol adıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
