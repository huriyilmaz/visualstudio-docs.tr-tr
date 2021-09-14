---
title: Eski kod analizini el ile çalıştırma (.NET)
description: Kaynak kodda olası hataları algılamayı öğrenin. Eski kod analizini yönetilen kod üzerinde el ile çalıştırma hakkında daha fazla Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 7471cc1d5b7a3aaa90ae2329d080e4c9e68a2db9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631935"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Nasıl yapılır: Yönetilen kod için eski kod analizini el ile çalıştırma

Kod analizi aracı, kaynak kodundaki olası hatalar hakkında size bilgi sağlar. Kod analizini bir kod projesinin her derlemesi ile otomatik olarak çalıştırabilir ve kod analizini el ile de çalıştırabilirsiniz. Kod analizi çalıştırlendiğinde denetlenen kurallar, proje özellik Code Analysis sayfasında belirtilir. Daha fazla bilgi için, [bkz. How to: Configure Code Analysis for a Managed Code Project.](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)

## <a name="to-run-code-analysis-manually"></a>Kod analizini el ile çalıştırmak için

1. 2019 Visual Studio 16.5 veya sonraki bir sürümün üzerindeyebilirsiniz. Komut istemine başlamadan önce aşağıdaki komutu Visual Studio:

```
setx EnableLegacyCodeAnalysis true
```

2. Bu **Çözüm Gezgini** projesine tıklayın.

3. Çözümle **menüsünde Ad'Code Analysis** **Çalıştır'a** *Project tıklayın.*
