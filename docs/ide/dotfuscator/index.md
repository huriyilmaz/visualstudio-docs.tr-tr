---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator topluluğu, PreEmptive, PreEmptive çözümleri, PreEmptive Protection, koruma, topluluk sürümü, gizleme, .NET, ücretsiz, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Visual Studio 'Ya dahil edilen Dotfuscator topluluğunun ücretsiz kopyasıyla .NET uygulamalarınızı nasıl koruyabileceğinizi öğrenin.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e2ee678e5cf71693d12d4ddeb6af51f55a870b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652433"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***Preemptive Protection-Dotfuscator*** , güvenli yazılım geliştirme yaşam döngüsüne kolayca uyum sağlayan kapsamlı .NET uygulama koruması sağlar.
Ticari gizli dizileri ve diğer fikri mülkiyet (IP) güvenliğini sağlamak, korsanlığın ve sahteciliği azaltmak ve izinsiz ve yetkisiz hata ayıklamaya karşı koruma sağlamak için masaüstünü, mobil, sunucu ve katıştırılmış uygulamaları güvenli hale getirmek, korumak ve ayıklamak için bu özelliği kullanın.
Dotfuscator, derlenmiş derlemelerde, ek programlamaya gerek olmadan veya kaynak koduna hatta erişim gerektirmeden çalışmaktadır.

![PreEmptive koruması-Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Korumanın önemi önemli

Fikri mülkiyet (IP) **özelliğinin korunması** önemlidir.
Uygulamanızın kodu, IP olarak kabul edilebilir tasarım ve uygulama ayrıntılarını içerir.
Ancak, .NET Framework oluşturulan uygulamalar, çok sayıda ücretsiz ve otomatikleştirilmiş araçlardan birini kullanarak, daha kolay mühendisin yanı sıra, [önemli meta veriler ve yüksek düzeyli ara kod içerir][assemblies].
Ters mühendisi durdurup durdurarak, yetkisiz IP 'nin açığa çıkmasına engel olabilir ve kodunuzun ticari gizli dizileri içerdiğini gösterir.
Dotfuscator, .NET derlemelerinizi, geriye doğru Mühendislik için, özgün uygulama davranışını koruyarak [karartabilir][obfuscation] .

**Uygulamanızın bütünlüğünü korumak**da önemlidir.
Ters mühendisliğin yanı sıra, kötü aktörler uygulamanızı önücretlendirebilirsiniz, uygulamanın davranışını çalışma zamanında değiştirebilir veya verileri işleyebilir.
Dotfuscator, izinsiz kullanım, üçüncü taraf hata ayıklama ve kökü belirtilmiş cihazlar dahil olmak üzere [yetkisiz kullanımları tespit etme ve bunlara yanıt verme][checks]özelliği ile uygulamanızı ekleyebilir.

Dotfuscator 'un güvenli bir yazılım geliştirme yaşam döngüsüne nasıl uyduğunu hakkında daha fazla bilgi için, bkz. PreEmptive Solutions ' [SDL uygulama koruma sayfası][sdl-protection].

## <a name="about-dotfuscator-community"></a>Dotfuscator topluluğu hakkında

Microsoft Visual Studio kopyanız, kişisel kullanım için ücretsiz bir ***preemptive Protection-Dotfuscator topluluğunun***bir kopyasını içerir.
(Bu ücretsiz sürüm daha önce Dotfuscator Community Edition veya Dotfuscator CE olarak biliniyordu.) Visual Studio 'da bulunan Dotfuscator Community sürümünün nasıl yükleneceğine ilişkin yönergeler için [yükleme sayfasına][install]bakın.

Dotfuscator topluluğu, geliştiriciler, mimarlar ve test ediciler için bir dizi [yazılım koruması ve sağlamlaştırma][software-protection] hizmeti sunar.
[.Net gizleme][obfuscation] ve Dotfuscator topluluğu 'nda bulunan diğer [Uygulama koruma][app-protection] özellikleri örnekleri şunlardır:

* Derlenmiş derlemelerin ters mühendislik işlemini daha zor hale getirmek için tanımlayıcıları *[yeniden adlandırma][renaming]* .
* Değiştirilen uygulamaların yürütülmesini tespit etmek ve değişiklik yapılan oturumları sonlandırmak veya yanıtlamak için müdahale *[önleme][tamper]* .
* Hata ayıklamanın çalışan bir uygulamaya eklenmesini algılamak ve hata ayıklaması yapılan oturumları sonlandırmak veya yanıt vermek için *[hata ayıklama][debug]* .
* Uygulamanın, belirtilen bir Android cihazda çalışıp çalışmadığını tespit etmek ve bu cihazlarda oturumları sonlandırmak veya yanıt vermek için, *[kök olmayan cihaz][root]* .
* "Yaşam sonu" tarihi kodlayan ve süresi dolmayan uygulama oturumlarını sonlandıran *[uygulama süre sonu davranışları][shelflife]* .

Bu özelliklerle ilgili ayrıntılar için uygulama koruma stratejinize nasıl uyum dahil, bkz. [Özellikler sayfası][capabilities].

Dotfuscator topluluğu, kullanıma hazır temel koruma sunar.
Daha fazla uygulama koruma ölçümü, Dotfuscator Community 'nin kayıtlı kullanıcıları ve dünyanın önde gelen [.net gizleme][net-obfuscator]sürümü olan ***preemptive Protection-Dotfuscator Professional***kullanıcıları için de kullanılabilir.
Dotfuscator 'u geliştirme hakkında daha fazla bilgi için [yükseltmeler sayfasına][upgrades]bakın.

## <a name="getting-started"></a>Başlarken

::: moniker range="vs-2019"

Visual Studio 'dan Dotfuscator topluluğunu kullanmaya başlamak için, **Arama kutusuna** `dotfuscator` yazın (CTRL + Q).

* Dotfuscator topluluğu zaten yüklüyse, **arama kutusu** *menü* başlığı altında Dotfuscator Community 'yi başlatma seçeneğini gösterecektir. Ayrıntılar için, [tam Dotfuscator topluluk Kullanıcı kılavuzunun Başlarken sayfasına][get-started]bakın.
* Dotfuscator topluluğu henüz yüklenmemişse, **arama kutusu** bunun yerine *tek tek bileşenler* başlığı altında **Install preemptive Protection-Dotfuscator** öğesini gösterir. Ayrıntılar için [yükleme sayfasına][install] bakın.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 'dan Dotfuscator topluluğunu kullanmaya başlamak için **Hızlı Başlat** (CTRL + Q) arama çubuğuna `dotfuscator` yazın.

* Dotfuscator topluluğu zaten yüklüyse **Hızlı Başlat** , Dotfuscator topluluk Kullanıcı arabirimini başlatmak için *menü* seçeneğini getirir. Ayrıntılar için, [tam Dotfuscator topluluk Kullanıcı kılavuzunun Başlarken sayfasına][get-started]bakın.
* Dotfuscator topluluğu henüz yüklenmemişse **Hızlı başlatma** ilgili *yükleme* seçeneğini getirir. Ayrıntılar için [yükleme sayfasına][install] bakın.

::: moniker-end

Ayrıca, [preemptive.com ' deki Dotfuscator İndirmeleri sayfasından][download]Dotfuscator topluluğunun **en son sürümünü** edinebilirsiniz.

## <a name="full-documentation"></a>Tam belgeler

Bu sayfa ve alt sayfaları, Dotfuscator topluluğunun özelliklerine ilişkin üst düzey bir genel bakış ve [araç yükleme yönergeleri][install]sağlar.

[Dotfuscator topluluk Kullanıcı arabirimini kullanmaya başlama][get-started]dahil olmak üzere ayrıntılı kullanım yönergeleri için [preemptive.com adresindeki tam Dotfuscator topluluk Kullanıcı kılavuzuna][full] bakın.

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
