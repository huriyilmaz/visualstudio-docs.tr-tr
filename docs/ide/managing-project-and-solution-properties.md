---
title: Proje ve çözüm özelliklerini yönetme
description: Hem proje özelliklerini hem de çözüm özelliklerini yönetim hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e67a0bde42854e39b21670e612ebf4b42015cf54
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069463"
---
# <a name="manage-project-and-solution-properties"></a>Proje ve çözüm özelliklerini yönetme

Projelerin derleme, hata ayıklama, test etme ve dağıtma gibi birçok yönü yöneten özellikleri vardır. Bazı özellikler tüm proje türleri arasında ortaktır ve bazıları belirli diller veya platformlar için benzersizdir. Proje özelliklerine erişmek için Çözüm Gezgini'daki  proje düğümüne sağ tıklar  ve Özellikler'i seçer veya menü çubuğundaki arama kutusuna özellikler yazın ve sonuçlardan Özellikler **Penceresi'ne** tıklayın. 

![Project menüsü](../ide/media/vs2015_proj_prop_menu.gif)

.NET projelerinin de proje ağacında bir özellikler düğümü olabilir.

![Ağaç üzerinde Çözüm Gezgini düğümü](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Proje özellikleri

Project özellikleri gruplar halinde düzenlenmiştir ve her grubun kendi özellik sayfası vardır. Sayfalar farklı diller ve proje türleri için farklı olabilir.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic ve F# projeleri

C#, Visual Basic ve F# projelerinde, özellikler Project **Designer'da ortaya çıkar.** Aşağıdaki çizimde, **C#** içinde bir WPF projesinin Derleme özelliği sayfası gösterilmiştir:

![Visual Studio Project Tasarımcısı](../ide/media/vs2015_proppage_build.png)

Project Designer'daki özellik **sayfalarının her biri hakkında bilgi için** [bkz. Project özellikleri başvurusu.](../ide/reference/project-properties-reference.md)

> [!TIP]
> Çözümlerin birkaç özelliği vardır ve proje öğeleri de vardır; Bu özelliklere Tasarımcı [Özellikler penceresi](../ide/reference/properties-window.md)değil, **Project erişilir.**

### <a name="c-and-javascript-projects"></a>C++ ve JavaScript projeleri

C++ ve JavaScript projeleri, proje özelliklerini yönetmek için farklı bir kullanıcı arabirimine sahiptir. Bu çizimde bir C++ proje özellik sayfası gösterilmiştir (JavaScript sayfaları birbirine benzer):

![Visual C&#43;&#43; proje özellikleri](../ide/media/vs2015_projprops_cpp.png)

C++ proje özellikleri hakkında bilgi için [bkz. Proje özellikleriyle çalışma (C++)](/cpp/build/working-with-project-properties). JavaScript özellikleri hakkında daha fazla bilgi için [bkz. Özellik sayfaları, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Çözüm özellikleri

Çözümdeki özelliklere erişmek için, Çözüm Gezgini'de **çözüm** düğümüne sağ tıklayın ve **Özellikler'i seçin.** İletişim kutusunda Hata Ayıklama veya  Yayın derlemeleri için proje yapılandırmalarını ayarlayabilir, **F5'e** basıldığında hangi projelerin başlangıç projesi olması gerektiğini seçebilir ve kod analizi seçeneklerini ayarlayabilirsiniz. 

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [Çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties)
