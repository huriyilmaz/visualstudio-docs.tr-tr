---
title: Eski Kod analizini el ile Çalıştır (.NET)
description: Kaynak kodundaki olası kusurları algılamayı öğrenin. Visual Studio, Eski Kod analizini yönetilen kodda el ile nasıl çalıştıracağınızı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045001"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Nasıl yapılır: yönetilen kod için eski kod analizini el ile çalıştırma

Kod Analizi Aracı, kaynak kodunuzda olası hatalar hakkında bilgi sağlar. Kod analizini her bir kod projesi derlemesi ile otomatik olarak çalıştırabilirsiniz ve Kod analizini el ile de çalıştırabilirsiniz. kod analizi çalıştırıldığında işaretlenen kurallar, proje özelliği sayfalarının Code Analysis sayfasında belirtilir. daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma Code Analysis yönetilen kod Project](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Kod analizini el ile çalıştırmak için

1. Visual Studio 2019 sürüm 16,5 veya sonraki bir sürümü kullanıyorsanız, Visual Studio başlatmadan önce komut isteminde aşağıdaki komutu yürütün:

```
setx EnableLegacyCodeAnalysis true
```

2. **Çözüm Gezgini**, projeye tıklayın.

3. **çözümle** menüsünde, *Project adı* **üzerinde Code Analysis çalıştır** ' a tıklayın.
