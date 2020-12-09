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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4f1f1a88ad30d5102043571473be0d72d71a054
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863055"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Hata Ayıklama Oturumu İçin Yürütülebilir İletişim Kutusu

Bu iletişim kutusu, çalıştırılabilir dosya belirtilmediğinde bir DLL 'de hata ayıklamaya çalıştığınızda görüntülenir. Visual Studio doğrudan bir DLL başlatamıyor. Bunun yerine, Visual Studio belirtilen yürütülebiliri başlatır. Yürütülebilir dosya tarafından çağrıldığında DLL 'de hata ayıklaması yapabilirsiniz.

 **Yürütülebilir dosya adı** Hata ayıklaması yaptığınız DLL 'yi çağıran bir yürütülebilir dosyanın yolunu girin.

 **Projenin erişilebileceği URL (yalnızca atl sunucusu)** ATL sunucu DLL dosyasında hata ayıklaması yapıyorsanız, projenin bulunabileceği URL 'YI girin.

 Bu ayarlar girildikten sonra proje özelliği sayfalarında depolanır, bu nedenle sonraki hata ayıklama oturumları için bunları yeniden girmeniz gerekmez. Ayarları değiştirmeniz gerekiyorsa, özellik sayfalarını açıp değerleri değiştirebilirsiniz. Hata ayıklama oturumu için yürütülebilir dosya belirtme hakkında daha fazla bilgi için bkz. [hata ayıklama dll 'leri](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)