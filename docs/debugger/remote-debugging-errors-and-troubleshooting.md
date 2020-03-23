---
title: Uzaktan Hata Ayıklama Hataları ve Sorun Giderme | Microsoft Dokümanlar
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302093"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Uzaktan Hata Ayıklama Hataları ve Sorun Giderme

Uzaktan hata ayıklamaya çalışırken aşağıdaki hatalarla karşılaşabilirsiniz.

- [Hata: Sunucunun İçine Otomatik Olarak Adımlanamıyor](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Microsoft Visual Studio Uzaktan Hata Ayıklama Monitörüne Bağlanamıyor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Hata: Uzak Makine, Uzaktan Bağlantılar iletişim kutusunda görünmüyor](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Uzaktan hata ayıklamayı yönetici olarak çalıştırma

Uzaktan hata ayıklamayı yönetici olarak çalıştırmazsanız sorunlarla karşılaşabilirsiniz. Örneğin, aşağıdaki hatayı görebilirsiniz: "Visual Studio Uzaktan Hata Ayıklama (MSVSMON). EXE) bu işlemi hata ayıklamak için yeterli ayrıcalıklara sahiptir." Uzaktan hata ayıklamayı bir uygulama olarak çalıştırıyorsanız (hizmet olarak değil), [farklı kullanıcı hesabı](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) hatasını görebilirsiniz.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Uzaktan hata ayıklamayı hizmet olarak çalıştırırken

Uzaktan hata ayıklamayı s hizmeti olarak çalıştırırken, çeşitli nedenlerle yönetici olarak çalıştırmanızı öneririz:

- Uzaktan hata ayıklama hizmeti yalnızca yöneticilerin bağlantılarına izin verir, bu nedenle yönetici olarak çalıştırılarak yeni güvenlik riskleri **getirilmez.**

- Visual Studio kullanıcısı, bir işlemi hata ayıklama için uzaktan hata ayıklamanın kendisinden daha fazla hakka sahip olduğunda ortaya çıkan hataları önleyebilir.

- Uzaktan hata ayıklamanın kurulumve yapılandırmasını kolaylaştırmak için.

Uzaktan hata ayıklamayı yönetici olarak çalıştırmadan hata ayıklama yapmak mümkün olsa da, bunun doğru çalışması için çeşitli gereksinimler vardır ve genellikle daha gelişmiş hizmet yapılandırma adımları gerektirir.

- Uzak makinede kullandığınız hesabın **hizmet ayrıcalığı olarak oturum** açması gerekir. [Geri bağlanamaz](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) hata makalesinde "Oturum açma hizmeti olarak eklemek için" altındaki adımlara bakın.

- Hesabın hedef işlemi hata ayıklama hakları olmalıdır. Bu hakları almak için, uzak hata ayıklama işleminin debugged olması için aynı hesap altında çalıştırmalısınız. (Daha kolay alternatif, hizmeti yönetici olarak çalıştırmaktır.) 

- Hesap, ağ üzerinden Visual Studio bilgisayarına yeniden bağlanabilmeli (diğer bir şekilde kimlik doğrulaması) olmalıdır. Bir etki alanında, uzaktan hata ayıklayıcı yerleşik Yerel Sistem veya Ağ Hizmeti hesapları veya bir etki alanı hesabı altında çalışıyorsa, geri bağlanmak daha kolaydır. Yerleşik hesaplar, güvenlik riski oluşturabilecek yüksek güvenlik ayrıcalıklarına sahiptir.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Uzaktan hata ayıklamayı uygulama olarak çalıştırırken (normal mod)

Kendi yükseltmemiş işleminize (normal bir uygulama gibi) eklemeye çalışıyorsanız, uzaktan hata ayıklama işlemini yönetici olarak çalıştırıp çalıştırmadığınız önemli değildir.

Uzak hata ayıklamayı birkaç senaryoda yönetici olarak çalıştırmak istiyorsunuz:

- Başka bir kullanıcı olarak çalışan işlemlere (örneğin, IIS hata ayıklama gibi) eklemek istiyorsunuz veya

- Başka bir işlem başlatmaya çalışıyorsunuz ve başlatmak istediğiniz işlem bir yöneticidir.

İşlemleri başlatmak istiyorsanız yönetici olarak çalıştırmak **istemezsinizi** ve başlatmak istediğiniz işlemin yönetici **olmaması** gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)