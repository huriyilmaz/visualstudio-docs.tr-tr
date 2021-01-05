---
title: Uzaktan hata ayıklama için güvenlik duvarını yapılandırma Iletişim kutusu | Microsoft Docs
description: Uzaktan hata ayıklama için güvenlik duvarını Yapılandır iletişim kutusu hakkında bilgi edinmek için Windows Güvenlik Duvarı hata ayıklayıcının ağ üzerinden veri almasını durdurduğu zaman görüntülenir.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 86a0cac2e42e1271e689f2b1880eef8ca6d14644
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728969"
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

- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [Kullanıcı Arabirim Başvurusunda Hata Ayıklama](../debugger/debugging-user-interface-reference.md)