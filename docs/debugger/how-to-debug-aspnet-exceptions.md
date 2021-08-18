---
title: Özel ASP.NET Hata Ayıklama | Microsoft Docs
description: Hata ayıklayıcının uygulamanıza işlanmamış özel durumlar için durarak ASP.NET öğrenin. Kesmenin sistem dışı kodda oluştuğundan emin olabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: d8e1ffd49153ba51b8b636ba30d756a3975680b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161264"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Nasıl Yapılır: ASP.NET Özel Durumlarında Hata Ayıklama
Özel durumlarda hata ayıklama, sağlam bir uygulama geliştirmenin önemli bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kısmıdır. Özel durumların hata ayıklaması hakkında genel bilgiler Hata [Ayıklayıcı ile Özel Durumları Yönetme konusundadır.](../debugger/managing-exceptions-with-the-debugger.md)

 İşlenemeyen özel [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] durumlarda hata ayıklamak için, hata ayıklayıcının onlar için durduğundan emin olun. Çalışma [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zamanının üst düzey bir özel durum işleyicisi vardır. Bu nedenle, hata ayıklayıcı varsayılan olarak işlanmamış özel durumlarda hiçbir zaman kesmez. Bir özel durum sızıp hata ayıklayıcıya girebilirsiniz. Özel durumlar iletişim kutusunda Özel durumlar: Bu özel durum için **thrown** ayarı olduğunda **Kesme'yi** seçmeniz gerekir.

 Özel durum olduğunda Yalnızca kendi kodum **etkinleştirdiyseniz:** Bir .NET yönteminde veya başka bir sistem kodunda özel durum etkinleştirilmişse hata ayıklayıcı hemen kesmeye neden olmaz. Bunun yerine, hata ayıklayıcı sistem dışı koda isabet edene kadar yürütme devam eder ve ardından hata ayıklar. Sonuç olarak, bir özel durum oluştuğunda sistem kodunda adım adım ilerlersiniz.

 Yalnızca kendi kodum daha kullanışlı olacak başka bir seçenek daha sağlar: Özel durum olduğunda **kesme: Kullanıcı tarafından işlanmamış**. Bir özel durum için bu ayarı seçerseniz, hata ayıklayıcı kullanıcı kodunda yürütmeyi bozabilir, ancak yalnızca özel durum yakalanmaz ve kullanıcı kodu tarafından işlanmazsa. Bu ayar, işleyici kullanıcı olmayan kodda olduğundan üst düzey özel durum [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işleyicinin etkisini olumsuz etkilemektedir.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Özel durumlarda hata ayıklamayı ASP.NET için Yalnızca kendi kodum

1. Hata Ayıklama **menüsünde Özel** Durumlar'a **tıklayın.**

     Özel **Durumlar iletişim** kutusu görüntülenir.

2. Ortak Dil **Çalışma Zamanı Özel Durumları satırda,** **Thrown veya** **User-unhandled seçeneğini seçin.**

     Kullanıcı tarafından **iş ayarlanmamış ayarını kullanmak** için **Yalnızca kendi kodum** etkinleştirilmesi gerekir.

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Özel durum işleme için en ASP.NET yöntemleri kullanmak için

- Kodun `try ... catch` çevreye bloklar, işleyebilirsiniz ve nasıl işleyebilirsiniz tahmin etmek ve bilmek özel durumlar oluşturur. Örneğin, uygulama bir XML Web Hizmetine veya doğrudan bir SQL Server çağrıları yapıyorsa, bu kod denemede **... oluşabilir** çok sayıda özel durum olduğundan catch blokları.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET Uygulamalarında Hata Ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
