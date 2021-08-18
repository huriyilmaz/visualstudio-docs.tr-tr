---
title: DA0002 - VSPerfCorProf.dll eksik | Microsoft Docs
description: Profil oluşturma verileri koleksiyonu için komut satırı araçları, gerekli ortam değişkenlerini başlatmak için VSPerfCLREnv.cmd aracı kullanılmadan kullanılırsa veya profil oluşturma başlatılırken başka bir profil Profil Oluşturma Araçları oluşur.
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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d6aabbae9b0e65933e9340a09a20d66fba4da98f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084382"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll eksik

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0002|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemleri|VSPerfCmd ve VSPerfASPNETCmd komut satırı araçlarını kullanarak profil oluşturma|
|İleti|*VsPerfCLREnv.cmd* ile ortam değişkenlerini düzgün ayarlamadan dosyanın toplanmış olduğu görünüyor. Yönetilen ikili dosyalar için semboller çözümlenebilmiyor olabilir.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Profil oluşturma çalıştırması *VSPerfCorProf.dll* profil oluşturma profili bulamadı. Profil oluşturma verileri koleksiyonu için komut satırı araçları, gerekli ortam değişkenlerini başlatmak için *VSPerfCLREnv.cmd* aracı kullanılmadan kullanılırsa bu uyarı oluşur. Uyarı, başka bir profil oluşturma profili oluşturma başlatıcısı çalıştırılıyorsa Profil Oluşturma Araçları olabilir.

## <a name="rule-description"></a>Kural açıklaması
 Belirli ortam değişkenleri, profil oluşturma çalışmadan önce, profil oluşturma ikilileri içinde sembolleri çözümlemek .NET Framework gerekir. Bu uyarı, profil oluşturma *verileri toplanmadan önce VSPerfCLREnv.cmd* aracının çalıştırılamay olmadığını önerir. Yönetilen ikili dosyalar için semboller çözümlenebilmiyor olabilir. Komut satırına ilişkin Profil Oluşturma Araçları daha fazla bilgi için [bkz. Komut satırı profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Profil Oluşturma Araçları'daki komut satırı araçlarını kullanarak yönetilen uygulamaların profilini larken, veri toplamaya başlamadan önce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [VSPerfCLREnv](../profiling/vsperfclrenv.md) komut satırı aracını çalıştırın.
