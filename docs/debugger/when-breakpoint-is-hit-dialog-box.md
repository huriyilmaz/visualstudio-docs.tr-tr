---
title: Kesme NoktasıNa Geldiğinde İletişim Kutusu | Microsoft Docs
description: Kesme Noktası Isabet Olduğunda'ı kullanarak hataya neden olan eylemi belirtin. Bir iletinin yazdırılacak ve yürütmenin daha sonra devam edeceğini belirtebilirsiniz.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 444b9c2860e3e79a5fea5b673b68881a1fec4294
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090115"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Kesme Noktası İsabet Edildiğinde İletişim Kutusu
Bu iletişim kutusu ile bir kesme noktasına gelindiğinde gerçekleşen eylemi özelleştirebilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi
 **İleti Yazdırma** DebuggerDisplay söz dizimi kullanarak bir ileti yazdırır. Daha fazla bilgi için [bkz. DebuggerDisplay Özniteliğini Kullanma.](../debugger/using-the-debuggerdisplay-attribute.md)

 Bu metin kutusu, bir DebuggerDisplay ifadesinin küme ayraçları içinde veya tek başlarına kullanılabilecek özel anahtar sözcükleri (örneğin, $ADDRESS) de destekler. Kullanılabilir anahtar sözcükler, iletişim kutusunda listelenir.

 **Yürütmeye Devam** Bu denetim yalnızca İleti Yazdır **seçildiğinde** etkinleştirilir. Bu denetim seçildiğinde, bir kesme noktasını, konuma ulaşıldığında kesmek yerine, program yürütmenizi izlemek üzere bir izleme noktası olarak kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kesme Noktaları Kullanma](../debugger/using-breakpoints.md)
- [DebuggerDisplay Özniteliğini Kullanma](../debugger/using-the-debuggerdisplay-attribute.md)