---
title: VS Shell dağıtımı
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445005"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı

İzole edilmiş bir kabuk, etki alanına özgü dilinizle etkileşimde kalmak için hangi Visual Studio işlevini belirlemenize ve bu çözümün nasıl görünmesi gerektiğini belirlemenize olanak tanır. Visual Studio yalıtılmış kabuk hakkında daha fazla bilgi [için, İzole Kabuk Özelleştirme](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell)bakın.

Visual Studio Shell'i dağıtım hedefi olarak ayarlamak için:

1. **DslPackage** projesinde, açık **source.extension.tt.**

2. Ekleme `<SupportedProducts>` altında:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell'i* yalıtılmış kabuk paketinizin adı ile değiştirin.
