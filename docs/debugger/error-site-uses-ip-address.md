---
title: Hata-site IP adresini kullanıyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58db12ba9dbbc9526ac86262a6be5b2c0a7f765e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460552"
---
# <a name="error-site-uses-ip-address"></a>Hata: Site IP Adresi Kullanıyor
Hata ayıklayıcı bir IP adresi kullanan bir Web uygulamasına otomatik olarak iliştirmeye çalıştığında bu hata oluşur. Bu durum, **Web sitesi KIMLIĞINI** IIS 'de **belirli IP adresini kullanacak** şekilde değiştirirseniz oluşur.

 Otomatik iliştirme 'nin çalışması için, projeyi yalnızca makine adı yerine belirli bir IP adresi ile oluşturmanız gerekir. Aksi takdirde, hata ayıklayıcı makine adını localhost olarak değiştirecek, bu da hata ayıklama fiilini IIS 'e gönderememesine neden olur.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Yerine el ile iliştirme kullanın (hata ayıklama menüsünden **Işleme İliştir**' i seçin).

     —veya—

2. **IIS Web sitesi kimlik** ayarını değiştirin.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)