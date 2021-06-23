---
title: Projelerin Visual Studio çözümleri & nedir?
description: Proje ve Visual Studio, şablondan yeni projeler oluşturma ve proje yönetimi ile ilgili & görüntüleme hakkında Çözüm Gezgini.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/31/2020
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61cc760eb34df7f643bbdc16607f2316e92785bf
ms.sourcegitcommit: 40646cd90ca0701c034311931f026cf67edb74de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2021
ms.locfileid: "112500896"
---
# <a name="what-are-solutions-and-projects-in-visual-studio"></a>Bu hizmette çözümler ve projeler Visual Studio?

Bu makalede, bir projenin ve *çözümün* nasıl bir çözüm *olduğunu* Visual Studio. Ayrıca araç penceresinin Çözüm Gezgini ve yeni proje oluşturma hakkında da bilgi edinebilirsiniz.

> [!NOTE]
> Bu konu Windows'Visual Studio için geçerlidir. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio'de projeler ve çözümler.](/visualstudio/mac/projects-and-solutions)

## <a name="projects"></a>Projeler

Uygulama veya web sitesi oluşturmak için Visual Studio projesiyle *başlarsiniz.* Mantıksal anlamda bir proje yürütülebilir dosya, kitaplık veya web sitesinde derlenmiş olan tüm dosyaları içerir. Bu dosyalar kaynak kodu, simgeler, görüntüler, veri dosyaları gibi dosyaları içerebilir. Proje ayrıca derleyici ayarlarını ve programla iletişim kuran çeşitli hizmetler veya bileşenler için gerekebilecek diğer yapılandırma dosyalarını içerir.

### <a name="project-file"></a>Proje dosyası

Visual Studio bir [çözümde her](../msbuild/msbuild.md) projeyi derlemek için MSBuild kullanır ve her proje bir MSBuild proje dosyası içerir. Dosya uzantısı, bir C# projesi (.csproj), bir Visual Basic projesi (.vbproj) veya veritabanı projesi (.dbproj) gibi proje türünü gösterir. Proje dosyası; içerik, platform gereksinimleri, sürüm oluşturma bilgileri, web sunucusu veya veritabanı sunucusu ayarları ve gerçekleştirecek görevler de dahil olmak üzere projenizi derlemek için MSBuild'e gereken tüm bilgileri ve yönergeleri içeren bir XML belgesidir.

Proje dosyaları [MSBuild XML şemasını temel alan dosyalardır.](../msbuild/msbuild-project-file-schema-reference.md) Yeni, [sdk](../msbuild/how-to-use-project-sdk.md) stili proje dosyalarının içeriğine bakmak için Visual Studio içindeki proje düğümüne sağ tıklayın ve **Çözüm Gezgini'yi seçin. \<projectname\>**  Bu stildeki .NET Framework ve diğer projelerin içeriğine bakmak için, önce projeyi kaldır (projedeki proje düğümüne sağ tıklayın ve **Projeyi Kaldır'ı Çözüm Gezgini** **seçin).** Ardından projeye sağ tıklayın ve Düzenle'yi **seçin. \<projectname\>**

> [!NOTE]
> Kodu düzenlemek, derlemek ve hata ayıklamak Visual Studio çözümler veya projeler kullanmak zorunda değilsiniz. Kaynak dosyalarınızı içeren klasörü tek yapmanız gereken Visual Studio düzenlemeye başlamaktır. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

### <a name="create-new-projects"></a>Yeni projeler oluştur

Yeni proje oluşturmanın en kolay yolu, istediğiniz proje türü için bir proje şablonu kullanmaktır. Proje şablonu, önceden oluşturulmuş kod dosyaları, yapılandırma dosyaları, varlıklar ve ayarlardan oluşturulmuş temel bir küme içerir. Proje **şablonu**  >  **seçmek**  >  **için** Dosya Yeni Proje'yi kullanın. Daha fazla bilgi için [bkz. Yeni proje oluşturma.](create-new-project.md)

Ayrıca, yeni projeler oluşturmak için kullanabileceğiniz özel bir proje şablonu da oluşturabilirsiniz. Daha fazla bilgi için [bkz. Proje ve öğe şablonları oluşturma.](../ide/creating-project-and-item-templates.md)

Yeni bir proje oluşturmadan önce Visual Studio *%USERPROFILE%\source\repos* konumundaki varsayılan konuma kaydeder. Bu konumu değiştirmek için Araçlar Seçenekler Projeleri  >  **ve Çözümler**  >  **Konumları'ne**  >  **gidin.** Daha fazla bilgi için [bkz. Seçenekler iletişim kutusu: Projeler ve Çözümler >.](./reference/projects-solutions-locations-options.md)

## <a name="solutions"></a>Çözümler

Bir proje bir çözümün içinde *yer alan bir projedir.* Adına rağmen çözüm bir "yanıt" değildir. Yalnızca bir veya daha fazla ilgili projenin kapsayıcısı, derleme bilgileri, Visual Studio penceresi ayarları ve belirli bir projeyle ilişkili olmayan çeşitli dosyalar.

### <a name="solution-file"></a>Çözüm dosyası

Visual Studio için ayarları depolamak için iki dosya türü *(.sln* ve *.suo*) kullanılır:

|Dahili numara|Ad|Açıklama|
|---------------|----------|-----------------|
|Sln|Visual Studio Çözümü|Çözümdeki projeleri, proje öğelerini ve çözüm öğelerini düzenleme.|
|.suo|Çözüm Kullanıcı Seçenekleri|Kesme noktaları gibi kullanıcı düzeyinde ayarları ve özelleştirmeleri depolar.|

> [!IMPORTANT]
> Çözüm, kendi benzersiz biçimine sahip bir metin dosyası *(.sln* uzantısı) ile açıklanmıştır; El ile düzenlemek amaçlanmaz. Buna karşılık, *.suo* dosyası varsayılan dosya adı ayarları altında görüntülenmez gizli Dosya Gezgini olur. Gizli dosyaları göstermek için, **Dosya Gezgini** menüsünde Gizli Öğeler **onay kutusunu** seçin.

### <a name="solution-folder"></a>Çözüm klasörü

"Çözüm klasörü", yalnızca Çözüm Gezgini içinde yer alan ve bir çözümdeki projeleri grup oluşturmak için kullanabileceğiniz sanal bir klasördür. Bir bilgisayarda bir çözüm dosyası bulmak için Araçlar Seçenekler Projeleri **ve** Çözümler  >    >  **Konumları'ne**  >  **gidin.** Daha fazla bilgi için [bkz. Seçenekler iletişim kutusu: Projeler ve Çözümler >.](./reference/projects-solutions-locations-options.md)

> [!TIP]
> Sıfırdan oluşturulan bir proje ve çözüm örneği için, adım adım yönergeler ve örnek kod ile eksiksiz bir örnek için [bkz. Projelere ve çözümlere giriş.](../get-started/tutorial-projects-solutions.md)

## <a name="solution-explorer"></a>Çözüm Gezgini

Yeni bir proje oluşturdukta, projeyi ve **Çözüm Gezgini** ilgili öğelerini görüntülemek ve yönetmek için Çözüm Gezgini'i kullanabilirsiniz. Aşağıdaki çizimde, **Çözüm Gezgini** proje içeren bir C# çözümüne sahip bir çözüm gösterilmiştir:

::: moniker range="vs-2017"

![İki proje Çözüm Gezgini ekran görüntüsü.](../ide/media/vs2015_solution_explorer.png)

Üst kısmında yer alan **araç Çözüm Gezgini** bir çözüm görünümünden klasör görünümüne geçme, gizli dosyaları gösterme, tüm düğümleri daralt ve daha birçok düğme içerir.

::: moniker-end

::: moniker range=">=vs-2019"

![İki Çözüm Gezgini projenin yer alan ekran Visual Studio.](../ide/media/solution-explorer.png)

**Çözüm Gezgini** üst kısmında yer alan araç çubuğunda çözüm görünümünden klasör görünümüne geçme, bekleyen değişiklikleri filtreleme, tüm dosyaları [](managing-project-and-solution-properties.md) gösterme, tüm düğümleri [](writing-code-in-the-code-and-text-editor.md)daraltma, özellik sayfalarını görüntüleme, kod düzenleyicisinde kodu önizleme ve daha birçok düğme bulunur.

::: moniker-end

Birçok menü komutu, öğesinde bulunan çeşitli öğelerde sağ tıklama bağlam **menüsünden Çözüm Gezgini.** Bu komutlar arasında proje, NuGet paketlerini yönetme, başvuru ekleme, dosyayı yeniden adlandırma ve test çalıştırma yer almaktadır.

ASP.NET Core projeleri için, dosyaların içinde nasıl iç içe **Çözüm Gezgini.** Daha fazla bilgi için [bkz. Dosya iç içe yerleştirmeyi Çözüm Gezgini.](file-nesting-solution-explorer.md)

> [!TIP]
> Dosyayı kapattıysanız Çözüm Gezgini yeniden açmak için menü çubuğundan Görünüm Çözüm Gezgini'yi seçin veya  >   Ctrl Alt L  + **tuşlarına** + **basın.** Ayrıca, yan sekmeleri kapattıysanız ve bunları varsayılan konumlarına geri yüklemek için menü çubuğundan **Pencere** Sıfırlama Penceresi  >  **Düzeni'ne** tıklayın.

> [!NOTE]
> Uygulamasında görünen uygulama görüntülerini ve simgelerini görüntülemek Visual Studio Görüntü [**Kitaplığı'Visual Studio indirin.**](https://www.microsoft.com/download/details.aspx?id=35825)

## <a name="see-also"></a>Ayrıca bkz.

- [Projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Verilerde filtrelenmiş Visual Studio](filtered-solutions.md)
- [Projeleri taşıma, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [IDE hatalarını Visual Studio kaynakları](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Projeler ve çözümler (Mac için Visual Studio)](/visualstudio/mac/projects-and-solutions)
