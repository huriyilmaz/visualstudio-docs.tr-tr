---
title: Tam zamanında hata ayıklayıcıyı devre dışı bırakın | Microsoft Docs
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3155c2cdc9ea3dc5208a52e5fe37f697a4ad5ef6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386127"
---
# <a name="disable-the-just-in-time-debugger"></a>Anında Hata Ayıklayıcı’yı devre dışı bırakma

Çalışan bir uygulamada hata oluştuğunda tam zamanında hata ayıklayıcı iletişim kutusu açılabilir ve uygulamanın devam etmesini engelleyebilirsiniz.

Tam zamanında hata ayıklayıcı, hata ayıklamak için Visual Studio 'Yu başlatma seçeneği sunar. Hatayla ilgili ayrıntılı bilgileri görüntülemek veya hata ayıklamayı denemek için Visual Studio veya başka bir seçili hata ayıklayıcı yüklü olmalıdır.

Zaten bir Visual Studio kullanıcısı ve hata ayıklamayı denemek istiyorsanız, [tam zamanında hata ayıklayıcı kullanarak hata ayıkla](../debugger/debug-using-the-just-in-time-debugger.md)bölümüne bakın. Hatayı düzeltemedi veya tam zamanında hata ayıklayıcıyı açmak istiyorsanız, [Visual Studio 'Da tam zamanında hata ayıklamayı devre dışı](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)bırakabilirsiniz.

Visual Studio yüklüyse ancak artık bunu yapmazsanız, [Windows kayıt defterinden tam zamanında hata ayıklamayı devre dışı bırakmanız](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)gerekebilir.

Visual Studio yüklü değilse, betik hata ayıklamayı veya sunucu tarafı hata ayıklamayı devre dışı bırakarak tam zamanında hata ayıklamayı engelleyebilirsiniz.

- Bir Web uygulamasını çalıştırmaya çalışıyorsanız, betik hata ayıklamayı devre dışı bırakın:

  Windows **Denetim Masası**  >  **Ağ ve Internet**  >  **Internet seçenekleri**'nde, **betik hata ayıklamayı devre dışı bırak (Internet Explorer)** ve **betik hata ayıklamayı devre dışı bırak (diğer)** seçeneğini Tam adımlar ve ayarlar, Windows sürümünüze ve tarayıcınıza bağlıdır.

  ![JıT Internet seçenekleri](../debugger/media/jitinternetoptions.png "JıT Internet seçenekleri")

- IIS 'de bir ASP.NET Web uygulaması barındırıyorsanız, sunucu tarafı hata ayıklamayı devre dışı bırakın:

  1. IIS Yöneticisi **Özellikler görünümünde**, **ASP.net** bölümü altında, **.NET derlemesi**' ne çift tıklayın veya seçin ve ardından **Eylemler** bölmesinde **özelliği aç** ' ı seçin.
  1. **Davranış**  >  **hata ayıklaması**altında **yanlış**' ı seçin. Adımlar, IIS 'nin eski sürümlerinde farklıdır.

Tam zamanında hata ayıklamayı devre dışı bıraktıktan sonra, uygulama hatayı işleyebilir ve normal şekilde çalıştırabilir.

Uygulamada hala işlenmeyen bir hata varsa, bir hata iletisi görebilirsiniz veya uygulama kilitlenebilir veya yanıt vermeyi durdurabilir. Uygulama, hata düzeltilene kadar normal şekilde çalışmaz. Uygulamanın sahibine başvurarak bu uygulamayı çözmesini deneyebilirsiniz.
