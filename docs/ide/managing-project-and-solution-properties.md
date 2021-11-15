---
title: Proje ve çözüm özelliklerini yönetme
description: Hem proje özelliklerini hem de çözüm özelliklerini yönetim hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/12/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8f506242994b0bfe9d16f2404912f8e1bfb23927
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132454102"
---
# <a name="manage-project-and-solution-properties"></a>Proje ve çözüm özelliklerini yönetme

Projelerin derleme, hata ayıklama, test etme ve dağıtma gibi birçok yönü yöneten özellikleri vardır. Bazı özellikler tüm proje türleri arasında ortaktır ve bazıları belirli diller veya platformlar için benzersizdir.

Proje özelliklerine erişmek için Çözüm Gezgini'daki  proje düğümüne sağ tıklar  ve Özellikler'i seçersiniz veya menü çubuğundaki arama kutusuna özellikler yazarak ve sonuçlardan **Özellikler Penceresi'ne** tıklayarak.

::: moniker range="vs-2022"

:::image type="content" source="media/vs-2022/properties-from-solution-explorer-context-menu.png" alt-text="Özellikler seçeneğinin Çözüm Gezgini ekran görüntüsü.":::

::: moniker-end

::: moniker range="<=vs-2019"

![Project menüsü](../ide/media/vs2015_proj_prop_menu.gif)

::: moniker-end

.NET projelerinin de proje ağacında bir özellikler düğümü olabilir.

::: moniker range="vs-2022"

:::image type="content" source="media/vs-2022/properties-node-solution-explorer.png" alt-text="Özellikler düğümü Çözüm Gezgini ekran görüntüsü.":::

::: moniker-end

::: moniker range="<=vs-2019"

![Ağaç üzerinde Çözüm Gezgini düğümü](../ide/media/vs2015_props_se.png)

::: moniker-end

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Proje özellikleri

Project gruplar halinde düzenlenmiştir ve her grubun kendi özellik sayfası vardır. Sayfalar farklı diller ve proje türleri için farklı olabilir.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic ve F# projeleri

C#, Visual Basic ve F# projelerinde özellikler, Project **Tasarımcısı'nda ortaya çıkar.**

::: moniker range="vs-2022"

Aşağıdaki çizimde **C# ile** bir konsol projesinin Derleme özelliği sayfası gösterilmiştir:

:::image type="content" source="media/vs-2022/properties-page-csharp-console.png" alt-text="Visual Studio 2022'de Özellikler sayfasının ekran görüntüsü." lightbox="media/vs-2022/properties-page-csharp-console.png":::

::: moniker-end

::: moniker range="<=vs-2019"

Aşağıdaki çizimde, **C#** içinde bir WPF projesinin Derleme özelliği sayfası gösterilmiştir:

![Visual Studio Project Tasarımcısı](../ide/media/vs2015_proppage_build.png)

::: moniker-end

Project Designer'daki özellik **sayfalarının her biri hakkında bilgi için** [bkz. Project özellikleri başvurusu.](../ide/reference/project-properties-reference.md)

> [!TIP]
> Çözümlerin birkaç özelliği vardır ve proje öğeleri de vardır; Bu özelliklere Tasarımcı [Özellikler penceresi](../ide/reference/properties-window.md)değil, **Project erişilir.**

### <a name="c-and-javascript-projects"></a>C++ ve JavaScript projeleri

C++ ve JavaScript projeleri, proje özelliklerini yönetmek için farklı bir kullanıcı arabirimine sahiptir. Bu çizimde bir C++ proje özellik sayfası gösterilmiştir (JavaScript sayfaları birbirine benzer):

::: moniker range="vs-2022"

:::image type="content" source="media/vs-2022/properties-page-cpp-console.png" alt-text="C++ proje özellikleri sayfasının ekran görüntüsü.":::

::: moniker-end

::: moniker range="<=vs-2019"

![Visual C&#43;&#43; proje özellikleri](../ide/media/vs2015_projprops_cpp.png)

::: moniker-end

C++ proje özellikleri hakkında bilgi için [bkz. Proje özellikleriyle çalışma (C++)](/cpp/build/working-with-project-properties). JavaScript özellikleri hakkında daha fazla bilgi için [bkz. Özellik sayfaları, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Çözüm özellikleri

Çözümdeki özelliklere erişmek için, Çözüm Gezgini 'de **çözüm** düğümüne sağ tıklayın ve **Özellikler'i seçin.** İletişim kutusunda Hata Ayıklama veya  Yayın derlemeleri için proje yapılandırmalarını ayarlayabilir, **F5'e** basıldığında hangi projelerin başlangıç projesi olması gerektiğini seçebilir ve kod analizi seçeneklerini ayarlayabilirsiniz. 

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [Çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties)
