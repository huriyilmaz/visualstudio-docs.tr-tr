---
title: Tam Zamanında Hata Ayıklayıcı hata ayıklayıcısını devre dışı | Microsoft Docs
description: Uygulamada bir hata oluştuğunda Tam Zamanında Hata Ayıklayıcı iletişim kutusu açabilirsiniz. Bu olduğunda neler yapabilirsiniz ve bunu önlemenin yollarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b9d0c820877d30d0228c996538e320508dad2661
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080786"
---
# <a name="disable-the-just-in-time-debugger"></a>Anında Hata Ayıklayıcı’yı devre dışı bırakma

Çalışan bir uygulamada hata oluştuğunda Tam Zamanında Hata Ayıklayıcısı iletişim kutusu açabiliyor ve uygulamanın devam ettirilene kadar devam ettirilene kadar devam ediyor.

Tam Zamanında Hata Ayıklayıcı, hatada hata ayıklamak için Visual Studio başlatma seçeneği verir. Hata hakkında ayrıntılı Visual Studio görüntülemek veya hata ayıklamayı denemek için bir hata ayıklayıcısı veya seçili başka bir hata ayıklayıcı yüklü olması gerekir.

Zaten bir kullanıcı Visual Studio hata ayıklamayı denemek için bkz. Tam Zamanında Hata [Ayıklayıcı'sını kullanarak hata ayıklama.](../debugger/debug-using-the-just-in-time-debugger.md) Hatayı düzelte istemiyorsanız veya Tam Zamanında Hata Ayıklayıcı'nın açılmasını istemiyorsanız, hata ayıklamayı zaman içinde [Visual Studio.](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)

Yüklemesi Visual Studio ancak artık yüklenemediyse, kayıt defterinden Tam Zamanında hata ayıklamayı [devre dışı Windows gerekir.](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)

Henüz yüklü Visual Studio betik hata ayıklamayı veya sunucu tarafı hata ayıklamayı devre dışı bırakarak Tam Zamanında hata ayıklamayı önleyebilirsiniz.

- Bir web uygulaması çalıştırmaya çalışıyorsanız betik hata ayıklamayı devre dışı bırakma:

  Ağ Windows **Denetim Masası** İnternet Seçenekleri'ne tıklayın, Betik hata ayıklamasını devre dışı bırak (Internet Explorer) ve Betik hata ayıklamasını devre dışı bırak  >    >    **(diğer) seçeneğini belirleyin.** Tam adımlar ve ayarlar, Windows sürümünüze bağlıdır.

  ![JIT İnternet Seçenekleri](../debugger/media/jitinternetoptions.png "JIT internet seçenekleri")

- IIS'de bir ASP.NET web uygulaması barındırıyorsanız sunucu tarafı hata ayıklamayı devre dışı bırakma:

  1. IIS Yöneticisi **Özellikleri Görünümü'nde,** **ASP.NET** bölümünde **.NET** Derlemesi'ne çift tıklayın  veya seçin ve ardından Eylemler bölmesinde Özelliği **Aç'ı** seçin.
  1. Davranış **Hata**  >  **Ayıklama'nın altında** Yanlış'ı **seçin.** Adımlar, IIS'nin eski sürümlerinde farklıdır.

Tam Zamanında hata ayıklamayı devre dışı bırakarak, uygulama hatayı işebilir ve normal şekilde çalıştırabilirsiniz.

Uygulama hala iş görmüyorsa bir hata iletisi görebilir veya uygulamanın kilitlenmesi veya yanıt vermenin durdurması. Hata düzeltene kadar uygulama normal şekilde çalışmaz. Uygulamanın sahibiyle iletişime geçebilirsiniz ve düzeltmelerini sebilirsiniz.
