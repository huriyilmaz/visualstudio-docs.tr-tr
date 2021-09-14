---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: overview
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, koruma, topluluk sürümü, kod karartma, .NET, ücretsiz, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Visual Studio’ya dahil edilen ücretsiz Dotfuscator Community kopyasıyla .NET uygulamalarınızı korumayı öğrenin.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 6f3a23e13d37b3c71a8ab5b7f680e16d51ca3164
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625941"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***PreEmptive Protection - Dotfuscator***, güvenli yazılım geliştirme yaşam döngünüze kolayca uyum sağlayan kapsamlı .NET uygulama koruması sağlar.
Ticari sırları ve diğer fikri mülkiyeti (IP) güvenli hale getirmek, korsanlığı ve sahteciliği azaltmak, kurcalama ve yetkisiz hata ayıklama işlemlerine karşı korunmak amacıyla masaüstü, mobil, sunucu uygulamalarını ve gömülü uygulamaları güçlendirmek, korumak ve ayıklamak için bunu kullanın.
Dotfuscator, ek programlama ve hatta kaynak koduna erişim ihtiyacı duymadan derlenmiş bütünleştirilmiş kodlarda çalışır.

![PreEmptive Protection - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Korumanın önemi

**Fikri mülkiyetinizin (IP) korunması** önemlidir.
Uygulamanızın kodu tasarım ve uygulama ayrıntılarını içerdiğinden IP olarak düşünülebilir.
Ancak, .NET Framework’te oluşturulan uygulamalar [önemli meta veriler ve yüksek düzeyde ara kod içerdiğinden][assemblies] birçok otomatikleştirilmiş araç ile bunlara tersine mühendislik uygulamak oldukça kolaydır.
Tersine mühendisliği engelleyip durdurarak IP’nizin yetkisiz şekilde açığa çıkarılmasını engelleyebilir ve kodunuzun ticari sırlar içerdiğini gösterebilirsiniz.
Dotfuscator, asıl uygulama davranışlarını korurken tersine mühendisliği engellemek için .NET bütünleştirilmiş kodlarınızı [karartabilir][obfuscation].

**Uygulamanızın bütünlüğünün korunması** da önemlidir.
Kötü aktörler, tersine mühendisliğe ek olarak uygulamanızın korsan sürümünü yayınlamayı, uygulamanın çalışma zamanındaki davranışını değiştirmeyi veya verileri denetlemeyi deneyebilir.
Dotfuscator, uygulamanıza yönelik kurcalama, üçüncü taraf hata ayıklaması ve kök erişimi verilmiş cihazlar gibi [yetkisiz kullanımları algılayıp bunlara yanıt verme][checks] özelliği ekleyebilir.

Dotfuscator’un güvenli bir yazılım geliştirme yaşam döngüsüne nasıl uyum sağladığına ilişkin daha fazla bilgi edinmek için bkz. PreEmptive Solutions [SDL Uygulama Koruması sayfası][sdl-protection].

## <a name="about-dotfuscator-community"></a>Dotfuscator Community hakkında

Microsoft Visual Studio kopyanız, kişisel kullanım için ücretsiz olarak sunulan ***PreEmptive Protection - Dotfuscator Community*** kopyasını içerir.
(Bu ücretsiz sürüm daha önce Dotfuscator Community Sürümü veya Dotfuscator CE olarak biliniyordu.) Visual Studio ile sunulan Dotfuscator Community’nin sürümünü yüklemek için bkz. [Yükleme sayfası][install].

Dotfuscator Community, geliştiriciler, mimarlar ve test ediciler için çeşitli [yazılım koruması ve sağlamlaştırma][software-protection] hizmetleri sunar.
Dotfuscator Community ile sunulan [.NET Kod karartma][obfuscation] ve diğer [Uygulama Koruması][app-protection] özelliklerine şunlar örnek verilebilir:

* Derlenmiş bütünleştirilmiş kodlarda tersine mühendislik uygulamayı zorlaştırmak için tanımlayıcıları *[yeniden adlandırma][renaming]* .
* Kurcalama yapılan uygulamaları algılamaya ve kurcalamaya maruz kalan oturumları sonlandırmaya veya bunlara yanıt vermeye yarayan *[kurcalama koruması][tamper]* .
* Çalışan bir uygulamaya hata ayıklayıcı eklenmesini algılamaya ve hatası ayıklanmış oturumları sonlandırmak veya bunlara yanıt vermeye yarayan *[hata ayıklama koruması][debug]* .
* Uygulamanın kök erişimi verilmiş bir Android cihazında çalışıp çalışmadığını algılama, bu cihazlardaki oturumları sonlandırma ve bunlara yanıt verme olanağı tanıyan *[kök erişimi verilmiş cihaz koruması][root]* .
* “Yaşam sonu” tarihi kodlayan ve süresi dolan uygulamaları sonlandıran *[uygulamanın süresinin dolmasına ilişkin davranışlar][shelflife]* .

Özelliklere ilişkin, uygulama koruma stratejinize nasıl uyum sağladıkları gibi ayrıntılar için [Özellikler sayfasına][capabilities] bakın.

Dotfuscator Community, kullanıma hazır temel koruma sunar.
Dotfuscator Community’nin kayıtlı kullanıcıları ve dünyanın lider [.NET Kod Karartıcısı][net-obfuscator] olan ***PreEmptive Protection - Dotfuscator Professional*** kullanıcıları, diğer uygulama koruma önleminden de yararlanabilir.
Dotfuscator’ı geliştirmeye ilişkin daha fazla bilgi için [Yükseltmeler sayfasına][upgrades] bakın.

## <a name="getting-started"></a>Başlarken

::: moniker range=">=vs-2019"

Visual Studio’dan Dotfuscator Community’yi kullanmaya başlamak için **Arama Kutusuna** (Ctrl+Q) `dotfuscator` yazın.

* Dotfuscator Community zaten yüklüyse, **Arama Kutusu**, *Menü* başlığının altında Dotfuscator Community’yi başlatma seçeneğini gösterir. Ayrıntılar için, bkz. [Tam kapsamlı Dotfuscator Community Kullanıcı Kılavuzu’nun Kullanmaya Başlama Sayfası][get-started].
* Dotfuscator Community yüklü değilse, **Arama Kutusu**, *Ayrı Bileşenler* başlığının altında **PreEmptive Protection - Dotfuscator’ı Yükle** seçeneğini gösterir. Ayrıntılar için [Yükleme sayfasına][install] bakın.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio’dan Dotfuscator Community’yi kullanmaya başlamak için **Hızlı Başlatma** (Ctrl+Q) arama çubuğuna `dotfuscator` yazın.

* Dotfuscator Community yüklüyse, **Hızlı Başlat** Dotfuscator Community kullanıcı arabirimini başlatmaya yarayan *Menü* seçeneğini getirir. Ayrıntılar için, bkz. [Tam kapsamlı Dotfuscator Community Kullanıcı Kılavuzu’nun Kullanmaya Başlama Sayfası][get-started].
* Dotfuscator Community yüklü değilse, **Hızlı Başlat** ilgili *Yükle* seçeneğini getirir. Ayrıntılar için [Yükleme sayfasına][install] bakın.

::: moniker-end

Dotfuscator Community’nin **en son sürümünü** [preemptive.com adresindeki Dotfuscator İndirmeleri sayfasından][download] edinebilirsiniz.

## <a name="full-documentation"></a>Tüm belgeler

Bu sayfa ve tüm alt sayfaları, [aracı yüklemeye ilişkin yönergelerin][install] yanı sıra Dotfuscator Community özelliklerine yönelik yüksek düzeyde bir genel bakış sunar.

[Dotfuscator Community kullanıcı arabirimini kullanmaya başlama][get-started] gibi ayrıntılı kullanım yönergeleri için [preemptive.com adresindeki tam kapsamlı Dotfuscator Community Kullanıcı Kılavuzu][full]’na bakın.

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
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
