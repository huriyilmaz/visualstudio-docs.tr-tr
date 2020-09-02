---
title: DA0002-VSPerfCorProf.dll eksik | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 36c9f3b33eab8428cd14aa26896c3813422d3dd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537078"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll eksik

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0002|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemleri|VSPerfCmd ve VSPerfASPNETCmd komut satırı araçlarını kullanarak profil oluşturma|
|İleti|Dosya, *VSPerfCLREnv. cmd*ile ortam değişkenlerini düzgün şekilde ayarlamadan toplanmış gibi görünüyor. Yönetilen ikililerin sembolleri çözümlenmeyebilir.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Profil Oluşturucu, profil oluşturma çalışması sırasında *VSPerfCorProf.dll* bulamadı. Bu uyarı, profil oluşturucu verileri koleksiyonu için komut satırı araçları, gerekli ortam değişkenlerini başlatmak için *VSPerfCLREnv. cmd* aracı kullanılmadan kullanıldığında oluşur. Uyarı, Profil Oluşturma Araçları başlatıldığında başka bir profil oluşturucu çalışıyorsa de tetikde olur.

## <a name="rule-description"></a>Kural açıklaması
 Profil Oluşturucu için bir profil oluşturma çalıştırılmadan önce, .NET Framework ikili dosyalarında sembolleri çözümlemek üzere belirli ortam değişkenlerinin ayarlanması gerekir. Bu uyarı, profil oluşturma verileri toplanmadan önce *VSPerfCLREnv. cmd* aracının çalıştırılmadığını önerir. Yönetilen ikililerin sembolleri çözümlenmeyebilir. Komut satırından Profil Oluşturma Araçları kullanma hakkında daha fazla bilgi için, bkz [. komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Profil Oluşturma Araçları içinde komut satırı araçlarını kullanarak yönetilen uygulamalar profilini oluştururken [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , veri toplamaya başlamadan önce [VSPerfCLREnv](../profiling/vsperfclrenv.md) komut satırı aracını çalıştırın.
