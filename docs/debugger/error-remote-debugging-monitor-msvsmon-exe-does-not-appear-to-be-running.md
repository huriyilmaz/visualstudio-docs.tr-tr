---
description: Bu hata iletisi, Visual Studio bilgisayarda uygulamanın doğru örneğini Visual Studio Uzaktan Hata Ayıklama İzleyicisi olmadığını gösterir.
title: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.
titleSuffix: ''
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
ms.openlocfilehash: 41711cec9afec7bd4b13cdd768184ef0b106f52b
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970002"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.
Bu hata iletisi, Visual Studio bilgisayarda uygulamanın doğru örneğini Visual Studio Uzaktan Hata Ayıklama İzleyicisi olmadığını gösterir. Uzaktan Visual Studio Uzaktan Hata Ayıklama İzleyicisi hata ayıklamanın çalışması için uygulamanın yüklü olması gerekir. Uzaktan hata ayıklayıcısını indirme ve ayarlama hakkında bilgi için bkz. [Uzaktan Hata Ayıklama.](../debugger/remote-debugging.md)

> [!IMPORTANT]
> Bu iletiyi bir ürün hatası nedeniyle aldığınızı inanıyorsanız lütfen bu sorunu [Visual Studio.](../ide/how-to-report-a-problem-with-visual-studio.md) Daha fazla yardıma ihtiyacınız varsa [Microsoft'a Community](https://developercommunity.visualstudio.com/home) geliştirici hizmetleri makalesi'ne bakın.

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>2010 veya önceki bir sürümde hata Visual Studio bu iletiyi aldım
 Kullanmakta Visual Studio sürüm 2010 veya Visual Studio ise, dosya ve yazıcı paylaşımı etkinleştirilmediyse de bu hatayı alabilirsiniz. Bu sorun hakkında daha fazla bilgi için lütfen bu belgelerin Visual Studio 2010 sürümüne bakın: Hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayarda çalışmıyor [gibi görünüyor. - Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Yerel olarak hata ayıklarken bu iletiyi aldım
 Yerel olarak hata ayıklarken bu iletiyi alıyorsanız, virüsten koruma yazılımınız veya üçüncü taraf güvenlik duvarınız suçlayıcı olabilir. Visual Studio 32 bit bir uygulamadır, bu nedenle 64 bit uygulamalarda hata ayıklamak için uzak hata ayıklayıcının 64 bit sürümünü kullanır. İki işlem, yerel bilgisayar içindeki yerel ağı kullanarak iletişim kurar. Bilgisayardan hiçbir trafik ayrılsa da üçüncü taraf güvenlik yazılımı iletişimi engelleyebilir.

 Aşağıdaki bölümlerde bu iletiyi neden almış olabileceğiniz ve sorunu çözmek için neler yapabilirsiniz?

## <a name="the-remote-machine-is-not-reachable"></a>Uzak makineye ulaşılamaz
 Uzak [makineye ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) atmaya deneyin. Pinge yanıt verene kadar uzak araçlar da bağlanamıyor. Uzak makineyi yeniden başlatmayı deneyin ve aksi takdirde ağ üzerinde doğru yapılandırıldığından emin olun.

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcının sürümü, uzak hata ayıklayıcının Visual Studio
 Yerel olarak Visual Studio dosyanın sürümünün, uzak makinede çalışan uzaktan hata ayıklama izleyicisi sürümüyle eşleşmesi gerekir. Bunu düzeltmek için uzaktan hata ayıklama izleyicinin eşleşen sürümünü indirip yükleyin. Uzaktan hata [ayıklayıcının](https://www.microsoft.com/download) doğru sürümünü bulmak için İndirme Merkezi'ne gidin.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makinelerin farklı kimlik doğrulama modları vardır
 Yerel ve uzak makinelerin aynı kimlik doğrulama modunu kullanması gerekir. Bunu düzeltmek için her iki makinede de aynı kimlik doğrulama modunun kullana olduğundan emin olun. Kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows Kimlik Doğrulamasına Genel Bakış.](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11))

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor
 Bunu çözmek için aşağıdaki yöntemlerden birini kullanabilirsiniz:

- Uzak hata ayıklayıcıyı durdurabilir ve yerel bilgisayarda kullanmakta olan hesap ile yeniden başlatabilirsiniz.

- Uzak hata ayıklayıcıyı komut satırına **/allow \<username> parametresiyle başlatabilirsiniz:**`msvsmon /allow <username@computer>`

- Kullanıcıyı uzaktan hata ayıklayıcısının izinlerine eklemek için kullanabilirsiniz (uzaktan hata ayıklayıcısı penceresinde Araçlar **> İzinleri).**

- Önceki adımlarda yöntemleri kullanasanız, herhangi bir kullanıcının uzaktan hata ayıklaması yapmalarına izin veebilirsiniz. Uzaktan hata ayıklayıcısı penceresinde Araçlar ve Seçenekler **iletişim > gidin.** Kimlik Doğrulaması **Yok'u seçerek** Herhangi bir kullanıcının hata **ayıklamasına izin ver'i kontrol edin.** Ancak, bu seçeneği yalnızca seçeneğiniz yoksa veya özel bir ağ üzerindeyseniz kullanabilirsiniz.

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Uzak makinede güvenlik duvarı, uzaktan hata ayıklayıcıya gelen bağlantılara izin vermiyor
 Sanal makinede Visual Studio ve uzak makinede yer alan güvenlik duvarı, Visual Studio hata ayıklayıcısı arasında iletişime izin verecek şekilde yapılandırmalısınız. Uzaktan hata ayıklayıcının kullanmakta olduğu bağlantı noktaları hakkında bilgi için bkz. [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları.](../debugger/remote-debugger-port-assignments.md) Güvenlik duvarını yapılandırma hakkında Windows için [bkz. Uzaktan Hata Ayıklama Windows Güvenlik Duvarı'nı yapılandırma.](../debugger/configure-the-windows-firewall-for-remote-debugging.md)

## <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımı bağlantıları engelliyor
 Windows virüsten koruma yazılımı uzaktan hata ayıklayıcı bağlantılarına izin verir, ancak bazı üçüncü taraf virüsten koruma yazılımları bunları engelleyebilir. Bu bağlantılara izin verme hakkında bilgi için virüsten koruma yazılımınıza ilişkin belgelere bakın.

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi, uzak makine ile sanal makine arasındaki iletişimi Visual Studio
 İletişimi engellemey olduğundan emin olmak için ağ güvenliğinizi gözden geçirme. Ağ güvenlik ilkesi yapılandırma hakkında Windows için bkz. [Güvenlik ilkesi ayarları.](/windows/device-security/security-policy-settings/security-policy-settings)

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ uzaktan hata ayıklamayı destekleyecek kadar meşgul
 Farklı bir zamanda uzaktan hata ayıklamanız veya ağ üzerinde farklı bir süre için çalışma zamanlamanız gerekir.

## <a name="more-help"></a>Daha fazla yardım
 Komut satırı anahtarları da dahil olmak üzere daha fazla uzaktan hata ayıklayıcısı yardımı almak için, **uzak hata ayıklayıcı penceresinde >** Yardım Hata Ayıklayıcısı Kullanımı'na tıklayın. Açık yoksa, aşağıdaki satırı bir web sitesi penceresine kopyalayıp web  **Dosya Gezgini** görebilirsiniz. (yerine \<Visual Studio installation directory> yüklemenizin konumunu Visual Studio.)

 res:// *\<Visual Studio installation directory>* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
