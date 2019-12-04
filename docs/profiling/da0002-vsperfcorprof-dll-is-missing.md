---
title: 'DA0002: VSPerfCorProf. dll eksik | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f768a35e7c50ec55867ae49901718063ca39bd0b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777757"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll eksik

|||
|-|-|
|Kural Kimliği|DA0002|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemleri|VSPerfCmd ve VSPerfASPNETCmd komut satırı araçlarını kullanarak profil oluşturma|
|İleti|Dosya, *VSPerfCLREnv. cmd*ile ortam değişkenlerini düzgün şekilde ayarlamadan toplanmış gibi görünüyor. Yönetilen ikililerin sembolleri çözümlenmeyebilir.|
|Kural türü|Bilgisi|

## <a name="cause"></a>Sebep
 Profil Oluşturucu, profil oluşturma çalışması sırasında *VSPerfCorProf. dll dosyasını* bulamadı. Bu uyarı, profil oluşturucu verileri koleksiyonu için komut satırı araçları, gerekli ortam değişkenlerini başlatmak için *VSPerfCLREnv. cmd* aracı kullanılmadan kullanıldığında oluşur. Uyarı, Profil Oluşturma Araçları başlatıldığında başka bir profil oluşturucu çalışıyorsa de tetikde olur.

## <a name="rule-description"></a>Kural açıklaması
 Profil Oluşturucu için bir profil oluşturma çalıştırılmadan önce, .NET Framework ikili dosyalarında sembolleri çözümlemek üzere belirli ortam değişkenlerinin ayarlanması gerekir. Bu uyarı, profil oluşturma verileri toplanmadan önce *VSPerfCLREnv. cmd* aracının çalıştırılmadığını önerir. Yönetilen ikililerin sembolleri çözümlenmeyebilir. Komut satırından Profil Oluşturma Araçları kullanma hakkında daha fazla bilgi için, bkz [. komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları ' de komut satırı araçlarını kullanarak yönetilen uygulamalar profilini oluştururken, veri toplamaya başlamadan önce [VSPerfCLREnv](../profiling/vsperfclrenv.md) komut satırı aracını çalıştırın.
