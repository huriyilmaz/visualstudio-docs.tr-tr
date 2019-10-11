---
title: Taşınabilirlik Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163067"
---
# <a name="portability-warnings"></a>Taşınabilirlik Uyarıları
Taşınabilirlik uyarıları, farklı işletim sistemleri arasında taşınabilirliği destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1900: Değer türü alanları taşınabilir @ no__t-0 olmalıdır|Bu kural, 64 bit işletim sistemlerinde yönetilmeyen koda kopyalandıklarında açık bir düzen özniteliği kullanılarak belirtilen yapıların doğru şekilde hizalanmasını denetler.|
|[CA1901: P/Invoke bildirimleri taşınabilir @ no__t-0 olmalıdır|Bu kural, her parametrenin boyutunu ve bir P/Invoke dönüş değerini değerlendirir ve 32-bit ve 64-bit işletim sistemlerinde yönetilmeyen koda sıralandığında boyutunun doğru olduğunu doğrular.|
|[CA1903: Hedeflenen Framework @ no__t-0 ' dan yalnızca API kullan|Bir üye veya tür, bir üye veya projedeki hedeflenen çerçeve ile birlikte dahil edilmemiş hizmet paketinde tanıtılmış türü kullanır.|
