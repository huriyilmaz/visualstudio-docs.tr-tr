---
description: bu hata iletisi Visual Studio, uzak bilgisayarda Visual Studio Uzaktan Hata Ayıklama İzleyicisi doğru örneğini bulamadığı anlamına gelir.
title: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.server_machine_no_default
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
ms.openlocfilehash: 46cc9d7414d3e45492d4d5c43420b3b621bcc755a8b65b18614214f107647a72
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391456"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.
bu hata iletisi Visual Studio, uzak bilgisayarda Visual Studio Uzaktan Hata Ayıklama İzleyicisi doğru örneğini bulamadığı anlamına gelir. uzaktan hata ayıklamanın çalışması için Visual Studio Uzaktan Hata Ayıklama İzleyicisi yüklü olmalıdır. Uzaktan hata ayıklayıcıyı indirme ve ayarlama hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

> [!IMPORTANT]
> Bir ürün hatası nedeniyle bu iletiyi aldığınızı düşünüyorsanız, lütfen [Bu sorunu Visual Studio bildirin](../ide/how-to-report-a-problem-with-visual-studio.md). Daha fazla yardıma ihtiyacınız varsa bkz. Microsoft 'a başvurmanın yolları için [bize](../ide/feedback-options.md) danışın.

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Visual Studio 2010 veya önceki sürümlerde hata ayıklarken bu iletiyi aldım
 kullanmakta olduğunuz Visual Studio sürümü Visual Studio 2010 veya daha önceki bir sürümdeyse, dosya ve yazıcı paylaşımı etkinleştirilmemişse da bu hatayı alabilirsiniz. bu sorun hakkında daha fazla bilgi edinmek için lütfen bu belgenin Visual Studio 2010 sürümüne bakın: [hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayarda çalışıyor görünmüyor.-Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Yerel olarak hata ayıklarken bu iletiyi aldım
 Yerel olarak hata ayıklarken bu iletiyi alıyorsanız, virüsten koruma yazılımınız veya üçüncü taraf güvenlik duvarınız önlenebilir. Visual Studio, 32 bitlik bir uygulamadır, bu nedenle 64 bit uygulamalarda hata ayıklamak için uzaktan hata ayıklayıcının 64 bit sürümünü kullanır. İki işlem yerel bilgisayar içindeki yerel ağı kullanarak iletişim kurar. Bilgisayardan hiçbir trafik kalmayacak, ancak üçüncü taraf güvenlik yazılımlarının iletişimi engelleyebilmesini mümkün olabilir.

 Aşağıdaki bölümlerde bu iletiyi edinmenizin bazı nedenleri ve sorunu çözebilmeniz için yapabilecekleriniz listelenmektedir.

## <a name="the-remote-machine-is-not-reachable"></a>Uzak makineye ulaşılamıyor
 Uzak makineye [ping işlemi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) yapmayı deneyin. Ping komutuna yanıt vermezse uzak Araçlar bağlanamaz. Uzak makineyi yeniden başlatmayı deneyin, aksi takdirde ağda doğru yapılandırıldığından emin olun.

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcının sürümü Visual Studio sürümüyle eşleşmiyor
 yerel olarak çalıştırdığınız Visual Studio sürümünün uzak makinede çalışan uzaktan hata ayıklama izleyicisinin sürümüyle eşleşmesi gerekir. Bu hatayı gidermek için, uzaktan hata ayıklama izleyicisinin eşleşen sürümünü indirip yükleyin. Uzaktan hata ayıklayıcının doğru sürümünü bulmak için [Indirme merkezi](https://www.microsoft.com/download) 'ne gidin.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makineler farklı kimlik doğrulama modlarına sahiptir
 Yerel ve uzak makinelerin aynı kimlik doğrulama modunu kullanması gerekir. Bu hatayı onarmak için her iki makinenin da aynı kimlik doğrulama modunu kullanmasını sağlayın. kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasına genel bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor
 Bunu, aşağıdaki yollarla çözebilirsiniz:

- Uzaktan hata ayıklayıcıyı durdurabilir ve yerel bilgisayarda kullandığınız hesapla yeniden başlatabilirsiniz.

- Uzaktan hata ayıklayıcıyı komut satırından **/Allow \<username>** parametresiyle başlatabilirsiniz:`msvsmon /allow <username@computer>`

- Kullanıcıyı uzaktan hata ayıklayıcı 'nın izinlerine (uzaktan hata ayıklayıcı penceresinde, **araçlar > izinler**) ekleyebilirsiniz.

- Yukarıdaki adımlarda yöntemleri kullanamıyoruz, herhangi bir kullanıcının uzaktan hata ayıklama yapmasına izin verebilirsiniz. Uzaktan hata ayıklayıcı penceresinde, **araçlar > seçenekleri** iletişim kutusuna gidin. **Kimlik doğrulaması yok**' u seçtiğinizde, **herhangi bir kullanıcının hata ayıklamasına izin ver**' i kontrol edebilirsiniz. Ancak, bu seçeneği yalnızca herhangi bir seçiminiz yoksa veya özel bir ağınız üzerinde olduğunuzda kullanmanız gerekir.

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Uzak makinedeki güvenlik duvarı uzaktan hata ayıklayıcıya gelen bağlantılara izin vermiyor
 Visual Studio makinesindeki güvenlik duvarının ve uzak makinedeki güvenlik duvarının Visual Studio ile uzaktan hata ayıklayıcı arasında iletişime izin verecek şekilde yapılandırılması gerekir. Uzaktan hata ayıklayıcı tarafından kullanılan bağlantı noktaları hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Windows güvenlik duvarını yapılandırma hakkında daha fazla bilgi için bkz. [uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımı bağlantıları engelliyor
 virüsten koruma yazılımı Windows, uzaktan hata ayıklayıcı bağlantılarına izin verir, ancak bazı üçüncü taraf virüsten koruma yazılımları bunları engelleyebilir. Bu bağlantılara nasıl izin verbileceğinizi öğrenmek için virüsten koruma yazılımınızın belgelerini denetleyin.

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi, uzak makine ile Visual Studio arasındaki iletişimi engelliyor
 İletişimi engellemediğinden emin olmak için ağ güveninizi gözden geçirin. Windows ağ güvenlik ilkesi hakkında daha fazla bilgi için bkz. [güvenlik ilkesi ayarları](/windows/device-security/security-policy-settings/security-policy-settings).

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ, uzaktan hata ayıklamayı desteklemeye yönelik çok meşgul
 Uzaktan hata ayıklamayı farklı bir zamanda yapmanız veya ağdaki çalışmayı farklı bir süre için yeniden zamanlamanız gerekebilir.

## <a name="more-help"></a>Daha fazla yardım
 Komut satırı anahtarları dahil olmak üzere daha fazla uzaktan hata ayıklayıcı yardımı almak için, uzaktan hata ayıklayıcı penceresinde **yardım > kullanımı** ' na tıklayın. Açık değilse, aşağıdaki satırı bir  **Dosya Gezgini** penceresine kopyalayarak Web sayfasına bakabilirsiniz. ( \<Visual Studio installation directory> Visual Studio yüklemenizin konumuyla değiştirmeniz gerekir.)

 res:// *\<Visual Studio installation directory>* \Common7\IDE\Remote% 20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
