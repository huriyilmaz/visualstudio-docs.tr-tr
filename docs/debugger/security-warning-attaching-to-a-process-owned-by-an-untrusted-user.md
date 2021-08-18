---
description: Kısmen güvenilen kod içeren veya ekleme işlemi oluşmadan hemen önce güvenilmeyen bir kullanıcıya ait olan bir işleme eklendiğinde bu uyarı iletişim kutusu görüntülenir.
title: 'Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz bu işlemi | Microsoft Docs'
ms.date: 1/15/2021
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b0b60cc9a86f0eafce8378865b6161ef1c56a407
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090479"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin

Kısmen güvenilen kod içeren veya ekleme işlemi oluşmadan hemen önce güvenilmeyen bir kullanıcıya ait olan bir işleme eklendiğinde bu uyarı iletişim kutusu görüntülenir. Kötü amaçlı kod içeren güvenilmeyen bir işlem, hata ayıklamayı yapan bilgisayara zarar verebilir. İşleme güvenmeme nedenin varsa, hata ayıklamayı önlemek için **İptal'e** tıklamalısiniz.

IIS senaryolarında, güvenilmeyen bir özel uygulama havuzu kullanırsanız bu uyarıyı görebilirsiniz.

Geçerli bir senaryoda hata ayıklarken bu uyarıyı gizleme:

1. Visual Studio’yu kapatın.

1. Kayıt defteri anahtarının `DisableAttachSecurityWarning` değerini 1 olarak ayarlayın.

   altında anahtarı bulun veya oluşturun `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger` ve 1 olarak ayarlayın.

   2017'Visual Studio başlayarak, kayıt defteri ayarlarının tamamını görüntülemek için özel kayıt defteri kovanını yüklemeniz gerekir. Daha fazla bilgi için [bkz. 2017](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md)kayıt Visual Studio inceleme. Özel kayıt defteri kovanını kaldırmadan önce özel kayıt defteri kovanını kaldırmayı Visual Studio.

1. Visual Studio’yu yeniden başlatın.

1. Senaryoda hata ayıklamayı bitirdikten sonra değeri 0 olarak sıfırlayın ve yeniden başlatın Visual Studio.

"Güvenilen kullanıcılar" kendinizin yanı sıra, genellikle , , ve gibi yük .NET Framework bilgisayarlarda tanımlanan standart `aspnet` `localsystem` `networkservice` kullanıcılardan `localservice` bazılarıdır.

## <a name="uielement-list"></a>UIElement Listesi

 Hata ayıklamak için istenen derlemenin Ad Adı

 Kullanıcı Geçerli kullanıcı

 Ekle' tuşuna basarak hata ayıklamaya devam etmek için

 Ekleme İşleme ekleme

## <a name="see-also"></a>Ayrıca bkz.
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
