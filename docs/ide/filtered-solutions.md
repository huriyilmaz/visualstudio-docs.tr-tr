---
title: Projelerin bir alt kümesini yükleme
ms.date: 04/22/2019
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: jillre
ms.author: stsu
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4c44d267ef5686d04e9549601e05866aabbfb62d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72650844"
---
# <a name="filtered-solutions-in-visual-studio"></a>Visual Studio'da filtrelenmiş çözümler

Büyük geliştirme ekipleri genellikle birçok projeyle tek bir büyük çözüm kullanarak işbirliği yapmaktadır. Ancak, tek tek geliştiriciler genellikle bu projelerin küçük bir alt kümesi üzerinde çalışır. Büyük çözümleri açarken performansı artırmak için Visual Studio 2019 *çözüm filtrelemesini*tanıttı. Çözüm filtreleme, yalnızca seçici projeler yüklü bir çözüm açmanızı sağlar. Bir çözümde projelerin bir alt kümesinin yüklenmesi çözüm yükünü, oluşturmayı ve test çalışma süresini azaltır ve daha odaklı inceleme sağlar.

Aşağıdaki özellikler mevcuttur:

- Herhangi bir projeyüklemeden bir çözüm açarak koda daha hızlı ulaşabilirsiniz. Çözüm açıldıktan sonra, hangi projelerin yüklenmesini seçebilirsiniz.

- Bir çözümü yeniden açtığınızda, Visual Studio önceki oturumunuzda hangi projelerin yüklendiğini hatırlar ve bu projeleri yalnızca yükler.

- Bir veya daha fazla proje yükleme yapılandırmasını kaydetmek veya yapılandırmayı takım arkadaşlarıyla paylaşmak için bir çözüm filtresi dosyası oluşturabilirsiniz.

## <a name="open-a-filtered-solution"></a>Filtreuygulanmış bir çözüm açma

Projelerinden herhangi birini doğrudan **Open Project** iletişim kutusundan veya [komut satırından](#command-line)yüklemeden bir çözüm açabilirsiniz.

### <a name="open-project-dialog"></a>Proje iletişim kutusunu aç

**Proje Aç** iletişim kutusunu kullanarak projelerinden herhangi birini yüklemeden bir çözüm açmak için:

1. Menü çubuğundan **Dosya** > **Aç** > **Projesi/Çözümü'nü** seçin.

2. Proje **aç** iletişim kutusunda, çözümü seçin ve ardından **projeleri yükleme'yi**seçin.

   ![Visual Studio Open Project iletişim kutusu ile proje yükleme yitimi kontrol edildi](media/filtered-solutions/do-not-load-projects.png)

3. **Aç'ı**seçin.

   Çözüm, tüm projeleri boşaltıldı.

4. **Çözüm Gezgini'nde,** yüklemek istediğiniz projeleri seçin (birden fazla proje seçmek için tıklatırken **Ctrl** tuşuna basın) ve ardından projeye sağ tıklayın ve **Project'i Yeniden Yükle'yi**seçin.

   ![Visual Studio Solution Explorer'da birden fazla projeyi yeniden yükleme](media/filtered-solutions/reload-project.png)

   Visual Studio, çözümü yerel olarak bir sonraki açtığınızda hangi projelerin yüklendiğini hatırlayacaktır.

### <a name="command-line"></a>Komut satırı

(Visual Studio Yeni 2019 sürümü 16.1.)

Projelerinden herhangi birini komut satırından yüklemeden bir [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) çözüm açmak için, aşağıdaki örnekte gösterildiği gibi anahtarı kullanın:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Boşaltılmış proje görünürlüğünü geçişe kaydırma

**Çözüm**Gezgini'ndeki aşağıdaki seçeneklerden birini kullanarak tüm projeleri çözümde veya sadece yüklenen leri görmeyi seçebilirsiniz:

- Çözümünüzün üzerine sağ tıklayın ve **Boşaltılan Projeleri Göster'i** veya **Boşaltılan Projeleri Gizle'yi**seçin.

- **Tüm Dosyaları Göster** düğmesini etkinleştirmek için çözüm düğümünü seçin; ardından, boşaltılan projelerin görünürlüğünü geçiş için düğmeyi tıklatın.

   ![Visual Studio Solution Explorer'da Tüm Dosyaları Göster düğmesini göster](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Yük proje bağımlılıkları

Yalnızca seçili projelerin yüklendiği bir çözümde, projenin tüm proje bağımlılıklarının yüklenmemiş olması gerekmez. Projenin bağlı olduğu projelerin de yüklendiğinden emin olmak için **Yükle proje bağımlılıkları** menüsünü kullanın. **Solution Explorer'da** bir veya daha fazla yüklü projeye sağ tıklayın ve Yükle **proje bağımlılıklarını**seçin.

![Visual Studio 2019'da yük proje bağımlılıkları](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Çözüm filtresi dosyaları

Proje yükleme yapılandırmanızı paylaşmak veya kaynak denetimine işlemek istiyorsanız, bir çözüm filtresi dosyası oluşturabilirsiniz (uzantısı *.slnf).* Bir çözüm filtresi dosyasını açtığınızda, çözüm Visual Studio'da belirtilen projeler yüklenen ve tüm boşaltılan projeler gizlendiğinde açılır. Boşaltılan projeleri görüntülemek için [geçiş](#toggle-unloaded-project-visibility) yapabilirsiniz.

Çözüm filtresi dosyaları, **Solution Explorer'daki**çözümün yanındaki simgedeki ek huni glyph ile normal çözüm dosyalarından görsel olarak ayırt edilir. Filtrenin adı ve yüklenen proje sayısı da çözüm adının yanında gösterilir.

![Visual Studio Solution Explorer'da çözüm filtresi dosyası açıldı](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Çözüm filtresi dosyasını oluşturduktan sonra özgün çözüme yeni projeler eklenirse, **Çözüm Gezgini'nde**boş proje olarak görünürler.

### <a name="create-a-solution-filter-file"></a>Çözüm filtresi dosyası oluşturma

1. **Çözüm Gezgini'nde,** çözüme sağ tıklayın ve Çözüm Filtresi **Olarak Kaydet'i**seçin.

   ![Visual Studio Solution Explorer'da Çözüm Filtresi Olarak Kaydet menüsü](media/filtered-solutions/save-as-solution-filter.png)

2. Çözüm filtresi dosyası için bir ad ve konum seçin.

Bir çözüm filtresi dosyası oluşturduktan sonra, kolay erişim için **Son Projeler ve Çözümler** listenize eklenir:

![Son zamanlarda Visual Studio'da açık](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözüm Gezgini’nde dosya iç içe yerleştirmeyi özelleştirme](file-nesting-solution-explorer.md)
- [Visual Studio performansını iyileştirme](optimize-visual-studio-performance.md)
