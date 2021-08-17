---
title: Oluşturulan Code Analysis için güvenlik ihlallerini gizleme
ms.date: 05/13/2019
description: Oluşturulan kod için kod analizi uyarılarını gizlemeyi öğrenin. Oluşturulan kodla ilgili Visual Studio eski analiz uyarılarını görüntülemesini önlemeye bakın.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 214c7ca6bd7dcf648060383462fa2dfef24a3618
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098014"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Nasıl oluşturulur: Oluşturulan kod için kod analizi uyarılarını gizleme

Oluşturulan kod, yönetilen kod derleyicileri veya üçüncü taraf araçlar tarafından projenize eklenen kodu içerir. Kod analizinin oluşturulan kodda keşfettikleri kural ihlallerini görmek istiyor olabilirsiniz. Ancak, ihlalleri içeren kodu görüntüleye ve koruyamayabilirsiniz, bunları görmek istemeyebilirsiniz.

Projenin **kod analizi özellik sayfasındaki** Oluşturulan kodun sonuçlarını bastır onay kutusu, üçüncü taraf bir araç tarafından oluşturulan koddan kod analizi uyarılarını gösterme seçeneğini seçmenize olanak sağlar.

> [!NOTE]
> Bu seçenek, formlarda ve şablonlarda hatalar ve uyarılar görünürken kod analizi hatalarını ve uyarıları oluşturulan koddan gizlemez. Bir formun veya şablonun kaynak kodunu hem görüntü hem de bakım için kullanabilirsiniz.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Bir projede oluşturulan kod için uyarıları gizleme

1. Çözüm Gezgini'da projeye **sağ tıklayın ve** ardından Özellikler'e **tıklayın.**

2. Code Analysis **sekmesini** seçin.

3. Oluşturulan **koddan sonuçları bastır onay** kutusunu seçin.

> [!IMPORTANT]
> Uyarıları yalnızca eski analizden bastırılır. ayarına sahip özellik sayfası kullanım dışı bırakılmıştır ve gelecek ürün yayınlarında kaldırılacaktır. Şu anda çözümleyicilerden kod analizi uyarılarını [bastıramazsiniz.](roslyn-analyzers-overview.md)
