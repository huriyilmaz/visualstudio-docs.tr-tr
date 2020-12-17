---
title: Çözümler ve projelere genel bakış
description: Visual Studio projeleri ve çözümleri hakkında, bir şablondan yeni projeler oluşturma ve Çözüm Gezgini projeleri görüntüleme & yönetme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 12/15/2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1981bc5c9d1c2589607f355528c332d01284917e
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615759"
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

## <a name="solutions"></a>Çözümler

Bir proje bir *çözüm* içinde yer alır. Adına rağmen çözüm bir "yanıt" değildir. Yalnızca bir veya daha fazla ilişkili projenin kapsayıcısı, derleme bilgileri, Visual Studio pencere ayarları ve belirli bir projeyle ilişkilendirilmemiş çeşitli dosyalar için bir kapsayıcıdır. Bir çözüm, bir metin dosyası (uzantısı *. sln*) tarafından kendine özgü benzersiz biçimde tanımlanır; el ile düzenlenmesi amaçlanmamıştır.

### <a name="solution-file"></a>Çözüm dosyası

Visual Studio, çözümlerin ayarlarını depolamak için iki dosya türü (*. sln* ve *. suo*) kullanır:

|Dahili numara|Ad|Açıklama|
|---------------|----------|-----------------|
|. sln|Visual Studio çözümü|Çözümdeki projeleri, proje öğelerini ve çözüm öğelerini düzenler.|
|. suo|Çözüm Kullanıcı seçenekleri|Kesme noktaları gibi kullanıcı düzeyindeki ayarları ve özelleştirmeleri depolar.|

### <a name="solution-folder"></a>Çözüm klasörü

Bir "Çözüm klasörü", yalnızca **Çözüm Gezgini** olan ve bir çözümdeki projeleri gruplamak için kullanabileceğiniz sanal bir klasördür. Bir bilgisayarda çözüm dosyası bulmak istiyorsanız, **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **konumlar**' a gidin. Daha fazla bilgi için bkz. [Seçenekler iletişim kutusu: projeler ve çözümler > konumları](./reference/projects-solutions-locations-options.md).

## <a name="create-new-projects"></a>Yeni projeler oluştur

Yeni bir proje oluşturmanın en kolay yolu, istediğiniz proje türü için bir proje şablonu kullanmaktır. Proje şablonu, önceden oluşturulmuş temel bir kod dosyaları, yapılandırma dosyaları, varlıklar ve ayarlar kümesi içerir. **Dosya**  >  **Yeni**  >  **Proje** ' yi kullanarak bir proje şablonu seçin. Daha fazla bilgi için bkz. [Yeni proje oluşturma](create-new-project.md).

Ayrıca, ' den yeni projeler oluşturmak için kullanabileceğiniz özel bir proje şablonu da oluşturabilirsiniz. Daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

Yeni bir proje oluşturduğunuzda, Visual Studio onu varsayılan konumuna, *%userprofile%\source\repos dizinine* kaydeder. Bu konumu değiştirmek için **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **konumlar**' a gidin. Daha fazla bilgi için bkz. [Seçenekler iletişim kutusu: projeler ve çözümler > konumları](./reference/projects-solutions-locations-options.md).

## <a name="solution-explorer"></a>Çözüm Gezgini

Yeni bir proje oluşturduktan sonra, projeyi ve çözümü ve ilişkili öğelerini görüntülemek ve yönetmek için **Çözüm Gezgini** kullanabilirsiniz. Aşağıdaki çizimde, iki proje içeren bir C# çözümü ile **Çözüm Gezgini** gösterilmektedir:

![Çözüm Gezgini](../ide/media/vs2015_solution_explorer.png)

Birçok menü komutu, **Çözüm Gezgini** çeşitli öğelerde sağ tıklama menüsünde bulunur. Bu komutlar bir proje oluşturma, NuGet paketlerini yönetme, bir başvuru ekleme, bir dosyayı yeniden adlandırma ve Testleri çalıştırma, yalnızca birkaç kez adlandırma içerir. **Çözüm Gezgini** üstündeki araç çubuğunda, bir çözüm görünümünden klasör görünümüne geçiş yapmak, gizli dosyaları göstermek, tüm düğümleri daraltmak ve daha fazlası için düğmeler bulunur.

> [!TIP]
> Çözüm Gezgini kapattıysanız ve yeniden açmak istiyorsanız, menü çubuğundan **pencere**  >  **düzeni penceresini Sıfırla** ' yı seçin.

ASP.NET Core projeleri için, dosyaların **Çözüm Gezgini** nasıl iç içe yerleşdiğini özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Çözüm Gezgini dosya iç içe geçirmeyi özelleştirme](file-nesting-solution-explorer.md).

Çözüm Gezgini görünen simgelerin bir listesini görüntülemek için, bkz. [sınıf görünümü ve nesne tarayıcısı simgeleri](class-view-and-object-browser-icons.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Projeleri taşıma, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Projeler ve çözümler (Mac için Visual Studio)](/visualstudio/mac/projects-and-solutions)
