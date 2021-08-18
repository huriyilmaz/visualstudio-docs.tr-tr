---
title: Dotfuscator Community’yi yükseltme
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2019, Visual Studio 2017, Visual Studio, upgrade, komut satırı
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Yeni sürüme dahil edilen Dotfuscator Community ücretsiz kopyasını Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 2ac56a2b4a7f50412ba377eb090d2c168db11f7a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086228"
---
# <a name="upgrade-dotfuscator-community"></a>Dotfuscator Community’yi yükseltme

Dotfuscator Community, uygulama koruma ve sağlamlaştırma özelliklerini hemen kullanarak tüm geliştiricilere Microsoft Visual Studio.
Ancak Dotfuscator sürümünü yükselten kullanıcılara daha fazla özellik sunulmaktadır.

## <a name="registering-dotfuscator-community"></a>Dotfuscator Community

Dotfuscator'Community kayıtlı kullanıcıları komut satırı desteği gibi [][cli]ek özelliklere erişim elde etmek için Dotfuscator Community'i otomatik derleme sürecinize kolayca tümleştirebilirsiniz. Kayıt, karartılmış yığın izlemeleri kodunun kodunu çözmede kullanılan yerleşik [bir araç için erişim de sağlar.][decode-obfuscated]

Kayıt hızlı, basit ve ücretsizdir.
Dotfuscator'Community kaydetmek için tüm [Dotfuscator kullanıcı kılavuzunda yer Community bakın.][register-ce]

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Dotfuscator Community temel bir koruma düzeyi ***sağlarken, PreEmptive Protection - Dotfuscator Professional*** gelişmiş karartma dönüşümleri ve koruma özellikleri içerir:

* *Fikri Mülkiyet Koruması*
  * Gelişmiş Aşırı Yükleme EnDüdülesi ve rastgele ™ gibi ek yeniden adlama seçenekleri.
  * Otomatik kod kod koda dönüştürmeyi hedef alan dönüştürmeler de dahil olmak üzere kurumsal düzeyde [karartma dönüşümlerine erişim.][control-flow]
  * Hassas [dizeleri karartabilme özelliği,][string-encryption]kodda basit bir arama yapmak olanaksız hale gelir.
  * Yetkisiz yazılım [sızıntılarının kaynağını belirlemenize olanak sağlayan,][watermarking]sahipliği ve dağıtım dizelerini derlemelerinize gizli bir şekilde ekleme özelliği.
  * Birden çok [derlemeyi tek][linking]bir derlemede birleştirebilme özelliği, endişelerin ayrımı ortadan kaldırılmış olduğu için saldırganların kod öğelerinin rollerini belirlemesini daha da zorlaştırabilir.
  * Uygulamanıza [kullanılmayan kodu otomatik olarak kaldırma özelliği,][pruning]gönderilen hassas kod miktarını azaltıyor.
* *Uygulama Bütünlüğü Koruması*
  * Ek [uygulama savunması davranışları.][check-actions]
  * Bir uygulamanın yaşam süresi dolmadan önce uyarı süresi sağlayabilme özelliği.
  * Yaşam süresi sonu uyarı süresi içinde veya son tarih sonrasında uygulama kodunu bildirme özelliği.

Dotfuscator Professional endüstri standardı [olan .NET Obfuscator'dır][net-obfuscator] ve sürekli destek, bakım ve ürün güncelleştirmeleri gerektiren kurumsal geliştiriciler için uygundur.
Ayrıca Dotfuscator Professional, Visual Studio daha sıkı tümleştirme sunar ve ticari kullanım için lisanslıdır.

Dotfuscator Professional'nin gelişmiş uygulama koruma özellikleri hakkında daha fazla bilgi için PreEmptive [Solutions'ın Dotfuscator][product-about] Genel Bakış sayfasını ziyaret edin ve [dotfuscator Community.][product-compare]
[Tam olarak desteklenen denemeler için preemptive.com.][eval]

## <a name="see-also"></a>Ayrıca bkz.

[Dotfuscator kullanıcı kılavuzunda yer Community makale][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html
