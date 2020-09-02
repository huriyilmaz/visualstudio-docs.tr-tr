---
title: Taşınabilirlik uyarıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 932474143b4770e81d8bfca14ab05a6538ae84a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671163"
---
# <a name="portability-warnings"></a>Taşınabilirlik Uyarıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Taşınabilirlik uyarıları, farklı işletim sistemleri arasında taşınabilirliği destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Description|
|----------|-----------------|
|[CA1900: Değer tür alanları taşınabilir olmalıdır](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Bu kural, 64 bit işletim sistemlerinde yönetilmeyen koda kopyalandıklarında açık bir düzen özniteliği kullanılarak belirtilen yapıların doğru şekilde hizalanmasını denetler.|
|[CA1901: P/Invoke bildirimleri taşınabilir olmalıdır](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Bu kural, her parametrenin boyutunu ve bir P/Invoke dönüş değerini değerlendirir ve 32-bit ve 64-bit işletim sistemlerinde yönetilmeyen koda sıralandığında boyutunun doğru olduğunu doğrular.|
|[CA1903: Yalnızca hedeflenen çerçeveden API kullanın](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Bir üye veya tür, bir üye veya projedeki hedeflenen çerçeve ile birlikte dahil edilmemiş hizmet paketinde tanıtılmış türü kullanır.|
