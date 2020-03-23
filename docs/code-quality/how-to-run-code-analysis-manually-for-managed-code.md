---
title: 'Nasıl yapılı: Yönetilen kod için kod çözümlemeyi el ile çalıştırın'
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431390"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Nasıl yapılır: Yönetilen kod için kod çözümlemeyi el ile çalıştırın (Visual Studio 2019 sürüm 16.5 veya sonrası gerektirir)
Varsayılan olarak, .NET Derleyici Platformu ("Roslyn") kod çözümleyicileri, c# veya Visual Basic kodunuzu, yapı sırasında ve yapı sırasında canlı analiz yaparak yazarken analiz eder. Bu nedenle, normalde kod çözümlemesi el ile tetiklemek gerekmez. Ancak, kod çözümlemesi el ile tetiklemek isteyebilirsiniz bazı senaryolar vardır:

- Varsayılan olarak, canlı kod çözümlemesi yalnızca Visual Studio'daki açık dosyalar için çözümleyicileri yürütür. Ancak, belirli bir proje veya çözümdeki tüm dosyalar için kod çözümlemesi uyarılarını görüntülemek ilginizi çekebilir. Bu nedenle, bir proje veya çözüm üzerinde bir kez kod çözümlemesi tetiklemek isteyebilirsiniz. Alternatif olarak, tüm çözüm üzerinde yürütmek için sürekli canlı kod çözümlemesi etkinleştirebilirsiniz. Daha fazla bilgi için [bkz: Yönetilen kod için canlı kod çözümlemesi kapsamını yapılandırma.](./configure-live-code-analysis-scope-managed-code.md)
- Sürekli canlı çözümleme veya yapı zamanı çözümlemesi yerine isteğe bağlı kod analizi yürütme iş akışını tercih edebilirsiniz. Bu nedenle, canlı analiz ve/veya yapı sırasında çözümleyici yürütmeyi devre dışı kullanabilirsiniz. Çözümleme çözümlemesi hakkında bilgi için [kaynak kodu çözümlemesi nasıl devre dışı bırakılabildiğini](disable-code-analysis.md)öğrenin. Daha sonra bir proje veya çözüm üzerinde bir kez kod çözümlemesi el ile tetiklemek isteyebilirsiniz. 

### <a name="run-code-analysis-manually"></a>Kod analizini el ile çalıştırma

1. **Çözüm Gezgini'nde**projeyi tıklatın.

2. **Analiz** menüsünde, Proje **Adı'nda Kod Çözümlemesi'ni** *Project Name*tıklatın.

Kod çözümlemesi arka planda yürütmeye başlar. Sol alt köşeye doğru Visual Studio durum çubuğunda **proje> için \<kod çözümlemesi çalıştıran** iletiyi görmeniz gerekir. Kod çözümlemesi tamamlandıktan sonra durum iletisi **proje>için tamamlanan Kod çözümlemesi olarak \< **değişecektir. Hata listesi yakında tüm kod analizi tanılama ile yenilenir.
