---
title: Profil oluşturma komut satırı araçlarının yolunu belirtme
description: Profil Oluşturma Araçları komut satırı araçlarının yolu PATH ortam değişkenine eklenmediyse profil oluşturma araçları komut satırı araçlarının yolunu belirtin.
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
ms.openlocfilehash: d96ea6d373f01210e7226e809c01c216506c86c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157260"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Profil Araçları komut satırı araçlarının yolunu belirtin

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Profil oluşturma araçları komut satırı araçlarının yolu, PATH ortam değişkenine eklenmez. 32 bit bilgisayarlarda, Araçlar tek bir dizindir. 64 bit bilgisayarlarda profil oluşturma araçlarının 32-bit ve 64 bit sürümleri vardır.

## <a name="32-bit-computers"></a>32 bit bilgisayarlar

yerel kod için Visual Studio profiler apı 'leri *VSPerf.dll*. *vsperf. h* ve içeri aktarma kitaplığı olan *vsperf. lib* üstbilgi dosyası, *Microsoft Visual Studio \2017\team tools\performance tools\perfsdk* dizininde bulunur.

 Yönetilen kod için, profil oluşturucu API 'Leri *Microsoft.VisualStudio.Profiler.dll*. bu DLL, *Microsoft Visual Studio \shared\common\vsperfcollectiontools* dizininde bulunur.

## <a name="64-bit-computers"></a>64 bit bilgisayarlar

64 bit bilgisayarlarda, profili oluşturulmuş uygulamanın hedef platformuna göre yolunu belirtin.

- 32 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:

     Yerel *Microsoft Visual Studio \2017\team tools\performance tools\perfsdk*
     
     lebilmesi *Microsoft Visual Studio \shared\common\vsperfcollectiontools*

- 64 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:

     Yerel *Microsoft Visual Studio \2017\team tools\performance tools\x64\perfsdk*

     lebilmesi *Microsoft Visual Studio \shared\common\vsperfcollectiontools\x64*
