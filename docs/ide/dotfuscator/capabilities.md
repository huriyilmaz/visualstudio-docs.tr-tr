---
title: Dotfuscator Özellikleri
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: dotfuscator, dotfuscator Community, dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, koruma, topluluk sürümü, gizleme, .net, ücretsiz, Visual Studio 2017, Visual Studio 2019 Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Visual Studio eklenen Community dotfuscator 'un ücretsiz kopyasının yeteneklerini öğrenin.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: eaab9f7fbadaca22aac88ec62d0331f6dee995fa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625947"
---
# <a name="capabilities-of-dotfuscator"></a>Dotfuscator Özellikleri

bu sayfa, [yükseltmeler][upgrades]aracılığıyla kullanılabilen gelişmiş seçeneklere yönelik bazı başvurularıyla dotfuscator Community özelliklerine odaklanır.

dotfuscator Community, .net uygulamaları için bir *derleme sonrası* sistemidir.
bu arada, Visual Studio kullanıcılar [derlemeleri][obfuscation] ayırt edebilir ve [etkin savunma ölçümlerini][checks] , özgün kaynak koduna erişmesi gereken dotfuscator olmadan uygulamaya ekleyebilir.
Dotfuscator, uygulamanızı birden çok şekilde korur, katmanlı bir koruma stratejisi oluşturur.

dotfuscator Community, [Evrensel Windows Platformu (UWP)][uwp] ve [Xamarin][xamarin]dahil olmak üzere çok çeşitli .net bütünleştirilmiş kod ve uygulama türlerini destekler.

## <a name="intellectual-property-protection"></a>Fikri mülkiyet koruması

Uygulamanızın tasarımı, davranışı ve uygulaması, fikri mülkiyet (IP) formlarıdır.
Ancak, .NET için oluşturulan uygulamalar temelde açık kitaplardır; [yüksek düzeyde meta veriler ve ara kod içerdiğinden][assemblies], .NET derlemelerine tersine mühendislik uygulamak çok kolaydır.

dotfuscator Community, [yeniden adlandırma][renaming]biçiminde temel [.net gizleme][obfuscation] bilgilerini içerir.
Kodunuzu Dotfuscator ile gizleme, önemli adlandırma bilgileri artık genel olmayacak şekilde, ters mühendislik aracılığıyla kaynak koda yetkisiz erişim riskini azaltır.
Gizleme Ayrıca, kodunuzun inceinizden korunması için önemli bir adımdır; Örneğin, IP 'nizin ticari gizli anahtar olarak korunmasını sağlamak için değerli bir adımdır.

dotfuscator 'un [uygulama bütünlüğü koruma özelliklerinin](#application-integrity-protection) birçoğu, daha fazla aksatabilir ters mühendislik Community.
Örneğin, hatalı aktör program mantığını anlamak için uygulamanızın çalışan bir örneğine bir hata ayıklayıcı eklemeyi deneyebilir.
Dotfuscator, uygulamanıza [hata ayıklama davranışını][debug] sınıftakiyle öğesine ekleyebilir.

## <a name="application-integrity-protection"></a>Uygulama bütünlüğü koruması

Kaynak kodunuzu korumanın yanı sıra, uygulamanızın tasarlandığı gibi kullanıldığından emin olmak da önemlidir.
Saldırganlar, uygulama tarafından işlenen hassas verileri çalmak veya işlemek ya da uygulamanın davranışını değiştirmek için, uygulamanızı, lisans ilkelerini (yani, yazılım korsanlığı) aşmak için bir sıraya alma girişiminde bulunabilir.

dotfuscator Community, [uygulama doğrulama kodunu][checks] derlemelerinize, [korsanlığa karşı koruma][tamper], [hata ayıklama][debug]ve [köklü cihaz][root] ölçüleri dahil olmak üzere ekleyebilir.
Geçersiz bir uygulama durumu algılandığında, doğrulama kodu, [durumu uygun bir şekilde ele almak için uygulama kodundan sonra çağırabilir][check-app].
Ya da uygulamanın geçersiz kullanımlarını işlemek üzere kod yazmamayı tercih ediyorsanız, Dotfuscator, kaynak kodunuzda herhangi bir değişikliğe gerek kalmadan [Yanıt][check-action] davranışları da ekleyebilir.

Bu yöntemlerin birçoğu, değerlendirme veya deneme yazılımı için [yaşam süresi son tarihleri][shelflife] zorlamak üzere de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

[tam dotfuscator Community kullanıcı kılavuzu 'ndaki bu konu][full]

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
