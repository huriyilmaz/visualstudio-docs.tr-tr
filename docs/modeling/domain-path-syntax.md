---
title: Etki Alanı Yolu Sözdizimi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7ab5f080328338e40bed080ec8a4c7a85eabdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114632"
---
# <a name="domain-path-syntax"></a>Etki Alanı Yolu Sözdizimi
DSL tanımları bir modeldeki belirli öğeleri bulmak için XPath benzeri bir sözdizimi kullanır.

 Normalde bu söz dizimi ile doğrudan çalışmanız gerekmez. DSL ayrıntılarında veya Özellikler penceresi göründüğü yerde, aşağı oka tıklayıp yol düzenleyicisini kullanabilirsiniz. Ancak, düzenleyici kullanıldıktan sonra bu formda bu formda yol görüntülenir.

 Bir etki alanı yolu aşağıdaki biçimi alır:

 *RelationshipName. PropertyName/! Rolü*

 ![Commentreferenceskonularla başvuru ilişkisi](../modeling/media/dsl_reference.png)

 Sözdizimi, modelin ağacını gezdiğinde. Örneğin, yukarıdaki çizimde yer alan ilişki **Referenceskonularla** ilgili etki alanı Ilişkisi bir **konular** rolüne sahiptir. Yol kesimi **/! Subjectt** , bir yolun **konular** rolüyle erişilen öğelerde bitdiğini belirtir.

 Her segment, bir etki alanı ilişkisinin adıyla başlar. Çapraz geçiş bir öğeden bir ilişkiye ise yol segmenti *Relationship. PropertyName*olarak görünür. Atlama bir öğeye ait bir bağlantıdır, yol kesimi *ilişki/! olarak görünür. RoleName*.

 Eğik çizgi, bir yolun söz dizimini ayırır. Her yol segmenti, bir öğeden bir bağlantı (bir ilişkinin örneği) veya bir öğe bağlantısı olan bir atlama olur. Yol kesimleri genellikle çiftler halinde görünür. Bir yol kesimi bir öğeden bir bağlantıyı bir atlama temsil eder ve sonraki kesim, diğer uçtaki öğesine olan bağlantılardan bir atlama temsil eder. (Herhangi bir bağlantı, bir ilişkinin kendisinin kaynağı veya hedefi de olabilir).

 Öğe-bağlantı atlama için kullandığınız ad, rolün değeridir `Property Name` . Öğe bağlantısı atlaması için kullandığınız ad, hedef rol adıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
