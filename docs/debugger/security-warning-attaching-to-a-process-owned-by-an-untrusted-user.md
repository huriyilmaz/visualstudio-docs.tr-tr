---
description: Bu uyarı iletişim kutusu, kısmen güvenilen kod içeren bir işleme iliştirdiyseniz ya da iliştirme gerçekleşmeden hemen önce güvenilmeyen bir kullanıcıya aitse görüntülenir.
title: 'Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin | Microsoft Docs'
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636633"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin

Bu uyarı iletişim kutusu, kısmen güvenilen kod içeren bir işleme iliştirdiyseniz ya da iliştirme gerçekleşmeden hemen önce güvenilmeyen bir kullanıcıya aitse görüntülenir. Kötü amaçlı kod içeren güvenilmeyen bir işlemin, hata ayıklamayı yapan bilgisayara zarar verme olasılığı vardır. İşleme güvenmediğiniz bir nedeniniz varsa, hata ayıklamayı engellemek için **iptal** ' e tıklamanız gerekir.

IIS senaryolarında, güvenilir olmayan özel bir uygulama havuzu kullanıyorsanız bu uyarıyı görebilirsiniz.

Meşru bir senaryoda hata ayıklarken bu uyarıyı bastırmak için:

1. Visual Studio’yu kapatın.

1. `DisableAttachSecurityWarning`Kayıt defteri anahtarının değerini 1 olarak ayarlayın.

   Altında anahtarı bulun veya oluşturun `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger` ve 1 olarak ayarlayın.

   Visual Studio 2017 ' den başlayarak, tüm kayıt defteri ayarlarını görüntülemek istiyorsanız, özel kayıt defteri kovanını yüklemeniz gerekir. daha fazla bilgi için bkz. [Visual Studio 2017 kayıt defterini inceleme](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md). Visual Studio başlatmadan önce özel kayıt defteri kovanını kaldırdığınızdan emin olun.

1. Visual Studio’yu yeniden başlatın.

1. Senaryoda hata ayıklamayı tamamladıktan sonra değeri 0 olarak sıfırlayın ve Visual Studio yeniden başlatın.

"güvenilen kullanıcılar",,, ve gibi .NET Framework yüklü olan bilgisayarlarda genellikle tanımlanan bir dizi standart kullanıcı içerir `aspnet` `localsystem` `networkservice` `localservice` .

## <a name="uielement-list"></a>UIElement Listesi

 Hata ayıklamada istenen derlemenin ad adı

 Kullanıcı geçerli Kullanıcı

 Ekleyerek hata ayıklamaya devam etmek için bas ekleyin

 Iliştirmeyin işleme iliştirme

## <a name="see-also"></a>Ayrıca bkz.
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
