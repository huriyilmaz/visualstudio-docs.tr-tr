---
title: 'Hata: sunucuda otomatik olarak adımla | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 34b298b299bb4911bfe64b362d94c3e90ecfa585
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736868"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Hata: Sunucunun İçine Otomatik Olarak Adımlanamıyor
Hata şunu okur:

 Otomatik olarak sunucuda adım adım alınamıyor. Uzaktan yordam yürütülmeden önce hata ayıklayıcıya bildirimde bulunulmadı

 Bu hata, bir Web hizmetine (bkz. [BIR XML Web hizmeti Içine adımla](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)) çalışırken ortaya çıkabilir. @No__t_0 düzgün şekilde kurulmazdiğinde bu durum oluşabilir.

 Olası nedenler şunlardır:

- @No__t_0 uygulamanızın Web. config dosyası ' de hata ayıklamayı "true" olarak belirtmiyor (bkz. [ASP.NET uygulamalarında hata ayıklama modu](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Visual Studio yüklendikten sonra [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bir sürümü yüklendi. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], Visual Studio 'dan önce yüklenmelidir. Bu sorunu gidermek için, Visual Studio yüklemenizi onarmak üzere Windows **Denetim masası > programlar ve Özellikler** ' i kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)