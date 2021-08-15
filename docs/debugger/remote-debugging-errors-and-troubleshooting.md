---
title: Uzaktan Hata Ayıklama Hataları ve Sorun Giderme | Microsoft Docs
description: Hata ayıklama sırasında sık karşılaşılan uzaktan hata ayıklama hatalarının bağlantılarını Visual Studio. Uzak hata ayıklayıcıyı yönetici olarak çalıştırmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c53bcf0db2954c4edbf9ff5c8b04a62f8cbed0b883f0c0af57ddade5dfeb2916
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121310939"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Uzaktan Hata Ayıklama Hataları ve Sorun Giderme

Uzaktan hata ayıklamaya çalışırken aşağıdaki hatayla karşı karşıya gelebilirsiniz.

- [Hata: Sunucunun İçine Otomatik Olarak Adımlanamıyor](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Bağlan bağlantı Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Hata: Uzak Makine, Uzaktan Bağlantılar iletişim kutusunda görünmüyor](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Uzak hata ayıklayıcıyı yönetici olarak çalıştırma

Uzak hata ayıklayıcısını yönetici olarak çalıştırarak karşılaşabilirsiniz. Örneğin, şu hatayı alabilirsiniz: "Visual Studio Uzaktan Hata Ayıklayıcı (MSVSMON.EXE) bu işlemde hata ayıklamak için yeterli ayrıcalıklara sahip değil." Uzaktan hata ayıklayıcıyı bir uygulama olarak (hizmet olarak değil) çalıştırdısanız, farklı kullanıcı [hesabı hatasıyla karşılaşabilirsiniz.](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)

### <a name="when-running-the-remote-debugger-as-a-service"></a>Uzak hata ayıklayıcısını hizmet olarak çalıştırma

Uzaktan hata ayıklayıcısını hizmet olarak çalıştırarak çeşitli nedenlerle yönetici olarak çalıştırmanız önerilir:

- Uzaktan hata ayıklayıcı hizmeti yalnızca yöneticilerden gelen  bağlantılara izin verir, bu nedenle yönetici olarak çalıştırarak yeni bir güvenlik riski yoktur.

- Bu, kullanıcının bir işlemde hata ayıklama Visual Studio hata ayıklamak için uzak hata ayıklayıcının sahip olduğu haklardan daha fazla olduğunda ortaya çıkan hataları önlenebilir.

- Uzaktan hata ayıklayıcının kurulumunu ve yapılandırmasını basitleştirmek için.

Uzaktan hata ayıklayıcıyı yönetici olarak çalıştırmadan hata ayıklamak mümkün olabilir, ancak bunun doğru şekilde çalışması için çeşitli gereksinimler vardır ve bunlar genellikle daha gelişmiş hizmet yapılandırma adımları gerektirir.

- Uzak makinede kullanmakta olan hesabın hizmet olarak oturum **açma ayrıcalığına sahip olması** gerekir. Geri bağlanamıyor hatası makalesinde "Hizmet olarak oturum açma eklemek için" [altındaki adımlara](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) bakın.

- Hesabın hedef işlemde hata ayıklama haklarına sahip olması gerekir. Bu hakları almak için, uzaktan hata ayıklayıcıyı hata ayıklama işlemiyle aynı hesap altında çalıştırmanız gerekir. (Daha kolay bir alternatif, hizmeti yönetici olarak çalıştırmaktır.) 

- Hesabın, ağ üzerinden bir bilgisayara bağlanarak (kimlik doğrulaması Visual Studio) olması gerekir. Bir etki alanında, uzak hata ayıklayıcı yerleşik Yerel Sistem veya Ağ Hizmeti hesapları veya bir etki alanı hesabı altında çalışıyorsa, geri bağlanmak daha kolaydır. Yerleşik hesaplar, güvenlik riski sunacak yükseltilmiş güvenlik ayrıcalıklarına sahiptir.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Uzak hata ayıklayıcıyı uygulama olarak (normal mod) çalıştırma

Kendi yükseltilmiş olmayan işleminize (normal bir uygulama gibi) eklemeye çalışıyorsanız, uzak hata ayıklayıcıyı yönetici olarak çalıştırmanız önemli değildir.

Uzak hata ayıklayıcısını çeşitli senaryolarda yönetici olarak çalıştırmak istiyorsunuz:

- Başka bir kullanıcı olarak çalışan işlemlere (örneğin IIS'de hata ayıklarken) eklemek veya

- Başka bir işlem başlatmaya çalışıyorsunuz ve başlatmak istediğiniz işlem bir yöneticidir.

İşlemleri  başlatmak için yönetici olarak çalıştırmak istemiyorsunuz ve başlatmak istediğiniz işlem **yönetici** olmayacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)