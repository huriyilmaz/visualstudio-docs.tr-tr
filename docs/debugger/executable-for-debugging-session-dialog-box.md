---
title: Hata ayıklama oturumu için yürütülebilir Iletişim kutusu | Microsoft Docs
description: Bir DLL dosyasında hata ayıklamak için DLL 'yi çağırmak üzere bir yürütülebilir dosya belirtmeniz gerekir. Yürütülebilir dosya belirtilmediğinde görüntülenen iletişim kutusu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 528a34c6f9d7ecbe4ab3254e779441a4bc307239
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065585"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Hata Ayıklama Oturumu İçin Yürütülebilir İletişim Kutusu

Bu iletişim kutusu, çalıştırılabilir dosya belirtilmediğinde bir DLL 'de hata ayıklamaya çalıştığınızda görüntülenir. Visual Studio doğrudan DLL başlatamıyor. bunun yerine, Visual Studio belirtilen çalıştırılabiliri başlatır. Yürütülebilir dosya tarafından çağrıldığında DLL 'de hata ayıklaması yapabilirsiniz.

 **Yürütülebilir dosya adı** Hata ayıklaması yaptığınız DLL 'yi çağıran bir yürütülebilir dosyanın yolunu girin.

 **Projenin erişilebileceği URL (yalnızca atl sunucusu)** ATL sunucu DLL dosyasında hata ayıklaması yapıyorsanız, projenin bulunabileceği URL 'YI girin.

 Bu ayarlar girildikten sonra proje özelliği sayfalarında depolanır, bu nedenle sonraki hata ayıklama oturumları için bunları yeniden girmeniz gerekmez. Ayarları değiştirmeniz gerekiyorsa, özellik sayfalarını açıp değerleri değiştirebilirsiniz. Hata ayıklama oturumu için yürütülebilir dosya belirtme hakkında daha fazla bilgi için bkz. [hata ayıklama dll 'leri](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)