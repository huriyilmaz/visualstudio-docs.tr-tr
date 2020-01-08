---
title: Dotfuscator Özellikleri
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive çözümleri, PreEmptive Protection, koruma, topluluk sürümü, gizleme, .NET, ücretsiz, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Visual Studio 'Ya dahil edilen Dotfuscator topluluğunun ücretsiz kopyasının yeteneklerini öğrenin.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a36aa17207affa257cdbb2caec0f2d6d9392285b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590013"
---
# <a name="capabilities-of-dotfuscator"></a>Dotfuscator Özellikleri

Bu sayfa, [yükseltmeler][upgrades]aracılığıyla kullanılabilen gelişmiş seçeneklere yönelik bazı başvurularla Dotfuscator topluluğunun özelliklerine odaklanır.

Dotfuscator topluluğu, .NET uygulamaları için bir *Derleme sonrası* sistemidir.
Bununla birlikte, Visual Studio kullanıcıları [derlemeleri][obfuscation] ayırt edebilir ve [etkin savunma ölçümlerini][checks] , özgün kaynak koduna erişmesi gereken Dotfuscator olmadan uygulamaya ekleyebilir.
Dotfuscator, uygulamanızı birden çok şekilde korur, katmanlı bir koruma stratejisi oluşturur.

Dotfuscator topluluğu, [Evrensel Windows platformu (UWP)][uwp] ve [Xamarin][xamarin]dahil olmak üzere çok sayıda .NET derlemesini ve uygulama türünü destekler.

## <a name="intellectual-property-protection"></a>Fikri mülkiyet koruması

Uygulamanızın tasarımı, davranışı ve uygulaması, fikri mülkiyet (IP) formlarıdır.
Ancak, .NET için oluşturulan uygulamalar temelde açık kitaplardır; [yüksek düzeyde meta veriler ve ara kod içerdiğinden][assemblies], .NET derlemelerine tersine mühendislik uygulamak çok kolaydır.

Dotfuscator topluluğu, [yeniden adlandırma][renaming]biçiminde temel [.net gizleme][obfuscation] özelliklerini içerir.
Kodunuzu Dotfuscator ile gizleme, önemli adlandırma bilgileri artık genel olmayacak şekilde, ters mühendislik aracılığıyla kaynak koda yetkisiz erişim riskini azaltır.
Gizleme Ayrıca, kodunuzun inceinizden korunması için önemli bir adımdır; Örneğin, IP 'nizin ticari gizli anahtar olarak korunmasını sağlamak için değerli bir adımdır.

Dotfuscator Community 'nin [uygulama bütünlüğü koruma özelliklerinin](#application-integrity-protection) birçoğu, geriye doğru mühendislik.
Örneğin, hatalı aktör program mantığını anlamak için uygulamanızın çalışan bir örneğine bir hata ayıklayıcı eklemeyi deneyebilir.
Dotfuscator, uygulamanıza [hata ayıklama davranışını][debug] sınıftakiyle öğesine ekleyebilir.

## <a name="application-integrity-protection"></a>Uygulama bütünlüğü koruması

Kaynak kodunuzu korumanın yanı sıra, uygulamanızın tasarlandığı gibi kullanıldığından emin olmak da önemlidir.
Saldırganlar, uygulama tarafından işlenen hassas verileri çalmak veya işlemek ya da uygulamanın davranışını değiştirmek için, uygulamanızı, lisans ilkelerini (yani, yazılım korsanlığı) aşmak için bir sıraya alma girişiminde bulunabilir.

Dotfuscator topluluğu, [uygulama doğrulama kodunu][checks] derlemelerinize, [korsanlığa karşı koruma][tamper], [hata ayıklama][debug]ve [köklü cihaz][root] ölçüleri dahil olmak üzere ekleyebilir.
Geçersiz bir uygulama durumu algılandığında, doğrulama kodu, [durumu uygun bir şekilde ele almak için uygulama kodundan sonra çağırabilir][check-app].
Ya da uygulamanın geçersiz kullanımlarını işlemek üzere kod yazmamayı tercih ediyorsanız, Dotfuscator, kaynak kodunuzda herhangi bir değişikliğe gerek kalmadan [Yanıt][check-action] davranışları da ekleyebilir.

Bu yöntemlerin birçoğu, değerlendirme veya deneme yazılımı için [yaşam süresi son tarihleri][shelflife] zorlamak üzere de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

[Tam Dotfuscator topluluk Kullanıcı Kılavuzu 'ndaki bu konu][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
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
