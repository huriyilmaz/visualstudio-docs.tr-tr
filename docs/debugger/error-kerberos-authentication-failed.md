---
title: Kerberos kimlik doğrulaması başarısız oldu | Microsoft Docs
description: bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi yerel sistem veya ağ hizmeti hesabı altında çalışırken oluşur.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f21ff098132d934d94cace2f4c43dc9ad3a392bda6f7b273a1b58ef6822e05b3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121280293"
---
# <a name="error-kerberos-authentication-failed"></a>Hata: Kerberos Kimlik Doğrulaması Başarısız
Uzaktan hata ayıklama yapmayı denediğinizde aşağıdaki hata iletisini alabilirsiniz:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi yerel sistem veya ağ hizmeti hesabı altında çalışırken oluşur. bu hesaplardan birinde, uzaktan hata ayıklayıcı Visual Studio hata ayıklayıcı ana bilgisayarına geri iletişim kurmak için bir Kerberos kimlik doğrulaması bağlantısı kurmalıdır.

 Kerberos kimlik doğrulaması şu koşullarda kullanılamaz:

- Hedef bilgisayar veya hata ayıklayıcı Konak bilgisayar, etki alanı yerine bir çalışma grubunda bulunuyor

   \- veya

- Kerberos, etki alanı denetleyicisinde devre dışı bırakıldı.

  Kerberos kimlik doğrulaması kullanılamıyorsa, Visual Studio Uzaktan Hata Ayıklama İzleyicisi çalıştırmak için kullanılan hesabı değiştirin. yordam için bkz. [hata: hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti bu bilgisayara geri bağlanamıyor](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

  Her iki bilgisayar aynı etki alanına bağlıysa ve yine de bu iletiyi alırsanız hedef bilgisayardaki DNS 'nin hata ayıklayıcı ana bilgisayar adını doğru bir şekilde çözümlediğinden emin olun. Aşağıdaki yordama bakın.

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Hedef bilgisayardaki DNS 'in hata ayıklayıcı ana bilgisayar adını doğru bir şekilde çözdüğünü doğrulamak için

1. Hedef bilgisayarda **Başlat** menüsünü açın, **Donatılar** ' ın üzerine gelin ve ardından **komut istemi**' ne tıklayın.

2. **Komut istemi** penceresinde şunu yazın:

    ```cmd
    ping <debugger_host_computer_name>
    ```

3. Yanıtın ilk satırı, `ping` belirtilen bilgisayar IÇIN DNS tarafından döndürülen tam bilgisayar adını ve IP adresini gösterir.

4. Hata ayıklayıcı ana bilgisayarında, bir **komut istemi** penceresi açın ve komutunu çalıştırın `ipconfig` .

5. IP adresi değerlerini karşılaştırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
