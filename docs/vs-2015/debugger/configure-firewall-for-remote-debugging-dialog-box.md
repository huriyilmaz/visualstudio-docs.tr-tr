---
title: Uzaktan hata ayıklama için güvenlik duvarını yapılandırma Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e2b1300feb8d2a15e63089ee9bddde5f2d1ef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702293"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Uzaktan Hata Ayıklama İçin Güvenlik Duvarını Yapılandır İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Güvenlik Duvarı hata ayıklayıcının ağ üzerinden bilgi almasını engelliyorsa, bu iletişim kutusu görüntülenir. Uzaktan hata ayıklamaya devam etmek için, hata ayıklayıcının bilgi alabilmesi için güvenlik duvarında bir delik açmanız gerekir.  
  
> [!CAUTION]
> Güvenlik duvarında bir delik açmak, makinenizi güvenlik duvarının engellemek için tasarlandığı güvenlik tehditlerine maruz bırakabilir. Uzaktan hata ayıklama için bir delik açmak Visual Studio 2015 4020 ve 4021 bağlantı noktalarını kaldırır. Visual Studio 'nun diğer sürümlerinde diğer bağlantı noktası numaraları kullanılır. Daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Ayrıca, hata ayıklayıcının ek bağlantı noktalarını açmasına izin verir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama Için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **Uzaktan hata ayıklamayı iptal et**  
 Uzaktan hata ayıklama girişimini iptal eder. Makinenizin güvenlik ayarları bozulmadan kalır.  
  
 **Yerel ağdaki bilgisayarların uzaktan hata ayıklamasını engellemeyi kaldır (alt ağ)**  
 Yerel alt ağınızdaki makinelerin uzaktan hata ayıklamasını sağlar. Bu, yerel alt ağınızdaki makinelere yönelik güvenlik açıklarını açabilir, ancak güvenlik duvarı alt ağ dışından gelen bilgileri engellemeye devam eder.  
  
 **Uzaktan hata ayıklamayı herhangi bir bilgisayardan engellemeyi kaldır**  
 Ağ üzerinde herhangi bir yerde makinelerde uzaktan hata ayıklamayı sağlar. Bu ayar en az güvenli seçenektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Cihazda uzak araçları ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Kullanıcı Arabirim Başvurusunda Hata Ayıklama](../debugger/debugging-user-interface-reference.md)
