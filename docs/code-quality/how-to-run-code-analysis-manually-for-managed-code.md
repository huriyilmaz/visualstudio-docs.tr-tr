---
title: .NET için kod analizini el ile çalıştırma
ms.date: 09/02/2020
description: Visual Studio 2019 sürüm 16.5 veya sonraki sürümlerinde kod analizini el ile çalıştırmayı öğrenin. Roslyn çözümleyicilerini C# veya kod üzerinde Visual Basic bakın.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 571845c313a0712a10383a1cb718fea4bc4817f2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631952"
---
# <a name="run-code-analysis-manually-for-net"></a>.NET için kod analizini el ile çalıştırma
Varsayılan olarak, .NET Compiler Platform analizi ("Roslyn") çözümleyicileri hem canlı analiz hem de derleme sırasında Visual Basic C# veya Visual Basic kodunuzu analiz eder. Bu nedenle, normalde kod analizini el ile tetiklemeniz gerekmez. Ancak, kod analizini el ile tetiklemek istediğiniz bazı senaryolar vardır:

> [!NOTE]
> Kod analizini el ile çalıştırma Visual Studio 2019 sürüm 16.5 veya sonraki bir sürümü gerektirir

- Varsayılan olarak, canlı kod analizi çözümleyicileri yalnızca dosyalarda açık dosyalar için Visual Studio. Ancak, belirli bir proje veya çözümde yer alan tüm dosyalar için kod analizi uyarılarını görüntülemek ilginizi çekebilirsiniz. Öyleyse, bir proje veya çözüm üzerinde kod analizini bir kez tetiklemek iyi olur. Alternatif olarak, çözümün tamamına yürütmek için sürekli canlı kod analizini etkinleştirebilirsiniz. Daha fazla bilgi için [bkz. Nasıl yapılandırılır: Yönetilen kod için canlı kod analizi kapsamını yapılandırma.](./configure-live-code-analysis-scope-managed-code.md)
- Sürekli canlı analiz veya derleme zamanı analizi yerine isteğe bağlı kod analizi yürütme iş akışını tercih edebilirsiniz. Öyleyse, canlı analiz ve/veya derleme sırasında çözümleyici yürütmeyi devre dışı 3. Analizi devre dışı bırakma hakkında bilgi için [bkz. Kaynak kodu analizini devre dışı bırakma.](disable-code-analysis.md) Ardından bir proje veya çözüm üzerinde kod analizini el ile tetiklemeniz gerekir.

### <a name="run-code-analysis-manually"></a>Kod analizini el ile çalıştırma

1. Bu **Çözüm Gezgini** projesini seçin.

2. Çözümle **menüsünde,** **Ad'Code Analysis Çalıştır'Project** *seçin.*

Kod analizi arka planda yürütülmektedir. Sol alt köşedeki **durum çubuğunda \<project> ...** için kod analizi Visual Studio iletisi görüyorsanız. Kod analizi tamamlandıktan sonra durum iletisi için Kod analizi **tamamlandı olarak değişir. \<project>** Hata listesi yakında tüm kod analizi tanılamaları ile yenilenir.
