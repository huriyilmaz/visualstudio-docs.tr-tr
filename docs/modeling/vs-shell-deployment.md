---
title: VS Shell dağıtımı
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f3729c09198b331728e2cc67299ffc3ad6c3d26
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809654"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı

Yalıtılmış bir kabuk, etki alanına özgü diliniz ve bu çözümün görünmesi için hangi Visual Studio işlevselliğini kullanmanız gerektiğini belirlemenizi sağlar. Visual Studio yalıtılmış Kabuğu hakkında daha fazla bilgi için bkz. [yalıtılmış Kabuğu özelleştirme](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Bir Visual Studio kabuğunu dağıtım hedefi olarak ayarlamak için:

1. **DslPackage** projesinde **Source.Extension.tt**öğesini açın.

2. `<SupportedProducts>`Ekle altında:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell* öğesini yalıtılmış Kabuk paketinizin adıyla değiştirin.