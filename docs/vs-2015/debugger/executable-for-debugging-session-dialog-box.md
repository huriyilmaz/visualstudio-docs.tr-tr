---
title: Hata ayıklama oturumu için yürütülebilir Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2ee71c5e23b0c5784cd2fe9b57b46fe28d41d30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157463"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Hata Ayıklama Oturumu İçin Yürütülebilir İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu iletişim kutusu, çalıştırılabilir dosya belirtilmediğinde bir DLL 'de hata ayıklamaya çalıştığınızda görüntülenir. Visual Studio doğrudan DLL 'yi başlatamaz. Bunun yerine, belirtilen yürütülebiliri başlatacaktır. Yürütülebilir dosya tarafından çağrıldığında DLL 'de hata ayıklaması yapabilirsiniz.  
  
 **Yürütülebilir dosya adı**  
 Hata ayıklaması yaptığınız DLL 'yi çağıran bir yürütülebilir dosyanın yolunu girin.  
  
 **Projenin erişilebileceği URL (yalnızca ATL sunucusu)**  
 ATL sunucu DLL dosyasında hata ayıklaması yapıyorsanız, projenin bulunabileceği URL 'YI girin.  
  
 Bu ayarlar girildikten sonra proje özellik sayfalarında depolanır, bu nedenle sonraki hata ayıklama oturumları için bunları yeniden girmeniz gerekmez. Ayarları değiştirmeniz gerekiyorsa, özellik sayfalarını açıp değerleri değiştirebilirsiniz. Hata ayıklama oturumu için yürütülebilir dosya belirtme hakkında daha fazla bilgi için bkz. [hata ayıklama dll 'leri](../debugger/how-to-debug-native-dlls.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da Hata Ayıklama](../debugger/debugging-in-visual-studio.md)
