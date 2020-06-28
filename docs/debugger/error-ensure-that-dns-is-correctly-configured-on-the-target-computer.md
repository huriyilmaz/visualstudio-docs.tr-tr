---
title: Hata-DNS 'nin hedef bilgisayarda doğru yapılandırıldığından emin olun | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e374e75caca3dec28800a2eac86d921c861888ab
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460831"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Hata: DNS'nin Hedef Bilgisayarda Doğru Yapılandırıldığından Emin Olma
Uzaktan hata ayıklama yapmaya çalışırken, aşağıdaki hata iletisini alabilirsiniz:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 Bu ileti, hedef bilgisayar, Visual Studio hata ayıklayıcısı ana bilgisayar adını çözümleyemediğinde oluşur. Hedef bilgisayarda DNS ayarlarını denetleyin.

- Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 veya Windows Server 2008 R2 'de DNS ayarınızı görüntüleme hakkında daha fazla bilgi için şunu yapın: **Başlat** menüsünde **Yardım ve destek**' i seçin ve ardından **TCP/IP ayarlarını değiştir**' i arayın.

- Daha fazla bilgi için [Microsoft Windows Web sitesine](https://www.microsoft.com/windows/) gıdın ve **TCP/IP ayarlarını değiştir**'i arayın.

  DNS sorununu gideremezseniz, farklı bir hesap altında Uzaktan Hata Ayıklayıcı'yı çalıştırmayı deneyebilirsiniz. Bu hata yalnızca Yerel Sistem veya Ağ Hizmeti hesabı altında Uzaktan Hata Ayıklayıcı'yı çalıştırırken oluşur. Uzaktan Haya Ayıklayıcı'yı başka bir hesap altında çalıştırırsanız, DNS gerektirmeyen NTLM kimlik doğrulaması kullanabilir. . Yordam için bkz. [hata: hedef bilgisayardaki Visual Studio uzaktan hata ayıklayıcı hizmeti bu bilgisayara geri bağlanamıyor](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
