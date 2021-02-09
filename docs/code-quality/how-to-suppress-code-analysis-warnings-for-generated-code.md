---
title: Üretilen kod için kod analizi ihlallerini gösterme
ms.date: 05/13/2019
description: Üretilen kod için kod analizi uyarılarını nasıl bastıralabileceğinizi öğrenin. Bkz. Visual Studio 'Nun oluşturulan kod hakkında eski analiz uyarılarını görüntülemesini engelleme.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a149511b447f1f21d180eaf526ebc3d991c95997
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859950"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Nasıl yapılır: üretilen kod için kod analizi uyarılarını gösterme

Oluşturulan kod, yönetilen kod derleyicileri veya üçüncü taraf araçları tarafından projenize eklenen kodu içerir. Kod analizinin üretilen kodda bulduğu kural ihlallerini görmek isteyebilirsiniz. Ancak, ihlalleri içeren kodu görüntüleyemediğinden ve koruyabileceğinizden, bunları görmek istemeyebilirsiniz.

Bir projenin kod analizi özelliği sayfasında, **üretilen koddan sonuçları gösterme** onay kutusu, üçüncü taraf bir araç tarafından oluşturulan koddan kod analizi uyarılarını gösterip göstermeyeceğinizi seçmenize olanak sağlar.

> [!NOTE]
> Bu seçenek, hatalar ve uyarılar formlarda ve şablonlarda görüntülendiğinde, kod analizi hatalarını ve üretilen koddan gelen uyarıları göstermez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilirsiniz.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Bir projede oluşturulan koda yönelik uyarıları gizlemek için

1. **Çözüm Gezgini** ' de projeye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Kod Analizi** sekmesini seçin.

3. **Oluşturulan koddan sonuçları bastır** onay kutusunu seçin.

> [!IMPORTANT]
> Yalnızca eski analizden gelen uyarıları gizleyebilirsiniz. Ayarı olan özellik sayfası kullanım dışı bırakılmıştır ve gelecekteki bir ürün sürümünde kaldırılacak. Şu anda [çözümleyicilerin](roslyn-analyzers-overview.md)kod analizi uyarılarını gizlenemez.
