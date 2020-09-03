---
title: Mac için Visual Studio turu
description: Mac için Visual Studio, macOS 'ta iOS, Android, Mac ve Xamarin. Forms için ASP.NET Core Web siteleri ve Xamarin projeleri gibi .NET uygulamaları oluşturmaya yönelik tümleşik bir geliştirme ortamı sağlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 3d25fced1e9c9dd6431f4056b5b561f476eecb28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984976"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Mac için Visual Studio 2017 Tur turu

> [!NOTE]
> Mac için Visual Studio 2019 [artık kullanılabilir](installation.md).

Mac için Visual Studio, Mac üzerinde kod düzenlemek, hata ayıklamak ve derlemek ve sonra bir uygulama yayımlamak için kullanılabilen .NET _Tümleşik geliştirme ortamıdır_ . Standart bir düzenleyici ve hata ayıklayıcı gibi beklenen özelliklere ek olarak Mac için Visual Studio, yazılım geliştirme sürecini ese için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve kaynak denetimi içerir.

Mac için Visual Studio,, veya dosyaları gibi Windows karşılığı ile aynı dosya türlerini destekler `.csproj` `.fsproj` `.sln` ve editorconfig gibi özellikleri destekler, bu da sizin IÇIN en uygun IDE 'yi kullanabileceğiniz anlamına gelir.
Bir uygulama oluşturmak, açmak ve geliştirmek, daha önce Windows üzerinde Visual Studio kullanan herkes için tanıdık bir deneyim olacaktır. Ayrıca Mac için Visual Studio, Windows karşılığına yönelik güçlü bir IDE gibi birçok güçlü araç kullanır. Roslyn derleyici platformu, yeniden düzenleme ve IntelliSense için kullanılır. Proje sistemi ve yapı altyapısı MSBuild kullanır ve kaynak Düzenleyicisi TextMate paketlerini destekler. Xamarin ve .NET Core uygulamaları için aynı hata ayıklayıcı altyapılarını ve Xamarin. iOS ve Xamarin. Android için aynı tasarımcıları kullanır.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Mac için Visual Studio için ne yapabilirim?

Mac için Visual Studio aşağıdaki geliştirme türlerini destekler:

- C#, F # ve Razor sayfaları, JavaScript ve TypeScript desteği ile Web uygulamalarını ASP.NET Core
- C# veya F ile .NET Core konsol uygulamaları #
- C ile platformlar arası Unity oyunları ve uygulamaları #
- C# veya F # ve XAML ile Xamarin 'te Android, iOS, tvOS ve watchOS uygulamaları
- C# veya F 'de Cocoa masaüstü uygulamaları #

Bu makalede, bu uygulamaların oluşturulmasına yönelik güçlü bir araç haline gelen bazı özelliklere göz atabilmek için Mac için Visual Studio çeşitli bölümleri incelenmektedir.

## <a name="ide-tour"></a>IDE Turu

Mac için Visual Studio, uygulama dosyalarını ve ayarlarını yönetmek, uygulama kodu oluşturmak ve hata ayıklamak için çeşitli bölümler halinde düzenlenmiştir.

## <a name="welcome-screen"></a>Karşılama ekranı

Başlatıldığında, Mac için Visual Studio bir *hoş geldiniz ekranı*görüntüler:

![Karşılama ekranı](media/ide-tour-image1.png)

Hoş geldiniz ekranı aşağıdaki bölümleri içerir:

- **Araç çubuğu** -arama çubuğuna hızlı erişim sağlar. Bir çözüm yüklendiğinde, araç çubuğu uygulama yapılandırmasını ayarlamak için, hata ayıklama için ve hataları görüntülemek için kullanılır.
- **Başlarken** -Mac için Visual Studio kullanmaya başlarken geliştiriciler için faydalı konulara hızlı erişim sağlar.
- **Son çözümler** -son açılan çözümlere hızlı erişim sağlar ve projeleri açmak veya oluşturmak için uygun düğmeleri de sağlar.
- **Geliştirici Haberleri** -en son Microsoft Geliştirici bilgilerini güncel tutan bir haber akışı.

## <a name="solutions-and-projects"></a>Projeler ve Çözümler

Aşağıdaki görüntüde, yüklü bir uygulamayla birlikte Mac için Visual Studio gösterilmektedir:

![Yüklü bir uygulama ile Mac için Visual Studio](media/ide-tour-image17.png)

Aşağıdaki bölümlerde Mac için Visual Studio içindeki önemli alanlara genel bir bakış sağlanmaktadır.

## <a name="solution-pad"></a>Çözüm Bölmesi

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

## <a name="refactoring"></a>Yeniden Düzenle

Mac için Visual Studio, kodunuzu yeniden düzenleme için iki yararlı yol sağlar: bağlam eylemleri ve kaynak analizi. Yeniden [düzenleme](/visualstudio/mac/refactoring) makalesindeki bunlarla ilgili daha fazla bilgi edinebilirsiniz.

## <a name="debugging"></a>Hata Ayıklama

Mac için Visual Studio, Xamarin. iOS, Xamarin. Mac ve Xamarin. Android uygulamaları için hata ayıklama desteğine izin veren yerel bir hata ayıklayıcıya sahiptir. Mac için Visual Studio, mono çalışma zamanına uygulanan, IDE 'nin tüm platformlarda yönetilen kodda hata ayıklamasına izin veren mono yazılım hata ayıklayıcısını kullanır. Hata ayıklama hakkında daha fazla bilgi için [hata ayıklama](/visualstudio/mac/debugging) makalesini ziyaret edin.

Hata ayıklayıcı, dizeler, renkler, URL 'Ler ve boyutlar, birlikte ordinklar ve Bézier eğrileri gibi özel türler için zengin Görselleştiriciler içerir.

Hata ayıklayıcının veri görselleştirmeleri hakkında daha fazla bilgi için, [veri görselleştirmeleri](/visualstudio/mac/data-visualizations) makalesini ziyaret edin.

## <a name="version-control"></a>Sürüm Denetimi

Mac için Visual Studio, git ve alt sürüm kaynak denetimi sistemleriyle tümleştirilir. Kaynak denetimi altındaki projeler, çözüm adının yanında listelenen Dalla birlikte gösterilir:

![Kaynak denetimi altında projeyi gösterecek dal adı](media/ide-tour-image22.png)

Kaydedilmemiş değişiklikleri olan dosyalar, aşağıdaki görüntüde gösterildiği gibi, çözüm bölmesindeki simgelerinde ek açıklamasına sahiptir:

![Çözüm panelinde işlenmemiş dosyalar](media/ide-tour-image23.png)

Visual Studio 'da sürüm denetimini kullanma hakkında daha fazla bilgi için [sürüm denetimi](/visualstudio/mac/version-control) makalesine bakın.

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE (Windows üzerinde)](/visualstudio/ide/visual-studio-ide)
