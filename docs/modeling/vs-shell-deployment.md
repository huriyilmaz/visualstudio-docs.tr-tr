---
title: VS Shell dağıtımı
description: Yalıtılmış kabuk, DSL'niz Visual Studio hangi işleve ihtiyacınız olduğunu ve bu çözümün nasıl görünmesi gerektiğini belirlemenize nasıl olanak sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: c521e68f8e26d636cfccaccc607c4a03a2d5b714
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123508"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı

Yalıtılmış kabuk, etki alanına Visual Studio etkileşimde bulunmak için ihtiyacınız olan işlev işlevlerini ve bu çözümün nasıl görünmesi gerektiğini belirlemenizi sağlar. Yalıtılmış kabuk Visual Studio daha fazla bilgi için [bkz. Yalıtılmış Kabuğu Özelleştirme.](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

Visual Studio Shell'i dağıtım hedefi olarak ayarlamak için:

1. **DslPackage projesinde** **source.extension.tt.**

2. Ekle `<SupportedProducts>` altında:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell'i* yalıtılmış kabuk paketinizin adıyla değiştirin.