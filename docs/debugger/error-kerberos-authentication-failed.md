---
title: Hata-Kerberos kimlik doğrulaması başarısız oldu | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07afa4aca82a83f5b7ba64ad0e9958710582a6a0
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460683"
---
# <a name="error-kerberos-authentication-failed"></a>Hata: Kerberos Kimlik Doğrulaması Başarısız
Uzaktan hata ayıklama yapmayı denediğinizde aşağıdaki hata iletisini alabilirsiniz:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 Bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi yerel sistem veya ağ hizmeti hesabı altında çalışırken oluşur. Bu hesaplardan birinin altında, uzaktan hata ayıklayıcı Visual Studio hata ayıklayıcısı ana bilgisayarına geri iletişim kurmak için bir Kerberos kimlik doğrulaması bağlantısı kurmalıdır.

 Kerberos kimlik doğrulaması şu koşullarda kullanılamaz:

- Hedef bilgisayar veya hata ayıklayıcı Konak bilgisayar, etki alanı yerine bir çalışma grubunda bulunuyor

   \-veya

- Kerberos, etki alanı denetleyicisinde devre dışı bırakıldı.

  Kerberos kimlik doğrulaması kullanılamıyorsa, Visual Studio Uzaktan Hata Ayıklama İzleyicisi çalıştırmak için kullanılan hesabı değiştirin. Yordam için bkz. [hata: hedef bilgisayardaki Visual Studio uzaktan hata ayıklayıcı hizmeti bu bilgisayara geri bağlanamıyor](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

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
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
