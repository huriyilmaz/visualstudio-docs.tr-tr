---
title: Uzaktan Windows ayıklama için Güvenlik Duvarı'nı | Microsoft Docs
description: Uzaktan Windows için Güvenlik Duvarı'nı yapılandırma. Uzaktan hata ayıklama için bağlantı noktalarını yapılandırma. Uzaktan hata ayıklama bağlantısı sorunlarını giderin.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ae4a3ea65c9db713bcbdb9a9d9b1027767614b21
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031412"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Uzaktan Windows için Güvenlik Duvarı'nı yapılandırma

Güvenlik Duvarı tarafından korunan bir Windows güvenlik duvarının uzaktan hata ayıklamaya izin ver için yapılandırılması gerekir. Visual Studio ve uzaktan hata ayıklama araçları yükleme veya başlatma sırasında doğru güvenlik duvarı bağlantı noktalarını açmayı dener, ancak bağlantı noktalarını açmanız veya uygulamalara el ile izin vermeniz de gerekebilir.

Bu konuda, Windows, 8.1 ve 7 Windows 10 de uzaktan hata ayıklamayı etkinleştirmek için Windows 10 güvenlik duvarını yapılandırma açıklanmıştır; ve Windows Server 2012 R2, 2012 ve 2008 R2 bilgisayarlarını kullanır. Visual Studio ve uzak bilgisayarın aynı işletim sistemini çalıştırması gerekir. Örneğin, Visual Studio bir bilgisayar Windows 10 ve uzak bilgisayar R2'de Windows Server 2012 çalıştırabilirsiniz.

>[!NOTE]
>Güvenlik duvarı yapılandırma yönergeleri Windows işletim sistemlerinde ve eski işletim sistemlerinde biraz farklılık Windows. Windows 8/8.1, Windows 10 ve Windows Server 2012 ayarları sözcük *uygulamasını,* Windows 7 ve Windows Server 2008 ise sözcük *programını kullanır.*

## <a name="configure-ports-for-remote-debugging"></a>Uzaktan hata ayıklama için bağlantı noktalarını yapılandırma

Visual Studio ve uzak hata ayıklayıcısı yükleme veya başlatma sırasında doğru bağlantı noktalarını açmayı dener. Ancak üçüncü taraf güvenlik duvarı gibi bazı senaryolarda bağlantı noktalarını el ile açmanız gerekebilir.

**Bir bağlantı noktasını açmak için:**

1. Başlat Windows **gelişmiş** güvenlik duvarı için arama **Windows ve açın.** Bu Windows 10, Gelişmiş Güvenlik **Windows Defender Güvenlik Duvarı'dır.**

1. Yeni bir gelen bağlantı noktası için Gelen **Kuralları'ı ve ardından** Yeni **Kural'ı seçin.** Giden kural için bunun yerine **Giden Kuralları'ı** seçin.

1. Yeni Gelen **Kuralı Sihirbazı'nda Bağlantı Noktası'nı** **ve** ardından Sonraki'yi **seçin.**

1. Aşağıdaki **tablolarda yer** alan bağlantı noktası numarasına bağlı olarak TCP veya **UDP'yi** seçin.

1. Belirli **yerel bağlantı noktaları** altında, aşağıdaki tablolardan bir bağlantı noktası numarası girin ve Sonraki'yi **seçin.**

1. Bağlantıya **İzin Ver'i** ve ardından Sonraki'yi **seçin.**

1. Uzak bağlantının ağ türü de dahil olmak üzere etkinleştirilen bir veya daha fazla ağ türünü seçin ve ardından Sonraki'yi **seçin.**

1. Kural için bir ad ekleyin (örneğin, **msvsmon**, **IIS** veya **Web Dağıtımı)** ve ardından Son'a **tıklayın.**

   Yeni kural, Gelen Kuralları veya Giden Kuralları **listesinde görüntü olmalı** ve **seçilmelidir.**

**PowerShell kullanarak bağlantı noktasını açmak için:**

Güvenlik Windows için [New-NetFirewallRule](/powershell/module/netsecurity/new-netfirewallrule?view=win10-ps)gibi PowerShell komutlarını kullanabilirsiniz.

Aşağıdaki örnek, uzak bilgisayardaki uzak hata ayıklayıcı için 4024 bağlantı noktasını açar. Kullanmak için gereken yol farklı olabilir.

```ps
New-NetFirewallRule -DisplayName "msvsmon" -Direction Inbound -Program "Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe" -LocalPort 4024 -Protocol TCP -Authentication Required -Action Allow
```

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Uzak bilgisayarda uzaktan hata ayıklamayı etkinleştiren bağlantı noktaları

Uzaktan hata ayıklama için, uzak bilgisayarda aşağıdaki bağlantı noktalarının açık olması gerekir:

::: moniker range="vs-2017"

|**Bağlantı noktaları**|**Gelen/Giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|4022|Gelen|TCP|VS 2017 için. Bağlantı noktası numarası, her bir sürüm için 2 Visual Studio artırır. Daha fazla bilgi için [bkz. Visual Studio hata ayıklayıcısı bağlantı noktası atamalarını yükleme.](../debugger/remote-debugger-port-assignments.md)|
|4023|Gelen|TCP|VS 2017 için. Bağlantı noktası numarası, her bir sürüm için 2 Visual Studio artırır. Bu bağlantı noktası yalnızca uzaktan hata ayıklayıcının 64 bit sürümünden 32 bitlik bir işlemde uzaktan hata ayıklamak için kullanılır. Daha fazla bilgi için [bkz. Visual Studio hata ayıklayıcısı bağlantı noktası atamalarını yükleme.](../debugger/remote-debugger-port-assignments.md)|
|3702|Giden|UDP|(İsteğe bağlı) Uzaktan hata ayıklayıcı bulma için gereklidir.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Bağlantı noktaları**|**Gelen/Giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|4024|Gelen|TCP|VS 2019 için. Bağlantı noktası numarası, her bir sürüm için 2 Visual Studio artırır. Daha fazla bilgi için [bkz. Visual Studio hata ayıklayıcısı bağlantı noktası atamalarını yükleme.](../debugger/remote-debugger-port-assignments.md)|
|4025|Gelen|TCP|VS 2019 için. Bağlantı noktası numarası, her bir sürüm için 2 Visual Studio artırır. Bu bağlantı noktası yalnızca uzaktan hata ayıklayıcının 64 bit sürümünden 32 bitlik bir işlemde uzaktan hata ayıklamak için kullanılır. Daha fazla bilgi için [bkz. Visual Studio hata ayıklayıcısı bağlantı noktası atamalarını yükleme.](../debugger/remote-debugger-port-assignments.md)|
|3702|Giden|UDP|(İsteğe bağlı) Uzaktan hata ayıklayıcı bulma için gereklidir.|

::: moniker-end

Araçlar Seçenekler Hata **Ayıklama altında Yönetilen Uyumluluk Modunu** **Kullan'ı**  >    >  **seçerse,** bu ek uzaktan hata ayıklayıcı bağlantı noktalarını açın. Hata Ayıklayıcısı Yönetilen Uyumluluk Modu, hata ayıklayıcının eski Visual Studio 2010 sürümünü sağlar.

|**Bağlantı noktaları**|**Gelen/Giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|135, 139, 445|Giden|TCP|Gereklidir.|
|137, 138|Giden|UDP|Gereklidir.|

Etki alanı ilkeniz IPSec üzerinden ağ iletişiminin gerçekleştiriliyorsa, hem etki alanı hem de uzak bilgisayarlarda Visual Studio bağlantı noktalarını açabilirsiniz. Uzak bir IIS web sunucusunda hata ayıklamak için uzak bilgisayarda 80 bağlantı noktasını açın.

|**Bağlantı noktaları**|**Gelen/Giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|500, 4500|Giden|UDP|Etki alanı ilkeniz IPSec üzerinden ağ iletişimini gerektiriyorsa gereklidir.|
|80|Giden|TCP|Web sunucusu hata ayıklaması için gereklidir.|

Belirli uygulamalara güvenlik duvarı üzerinden izin Windows için bkz. Güvenlik [Duvarı üzerinden uzaktan Windows yapılandırma.](#configure-remote-debugging-through-windows-firewall)

## <a name="configure-remote-debugging-through-windows-firewall"></a>Güvenlik duvarı aracılığıyla uzaktan Windows yapılandırma

Uzak hata ayıklama araçlarını uzak bilgisayara yükleyebilir veya paylaşılan bir klasörden çalıştırabilirsiniz. Her iki durumda da uzak bilgisayar güvenlik duvarının doğru yapılandırılması gerekir.

Uzak bir bilgisayarda, uzaktan hata ayıklama araçları şu işlemlerdedir:

*\<Visual Studio installation directory\>\\Common7 \\ IDE \\ Uzaktan Hata Ayıklayıcısı\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Güvenlik Duvarı üzerinden uzaktan hata ayıklayıcıya izin Windows yapılandırma

1. Başlat Windows **Güvenlik** Duvarı'nı veya Güvenlik **Duvarı'nı Windows** **için arama Windows Defender açın.**

1. Güvenlik **Duvarı üzerinden bir uygulamaya izin Windows seçin.**

1. Uzaktan **Hata Ayıklayıcısı veya** **Visual Studio Uzaktan Hata Ayıklayıcı** izin verilen uygulamalar ve özellikler altında görünmüyorsa, Ayarları değiştir'i ve ardından Başka bir uygulamaya izin **ver'i seçin.**

1. Uzaktan hata ayıklayıcı uygulaması hala Uygulama  ekle iletişim kutusunda listelenmiyorsa, uygulamanıza uygun mimariye bağlı olarak Gözat 'ı seçin ve * Ortak7 IDE Uzaktan Hata Ayıklayıcısı'ne \<Visual Studio installation directory\> \\ \\ \\ \\ \<x86*, *x64*, or *Appx*\> gidin. Öğesini *msvsmon.exe* ve ardından Ekle'yi **seçin.**

1. Uygulamalar **listesinde,** yeni **ekley istediğiniz Uzaktan Hata** Ayıklayıcı'ya tıklayın. Ağ **türleri'ne** ve ardından uzak bağlantının ağ türü de dahil olmak üzere bir veya daha fazla ağ türü seçin.

1. **Ekle'yi** ve ardından Tamam'ı **seçin.**

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Uzaktan hata ayıklama bağlantısı sorunlarını giderme

Uygulamanıza uzaktan hata ayıklayıcı ile bağlana biliyorsanız uzaktan hata ayıklama güvenlik duvarı bağlantı noktalarının, protokollerin, ağ türlerinin ve uygulama ayarlarının doğru olduğundan emin olun.

- Başlat menüsünde Windows **Güvenlik** Duvarı'nı arayın **ve Windows Güvenlik** Duvarı aracılığıyla uygulamaya izin **ver'Windows seçin.** Uzaktan Hata **Ayıklayıcısı'nın** **Visual Studio Uzaktan Hata Ayıklayıcı** izin  verilen uygulamalar ve özellikler listesinde seçili bir onay kutusuyla göründüğünden ve doğru ağ türlerinin seçildiğinden emin olun. Yoksa, [doğru uygulamaları ve ayarları ekleyin.](#configure-remote-debugging-through-windows-firewall)

- Başlat menüsünde Windows **Güvenlik** Duvarı'nı **arayın ve Windows Güvenlik Duvarı'nı açın.** Uzaktan Hata **Ayıklayıcısı'nın** **Visual Studio Uzaktan Hata Ayıklayıcı** kurallar **(ve** isteğe bağlı olarak **Giden** Kuralları) altında yeşil onay işareti simgesiyle göründüğünden ve tüm ayarların doğru olduğundan emin olun.

  - Kural ayarlarını görüntülemek veya değiştirmek için, listeden Uzaktan Hata Ayıklayıcı **uygulamasına** sağ tıklayın ve Özellikler'i **seçin.** Kuralı etkinleştirmek **veya** devre dışı bırakmak ya da bağlantı noktası numaralarını, protokolleri veya ağ türlerini değiştirmek için Özellikler sekmelerini kullanın.
  - Uzaktan hata ayıklayıcı uygulaması kurallar listesinde görünmüyorsa, doğru bağlantı [noktalarını ekleyin ve yapılandırabilirsiniz.](#configure-ports-for-remote-debugging)

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [Visual Studio hata ayıklayıcısı bağlantı noktası atamalarını yeniden yükleme](../debugger/remote-debugger-port-assignments.md)
