---
title: Eski kod analizini el ile çalıştırma (.NET)
description: Kaynak kodda olası hataları algılamayı öğrenin. Eski kod analizini yönetilen kod üzerinde el ile çalıştırma hakkında Visual Studio.
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
ms.openlocfilehash: ff428f1a72812996a8217d4193deebe7393cbcc4a2fa9b0b870ab41f7094a0bf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392763"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Nasıl yapılır: Yönetilen kod için eski kod analizini el ile çalıştırma

Kod analizi aracı, kaynak kodundaki olası hatalar hakkında size bilgi sağlar. Kod analizini bir kod projesinin her derlemesi ile otomatik olarak çalıştırabilir ve kod analizini el ile de çalıştırabilirsiniz. Kod analizi çalıştırlendiğinde denetlenen kurallar, proje Code Analysis sayfasında belirtilir. Daha fazla bilgi için, [bkz. How to: Configure Code Analysis for a Managed Code Project.](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)

## <a name="to-run-code-analysis-manually"></a>Kod analizini el ile çalıştırmak için

1. 2019 Visual Studio 16.5 veya sonraki bir sürümü yüklüyebilirsiniz. Aşağıdaki komutu başlatmadan önce komut isteminde Visual Studio:

```
setx EnableLegacyCodeAnalysis true
```

2. Bu **Çözüm Gezgini** projesine tıklayın.

3. Çözümle **menüsünde Ad'da** **Çalıştır'Code Analysis'Project** *tıklayın.*
