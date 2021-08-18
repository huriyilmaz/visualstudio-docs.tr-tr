---
title: Eski Dil Hizmeti HizmetLerinde Otomatik Biçimlendirme | Microsoft Docs
description: Eski dil hizmetlerinde, bilinen bir kod yapısı yazmaya başsanız otomatik olarak kod parçacığı ekli olan otomatik biçimlendirme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1d5e824c96860030f0299fe6e1178515b7d1693d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124808"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Eski dil hizmetlerinde otomatik biçimlendirme
Otomatik biçimlendirme ile dil hizmeti, kullanıcı bilinen bir kod yapısı yazmaya başladığında otomatik olarak bir kod parçacığı ekler.

## <a name="automatic-formatting-behavior"></a>Otomatik biçimlendirme davranışı
 Örneğin, , ise, *dil* hizmeti eşleşen ayraçları otomatik olarak ekler veya ENTER tuşuna basıyorsanız, dil hizmeti ekleme noktasını önceki satırın yeni bir kapsam açıp açmay durumuna bağlı olarak yeni satırda uygun girinti düzeyine güç sağlar.

 Dil hizmetinin geri kalanı için kullanılan komut filtresi de otomatik biçimlendirme için kullanılabilir. ayrıca çağırarak eşleşen küme ayraçlarını <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> vurgulayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
