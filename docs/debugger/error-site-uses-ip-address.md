---
description: Hata ayıklayıcısı IP adresi kullanan bir Web uygulamasına otomatik olarak eklemeye çalıştığında bu hata oluşur.
title: Site IP Adresi | Microsoft Docs
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f141cf050e41e5f2a30b66c47e68b1b3c35aeb5c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030912"
---
# <a name="error-site-uses-ip-address"></a>Hata: Site IP Adresi Kullanıyor
Hata ayıklayıcısı IP adresi kullanan bir Web uygulamasına otomatik olarak eklemeye çalıştığında bu hata oluşur. Bu durum, Web sitesi tanımlamayı **IIS'de belirli** **BIR IP adresi kullanmak üzere değiştirirsiniz.**

 Otomatik eklemenin çalışması için projeyi yalnızca makine adı yerine belirli bir IP adresiyle oluşturmanız gerekir. Aksi takdirde, hata ayıklayıcı makine adını localhost olarak değiştirir ve bu da hata ayıklama fiilinin IIS'ye gönderilebeğine neden olur.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Bunun yerine el ile ekleme kullanın (Hata Ayıklama menüsünde İşleme **Ekle'yi seçin).**

     —veya—

2. IIS **Web sitesi tanımlama ayarını** değiştirme.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
