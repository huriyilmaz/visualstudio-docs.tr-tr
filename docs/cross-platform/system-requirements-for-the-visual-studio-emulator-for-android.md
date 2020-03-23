---
title: Android için Visual Studio Emülatör için Sistem Gereksinimleri | Microsoft Dokümanlar
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f1462769a4ba9929a000bca998c1fe3708908798
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272042"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Emülatörü için sistem gereksinimleri

Android için Visual Studio Emulator Hyper-V, Windows 8 ve daha sonraki sürümleri için sanallaştırma teknolojisi sanalbir makine olarak çalışır. Emülatörçalıştırmak için bilgisayarınızın bu konuda açıklandığı gibi Hyper-V çalıştırmak için gereksinimleri karşılaması gerekir.

Kurulum programı, emülatöryüklediğinizde bu ön koşulları sessizce sizin için yapılandırmaya çalışır. Kurulum ön koşulları başarıyla yapılandırdığında, emülatör beklendiği gibi çalışır. Aksi takdirde bu ön koşulları el ile etkinleştirmeniz gerekebilir. Ön koşulları el ile yapılandırmanız gerekiyorsa, adımlar ve araçlar Windows Phone Emülatörü için [burada](/previous-versions/windows/apps/jj863509\(v=vs.105\)) açıklanan adımlarla aynıdır.

> [!IMPORTANT]
> Emülatör için kurulum programı Android için Visual Studio Emulator çalıştırmak için ön koşulları denetler. Ön koşullar yoksa uyarılar görüntüler, ancak bunları gerektirmez.

## <a name="quick-checklist"></a><a name="Checklist"></a>Hızlı denetim listesi

Burada Android için Visual Studio Emülatörü çalıştırmak için gereksinimleri hızlı bir kontrol listesidir. Daha ayrıntılı bilgi için bu konuyla ilgili sonraki bölümlere bakın.

Sistem gereksinimleri

- Hyper-V desteği (aşağıdaki Hyper-V gereksinimlerine bakın)

- 6 GB veya daha fazla RAM.

- Windows 8, Windows 8.1, Windows10 veya daha yüksek Pro sürümü 64 bit sürümü

- SSSE3 veya daha sonra destekleyen bir işlemci.

Ağ gereksinimleri

- DHCP

- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları

Hiper-V gereksinimleri

- BIOS'ta aşağıdaki özellikler desteklenmelidir:

  - Donanım destekli sanallaştırma

  - İkinci Düzey Adres Çevirisi (SLAT)

  - Donanım tabanlı Veri Yürütme Önleme (DEP)

- Windows'da Hyper-V etkin ve çalışır durumda olmalıdır.

- Yerel Hyper-V Yöneticileri grubunun bir üyesi olabilirsiniz.

## <a name="system-requirements"></a>Sistem gereksinimleri
 Bilgisayarınız aşağıdaki gereksinimleri karşılamalıdır:

- Hyper-V desteği (bkz. [Hyper-V gereksinimleri)](#hyper-v-requirements)

- 6 GB veya daha fazla RAM.

- Windows 8, Windows 8.1, Windows10 veya daha yüksek Pro sürümü 64 bit sürümü.

Denetim Masası'nda RAM ve Windows gereksinimlerini denetlemek için Sistem ve Güvenlik'i seçin ve ardından Sistem'i seçin.

![Sistem gereksinimlerini doğrulama](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>Ağ gereksinimleri

Ağınız aşağıdaki gereksinimleri karşılamalıdır:

- DHCP

   Emülatör, kendisini ağüzerinde kendi IP adresine sahip ayrı bir aygıt olarak yapılandırdığı için DHCP gerektirir.

- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları

   DNS ve ağ geçidi ayarlarını emülatör için el ile yapılandırmak mümkün değildir.

  Emülatördeki ağ sorunlarını gidermek için aşağıdaki konulara bakın:

- [Android için Visual Studio Öykünücüsü’nde Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Hiper-V gereksinimleri

BIOS'ta Hyper-V gereksinimleri

Bilgisayarınızın BIOS'u aşağıdaki gereksinimleri desteklemeli ve etkinleştirilmelidir:

- Donanım destekli sanallaştırma

- İkinci Düzey Adres Çevirisi (SLAT)

- Donanım tabanlı Veri Yürütme Önleme (DEP)

Windows'da Hyper-V gereksinimleri

Bilgisayarınız ve BIOS ayarları zaten Hyper-V'yi destekleyecek şekilde yapılandırıldığınızda, kurulum programı Hyper-V'yi etkinleştirer ve başlatır. Aksi takdirde bu gereksinimleri el ile etkinleştirmeniz gerekebilir.

|Gereksinim|Bu gereksinimi nasıl denetler ve etkinleştirin|
|-----------------|----------------------------------------------|
|Hyper-V yüklü olmalıdır|[Windows Phone emülatörü için Hyper-V'yi etkinleştirmek için](/previous-versions/windows/apps/jj863509(v=vs.105))kullanılan talimatları izleyin.<br /><br /> Hizmetler snap-in **Hyper-V Sanal Makine Yönetimi** hizmetinin durumunu kontrol edin.|
|Hyper-V çalışıyor olmalı.|Hizmetleri yönetme hakkında daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> -   [Bir hizmeti başlatma, durdurma, duraklatma, devam ettirme veya yeniden başlatma](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Bir hizmetin nasıl başlatıldığını yapılandırma](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Yerel Hyper-V Yöneticileri grubunun bir üyesi olabilirsiniz.

 Haklarınızı yükseltmek için yinelenen bir istem olmadan Android için Visual Studio Emülatörü çalıştırmak için, yerel Hyper-V Yöneticileri grubunun bir üyesi olmak zorunda. SDK'yı yüklediğinizde zaten bilgisayarda yerel bir yöneticiyseniz, SDK'nın kurulum programı sizi Hyper-V Yöneticileri grubuna ekler. Aksi takdirde bu gereksinimi el ile etkinleştirmeniz gerekebilir.

 Emülatörçalıştırdığınızda, Hyper-V Yöneticileri grubunun bir üyesi değilseniz, gruba katılmanız istenir (iletişim kutusu Windows Phone emülatörünün ifadesidir). Gruba katılmak yönetici hakları gerektirir.

> [!IMPORTANT]
> Gruba katıldıktan sonra, değişikliğin etkili olması için oturumu kapatın veya yeniden başlatın.

 ![Hyper&#45;V Administrators güvenlik grubuna katılma](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 Kendinizi bir gruba el ile eklemek için Yerel Kullanıcılar ve Gruplar'ı açın.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>Önyüklenebilir bir VHD'den emülatör çalıştırma desteklenmez
 Önyüklemeli bir VHD'den Windows çalıştırırken Android için Visual Studio Emülatör'de bir uygulamayı çalıştırmaya çalışırsanız, emülatörün başlatılması genellikle birkaç dakika sürer veya başlatılamaz. Emülatör başlatıldığında aşağıdaki iletiyi görürsünüz: Uygulama dağıtımı başarısız oldu. Lütfen tekrar deneyin.

 Bu yapılandırma desteklenmez. İlgili konular hakkında daha fazla bilgi için [Android için Visual Studio Emülatörü Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)konusuna bakın.

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Hyper-V sıkıştırılmamış ve şifrelenmemiş dosyalar gerektirir
 NTFS dosya sistemiyle yapılandırılan bir sabit diskte Hyper-V tarafından kullanılan sanal sabit disk dosyaları sıkıştırılmamış ve şifrelenmemiş olmalıdır. Aşağıdaki dizinlerin sıkıştırılmadığını veya şifrelenmediğinden emin olun:

- %localappdata%\Microsoft\XDE

- C:\Program Dosyaları (x86)\Microsoft Emülatör Yöneticisi

- C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

ReFS dosya sisteminde, sanal sabit disk dosyaları bütünlük biti kümesine sahip olmamalıdır.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Donanım grafik yönlendirme (OpenGL ES desteği) gereksinimleri

Emülatörün OpenGL ES tarafından kullanılanlar gibi GPU'ya yapılan çağrıları taklit edebilmesi için makinenizin uygun DirectX sürücüleri yüklü directx uyumlu bir GPU'ya sahip olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Android için Visual Studio Öykünücüsü’nde Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
