---
title: Android öykünücüsü için sistem gereksinimleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: b1b77dc7e01ae791379dda52b305ebcdbbf68447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791056"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü Sistem Gereksinimleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Android için Visual Studio öykünücüsü, Windows 8 ve sonraki sürümleri için sanallaştırma teknolojisi olan Hyper-V ' d a sanal makine olarak çalışır. Öykünücüyü çalıştırmak için bilgisayarınızın bu konuda açıklandığı gibi Hyper-V ' d i çalıştırmak için gereken gereksinimleri karşılaması gerekir.

 Kurulum programı, öykünücüsü yüklerken sessizce bu önkoşulları yapılandırmaya çalışır. Kurulum önkoşulları başarıyla yapılandırdığında, öykünücü yalnızca beklendiği gibi çalışmaktadır. Aksi takdirde, bu önkoşulları el ile etkinleştirmeniz gerekebilir. Önkoşulları el ile yapılandırmanız gerekirse, adımlar ve araçlar Windows Phone öykünücüsü için [burada](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx) açıklanan adımlardan aynıdır.

> [!IMPORTANT]
> Öykünücü için Kurulum programı, Android için Visual Studio öykünücüsü 'nü çalıştırmaya yönelik önkoşulları denetler. Önkoşullar yoksa uyarıları görüntüler, ancak bunu gerektirmez.

 Bu konuda aşağıdaki bölümler yer almaktadır.

- [Hızlı denetim listesi](#Checklist)

- [Sistem gereksinimleri](#System)

- [Ağ gereksinimleri](#Network)

- [Hyper-V gereksinimleri](#HyperV)

- [Öykünücüyü önyüklenebilir bir VHD 'den çalıştırmak desteklenmez](#BootableVHD)

- [Hyper-V sıkıştırılmamış ve şifrelenmemiş dosyalar gerektirir](#Files)

## <a name="quick-checklist"></a><a name="Checklist"></a> Hızlı denetim listesi
 Android için Visual Studio öykünücüsü 'nü çalıştırmaya yönelik gereksinimlerin hızlı bir denetim listesi aşağıda verilmiştir. Daha ayrıntılı bilgi için bu konudaki sonraki bölümlere bakın.

 Sistem gereksinimleri

- Hyper-V desteği (aşağıdaki Hyper-V gereksinimlerine bakın)

- 6 GB veya daha fazla RAM.

- Windows 8, Windows 8.1, Windows10 veya üzeri Pro sürümünün 64 bit sürümü

- SSSE3 veya üstünü destekleyen bir işlemci.

  Ağ gereksinimleri

- DHCP

- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları

  Hyper-V gereksinimleri

- BIOS 'ta aşağıdaki özellikler desteklenmelidir:

  - Donanım destekli sanallaştırma

  - İkinci düzey adres çevirisi (SLAT)

  - Donanım tabanlı veri yürütme engellemesi (DEP)

- Windows 'de, Hyper-V etkinleştirilmeli ve çalışıyor olmalıdır.

- Yerel Hyper-V yöneticileri grubunun bir üyesi olmanız gerekir.

## <a name="system-requirements"></a><a name="System"></a> Sistem gereksinimleri
 Bilgisayarınızın aşağıdaki gereksinimleri karşılaması gerekir:

- Hyper-V desteği (bkz. [Hyper-v gereksinimleri](#HyperV))

- 6 GB veya daha fazla RAM.

- Windows 8, Windows 8.1, Windows10 veya üzeri Pro sürümünün 64 bitlik sürümü.

  RAM ve Windows gereksinimlerini denetlemek için, Denetim Masası 'nda sistem ve güvenlik ' i seçin ve ardından Sistem ' i seçin.

  ![Sistem gereksinimlerini doğrulama](../cross-platform/media/android-emu-system-requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a><a name="Network"></a> Ağ gereksinimleri
 Ağınızın aşağıdaki gereksinimleri karşılaması gerekir:

- DHCP

   Öykünücü, kendisini ağ üzerinde kendi IP adresiyle ayrı bir cihaz olarak yapılandırdığından DHCP gerektirir.

- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları

   Öykünücü için DNS ve ağ geçidi ayarlarını el ile yapılandırmak mümkün değildir.

  Öykünücüdeki ağ sorunlarını gidermek için aşağıdaki konulara bakın:

- [Android için Visual Studio Öykünücüsü’nde Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a><a name="HyperV"></a> Hyper-V gereksinimleri
 BIOS 'ta Hyper-V gereksinimleri

 Bilgisayarınızın BIOS 'U aşağıdaki gereksinimleri desteklemelidir ve bu koşulların etkinleştirilmesi gerekir:

- Donanım destekli sanallaştırma

- İkinci düzey adres çevirisi (SLAT)

- Donanım tabanlı veri yürütme engellemesi (DEP)

  Windows 'daki Hyper-V gereksinimleri

  Bilgisayarınız ve BIOS ayarlarınız zaten Hyper-V ' d i destekleyecek şekilde yapılandırıldıysa, Kurulum programı Hyper-V ' ı sağlar ve başlatır. Aksi takdirde, bu gereksinimleri el ile etkinleştirmeniz gerekebilir.

|Gereksinim|Bu gereksinimi denetleme ve etkinleştirme|
|-----------------|----------------------------------------------|
|Hyper-V yüklü olmalıdır|[Windows Phone öykünücüsü Için Hyper-V](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx)' i etkinleştirmek için kullanılan yönergeleri izleyin.<br /><br /> Hizmetler ek bileşeninde **Hyper-V sanal makine yönetimi** hizmetinin durumunu denetleyin.|
|Hyper-V çalışıyor olmalıdır.|Hizmetleri yönetme hakkında daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> -   [Hizmeti başlatma, durdurma, duraklatma, devam ettirme veya yeniden başlatma](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Hizmetin nasıl başlatıldığını yapılandırma](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Yerel Hyper-V yöneticileri grubunun bir üyesi olmanız gerekir.

 Haklarınızı yükseltmek için yinelenen bir istem olmadan Android için Visual Studio öykünücüsü 'nü çalıştırmak için yerel Hyper-V yöneticileri grubunun bir üyesi olmanız gerekir. SDK 'Yı yüklerken bilgisayarda zaten bir yerel yönetici varsa SDK 'nın Kurulum programı sizi Hyper-V Yöneticiler grubuna ekler. Aksi takdirde, bu gereksinimi el ile etkinleştirmeniz gerekebilir.

 Öykünücüyü çalıştırdığınızda, zaten Hyper-V yöneticileri grubunun bir üyesi değilseniz, gruba katılmanız istenir (iletişim kutusu Windows Phone öykünücüsünü ifade eder). Gruba katılabilmek için yönetici hakları gerekir.

> [!IMPORTANT]
> Gruba katılırsanız, değişikliğin etkili olması için oturumu kapatın veya yeniden başlatın.

 ![Hyper&#45;V yöneticileri güvenlik grubuna katılma](../cross-platform/media/android-emu-hyperv-admin.png "Android_Emu_HyperV_Admin")

 Kendiniz bir gruba el ile eklemek için, yerel kullanıcılar ve Gruplar ek bileşenini açın.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a><a name="BootableVHD"></a> Öykünücüyü önyüklenebilir bir VHD 'den çalıştırmak desteklenmez
 Windows 'u önyüklenebilir bir VHD 'den çalıştırdığınız sırada Android için Visual Studio öykünücüsü üzerinde uygulamayı çalıştırmayı denerseniz, öykünücü genellikle başlatılması veya başlatılması birkaç dakika sürer. Öykünücü başlayamazsa şu iletiyi görürsünüz: uygulama dağıtımı başarısız oldu. Lütfen tekrar deneyin.

 Bu yapılandırma desteklenmez. İlgili sorunlar hakkında daha fazla bilgi için bkz. [Android Için Visual Studio öykünücüsü sorunlarını giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a><a name="Files"></a> Hyper-V sıkıştırılmamış ve şifrelenmemiş dosyalar gerektirir
 NTFS dosya sistemiyle yapılandırılmış bir sabit sürücüde, Hyper-V tarafından kullanılan sanal sabit disk dosyalarının sıkıştırması ve şifrelenmemiş olması gerekir. Aşağıdaki dizinlerin sıkıştırıldığından veya şifrelendiğinden emin olun:

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86) \Microsoft öykünücü yöneticisi

- C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

  ReFS dosya sisteminde, sanal sabit disk dosyalarının bütünlük bit kümesi olmamalıdır.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Donanım grafikleri Iletme (OpenGL ES desteği) gereksinimleri
 Öykünücüsünün, OpenGL 'ler tarafından kullanılanlar gibi GPU 'ya yapılan çağrılara öykünmesine olanak sağlamak için, makinenizde uygun DirectX sürücüleri yüklü bir DirectX uyumlu GPU olması gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Android için Visual Studio Öykünücüsü’nde Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
