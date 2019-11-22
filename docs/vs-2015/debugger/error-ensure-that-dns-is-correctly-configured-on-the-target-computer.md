---
title: "Hata: DNS 'nin hedef bilgisayarda doğru yapılandırıldığından emin olun | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6815e21d0fe7af3a24f2fc36a4f448ec420c89de
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299747"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Hata: DNS'nin Hedef Bilgisayarda Doğru Yapılandırıldığından Emin Olma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzaktan hata ayıklama yapmaya çalışırken, aşağıdaki hata iletisini alabilirsiniz:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Bu ileti, hedef bilgisayar, Visual Studio hata ayıklayıcısı ana bilgisayar adını çözümleyemediğinde oluşur. Hedef bilgisayarda DNS ayarlarını denetleyin.  
  
- Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 veya Windows Server 2008 R2 'de DNS ayarınızı görüntüleme hakkında daha fazla bilgi için şunu yapın: **Başlat** menüsünde **Yardım ve destek**' i seçin ve ardından **TCP/IP ayarlarını değiştir**' i arayın.  
  
- Daha fazla bilgi için [Microsoft Windows Web sitesine](https://go.microsoft.com/fwlink/?LinkId=252720) gıdın ve **TCP/IP ayarlarını değiştir**'i arayın.  
  
  DNS sorununu gideremezseniz, farklı bir hesap altında Uzaktan Hata Ayıklayıcı'yı çalıştırmayı deneyebilirsiniz. Bu hata yalnızca Yerel Sistem veya Ağ Hizmeti hesabı altında Uzaktan Hata Ayıklayıcı'yı çalıştırırken oluşur. Uzaktan Haya Ayıklayıcı'yı başka bir hesap altında çalıştırırsanız, DNS gerektirmeyen NTLM kimlik doğrulaması kullanabilir. . Yordam için bkz. [hata: hedef bilgisayardaki Visual Studio uzaktan hata ayıklayıcı hizmeti bu bilgisayara geri bağlanamıyor](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
