---
title: Proje ve çözüm özelliklerini yönetme
description: Visual Studio 'da hem proje özelliklerini hem de çözüm özelliklerini yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cef610da1bcbfe7cb9c6c7ab5a806b74e07e177
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959421"
---
# <a name="manage-project-and-solution-properties"></a>Proje ve çözüm özelliklerini yönetme

Projelerin, derleme, hata ayıklama, test ve dağıtmanın birçok yönünü yöneten özellikleri vardır. Bazı özellikler tüm proje türleri arasında ortaktır ve bazıları belirli diller veya platformlar için benzersizdir. Proje özelliklerine **Çözüm Gezgini** ' de proje düğümüne sağ tıklayıp **Özellikler** ' i seçerek veya menü çubuğundaki arama kutusuna **Özellikler** yazarak ve sonuçlardan **Özellikler penceresi** ' ni seçerek erişebilirsiniz.

![Proje bağlam menüsü](../ide/media/vs2015_proj_prop_menu.gif)

.NET projeleri de proje ağacının bir özellikler düğümüne sahip olabilir.

![Çözüm Gezgini ağacındaki Özellikler düğümü](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Proje özellikleri

Proje özellikleri gruplar halinde düzenlenir ve her grubun kendi özellik sayfası vardır. Sayfalar farklı diller ve proje türleri için farklı olabilir.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic ve F # projeleri

C#, Visual Basic ve F # projelerinde, Özellikler **Proje Tasarımcısı**'nda gösterilir. Aşağıdaki çizimde, C# ' de bir WPF projesi için **derleme** Özellik sayfası gösterilmektedir:

![Visual Studio proje Tasarımcısı](../ide/media/vs2015_proppage_build.png)

**Proje Tasarımcısı**'ndaki her özellik sayfası hakkında daha fazla bilgi için bkz. [Proje Özellikleri başvurusu](../ide/reference/project-properties-reference.md).

> [!TIP]
> Çözümlerin birkaç özelliği vardır ve proje öğelerini yapın; Bu özelliklere **Proje tasarımcısında** değil [Özellikler penceresi](../ide/reference/properties-window.md)erişilir.

### <a name="c-and-javascript-projects"></a>C++ ve JavaScript projeleri

C++ ve JavaScript projelerinin proje özelliklerini yönetmek için farklı bir kullanıcı arabirimi vardır. Bu çizimde bir C++ proje özellik sayfası gösterilmektedir (JavaScript sayfaları benzerdir):

![Visual C&#43;&#43; projesi özellikleri](../ide/media/vs2015_projprops_cpp.png)

C++ proje özellikleri hakkında daha fazla bilgi için bkz. [çalımak with Project Properties (C++)](/cpp/build/working-with-project-properties). JavaScript özellikleri hakkında daha fazla bilgi için bkz. [Özellik sayfaları, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Çözüm özellikleri

Çözümdeki özelliklere erişmek için, **Çözüm Gezgini** ' deki çözüm düğümüne sağ tıklayın ve **Özellikler**' i seçin. İletişim kutusunda, **hata ayıklama** veya **Sürüm** derlemeleri için proje yapılandırmaları ayarlayabilir, **F5** tuşuna basıldığında hangi projelerin başlangıç projesi olması gerektiğini seçebilir ve kod analizi seçeneklerini ayarlarsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [Çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties)
