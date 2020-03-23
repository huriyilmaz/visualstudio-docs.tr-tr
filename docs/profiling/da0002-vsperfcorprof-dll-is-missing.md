---
title: 'DA0002: VSPerfCorProf.dll eksik | Microsoft Dokümanlar'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777757"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll eksik

|||
|-|-|
|Kural Id|DA0002|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemleri|VSPerfCmd ve VSPerfASPNETCmd komut satırı araçlarını kullanarak profil oluşturma|
|İleti|Bu dosya düzgün *VSPerfCLREnv.cmd*ile ortam değişkenleri ayarı olmadan toplanmış görünüyor. Yönetilen ikililer için semboller çözülmeyebilir.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında profil oluşturucu *VSPerfCorProf.dll* bulamadı. Bu uyarı, gerekli ortam değişkenlerini ortaya çıkarmak için *VSPerfCLREnv.cmd* aracını kullanmadan profil oluşturucu verilerinin toplanması için komut satırı araçları kullanıldığında oluşur. Profil Oluşturma Araçları başlatıldığında başka bir profil oluşturucu çalışıyorsa uyarı da ateşlenebilir.

## <a name="rule-description"></a>Kural açıklaması
 Profil oluşturucunun .NET Framework ikililerinde sembolleri çözmesi için profil oluşturma çalışmasından önce belirli ortam değişkenleri ayarlanmalıdır. Bu *uyarı, VSPerfCLREnv.cmd* aracının profil oluşturma verileri toplanmadan önce çalıştırılmadığını göstermektedir. Yönetilen ikililer için semboller çözülmeyebilir. Komut satırından Profil Oluşturma Araçlarını kullanma hakkında daha fazla bilgi için [komut satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Profil Oluşturma Araçları'ndaki [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komut satırı araçlarını kullanarak yönetilen uygulamaların profilini çıkarırken, veri toplamaya başlamadan önce [VSPerfCLREnv](../profiling/vsperfclrenv.md) komut satırı aracını çalıştırın.
