---
title: Mac Tour için Visual Studio
description: Mac için Visual Studio, ASP.NET Core web siteleri ve iOS, Android, Mac ve Xamarin.Forms için Xamarin projeleri de dahil olmak üzere macOS'ta .NET uygulamaları oluşturmak için entegre bir geliştirme ortamı sağlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/13/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: f7686efae903912b64d8692a823d6e82592cbec9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405827"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Mac turu için Visual Studio 2019

Mac için Visual Studio, Mac'te kodu düzenlemesi, hata ayıklama ve oluşturma ve ardından bir uygulama yayımlamak için kullanılabilecek bir .NET _tümleşik geliştirme ortamıdır._ Standart bir düzenleyici ve hata ayıklayıcı gibi beklenen özelliklere ek olarak, Mac için Visual Studio yazılım geliştirme sürecini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve kaynak denetimi içerir.

Mac için Visual Studio, Windows'daki muadili , `.csproj` `.fsproj`, `.sln` , veya dosyalar gibi aynı dosya türlerinin çoğunu destekler ve EditorConfig gibi özellikleri destekler, yani sizin için en uygun IDE'yi kullanabilirsiniz.
Bir uygulama oluşturmak, açmak ve geliştirmek, daha önce Windows'da Visual Studio'u kullanmış olan herkes için tanıdık bir deneyim olacaktır. Buna ek olarak, Mac için Visual Studio, Windows muadili gibi güçlü bir IDE yapmak güçlü araçların birçok kullanır. Roslyn Derleyici Platformu refactoring ve IntelliSense için kullanılır. Proje sistemi ve yapı motoru kullanımı MSBuild ve kaynak düzenleyiciwindows Visual Studio aynı temel kullanır. Xamarin ve .NET Core uygulamaları için aynı hata ayıklama motorlarını ve Xamarin.iOS ve Xamarin.Android için aynı tasarımcıları kullanır.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Mac için Visual Studio'da neler yapabilirim

Mac için Visual Studio aşağıdaki geliştirme türlerini destekler:

- ASP.NET C#, F#ve Razor sayfaları, JavaScript ve TypeScript desteği içeren Core web uygulamaları
- .NET Core konsol uygulamaları C# veya F #
- C ile platform ötesi Unity oyunları ve uygulamaları #
- C# veya F# ve XAML ile Xamarin'de Android, iOS, tvOS ve watchOS uygulamaları
- C# veya F'de kakao masaüstü uygulamaları #

Bu makalede, Mac için Visual Studio'nun çeşitli bölümlerini inceleyerek, bu uygulamaları oluşturmak için güçlü bir araç haline getiren bazı özelliklere bir göz atabilirsiniz.

## <a name="ide-tour"></a>IDE turu

Mac için Visual Studio, uygulama dosyalarını ve ayarlarını yönetmek, uygulama kodu oluşturmak ve hata ayıklama için çeşitli bölümlere ayrılmıştır.

## <a name="getting-started"></a>Başlarken

Mac için Visual Studio 2019'u başlattığınızda, yeni kullanıcılar oturum açma penceresi görür. Ücretli bir lisansı etkinleştirmek için Microsoft hesabınızla oturum açın (varsa) veya Azure aboneliklerine bağlantı. **Bunu daha sonra yapacağım** a basın ve daha sonra Visual Studio > Sign **in** menü öğesi aracılığıyla oturum açabilirsiniz:

![Microsoft hesabınızda oturum açma](media/ide-tour-2019-start-signin.png)

Daha sonra tercih ettiğiniz klavye kısayollarını seçerek IDE'yi özelleştirme seçeneği ne olacak: Mac için Visual Studio, Visual Studio Code veya Xcode:

![En sevdiğiniz klavye kısayollarını seçin](media/ide-tour-2019-keyboard-shortcut.png)

Oturum açmış kullanıcılar, yeni projelerin listesini gösteren yeni _başlangıç penceresini_ve varolan bir projeyi açmak veya yeni bir proje oluşturmak için düğmeleri görür:

![Son projelerden birini seçin veya yeni bir şey oluşturun](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Aşağıdaki resimde Visual Studio for Mac yüklü bir uygulama ile gösterilmektedir:

![Yüklü bir uygulama ile Mac için Visual Studio](media/ide-tour-image17.png)

Aşağıdaki bölümler, Mac için Visual Studio'daki ana alanlara genel bir bakış sağlar.

## <a name="solution-pad"></a>Çözüm pedi

Çözüm Pad, proje(ler)i bir çözümde düzenler:

![Çözüm Ped'de Düzenlenen Projeler](media/ide-tour-image18.png)

Kaynak kodu, kaynaklar, kullanıcı arabirimi ve bağımlılıklar için dosyaların platforma özgü Projeler olarak düzenlendiği yerdir.

Mac için Visual Studio'da Projeler ve Çözümler'i kullanma hakkında daha fazla bilgi için [Projeler ve Çözümler](/visualstudio/mac/projects-and-solutions) makalesine bakın.

## <a name="assembly-references"></a>Montaj başvuruları

Her proje için derleme başvuruları Başvurular klasörü altında mevcuttur:

![Çözüm defterindeki başvurular klasörü](media/ide-tour-image19.png)

Başvurular klasörüne çift tıklayarak veya bağlam menüsü eylemlerinde **Başvuruları Edit** seçilerek görüntülenen **Başvuruları Edit** iletişim kutusu kullanılarak ek başvurular eklenir:

![Başvuruları Edin İletişim](media/ide-tour-image20.png)

Mac için Visual Studio'da Referansları kullanma hakkında daha fazla bilgi [için, Bir Proje makalesinde Başvuruları Yönetme'ye](/visualstudio/mac/managing-references-in-a-project) bakın.

## <a name="dependencies--packages"></a>Bağımlılıklar / paketler

Uygulamanızda kullanılan tüm dış bağımlılıklar, bir .Net Core veya Xamarin.iOS/Xamarin.Android projesinde olup olmadığınıza bağlı olarak Bağımlılıklar veya Paketler klasöründe depolanır. Bunlar genellikle NuGet şeklinde sağlanır.

NuGet ,NET geliştirme için en popüler paket yöneticisidir. Visual Studio'nun NuGet desteği ile projenize kolayca arama yapabilir ve uygulamaya paket ekleyebilirsiniz.

Uygulamanıza bağımlılık eklemek için Bağımlılıklar / Paketler klasörüne sağ tıklayın ve **Paket Ekle'yi**seçin:

![NuGet paketi ekle](media/ide-tour-image21.png)

Bir uygulamada NuGet paketini kullanma yla ilgili bilgileri [proje makalenizde Bir NuGet projesi dahil etme'de](/visualstudio/mac/nuget-walkthrough) bulabilirsiniz.

## <a name="source-editor"></a>Kaynak Düzenleyicisi

C#, XAML veya Javascript'te yazıyorsanız, kod düzenleyicisi visual studio Windows ile tamamen yerel bir kullanıcı arabirimi yle aynı temel bileşenleri paylaşır.

Bu, aşağıdaki özelliklerden bazılarını getirir:

* Yerel macOS (Cocoa tabanlı) kullanıcı arabirimi (araç ipuçları, düzenleyici yüzeyi, kenarlıklar, metin işleme, IntelliSense)
* IntelliSense türü filtreleme ve "alma öğelerini göster"
* Yerel metin girişleri için destek
* RTL/BiDi dil desteği
* Roslyn 3
* Çoklu giriş işareti desteği
* Sözcük kaydırma
* Güncelleştirilmiş IntelliSense UI
* Geliştirilmiş bul/değiştir
* Snippet desteği 
* Biçim seçimi
* Sıralı ampuller

Mac için Visual Studio'daki Kaynak Düzenleyici'yi kullanma hakkında daha fazla bilgi için [Kaynak Düzenleyici](/visualstudio/mac/source-editor) belgelerine bakın.

Sekmeleri her zaman görünür tutmak için, bunları sabitleme avantajlarından yararlanabilirsiniz. Bu, bir projeyi her başlattığınızda, gereksinim duyduğunuz sekmenin her zaman görünmesini sağlar. Bir sekmeyi sabitlemek için sekmeye basın ve _pin_ simgesini tıklatın:

![Sekmeyi sabitleme](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Yeniden Düzenle

Mac için Visual Studio kodunuzu yeniden düzenlemenin iki yararlı yolunu sağlar: Bağlam Eylemleri ve Kaynak Çözümlemesi. [Refactoring](/visualstudio/mac/refactoring) makalesinde onlar hakkında daha fazla bilgi edinebilirsiniz.

## <a name="debugging"></a>Hata ayıklama

Mac için Visual Studio,.NET Core, .NET Framework, Unity ve Xamarin projelerini destekleyen hata ayıklayıcıları vardır. Mac için Visual Studio ,NET Core hata ayıklayıcıve Mono Yumuşak Hata Ayıklayıcı'yı kullanır ve IDE'nin tüm platformlarda yönetilen kodu hata ayıklamasına olanak sağlar. Hata ayıklama hakkında daha fazla bilgi için Hata Ayıklama makalesini ziyaret [edin.](/visualstudio/mac/debugging)

Hata ayıklayıcı, dizeleri, renkleri, URL'leri gibi özel türleri yanı sıra boyutlar, koordinatlar ve bézier eğrileri için zengin görselleştiriciler içerir.

Hata ayıklamanın veri görselleştirmeleri hakkında daha fazla bilgi için [Veri Görselleştirmeleri](/visualstudio/mac/data-visualizations) makalesini ziyaret edin.

## <a name="version-control"></a>Sürüm denetimi

Mac için Visual Studio, Git ve Subversion kaynak kontrol sistemleriyle entegre olur. Kaynak denetimi altındaki projeler, Çözüm adının yanında listelenen şube ile gösterilir:

![Kaynak denetimi altındaki projeyi belirtmek için şube adı](media/ide-tour-image22.png)

Kaydedilmemiş değişiklikleri olan dosyaların Çözüm Bölmesi'ndeki simgelerinde aşağıdaki resimde gösterildiği gibi ek bir açıklama bulunur:

![Çözüm defterinde kaydedilmemiş dosyalar](media/ide-tour-image23.png)

Visual Studio'da sürüm denetimini kullanma hakkında daha fazla bilgi için [Sürüm Denetimi](/visualstudio/mac/version-control) makalesine bakın.

## <a name="next-steps"></a>Sonraki adımlar

- [Mac için Visual Studio’yu yükleyin](installation.md)
- [Kullanılabilir iş yüklerini gözden geçirme](workloads.md)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE (Windows'da)](/visualstudio/ide/visual-studio-ide)
