---
title: Mac için Visual Studio Tur
description: Mac için Visual Studio, iOS, Android, Mac ve Xamarin.Forms için ASP.NET Core web siteleri ve Xamarin projeleri dahil olmak üzere macOS üzerinde .NET uygulamaları derlemek için tümleşik bir geliştirme ortamı sağlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: a2caadd454564b389f48987e69e1bc08475affea
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964776"
---
# <a name="visual-studio-2019-for-mac-tour"></a>mac Visual Studio 2019 turu

Mac için Visual Studio, Mac üzerinde kod  düzenlemek, hata ayıklamak ve derlemek ve ardından uygulama yayımlamak için kullanılmaktadır. Kod düzenleyicisi ve hata ayıklayıcısına ek olarak Mac için Visual Studio geliştirme sürecini kolaylaştıran derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve kaynak denetimi özellikleri de vardır.

Mac için Visual Studio, , veya dosyaları gibi Windows dosya türlerinin çoğunu destekler ve EditorConfig gibi özellikleri destekler; yani sizin için en iyi şekilde çalışan `.csproj` `.fsproj` `.sln` IDE'yi kullanabilirsiniz.
Uygulama oluşturma, açma ve geliştirme, daha önce bir uygulama üzerinde uygulama Visual Studio herkes için tanıdık Windows. Ayrıca, Mac için Visual Studio bir IDE gibi güçlü bir IDE Windows güçlü araçlardan birçoğuna sahip olur. Roslyn Derleyici Platformu, yeniden düzenleme ve IntelliSense için kullanılır. Proje sistemi ve derleme altyapısı MSBuild kullanır ve kaynak düzenleyicisi de Visual Studio ile aynı Windows. Xamarin ve .NET Core uygulamaları için aynı hata ayıklayıcı altyapılarını ve Xamarin.iOS ve Xamarin.Android için aynı tasarımcıları kullanır.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Mac için Visual Studio'da neler yapabilirim?

Mac için Visual Studio aşağıdaki geliştirme türlerini destekler:

- ASP.NET Core C#, F# ile web uygulamaları oluşturma ve Razor sayfaları, JavaScript ve TypeScript desteği
- C# veya F ile .NET Core konsol uygulamaları #
- C ile platformlar arası Unity oyunları ve uygulamaları #
- C# veya F# ve XAML ile Xamarin'de Android, iOS, tvOS ve watchOS uygulamaları
- C# veya F'de Cocoa masaüstü uygulamaları #

Bu makalede, bu Mac için Visual Studio için güçlü bir araç olan bazı özelliklere göz atarak bu uygulamanın çeşitli bölümleri incelemektedir.

## <a name="ide-tour"></a>IDE turu

Mac için Visual Studio, uygulama dosyalarını ve ayarlarını yönetmek, uygulama kodu oluşturmak ve hata ayıklamak için çeşitli bölümler halinde düzenlenmiştir.

## <a name="getting-started"></a>Başlarken

Mac için 2019'u ilk kez Visual Studio, yeni kullanıcılar oturum açma penceresiyle karşılar. Ücretli bir lisansı etkinleştirmek Microsoft hesabı (varsa) veya Azure abonelikleri bağlantısını etkinleştirmek için aboneliğiniz ile oturum açma. Bunu daha **sonra yapabilirim'e basabilirsiniz ve** Oturum aç menü öğesinde Visual Studio > **oturum** açabilirsiniz:

![Oturum açma Microsoft hesabı](media/ide-tour-2019-start-signin.png)

Ardından tercih ettiğiniz klavye kısayollarını seçerek IDE'yi özelleştirme seçeneği verilir: Mac için Visual Studio, Visual Studio, Visual Studio Code veya Xcode:

![Sık kullandığınız klavye kısayollarını seçin](media/ide-tour-2019-keyboard-shortcut.png)

Bu ilk kurulum deneyimi sonrasında Mac  için Visual Studio 2019'u her açsanız başlangıç penceresini ve mevcut bir projeyi açma veya yeni proje oluşturma düğmelerini gösterir:

![Son projelerden birini seçin veya yeni bir şey oluşturun](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Aşağıdaki görüntüde, Mac için Visual Studio yüklü bir uygulamanın nasıl yükleniyor olduğu gösterir:

![Mac için Visual Studio yüklü bir uygulamayla ilgili sorun](media/ide-tour-image17.png)

Aşağıdaki bölümlerde, uygulamanın temel alanlarına genel bir bakış Mac için Visual Studio.

## <a name="solution-window"></a>Çözüm Penceresi

Çözüm Penceresi, projeleri bir çözümde organize ediyor:

![Çözüm Penceresinde düzenlenen projeler](media/ide-tour-image18.png)

Burada kaynak kodu, kaynaklar, kullanıcı arabirimi ve bağımlılıklar için dosyalar platforma özgü Projeler olarak düzenlenmiştir.

Mac için Visual Studio'da Projeleri ve Çözümleri kullanma hakkında daha fazla bilgi için Projeler [ve Çözümler makalesine](./projects-and-solutions.md) bakın.

## <a name="assembly-references"></a>Derleme başvuruları

Her proje için derleme başvuruları, Başvurular klasörü altında kullanılabilir:

![Çözüm Penceresi'nin Başvurular klasörü](media/ide-tour-image19.png)

Ek başvurular, Başvurular klasörüne çift tıklar veya bağlam menüsü eylemlerini Düzenle'yi  seçerek görüntülenen Başvuruları Düzenle iletişim kutusu kullanılarak eklenir: 

![Başvuruları Düzenle İletişim Kutusu](media/ide-tour-image20.png)

Mac için Visual Studio'da Başvuruları kullanma hakkında daha fazla bilgi için bir Project [makalesine](./managing-references-in-a-project.md) bakın.

## <a name="dependencies--packages"></a>Bağımlılıklar/paketler

Bir .NET Core veya Xamarin.iOS/Xamarin.Android projesinde olup olmadığınız bağlı olarak, uygulamanıza kullanılan tüm dış bağımlılıklar Bağımlılıklar veya Paketler klasöründe depolanır. Bunlar genellikle bir NuGet.

NuGet .NET geliştirme için en popüler paket yöneticisidir. Visual Studio'nin NuGet desteği sayesinde kolayca projenizi arayabilir ve uygulamanıza paket ebilirsiniz.

Uygulamanıza bağımlılık eklemek için Bağımlılıklar / Paketler klasörüne sağ tıklayın ve Paket **Ekle'yi seçin:**

![Bir NuGet ekleme](media/ide-tour-image21.png)

Bir uygulamada NuGet paketi kullanma hakkında bilgiler, Projenizin bir [NuGet projesi dahil makalesinde](./nuget-walkthrough.md) bulunabilir.

## <a name="source-editor"></a>Kaynak Düzenleyicisi

C#, XAML veya JavaScript'te yazmadan bağımsız olarak, kod düzenleyicisi tamamen yerel bir kullanıcı arabirimiyle Visual Studio'de Windows ile aynı temel bileşenleri paylaşıyor.

Bu, aşağıdaki özelliklerden bazılarını getirir:

* Yerel macOS (Cocoa tabanlı) kullanıcı arabirimi (araç ipuçları, düzenleyici yüzeyi, kenarlıklar, metin işleme, IntelliSense)
* IntelliSense tür filtreleme ve "içeri aktarma öğelerini göster"
* Yerel metin girişleri için destek
* RTL/BiDi dil desteği
* Roslyn 3
* Çoklu giriş işareti desteği
* Sözcük kaydırma
* IntelliSense kullanıcı arabirimi güncelleştirildi
* Geliştirilmiş bul/değiştir
* Kod parçacığı desteği 
* Biçim seçimi
* Satır içi ampuller

Kaynak Düzenleyicisi'ni uygulama içinde kullanma hakkında daha fazla Mac için Visual Studio için Kaynak Düzenleyicisi [belgelerine](./source-editor.md) bakın.

Sekmeleri her zaman görünür tutmak için bunları sabitlemenin avantajını elde etmektir. Bu, bir projeyi her başlatmada ihtiyacınız olan sekmenin her zaman görünmesini sağlar. Bir sekmeyi sabitlemek için sekmenin üzerine gelin ve sabitleme _simgesine_ tıklayın:

![Sekme sabitleme](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Yeniden Düzenle

Mac için Visual Studio kodunuzu yeniden düzenlemenin iki yararlı yolu vardır: Bağlam Eylemleri ve Kaynak Analizi. Yeniden düzenleme makalesinde bu konuda daha [fazla bilgi bulabilirsiniz.](./refactoring.md)

## <a name="debugging"></a>Hata Ayıklama

Mac için Visual Studio.NET Core, .NET Framework, Unity ve Xamarin projelerini destekleyen hata ayıklayıcıları vardır. Mac için Visual Studio .NET Core hata ayıklayıcısını ve Mono Yazılım hata ayıklayıcısını kullanarak IDE'nin tüm platformlarda yönetilen kodda hata ayıklamasına olanak sağlar. Hata ayıklama hakkında daha fazla bilgi için Hata ayıklama [makalesine bakın.](./debugging.md)

Hata ayıklayıcısı dizeler, renkler, URL'ler, boyutlar, koordinatlar ve bézier eğrileri gibi özel türler için zengin görselleştiriciler içerir.

Hata ayıklayıcının veri görselleştirmeleri hakkında daha fazla bilgi için Veri [Görselleştirmeleri makalesini ziyaret](./data-visualizations.md) edin.

## <a name="version-control"></a>Sürüm denetimi

Mac için Visual Studio Git ve Subversion kaynak denetim sistemleriyle tümleştirilmiştir. Kaynak denetimi altındaki projeler, Çözüm adının yanında listelenen dal ile gösterilir:

![Kaynak denetimi altındaki projeyi göstermek için dal adı](media/ide-tour-image22.png)

Tamamlanmamış değişikliklere sahip dosyaların, aşağıdaki görüntüde gösterildiği gibi Çözüm Penceresi'nin simgelerinde bir ek açıklaması vardır:

![Çözüm Penceresinde işlanmamış dosyalar](media/ide-tour-image23.png)

Visual Studio'da sürüm denetimi kullanma hakkında daha fazla bilgi için Sürüm Denetimi [makalesine](./version-control.md) bakın.

## <a name="next-steps"></a>Sonraki adımlar

- [Mac için Visual Studio’yu yükleyin](installation.md)
- [Kullanılabilir iş yüklerini gözden geçirme](workloads.md)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE (Windows)](/visualstudio/ide/visual-studio-ide)