---
title: Çözümler ve projeler
ms.date: 10/05/2017
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
ms.openlocfilehash: ffa561667ea31f215306c7cac4b9820d7b386b5c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590091"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio 'da çözümler ve projeler

Bu sayfa, Visual Studio 'da bir *Proje* ve *çözüm* kavramını açıklar. Ayrıca Çözüm Gezgini araç penceresini ve yeni bir proje oluşturmayı kısaca ele alır.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için, bkz. [Mac için Visual Studio Içindeki projeler ve çözümler](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projeler

Visual Studio 'da bir uygulama veya Web sitesi oluşturduğunuzda bir *Proje*ile başlayabilirsiniz. Bir mantıksal anlamda, bir proje çalıştırılabilir, kitaplık veya Web sitesine derlenen tüm dosyaları içerir. Bu dosyalar, kaynak kodu, simgeler, resimler, veri dosyaları vb. içerebilir. Bir proje Ayrıca, programınızın iletişim kurduğu çeşitli hizmetler veya bileşenler tarafından gerekebilecek derleyici ayarlarını ve diğer yapılandırma dosyalarını da içerir.

### <a name="project-file"></a>Proje dosyası

Visual Studio, bir çözümde her projeyi derlemek için [MSBuild](../msbuild/msbuild.md) kullanır ve her proje bir MSBuild proje dosyası içerir. Dosya Uzantısı proje türünü (örneğin, bir C# proje (. csproj), Visual Basic projesi (. vbproj) veya veritabanı projesini (. dbproj) yansıtır. Proje dosyası, projenizi derlemek için içerik, Platform gereksinimleri, sürüm bilgileri, Web sunucusu veya veritabanı sunucusu ayarları, ve görevleri dahil olmak üzere, MSBuild 'in ihtiyaç duyacağı tüm bilgileri ve yönergeleri içeren bir XML belgesidir. gerçekleştirirken.

Proje dosyaları [MSBUILD XML şemasını](../msbuild/msbuild-project-file-schema-reference.md)temel alır. Visual Studio 'da daha yeni, [SDK stili proje dosyalarının](../msbuild/how-to-use-project-sdk.md) içeriğine bakmak için, **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve **\<ProjectName\>Düzenle** ' yi seçin. .NET Framework içeriğine ve bu stilin diğer projelerine bakmak için, önce projeyi kaldırın ( **Çözüm Gezgini** proje düğümüne sağ tıklayın ve **Projeyi Kaldır**' ı seçin). Ardından projeye sağ tıklayıp **\<projectname\>Düzenle** ' yi seçin.

> [!NOTE]
> Kodu düzenlemek, derlemek ve hata ayıklamak için Visual Studio 'da çözüm veya proje kullanmanız gerekmez. Yalnızca kaynak dosyalarınızı içeren klasörü Visual Studio 'da açabilir ve düzenleyebilirsiniz. Daha fazla bilgi için [kod Visual Studio'da projeler veya çözümler olmadan geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Çözümler

Bir proje bir *çözüm*içinde yer alır. Adına rağmen çözüm bir "yanıt" değildir. Yalnızca bir veya daha fazla ilişkili projenin kapsayıcısı, derleme bilgileri, Visual Studio pencere ayarları ve belirli bir projeyle ilişkilendirilmemiş çeşitli dosyalar için bir kapsayıcıdır. Bir çözüm, bir metin dosyası (uzantısı *. sln*) tarafından kendine özgü benzersiz biçimde tanımlanır; el ile düzenlenmesi amaçlanmamıştır.

Visual Studio, çözümlerin ayarlarını depolamak için iki dosya türü ( *. sln* ve *. suo*) kullanır:

|Uzantı|Name|Açıklama|
|---------------|----------|-----------------|
|.sln|Visual Studio Çözümü|Çözümdeki projeleri, proje öğelerini ve çözüm öğelerini düzenler.|
|. suo|Çözüm Kullanıcı seçenekleri|Kesme noktaları gibi kullanıcı düzeyindeki ayarları ve özelleştirmeleri depolar.|

## <a name="create-new-projects"></a>Yeni projeler oluştur

Yeni bir proje oluşturmanın en kolay yolu, belirli bir uygulama veya Web sitesi türü için proje şablonundan başlamadır. Proje şablonu, önceden oluşturulmuş temel bir kod dosyaları, yapılandırma dosyaları, varlıklar ve ayarlar kümesinden oluşur. Bu şablonlar, yeni bir proje oluşturduğunuz (**dosya** > **Yeni** > **projesi**) iletişim kutusunda kullanılabilir. Daha fazla bilgi için bkz. [Visual Studio 'da yeni proje oluşturma](create-new-project.md) ve [çözüm ve proje oluşturma](../ide/creating-solutions-and-projects.md).

Projelerinizi genellikle belirli bir şekilde özelleştirirseniz, daha sonra yeni projeler oluşturmak için kullanabileceğiniz özel bir proje şablonu oluşturabilirsiniz. Daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

Yeni bir proje oluşturduğunuzda, varsayılan olarak *%USERPROFILE%\source\repos dizinine*kaydedilir. Bu konumu, **araçlar** > **Seçenekler** > **Projeler ve çözümler** > **konumlar**altında bulunan **Projeler konum** ayarında değiştirebilirsiniz. Daha fazla bilgi için bkz. [Projeler ve çözümler sayfası, Seçenekler iletişim kutusu](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Çözüm Gezgini

Yeni bir proje oluşturduktan sonra, projeyi ve çözümü ve ilişkili öğelerini görüntülemek ve yönetmek için **Çözüm Gezgini** kullanabilirsiniz. Aşağıdaki çizimde, iki proje içeren bir C# çözümle birlikte Çözüm Gezgini gösterilmektedir:

![Çözüm Gezgini](../ide/media/vs2015_solution_explorer.png)

Birçok menü komutu, **Çözüm Gezgini**çeşitli öğelerde sağ tıklama menüsünde bulunur. Bu komutlar bir proje oluşturma, NuGet paketlerini yönetme, bir başvuru ekleme, bir dosyayı yeniden adlandırma ve Testleri çalıştırma, yalnızca birkaç kez adlandırma içerir. **Çözüm Gezgini** üstündeki araç çubuğunda, bir çözüm görünümünden klasör görünümüne geçiş yapmak, gizli dosyaları göstermek, tüm düğümleri daraltmak ve daha fazlası için düğmeler bulunur.

ASP.NET Core projeleri için, dosyaların **Çözüm Gezgini**nasıl iç içe yerleşdiğini özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Çözüm Gezgini dosya iç içe geçirmeyi özelleştirme](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Projeler ve çözümler (Mac için Visual Studio)](/visualstudio/mac/projects-and-solutions)
- [Proje öğeleri ekleme ve kaldırma (Mac için Visual Studio)](/visualstudio/mac/add-and-remove-project-items)
