---
title: Özel durum İnceleme
titleSuffix: ''
description: Visual Studio 'Nun özel durumların hatalarını ayıklamanıza yardımcı olmak için sağladığı bilgiler ve özel durumların kesilmesini seçmeli olarak devre dışı bırakma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 1/18/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e10dc341ce33ba91c05348e9d3fba545437ce497
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870863"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Özel durum yardımcısını kullanarak özel bir durum inceleyin 

Özel durumlarla uğraşıyorsanız, teknolojiniz veya uzmanlık düzeyi ne olduğuna bakılmaksızın yaygın bir sorundur. Özel durumların kodunuzda sorunlara neden olduğunu ortaya çıkan, sinir bozucu bir deneyim olabilir. Visual Studio 'da bir özel durumun hatalarını ayıkladığınızda, sorununuzu daha hızlı ayıklamanıza yardımcı olacak ilgili özel durum bilgilerini sağlayarak bu sorunu gidermek istiyoruz.

![Özel durum Yardımcısı](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Özel durum üzerinde Duraklat
Hata ayıklayıcı bir özel durumu kaparsa, bu kod satırının sağında bir özel durum hatası simgesi görüntülenir. Özel durum simgesinin yakınında, kalıcı olmayan bir özel durum Yardımcısı görüntülenir.

![Kod satırının yanında özel durum Yardımcısı](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Özel durum bilgisini İncele
Özel durum Yardımcısı 'nda özel durum türünü ve özel durum iletisini anında okuyabilir ve özel durumun oluşturulup oluşturulmayacağını veya işlenmemiş olduğunu görebilirsiniz. **Ayrıntıları görüntüle** bağlantısına tıklayarak özel durum nesnesinin özelliklerini inceleyebilir ve görüntüleyebilirsiniz.

## <a name="analyze-null-references"></a>Null başvurularını çözümle
Visual Studio 2017 ' den başlayarak, hem .net hem de C/C++ kodu için, bir `NullReferenceException` veya bir veya bir yazdığınızda `AccessViolation` , özel durum Yardımcısı 'nda null analiz bilgilerini görürsünüz. Analiz, özel durum iletisinin altında metin olarak görüntülenir. Aşağıdaki çizimde, bilgiler "**s** null." olarak gösterilir.

![Özel durum Yardımcısı null Analizi](media/debugger-exception-helper-default.png)


> [!NOTE]
> Yönetilen kodda null başvuru analizi .NET Version 4.6.2 gerektirir. Null Analysis Şu anda Evrensel Windows Platformu (UWP) ve diğer .NET Core uygulamaları için desteklenmemektedir. Yalnızca bir tam zamanında (JıT) kod iyileştirmesi olmayan kod hata ayıklaması sırasında kullanılabilir.

## <a name="configure-exception-settings"></a>Özel durum ayarlarını yapılandırma 
Özel durum Yardımcısı 'nın **özel durum ayarları** bölümünden geçerli türde bir özel durum oluştuğunda, hata ayıklayıcıyı kesilecek şekilde yapılandırabilirsiniz. Hata ayıklayıcı oluşturulan bir özel durum üzerinde duraklatılmışsa, gelecekte oluşturulduğunda bu özel durum türünün kesilmesini devre dışı bırakmak için onay kutusunu kullanabilirsiniz. Bu belirli bir modülde oluşturulan bu özel durumun kesilmesini istemiyorsanız, **özel durum ayarları** penceresinde, ' **den şunun dışında:** ' ın altında modül adıyla onay kutusunu işaretleyin. 

## <a name="inspect-inner-exceptions"></a>İç özel durumları incele 
Özel durumun iç özel durumları varsa ([InnerException](/dotnet/api/system.exception.innerexception), bunları özel durum Yardımcısı 'nda görüntüleyebilirsiniz. Birden çok özel durum varsa, çağrı yığınının üzerinde gösterilen sol ve sağ okları kullanarak bunlar arasında gezinebilirsiniz.

![İç özel durum ile özel durum Yardımcısı](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Yeniden oluşturulan özel durumları incele
Bir özel durumun özel durum Yardımcısı olduğu durumlarda, özel durumun oluşturulduğu `thrown` ilk sefer çağrı yığınını gösterir. Özel durum birden çok kez oluşturulursa, yalnızca özgün özel durumdan gelen çağrı yığını gösterilir.

![Yeniden oluşturulan özel durumlarla özel durum Yardımcısı](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Live Share bir hata ayıklama oturumu paylaşma
Özel durum Yardımcısı ' ndan, bağlantı **başlatma Live Share oturumu..**. ' yi kullanarak bir [live share](/visualstudio/liveshare/) oturumu başlatabilirsiniz. Live Share oturumuna katılan herkes, diğer hata ayıklama bilgileriyle birlikte özel durum Yardımcısı 'nı görebilir.