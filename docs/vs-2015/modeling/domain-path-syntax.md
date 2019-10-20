---
title: Etki alanı yolu sözdizimi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b25b47b5b711f09334501ed21abf06cb66402b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669735"
---
# <a name="domain-path-syntax"></a>Etki Alanı Yolu Sözdizimi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL tanımları bir modeldeki belirli öğeleri bulmak için XPath benzeri bir sözdizimi kullanır.

 Normalde bu söz dizimi ile doğrudan çalışmanız gerekmez. DSL ayrıntılarında veya Özellikler penceresi göründüğü yerde, aşağı oka tıklayıp yol düzenleyicisini kullanabilirsiniz. Ancak, düzenleyici kullanıldıktan sonra bu formda bu formda yol görüntülenir.

 Bir etki alanı yolu aşağıdaki biçimi alır:

 *RelationshipName. PropertyName/! Rolü*

 ![Commentreferenceskonularla başvuru ilişkisi](../modeling/media/dsl-reference.png "dsl_reference")

 Sözdizimi, modelin ağacını gezdiğinde. Örneğin, yukarıdaki çizimde yer alan ilişki **Referenceskonularla** ilgili etki alanı Ilişkisi bir **konular** rolüne sahiptir. Yol kesimi **/! Subjectt** , bir yolun **konular** rolüyle erişilen öğelerde bitdiğini belirtir.

 Her segment, bir etki alanı ilişkisinin adıyla başlar. Çapraz geçiş bir öğeden bir ilişkiye ise yol segmenti *Relationship. PropertyName*olarak görünür. Atlama bir öğeye ait bir bağlantıdır, yol kesimi *ilişki/! olarak görünür. RoleName*.

 Eğik çizgi, bir yolun söz dizimini ayırır. Her yol segmenti, bir öğeden bir bağlantı (bir ilişkinin örneği) veya bir öğe bağlantısı olan bir atlama olur. Yol kesimleri genellikle çiftler halinde görünür. Bir yol kesimi bir öğeden bir bağlantıyı bir atlama temsil eder ve sonraki kesim, diğer uçtaki öğesine olan bağlantılardan bir atlama temsil eder. (Herhangi bir bağlantı, bir ilişkinin kendisinin kaynağı veya hedefi de olabilir).

 Öğe-bağlantı atlama için kullandığınız ad, rol `Property Name` değeridir. Öğe bağlantısı atlaması için kullandığınız ad, hedef rol adıdır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
