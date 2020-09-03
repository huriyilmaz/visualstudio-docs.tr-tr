---
title: Hata-sunucuda otomatik olarak adımla | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd85d5564bb6f8a0a5f4ead8c5a4ef8e1be48598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460292"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Hata: Sunucunun İçine Otomatik Olarak Adımlanamıyor
Hata şunu okur:

 Otomatik olarak sunucuda adım adım alınamıyor. Uzaktan yordam yürütülmeden önce hata ayıklayıcıya bildirimde bulunulmadı

 Bu hata, bir Web hizmetine (bkz. [BIR XML Web hizmeti Içine adımla](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)) çalışırken ortaya çıkabilir. Düzgün kurulmamış her zaman oluşabilir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

 Olası nedenler şunlardır:

- Uygulamanız için web.config dosyası [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ' de hata ayıklamayı "true" olarak ayarladı (bkz. [ASP.NET uygulamalarında hata ayıklama modu](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Visual Studio yüklendikten sonra bir sürümü yüklendi. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Visual Studio 'dan önce yüklenmelidir. Bu sorunu gidermek için, Visual Studio yüklemenizi onarmak üzere Windows **Denetim masası > programlar ve Özellikler** ' i kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)