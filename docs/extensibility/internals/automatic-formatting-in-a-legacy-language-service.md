---
title: Eski dil hizmetinde otomatik biçimlendirme | Microsoft Docs
description: Bilinen bir dil hizmetinde otomatik biçimlendirme hakkında bilgi edinin. Bu, bilinen bir kod yapısını oluşturmaya başladığınızda otomatik olarak bir kod parçacığı ekler.
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
ms.openlocfilehash: be59d5101c07e361056142bfda96a82b06d4389c2928f1d1750d370f0947b7c3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401485"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Eski dil hizmetinde otomatik biçimlendirme
Otomatik biçimlendirme ile, bir Kullanıcı bilinen kod yapısını yazmak için başladığında bir dil hizmeti otomatik olarak bir kod parçacığı ekler.

## <a name="automatic-formatting-behavior"></a>Otomatik Biçimlendirme davranışı
 Örneğin *, dil hizmeti, eşleşen* küme ayraçlarını otomatik olarak ekler veya ENTER tuşuna basarsanız, dil hizmeti, önceki satırın yeni bir kapsam açılıp açılmayacağı bağlı olarak, yeni satırdaki ekleme noktasını uygun girinti düzeyine zorlar.

 Dil hizmetinin geri kalanı için kullanılan komut filtresi otomatik biçimlendirme için de kullanılabilir. Ayrıca, çağırarak eşleşen küme ayraçlarını vurgulayabilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
