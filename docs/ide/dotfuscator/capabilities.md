---
title: Dotfuscator Özellikleri
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Ücretsiz Dotfuscator kopyasının özelliklerini ve Community özelliklerini Visual Studio.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 484c05c988351d729be1e4d37763b62e99794ed5
ms.sourcegitcommit: 485f0f6f578568ee31b2ac093e32a6d01dc9c1c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130015997"
---
# <a name="capabilities-of-dotfuscator"></a>Dotfuscator Özellikleri

Bu sayfa, yükseltmeler aracılığıyla kullanılabilen gelişmiş seçeneklere Community dotfuscator'ın özelliklerine [odaklanır.][upgrades]

Dotfuscator Community . NET *uygulamaları için derleme* sonrası bir sistemdir.
Bu Visual Studio tüm kullanıcılar derlemeleri [][obfuscation] karartabilir ve uygulamaya [][checks] etkin savunma önlemlerini eklemeye devam eder. Bunların hepsi Dotfuscator'ın özgün kaynak koduna erişmesi gerekmedendir.
Dotfuscator, katmanlı koruma stratejisi oluşturarak uygulamanızı birden çok şekilde korur.

Dotfuscator Community, Evrensel Windows Platformu (UWP) ve [Xamarin][xamarin]dahil olmak üzere çok çeşitli .NET derleme ve uygulama türlerini destekler.

## <a name="intellectual-property-protection"></a>Fikri Mülkiyet Koruması

Uygulamanın tasarımı, davranışı ve uygulaması fikri mülkiyet (IP) biçimleridir.
Ancak.NET için oluşturulan uygulamalar temelde açık kitaplardır; Üst düzey meta veriler ve ara kod içerdiği için .NET derlemelerinin [tersine mühendisliği kolaydır.][assemblies]

Dotfuscator Community, yeniden anma şeklinde [temel .NET][obfuscation] [karartma içerir.][renaming]
Kodunuzu Dotfuscator ile karartarak, önemli adlandırma bilgileri artık genel kullanıma açık olmayacaktır.
Karartma, kodunuzu incelemeye karşı korumak için çaba gösterir. IP'nizin yasal olarak ticari bir gizli dizi olarak korunmaktadır.

Dotfuscator'ın [uygulama bütünlüğü koruma](#application-integrity-protection) özelliklerinin çoğu Community tersine mühendisliği daha da engellemektedir.
Örneğin kötü bir aktör, program mantığını anlamak için çalışan bir uygulama örneğine hata ayıklayıcı eklemeye çalışıyor olabilir.
Dotfuscator, bunu [engellemek için uygulamanıza][debug] hata ayıklamaya karşı koruma davranışı da eklemenizi sağlar.

## <a name="application-integrity-protection"></a>Uygulama Bütünlüğü Koruması

Kaynak kodunuzu korumaya ek olarak, uygulamanın tasarlanma şekilde kullanıldıklerinden emin olmak da önemlidir.
Saldırganlar lisanslama ilkelerini (yazılım korsanlığı), uygulama tarafından işilen hassas verileri çalma veya işleme ya da uygulamanın davranışını değiştirmek için uygulamanızı ele geçirebilir.

Dotfuscator Community derlemelerinize [][checks] kurcalama [önleme,][tamper]hata ayıklamaya karşı koruma [ve][debug]köke bağlı olmayan cihaz ölçüleri dahil olmak üzere uygulama doğrulama [kodu][root] eklemenizi sağlar.
Geçersiz bir uygulama durumu algılandığında doğrulama kodu, durumu uygun bir şekilde ele için [uygulama koduna çağırabilir.][check-app]
Veya uygulamanın geçersiz kullanımlarını işlemek için kod yazmamayı tercih ederseniz, [][check-action] Dotfuscator kaynak kodunda herhangi bir değişiklik yapmadan yanıt davranışları da abilir.

Bu yöntemlerin çoğu, değerlendirme veya deneme yazılımı [için][shelflife] yaşam sonu son tarihlerini uygulamak için de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

[Dotfuscator kullanıcı kılavuzunda bu Community kılavuzu][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
