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
description: Visual Studio'da yer alan Dotfuscator Community'nin ücretsiz kopyasının özelliklerini öğrenin.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 019acd338ab49dd08255e3dc5d174cf2e371b71e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918413"
---
# <a name="capabilities-of-dotfuscator"></a>Dotfuscator Özellikleri

Bu sayfa, yükseltmeler aracılığıyla mevcut gelişmiş seçeneklere bazı [referanslar][upgrades]ile Dotfuscator Topluluk yetenekleri üzerinde duruluyor.

Dotfuscator Community ,NET uygulamaları için *bir post-build* sistemidir.
Bununla, Visual Studio kullanıcıları [derlemeleri gizlemek][obfuscation] ve uygulamaya [aktif savunma önlemleri][checks] enjekte edebiliyoruz - tüm Dotfuscator orijinal kaynak koduna erişmek için gerek olmadan.
Dotfuscator, katmanlı bir koruma stratejisi oluşturarak uygulamanızı birden çok şekilde korur.

Dotfuscator Community, [Evrensel Windows Platformu (UWP)][uwp] ve [Xamarin][xamarin]dahil olmak üzere çok çeşitli .NET derlemesini ve uygulama türlerini destekler.

## <a name="intellectual-property-protection"></a>Fikri Mülkiyet Koruması

Uygulamanızın tasarımı, davranışı ve uygulaması fikri mülkiyet (IP) biçimleridir.
Ancak,.NET için oluşturulan uygulamalar temelde açık kitaplardır; üst düzey meta veriler ve ara [kod içerdikleri][assemblies]için .NET derlemelerini tersine çevirmek kolaydır.

Dotfuscator Topluluk [yeniden adlandırma][renaming]şeklinde temel [.NET gizleme][obfuscation] içerir.
Kodunuzu Dotfuscator ile gizlemek, önemli adlandırma bilgilerinin artık herkese açık olmayacağından, ters mühendislik yoluyla kaynak koduna yetkisiz erişim riskini azaltır.
Gizleme, kodunuzu incelemeden korumak için sizin için de çaba gösterir - IP'nizin yasal olarak ticari sır olarak korunduğunu belirlemede değerli bir adımdır.

Dotfuscator Community'nin [uygulama bütünlüğü koruma özelliklerinin](#application-integrity-protection) çoğu ters mühendisliği daha da engellemez.
Örneğin, kötü bir aktör, program mantığını anlamak için uygulamanızın çalışan bir örneğine hata ayıklama eklemeyi deneyebilir.
Dotfuscator bunu engellemek için uygulamanıza [hata ayıklama önleme davranışı][debug] enjekte edebilir.

## <a name="application-integrity-protection"></a>Uygulama Bütünlüğü Koruması

Kaynak kodunuzu korumanın yanı sıra, uygulamanızın tasarlanmış şekilde kullanıldığından da emin olmak önemlidir.
Saldırganlar, lisans lama ilkelerini (diğer bir deyişle yazılım korsanlığı) atlatmak, uygulama tarafından işlenen hassas verileri çalmak veya işlemek veya uygulamanın davranışını değiştirmek için uygulamanızı ele geçirmeye çalışabilir.

Dotfuscator [Topluluk, anti-kurcalan,][tamper] [hata ayıklama ve][debug] [anti-köklü cihaz][root] önlemleri de dahil olmak üzere derlemelerinize uygulama doğrulama [kodu][checks] enjekte edebilir.
Geçersiz bir uygulama durumu algılandığında, doğrulama kodu [durumu uygun bir şekilde ele almak için uygulama kodunu arayabilir.][check-app]
Veya, uygulamanın geçersiz kullanımlarını işlemek için kod yazmayı tercih ederseniz, Dotfuscator kaynak kodunuzda herhangi bir değişiklik gerektirmeden [yanıt][check-action] davranışları da enjekte edebilir.

Bu aynı yöntemlerin çoğu, değerlendirme veya deneme yazılımı için [yaşam sonu tarihlerini][shelflife] uygulamak için de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

[Tam Dotfuscator Topluluk Kullanım Kılavuzu bu konu][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
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
