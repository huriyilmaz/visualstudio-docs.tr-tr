---
title: Projeler ve Çözümler
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b1783adadd1bfab32bfbbdcfb5ae28df7c0aae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661188"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio’da Çözümler ve Projeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da bir uygulama, uygulama, Web sitesi, Web uygulaması, komut dosyası, eklenti, vb. oluşturduğunuz zaman bir *Proje*ile başlayabilirsiniz. Bir mantıksal anlamda, bir proje tüm kaynak kodu dosyalarını, simgeleri, resimleri, veri dosyalarını ve yürütülebilir bir program veya Web sitesinde derlenecek başka herhangi bir şeyi içerir veya derlemeyi gerçekleştirmek için başka bir işlem gerekir.  Proje ayrıca, programınızın iletişim kuracağı çeşitli hizmetler veya bileşenler tarafından gerekebilecek tüm derleyici ayarlarını ve diğer yapılandırma dosyalarını da içerir.

 Bir sabit değer anlamda, bir sanal klasör hiyerarşisini tanımlayan bir XML dosyası (*. vbproj, \* . csproj, \* . vcxproj) ve tüm derleme ayarları. Visual Studio 'da proje dosyası, proje içeriğini ve ayarlarını göstermek için Çözüm Gezgini tarafından kullanılır. Projenizi derlerken, MSBuild altyapısı yürütülebilir dosyayı oluşturmak için proje dosyasını kullanır. Ayrıca, projeleri ürüne diğer çıktı türleri için de özelleştirebilirsiniz.

 Bir proje, bir veya daha fazla proje içerebilen bir *çözüm*içindeki mantıksal bir anlamda ve dosya sisteminde yer alır. Bu, derleme bilgileri, Visual Studio pencere ayarları ve herhangi bir proje ile ilişkilendirilmemiş tüm diğer dosyalar ile birlikte. Değişmez değer anlamda çözüm, kendi benzersiz biçimiyle bir metin dosyasıdır; genellikle el ile düzenlenmesi amaçlanmamıştır.

 Bir çözüm, proje üzerinde çalışan her bir kullanıcı için ayarları, tercihleri ve yapılandırma bilgilerini depolayan ilişkili *. suo dosyasına sahiptir.

 Aşağıdaki diyagramda projeler ve çözümler arasındaki ilişki ve mantıksal olarak içerdikleri öğeler gösterilmektedir.

 ![Visual Studio projeleri ve çözümleri](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 Ayrıca, özel proje ve öğe şablonları da oluşturabilirsiniz. Daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

## <a name="creating-new-projects"></a>Yeni projeler oluşturma
 Yeni bir proje oluşturmanın en kolay yolu, önceden tanımlanmış bir proje şablonuyla başlamak ve belirli bir programlama dilinde belirli bir uygulama veya Web sitesi oluşturmaya başlamanızı sağlayan, önceden oluşturulmuş bir kod dosyalarından, yapılandırma dosyalarından, varlıklardan ve ayarlardan oluşan, önceden tanımlanmış bir proje şablonuyla başlamadır. Bu şablonlar, yeni **Proje Iletişim kutusunda** gördüğünüz, yeni **&#124; proje** veya dosya &#124; yeni **&#124; Web sitesi &#124;** ana menüden gördüklerdir ve ardından gezinmeniz gerekir. Daha fazla bilgi için, bkz. [çözüm ve proje oluşturma](../ide/creating-solutions-and-projects.md) ve  [şablonlardan proje oluşturma](https://msdn.microsoft.com/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Çözüm Gezgini projeleri yönetme
 Yeni bir proje oluşturduktan sonra projeleri ve çözümleri ve bunlarla ilişkili öğeleri görüntülemek ve yönetmek için **Çözüm Gezgini** kullanırsınız. Aşağıdaki çizimde, iki proje içeren bir C# çözümünün Sunucu Gezgini gösterilmektedir.

 ![Çözüm Gezgini](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>Bu Bölümde

- [Çözümler ve Projeler Oluşturma](../ide/creating-solutions-and-projects.md)

- [Proje öğeleri ekleme ve kaldırma](../ide/adding-and-removing-project-items.md)

- [Proje ve Çözüm Özelliklerini Yönetme](../ide/managing-project-and-solution-properties.md)

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)

- [Uygulama özellikleri](../ide/application-properties.md)

- [Derleme ve Bildirim İmzalamayı Yönetme](../ide/managing-assembly-and-manifest-signing.md)

- [Nasıl Yapılır: Uygulama Simgesi Belirtme (Visual Basic C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

- [Belirli Bir .NET Framework Sürümünü Hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md)

- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio IDE](../ide/visual-studio-ide.md)
