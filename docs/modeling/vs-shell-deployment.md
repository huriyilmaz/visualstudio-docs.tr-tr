---
title: VS Shell dağıtımı
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8793312e0ed022fc7210508efdf20a81b293f0f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535856"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı

Yalıtılmış bir kabuk, etki alanına özgü diliniz ve bu çözümün görünmesi için hangi Visual Studio işlevselliğini kullanmanız gerektiğini belirlemenizi sağlar. Visual Studio yalıtılmış Kabuğu hakkında daha fazla bilgi için bkz. [yalıtılmış Kabuğu özelleştirme](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Bir Visual Studio kabuğunu dağıtım hedefi olarak ayarlamak için:

1. **DslPackage** projesinde **Source.Extension.tt**öğesini açın.

2. `<SupportedProducts>`Ekle altında:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell* öğesini yalıtılmış Kabuk paketinizin adıyla değiştirin.
