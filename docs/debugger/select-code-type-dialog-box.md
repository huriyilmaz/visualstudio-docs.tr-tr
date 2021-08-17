---
title: Kod Türü Seç İletişim Kutusu | Microsoft Docs
description: Dosyanın Kod Türünü Seç iletişim kutusu hakkında Visual Studio. Bu iletişim kutusunu açmak için İşleme Ekle iletişim kutusunu açın ve seç düğmesine tıklayın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 66b7d9d5b63bad3d94accc8a87bbbdbcf1c49dbccdbde9b84fb21cd34362b6a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435835"
---
# <a name="select-code-type-dialog-box"></a>Kod Türünü Seç İletişim Kutusu

Bu iletişim kutusunu açmak için İşleme **Ekle iletişim** kutusunu açın ve seç **düğmesine** tıklayın.

**Hata ayıklamak için kod türünü otomatik olarak belirleme** Uygun hata ayıklayıcı, çalışan koda göre seçilir.

**Şu kod türlerinde hata ayıklama:** Sağlanan listeden, hata ayıklamak istediğiniz kod türünü seçin. Bu, ekleme [hatasıyla ilgili sorunları giderirken yararlı olabilir.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors) Bu seçenek, algılamayı yalnızca hata ayıklamak istediğiniz kod türleriyle kısıtlar.

::: moniker range=">=vs-2019"
- Blazor WebAssembly - İstemci tarafı Blazor WebAssembly
- GPU - Yazılım Emulator - GPU yazılım öykünücüsünü çalıştıran C++ kodu
- JavaScript (Chrome) - Chrome'da çalışan JavaScript
- JavaScript (Microsoft Edge - Chromium) - Chromium tabanlı Microsoft Edge JavaScript Windows 10
- Bir CDP istemcisinde hata ayıklama için kullanılan JavaScript CDP (V3) Hata Ayıklayıcısı - Chrome DevTools Protokolü sürüm 3
- Yönetilen (CoreCLR) - .NET Core
- Yönetilen (Yerel derleme) - C++/CLR kodu
- Yönetilen (v3.5, v3.0, v2.0) - .NET Framework 2.0 ve daha yüksek (3.5'e kadar) için .NET Framework kodu
- Yönetilen (v.4.6, v4.5, v4.0) - .NET Framework 4.0 ve .NET Framework için .NET Framework kodu
- Yerel - C/C++
- Node.js Ayıklama - Node.js çalışma zamanı tarafından barındırılan kod
- Python - Python 
- Betik - JavaScript için genel betik hata ayıklayıcısını belirtir. Senaryo için geçerli olan JavaScript (Chrome) gibi daha kısıtlayıcı seçenekleri kullanın.
- T-SQL - Transact-SQL
- Unity - Unity
- Yönetilen Uyumluluk Modu - Yönetilen kod için, genellikle C++/CLR koduyla karışık modda hata ayıklamada kullanmak (karma mod için Düzenle ve Devam'ı sağlar) veya eski hata ayıklayıcıyı hedef alan uzantıları desteklemek için eski hata ayıklayıcısını belirtir. Çoğu karma mod hata ayıklama senaryosunda, Yönetilen **Uyumluluk** Modu yerine Yerel **ve** uygun Yönetilen kod türlerini seçin.
::: moniker-end

Çoğu senaryo için, aynı hata ayıklama oturumunda birden çok hata ayıklayıcısı eklemek desteklenmiyor. Bunu, uygulamanın ikinci bir örneğini kullanarak Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
