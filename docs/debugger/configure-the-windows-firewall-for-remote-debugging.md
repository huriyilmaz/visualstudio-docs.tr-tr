---
title: Uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma | Microsoft Docs
description: Uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırın. Uzaktan hata ayıklama için bağlantı noktalarını yapılandırın. Uzaktan hata ayıklama bağlantısında sorun giderin.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 52264580e428fa6a2c33d80ea8fb9fb8e07f0c59
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149333"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma

Windows güvenlik duvarı tarafından korunan bir ağda, güvenlik duvarının uzaktan hata ayıklamaya izin verecek şekilde yapılandırılması gerekir. Visual Studio ve uzaktan hata ayıklama araçları, yükleme veya başlatma sırasında doğru güvenlik duvarı bağlantı noktalarını açmaya çalışır, ancak bağlantı noktalarını açmanız veya uygulamalara el ile izin vermeniz de gerekebilir.

Bu konuda, Windows 10, 8/8.1 ve 7 ' de uzaktan hata ayıklamayı etkinleştirmek için Windows Güvenlik Duvarı 'nın nasıl yapılandırılacağı açıklanmaktadır; ve Windows Server 2012 R2, 2012 ve 2008 R2 bilgisayarları. Visual Studio ve uzak bilgisayarın aynı işletim sistemini çalıştırması gerekmez. Örneğin, Visual Studio bilgisayarı Windows 10 çalıştırabilir ve uzak bilgisayar Windows Server 2012 R2 'yi çalıştırabilir.

>[!NOTE]
>Windows Güvenlik Duvarı 'nı yapılandırmaya yönelik yönergeler, farklı işletim sistemlerinde ve Windows 'un eski sürümlerinde farklılık gösterebilir. Windows 8/8.1, Windows 10 ve Windows Server 2012 ayarları Word *uygulamasını* kullanır, Windows 7 ve windows Server 2008 Word *programını* kullanır.

## <a name="configure-ports-for-remote-debugging"></a>Uzaktan hata ayıklama için bağlantı noktalarını yapılandırma

Visual Studio ve uzaktan hata ayıklayıcı yükleme veya başlatma sırasında doğru bağlantı noktalarını açmaya çalışır. Ancak, üçüncü taraf güvenlik duvarı gibi bazı senaryolarda bağlantı noktalarını el ile açmanız gerekebilir.

**Bir bağlantı noktasını açmak için:**

1. Windows **Başlat** menüsünde, **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı 'nı** arayın ve açın. Windows 10 ' da bu, **Gelişmiş Güvenlik Özellikli Windows Defender güvenlik duvarıdır**.

1. Yeni gelen bağlantı noktası için **gelen kuralları** ' nı seçin ve ardından **Yeni kural**' ı seçin. Giden kuralı için bunun yerine **giden kuralları** ' nı seçin.

1. **Yeni gelen kuralı sihirbazında**, **bağlantı noktası**' nı seçin ve ardından **İleri**' yi seçin.

1. Aşağıdaki tablolardaki bağlantı noktası numarasına bağlı olarak **TCP** veya **UDP**' yi seçin.

1. **Belirli yerel bağlantı noktaları** altında, aşağıdaki tablolardan bir bağlantı noktası numarası girin ve **İleri**' yi seçin.

1. **Bağlantıya Izin ver**' i seçin ve ardından **İleri**' yi seçin.

1. Uzaktan bağlantı için ağ türü de dahil olmak üzere etkinleştirilecek bir veya daha fazla ağ türünü seçin ve ardından **İleri**' yi seçin.

1. Kural için bir ad ekleyin (örneğin, **msvsmon**, **IIS** veya **Web dağıtımı**) ve ardından **son**' u seçin.

   Yeni kural, **gelen kurallar** veya **giden kurallar** listesinde görünmelidir ve seçilmelidir.

**PowerShell kullanarak bir bağlantı noktasını açmak için:**

Windows Güvenlik Duvarı için, [New-NetFirewallRule](/powershell/module/netsecurity/new-netfirewallrule?view=win10-ps)gibi PowerShell komutlarını kullanabilirsiniz.

Aşağıdaki örnek, uzak bilgisayarda uzaktan hata ayıklayıcı için 4024 numaralı bağlantı noktasını açar. Kullanmanız gereken yol farklı olabilir.

```ps
New-NetFirewallRule -DisplayName "msvsmon" -Direction Inbound -Program "Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe" -LocalPort 4024 -Protocol TCP -Authentication Required -Action Allow
```

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Uzak bilgisayarda uzaktan hata ayıklamayı etkinleştiren bağlantı noktaları

Uzaktan hata ayıklama için, uzak bilgisayarda aşağıdaki bağlantı noktalarının açık olması gerekir:

::: moniker range="vs-2017"

|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|4022|Gelen|TCP|VS 2017 için. Her Visual Studio sürümü için bağlantı noktası numarası 2 ' ye kadar artar. Daha fazla bilgi için bkz. [Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).|
|4023|Gelen|TCP|VS 2017 için. Her Visual Studio sürümü için bağlantı noktası numarası 2 ' ye kadar artar. Bu bağlantı noktası yalnızca uzaktan hata ayıklayıcının 64 bit sürümünden 32 bitlik bir işlemin uzaktan hata ayıklamasını yapmak için kullanılır. Daha fazla bilgi için bkz.  [Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).|
|3702|Tarafına|UDP|Seçim Uzaktan hata ayıklayıcı keşfi için gereklidir.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|4024|Gelen|TCP|VS 2019 için. Her Visual Studio sürümü için bağlantı noktası numarası 2 ' ye kadar artar. Daha fazla bilgi için bkz. [Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).|
|4025|Gelen|TCP|VS 2019 için. Her Visual Studio sürümü için bağlantı noktası numarası 2 ' ye kadar artar. Bu bağlantı noktası yalnızca uzaktan hata ayıklayıcının 64 bit sürümünden 32 bitlik bir işlemin uzaktan hata ayıklamasını yapmak için kullanılır. Daha fazla bilgi için bkz.  [Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).|
|3702|Tarafına|UDP|Seçim Uzaktan hata ayıklayıcı keşfi için gereklidir.|

::: moniker-end

**Araçlar** seçenekler hata ayıklama bölümünde **yönetilen uyumluluk modunu kullan**  >    >  ' ı seçerseniz, bu ek uzaktan hata ayıklayıcı bağlantı noktalarını açın. Hata ayıklayıcı yönetilen uyumluluk modu, hata ayıklayıcının eski, Visual Studio 2010 sürümünü sunar.

|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|135, 139, 445|Tarafına|TCP|Gereklidir.|
|137, 138|Tarafına|UDP|Gereklidir.|

Etki alanı ilkeniz, IPSec üzerinden ağ iletişimi gerçekleştirilmesini gerektiriyorsa, hem Visual Studio 'da hem de uzak bilgisayarlarda ek bağlantı noktalarını açmanız gerekir. Uzak bir IIS Web sunucusunda hata ayıklamak için uzak bilgisayarda 80 numaralı bağlantı noktasını açın.

|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|
|-|-|-|-|
|500, 4500|Tarafına|UDP|Etki alanı ilkeniz, IPSec aracılığıyla ağ iletişimi gerçekleştirilmesini gerektiriyorsa gereklidir.|
|80|Tarafına|TCP|Web sunucusu hata ayıklaması için gereklidir.|

Windows Güvenlik Duvarı aracılığıyla belirli uygulamalara izin vermek için bkz. [Windows Güvenlik Duvarı üzerinden uzaktan hata ayıklamayı yapılandırma](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Windows Güvenlik Duvarı üzerinden uzaktan hata ayıklamayı yapılandırma

Uzaktan hata ayıklama araçlarını uzak bilgisayara yükleyebilir veya paylaşılan bir klasörden çalıştırabilirsiniz. Her iki durumda da, uzak bilgisayar güvenlik duvarının doğru şekilde yapılandırılması gerekir.

Uzak bir bilgisayarda, uzaktan hata ayıklama araçları şu şekilde bulunur:

*\<Visual Studio installation directory\>\\Common7 \\ IDE \\ Uzaktan hata ayıklayıcı\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Windows Güvenlik Duvarı üzerinden uzaktan hata ayıklayıcıya izin verme ve yapılandırma

1. Windows **Başlat** menüsünde **Windows Güvenlik Duvarı** veya **Windows Defender güvenlik duvarı** araması yapın ve açın.

1. **Windows Güvenlik Duvarı aracılığıyla bir uygulamaya Izin ver**' i seçin.

1. **Uzaktan hata ayıklayıcı** veya **Visual Studio uzaktan hata ayıklayıcı** **izin verilen uygulamalar ve Özellikler** altında görünmezse, **Ayarları Değiştir**' i seçin ve sonra **başka bir uygulamaya izin ver**' i seçin.

1. Uzaktan hata ayıklayıcı uygulaması hala **Uygulama Ekle** iletişim kutusunda listelenmiyorsa, **Araştır**' ı seçin ve \<Visual Studio installation directory\> \\ \\ \\ \\ \<x86*, *x64*, or *Appx*\> uygulamanızın uygun mimarisine bağlı olarak * Common7 IDE uzaktan hata ayıklayıcı ' ya gidin. *msvsmon.exe*' yi seçin ve ardından **Ekle**' yi seçin.

1. **Uygulamalar** listesinde, az önce eklediğiniz **Uzaktan hata ayıklayıcıyı** seçin. **Ağ türleri**' ni seçin ve ardından uzak bağlantı için ağ türü de dahil olmak üzere bir veya daha fazla ağ türü seçin.

1. **Ekle**' yi ve ardından **Tamam**' ı seçin.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Uzaktan hata ayıklama bağlantısı sorunlarını giderme

Uzaktan hata ayıklayıcı ile uygulamanıza iliştiretemezsiniz, uzaktan hata ayıklama güvenlik duvarı bağlantı noktalarının, protokollerin, ağ türlerinin ve uygulama ayarlarının tümünün doğru olduğundan emin olun.

- Windows **Başlat** menüsünde **Windows Güvenlik Duvarı**'Nı arayıp açın ve **Windows Güvenlik Duvarı aracılığıyla uygulamaya izin ver**' i seçin. **Uzaktan hata ayıklayıcı** veya **Visual Studio uzaktan hata ayıklayıcı** , **izin verilen uygulamalar ve Özellikler** listesinde seçili onay kutusuyla göründüğünden emin olun ve doğru ağ türleri seçilidir. Aksi takdirde, [doğru uygulamaları ve ayarları ekleyin](#configure-remote-debugging-through-windows-firewall).

- Windows **Başlat** menüsünde, **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı 'nı** arayın ve açın. **Uzaktan hata ayıklayıcı** veya **Visual Studio uzaktan hata ayıklayıcı** , yeşil onay işareti simgesiyle **gelen kuralların** altında (ve isteğe bağlı olarak, **giden kuralları**) göründüğünden ve tüm ayarların doğru olduğundan emin olun.

  - Kural ayarlarını görüntülemek veya değiştirmek için, listede **Uzaktan hata ayıklayıcı** uygulamasına sağ tıklayın ve **Özellikler**' i seçin. Kuralı etkinleştirmek veya devre dışı bırakmak ya da bağlantı noktası numaralarını, protokolleri veya ağ türlerini değiştirmek için **Özellikler** sekmelerini kullanın.
  - Uzaktan hata ayıklayıcı uygulaması kurallar listesinde görünmüyorsa, [doğru bağlantı noktalarını ekleyin ve yapılandırın](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
