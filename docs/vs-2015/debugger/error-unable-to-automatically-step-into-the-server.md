---
title: 'Hata: sunucuda otomatik olarak adımla | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8dcb8fa757f1cccf2f3aef6c2520e0c61da0b9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682674"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Hata: Sunucunun İçine Otomatik Olarak Adımlanamıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata şunu okur:  
  
 Otomatik olarak sunucuda adım adım alınamıyor. Uzaktan yordam yürütülmeden önce hata ayıklayıcıya bildirimde bulunulmadı  
  
 Bu hata, bir Web hizmetine (bkz. [BIR XML Web hizmeti Içine adımla](https://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)) çalışırken ortaya çıkabilir. Düzgün kurulmamış her zaman oluşabilir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
 Olası nedenler şunlardır:  
  
- Uygulamanız için web.config dosyası [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ' de hata ayıklamayı "true" olarak ayarladı (bkz. [ASP.NET uygulamalarında hata ayıklama modu](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Visual Studio yüklendikten sonra bir sürümü yüklendi. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Visual Studio 'dan önce yüklenmelidir. Bu sorunu gidermek için, Visual Studio yüklemenizi onarmak üzere Windows **Denetim Masası**, **Programlar ve Özellikler** ' i kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
