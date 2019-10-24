---
title: DebugBreak ve __debugbreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce99cd360d75472df6326cfaf6a3f4ddb198b6d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738363"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak ve __debugbreak
Kodunuzda herhangi bir noktada DebugBreak Win32 işlevini veya [__debugbreak](/cpp/intrinsics/debugbreak) iç öğesini çağırabilirsiniz. `DebugBreak` ve `__debugbreak`, bu konumda kesme noktası ayarlama ile aynı etkiye sahiptir.

 @No__t_0, bir sistem işlevine yönelik bir çağrı olduğundan, doğru çağrı yığını bilgilerinin koparmadan sonra görüntülendiğinden emin olmak için sistem hata ayıklama simgelerinin yüklenmesi gerekir. Aksi takdirde, hata ayıklayıcı tarafından görünen çağrı yığını bilgileri bir çerçeve tarafından kapalı olabilir. @No__t_0 kullanıyorsanız, semboller gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Derleyici İç Bilgileri](/cpp/intrinsics/compiler-intrinsics)
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)