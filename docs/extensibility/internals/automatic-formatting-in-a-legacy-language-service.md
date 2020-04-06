---
title: Eski Dil Hizmetinde Otomatik Biçimlendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709988"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Eski bir dil hizmetinde otomatik biçimlendirme
Otomatik biçimlendirme ile, bir dil hizmeti otomatik olarak bir kullanıcı bilinen bir kod yapısı yazmaya başladığında bir kod snippet ekler.

## <a name="automatic-formatting-behavior"></a>Otomatik biçimlendirme davranışı
 Örneğin, dil hizmeti *if*eşleme leri otomatik olarak eklerse veya ENTER tuşuna bastığınızda, dil hizmeti ekleme noktasını önceki satırın yeni bir kapsam açıp açmadığına bağlı olarak yeni satırdaki ekleme noktasını uygun girinti düzeyine zorlar.

 Dil hizmetinin geri kalanı için kullanılan komut filtresi otomatik biçimlendirme için de kullanılabilir. Ayrıca arayarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>eşleşen ayraçları vurgulayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski bir dil hizmeti geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
