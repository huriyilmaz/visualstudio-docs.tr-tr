---
title: 'Nasıl yapılır: UML modelindeki değişikliklere yanıt verme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9eaaa1406591bc950dbbf95aff8dcd732eef3448
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293397"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Nasıl yapılır: Bir UML Modelindeki Değişikliklere Yanıt Verme
Visual Studio 'da bir UML modelinde her değişiklik olduğunda yürütülen kodu yazmak mümkündür. Doğrudan Kullanıcı tarafından ve diğer Visual Studio uzantıları tarafından yapılan değişikliklere eşit olarak yanıt verir. Hangi Visual Studio sürümlerini UML modellerini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Bu teknikler UML API tarafından desteklenmez. Bunlar, Visual Studio 'nun gelecek sürümlerinde çalışmayabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML Model](../modeling/navigate-the-uml-model.md) [olay Işleyicilerinde gezinerek değişiklikleri model dışında yay](../modeling/event-handlers-propagate-changes-outside-the-model.md) [örnek: stereotipe göre Renklendir](https://go.microsoft.com/fwlink/?LinkId=213841)