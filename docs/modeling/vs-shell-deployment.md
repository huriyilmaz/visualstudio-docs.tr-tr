---
title: VS Shell dağıtımı
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e010d2efd8174f2c61d7c97eb63d585f47812ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663665"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı

Yalıtılmış bir kabuk, etki alanına özgü diliniz ve bu çözümün görünmesi için hangi Visual Studio işlevselliğini kullanmanız gerektiğini belirlemenizi sağlar. Visual Studio yalıtılmış Kabuğu hakkında daha fazla bilgi için bkz. [yalıtılmış Kabuğu özelleştirme](https://vspartner.com/pages/vsshells).

Bir Visual Studio kabuğunu dağıtım hedefi olarak ayarlamak için:

1. **DslPackage** projesinde **Source.Extension.tt**öğesini açın.

2. @No__t_0 Ekle altında:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell* öğesini yalıtılmış Kabuk paketinizin adıyla değiştirin.