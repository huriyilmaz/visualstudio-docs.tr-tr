---
title: 'Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b78ea0ca06a0ba9670e61cc065cf539ea21ebc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729771"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin
Bu uyarı iletişim kutusu, kısmen güvenilen kod içeren bir işleme iliştirdiyseniz ya da iliştirme gerçekleşmeden hemen önce güvenilmeyen bir kullanıcıya aitse görüntülenir. Kötü amaçlı kod içeren güvenilmeyen bir işlemin, hata ayıklamayı yapan bilgisayara zarar verme olasılığı vardır. İşleme güvenmediğiniz bir nedeniniz varsa, hata ayıklamayı engellemek için **iptal** ' e tıklamanız gerekir.

 Yasal bir senaryoda hata ayıklarken bu uyarıyı bastırmak için, Visual Studio 'yu kapatın ve bu kayıt defteri anahtarının değerini 1: olarak ayarlayın `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning` ve ardından Visual Studio 'yu yeniden başlatın. Senaryoda hata ayıklamayı tamamladıktan sonra değeri 0 olarak sıfırlayın ve Visual Studio 'Yu yeniden başlatın.

 "Güvenilen kullanıcılar",,, ve gibi .NET Framework yüklü olan bilgisayarlarda genellikle tanımlanan bir dizi standart Kullanıcı içerir `aspnet` `localsystem` `networkservice` `localservice` .

## <a name="uielement-list"></a>UIElement Listesi
 Hata ayıklamada istenen derlemenin ad adı

 Kullanıcı geçerli Kullanıcı

 Ekleyerek hata ayıklamaya devam etmek için bas ekleyin

 Iliştirmeyin işleme iliştirme

## <a name="see-also"></a>Ayrıca bkz.
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)