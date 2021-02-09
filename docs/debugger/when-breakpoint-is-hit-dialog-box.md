---
title: Kesme noktası Isabet edildiğinde Iletişim kutusu | Microsoft Docs
description: Kesme üzerine bir eylem belirtmek için kesme noktası Isabet edildiğinde kullanın. Bir iletinin yazdırılmasını belirtebilir ve bu yürütmenin daha sonra devam etmesi gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfb5099bd0fab17cd983af4e16a435fd192a1668
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883876"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Kesme Noktası İsabet Edildiğinde İletişim Kutusu
Bu iletişim kutusu ile bir kesme noktasına gelindiğinde gerçekleşen eylemi özelleştirebilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi
 **Ileti Yazdır** DebuggerDisplay söz dizimini kullanarak bir ileti yazdırır. Daha fazla bilgi için bkz. [DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md).

 Bu metin kutusu, bir DebuggerDisplay ifadesinin küme ayraçları içinde veya tek başlarına kullanılabilecek özel anahtar sözcükleri (örneğin, $ADDRESS) de destekler. Kullanılabilir anahtar sözcükler, iletişim kutusunda listelenir.

 **Yürütmeye devam et** Bu denetim yalnızca **bir Ileti Yazdır** seçildiğinde etkindir. Bu denetim seçildiğinde, bir kesme noktasını, konuma ulaşıldığında kesmek yerine, program yürütmenizi izlemek üzere bir izleme noktası olarak kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kesme noktaları kullanma](../debugger/using-breakpoints.md)
- [DebuggerDisplay Özniteliğini Kullanma](../debugger/using-the-debuggerdisplay-attribute.md)