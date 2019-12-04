---
title: Komut satırı araçlarının Profil Oluşturma Araçları yolunu belirtme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 087407f511c038a369694beca8a9fe4ecc2ff7b7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771597"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Profil Araçları komut satırı araçlarının yolunu belirtin

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçlarının yolu, PATH ortam değişkenine eklenmez. 32 bit bilgisayarlarda, Araçlar tek bir dizindir. 64 bit bilgisayarlarda profil oluşturma araçlarının 32-bit ve 64 bit sürümleri vardır.

## <a name="32-bit-computers"></a>32 bit bilgisayarlar

::: moniker range="vs-2017"
 Yerel kod için, Visual Studio Profiler API 'Leri *VSPerf. dll*' dir. *VSPerf. h*ve içeri aktarma kitaplığı olan *VSPerf. lib*üstbilgi dosyası *Microsoft Visual Studio\2017\team Tools\Performance Tools\PerfSDK* dizininde bulunur.
::: moniker-end

 Yönetilen kod için profil oluşturucu API 'Leri *Microsoft. VisualStudio. Profiler. dll*' dir. Bu DLL *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* dizininde bulunur.

## <a name="64-bit-computers"></a>64 bit bilgisayarlar

64 bit bilgisayarlarda, profili oluşturulmuş uygulamanın hedef platformuna göre yolunu belirtin.

::: moniker range="vs-2017"
- 32 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:

     Yerel *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* (yönetilen) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- 64 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:

     Yerel *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK* (yönetilen) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
::: moniker-end
