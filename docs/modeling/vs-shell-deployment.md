---
title: VS Shell dağıtımı
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ef0124c06cd6f1a4d24e29b2c02cd0b50a37b0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115278"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı

Yalıtılmış bir kabuk, etki alanına özgü diliniz ve bu çözümün görünmesi için hangi Visual Studio işlevselliğini kullanmanız gerektiğini belirlemenizi sağlar. Visual Studio yalıtılmış Kabuğu hakkında daha fazla bilgi için bkz. [yalıtılmış Kabuğu özelleştirme](https://vspartner.com/pages/vsshells).

Bir Visual Studio kabuğunu dağıtım hedefi olarak ayarlamak için:

1. **DslPackage** projesinde **Source.Extension.tt**öğesini açın.

2. `<SupportedProducts>` Ekle altında:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell* öğesini yalıtılmış Kabuk paketinizin adıyla değiştirin.
