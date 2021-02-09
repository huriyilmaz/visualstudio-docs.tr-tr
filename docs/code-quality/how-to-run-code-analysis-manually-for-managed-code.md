---
title: .NET için kod analizini el ile çalıştırma
ms.date: 09/02/2020
description: Visual Studio 2019 sürüm 16,5 veya sonraki sürümlerinde kod analizini el ile çalıştırmayı öğrenin. Bkz. C# veya Visual Basic kodu üzerinde Roslyn Çözümleyicileri çalıştırma.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 997fc6f6ecb8ffbd8c48e2352dcc9ae2f6092211
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860028"
---
# <a name="run-code-analysis-manually-for-net"></a>.NET için kod analizini el ile çalıştırın
Varsayılan olarak, .NET Compiler Platform ("Roslyn") Çözümleyicileri, derleme sırasında ve canlı analizler yaparak C# veya Visual Basic kodunuzu sizin yazarken analiz eder. Bu nedenle normalde Kod analizini el ile tetiklemeniz gerekmez. Ancak, Kod analizini el ile tetiklemek isteyebileceğiniz bazı senaryolar vardır:

> [!NOTE]
> Kod analizini el ile çalıştırmak için Visual Studio 2019 sürüm 16,5 veya üzeri gerekir

- Varsayılan olarak, canlı kod analizi yalnızca Visual Studio 'daki açık dosyalar için Çözümleyicileri yürütür. Bununla birlikte, belirli bir proje ya da Çözümdeki tüm dosyalar için kod analizi uyarılarını görüntülemeyi ilgileniyor olabilirsiniz. Bu durumda, Kod analizini bir proje veya çözüm üzerinde bir kez tetiklemeniz gerekir. Alternatif olarak, sürekli canlı kod analizini tüm çözümde yürütmek üzere etkinleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod için canlı kod analizi kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md).
- Sürekli canlı analiz veya derleme zamanı analizi üzerinde isteğe bağlı kod analizi yürütme iş akışını tercih edebilirsiniz. Bu durumda, canlı analiz ve/veya derleme sırasında çözümleyici yürütmeyi devre dışı bırakabilirsiniz. Çözümlemeyi devre dışı bırakma hakkında daha fazla bilgi için bkz. [kaynak kodu analizini devre dışı bırakma](disable-code-analysis.md). Daha sonra kod analizini bir proje veya çözümde bir kez daha el ile tetiklemeniz gerekir.

### <a name="run-code-analysis-manually"></a>Kod analizini el ile çalıştırma

1. **Çözüm Gezgini**, projeyi seçin.

2. **Çözümle** menüsünde, *Proje adı* **üzerinde Kod analizini Çalıştır** ' ı seçin.

Kod Analizi, arka planda yürütülmeye başlayacak. Visual Studio durum çubuğunda **\<project> ... için kod analizini çalıştıran** iletiyi sol alt köşeye doğru görmeniz gerekir. Kod Analizi tamamlandığında, durum iletisi **Için \<project> kod analizi tamamlandı** olarak değişecektir. Hata listesi, kısa bir süre önce tüm kod analizi Tanılama ile yenilenir.
