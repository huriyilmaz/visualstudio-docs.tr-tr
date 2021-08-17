---
title: DebugBreak ve __debugbreak | Microsoft Docs
description: Programda kesme noktası ayarlanmış gibi, debugBreak işlevinin ve __debugbreak işlevinin programda kesintiye neden olmasına nasıl neden olduğunu öğrenin.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 707c660b658a4f1c34ab0faf345ff64c5063dc8f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052160"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak ve __debugbreak
[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Win32 işlevini veya [__debugbreak](/cpp/intrinsics/debugbreak) herhangi bir noktada iç işlevini çağırabilirsiniz. `DebugBreak` ve `__debugbreak` bu konumda bir kesme noktası ayarlamayla aynı etkiye sahiptir.

 bir sistem işlevine yapılan bir çağrı olduğundan, hata ayıklama sonrasında doğru çağrı yığını bilgisinin görüntülendiğinden emin olmak için `DebugBreak` sistem hata ayıklama sembolleri yükleniyor. Aksi takdirde, hata ayıklayıcı tarafından görüntülenen çağrı yığını bilgileri tek bir kareyle kapalı olabilir. `__debugbreak`kullanıyorsanız, semboller gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Derleyici IçLeri](/cpp/intrinsics/compiler-intrinsics)
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
