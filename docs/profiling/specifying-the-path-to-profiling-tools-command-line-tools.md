---
title: Profil Oluşturma Araçları Komut Satırı Araçları Yolunu Belirtme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f66ed17aec8c6e5303ea61741021dd25032fcb37
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75406311"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Profil oluşturma araçları komut satırı araçlarına giden yolu belirtin

Profil Oluşturma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Araçları komut satırı araçlarının yolu PATH ortamı değişkenine eklenmez. 32 bit bilgisayarlarda araçlar tek bir dizindedir. 64 bit bilgisayarlarda profil oluşturma araçlarının 32 bit ve 64 bit sürümleri vardır.

## <a name="32-bit-computers"></a>32 bit bilgisayarlar

Yerel kod için Visual Studio profil oluşturucu API'leri *VSPerf.dll'dedir.* Başlık dosyası, *VSPerf.h*ve alma kitaplığı *VSPerf.lib,* Microsoft *Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* dizininde bulunur.

 Yönetilen kod için profil oluşturucu API'ler *Microsoft.VisualStudio.Profiler.dll'dedir.* Bu *DLL, Microsoft Visual Studio\Shared\SHARED\VSPerfCollectionTools* dizininde bulunur.

## <a name="64-bit-computers"></a>64 bit bilgisayarlar

64 bit bilgisayarlarda, profili saptanan uygulamanın hedef platformuna göre yolu belirtin.

- 32 bit uygulamalar için varsayılan profil oluşturma araçları dizini:

     (yerli) *Microsoft Visual Studio\2017\Takım Araçları\Performans Araçları\PerfSDK*
     
     (yönetilen) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- 64 bit uygulamalar için varsayılan profil oluşturma araçları dizini:

     (yerli) *Microsoft Visual Studio\2017\Takım Araçları\Performans Araçları\x64\PerfSDK*

     (yönetilen) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
