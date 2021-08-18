---
title: Özel durumu inceleme
titleSuffix: ''
description: Özel durumlarda hata ayıklamanıza Visual Studio ve özel durumlarda hata ayıklamayı seçmeli olarak devre dışı bırakma hakkında bilgi edinebilirsiniz.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0b93a717d4a3f22db860f2bbef51bc51e0f8cc85
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139060"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Özel Durum Yardımcı'sı kullanarak özel durumu inceleme 

Teknolojiniz veya uzmanlık düzeyiniz ne olursa olsun özel durumlarla ilgilenmek yaygın bir sorundur. Özel durumların kodunda sorunlara neden olduğunu anlamak can sıkıcı bir deneyim olabilir. Visual Studio'da bir özel durum için hata ayıklarken, sorunda daha hızlı hata ayıklamanıza yardımcı olacak ilgili özel durum bilgileri sağlayarak bu hayal kırıklığını hafifletebilirsiniz.

![Özel Durum Yardımcı](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Özel durum üzerinde duraklatma
Hata ayıklayıcı bir özel durum üzerinde hata ayıklayıcıda kırılırsa, bu kod satırın sağ yanında bir özel durum hata simgesi görünür. Kalıcı olmayan bir Özel Durum yardımcı, özel durum simgesinin yakınında görünür.

![Bir kod satırı yanındaki özel durum yardımcı](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Özel durum bilgilerini inceleme
Özel Durum Yardımcısı'nın özel durum türünü ve özel durum iletiyi anında okuyabilir ve özel durumun at mı yoksa işsüz olarak mı olduğunu okuyabilirsiniz. Ayrıntıları Görüntüle bağlantısına tıklayarak Özel Durum nesnesinin özelliklerini inceler **ve görüntüebilirsiniz.**

## <a name="analyze-null-references"></a>Null başvuruları analiz etme
2017'Visual Studio başlayarak, hem .Net hem de C/C++ kodu için veya değerine isabet ettiyken, Özel Durum Yardımcı'da null analiz `NullReferenceException` `AccessViolation` bilgileri görüyorsunuz. Analiz, özel durum iletisi altında metin olarak görüntülenir. Aşağıdaki çizimde bilgiler " s **was** null" olarak gösterilmiştir.

![Özel durum yardımcı null analizi](media/debugger-exception-helper-default.png)


> [!NOTE]
> Yönetilen kodda null başvuru analizi için .NET sürüm 4.6.2 gerekir. Null analizi şu anda Universal Windows Platform (UWP) ve diğer .NET Core uygulamaları için desteklenmiyor. Yalnızca herhangi bir Tam Zamanında (JIT) kod iyileştirmesi olmayan kodlarda hata ayıklarken kullanılabilir.

## <a name="configure-exception-settings"></a>Özel durum ayarlarını yapılandırma 
Özel Durum Yardımcısı'nın Özel Durum Bilgileri bölümünden geçerli türde  bir özel durum Ayarlar hata ayıklayıcıyı bozacak şekilde yapılandırabilirsiniz. Hata ayıklayıcı bir özel durum sırasında duraklatıldı ise, gelecekte sızan özel durum türünde hata ayıklamayı devre dışı bırakmak için onay kutusunu kullanabilirsiniz. Bu modülde 30. özel durumu bozmak istemiyorsanız, Özel durum denetimi penceresindeKimlik durumu penceresindeki Şu özel durumdan sızan durumlar altındaki modül adına göre onay **kutusunu işaretleyin** **Ayarlar.** 

## <a name="inspect-inner-exceptions"></a>İç özel durumları inceleme 
Özel durumda herhangi bir iç özel durum varsa ([InnerException),](/dotnet/api/system.exception.innerexception)bunları Özel Durum Yardımcısı'da görüntüabilirsiniz. Birden çok özel durum varsa, çağrı yığınının üzerinde gösterilen sol ve sağ okları kullanarak bunlar arasında gezinebilirsiniz.

![İç özel durum ile özel durum yardımcı](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Yenidenrown özel durumlarını inceleme
Bir özel durumun Özel Durum Yardımcı olduğu durumlarda, özel durum ilk kez `thrown` sızan çağrı yığınını gösterir. Özel durum birden çok kez oluşturduysanız, yalnızca özgün özel durumun çağrı yığını gösterilir.

![Yenidenrown özel durumlarını olan özel durum yardımcı](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Hata ayıklama oturumunu Live Share
Özel Durum Yardımcı'dan, Oturum [](/visualstudio/liveshare/) Live Share başlat... bağlantısını **kullanarak bir Live Share başlatabilirsiniz.** Oturuma katılarak Live Share özel durum yardımcısını ve diğer hata ayıklama bilgilerini görebilir.