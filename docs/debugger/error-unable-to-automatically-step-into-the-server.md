---
title: Sunucuda otomatik olarak adımaktarılamıyor | Microsoft Docs
description: Otomatik olarak sunucuda adım adım alınamıyor. Uzaktan yordam yürütülmeden önce hata ayıklayıcıya bildirimde bulunulmadı.
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
ms.openlocfilehash: aa422872c2c57d9fb4515692e051f7eb795766dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065611"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Hata: Sunucunun İçine Otomatik Olarak Adımlanamıyor
Hata şunu okur:

 Otomatik olarak sunucuda adım adım alınamıyor. Uzaktan yordam yürütülmeden önce hata ayıklayıcıya bildirimde bulunulmadı

 Bu hata, bir Web hizmetine (bkz. [BIR XML Web hizmeti Içine adımla](/previous-versions/zc57803s(v=vs.100))) çalışırken ortaya çıkabilir. Düzgün kurulmamış her zaman oluşabilir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

 Olası nedenler şunlardır:

- uygulamanız için web.config dosyası [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ' de hata ayıklamayı "true" olarak ayarladı (bkz. [ASP.NET uygulamalarda hata ayıklama modu](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Visual Studio yüklendikten sonra bir sürümü yüklendi. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Visual Studio önce yüklenmelidir. bu sorunu gidermek için Visual Studio yüklemenizi onarmak üzere **programlar ve özellikler > Windows denetim masası** 'nı kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
