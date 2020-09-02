---
title: Proje ve çözüm özelliklerini yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec48aac60a8f15527c92d19a38ca9f996dcfdd6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651357"
---
# <a name="managing-project-and-solution-properties"></a>Proje ve Çözüm Özelliklerini Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projelerin, derleme, hata ayıklama, test ve dağıtmanın birçok yönünü yöneten özellikleri vardır. Bazı özellikler tüm proje türleri arasında ortaktır ve bazıları belirli diller veya platformlar için benzersizdir. Proje özelliklerine Çözüm Gezgini ' de proje düğümüne sağ tıklayıp Özellikler ' i seçerek ya da menü çubuğundaki **Hızlı Başlat** arama kutusuna Özellikler yazarak erişebilirsiniz.

 ![Proje bağlam menüsü](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")

 .NET projelerinin aynı zamanda proje ağacının bir özellikler düğümü de vardır.

 ![Çözüm Gezgini ağacındaki Özellikler düğümü](../ide/media/vs2015-props-se.png "VS2015_Props_SE")

> [!TIP]
> Çözümlerin birkaç özelliği vardır ve proje öğelerini yapın; Bu özelliklere **Proje Tasarımcısı**değil [Özellikler penceresinde](../ide/reference/properties-window.md)erişilir.

## <a name="project-properties"></a>Proje Özellikleri
 Proje özellikleri gruplar halinde düzenlenir ve her grubun kendi özellik sayfası vardır ve sayfalar farklı diller ve proje türleri için farklı olabilir.

### <a name="c-and-visual-basic-projects"></a>C# ve Visual Basic projeleri
 C# ve Visual Basic projelerinde, Özellikler **Proje tasarımcısında**gösterilir. Aşağıdaki çizimde, C# ' de bir WPF projesi için derleme özellik sayfası gösterilmektedir:

 ![Visual Studio proje Tasarımcısı](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")

 Proje Tasarımcısı 'ndaki her özellik sayfası hakkında daha fazla bilgi için bkz. [Proje Özellikleri başvurusu](../ide/reference/project-properties-reference.md).

### <a name="c-and-javascript-projects"></a>C++ ve JavaScript projeleri
 C++ ve JavaScript projelerinin proje özelliklerini yönetmek için farklı bir kullanıcı arabirimi vardır. Bu çizimde bir C++ proje özellik sayfası gösterilmektedir (JavaScript sayfaları benzerdir):

 ![Visual C&#43;&#43; projesi özellikleri](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")

 C++ proje özellikleri hakkında daha fazla bilgi için bkz. [Proje özellikleriyle çalışma](https://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd). JavaScript özellikleri hakkında daha fazla bilgi için bkz. [Özellik sayfaları, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Çözüm özellikleri
 Çözümdeki özelliklere erişmek için, **Çözüm Gezgini** ' deki çözüm düğümüne sağ tıklayın ve **Özellikler**' i seçin. İletişim kutusunda, hata ayıklama veya sürüm derlemeleri için proje yapılandırmaları ayarlayabilir, F5 tuşuna basıldığında hangi projelerin başlangıç projesi olması gerektiğini seçebilir ve kod analizi seçeneklerini ayarlarsınız.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio’da Çözümler ve Projeler](../ide/solutions-and-projects-in-visual-studio.md)
