---
title: Mac Tour için Visual Studio
description: Mac için Visual Studio, ASP.NET Core web siteleri ve iOS, Android, Mac ve Xamarin.Forms için Xamarin projeleri de dahil olmak üzere macOS'ta .NET uygulamaları oluşturmak için entegre bir geliştirme ortamı sağlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 3d25fced1e9c9dd6431f4056b5b561f476eecb28
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984976"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Mac turu için Visual Studio 2017

> [!NOTE]
> Mac için Visual Studio 2019 [artık mevcuttur.](installation.md)

Mac için Visual Studio, Mac'te kodu düzenlemesi, hata ayıklama ve oluşturma ve ardından bir uygulama yayımlamak için kullanılabilecek bir .NET _tümleşik geliştirme ortamıdır._ Standart bir düzenleyici ve hata ayıklayıcı gibi beklenen özelliklere ek olarak, Visual Studio for Mac derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve yazılım geliştirme sürecini yapmak için kaynak denetimi içerir.

Mac için Visual Studio, Windows'daki muadili , `.csproj` `.fsproj`, `.sln` , veya dosyalar gibi aynı dosya türlerinin çoğunu destekler ve EditorConfig gibi özellikleri destekler, yani sizin için en uygun IDE'yi kullanabilirsiniz.
Bir uygulama oluşturmak, açmak ve geliştirmek, daha önce Windows'da Visual Studio'u kullanmış olan herkes için tanıdık bir deneyim olacaktır. Buna ek olarak, Mac için Visual Studio, Windows muadili gibi güçlü bir IDE yapmak güçlü araçların birçok kullanır. Roslyn Derleyici Platformu refactoring ve IntelliSense için kullanılır. Proje sistemi ve yapı motoru kullanımı MSBuild ve kaynak düzenleyicisi TextMate paketlerini destekler. Xamarin ve .NET Core uygulamaları için aynı hata ayıklama motorlarını ve Xamarin.iOS ve Xamarin.Android için aynı tasarımcıları kullanır.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Mac için Visual Studio'da neler yapabilirim

Mac için Visual Studio aşağıdaki geliştirme türlerini destekler:

- ASP.NET Core web uygulamalarını C#, F#, ve Razor sayfaları, JavaScript ve TypeScript desteği ile
- .NET Core konsol uygulamaları C# veya F #
- C ile platform ötesi Unity oyunları ve uygulamaları #
- C# veya F# ve XAML ile Xamarin'de Android, iOS, tvOS ve watchOS uygulamaları
- C# veya F'de kakao masaüstü uygulamaları #

Bu makalede, Mac için Visual Studio'nun çeşitli bölümlerini inceleyerek, bu uygulamaları oluşturmak için güçlü bir araç haline getiren bazı özelliklere bir göz atabilirsiniz.

## <a name="ide-tour"></a>IDE Turu

Mac için Visual Studio, uygulama dosyalarını ve ayarlarını yönetmek, uygulama kodu oluşturmak ve hata ayıklama için çeşitli bölümlere ayrılmıştır.

## <a name="welcome-screen"></a>Hoş Geldiniz Ekranı

Başlatıldığında, Mac için Visual Studio bir *Karşılama Ekranı*görüntüler:

![Hoş Geldiniz Ekranı](media/ide-tour-image1.png)

Karşılama Ekranı aşağıdaki bölümleri içerir:

- **Araç Çubuğu** - Arama çubuğuna hızlı erişim sağlar. Bir çözüm yüklendiğinde, araç çubuğu uygulama yapılandırmalarını ayarlamak, hata ayıklamak ve hataları görüntülemek için kullanılır.
- **Başlarken** - Mac için Visual Studio ile başlayan geliştiriciler için yararlı konulara hızlı erişim sağlar.
- **Son Çözümler** - Projeleri açmak veya oluşturmak için yakın zamanda açılan çözümlere hızlı erişim inyanımının yanı sıra kullanışlı düğmeler sağlar.
- **Developer Haberler** - En son Microsoft Geliştirici bilgileri hakkında güncel tuttuğunuz bir haber akışı.

## <a name="solutions-and-projects"></a>Projeler ve Çözümler

Aşağıdaki resimde Visual Studio for Mac yüklü bir uygulama ile gösterilmektedir:

![Yüklü bir uygulama ile Mac için Visual Studio](media/ide-tour-image17.png)

Aşağıdaki bölümler, Mac için Visual Studio'daki ana alanlara genel bir bakış sağlar.

## <a name="solution-pad"></a>Çözüm Pedi

Çözüm Pad, proje(ler)i bir çözümde düzenler:

![Çözüm Ped'de Düzenlenen Projeler](media/ide-tour-image18.png)

Kaynak kodu, kaynaklar, kullanıcı arabirimi ve bağımlılıklar için dosyaların platforma özgü Projeler olarak düzenlendiği yerdir.

Mac için Visual Studio'da Projeler ve Çözümler'i kullanma hakkında daha fazla bilgi için [Projeler ve Çözümler](/visualstudio/mac/projects-and-solutions) makalesine bakın.

## <a name="assembly-references"></a>Montaj Referansları

Her proje için derleme başvuruları Başvurular klasörü altında mevcuttur:

![Çözüm defterindeki başvurular klasörü](media/ide-tour-image19.png)

Başvurular klasörüne çift tıklayarak veya bağlam menüsü eylemlerinde **Başvuruları Edit** seçilerek görüntülenen **Başvuruları Edit** iletişim kutusu kullanılarak ek başvurular eklenir:

![Başvuruları Edin İletişim](media/ide-tour-image20.png)

Mac için Visual Studio'da Referansları kullanma hakkında daha fazla bilgi [için, Bir Proje makalesinde Başvuruları Yönetme'ye](/visualstudio/mac/managing-references-in-a-project) bakın.

## <a name="dependencies--packages"></a>Bağımlılıklar / Paketler

Uygulamanızda kullanılan tüm dış bağımlılıklar, bir .Net Core veya Xamarin.iOS/Xamarin.Android projesinde olup olmadığınıza bağlı olarak Bağımlılıklar veya Paketler klasöründe depolanır. Bunlar genellikle NuGet şeklinde sağlanır.

NuGet ,NET geliştirme için en popüler paket yöneticisidir. Visual Studio'nun NuGet desteği ile projenize kolayca arama yapabilir ve uygulamaya paket ekleyebilirsiniz.

Uygulamanıza bağımlılık eklemek için Bağımlılıklar / Paketler klasörüne sağ tıklayın ve **Paket Ekle'yi**seçin:

![NuGet paketi ekle](media/ide-tour-image21.png)

Bir uygulamada NuGet paketini kullanma yla ilgili bilgileri [proje makalenizde Bir NuGet projesi dahil etme'de](/visualstudio/mac/nuget-walkthrough) bulabilirsiniz.

## <a name="refactoring"></a>Yeniden Düzenle

Mac için Visual Studio kodunuzu yeniden düzenlemenin iki yararlı yolunu sağlar: Bağlam Eylemleri ve Kaynak Çözümlemesi. [Refactoring](/visualstudio/mac/refactoring) makalesinde onlar hakkında daha fazla bilgi edinebilirsiniz.

## <a name="debugging"></a>Hata ayıklama

Mac için Visual Studio Xamarin.iOS, Xamarin.Mac ve Xamarin.Android uygulamaları için hata ayıklama desteği sağlayan bir yerli hata ayıklayıcı vardır. Mac için Visual Studio, Mono çalışma süresine uygulanan Mono Soft Debugger'ı kullanır ve IDE'nin tüm platformlarda yönetilen kodu hata ayıklamasına olanak sağlar. Hata ayıklama hakkında daha fazla bilgi için Hata Ayıklama makalesini ziyaret [edin.](/visualstudio/mac/debugging)

Hata ayıklayıcı, dizeleri, renkleri, URL'leri gibi özel türleri yanı sıra boyutları, koordinatları ve bézier eğrileri için zengin görselleştiriciler içerir.

Hata ayıklamanın veri görselleştirmeleri hakkında daha fazla bilgi için [Veri Görselleştirmeleri](/visualstudio/mac/data-visualizations) makalesini ziyaret edin.

## <a name="version-control"></a>Sürüm Denetimi

Mac için Visual Studio, Git ve Subversion kaynak kontrol sistemleriyle entegre olur. Kaynak denetimi altındaki projeler, Çözüm adının yanında listelenen şube ile gösterilir:

![Kaynak denetimi altındaki projeyi belirtmek için şube adı](media/ide-tour-image22.png)

Kaydedilmemiş değişiklikleri olan dosyaların Çözüm Bölmesi'ndeki simgelerinde aşağıdaki resimde gösterildiği gibi ek bir açıklama bulunur:

![Çözüm defterinde kaydedilmemiş dosyalar](media/ide-tour-image23.png)

Visual Studio'da sürüm denetimini kullanma hakkında daha fazla bilgi için [Sürüm Denetimi](/visualstudio/mac/version-control) makalesine bakın.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE (Windows'da)](/visualstudio/ide/visual-studio-ide)
