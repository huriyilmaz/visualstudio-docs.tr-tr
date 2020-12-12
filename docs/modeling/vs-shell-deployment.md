---
title: VS Shell dağıtımı
description: Yalıtılmış bir kabuğun, DSL ile etkileşimde bulunmak için hangi Visual Studio işlevselliğini ve bu çözümün nasıl görüneceğini belirlemenizi sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94cffbf5ea1f7ac3c437a4c22f27f881d5493e79
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361267"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı

Yalıtılmış bir kabuk, etki alanına özgü diliniz ve bu çözümün görünmesi için hangi Visual Studio işlevselliğini kullanmanız gerektiğini belirlemenizi sağlar. Visual Studio yalıtılmış Kabuğu hakkında daha fazla bilgi için bkz. [yalıtılmış Kabuğu özelleştirme](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Bir Visual Studio kabuğunu dağıtım hedefi olarak ayarlamak için:

1. **DslPackage** projesinde **Source.Extension.tt** öğesini açın.

2. `<SupportedProducts>`Ekle altında:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell* öğesini yalıtılmış Kabuk paketinizin adıyla değiştirin.