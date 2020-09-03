---
title: Kesme noktası Isabet edildiğinde Iletişim kutusu | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53b19f4dd0d4b0cb97bb33e4895f36c4dc8f670c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72728140"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Kesme Noktası İsabet Edildiğinde İletişim Kutusu
Bu iletişim kutusu ile bir kesme noktasına gelindiğinde gerçekleşen eylemi özelleştirebilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi
 **Ileti Yazdır** DebuggerDisplay söz dizimini kullanarak bir ileti yazdırır. Daha fazla bilgi için bkz. [DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md).

 Bu metin kutusu, bir DebuggerDisplay ifadesinin küme ayraçları içinde veya tek başlarına kullanılabilecek özel anahtar sözcükleri (örneğin, $ADDRESS) de destekler. Kullanılabilir anahtar sözcükler, iletişim kutusunda listelenir.

 **Yürütmeye devam et** Bu denetim yalnızca **bir Ileti Yazdır** seçildiğinde etkindir. Bu denetim seçildiğinde, bir kesme noktasını, konuma ulaşıldığında kesmek yerine, program yürütmenizi izlemek üzere bir izleme noktası olarak kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kesme Noktalarını Kullanma](../debugger/using-breakpoints.md)
- [DebuggerDisplay Özniteliğini Kullanma](../debugger/using-the-debuggerdisplay-attribute.md)