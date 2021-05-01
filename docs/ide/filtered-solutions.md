---
title: Projelerin bir alt kümesini yükleme
description: Çözüm filtreleme ve bir çözümdeki projelerin alt kümesini hızlı bir şekilde yüklemenize nasıl izin verdiği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 04/22/2019
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: TerryGLee
ms.author: stsu
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 3fc64b5f0623a03443278eaa8e4ee1f47b86da38
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217203"
---
# <a name="filtered-solutions-in-visual-studio"></a>Visual Studio 'da filtrelenmiş çözümler

Büyük geliştirme ekipleri genellikle birçok projeyle tek bir büyük çözüm kullanarak işbirliği yapabilirler. Ancak, bireysel geliştiriciler genellikle bu projelerin küçük bir alt kümesinde çalışır. Büyük çözümleri açarken performansı artırmak için, Visual Studio 2019 *çözüm filtrelemesini* sunmuştur. Çözüm filtreleme, yalnızca seçmeli projelerle yüklenmiş bir çözüm açmanıza olanak tanır. Bir çözümdeki projelerin alt kümesini yüklemek çözüm yükünü, derlemeyi ve test çalışma süresini azaltır ve daha odaklanmış gözden geçirmeyi mümkün bir şekilde sunar.

Aşağıdaki özellikler mevcuttur:

- Projelerini yüklemeden bir çözümü açarak kodu daha hızlı bir şekilde alabilirsiniz. Çözüm açıldıktan sonra, hangi projelerin yükleneceğini seçmeli olarak seçebilirsiniz.

- Bir çözümü yeniden açtığınızda, Visual Studio önceki oturumunuzda hangi projelerin yüklendiğini anımsar ve yalnızca bu projeleri yükler.

- Bir veya daha fazla proje yük yapılandırması kaydetmek veya yapılandırmayı takım Mates ile paylaşmak için bir çözüm filtresi dosyası oluşturabilirsiniz.

## <a name="open-a-filtered-solution"></a>Filtrelenmiş bir çözüm açın

Projelerini doğrudan **Proje Aç** iletişim kutusundan veya [komut satırı](#command-line)aracılığıyla yüklemeden bir çözüm açabilirsiniz.

### <a name="open-project-dialog"></a>Proje Aç iletişim kutusu

**Proje Aç** iletişim kutusunu kullanarak herhangi bir projeyi yüklemeden bir çözüm açmak için:

1. Menü çubuğundan **Dosya**  >  **Aç**  >  **Proje/çözüm** öğesini seçin.

2. **Proje Aç** iletişim kutusunda çözümü seçin ve ardından **Proje yükleme**' yi seçin.

   ![Visual Studio proje yükleme iletişim kutusu açık projeler işaretlendi](media/filtered-solutions/do-not-load-projects.png)

3. **Aç**' ı seçin.

   Çözüm, tüm projeleri bellekten kaldırılmış olarak açılır.

4. **Çözüm Gezgini**, yüklemek istediğiniz projeleri seçin (birden fazla proje seçmek için **CTRL** tuşuna basın) ve ardından projeye sağ tıklayıp **projeyi yeniden yükle**' yi seçin.

   ![Visual Studio 'da birden çok projeyi yeniden yükleme Çözüm Gezgini](media/filtered-solutions/reload-project.png)

   Visual Studio, çözümü yerel olarak ilk açışınızda hangi projelerin yükleneceğini hatırlayacaktır.

### <a name="command-line"></a>Komut satırı

(Visual Studio 2019 sürüm 16,1 ' de yenidir.)

Bir çözümü komut satırından yüklemeden açmak için [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) Aşağıdaki örnekte gösterildiği gibi anahtarı kullanın:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Kaldırılmış proje görünürlüğünü değiştirme

**Çözüm Gezgini**' de aşağıdaki seçeneklerden birini kullanarak Çözümdeki tüm projeleri ya da yalnızca yüklü olanları görmeyi seçebilirsiniz:

- Çözümünüze sağ tıklayın ve **kaldırılmış projeleri göster** ' i seçin veya **yüklü olmayan projeleri gizleyin**.

- **Tüm dosyaları göster** düğmesini etkinleştirmek için çözüm düğümünü seçin; ardından, yüklenmeyen projelerin görünürlüğünü değiştirmek için düğmeye tıklayın.

   ![Visual Studio 'da tüm dosyalar düğmesini göster Çözüm Gezgini](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Proje bağımlılıklarını yükle

Yalnızca seçili projelerin yüklendiği bir çözümde, projenin tüm proje bağımlılıkları yüklü olmayabilir. Projenin bağımlı olduğu projelerin de yüklü olduğundan emin olmak için **Proje bağımlılıklarını yükle** menü seçeneğini kullanın. **Çözüm Gezgini** yüklenen bir veya daha fazla projeye sağ tıklayın ve **Proje bağımlılıklarını yükle**' yi seçin.

![Visual Studio 2019 ' de Proje bağımlılıklarını yükle](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Çözüm filtresi dosyaları

Proje yük yapılandırmanızı paylaşmak veya kaynak denetimine uygulamak istiyorsanız, bir çözüm filtresi dosyası ( *. slnf* uzantısına sahiptir) oluşturabilirsiniz. Bir çözüm filtresi dosyası açtığınızda, çözüm Visual Studio 'da belirtilen projelerle yüklendi ve tüm yüklenmemiş projeler gizli olarak açılır. Yüklü projeleri görüntülemek için [geçiş](#toggle-unloaded-project-visibility) yapabilirsiniz.

Çözüm filtresi dosyaları, normal çözüm dosyalarından, **Çözüm Gezgini** çözümünün yanında bulunan simgenin yanındaki ek huni glifinin görsel açıdan farklılaştırılabilir. Filtrenin adı ve yüklenen proje sayısı, çözüm adının yanında da gösterilir.

![Visual Studio 'da çözüm filtresi dosyası açık Çözüm Gezgini](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Çözüm filtresi dosyasını oluşturduktan sonra özgün çözüme yeni projeler eklendiyse, bunlar **Çözüm Gezgini**' de kaldırılmış projeler olarak görünürler.

### <a name="create-a-solution-filter-file"></a>Çözüm filtresi dosyası oluşturma

1. **Çözüm Gezgini**, çözüme sağ tıklayıp **çözüm filtresi olarak kaydet**' i seçin.

   ![Visual Studio 'da çözüm filtresi menüsü olarak kaydet Çözüm Gezgini](media/filtered-solutions/save-as-solution-filter.png)

2. Çözüm filtresi dosyası için bir ad ve konum seçin.

Bir çözüm filtresi dosyası oluşturduktan sonra, kolay erişim için **son projeleriniz ve çözüm** listenize eklenir:

![Visual Studio 'da Son Kullanılanı Aç](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözüm Gezgini’nde dosya iç içe yerleştirmeyi özelleştirme](file-nesting-solution-explorer.md)
- [Visual Studio performansını iyileştirme](optimize-visual-studio-performance.md)
