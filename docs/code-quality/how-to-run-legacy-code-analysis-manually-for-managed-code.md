---
title: Eski Kod analizini el ile Çalıştır (.NET)
description: Kaynak kodundaki olası kusurları algılamayı öğrenin. Bkz. Visual Studio 'da eski kod analizini el ile yönetilen kodda çalıştırma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f214ac47ad3d831432b91652c5bbe3249ce5f1c5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223491"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Nasıl yapılır: yönetilen kod için eski kod analizini el ile çalıştırma

Kod Analizi Aracı, kaynak kodunuzda olası hatalar hakkında bilgi sağlar. Kod analizini her bir kod projesi derlemesi ile otomatik olarak çalıştırabilirsiniz ve Kod analizini el ile de çalıştırabilirsiniz. Kod Analizi çalıştırıldığında işaretlenen kurallar, proje özelliği sayfalarının kod analizi sayfasında belirtilir. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod projesi Için kod analizini yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Kod analizini el ile çalıştırmak için

1. Visual Studio 2019 sürüm 16,5 veya sonraki bir sürümü kullanıyorsanız, Visual Studio 'Yu başlatmadan önce komut isteminde aşağıdaki komutu yürütün:

```
setx EnableLegacyCodeAnalysis true
```

2. **Çözüm Gezgini**, projeye tıklayın.

3. **Çözümle** menüsünde, *Proje adı* **üzerinde Kod analizini Çalıştır** ' a tıklayın.
