---
title: Kod türünü seç Iletişim kutusu | Microsoft Docs
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ccfe636cd8981c2f9dcc1375fb795d6c026b572
ms.sourcegitcommit: 5e82a428795749c594f71300ab03a935dc1d523b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86211584"
---
# <a name="select-code-type-dialog-box"></a>Kod Türünü Seç İletişim Kutusu

Bu iletişim kutusunu açmak için **Işleme İliştir** iletişim kutusunu açın ve ardından **Seç** düğmesine tıklayın.

**Hata ayıklaması yapılacak kodun türünü otomatik olarak belirle** Uygun hata ayıklayıcı, çalıştıran kod türüne göre seçilir.

**Bu kod türlerinde hata ayıkla:** Belirtilen listeden, hata ayıklamak istediğiniz kodun türlerini seçin. Bu, [iliştirme hatası giderirken](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors)yararlı olabilir. Bu seçenek, algılamayı yalnızca hata ayıklamak istediğiniz kod türleri olarak kısıtlar.

   ::: moniker range=">=vs-2019"
   - Blazor WebAssembly-İstemci tarafıBlazor WebAssembly
   - GPU-yazılım öykünücüsü-bir GPU yazılım öykünücüsü üzerinde çalışan C++ kodu
   - JavaScript (Chrome)-Chrome 'da çalışan JavaScript
   - JavaScript (Microsoft Edge-Kmıum)-Windows 10 için Kmıum tabanlı Microsoft Edge 'de çalışan JavaScript
   - JavaScript CDP (v3) hata ayıklayıcı-bir CDP istemcisinde hata ayıklama için kullanılan Chrome DevTools protokol sürüm 3
   - Yönetilen (CoreCLR)-.NET Core
   - Yönetilen (yerel derleme)-C++/CLR kodu
   - Yönetilen (v 3.5, v 3.0, v 2.0)-.NET Framework 2,0 ve üzeri için .NET Framework kodu (3,5 ' e kadar)
   - Yönetilen (v. 4.6, v 4.5, v 4.0)-.NET Framework 4,0 ve üzeri için .NET Framework kodu
   - Yerel-C/C++
   - Node.js hata ayıklama-Node.js çalışma zamanı tarafından barındırılan kod
   - Python-python 
   - Betik-JavaScript için genel betik hata ayıklayıcısını belirtir. Senaryolarınız için JavaScript (Chrome) gibi daha kısıtlayıcı seçenekleri kullanın.
   - T-SQL-Transact-SQL
   - Unity-Unity
   - Yönetilen Uyumluluk modu-yönetilen kod için eski hata ayıklayıcıyı, genellikle C++/CLR kodu ile karışık modda hata ayıklamada kullanılmak üzere (karışık mod için Düzenle ve devam et ' i sağlar) veya eski hata ayıklayıcıyı hedefleyen uzantıları desteklemek için belirtir. Çoğu karma mod hata ayıklama senaryosunda, **Yerel** ve yönetilen uyumluluk modu yerine uygun **yönetilen** kod türlerini seçin.
   ::: moniker-end

   Çoğu senaryoda, aynı hata ayıklama oturumunda birden çok hata ayıklayıcıları eklemek desteklenmez. Bunu, Visual Studio 'nun ikinci bir örneğini kullanarak yapabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
