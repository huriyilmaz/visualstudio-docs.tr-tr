---
title: Mac için Visual Studio turu
description: Mac için Visual Studio, macos 'ta iOS, Android, Mac ve xamarin. Forms için ASP.NET Core web siteleri ve xamarin projeleri gibi .net uygulamaları oluşturmaya yönelik tümleşik bir geliştirme ortamı sağlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: f102fe5fece877098c30c9183f36203568f368ef
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517804"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Mac turu için Visual Studio 2019

Mac için Visual Studio, Mac üzerinde kod düzenlemek, hata ayıklamak ve derlemek ve sonra bir uygulama yayımlamak için kullanılabilen .net _tümleşik geliştirme ortamıdır_ . bir kod düzenleyicisine ve hata ayıklayıcıya ek olarak, Mac için Visual Studio yazılım geliştirme sürecini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve kaynak denetimi özellikleri içerir.

Mac için Visual Studio,, veya dosyaları gibi Windows karşılığından aynı dosya türlerini destekler `.csproj` `.fsproj` `.sln` ve editorconfig gibi özellikleri destekler, yani sizin için en uygun ıde 'yi kullanabileceğiniz anlamına gelir.
bir uygulama oluşturmak, açmak ve geliştirmek, daha önce Windows Visual Studio kullanan herkes için tanıdık bir deneyim olacaktır. ayrıca, Mac için Visual Studio güçlü bir ıde gibi Windows karşılığına sahip güçlü araçların çoğunu kullanır. Roslyn derleyici platformu, yeniden düzenleme ve IntelliSense için kullanılır. proje sistemi ve yapı altyapısı MSBuild kullanır ve kaynak düzenleyicisi, Windows Visual Studio aynı temeli kullanır. Xamarin ve .NET Core uygulamaları için aynı hata ayıklayıcı altyapılarını ve Xamarin. iOS ve Xamarin. Android için aynı tasarımcıları kullanır.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Mac için Visual Studio için ne yapabilirim?

Mac için Visual Studio aşağıdaki geliştirme türlerini destekler:

- C#, F # ve Razor sayfaları, JavaScript ve TypeScript desteği ile web uygulamalarını ASP.NET Core
- C# veya F ile .NET Core konsol uygulamaları #
- C ile platformlar arası Unity oyunları ve uygulamaları #
- C# veya F # ve XAML ile Xamarin 'te Android, iOS, tvOS ve watchOS uygulamaları
- C# veya F 'de Cocoa masaüstü uygulamaları #

bu makalede, bu uygulamaların oluşturulmasına yönelik güçlü bir araç haline gelen bazı özelliklere göz atabilmek için Mac için Visual Studio çeşitli bölümleri incelenmektedir.

## <a name="ide-tour"></a>IDE turu

Mac için Visual Studio, uygulama dosyalarını ve ayarlarını yönetmek, uygulama kodu oluşturmak ve hata ayıklamak için çeşitli bölümler halinde düzenlenmiştir.

## <a name="getting-started"></a>Başlarken

Mac için Visual Studio 2019 ' i ilk kez başlattığınızda, yeni kullanıcılar bir oturum açma penceresi görür. Ücretli bir lisansı etkinleştirmek (varsa) veya Azure aboneliklerine bağlanmak için Microsoft hesabı ile oturum açın. bunu **daha sonra yapacağım** ve daha sonra **Visual Studio > oturum açma** menü öğesi aracılığıyla oturum açacağım:

![Microsoft hesabı oturum açın](media/ide-tour-2019-start-signin.png)

daha sonra tercih ettiğiniz klavye kısayollarını seçerek ıde 'yi özelleştirme seçeneği verilir: Mac için Visual Studio, Visual Studio, Visual Studio Code veya xcode:

![En sevdiğiniz klavye kısayollarını seçin](media/ide-tour-2019-keyboard-shortcut.png)

bu ilk kurulum deneyiminden sonra, son projelerin bir listesini ve var olan bir projeyi açmak ya da yeni bir proje açmak için düğmeleri gösteren Visual Studio 2019 ' ı her açışınızda _başlangıç penceresini_ görürsünüz:

![Son projeler arasından seçim yapın veya yeni bir öğe oluşturun](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Çözümler ve projeler

aşağıdaki görüntüde, yüklü bir uygulamayla birlikte Mac için Visual Studio gösterilmektedir:

![yüklü bir uygulama ile Mac için Visual Studio](media/ide-tour-image17.png)

aşağıdaki bölümlerde Mac için Visual Studio içindeki önemli alanlara genel bir bakış sağlanmaktadır.

## <a name="solution-window"></a>Çözüm penceresi

Çözüm penceresi bir çözümdeki projeleri düzenler:

![Çözüm penceresinde düzenlenmiş projeler](media/ide-tour-image18.png)

Bu, kaynak kodu, kaynaklar, Kullanıcı arabirimi ve bağımlılıkların dosyaları platforma özgü projelere göre düzenlenir.

Mac için Visual Studio 'de projeleri ve çözümleri kullanma hakkında daha fazla bilgi için, bkz. [projeler ve çözümler](./projects-and-solutions.md) makalesi.

## <a name="assembly-references"></a>Bütünleştirilmiş kod başvuruları

Her proje için derleme başvuruları, başvurular klasörü altında kullanılabilir:

![Çözüm penceresinde başvurular klasörü](media/ide-tour-image19.png)

Başvurular klasörüne çift tıklanarak veya bağlam menüsü eylemlerinde **başvuruları Düzenle** ' yi seçerek görüntülenen **başvuruları Düzenle** iletişim kutusu kullanılarak ek başvurular eklenir:

![Başvuruları Düzenle Iletişim kutusu](media/ide-tour-image20.png)

Mac için Visual Studio başvuruları kullanma hakkında daha fazla bilgi için, [Project bir makalede başvuruları yönetme](./managing-references-in-a-project.md) makalesine bakın.

## <a name="dependencies--packages"></a>Bağımlılıklar/paketler

Uygulamanızda kullanılan tüm dış bağımlılıklar, .NET Core veya Xamarin. iOS/Xamarin. Android projesinde olmanıza bağlı olarak bağımlılıklar veya paketler klasörüne depolanır. Bunlar genellikle bir NuGet biçiminde sağlanır.

NuGet, .net geliştirme için en popüler paket yöneticisidir. Visual Studio NuGet desteğiyle, kolayca uygulamanıza paket arayabilir ve bunları uygulamanıza ekleyebilirsiniz.

Uygulamanıza bir bağımlılık eklemek için bağımlılıklar/paketler klasörüne sağ tıklayın ve **Paketleri Ekle**' yi seçin:

![NuGet paketi ekleme](media/ide-tour-image21.png)

bir uygulamada NuGet paketi kullanmayla ilgili bilgiler, [proje makalenize bir NuGet projesi dahil olmak üzere](./nuget-walkthrough.md) bulunabilir.

## <a name="source-editor"></a>Kaynak Düzenleyicisi

C#, XAML veya JavaScript dilinde yazı yazıyorsanız bağımsız olarak, kod düzenleyicisi, aynı çekirdek bileşenlerini tamamen yerel bir kullanıcı arabirimiyle Windows Visual Studio paylaşır.

Bu, aşağıdaki özelliklerden bazılarını getirir:

* Yerel macOS (Cocoa tabanlı) kullanıcı arabirimi (araç ipuçları, düzenleyici yüzeyi, kenarlıklar, metin işleme, IntelliSense)
* IntelliSense tür filtrelemesi ve "içeri aktarma öğelerini göster"
* Yerel metin girişleri için destek
* RTL/BiDi dil desteği
* Roslyn 3
* Çoklu giriş işareti desteği
* Sözcük kaydırma
* Güncelleştirilmiş IntelliSense Kullanıcı arabirimi
* Geliştirilmiş bulma/değiştirme
* Kod parçacığı desteği 
* Biçim seçimi
* Satır içi ampuller

kaynak düzenleyiciyi Mac için Visual Studio kullanma hakkında daha fazla bilgi için bkz. [kaynak düzenleyici](./source-editor.md) belgeleri.

Sekmeleri her zaman görünür tutmak için, onları sabitlemenin avantajlarından yararlanabilirsiniz. Bu, bir projeyi her başlattığınızda, ihtiyacınız olan sekmenin her zaman görünmesini sağlar. Bir sekmeyi sabitlemek için, sekmenin üzerine gelin ve _sabitle_ simgesine tıklayın:

![Sekmeyi sabitleme](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Yeniden Düzenle

Mac için Visual Studio, kodunuzu yeniden düzenleme için iki yararlı yol sağlar: bağlam eylemleri ve kaynak analizi. Yeniden [düzenleme](./refactoring.md) makalesindeki bunlarla ilgili daha fazla bilgi edinebilirsiniz.

## <a name="debugging"></a>Hata Ayıklama

Mac için Visual Studio .net Core, .NET Framework, Unity ve Xamarin projelerini destekleyen hata ayıklayıcıları vardır. Mac için Visual Studio, .net Core hata ayıklayıcısını ve Mono Soft debugger 'ı kullanarak ıde 'nin tüm platformlarda yönetilen kodun hatalarını ayıklamasına olanak tanır. Hata ayıklama hakkında daha fazla bilgi için [hata ayıklama](./debugging.md) makalesini ziyaret edin.

Hata ayıklayıcı, dizeler, renkler, URL 'Ler ve boyutlar, koordinatlar ve Bézier eğrileri gibi özel türler için zengin Görselleştiriciler içerir.

Hata ayıklayıcının veri görselleştirmeleri hakkında daha fazla bilgi için, [veri görselleştirmeleri](./data-visualizations.md) makalesini ziyaret edin.

## <a name="version-control"></a>Sürüm denetimi

Mac için Visual Studio, Git ve alt sürüm kaynak denetimi sistemleriyle tümleştirilir. Kaynak denetimi altındaki projeler, çözüm adının yanında listelenen Dalla birlikte gösterilir:

![Kaynak denetimi altında projeyi gösterecek dal adı](media/ide-tour-image22.png)

Kaydedilmemiş değişiklikleri olan dosyalar, aşağıdaki görüntüde gösterildiği gibi, çözüm penceresindeki simgelerinde ek açıklamaya sahiptir:

![Çözüm penceresinde işlenmemiş dosyalar](media/ide-tour-image23.png)

Visual Studio sürümünde sürüm denetimini kullanma hakkında daha fazla bilgi için [sürüm denetimi](./version-control.md) makalesine bakın.

## <a name="next-steps"></a>Sonraki adımlar

- [Mac için Visual Studio’yu yükleyin](installation.md)
- [Kullanılabilir iş yüklerini gözden geçirin](workloads.md)

## <a name="related-video"></a>İlgili video

> [!Video https://docs.microsoft.com/shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Ayrıca bkz.

- [ıde Visual Studio (Windows)](/visualstudio/ide/visual-studio-ide)