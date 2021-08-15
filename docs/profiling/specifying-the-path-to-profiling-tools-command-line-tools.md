---
title: Komut satırı araçlarının profilini oluşturma yolunu belirtme
description: Profil oluşturma araçları komut satırı araçlarının yolunu, Profil Oluşturma Araçları araçları PATH ortam değişkenine eklenmezken belirtin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6efcaa0fc731cc9c2399fb652dc453b1161326d59acb9f0a3de08091e8855a75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315635"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Profil oluşturma araçları komut satırı araçlarının yolunu belirtme

Komut [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları araçlarının yolu PATH ortam değişkenine eklenmez. 32 bit bilgisayarlarda, araçlar tek bir dizindedir. 64 bit bilgisayarlarda profil oluşturma araçlarının 32 bit ve 64 bit sürümleri vardır.

## <a name="32-bit-computers"></a>32 bit bilgisayarlar

Yerel kod için, Visual Studio profil oluşturma API'leri *VSPerf.dll.* *VSPerf.h* üst bilgi dosyası ve içeri aktarma kitaplığı *VSPerf.lib,* *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK dizininde* bulunur.

 Yönetilen kod için profil oluşturma API'leri *Microsoft.VisualStudio.Profiler.dll.* Bu DLL, *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools dizininde* bulunur.

## <a name="64-bit-computers"></a>64 bit bilgisayarlar

64 bit bilgisayarlarda, profili yapılan uygulamanın hedef platformuna göre yolu belirtin.

- 32 bit uygulamalar için varsayılan profil oluşturma araçları dizini şu şekildedir:

     (yerel) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
     (yönetilen) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- 64 bit uygulamalar için varsayılan profil oluşturma araçları dizini şu şekildedir:

     (yerel) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     (yönetilen) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
