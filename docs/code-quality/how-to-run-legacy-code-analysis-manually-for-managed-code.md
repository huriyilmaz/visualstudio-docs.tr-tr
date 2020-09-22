---
title: Eski Kod analizini el ile Çalıştır (.NET)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ca865b33d59f87453cafc337e1595c9d772b17a2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808619"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Nasıl yapılır: yönetilen kod için eski kod analizini el ile çalıştırma

Kod Analizi Aracı, kaynak kodunuzda olası hatalar hakkında bilgi sağlar. Kod analizini her bir kod projesi derlemesi ile otomatik olarak çalıştırabilirsiniz ve Kod analizini el ile de çalıştırabilirsiniz. Kod Analizi çalıştırıldığında işaretlenen kurallar, proje özelliği sayfalarının kod analizi sayfasında belirtilir. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod projesi Için kod analizini yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Kod analizini el ile çalıştırmak için

1. Visual Studio 2019 sürüm 16,5 veya sonraki bir sürümü kullanıyorsanız, Visual Studio 'Yu başlatmadan önce komut isteminde aşağıdaki komutu yürütün:

```
set EnableLegacyCodeAnalysis = true
```

2. **Çözüm Gezgini**, projeye tıklayın.

3. **Çözümle** menüsünde, *Proje adı* **üzerinde Kod analizini Çalıştır** ' a tıklayın.
