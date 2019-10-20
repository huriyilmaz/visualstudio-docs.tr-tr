---
title: 'Nasıl yapılır: üretilen kod için kod analizi uyarılarını gizleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646270"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Nasıl yapılır: Üretilen Kod İçin Kod Analizi Uyarılarını Bastırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen kod derleyicileri genellikle hızlı kod geliştirmeyi kolaylaştırmak için bir projeye eklenen kodu oluşturur. Ayrıca, geliştiriciler uygulamaları hızla geliştirmeye yardımcı olmak için genellikle üçüncü taraf araçları kullanır. Bu araçlar projeye eklenen kodu da oluşturur.

 Kod analizinin üretilen kodda bulduğu kural ihlallerini görmek isteyebilirsiniz. Ancak, ihlalin bulunduğu kodu görüntüleyemez ve koruyabilmeniz durumunda bunları görmek istemeyebilirsiniz.

 Bir projenin kod analizi özelliği sayfasında, **üretilen koddan sonuçları gösterme** onay kutusu, üçüncü taraf bir araç tarafından oluşturulan koddan kod analizi uyarılarını görmek isteyip istemediğinizi seçmenizi sağlar.

> [!NOTE]
> Bu seçenek, hatalar ve uyarılar formlarda ve şablonlarda görüntülendiğinde, kod analizi hatalarını ve üretilen koddan gelen uyarıları göstermez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilirsiniz.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Bir projede oluşturulan koda yönelik uyarıları gizlemek için

1. Çözüm Gezgini ' de projeye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Kod Analizi**' ne tıklayın.

3. **Oluşturulan koddan sonuçları bastır** onay kutusunu seçin.
