---
title: DebugBreak ve __debugbreak | Microsoft Docs
description: DebugBreak işlevini ve bir kesme noktasının ayarlanmış olduğu gibi, programınızın kesintiye neden olması için __debugbreak iç öğesini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 376dd75062dc5a78582a23a12e9e025db60b9f3a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559777"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak ve __debugbreak
Kodunuzda herhangi bir noktada [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Win32 işlevini veya [__debugbreak](/cpp/intrinsics/debugbreak) iç öğesini çağırabilirsiniz. `DebugBreak` ve `__debugbreak` Bu konumda bir kesme noktası ayarlamaya aynı etkiye sahiptir.

 `DebugBreak`Bir sistem işlevine yapılan bir çağrı olduğundan, doğru çağrı yığını bilgilerinin koparmadan sonra görüntülendiğinden emin olmak için sistem hata ayıklama simgelerinin yüklenmesi gerekir. Aksi takdirde, hata ayıklayıcı tarafından görünen çağrı yığını bilgileri bir çerçeve tarafından kapalı olabilir. Kullanıyorsanız `__debugbreak` , semboller gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Derleyici Iç bilgileri](/cpp/intrinsics/compiler-intrinsics)
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
