---
title: Dotfuscator Community’yi yükseltme
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive çözümleri, PreEmptive Protection, koruma, topluluk sürümü, gizleme, .NET, ücretsiz, Visual Studio 2019, Visual Studio 2017, Visual Studio, yükseltme, komut satırı
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
description: Visual Studio 'Ya dahil edilen Dotfuscator topluluğunun ücretsiz kopyasını nasıl yükselteceğinizi öğrenin.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 08492340022f772beadca8061a216de69fafc8af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596807"
---
# <a name="upgrade-dotfuscator-community"></a>Dotfuscator Community’yi yükseltme

Dotfuscator topluluğu, Microsoft Visual Studio kullanan tüm geliştiriciler için hemen birçok uygulama koruma ve sağlamlaştırma özelliği sunar.
Ancak, Dotfuscator sürümlerini yükseltecek kullanıcılar için daha fazla özellik mevcuttur.

## <a name="registering-dotfuscator-community"></a>Dotfuscator topluluğu kaydediliyor

Dotfuscator Community 'nin kayıtlı kullanıcıları, Dotfuscator Community 'yi otomatik derleme sürecinizde tümleştirmeyi kolaylaştıran [komut satırı desteği][cli]gibi ek özelliklere erişim sağlar. Kayıt Ayrıca, [karıştırılmış yığın izlemelerinin kodunu çözmek][decode-obfuscated]için kullanılan yerleşik bir araca erişim izni verir.

Kayıt hızlı, basit ve ücretsizdir.
Dotfuscator Community 'yi kaydettirmek için [tam Dotfuscator topluluk Kullanıcı Kılavuzu 'ndaki yönergelere][register-ce]bakın.

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Dotfuscator Community temel bir koruma düzeyi sağladığından, ***preemptive Protection-Dotfuscator Professional*** , gelişmiş gizleme dönüştürmeleri ve aşağıdakiler gibi koruma özellikleri içerir:

* *Fikri mülkiyet koruması*
  * Gelişmiş aşırı yükleme endüksiyon™ ve rastgele tanımlayıcı seçimi dahil ek yeniden adlandırma seçenekleri.
  * [Otomatik kod ayrıştırılmış derleme sırasında hedeflenen dönüşümler][control-flow]de dahil olmak üzere kurumsal düzeyde gizleme dönüştürmelerini erişim.
  * [Gizli dizeleri gizleyebilme][string-encryption]özelliği, ayrıştırılmış kodun basit bir aramasını olanaksız hale getirir.
  * [Şekilde belirtmeyecek adlandırmak sahiplik ve dağıtım dizelerini derlemelerinize ekleme][watermarking]özelliği, yetkisiz yazılım sızıntılarının kaynağını belirlemenizi sağlar.
  * [Birden çok derlemeyi tek bir halinde birleştirebilme][linking]özelliği, saldırganların kod öğelerinin rollerini belirlemede daha da zor olduğundan, kaygıların ayrılması ortadan kalkar.
  * [Kullanılmayan kodu uygulamanızdan otomatik olarak kaldırabilme][pruning], gönderilen hassas kod miktarını azaltır.
* *Uygulama bütünlüğü koruması*
  * Ek [uygulama savunma davranışları][check-actions].
  * Uygulamanın yaşam süresi sonu tarihinden önce bir uyarı dönemi sağlama özelliği.
  * Süre sonu uyarı dönemi sırasında veya son tarihten sonra uygulama kodunu bildirebilme özelliği.

Dotfuscator Professional, sektör standardı [.net gizleme][net-obfuscator] ve sürekli destek, bakım ve ürün güncelleştirmeleri gerektiren kurumsal geliştiricilere uygundur.
Ayrıca, Dotfuscator Professional, Visual Studio ile sıkı bir tümleştirme sunar ve ticari kullanım için lisanslanır.

Dotfuscator Professional 'ın Gelişmiş uygulama koruma özellikleri hakkında daha fazla bilgi için PreEmptive Solutions ' [Dotfuscator genel bakış sayfasını][product-about] ziyaret edin ve [Dotfuscator topluluğuyla karşılaştırın][product-compare].
[Tam olarak desteklenen denemeler preemptive.com adresinde bulunabilir][eval].

## <a name="see-also"></a>Ayrıca bkz.

[Tam Dotfuscator topluluk kullanıcı kılavuzunda bu makale][full]

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
