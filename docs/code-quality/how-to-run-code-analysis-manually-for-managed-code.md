---
title: Yönetilen kod için kod analizini el ile çalıştırma
ms.date: 11/04/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bbd3d2023310b9412310fc86f419c2e8c4a127c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88893404"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Nasıl yapılır: yönetilen kod için kod analizini el ile çalıştırma (Visual Studio 2019 sürüm 16,5 veya üzeri gerekir)
Varsayılan olarak, .NET Compiler Platform ("Roslyn") kod Çözümleyicileri, canlı analizler ve derleme sırasında yazı yazarken C# veya Visual Basic kodunuzu analiz eder. Bu nedenle normalde Kod analizini el ile tetiklemeniz gerekmez. Ancak, Kod analizini el ile tetiklemek isteyebileceğiniz bazı senaryolar vardır:

- Varsayılan olarak, canlı kod analizi yalnızca Visual Studio 'daki açık dosyalar için Çözümleyicileri yürütür. Bununla birlikte, belirli bir proje ya da Çözümdeki tüm dosyalar için kod analizi uyarılarını görüntülemeyi ilgileniyor olabilirsiniz. Bu durumda, Kod analizini bir proje veya çözüm üzerinde bir kez tetiklemeniz gerekir. Alternatif olarak, sürekli canlı kod analizini tüm çözümde yürütmek üzere etkinleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod için canlı kod analizi kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md).
- Sürekli canlı analiz veya derleme zamanı analizi üzerinde isteğe bağlı kod analizi yürütme iş akışını tercih edebilirsiniz. Bu durumda, canlı analiz ve/veya derleme sırasında çözümleyici yürütmeyi devre dışı bırakabilirsiniz. Çözümlemeyi devre dışı bırakma hakkında daha fazla bilgi için bkz. [kaynak kodu analizini devre dışı bırakma](disable-code-analysis.md). Daha sonra kod analizini bir proje veya çözümde bir kez daha el ile tetiklemeniz gerekir.

### <a name="run-code-analysis-manually"></a>Kod analizini el ile çalıştırma

1. **Çözüm Gezgini**, projeyi seçin.

2. **Çözümle** menüsünde, *Proje adı* **üzerinde Kod analizini Çalıştır** ' ı seçin.

Kod Analizi, arka planda yürütülmeye başlayacak. Visual Studio durum çubuğunda ** \<project> ... için kod analizini çalıştıran** iletiyi sol alt köşeye doğru görmeniz gerekir. Kod Analizi tamamlandığında, durum iletisi **Için \<project> kod analizi tamamlandı **olarak değişecektir. Hata listesi, kısa bir süre önce tüm kod analizi Tanılama ile yenilenir.
