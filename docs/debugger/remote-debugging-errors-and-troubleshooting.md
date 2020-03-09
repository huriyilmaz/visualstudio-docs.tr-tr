---
title: Uzaktan hata ayıklama hataları ve sorun giderme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409304"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Uzaktan Hata Ayıklama Hataları ve Sorun Giderme

Uzaktan hata ayıklamaya çalışırken aşağıdaki hatalarda karşılaşabilirsiniz.

- [Hata: Sunucunun İçine Otomatik Olarak Adımlanamıyor](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Hata: Uzak Makine, Uzaktan Bağlantılar iletişim kutusunda görünmüyor](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Uzaktan hata ayıklayıcıyı yönetici olarak çalıştır

Uzaktan hata ayıklayıcıyı yönetici olarak çalıştırmazsanız sorunlarla karşılaşabilirsiniz. Örneğin, şu hatayı görebilirsiniz: "Visual Studio Uzaktan Hata Ayıklayıcı (MSVSMON. EXE) Bu işlemde hata ayıklamak için yeterli ayrıcalıklara sahip değil. " Uzaktan hata ayıklayıcıyı bir uygulama olarak (hizmet değil) çalıştırıyorsanız, [farklı kullanıcı hesabı](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) hatası görebilirsiniz.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırırken

Uzaktan hata ayıklayıcıyı s hizmeti olarak çalıştırırken, birkaç nedenden dolayı onu yönetici olarak çalıştırmayı öneririz:

- Uzaktan hata ayıklayıcı hizmeti yalnızca yöneticilerin bağlantılarına izin veriyor, bu nedenle, yönetici olarak çalıştırılarak sunulan yeni bir güvenlik riski **yoktur** .

- Visual Studio kullanıcısının, uzak hata ayıklayıcı 'nın yaptığı bir işlemde hata ayıklamak için daha fazla haklara sahip olması nedeniyle oluşan hataları önleyebilir.

- Uzaktan hata ayıklayıcının kurulumunu ve yapılandırmasını basitleştirmek için.

Uzaktan hata ayıklayıcı 'yı yönetici olarak çalıştırmadan hata ayıklamak mümkün olsa da, bu çalışmayı doğru şekilde yapmak için birkaç gereksinim vardır ve genellikle daha gelişmiş hizmet yapılandırma adımları gerektirir.

- Uzak makinede kullandığınız hesabın **hizmet olarak oturum açma** ayrıcalığına sahip olması gerekir. [Geri bağlama](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) hatası makalesinde "hizmet olarak oturum açma eklemek için" altındaki adımlara bakın.

- Hesap, hedef işlemde hata ayıklamak için haklara sahip olmalıdır. Bu hakları almak için, uzaktan hata ayıklayıcıyı hata ayıklamakta olan işlemle aynı hesap altında çalıştırmalısınız. (Daha kolay alternatif, hizmeti yönetici olarak çalıştırmaktır.) 

- Hesabın, ağ üzerinden Visual Studio bilgisayar ile (kimlik doğrulaması yapılan) geri bağlanabilmesi gerekir. Bir etki alanında, uzaktan hata ayıklayıcı yerleşik yerel sistem veya ağ hizmeti hesapları ya da bir etki alanı hesabı altında çalışıyorsa, tekrar bağlanmak daha kolay olur. Yerleşik hesaplar güvenlik riski sunan yükseltilmiş güvenlik ayrıcalıklarına sahiptir.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Uzaktan hata ayıklayıcıyı bir uygulama olarak çalıştırırken (normal mod)

Kendi yükseltilmemiş işleminizi (örneğin, normal bir uygulama) eklemeye çalışıyorsanız, uzaktan hata ayıklayıcıyı yönetici olarak çalıştırıyor olmanız da önemlidir.

Uzaktan hata ayıklayıcıyı birkaç senaryoda yönetici olarak çalıştırmak istiyorsunuz:

- Başka bir kullanıcı olarak çalışan işlemlere (örneğin, IIS hata ayıklaması sırasında) eklemek istiyorsanız veya

- Başka bir işlem başlatmaya çalışıyorsunuz ve başlatmak istediğiniz işlem bir yönetici.

İşlemleri başlatmak istiyorsanız, yönetici olarak **çalıştırmak istemezsiniz ve** başlatmak istediğiniz işlem **yönetici olmamalıdır.**

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)