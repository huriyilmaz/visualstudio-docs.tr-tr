---
description: Bu hata, IIS Yönetim hizmeti yanıt vermezse oluşur.
title: IIS Yönetici hizmeti yanıt vermediğinden bir güvenlik denetimi başarısız oldu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 111530647f28b6978af3e7269f2be3e6292988e0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134096"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Hata: IIS Yönetici Hizmeti Yanıt Vermediğinden Güvenlik Denetimi Başarısız
Bu hata, IIS Yönetim hizmeti yanıt vermezse oluşur. Bu, genellikle IIS yüklemesiyle ilgili bir sorun olduğunu gösterir. İlk olarak, hizmetin **yönetim araçlarından** **Hizmetler** aracını kullanarak çalıştığını doğrulayın.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- **Program Ekle veya Kaldır** denetim MASASıNı kullanarak IIS 'yi yeniden yükleyin.

- -veya-

- Program Ekle veya Kaldır denetim masasını kullanarak IIS 'yi makinenizden kaldırın. IIS 'yi kaldırdıysanız ve sorun yaşamaya devam ediyorsanız, kayıt defterini denetleyin ve bu anahtarın artık mevcut olmadığından emin olun:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     -veya-

- Yönetim Araçları denetim masasını kullanarak IIS Yönetim hizmetini devre dışı bırakın. Bu, makinenizde IIS 'yi devre dışı bırakır.

     Bu üç adımdan herhangi birini gerçekleştirdikten sonra makinenizi yeniden başlatın.

     Daha fazla bilgi için bkz. IIS belgeleri.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
