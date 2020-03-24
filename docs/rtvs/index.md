---
title: Visual Studio için R Araçları
description: Visual Studio için R Araçları 2017 (RTVS); IntelliSense, hata ayıklama ve uzak çalışma alanları gibi birçok dil özelliği sağlayan, ücretsiz bir açık kaynak uzantısıdır.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 1132a7a0363e2d508d6eff1026192aad3407fca4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "73189246"
---
# <a name="work-with-r-in-visual-studio"></a>Visual Studio’da R ile çalışma

R, istatistiksel bilgi işlem ve grafik için yüksek düzeyde genişletilebilir bir dil ve ortamdır. GNU Genel Kamu Lisansı kapsamında ücretsiz olarak dağıtılır, güçlü topluluk desteği alır ve matematik sembolleri ve formülleri gibi yayımlanabilir kalitede çizimler üretebilmesiyle bilinir. [r-project.org](https://www.r-project.org/about.html) ve [R’ye Giriş](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) bölümünde R hakkında daha fazla bilgi edinebilirsiniz.

Visual Studio için R Araçları (RTVS), MIT lisansı kapsamında yayınlanan, Visual Studio 2017 ve Visual Studio 2015 Güncelleştirme 3’ün (veya üzeri) ücretsiz bir [açık kaynak](https://github.com/microsoft/RTVS) uzantısıdır. (R yorumlayıcı ikililerine bağlantı oluşturan, [RHost](https://github.com/microsoft/R-Host) adı verilen ikinci bir açık kaynak bileşeni, GNU Genel Lisansı V2 kapsamında yayınlanmıştır.)

> [!Note]
> RTVS şu anda Mac için Visual Studio’da değil, yalnızca Windows’da Visual Studio 2017’de desteklenmektedir. Visual Studio 2019 için kullanılamaz.

Visual Studio’da R deneyimi için:

- [R Araçlarını yükleyin](installing-r-tools-for-visual-studio.md).
- [Başlarken](getting-started-with-r.md) kılavuzunu ve [Örnekler](getting-started-samples.md) ve [Yardım Alma](getting-started-help.md) makalelerini izleyin.

Daha sonra R ile ilgili özellikler ve Visual Studio’nun genel özellikleri hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıları izleyin.

| Özellik | Açıklama | Genel Visual Studio Belgeleri |
| --- | --- | --- |
| [Visual Studio proje sistemi](r-projects-in-visual-studio.md) | İlgili dosyaları uygun bir yapıda düzenleyip yönetin ve R kodu, R belgeleri, R Markdown, SQL sorguları ve saklı yordamlar gibi öğeler için faydalı şablonlardan yararlanın. Ayrıca, [paket yöneticisi](r-package-manager-in-visual-studio.md) ve [SQL Server tümleştirmesi](integrating-sql-server-with-r.md) keyfini de çıkarın.  | [Visual Studio’da Çözümler ve Projeler](../ide/solutions-and-projects-in-visual-studio.md) |
| [Çalışma alanı](r-workspaces-in-visual-studio.md) | RTVS, yerel ve uzak çalışma alanlarına bağlanarak daha küçük veri kümeleriyle yerel olarak R kodu geliştirmenize ve sonra daha büyük veri kümeleriyle daha güçlü bulut tabanlı bilgisayarlarda kodu çalıştırmanıza olanak sağlar. | yok |
| [R Araçları seçenekleri](options-for-r-tools-in-visual-studio.md) | RTVS’nin çeşitli yönlerini denetleyin. | [Seçenekler iletişim kutusu](../ide/reference/options-dialog-box-visual-studio.md) |
| [Zengin düzenleme, IntelliSense ve kod parçacıkları](editing-r-code-in-visual-studio.md) | Sözdizimi renklendirmeyi, tüm kod ve kitaplıklarınızda [IntelliSense](r-intellisense.md)’i, kod biçimlendirmeyi, imza yardımını, Tanıma Git seçeneğini, Tüm Başvuruları Bul seçeneğini, [kod parçacıklarını](code-snippets-for-r.md) ve daha fazlasını içerir. | [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | R Markdown belgeleri, markdown kod bloklarının içinde R kodu tümleştirilmiş şekilde veri sonuçlarınızı paylaşmanıza yardımcı olur. | yok |
| [Etkileşimli Pencere](interactive-repl-for-r-in-visual-studio.md) | Etkileşimli penceredeki bir kaynak dosyada kolayca kod çalıştırılabilmesini sağlayarak R ile tam REPL deneyimi sunar. | yok |
| [Verileri görselleştirme](visualizing-data-with-r-in-visual-studio.md) | Çizim, R deneyiminin ayrılmaz bir parçasıdır ve RTVS, her biri kendi geçmişine ve pencereler arasında çizimleri taşıyabilme yeteneğine sahip olan birden çok bağımsız çizim penceresini destekler. Çizimler bit eşlem ve PDF dosyalarına kaydedilebilir veya panoya bit eşlem ya da meta dosyası olarak kopyalanabilir.  | yok |
| [Değişken Gezgini](variable-explorer.md) | Sıralanabilir tabloları görüntüleme ve CSV’ye dışarı aktarma özelliği sayesinde, genel veya pakete özgü kapsamlarda değişkenleri inceleyin. | yok |
| [Tam özellikli hata ayıklama](debugging-r-in-visual-studio.md) | Etkileşimli pencereyle tümleştirmeyi içerir. | [Visual Studio’da hata ayıklama](../debugger/debugger-feature-tour.md) |

Ayrıca bkz. [Sık sorulan sorular](faq.md).

|   |   |
|---|---|
| ![video için kamera simgesi](../install/media/video-icon.png "Video izleyin") | Visual Studio için R Araçları’na genel bakış için [bir video (youtube.com) izleyin](https://www.youtube.com/watch?v=dll3IS1bfWQ) (12 dk 36 sn). Ayrıca bkz. [diğer R Araçları videoları](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Bize geri bildirimlerinizi gönderin!

1. **GitHub sorunları**: RTVS ekibine ulaşmanın en iyi yolu, [GitHub’da bir sorun kaydetmek](https://github.com/Microsoft/RTVS/issues) veya **R Araçları** > **Geri Bildirim** menüsünü kullanmaktır.

1. **Gülümseme/Asık Surat Gönderme**: **R Araçları** > **Geri Bildirim** menüsü, sorununuzun tanılanmasına yardımcı olması için geri bildirim göndermenin ve RTVS günlük dosyaları göndermenin hızlı bir yoludur. (Ayrı olarak göndermek istemeniz durumunda günlükler *%temp%/RTVSlogs.zip* dizinine yazılır.) Yükleme sırasında veya **Yardım** > **Geri Bildirim** > **Ayarlar** menü komutuyla Visual Studio telemetrisini geri çevirdiyseniz günlüğe kaydetme devre dışı bırakılır.

1. **E-posta**: *rtvsuserfeedback (at) microsoft.com* adresinden ekibe doğrudan geri bildirim gönderebilirsiniz.
