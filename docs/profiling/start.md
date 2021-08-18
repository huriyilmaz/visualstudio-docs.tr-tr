---
title: Başlangıç | Microsoft Docs
description: Başlat seçeneğinin, profil VSPerfCmd.exe profil oluşturma yöntemine başlatan bir profil oluşturma seçeneği olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1468b4e7931a0a4d6f39593c28f42563cacce7952a7ab853a362fb4240e11083
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441715"
---
# <a name="start"></a>Başlangıç
Başlat **seçeneği,** *VSPerfCmd.exe* profil oluşturma yöntemine başlatan bir profil oluşturma seçeneğidir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametreler
 `Method` Aşağıdaki anahtar sözcüklerden biri olması gerekir:

- **TRACE** - İzleme yöntemini belirtir.

- **SAMPLE** - Örnekleme yöntemini belirtir.

- **KAPSAM** - Kod kapsamı belirtir.

- **CONCURRENCY** - Kaynak musiki yöntemini belirtir.

## <a name="required-options"></a>Gerekli seçenekler
 Komut **satırda** Başlat **belirtilirken** Çıkış seçeneği belirtilmelidir.

 **Çıktı:** `filename` Çıktı dosyasının adını belirtir.

## <a name="exclusive-options"></a>Özel seçenekler
 Aşağıdaki seçenekler yalnızca bir komut satırı **üzerinde Başlat** seçeneğiyle kullanılabilir.

 **Çapraz Geçiş&#124;** **CS,** çapraz işlem profili oluşturmayı sağlar. **CrossSession ve** CS seçenek **adlarının** her ikisi de de kullanılabilir.

 **Kullanıcı:**[ `domain\` ] `username` Belirtilen hesaptan izleyiciye istemci erişimini sağlar.

 **WinCounter:** `Path` [**Otomatik İşareti**: `n` ] **WinCounter,** profil Windows dosyasına işaret olarak eklenecek bir performans sayacı belirtir. **AutoMark,** veri dosyasının koleksiyonları arasındaki aralığı milisaniye cinsinden belirtir.

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler bir komut satırı **üzerinde Başlat** seçeneğiyle kullanılamaz.

 **Durum** **Durumu,** profili yapılan işlemler için geçerlidir. İşlemleri ve iş parçacıklarını ve bunların geçerli profil durumunu (Açık/Kapalı) listeler. Örneğin, bir işlem durdurulursa, **Durum** raporda bunu gösterir. **Durum,** sürecin profilinin profilinin olduğunu veya profilin olmadığını gösterir.

 **Kapatma**[**:** `Timeout` ] Profil oluşturma devre dışıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, profilleyiciyi başlatmak için *VSPerfCmd.exe* **Başlat** seçeneğinin nasıl kullanılamadı 1.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
