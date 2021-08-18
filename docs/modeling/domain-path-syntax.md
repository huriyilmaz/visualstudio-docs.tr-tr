---
title: Etki Alanı Yolu Sözdizimi
description: Etki alanı yolu söz dizimi ve DSL tanımlarının bir modeldeki belirli öğeleri bulmak için XPath benzeri bir sözdizimi nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 9f5254200ca60f66b03f5c3cd33f80ce9399cb93
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027740"
---
# <a name="domain-path-syntax"></a>Etki Alanı Yolu Sözdizimi
DSL tanımları bir modeldeki belirli öğeleri bulmak için XPath benzeri bir sözdizimi kullanır.

 Normalde bu söz dizimi ile doğrudan çalışmanız gerekmez. DSL ayrıntılarında veya Özellikler penceresi göründüğü yerde, aşağı oka tıklayıp yol düzenleyicisini kullanabilirsiniz. Ancak, düzenleyici kullanıldıktan sonra bu formda bu formda yol görüntülenir.

 Bir etki alanı yolu aşağıdaki biçimi alır:

 *RelationshipName. PropertyName/! Rolü*

 ![Commentreferenceskonularla başvuru ilişkisi](../modeling/media/dsl_reference.png)

 Sözdizimi, modelin ağacını gezdiğinde. Örneğin, yukarıdaki çizimde yer alan ilişki **Referenceskonularla** ilgili etki alanı Ilişkisi bir **konular** rolüne sahiptir. Yol kesimi **/! Subjectt** , bir yolun **konular** rolüyle erişilen öğelerde bitdiğini belirtir.

 Her segment, bir etki alanı ilişkisinin adıyla başlar. Çapraz geçiş bir öğeden bir ilişkiye ise yol segmenti *Relationship. PropertyName* olarak görünür. Atlama bir öğeye ait bir bağlantıdır, yol kesimi *ilişki/! olarak görünür. RoleName*.

 Eğik çizgi, bir yolun söz dizimini ayırır. Her yol segmenti, bir öğeden bir bağlantı (bir ilişkinin örneği) veya bir öğe bağlantısı olan bir atlama olur. Yol kesimleri genellikle çiftler halinde görünür. Bir yol kesimi bir öğeden bir bağlantıyı bir atlama temsil eder ve sonraki kesim, diğer uçtaki öğesine olan bağlantılardan bir atlama temsil eder. (Herhangi bir bağlantı, bir ilişkinin kendisinin kaynağı veya hedefi de olabilir).

 Öğe-bağlantı atlama için kullandığınız ad, rolün değeridir `Property Name` . Öğe bağlantısı atlaması için kullandığınız ad, hedef rol adıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
