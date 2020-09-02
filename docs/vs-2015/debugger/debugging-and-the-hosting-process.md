---
title: Hata ayıklama ve barındırma Işlemi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 10f3968367b188203671fa6bfff48bc482efe4f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157892"
---
# <a name="debugging-and-the-hosting-process"></a>Hata Ayıklama ve Barındırma İşlemi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio barındırma süreci hata ayıklayıcı performansını geliştirir ve kısmi güven hata ayıklama ve tasarım zamanı ifade değerlendirmesi gibi yeni hata ayıklayıcı özelliklerini sağlar. Gerekirse barındırma işlemini devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: barındırma Işlemini devre dışı bırakma](../ide/how-to-disable-the-hosting-process.md). Aşağıdaki bölümlerde, barındırma işlemi olmadan ve ile hata ayıklama arasındaki bazı farklılıklar açıklanır.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Kısmi güven hata ayıklama ve bir kez güvenlik  
 Kısmi güvenle hata ayıklama barındırma işlemini gerektirir. Barındırma işlemini devre dışı bırakırsanız, **proje özelliklerinin** **güvenlik** sayfasında kısmi güven güvenliği etkin olsa bile kısmi güven hata ayıklaması çalışmaz. Daha fazla bilgi için bkz. [nasıl yapılır: barındırma Işlemini devre dışı bırakma](../ide/how-to-disable-the-hosting-process.md) ve [nasıl yapılır: kısmi güven uygulamasında hata ayıklama](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Tasarım zamanı Ifade değerlendirmesi  
 Tasarım zamanı ifadesi her zaman barındırma işlemini kullanır. **Proje özelliklerindeki** barındırma işlemini devre dışı bırakmak, sınıf kitaplığı projeleri için tasarım zamanı ifade değerlendirmesini devre dışı bırakır. Diğer proje türleri için tasarım zamanı ifade değerlendirmesi devre dışı değildir. Bunun yerine, Visual Studio gerçek yürütülebiliri başlatır ve barındırma işlemi olmadan tasarım zamanı değerlendirmesi için kullanır. Bu fark farklı sonuçlar üretebilir.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain. CurrentDomain. FriendlyName farkları  
 `AppDomain.CurrentDomain.FriendlyName` barındırma işleminin etkin olup olmadığına bağlı olarak farklı sonuçlar döndürür. `AppDomain.CurrentDomain.FriendlyName`Barındırma işlemini etkin olarak çağırırsanız, *app_name*döndürür `.vhost.exe` . Bunu çağırırsanız barındırma işlemi devre dışı bırakılır, *app_name*döndürür `.exe` .  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly. GetCallingAssembly (). FullName farkları  
 `Assembly.GetCallingAssembly().FullName` barındırma işleminin etkin olup olmadığına bağlı olarak farklı sonuçlar döndürür. `Assembly.GetCallingAssembly().FullName`Barındırma işlemi etkin olarak çağırırsanız, döndürür `mscorlib` . `Assembly.GetCallingAssembly().FullName`Barındırma işlemi devre dışı olarak çağırırsanız, uygulama adını döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Işlemi (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Nasıl yapılır: kısmi güven uygulamasında hata ayıklama](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Nasıl Yapılır: Barındırma Sürecini Devre Dışı Bırakma](../ide/how-to-disable-the-hosting-process.md)
