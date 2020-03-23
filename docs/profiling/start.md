---
title: Başlangıç | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: df3ccda9730be02bafb7f7d069a26193a4528d1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778277"
---
# <a name="start"></a>Başlangıç
**Başlangıç** seçeneği, profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatan bir *VSPerfCmd.exe* seçeneğidir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametreler
 `Method`Aşağıdaki anahtar kelimelerden biri olmalıdır:

- **TRACE** - Enstrümantasyon yöntemini belirtir.

- **ÖRNEK** - Örnekleme yöntemini belirtir.

- **KAPSAM** - Kod kapsamını belirtir.

- **CONCURRENCY** - Kaynak çekişme yöntemini belirtir.

## <a name="required-options"></a>Gerekli seçenekler
 Komut satırında **Başlat** belirtildiğinde **Çıktı** seçeneği belirtilmelidir.

 **Çıktı:** `filename` Çıktı dosya adını belirtir.

## <a name="exclusive-options"></a>Özel seçenekler
 Aşağıdaki seçenekler yalnızca bir komut satırında **Başlat** seçeneği yle kullanılabilir.

 **Çapraz Oturum**&#124;**CS** çapraz işlem profiloluşturmasağlar. Çapraz **Oturum** ve **CS** seçeneği adları desteklenir.

 **Kullanıcı:**`domain\`[`username` ] İstemcinin belirtilen hesaptan monitöre erişimini sağlar.

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter** profil oluşturma veri dosyasına bir işaret olarak eklemek için bir Windows performans sayacı belirtir. **AutoMark,** veri dosyasının koleksiyonları arasındaki milisaniye aralığını belirtir.

## <a name="invalid-options"></a>Geçersiz seçenekler
 Komut satırında **Başlat** seçeneğiyle aşağıdaki seçenekler kullanılamaz.

 **Durum** **Durumu** profillenmiş bu işlemler için geçerlidir. İşlemleri ve iş parçacıklarını ve bunların geçerli profil durumunu (On/Off) listeler. Örneğin, bir işlem durdurulursa, **Durum** raporda bunu göstermez. **Durum,** işlemin profilli olup olmadığını gösterir.

 **Kapatma**[**:**`Timeout`] Profilleyiciyi kapatır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, profil oluşturucuyu başlatmak için *VSPerfCmd.exe* **Başlat** seçeneğinin nasıl kullanılacağını göstermektedir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
