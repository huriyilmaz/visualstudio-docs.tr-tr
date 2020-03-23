---
title: 'Nasıl yapılı: Yönetilen kod için eski kod çözümlemeyi el ile çalıştırma'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432233"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Nasıl yapılı: Yönetilen kod için eski kod çözümlemeyi el ile çalıştırma
Kod çözümleme aracı, kaynak kodunuzdaki olası hatalar hakkında size bilgi sağlar. Kod çözümlemesi'ni bir kod projesinin her yapısında otomatik olarak çalıştırabilir ve kod çözümlemesi de el ile çalıştırabilirsiniz. Kod çözümlemesi çalıştırıldığında denetlenen kurallar, proje özelliği sayfalarının Kod Analizi sayfasında belirtilir. Daha fazla bilgi için [bkz: Yönetilen Kod Projesi için Kod Çözümlemesi'ni yapılandırın.](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)

## <a name="to-run-code-analysis-manually"></a>Kod çözümlemesi el ile çalıştırmak için

1. Visual Studio 2019 sürüm 16.5 veya daha sonraysanız, Visual Studio'yu başlatmadan önce komut isteminde aşağıdaki komutu uygulayın:

```
set EnableLegacyCodeAnalysis = true
```

2. **Çözüm Gezgini'nde**projeyi tıklatın.

3. **Analiz** menüsünde, Proje **Adı'nda Kod Çözümlemesi'ni** *Project Name*tıklatın.

