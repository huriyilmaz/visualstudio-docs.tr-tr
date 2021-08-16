---
title: uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma | Microsoft Docs
description: uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırın. Uzaktan hata ayıklama için bağlantı noktalarını yapılandırın. Uzaktan hata ayıklama bağlantısında sorun giderin.
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
ms.openlocfilehash: 9f0be1f06d15c3309d8e67cab50a444228d99241fcde9c8648cc24431d27260f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345874"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma

Windows güvenlik duvarı tarafından korunan bir ağda, güvenlik duvarının uzaktan hata ayıklamaya izin verecek şekilde yapılandırılması gerekir. Visual Studio ve uzaktan hata ayıklama araçları, yükleme veya başlatma sırasında doğru güvenlik duvarı bağlantı noktalarını açmaya çalışır, ancak bağlantı noktalarını açmanız veya uygulamalara el ile izin vermeniz de gerekebilir.

bu konuda, Windows 10, 8/8.1 ve 7 ' de uzaktan hata ayıklamayı etkinleştirmek üzere Windows güvenlik duvarının nasıl yapılandırılacağı açıklanmaktadır. ve Windows Server 2012 r2, 2012 ve 2008 r2 bilgisayarları. Visual Studio ve uzak bilgisayar aynı işletim sistemini çalıştırmak zorunda değildir. örneğin, Visual Studio bilgisayar Windows 10 çalıştırabilir ve uzak bilgisayar Windows Server 2012 R2 çalıştırabilir.

>[!NOTE]
>Windows güvenlik duvarını yapılandırmaya yönelik yönergeler, farklı işletim sistemlerinde ve Windows eski sürümleri için biraz farklılık gösterir. Windows 8/8,1, Windows 10 ve Windows Server 2012 ayarları word *uygulamasını* kullanır, ancak Windows 7 ve Windows Server 2008 word *programını* kullanın.

## <a name="configure-ports-for-remote-debugging"></a>Uzaktan hata ayıklama için bağlantı noktalarını yapılandırma

Visual Studio ve uzaktan hata ayıklayıcı yükleme veya başlatma sırasında doğru bağlantı noktalarını açmaya çalışır. Ancak, üçüncü taraf güvenlik duvarı gibi bazı senaryolarda bağlantı noktalarını el ile açmanız gerekebilir.

**Bir bağlantı noktasını açmak için:**

1. Windows **başlat** menüsünde, **gelişmiş güvenlik özellikli Windows güvenlik duvarı** araması yapın ve açın. Windows 10, **gelişmiş güvenlik özellikli güvenlik duvarıdır Windows Defender**.

1. Yeni gelen bağlantı noktası için **gelen kuralları** ' nı seçin ve ardından **Yeni kural**' ı seçin. Giden kuralı için bunun yerine **giden kuralları** ' nı seçin.

1. **Yeni gelen kuralı sihirbazında**, **bağlantı noktası**' nı seçin ve ardından **İleri**' yi seçin.

1. Aşağıdaki tablolardaki bağlantı noktası numarasına bağlı olarak **TCP** veya **UDP**' yi seçin.

1. **Belirli yerel bağlantı noktaları** altında, aşağıdaki tablolardan bir bağlantı noktası numarası girin ve **İleri**' yi seçin.

1. **Bağlantıya Izin ver**' i seçin ve ardından **İleri**' yi seçin.

1. Uzaktan bağlantı için ağ türü de dahil olmak üzere etkinleştirilecek bir veya daha fazla ağ türünü seçin ve ardından **İleri**' yi seçin.

1. Kural için bir ad ekleyin (örneğin, **msvsmon**, **IIS** veya **Web dağıtımı**) ve ardından **son**' u seçin.

   Yeni kural, **gelen kurallar** veya **giden kurallar** listesinde görünmelidir ve seçilmelidir.

**PowerShell kullanarak bir bağlantı noktasını açmak için:**

Windows güvenlik duvarı için, [New-netfirewallrule](/powershell/module/netsecurity/new-netfirewallrule?view=win10-ps)gibi PowerShell komutlarını kullanabilirsiniz.

Aşağıdaki örnek, uzak bilgisayarda uzaktan hata ayıklayıcı için 4024 numaralı bağlantı noktasını açar. Kullanmanız gereken yol farklı olabilir.

```ps
New-NetFirewallRule -DisplayName "msvsmon" -Direction Inbound -Program "Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe" -LocalPort 4024 -Protocol TCP -Authentication Required -Action Allow
```

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Uzak bilgisayarda uzaktan hata ayıklamayı etkinleştiren bağlantı noktaları

Uzaktan hata ayıklama için, uzak bilgisayarda aşağıdaki bağlantı noktalarının açık olması gerekir:

::: moniker range="vs-2017"

|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|4022|Gelen|TCP|VS 2017 için. her Visual Studio sürümü için bağlantı noktası numarası 2 ' ye kadar artar. daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamalarını Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|Gelen|TCP|VS 2017 için. her Visual Studio sürümü için bağlantı noktası numarası 2 ' ye kadar artar. Bu bağlantı noktası yalnızca uzaktan hata ayıklayıcının 64 bit sürümünden 32 bitlik bir işlemin uzaktan hata ayıklamasını yapmak için kullanılır. daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamalarını Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Tarafına|UDP|Seçim Uzaktan hata ayıklayıcı keşfi için gereklidir.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|4024|Gelen|TCP|VS 2019 için. her Visual Studio sürümü için bağlantı noktası numarası 2 ' ye kadar artar. daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamalarını Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|Gelen|TCP|VS 2019 için. her Visual Studio sürümü için bağlantı noktası numarası 2 ' ye kadar artar. Bu bağlantı noktası yalnızca uzaktan hata ayıklayıcının 64 bit sürümünden 32 bitlik bir işlemin uzaktan hata ayıklamasını yapmak için kullanılır. daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamalarını Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Tarafına|UDP|Seçim Uzaktan hata ayıklayıcı keşfi için gereklidir.|

::: moniker-end

**Araçlar** seçenekler hata ayıklama bölümünde **yönetilen uyumluluk modunu kullan**  >    >  ' ı seçerseniz, bu ek uzaktan hata ayıklayıcı bağlantı noktalarını açın. hata ayıklayıcı yönetilen uyumluluk modu, hata ayıklayıcının eski, Visual Studio 2010 sürümlerini sunar.

|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|135, 139, 445|Tarafına|TCP|Gereklidir.|
|137, 138|Tarafına|UDP|Gereklidir.|

etki alanı ilkeniz ıpsec aracılığıyla ağ iletişimini gerektiriyorsa, Visual Studio ve uzak bilgisayarlarda ek bağlantı noktalarını açmanız gerekir. Uzak bir IIS Web sunucusunda hata ayıklamak için uzak bilgisayarda 80 numaralı bağlantı noktasını açın.

|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|500, 4500|Tarafına|UDP|Etki alanı ilkeniz, IPSec aracılığıyla ağ iletişimi gerçekleştirilmesini gerektiriyorsa gereklidir.|
|80|Giden|TCP|Web sunucusu hata ayıklaması için gereklidir.|

Belirli uygulamalara güvenlik duvarı üzerinden izin Windows için bkz. Güvenlik Duvarı üzerinden uzaktan [Windows yapılandırma.](#configure-remote-debugging-through-windows-firewall)

## <a name="configure-remote-debugging-through-windows-firewall"></a>Güvenlik duvarı aracılığıyla uzaktan Windows yapılandırma

Uzak hata ayıklama araçlarını uzak bilgisayara yükleyebilir veya paylaşılan bir klasörden çalıştırabilirsiniz. Her iki durumda da uzak bilgisayar güvenlik duvarının doğru yapılandırılması gerekir.

Uzak bir bilgisayarda, uzaktan hata ayıklama araçları şu işlemlerdedir:

*\<Visual Studio installation directory\>\\Common7 \\ IDE \\ Uzaktan Hata Ayıklayıcısı\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Güvenlik Duvarı üzerinden uzaktan hata ayıklayıcıya izin Windows yapılandırma

1. Başlat Windows **Güvenlik** Duvarı'nı veya Güvenlik **Duvarı'nı Windows** **için arama Windows Defender açın.**

1. Güvenlik Duvarı **üzerinden bir uygulamaya izin Windows seçin.**

1. Uzaktan **Hata Ayıklayıcısı veya** **Visual Studio Uzaktan Hata Ayıklayıcı** izin verilen uygulamalar ve özellikler altında görünmüyorsa **Ayarları** değiştir'i ve ardından Başka bir uygulamaya izin **ver'i seçin.**

1. Uzaktan hata ayıklayıcı uygulaması hala Uygulama  ekle iletişim kutusunda listelenmiyorsa, uygulamanıza uygun mimariye bağlı olarak Gözat 'ı seçin ve * Ortak7 IDE Uzaktan Hata Ayıklayıcısı'ne \<Visual Studio installation directory\> \\ \\ \\ \\ \<x86*, *x64*, or *Appx*\> gidin. Öğesini *msvsmon.exe* ve ardından **Ekle'yi seçin.**

1. Uygulamalar **listesinde,** yeni **ekley istediğiniz Uzaktan Hata** Ayıklayıcı'sını seçin. Ağ **türleri'ne** ve ardından uzak bağlantının ağ türü de dahil olmak üzere bir veya daha fazla ağ türü seçin.

1. **Ekle'yi** ve ardından Tamam'ı **seçin.**

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Uzaktan hata ayıklama bağlantısı sorunlarını giderme

Uygulamanıza uzaktan hata ayıklayıcı ile bağlana biliyorsanız uzaktan hata ayıklama güvenlik duvarı bağlantı noktalarının, protokollerin, ağ türlerinin ve uygulama ayarlarının doğru olduğundan emin olun.

- Başlat menüsünde Windows **Güvenlik** Duvarı'nı arayın **ve Windows Güvenlik** Duvarı aracılığıyla bir uygulamaya izin Windows **seçin.** Uzaktan Hata **Ayıklayıcısı'nın** **Visual Studio Uzaktan Hata Ayıklayıcı** izin  verilen uygulamalar ve özellikler listesinde seçili bir onay kutusuyla göründüğünden ve doğru ağ türlerinin seçildiğinden emin olun. Yoksa, [doğru uygulamaları ve ayarları ekleyin.](#configure-remote-debugging-through-windows-firewall)

- Başlat menüsünde Windows **Güvenlik** Duvarı'nı **arayın ve Windows Güvenlik Duvarı'nı açın.** Uzaktan Hata **Ayıklayıcısı'nın** **Visual Studio Uzaktan Hata Ayıklayıcı** kurallar **(ve** isteğe bağlı olarak **Giden** Kuralları) altında yeşil onay işareti simgesiyle göründüğünden ve tüm ayarların doğru olduğundan emin olun.

  - Kural ayarlarını görüntülemek veya değiştirmek için, listeden Uzaktan Hata Ayıklayıcı **uygulamasına** sağ tıklayın ve Özellikler'i **seçin.** Kuralı etkinleştirmek **veya** devre dışı bırakmak ya da bağlantı noktası numaralarını, protokolleri veya ağ türlerini değiştirmek için Özellikler sekmelerini kullanın.
  - Uzaktan hata ayıklayıcı uygulaması kurallar listesinde görünmüyorsa, doğru [bağlantı noktalarını ekleyin ve yapılandırabilirsiniz.](#configure-ports-for-remote-debugging)

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [Visual Studio hata ayıklayıcısı bağlantı noktası atamalarını yeniden yükleme](../debugger/remote-debugger-port-assignments.md)
