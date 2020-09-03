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
ms.openlocfilehash: 097405f98d1a80b8605b6773bdc675ff2c4ab773
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75404649"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak ve __debugbreak
Kodunuzda herhangi bir noktada [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Win32 işlevini veya [__debugbreak](/cpp/intrinsics/debugbreak) iç öğesini çağırabilirsiniz. `DebugBreak` ve `__debugbreak` Bu konumda bir kesme noktası ayarlamaya aynı etkiye sahiptir.

 `DebugBreak`Bir sistem işlevine yapılan bir çağrı olduğundan, doğru çağrı yığını bilgilerinin koparmadan sonra görüntülendiğinden emin olmak için sistem hata ayıklama simgelerinin yüklenmesi gerekir. Aksi takdirde, hata ayıklayıcı tarafından görünen çağrı yığını bilgileri bir çerçeve tarafından kapalı olabilir. Kullanıyorsanız `__debugbreak` , semboller gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Derleyici Iç bilgileri](/cpp/intrinsics/compiler-intrinsics)
- [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
