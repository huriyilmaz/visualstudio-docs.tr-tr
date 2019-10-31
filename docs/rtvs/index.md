---
title: Visual Studio için R Araçları
description: Visual Studio için R Araçları 2017 (RTVS), IntelliSense, hata ayıklama ve uzak çalışma alanları gibi birçok dil özelliği sağlayan ücretsiz, açık kaynaklı bir uzantıdır.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 1132a7a0363e2d508d6eff1026192aad3407fca4
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189246"
---
# <a name="work-with-r-in-visual-studio"></a>Visual Studio 'da R ile çalışma

R, istatistiksel bilgi işlem ve grafik için yüksek düzeyde genişletilebilir bir dildir. Bu, GNU Genel Kamu Lisansı kapsamında ücretsiz olarak dağıtılır, daha güçlü bir topluluk desteği sağlar ve matematik sembolleri ve formül dahil olmak üzere yayın kalitesi çizimleri üretme özelliği için bilinmektedir. R hakkında daha fazla bilgi için [r-Project.org](https://www.r-project.org/about.html) adresinden ve [r 'ye giriş](https://cran.r-project.org/doc/manuals/r-release/R-intro.html)yapabilirsiniz.

Visual Studio için R Araçları (RTVS), MıT lisansı kapsamında yayınlanan Visual Studio 2017 ve Visual Studio 2015 güncelleştirme 3 (veya üzeri) için ücretsiz, [Açık kaynaklı](https://github.com/microsoft/RTVS) bir uzantıdır. (R yorumlayıcı ikilileriyle bağlantı sağlayan, [rhost](https://github.com/microsoft/R-Host)adlı ikinci bir açık kaynaklı BILEŞEN, GNU Genel lisans v2 altında yayımlanmıştır.)

> [!Note]
> RTVS, şu anda yalnızca Windows üzerinde Visual Studio 2017 ' de desteklenir ve Mac için Visual Studio. Visual Studio 2019 için kullanılamaz.

Visual Studio 'da R deneyimi için:

- [R araçları 'Nı yükler](installing-r-tools-for-visual-studio.md).
- [Kullanmaya](getting-started-with-r.md) başlama kılavuzunu, [örnekleri](getting-started-samples.md) ve [yardım makalelerini alma](getting-started-help.md) makalesini izleyin.

Ardından, R ile ilgili özelliklerin yanı sıra Visual Studio 'nun genel özellikleri hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıları izleyin.

| Özellik | Açıklama | Genel Visual Studio belgeleri |
| --- | --- | --- |
| [Visual Studio proje sistemi](r-projects-in-visual-studio.md) | Uygun bir yapıda ilgili dosyaları düzenleyin ve yönetin ve R Code, R documentation, R Markdown, SQL sorguları ve saklı yordamlar gibi öğeler için faydalı şablonlardan yararlanın. Ayrıca, [Paket Yöneticisi](r-package-manager-in-visual-studio.md) ve [SQL Server tümleştirmesini](integrating-sql-server-with-r.md)da yaşayın.  | [Visual Studio’da Çözümler ve Projeler](../ide/solutions-and-projects-in-visual-studio.md) |
| [Alanında](r-workspaces-in-visual-studio.md) | RTVS, yerel ve uzak çalışma alanlarına bağlanıp daha küçük veri kümeleriyle R kodu geliştirebilir, daha sonra kodu daha büyük veri kümelerine sahip daha güçlü bulut tabanlı bilgisayarlarda kolayca çalıştırmanıza olanak sağlar. | yok |
| [R araçları seçenekleri](options-for-r-tools-in-visual-studio.md) | RTVS 'nin çeşitli yönlerini denetleyin. | [Seçenekler iletişim kutusu](../ide/reference/options-dialog-box-visual-studio.md) |
| [Zengin düzenlemeler, IntelliSense ve kod parçacıkları](editing-r-code-in-visual-studio.md) | Sözdizimi renklendirme, tüm kod ve kitaplıklarınızda [IntelliSense](r-intellisense.md) , kod biçimlendirme, imza yardımı, tanıma git, tüm başvuruları bul, [kod parçacıkları](code-snippets-for-r.md)ve daha fazlasını içerir. | [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | R Markdown belgeler, markaşağı kod blokları içinde Tümleşik R kodu ile veri sonuçlarınızı paylaşmanıza yardımcı olur. | yok |
| [Etkileşimli pencere](interactive-repl-for-r-in-visual-studio.md) | Etkileşimli penceredeki bir kaynak dosyada kolayca kod çalıştırmak için R için tam bir REPL deneyimi sağlar. | yok |
| [Verileri görselleştirme](visualizing-data-with-r-in-visual-studio.md) | Çizim, R deneyiminin ayrılmaz bir parçasıdır ve RTVS, her biri kendi geçmişi ve pencereler arasında çizimler taşıyabilme gibi birden çok bağımsız çizim pencerelerini destekler. Çizimler bit eşlem ve PDF dosyalarına kaydedilebilir veya panoya bir bit eşlem veya meta dosyası olarak kopyalanabilir.  | yok |
| [Değişken Gezgini](variable-explorer.md) | Sıralanabilir tabloları görüntüleme ve CSV 'ye aktarma özelliği sayesinde, genel veya pakete özgü kapsamların değişkenlerini inceleyin. | yok |
| [Tam özellikli hata ayıklama](debugging-r-in-visual-studio.md) | Etkileşimli pencereyle tümleştirmeyi içerir. | [Visual Studio’da hata ayıklama](../debugger/debugger-feature-tour.md) |

Ayrıca [sık sorulan sorular](faq.md)bölümüne bakın.

|   |   |
|---|---|
| ![video için film kamerası simgesi](../install/media/video-icon.png "Video izleyin") | Visual Studio için R Araçları (12gb 36S) genel bakışı için [bir video (YouTube.com) izleyin](https://www.youtube.com/watch?v=dll3IS1bfWQ) . Ayrıca bkz. [diğer R araçları videoları](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Görüşlerinizi bize gönderin!

1. **GitHub sorunları**: rtvs ekibine ulaşmak için en iyi yol, [GitHub 'da bir sorunu dosyalayarak](https://github.com/Microsoft/RTVS/issues)veya **R araçları** > **geri bildirim** menüsünü kullanarak.

1. **Gülümseme/kaş çatma Gönder n**: **R araçları** > **geri bildirim** menüsü, geri bildirimde bulunmak ve sorunu tanılamaya yardımcı olmak için rtvs günlük dosyaları iliştirmek için hızlı bir yoldur. (Günlükler ayrı olarak göndermek istemeniz durumunda *% Temp%/RTVSlogs.zip* dosyasına yazılır.) **Yardım** > **geri bildirim** > **ayarları** menü komutu aracılığıyla veya yükleme sırasında Visual Studio telemetrisini devre dışı bıraktığınız takdirde günlüğe kaydetme devre dışıdır.

1. **E-posta**: *rtvsuserfeedback (at) Microsoft.com*adresinden ekibe doğrudan geri bildirim gönderebilirsiniz.
