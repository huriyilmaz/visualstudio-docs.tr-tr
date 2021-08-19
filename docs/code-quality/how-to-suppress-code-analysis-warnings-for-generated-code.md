---
title: oluşturulan kod için Code Analysis ihlallerini gösterme
ms.date: 05/13/2019
description: Üretilen kod için kod analizi uyarılarını nasıl bastıralabileceğinizi öğrenin. Visual Studio, oluşturulan kod hakkında eski analiz uyarılarını görüntülemesini nasıl önleyekullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 95ec7fab824160c58d259da2f2f4e5178e7b256ac7bbe310e0544bf3a835b739
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455328"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Nasıl yapılır: üretilen kod için kod analizi uyarılarını gösterme

Oluşturulan kod, yönetilen kod derleyicileri veya üçüncü taraf araçları tarafından projenize eklenen kodu içerir. Kod analizinin üretilen kodda bulduğu kural ihlallerini görmek isteyebilirsiniz. Ancak, ihlalleri içeren kodu görüntüleyemediğinden ve koruyabileceğinizden, bunları görmek istemeyebilirsiniz.

Bir projenin kod analizi özelliği sayfasında, **üretilen koddan sonuçları gösterme** onay kutusu, üçüncü taraf bir araç tarafından oluşturulan koddan kod analizi uyarılarını gösterip göstermeyeceğinizi seçmenize olanak sağlar.

> [!NOTE]
> Bu seçenek, hatalar ve uyarılar formlarda ve şablonlarda görüntülendiğinde, kod analizi hatalarını ve üretilen koddan gelen uyarıları göstermez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilirsiniz.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Bir projede oluşturulan koda yönelik uyarıları gizlemek için

1. **Çözüm Gezgini** ' de projeye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Code Analysis** sekmesini seçin.

3. **Oluşturulan koddan sonuçları bastır** onay kutusunu seçin.

> [!IMPORTANT]
> Yalnızca eski analizden gelen uyarıları gizleyebilirsiniz. Ayarı olan özellik sayfası kullanım dışı bırakılmıştır ve gelecekteki bir ürün sürümünde kaldırılacak. Şu anda [çözümleyicilerin](roslyn-analyzers-overview.md)kod analizi uyarılarını gizlenemez.
