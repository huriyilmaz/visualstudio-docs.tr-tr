---
title: VS Shell dağıtımı
description: Yalıtılmış kabuk, DSL'Visual Studio etkileşimde bulunmak için hangi işleve ihtiyacınız olduğunu ve bu çözümün nasıl görünmesi gerektiğini belirlemenize nasıl olanak sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 946cbf99fa7836fa8d7ec5aa1d921e7cda93bf46
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388314"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı

Yalıtılmış kabuk, etki alanına Visual Studio etkileşim kurmak için ihtiyacınız olan işlev işlevlerini ve bu çözümün nasıl görünmesi gerektiğini belirlemenize olanak sağlar. Yalıtılmış kabuk Visual Studio daha fazla bilgi için [bkz. Yalıtılmış Kabuğu Özelleştirme.](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

Visual Studio Shell'i dağıtım hedefi olarak ayarlamak için:

1. **DslPackage projesinde** **source.extension.tt.**

2. Ekle `<SupportedProducts>` altında:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell'i* yalıtılmış kabuk paketinizin adıyla değiştirin.