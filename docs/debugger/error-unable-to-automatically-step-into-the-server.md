---
title: Sunucu SunucusuNa Otomatik Olarak Adımlama | Microsoft Docs
description: Sunucuya Otomatik Olarak Adımlama. Uzaktan yordam yürütülmeden önce hata ayıklayıcıya bildirildi.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a4f2f2dfc0e4b9a9cb6bc723e64c0172ab4be532d4128a5255d38b49e4a9452f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419890"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Hata: Sunucunun İçine Otomatik Olarak Adımlanamıyor
Hata şunları okur:

 Sunucuya Otomatik Olarak Adımlama. Uzaktan yordam yürütülmeden önce hata ayıklayıcıya bildirildi

 Bu hata, bir web hizmetine adımlama sırasında oluşabilir (bkz. [XML Web Hizmetine Adımlama).](/previous-versions/zc57803s(v=vs.100)) Düzgün [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ayarlanmazsa bu durum oluşabilir.

 Olası nedenler:

- Uygulamanıza web.config dosyası içinde hata ayıklamayı [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] "true" olarak ayarlamaz (bkz. ASP.NET [Uygulamalarında Hata Ayıklama Modu).](../debugger/how-to-enable-debugging-for-aspnet-applications.md)

- bir sürümü [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yüklendikten sonra Visual Studio yüklendi. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]yüklemeden önce Visual Studio. Bu sorunu çözmek için Windows **Denetim Masası > Programlar ve Özellikler'i** kullanarak Visual Studio onarın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
