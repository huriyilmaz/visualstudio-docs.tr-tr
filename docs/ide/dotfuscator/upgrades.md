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
description: Visual Studio'da yer alan Dotfuscator Community'nin ücretsiz kopyasını nasıl yükselteceklerini öğrenin.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 08492340022f772beadca8061a216de69fafc8af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596807"
---
# <a name="upgrade-dotfuscator-community"></a>Dotfuscator Community’yi yükseltme

Dotfuscator Community, Microsoft Visual Studio'yu kullanan tüm geliştiricilere hemen birçok uygulama koruması ve sertleştirme özelliği sunar.
Ancak, Dotfuscator kendi sürümünü yükseltmek kullanıcılar için daha fazla özellik vardır.

## <a name="registering-dotfuscator-community"></a>Dotfuscator Topluluğunu Kaydetme

Dotfuscator Community'nin kayıtlı kullanıcıları, Dotfuscator Community'yi otomatik yapı işleminize entegre etmeyi kolaylaştıran [komut satırı desteği][cli]gibi ek özelliklere erişebilir. Kayıt [ayrıca, obfuscated yığın izlerini çözmek][decode-obfuscated]için kullanılan yerleşik bir araca erişim izni verir.

Kayıt hızlı, basit ve ücretsizdir.
Dotfuscator Topluluğu'nu kaydetmek [için, tam Dotfuscator Topluluk Kullanım Kılavuzu'ndaki talimatlara][register-ce]bakın.

## <a name="dotfuscator-professional"></a>Dotfuscator Profesyonel

Dotfuscator Topluluk koruma temel bir düzeyde sağlarken, ***PreEmptive Koruma - Dotfuscator Professional*** gibi gelişmiş gizleme dönüşümleri ve koruma yetenekleri içerir:

* *Fikri Mülkiyet Koruması*
  * Gelişmiş Aşırı Yük Tümeksiyonu™ ve randomize tanımlayıcı seçimi dahil olmak üzere ek yeniden adlandırma seçenekleri.
  * [Otomatik kod decompilation yenerek hedeflenen dönüşümler][control-flow]de dahil olmak üzere kurumsal düzeyde gizleme dönüşümleri erişim.
  * [Hassas dizeleri gizlemek][string-encryption]için yeteneği, derlenmiş kod basit bir arama imkansız hale.
  * Yetkisiz yazılım sızıntılarının kaynağını belirlemenize olanak [tanıyan, sahiplik ve dağıtım dizelerini derlemelerinize gizlice gömme][watermarking]olanağı.
  * [Birden çok derlemeyi tek bir araya getirebilme][linking]yeteneği, endişelerin ayrılması ortadan kaldırıldığıiçin saldırganların kod öğelerinin rollerini belirlemesini daha da zorlaştırır.
  * [Kullanılmayan kodu uygulamanızdan otomatik olarak kaldırarak][pruning]sevk edilen hassas kod miktarını azaltabilme özelliği.
* *Uygulama Bütünlüğü Koruması*
  * Ek [uygulama savunma davranışları][check-actions].
  * Bir uygulamanın kullanım ömrü sona erme tarihinden önce bir uyarı süresi sağlama yeteneği.
  * Kullanım ömrü sonu uyarı döneminde veya son başvuru tarihinden sonra başvuru kodunu bildirme yeteneği.

Dotfuscator Professional endüstri standardı [.NET Obfuscator'dur][net-obfuscator] ve sürekli destek, bakım ve ürün güncellemeleri gerektiren kurumsal geliştiriciler için uygundur.
Ayrıca, Dotfuscator Professional Visual Studio ile daha sıkı entegrasyon sunar ve ticari kullanım için lisanslanır.

Dotfuscator Professional'ın gelişmiş uygulama koruma özellikleri hakkında daha fazla bilgi için PreEmptive Solutions'ın [Dotfuscator Overview sayfasını][product-about] ziyaret edin ve [Dotfuscator Community ile karşılaştırın.][product-compare]
[Tam destekli denemeler preemptive.com mevcuttur.][eval]

## <a name="see-also"></a>Ayrıca bkz.

[Tam Dotfuscator Topluluk Kullanım Kılavuzu Bu makale][full]

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
