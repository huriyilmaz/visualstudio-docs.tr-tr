---
title: DebugBreak ve __debugbreak | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea2a40943233e7dfffd3340f2e27da1d43a76a0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691170"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak ve __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodunuzda herhangi bir noktada DebugBreak Win32 işlevini veya [__debugbreak](https://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) iç öğesini çağırabilirsiniz. `DebugBreak` ve `__debugbreak` Bu konumda bir kesme noktası ayarlamaya aynı etkiye sahiptir.  
  
 `DebugBreak`Bir sistem işlevine yapılan bir çağrı olduğundan, doğru çağrı yığını bilgilerinin koparmadan sonra görüntülendiğinden emin olmak için sistem hata ayıklama simgelerinin yüklenmesi gerekir. Aksi takdirde, hata ayıklayıcı tarafından görünen çağrı yığını bilgileri bir çerçeve tarafından kapalı olabilir. Kullanıyorsanız `__debugbreak` , semboller gerekli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleyici Iç bilgileri](https://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
