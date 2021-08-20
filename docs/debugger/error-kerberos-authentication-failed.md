---
title: Kerberos Kimlik Doğrulaması Başarısız | Microsoft Docs
description: Bu hata, yerel Visual Studio Uzaktan Hata Ayıklama İzleyicisi veya Ağ Hizmeti hesabı altında çalıştırıldıklarından oluşur.
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
ms.openlocfilehash: e884e92ad5ad6669746cee28adc3dccf60d2c468
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161395"
---
# <a name="error-kerberos-authentication-failed"></a>Hata: Kerberos Kimlik Doğrulaması Başarısız
Uzaktan hata ayıklamayı deneerek aşağıdaki hata iletisini alabilirsiniz:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 Bu hata, yerel Visual Studio Uzaktan Hata Ayıklama İzleyicisi veya Ağ Hizmeti hesabı altında çalıştırıldıklarından oluşur. Bu hesaplardan biri altında, uzak hata ayıklayıcısı, hata ayıklayıcısı ana bilgisayarına geri iletişim kurmak için bir Kerberos Visual Studio bağlantısı kurması gerekir.

 Kerberos kimlik doğrulaması şu koşullarda kullanılamaz:

- Hedef bilgisayar veya hata ayıklayıcı konak bilgisayarı etki alanı yerine bir çalışma grubunda

   \- veya -

- Etki alanı denetleyicisinde Kerberos devre dışı bırakıldı.

  Kerberos kimlik doğrulaması kullanılamıyorsa, hesabı çalıştırmak için kullanılan hesabı Visual Studio Uzaktan Hata Ayıklama İzleyicisi. Yordam için [bkz. Hata: Hedef Visual Studio Uzaktan Hata Ayıklayıcı hizmet bu bilgisayara geri bağlanamıyor.](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)

  Her iki bilgisayar da aynı etki alanına bağlıysa ve bu iletiyi almaya devam ediyorsanız, hedef bilgisayardaki DNS'nin hata ayıklayıcı konak bilgisayarının adını doğru çözümlemediğini doğrulayın. Aşağıdaki yordama bakın.

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Hedef bilgisayardaki DNS'nin hata ayıklayıcı ana bilgisayar adını doğru çözümlemediğini doğrulamak için

1. Hedef bilgisayarda Başlat menüsünü açın, **Donatılar'ın** üzerine **gelin ve** Komut İstemi'ne **tıklayın.**

2. Komut **İstemi penceresine** şunları yazın:

    ```cmd
    ping <debugger_host_computer_name>
    ```

3. Yanıtın ilk `ping` satırı, belirtilen bilgisayar için DNS tarafından döndürülen tam bilgisayar adını ve IP adresini gösterir.

4. Hata ayıklayıcı konak bilgisayarda bir Komut **İstemi penceresi açın** ve komutunu `ipconfig` çalıştırın.

5. IP adresi değerlerini karşılaştırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
