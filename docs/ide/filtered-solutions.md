---
title: Projelerin bir alt kümesini yükleme
description: Çözüm filtreleme hakkında bilgi ve çözümde projelerin bir alt kümesini hızla yükleme olanağını nasıl sağlar?
ms.custom: SEO-VS-2020
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: TerryGLee
ms.author: stsu
manager: jmartens
ms.technology: vs-ide-general
monikerRange: '>= vs-2019'
ms.openlocfilehash: 52c06a218c14fa09a6c879fa90805ddc48b22d8d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625923"
---
# <a name="filtered-solutions-in-visual-studio"></a>Visual Studio'da filtrelenmiş çözümler

Büyük geliştirme ekipleri genellikle birçok projeyle tek bir büyük çözüm kullanarak işbirliği yapıyor. Ancak, bireysel geliştiriciler genellikle bu projelerin küçük bir alt kümesi üzerinde çalışır. 2019'da büyük çözümler a Visual Studio performansı artırmak için çözüm *filtrelemesi tanıtıldı.* Çözüm filtreleme, yalnızca seçmeli projeler yüklenmiş bir çözüm açmana olanak sağlar. Bir çözümde projelerin bir alt kümesinin yüklenmesi çözüm yükünü, derlemeyi ve test çalıştırma sürelerini azaltarak daha odaklanmış bir gözden geçirme sağlar.

Aşağıdaki özellikler kullanılabilir:

- Herhangi bir projesini yüklemeden bir çözümü açarak daha hızlı koda sahip olabilirsiniz. Çözüm açıldıktan sonra, hangi projelerin yüklerini seçerek seçebilirsiniz.

- Bir çözümü yeniden Visual Studio önceki oturumda hangi projelerin yükleniyor olduğunu anımsar ve yalnızca bu projeleri yükler.

- Bir veya daha fazla proje yükleme yapılandırması kaydetmek veya yapılandırmayı ekip arkadaşlarınızla paylaşmak için bir çözüm filtresi dosyası oluşturabilirsiniz.

> [!NOTE]
> Bu konu, Visual Studio için Windows.

## <a name="open-a-filtered-solution"></a>Filtrelenmiş çözümü açma

Bir çözümü, projelerinden herhangi birini doğrudan Aç iletişim kutusundan **veya komut Project** yüklemeden [açabilirsiniz.](#command-line)

### <a name="open-project-dialog"></a>Açık Project iletişim kutusu

Herhangi bir projesini Yüklemeden Çözümü Aç iletişim kutusunu **kullanarak Project** için:

1. Menü   >  **çubuğundan**  >  **Dosya Project/Çözüm'i** seçin.

2. Açık Kaynak **Project** iletişim kutusunda çözümü seçin ve ardından Projeleri **yükleme'yi seçin.**

   ![Visual Studio Projeleri Project işaretli bir iletişim kutusu açın](media/filtered-solutions/do-not-load-projects.png)

3. **Aç'ı seçin.**

   Çözümün tüm projeleri kaldırılmış olarak açılır.

4. Bu **Çözüm Gezgini** yüklemek istediğiniz projeleri seçin (birden fazla proje seçmek için **tıklarken Ctrl tuşuna** basın) ve sonra projeye sağ tıklar ve Yeniden **Yükle'yi Project.**

   ![Visual Studio Çözüm Gezgini'da birden çok proje yeniden yükleme](media/filtered-solutions/reload-project.png)

   Visual Studio, çözümü yerel olarak bir sonraki açsanız hangi projelerin yükleniyor olduğunu anımsayabilirsiniz.

### <a name="command-line"></a>Komut satırı

(Visual Studio 2019 sürüm 16.1'de yeni.)

Projelerinden herhangi birini komut satırına yüklemeden bir çözümü açmak için, [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) aşağıdaki örnekte gösterildiği gibi anahtarını kullanın:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Kaldırılan proje görünürlüğünü değiştir

Çözümde yer alan tüm projeleri veya yalnızca yüklenen projeleri görmek için aşağıdaki seçeneklerden birini **Çözüm Gezgini:**

- Çözümünüze sağ tıklayın ve Kaldırılan Projeleri **Göster veya Kaldırılan** Projeleri **Gizle'yi seçin.**

- Tüm Dosyaları Göster düğmesini etkinleştirmek için **çözüm düğümünü** seçin; ardından, kaldırılan projelerin görünürlüğünü değiştirmek için düğmesine tıklayın.

   ![Tüm Dosyaları Göster düğmesi Visual Studio Çözüm Gezgini](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Proje bağımlılıklarını yükleme

Yalnızca seçili projelerin yükleniyor olduğu bir çözümde, projenin tüm proje bağımlılıkları yüklenmemiş olabilir. Bir projenin **bağımlı olduğu tüm projelerin** de yüklendiğinden emin olmak için Proje bağımlılıklarını yükle menü seçeneğini kullanın. Içinde yüklü bir veya daha fazla projeye sağ tıklayın **Çözüm Gezgini** **Proje bağımlılıklarını yükle'yi seçin.**

![Visual Studio 2019'da proje bağımlılıklarını yükleme](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Çözüm filtresi dosyaları

Proje yükleme yapılandırmanızı paylaşmak veya kaynak denetimine işlemek için bir çözüm filtre dosyası oluşturabilirsiniz *(.slnf uzantısına sahip).* Bir çözüm filtresi dosyasını açtığınız zaman, çözüm belirtilen Visual Studio ve tüm yüklenmemiş projelerin gizlenmiş olduğu bir yerde açılır. Kaldırılan [projeleri](#toggle-unloaded-project-visibility) görüntülemek için iki durumlu düğmeyi abilirsiniz.

Çözüm filtresi dosyaları, normal çözüm dosyalarından görsel olarak, içinde çözümün yanındaki simgede yer alan ek huni **Çözüm Gezgini.** Filtrenin adı ve yüklenen proje sayısı çözüm adının yanında da gösterilir.

![Çözüm filtresi dosyası Visual Studio Çözüm Gezgini](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Çözüm filtre dosyasını oluşturduk sonra özgün çözüme yeni projeler eklenirse, bu projeler dosyasında kaldırılmış projeler **Çözüm Gezgini.**

### <a name="create-a-solution-filter-file"></a>Çözüm filtre dosyası oluşturma

1. Bu **Çözüm Gezgini** çözümüne sağ tıklayın ve Çözüm Filtresi Olarak **Kaydet'i seçin.**

   ![Visual Studio Çözüm Gezgini'de Çözüm Filtresi Olarak Kaydet menüsü](media/filtered-solutions/save-as-solution-filter.png)

2. Çözüm filtresi dosyası için bir ad ve konum seçin.

Bir çözüm filtresi dosyası oluşturdukta, kolay erişim için Son Projeler **ve Çözümler** listenize eklenir:

![En son Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözüm Gezgini’nde dosya iç içe yerleştirmeyi özelleştirme](file-nesting-solution-explorer.md)
- [Visual Studio performansını iyileştirme](optimize-visual-studio-performance.md)
