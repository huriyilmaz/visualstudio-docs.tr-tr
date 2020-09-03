---
title: 'Hata: Site IP adresini kullanıyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46eace1c566a2810c5914a49654f8393f425fdee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155748"
---
# <a name="error-site-uses-ip-address"></a>Hata: Site IP Adresi Kullanıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklayıcı bir IP adresi kullanan bir Web uygulamasına otomatik olarak iliştirmeye çalıştığında bu hata oluşur. Bu durum, **Web sitesi KIMLIĞINI** IIS 'de **belirli IP adresini kullanacak** şekilde değiştirirseniz oluşur.  
  
 Otomatik iliştirme 'nin çalışması için, projeyi yalnızca makine adı yerine belirli bir IP adresi ile oluşturmanız gerekir. Aksi takdirde, hata ayıklayıcı makine adını localhost olarak değiştirecek, bu da hata ayıklama fiilini IIS 'e gönderememesine neden olur.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yerine el ile iliştirme kullanın (hata ayıklama menüsünden **Işleme İliştir**' i seçin).  
  
     —veya—  
  
2. **IIS Web sitesi kimlik** ayarını değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
