---
title: 'Hata: IIS Yönetici hizmeti yanıt vermediğinden bir güvenlik denetimi başarısız oldu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
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
ms.openlocfilehash: f668de3d7c7e9a8bd075beb972199cf849feea65
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737881"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Hata: IIS Yönetici Hizmeti Yanıt Vermediğinden Güvenlik Denetimi Başarısız
Bu hata, IIS Yönetim hizmeti yanıt vermezse oluşur. Bu, genellikle IIS yüklemesiyle ilgili bir sorun olduğunu gösterir. İlk olarak, hizmetin **yönetim araçlarından** **Hizmetler** aracını kullanarak çalıştığını doğrulayın.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- **Program Ekle veya Kaldır** denetim MASASıNı kullanarak IIS 'yi yeniden yükleyin.

- veya

- Program Ekle veya Kaldır denetim masasını kullanarak IIS 'yi makinenizden kaldırın. IIS 'yi kaldırdıysanız ve sorun yaşamaya devam ediyorsanız, kayıt defterini denetleyin ve bu anahtarın artık mevcut olmadığından emin olun:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     veya

- Yönetim Araçları denetim masasını kullanarak IIS Yönetim hizmetini devre dışı bırakın. Bu, makinenizde IIS 'yi devre dışı bırakır.

     Bu üç adımdan herhangi birini gerçekleştirdikten sonra makinenizi yeniden başlatın.

     Daha fazla bilgi için bkz. IIS belgeleri.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)