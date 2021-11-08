---
title: Proje ve çözüm özelliklerini yönetme
description: Hem proje özelliklerini hem de Visual Studio çözüm özelliklerini yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/02/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b45b1baa351014d5ebe410e3154fc784c4e50b78
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001536"
---
# <a name="manage-project-and-solution-properties"></a>Proje ve çözüm özelliklerini yönetme

Projelerin, derleme, hata ayıklama, test ve dağıtmanın birçok yönünü yöneten özellikleri vardır. Bazı özellikler tüm proje türleri arasında ortaktır ve bazıları belirli diller veya platformlar için benzersizdir.

> [!TIP]
> [Visual Studio 2022](/visualstudio/releases/2022/release-notes)' de, proje özelliklerine yeni işlevler ekledik ve kullanıcı arabirimini yeniledi. daha fazla bilgi edinmek için bkz. [**revaed Project Properties uı**](https://devblogs.microsoft.com/visualstudio/revamped-project-properties-ui/) blog gönderisi.

**Çözüm Gezgini** ' de proje düğümüne sağ tıklayıp **Özellikler**' i seçerek veya menü çubuğundaki arama kutusuna **Özellikler** yazarak ve sonuçlardan **Özellikler penceresi** ' ni seçerek Proje özelliklerine erişirsiniz.

![Project bağlam menüsü](../ide/media/vs2015_proj_prop_menu.gif)

.NET projeleri de proje ağacının bir özellikler düğümüne sahip olabilir.

![Çözüm Gezgini ağacındaki Özellikler düğümü](../ide/media/vs2015_props_se.png)

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Proje özellikleri

Project özellikler gruplar halinde düzenlenir ve her grubun kendi özellik sayfası vardır. Sayfalar farklı diller ve proje türleri için farklı olabilir.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic ve F # projeleri

C#, Visual Basic ve F # projelerinde özellikler, **Project tasarımcısında** sunulur. Aşağıdaki çizimde, C# ' de bir WPF projesi için **derleme** Özellik sayfası gösterilmektedir:

![Visual Studio Project tasarımcısı](../ide/media/vs2015_proppage_build.png)

**Project tasarımcısında** özellik sayfalarının her biri hakkında bilgi için bkz. [Project properties reference](../ide/reference/project-properties-reference.md).

> [!TIP]
> Çözümlerin birkaç özelliği vardır ve proje öğelerini yapın; bu özelliklere **Project tasarımcısında** değil [Özellikler penceresi](../ide/reference/properties-window.md)erişilir.

### <a name="c-and-javascript-projects"></a>C++ ve JavaScript projeleri

C++ ve JavaScript projelerinin proje özelliklerini yönetmek için farklı bir kullanıcı arabirimi vardır. Bu çizimde bir C++ proje özellik sayfası gösterilmektedir (JavaScript sayfaları benzerdir):

![Visual C&#43;&#43; projesi özellikleri](../ide/media/vs2015_projprops_cpp.png)

C++ proje özellikleri hakkında daha fazla bilgi için bkz. [çalımak with Project Properties (C++)](/cpp/build/working-with-project-properties). JavaScript özellikleri hakkında daha fazla bilgi için bkz. [Özellik sayfaları, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Çözüm özellikleri

Çözümdeki özelliklere erişmek için, **Çözüm Gezgini** ' deki çözüm düğümüne sağ tıklayın ve **Özellikler**' i seçin. İletişim kutusunda, **hata ayıklama** veya **Sürüm** derlemeleri için proje yapılandırmaları ayarlayabilir, **F5** tuşuna basıldığında hangi projelerin başlangıç projesi olması gerektiğini seçebilir ve kod analizi seçeneklerini ayarlarsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties)
