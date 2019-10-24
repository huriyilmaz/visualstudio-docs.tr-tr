---
title: Uzaktan hata ayıklama için güvenlik duvarını yapılandırma Iletişim kutusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a2511fc2adfa63ff28f8459f48cbdf4b4623ff5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745657"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Uzaktan Hata Ayıklama İçin Güvenlik Duvarını Yapılandır İletişim Kutusu
Windows Güvenlik Duvarı hata ayıklayıcının ağ üzerinden bilgi almasını engelliyorsa, bu iletişim kutusu görüntülenir. Uzaktan hata ayıklamaya devam etmek için, hata ayıklayıcının bilgi alabilmesi için güvenlik duvarında bir delik açmanız gerekir.

> [!CAUTION]
> Güvenlik duvarında bir delik açmak, makinenizi güvenlik duvarının engellemek için tasarlandığı güvenlik tehditlerine maruz bırakabilir. Uzaktan hata ayıklama için bir delik açmak Visual Studio 2015 4020 ve 4021 bağlantı noktalarını kaldırır. Visual Studio 'nun diğer sürümlerinde diğer bağlantı noktası numaraları kullanılır. Daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Ayrıca, hata ayıklayıcının ek bağlantı noktalarını açmasına izin verir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama Için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="uielement-list"></a>UIElement Listesi
 **Uzaktan hata ayıklamayı Iptal et** Uzaktan hata ayıklama girişimini iptal eder. Makinenizin güvenlik ayarları bozulmadan kalır.

 **Yerel ağdaki bilgisayarların uzaktan hata ayıklamasını engellemeyi kaldır (alt ağ)** Yerel alt ağınızdaki makinelerin uzaktan hata ayıklamasını sağlar. Bu, yerel alt ağınızdaki makinelere yönelik güvenlik açıklarını açabilir, ancak güvenlik duvarı alt ağ dışından gelen bilgileri engellemeye devam eder.

 **Uzaktan hata ayıklamayı herhangi bir bilgisayardan engellemeyi kaldır** Ağ üzerinde herhangi bir yerde makinelerde uzaktan hata ayıklamayı sağlar. Bu ayar en az güvenli seçenektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
- [Kullanıcı arabirim başvurusunda hata ayıklama](../debugger/debugging-user-interface-reference.md)