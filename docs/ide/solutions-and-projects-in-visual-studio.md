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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303073"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio'da çözümler ve projeler

Bu sayfada Visual Studio'da *proje* ve *çözüm* kavramı açıklanmaktadır. Ayrıca, Solution Explorer araç penceresini ve yeni bir projenin nasıl oluşturulacağını da kısaca kapsar.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'daki Projeler ve çözümlere](/visualstudio/mac/projects-and-solutions)bakın.

## <a name="projects"></a>Projeler

Visual Studio'da bir uygulama veya web sitesi oluşturduğunuzda, bir *projeyle*başlarsınız. Mantıksal anlamda, bir proje yürütülebilir, kitaplık veya web sitesinde derlenen tüm dosyaları içerir. Bu dosyalar kaynak kodu, simgeler, resimler, veri dosyaları ve benzeri içerebilir. Proje ayrıca derleyici ayarlarını ve programınızın iletişim kurduğu çeşitli hizmetler veya bileşenler tarafından ihtiyaç duyulabilecek diğer yapılandırma dosyalarını da içerir.

### <a name="project-file"></a>Proje dosyası

Visual Studio, her projeyi bir çözümde oluşturmak için [MSBuild'i](../msbuild/msbuild.md) kullanır ve her proje bir MSBuild proje dosyası içerir. Dosya uzantısı, örneğin C# projesi (.csproj), Visual Basic projesi (.vbproj) veya veritabanı projesi (.dbproj) gibi proje türünü yansıtır. Proje dosyası, içeriği, platform gereksinimleri, sürüm bilgileri, web sunucusu veya veritabanı sunucusu ayarları ve görevleri de dahil olmak üzere projenizi oluşturmak için MSBuild'in ihtiyaç duyduğu tüm bilgileri ve talimatları içeren bir XML belgesidir. Gerçekleştirmek.

Proje dosyaları [MSBuild XML şema](../msbuild/msbuild-project-file-schema-reference.md)dayanmaktadır. Visual Studio'daki yeni, [sdk tarzı proje dosyalarının](../msbuild/how-to-use-project-sdk.md) içeriğine bakmak için Solution **Explorer'daki** proje düğümüne sağ tıklayın ve **proje adını \<\>edit'i**seçin. .NET Framework ve bu stildeki diğer projelerin içeriğine bakmak için önce projeyi boşaltın **(Solution Explorer'da** proje düğümüne sağ tıklayın ve **Project'i Boşalt'ı**seçin). Ardından, projeye sağ tıklayın ve **proje \<adını\>edit'i**seçin.

> [!NOTE]
> Kodu yeniden oluşturmak, oluşturmak ve hata ayıklamak için Visual Studio'da çözüm veya proje kullanmanız gerekmemektedir. Visual Studio'da kaynak dosyalarınızı içeren klasörü açıp düzenlemeye başlayabilirsiniz. Daha fazla bilgi için visual [studio'da proje veya çözüm olmadan kod geliştir'e](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)bakın.

## <a name="solutions"></a>Çözümler

Bir proje bir *çözüm*içinde yer almaktadır. İsmini rağmen, bir çözüm bir "cevap" değildir. Bu yalnızca bir veya daha fazla ilgili proje için bir kapsayıcı, yapı bilgileri, Visual Studio pencere ayarları ve belirli bir projeile ilişkili olmayan herhangi bir çeşitli dosyaları ile birlikte. Bir çözüm, kendi benzersiz biçimine sahip bir metin dosyası (uzantı *.sln)* tarafından açıklanır; elle düzenlenmesi amaçlanmamıştır.

Visual Studio, çözümler için ayarları depolamak için iki dosya türü *(.sln* ve *.suo)* kullanır:

|Dahili numara|Adı|Açıklama|
|---------------|----------|-----------------|
|Sln|Visual Studio Çözümü|Çözümdeki projeleri, proje öğelerini ve çözüm öğelerini düzenler.|
|.suo|Çözüm Kullanıcı Seçenekleri|Kesme noktaları gibi kullanıcı düzeyinde ayarları ve özelleştirmeleri depolar.|

## <a name="create-new-projects"></a>Yeni projeler oluştur

Yeni bir proje oluşturmanın en kolay yolu, belirli bir uygulama veya web sitesi türü için proje şablonundan başlamaktır. Proje şablonu, önceden oluşturulmuş kod dosyaları, config dosyaları, varlıklar ve ayarlardan oluşan temel bir kümeden oluşur. Bu şablonlar, yeni bir proje **(Dosya** > **Yeni** > **Proje)** oluşturduğunuz iletişim kutusunda kullanılabilir. Daha fazla bilgi için Visual [Studio'da yeni bir proje oluştur](create-new-project.md) ve çözüm ve proje [oluşturun.](../ide/creating-solutions-and-projects.md)

Projelerinizi sık sık belirli bir şekilde özelleştiriyorsanız, daha sonra yeni projeler oluşturmak için kullanabileceğiniz özel bir proje şablonu oluşturabilirsiniz. Daha fazla bilgi için [bkz.](../ide/creating-project-and-item-templates.md)

Yeni bir proje oluşturduğunuzda, varsayılan olarak *%USERPROFILE%\source\repos*adresinde nitre edilir. Bu konumu **Araçlar** > **Seçenekleri** > **Projeleri ve Çözüm** > **Konumları**altında **Projeler konum** ayarında değiştirebilirsiniz. Daha fazla bilgi için [Projeler ve Çözümler sayfasına, Seçenekler iletişim kutusuna](../ide/reference/projects-and-solutions-options-dialog-box.md)bakın.

## <a name="solution-explorer"></a>Çözüm Gezgini

Yeni bir proje oluşturduktan sonra, projeyi ve çözümü ve bunların ilişkili öğelerini görüntülemek ve yönetmek için **Solution Explorer'ı** kullanabilirsiniz. Aşağıdaki resimde **Çözüm Gezgini** iki proje içeren bir C# çözümü ile gösterilmektedir:

![Çözüm Gezgini](../ide/media/vs2015_solution_explorer.png)

Birçok menü komutları **Çözüm Gezgini**çeşitli öğelerin sağ tıklama menüsünden kullanılabilir. Bu komutlar arasında bir proje oluşturma, NuGet paketlerini yönetme, başvuru ekleme, dosyayı yeniden adlandırma ve birkaç ıstabiri için testler çalıştırma yer alır. **Solution Explorer'ın** üst kısmındaki araç çubuğunda çözüm görünümünden klasör görünümüne geçmek, gizli dosyaları göstermek, tüm düğümleri daraltmak ve daha fazlası için düğmeler bulunur.

ASP.NET Core projeleri için, dosyaların **Solution Explorer'da**nasıl iç içe olduğunu özelleştirebilirsiniz. Daha fazla bilgi için [Bkz. Çözüm Gezgini'nde dosya iç içe geçmeyi özelleştir.](file-nesting-solution-explorer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo IDE](../get-started/visual-studio-ide.md)
- [Projeler ve çözümler (Mac için Visual Studio)](/visualstudio/mac/projects-and-solutions)
- [Proje öğeleri ekleme ve kaldırma (Mac için Visual Studio)](/visualstudio/mac/add-and-remove-project-items)
