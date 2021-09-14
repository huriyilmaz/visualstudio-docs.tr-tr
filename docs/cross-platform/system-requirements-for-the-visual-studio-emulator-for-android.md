---
title: Android için VS Emulator sistem gereksinimleri
description: Android'in Hyper-V'Visual Studio Emulator bir sanal makine olarak çalışması için gereken sistem gereksinimleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8568670e43f21227db7e3ef88d41b2c7c0fc63c3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631664"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Emulator gereksinimleri

Visual Studio Emulator, Hyper-V'de sanal makine olarak çalışır. Bu, Windows 8 ve sonraki sürümleri için sanallaştırma teknolojisidir. Öykünücüsünü çalıştırmak için bilgisayarınızın bu konuda açıklandığı gibi Hyper-V çalıştırma gereksinimlerini karşılaması gerekir.

Kurulum programı, öykünücüsü yüklenirken bu önkoşulları sessizce yapılandırmaya çalışır. Kurulum önkoşulları başarıyla yapılandırıldığında öykünücü beklendiği gibi çalışır. Aksi takdirde bu önkoşulları el ile etkinleştirmeniz gerekebilir. Önkoşulları el ile yapılandırmanız gerekirse, adımlar ve araçlar burada açıklanan [adımlarla](/previous-versions/windows/apps/jj863509\(v=vs.105\)) aynı Windows Phone Emulator.

> [!IMPORTANT]
> Öykünücü için kurulum programı, Android için çalıştırma önkoşullarını Visual Studio Emulator denetler. Önkoşullar yoksa ama bunları gerektirmeyen uyarılar görüntüler.

## <a name="quick-checklist"></a><a name="Checklist"></a> Hızlı denetim listesi

Android için uygulama çalıştırma gereksinimlerinin hızlı bir denetim listesi Visual Studio Emulator ve ardından. Daha ayrıntılı bilgi için bu konunun sonraki bölümlerine bakın.

Sistem Gereksinimleri

- Hyper-V desteği (aşağıdaki Hyper-V gereksinimlerine bakın)

- 6 GB veya daha fazla RAM.

- Windows 8, windows10 veya Pro sürümünün Windows 8.1 64 bit sürümü

- SSSE3 veya sonraki bir SSSE'yi destekleyen bir işlemci.

Ağ gereksinimleri

- DHCP

- Dns ve ağ geçidi ayarlarını otomatik olarak yapılandırma

Hyper-V gereksinimleri

- BIOS'ta aşağıdaki özelliklerin desteklenesi gerekir:

  - Donanım destekli sanallaştırma

  - İkinci Düzey Adres Çevirisi (SLAT)

  - Donanım Tabanlı Veri Yürütme Önleme (DEP)

- Bu Windows Hyper-V'nin etkinleştirilmesi ve çalışıyor olması gerekir.

- Yerel Hyper-V Yöneticiler grubunun üyesi olmak gerekir.

## <a name="system-requirements"></a>Sistem Gereksinimleri
 Bilgisayarınızın aşağıdaki gereksinimleri karşılaması gerekir:

- Hyper-V desteği (bkz. [Hyper-V gereksinimleri)](#hyper-v-requirements)

- 6 GB veya daha fazla RAM.

- Windows 8, Windows 8.1, Windows10 veya Pro sürümünün 64 bit sürümü.

RAM ve güvenlik gereksinimlerinizi Windows için Denetim Masası'da Sistem ve Güvenlik'i ve ardından Sistem'i seçin.

![Sistem gereksinimlerini doğrulama](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>Ağ gereksinimleri

Ağınız aşağıdaki gereksinimleri karşılamalıdır:

- DHCP

   Öykünücü, kendisini ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak yapılandıran DHCP gerektirir.

- Dns ve ağ geçidi ayarlarını otomatik olarak yapılandırma

   Öykünücü için DNS ve ağ geçidi ayarlarını el ile yapılandırmak mümkün değildir.

  Öykünücüde ağ sorunlarını gidermek için aşağıdaki konulara bakın:

- [Android için Visual Studio Öykünücüsü’nde Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Hyper-V gereksinimleri

BIOS'ta Hyper-V gereksinimleri

Bilgisayarınızın BIOS'u aşağıdaki gereksinimleri desteklemeli ve etkinleştirilmelidir:

- Donanım destekli sanallaştırma

- İkinci Düzey Adres Çevirisi (SLAT)

- Donanım Tabanlı Veri Yürütme Önleme (DEP)

Windows'de Hyper-V Windows

Bilgisayarınızın ve BIOS ayarlarınız Hyper-V'yi destekleyecek şekilde zaten yapılandırıldığında, kurulum programı Hyper-V'yi sağlar ve başlatır. Aksi takdirde bu gereksinimleri el ile etkinleştirmeniz gerekebilir.

|Gereksinim|Bu gereksinimi denetleme ve etkinleştirme|
|-----------------|----------------------------------------------|
|Hyper-V'nin yüklü olması gerekir|Sanal ağ öykünücüsü [için Hyper-V'yi etkinleştirmek Windows Phone izleyin.](/previous-versions/windows/apps/jj863509(v=vs.105))<br /><br /> Hizmetler ek **bileşeninde Hyper-V Sanal Makine Yönetimi** hizmetinin durumunu kontrol edin.|
|Hyper-V çalışıyor olmalı.|Hizmetleri yönetme hakkında daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> -   [Hizmeti başlatma, durdurma, duraklatma, sürdürme veya yeniden başlatma](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Hizmetin nasıl başlatıldığından emin olmak için](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Yerel Hyper-V Yöneticiler grubunun üyesi olmak gerekir.

 Haklarınızı yükseltmeye Visual Studio Emulator istemi olmadan Android'e Visual Studio Emulator çalıştırmak için yerel Hyper-V Yöneticiler grubunun bir üyesi olmak gerekir. SDK'yı yükleyen bilgisayarda zaten bir yerel yöneticiyseniz, SDK kurulum programı sizi Hyper-V Yöneticiler grubuna ekler. Aksi takdirde bu gereksinimi el ile etkinleştirmeniz gerekebilir.

 Öykünücüsünü çalıştırarak Hyper-V Yöneticiler grubunun bir üyesi değilseniz gruba katılmanız istenir (iletişim kutusu, hyper-V öykünücüsünü Windows Phone eder). Gruba katılmak için yönetici hakları gerekir.

> [!IMPORTANT]
> Gruba katıldıktan sonra, değişikliğin etkili olmak için oturumu kapatın veya yeniden başlatın.

 ![Hyper&#45;V Yöneticileri güvenlik grubuna katılma](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 Kendinizi bir gruba el ile eklemek için Yerel Kullanıcılar ve Gruplar ek bileşenini açın.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>Öykünücüyü önyüklenebilir bir VHD'den çalıştırma desteklenmiyor
 Önyüklenebilir bir VHD'den Windows android için Visual Studio Emulator üzerinde bir uygulama çalıştırmayı denersiniz, öykünücü genellikle birkaç dakika sürer veya başlatılamaz. Öykünücü başlatılamadı mı şu iletiyi alırsınız: Uygulama dağıtımı başarısız oldu. Lütfen tekrar deneyin.

 Bu yapılandırma desteklenmez. İlgili sorunlar hakkında bilgi için [bkz. Android için Visual Studio Emulator giderme.](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Hyper-V sıkıştırılmamış ve şifrelenmemiş dosyalar gerektirir
 NTFS dosya sistemiyle yapılandırılmış bir sabit sürücüde, Hyper-V tarafından kullanılan sanal sabit disk dosyaları sıkıştırılmamış ve şifrelenmemiş olmalıdır. Aşağıdaki dizinlerin sıkıştırılmış veya şifrelenmiş olduğundan emin olun:

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86)\Microsoft Emulator Manager

- C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

ReFS dosya sisteminde, sanal sabit disk dosyaları bütünlük bit kümesine sahip değildir.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Donanım grafik iletme (OpenGL ES desteği) gereksinimleri

Öykünücüsünün OpenGL ES tarafından kullanılanlar gibi GPU'ya yapılan çağrılara öykünecek olması için makinenizin uygun DirectX sürücülerine sahip DirectX uyumlu bir GPU'su olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Android için Visual Studio Öykünücüsü’nde Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
