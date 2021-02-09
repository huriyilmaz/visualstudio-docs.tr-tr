---
title: Çözümler ve projeler hakkında bilgi edinin
description: Visual Studio projeleri ve çözümleri hakkında, bir şablondan yeni projeler oluşturma ve Çözüm Gezgini projeleri görüntüleme & yönetme hakkında bilgi edinin.
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
ms.openlocfilehash: 473c3ca0e4a9998d6a320e384bf39b4b5e037085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878506"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio 'da çözümler ve projeler

Bu sayfa, Visual Studio 'da bir *Proje* ve *çözüm* kavramını açıklar. Ayrıca Çözüm Gezgini araç penceresini ve yeni bir proje oluşturmayı kısaca ele alır.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için, bkz. [Mac için Visual Studio Içindeki projeler ve çözümler](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projeler

Visual Studio 'da bir uygulama veya Web sitesi oluşturduğunuzda bir *Proje* ile başlayabilirsiniz. Bir mantıksal anlamda, bir proje çalıştırılabilir, kitaplık veya Web sitesine derlenen tüm dosyaları içerir. Bu dosyalar, kaynak kodu, simgeler, resimler, veri dosyaları vb. içerebilir. Bir proje Ayrıca, programınızın iletişim kurduğu çeşitli hizmetler veya bileşenler tarafından gerekebilecek derleyici ayarlarını ve diğer yapılandırma dosyalarını da içerir.

### <a name="project-file"></a>Proje dosyası

Visual Studio, bir çözümde her projeyi derlemek için [MSBuild](../msbuild/msbuild.md) kullanır ve her proje bir MSBuild proje dosyası içerir. Dosya uzantısı, projenin türünü (örneğin, bir C# projesi (. csproj), Visual Basic projesi (. vbproj) veya veritabanı projesini (. dbproj) yansıtır. Proje dosyası, içerik, Platform gereksinimleri, sürüm bilgileri, Web sunucusu veya veritabanı sunucusu ayarları ve gerçekleştirilecek görevler de dahil olmak üzere projenizi derlemek için MSBuild 'in ihtiyaç duyacağı tüm bilgileri ve yönergeleri içeren bir XML belgesidir.

Proje dosyaları [MSBUILD XML şemasını](../msbuild/msbuild-project-file-schema-reference.md)temel alır. Visual Studio 'da daha yeni, [SDK stili proje dosyalarının](../msbuild/how-to-use-project-sdk.md) içeriğine bakmak için **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve **Düzenle \<projectname\>**' yi seçin. .NET Framework içeriğine ve bu stilin diğer projelerine bakmak için, önce projeyi kaldırın ( **Çözüm Gezgini** proje düğümüne sağ tıklayın ve **Projeyi Kaldır**' ı seçin). Ardından projeye sağ tıklayıp **Düzenle \<projectname\>**' yi seçin.

> [!NOTE]
> Kodu düzenlemek, derlemek ve hata ayıklamak için Visual Studio 'da çözüm veya proje kullanmanız gerekmez. Yalnızca kaynak dosyalarınızı içeren klasörü Visual Studio 'da açabilir ve düzenleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

### <a name="create-new-projects"></a>Yeni projeler oluştur

Yeni bir proje oluşturmanın en kolay yolu, istediğiniz proje türü için bir proje şablonu kullanmaktır. Proje şablonu, önceden oluşturulmuş temel bir kod dosyaları, yapılandırma dosyaları, varlıklar ve ayarlar kümesi içerir. **Dosya**  >  **Yeni**  >  **Proje** ' yi kullanarak bir proje şablonu seçin. Daha fazla bilgi için bkz. [Yeni proje oluşturma](create-new-project.md).

Ayrıca, ' den yeni projeler oluşturmak için kullanabileceğiniz özel bir proje şablonu da oluşturabilirsiniz. Daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

Yeni bir proje oluşturduğunuzda, Visual Studio onu varsayılan konumuna, *%userprofile%\source\repos dizinine* kaydeder. Bu konumu değiştirmek için **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **konumlar**' a gidin. Daha fazla bilgi için bkz. [Seçenekler iletişim kutusu: projeler ve çözümler > konumları](./reference/projects-solutions-locations-options.md).

## <a name="solutions"></a>Çözümler

Bir proje bir *çözüm* içinde yer alır. Adına rağmen çözüm bir "yanıt" değildir. Yalnızca bir veya daha fazla ilişkili projenin kapsayıcısı, derleme bilgileri, Visual Studio pencere ayarları ve belirli bir projeyle ilişkilendirilmemiş çeşitli dosyalar için bir kapsayıcıdır.

### <a name="solution-file"></a>Çözüm dosyası

Visual Studio, çözümlerin ayarlarını depolamak için iki dosya türü (*. sln* ve *. suo*) kullanır:

|Dahili numara|Ad|Açıklama|
|---------------|----------|-----------------|
|. sln|Visual Studio çözümü|Çözümdeki projeleri, proje öğelerini ve çözüm öğelerini düzenler.|
|. suo|Çözüm Kullanıcı seçenekleri|Kesme noktaları gibi kullanıcı düzeyindeki ayarları ve özelleştirmeleri depolar.|

> [!IMPORTANT]
> Bir çözüm, bir metin dosyası (uzantısı *. sln*) tarafından kendine özgü benzersiz biçimde tanımlanır; el ile düzenlenmesi amaçlanmamıştır. Buna karşılık, *. suo* dosyası varsayılan dosya Gezgini ayarları altında görüntülenmeyen gizli bir dosyadır. Gizli dosyaları göstermek için dosya Gezgini 'ndeki **Görünüm** menüsünde **gizli öğeler** onay kutusunu seçin.

### <a name="solution-folder"></a>Çözüm klasörü

Bir "Çözüm klasörü", yalnızca **Çözüm Gezgini** olan ve bir çözümdeki projeleri gruplamak için kullanabileceğiniz sanal bir klasördür. Bir bilgisayarda çözüm dosyası bulmak istiyorsanız, **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **konumlar**' a gidin. Daha fazla bilgi için bkz. [Seçenekler iletişim kutusu: projeler ve çözümler > konumları](./reference/projects-solutions-locations-options.md).

> [!TIP]
> Sıfırdan oluşturulmuş bir proje ve çözüm örneği için adım adım yönergeler ve örnek kodla birlikte, bkz. [projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md).

## <a name="solution-explorer"></a>Çözüm Gezgini

Yeni bir proje oluşturduktan sonra, projeyi ve çözümü ve ilişkili öğelerini görüntülemek ve yönetmek için **Çözüm Gezgini** kullanabilirsiniz. Aşağıdaki çizimde, iki proje içeren bir C# çözümü ile **Çözüm Gezgini** gösterilmektedir:

::: moniker range="vs-2017"

![İki projeyle Çözüm Gezgini ekran görüntüsü.](../ide/media/vs2015_solution_explorer.png)

**Çözüm Gezgini** üstündeki araç çubuğunda, bir çözüm görünümünden klasör görünümüne geçiş yapmak, gizli dosyaları göstermek, tüm düğümleri daraltmak ve daha fazlası için düğmeler bulunur.

::: moniker-end

::: moniker range="vs-2019"

![Visual Studio 2019 ' de iki projeyle Çözüm Gezgini ekran görüntüsü.](../ide/media/solution-explorer.png)

**Çözüm Gezgini** üst kısmında bulunan araç çubuğu, bir çözüm görünümünden klasör görünümüne geçiş yapmak, bekleyen değişiklikleri filtrelemek, tüm dosyaları göstermek, tüm düğümleri daraltmak, [özellik](managing-project-and-solution-properties.md) sayfalarını görüntülemek, [kod düzenleyicisinde](writing-code-in-the-code-and-text-editor.md)önizleme kodu ve daha fazlası için düğmeler içerir.

::: moniker-end

Birçok menü komutu, **Çözüm Gezgini** çeşitli öğelerde sağ tıklama bağlam menüsünden kullanılabilir. Bu komutlar bir proje oluşturma, NuGet paketlerini yönetme, bir başvuru ekleme, bir dosyayı yeniden adlandırma ve Testleri çalıştırma, yalnızca birkaç kez adlandırma içerir.

ASP.NET Core projeleri için, dosyaların **Çözüm Gezgini** nasıl iç içe yerleşdiğini özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Çözüm Gezgini dosya iç içe geçirmeyi özelleştirme](file-nesting-solution-explorer.md).

> [!TIP]
> Çözüm Gezgini kapattıysanız ve yeniden açmak istiyorsanız,   >  menü çubuğundan **Çözüm Gezgini** görüntüle ' yi seçin veya **CTRL** + **alt** + **L** tuşuna basın. Yan sekmeleri kapattıysanız ve bunları varsayılan konumlarına geri yüklemek istiyorsanız, menü çubuğundan **pencere**  >  **penceresini Sıfırla** ' yı seçin.

> [!NOTE]
> Visual Studio 'da görünen uygulama görüntülerini ve simgelerini görüntülemek için [**Visual Studio Görüntü Kitaplığı**](https://www.microsoft.com/download/details.aspx?id=35825)' nı indirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Projelere ve çözümlere giriş](../get-started/tutorial-projects-solutions.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Visual Studio 'da filtrelenmiş çözümler](filtered-solutions.md)
- [Projeleri taşıma, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio IDE hatalarında sorun giderme kaynakları](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Projeler ve çözümler (Mac için Visual Studio)](/visualstudio/mac/projects-and-solutions)