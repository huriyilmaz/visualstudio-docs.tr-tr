---
title: Profil oluşturma komut satırı araçlarının yolunu belirtme
description: Profil Oluşturma Araçları komut satırı araçlarının yolu PATH ortam değişkenine eklenmediyse profil oluşturma araçları komut satırı araçlarının yolunu belirtin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa1cb81d46f0977de2db9d78c6db53f542faa70f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720040"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Profil Araçları komut satırı araçlarının yolunu belirtin

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Profil oluşturma araçları komut satırı araçlarının yolu, PATH ortam değişkenine eklenmez. 32 bit bilgisayarlarda, Araçlar tek bir dizindir. 64 bit bilgisayarlarda profil oluşturma araçlarının 32-bit ve 64 bit sürümleri vardır.

## <a name="32-bit-computers"></a>32 bit bilgisayarlar

Yerel kod için, Visual Studio Profiler API 'Leri *VSPerf.dll*. *VSPerf. h* ve içeri aktarma kitaplığı olan *VSPerf. lib* üstbilgi dosyası *Microsoft Visual Studio\2017\team Tools\Performance Tools\PerfSDK* dizininde bulunur.

 Yönetilen kod için, profil oluşturucu API 'Leri *Microsoft.VisualStudio.Profiler.dll*. Bu DLL *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* dizininde bulunur.

## <a name="64-bit-computers"></a>64 bit bilgisayarlar

64 bit bilgisayarlarda, profili oluşturulmuş uygulamanın hedef platformuna göre yolunu belirtin.

- 32 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:

     Yerel *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
     lebilmesi *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- 64 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:

     Yerel *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     lebilmesi *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
