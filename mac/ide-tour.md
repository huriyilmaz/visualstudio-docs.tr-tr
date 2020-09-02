---
title: Mac için Visual Studio turu
description: Mac için Visual Studio, macOS 'ta iOS, Android, Mac ve Xamarin. Forms için ASP.NET Core Web siteleri ve Xamarin projeleri gibi .NET uygulamaları oluşturmaya yönelik tümleşik bir geliştirme ortamı sağlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/13/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: f7686efae903912b64d8692a823d6e82592cbec9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75405827"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Mac için Visual Studio 2019 Tur turu

Mac için Visual Studio, Mac üzerinde kod düzenlemek, hata ayıklamak ve derlemek ve sonra bir uygulama yayımlamak için kullanılabilen .NET _Tümleşik geliştirme ortamıdır_ . Standart bir düzenleyici ve hata ayıklayıcı gibi beklenen özelliklerin yanı sıra, Mac için Visual Studio yazılım geliştirme sürecini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve kaynak denetimi de içerir.

Mac için Visual Studio,, veya dosyaları gibi Windows karşılığı ile aynı dosya türlerini destekler `.csproj` `.fsproj` `.sln` ve editorconfig gibi özellikleri destekler, bu da sizin IÇIN en uygun IDE 'yi kullanabileceğiniz anlamına gelir.
Bir uygulama oluşturmak, açmak ve geliştirmek, daha önce Windows üzerinde Visual Studio kullanan herkes için tanıdık bir deneyim olacaktır. Ayrıca Mac için Visual Studio, Windows karşılığına yönelik güçlü bir IDE gibi birçok güçlü araç kullanır. Roslyn derleyici platformu, yeniden düzenleme ve IntelliSense için kullanılır. Proje sistemi ve derleme altyapısı MSBuild kullanır ve kaynak Düzenleyicisi Windows üzerinde Visual Studio ile aynı temeli kullanır. Xamarin ve .NET Core uygulamaları için aynı hata ayıklayıcı altyapılarını ve Xamarin. iOS ve Xamarin. Android için aynı tasarımcıları kullanır.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Mac için Visual Studio için ne yapabilirim?

Mac için Visual Studio aşağıdaki geliştirme türlerini destekler:

- C#, F # ve Razor sayfaları, JavaScript ve TypeScript desteği ile Web uygulamalarını ASP.NET Core
- C# veya F ile .NET Core konsol uygulamaları #
- C ile platformlar arası Unity oyunları ve uygulamaları #
- C# veya F # ve XAML ile Xamarin 'te Android, iOS, tvOS ve watchOS uygulamaları
- C# veya F 'de Cocoa masaüstü uygulamaları #

Bu makalede, bu uygulamaların oluşturulmasına yönelik güçlü bir araç haline gelen bazı özelliklere göz atabilmek için Mac için Visual Studio çeşitli bölümleri incelenmektedir.

## <a name="ide-tour"></a>IDE turu

Mac için Visual Studio, uygulama dosyalarını ve ayarlarını yönetmek, uygulama kodu oluşturmak ve hata ayıklamak için çeşitli bölümler halinde düzenlenmiştir.

## <a name="getting-started"></a>Başlarken

Mac için Visual Studio 2019 ' u başlattığınızda yeni kullanıcılar bir oturum açma penceresi görür. Ücretli bir lisansı etkinleştirmek (varsa) veya Azure aboneliklerine bağlanmak için Microsoft hesabı ile oturum açın. Bunu **daha sonra yapacağım** ve daha sonra **Visual Studio > oturum açma** menü öğesi aracılığıyla oturum açacağım.

![Microsoft hesabı oturum açın](media/ide-tour-2019-start-signin.png)

Daha sonra tercih ettiğiniz klavye kısayollarını seçerek IDE 'yi özelleştirme seçeneği verilir: Mac için Visual Studio, Visual Studio, Visual Studio Code veya Xcode:

![En sevdiğiniz klavye kısayollarını seçin](media/ide-tour-2019-keyboard-shortcut.png)

Oturum açan kullanıcılar yeni _başlangıç penceresini_görür. Bu, en son projelerin bir listesini ve mevcut bir projeyi açmak ya da yeni bir proje açmak için düğmeleri gösterir:

![Son projeler arasından seçim yapın veya yeni bir öğe oluşturun](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Aşağıdaki görüntüde, yüklü bir uygulamayla birlikte Mac için Visual Studio gösterilmektedir:

![Yüklü bir uygulama ile Mac için Visual Studio](media/ide-tour-image17.png)

Aşağıdaki bölümlerde Mac için Visual Studio içindeki önemli alanlara genel bir bakış sağlanmaktadır.

## <a name="solution-pad"></a>Çözüm paneli

Çözüm Bölmesi bir çözümde proje (ler) i düzenler:

![Çözüm Bölmesi düzenlenmiş projeler](media/ide-tour-image18.png)

Bu, kaynak kodu, kaynaklar, Kullanıcı arabirimi ve bağımlılıkların dosyaları platforma özgü projelere göre düzenlenir.

Mac için Visual Studio 'de projeleri ve çözümleri kullanma hakkında daha fazla bilgi için, bkz. [Projeler ve çözümler](/visualstudio/mac/projects-and-solutions) makalesi.

## <a name="assembly-references"></a>Bütünleştirilmiş kod başvuruları

Her proje için derleme başvuruları, başvurular klasörü altında kullanılabilir:

![Çözüm panelinde başvurular klasörü](media/ide-tour-image19.png)

Başvurular klasörüne çift tıklanarak veya bağlam menüsü eylemlerinde **başvuruları Düzenle** ' yi seçerek görüntülenen **başvuruları Düzenle** iletişim kutusu kullanılarak ek başvurular eklenir:

![Başvuruları Düzenle Iletişim kutusu](media/ide-tour-image20.png)

Mac için Visual Studio başvuruları kullanma hakkında daha fazla bilgi için bkz. [bir projede başvuruları yönetme](/visualstudio/mac/managing-references-in-a-project) makalesi.

## <a name="dependencies--packages"></a>Bağımlılıklar/paketler

Uygulamanızda kullanılan tüm dış bağımlılıklar, .Net Core veya Xamarin. iOS/Xamarin. Android projesinde olup olmadığına bağlı olarak bağımlılıklar veya paketler klasörüne depolanır. Bunlar genellikle bir NuGet biçiminde sağlanır.

NuGet, .NET geliştirme için en popüler paket yöneticisidir. Visual Studio 'nun NuGet desteğiyle, kolayca uygulamanıza paket arayabilir ve uygulamanızı ekleyebilirsiniz.

Uygulamanıza bir bağımlılık eklemek için bağımlılıklar/paketler klasörüne sağ tıklayın ve **Paketleri Ekle**' yi seçin:

![NuGet paketi ekleme](media/ide-tour-image21.png)

Bir uygulamada NuGet paketinin kullanılmasıyla ilgili bilgiler, [Proje makalenize bir NuGet projesi dahil](/visualstudio/mac/nuget-walkthrough) bulunabilir.

## <a name="source-editor"></a>Kaynak Düzenleyicisi

C#, XAML veya JavaScript 'e yazıyorsanız bağımsız olarak, kod Düzenleyicisi Visual Studio Windows ile aynı çekirdek bileşenlerini tamamen yerel bir kullanıcı arabirimiyle paylaşır.

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

Kaynak düzenleyiciyi Mac için Visual Studio kullanma hakkında daha fazla bilgi için bkz. [kaynak Düzenleyici](/visualstudio/mac/source-editor) belgeleri.

Sekmeleri her zaman görünür tutmak için, onları sabitlemenin avantajlarından yararlanabilirsiniz. Bu, bir projeyi her başlattığınızda, ihtiyacınız olan sekmenin her zaman görünmesini sağlar. Bir sekmeyi sabitlemek için, sekmenin üzerine gelin ve _sabitle_ simgesine tıklayın:

![Sekmeyi sabitleme](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Yeniden Düzenle

Mac için Visual Studio, kodunuzu yeniden düzenleme için iki yararlı yol sağlar: bağlam eylemleri ve kaynak analizi. Yeniden [düzenleme](/visualstudio/mac/refactoring) makalesindeki bunlarla ilgili daha fazla bilgi edinebilirsiniz.

## <a name="debugging"></a>Hata Ayıklama

Mac için Visual Studio .NET Core, .NET Framework, Unity ve Xamarin projelerini destekleyen hata ayıklayıcıları vardır. Mac için Visual Studio, .NET Core hata ayıklayıcısını ve mono Soft Debugger 'ı kullanarak IDE 'nin tüm platformlarda yönetilen kodun hatalarını ayıklamasına olanak tanır. Hata ayıklama hakkında daha fazla bilgi için [hata ayıklama](/visualstudio/mac/debugging) makalesini ziyaret edin.

Hata ayıklayıcı, dizeler, renkler, URL 'Ler ve boyutlar, koordinatlar ve Bézier eğrileri gibi özel türler için zengin Görselleştiriciler içerir.

Hata ayıklayıcının veri görselleştirmeleri hakkında daha fazla bilgi için, [veri görselleştirmeleri](/visualstudio/mac/data-visualizations) makalesini ziyaret edin.

## <a name="version-control"></a>Sürüm denetimi

Mac için Visual Studio, git ve alt sürüm kaynak denetimi sistemleriyle tümleştirilir. Kaynak denetimi altındaki projeler, çözüm adının yanında listelenen Dalla birlikte gösterilir:

![Kaynak denetimi altında projeyi gösterecek dal adı](media/ide-tour-image22.png)

Kaydedilmemiş değişiklikleri olan dosyalar, aşağıdaki görüntüde gösterildiği gibi, çözüm bölmesindeki simgelerinde ek açıklamasına sahiptir:

![Çözüm panelinde işlenmemiş dosyalar](media/ide-tour-image23.png)

Visual Studio 'da sürüm denetimini kullanma hakkında daha fazla bilgi için [sürüm denetimi](/visualstudio/mac/version-control) makalesine bakın.

## <a name="next-steps"></a>Sonraki adımlar

- [Mac için Visual Studio’yu yükleyin](installation.md)
- [Kullanılabilir iş yüklerini gözden geçirin](workloads.md)

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE (Windows üzerinde)](/visualstudio/ide/visual-studio-ide)
