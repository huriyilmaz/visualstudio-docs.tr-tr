---
title: Proje ve çözüm özelliklerini yönetme
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01fcdc09c9d3ee4f5a38a95ef4304bfdf537d527
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591313"
---
# <a name="manage-project-and-solution-properties"></a>Proje ve çözüm özelliklerini yönetme

Projeler, derleme, hata ayıklama, test etme ve dağıtmanın birçok yönünü yöneten özelliklere sahiptir. Bazı özellikler tüm proje türleri arasında yaygındır ve bazıları belirli dillere veya platformlara özgüdür. **Çözüm Gezgini'ndeki** proje düğümüne sağ tıklayarak ve **Özellikler** seçerek veya menü çubuğundaki arama kutusuna **özellikleri** yazarak ve sonuçlardan **Özellikler Penceresi'ni** seçerek proje özelliklerine erişebilirsiniz.

![Proje bağlam menüsü](../ide/media/vs2015_proj_prop_menu.gif)

.NET projelerinde proje ağacının kendisinde bir özellik düğümü de olabilir.

![Çözüm Gezgini ağacında özellikler düğümü](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için çözüm [ve proje özelliklerini yönetme (Mac için Visual Studio) adresine](/visualstudio/mac/managing-solutions-and-project-properties)bakın.

## <a name="project-properties"></a>Proje özellikleri

Proje özellikleri gruplar halinde düzenlenir ve her grubun kendi özellik sayfası vardır. Sayfalar farklı diller ve proje türleri için farklı olabilir.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic ve F# projeleri

C#, Visual Basic ve F# projelerinde özellikler **Project Designer'da**açığa çıkar. Aşağıdaki resimde C#'daki bir WPF projesiiçin **Yapı** özelliği sayfası gösterilmektedir:

![Visual Studio Proje Tasarımcısı](../ide/media/vs2015_proppage_build.png)

**Project Designer'daki**özellik sayfalarının her biri hakkında bilgi için [Bkz. Proje özellikleri başvurusu.](../ide/reference/project-properties-reference.md)

> [!TIP]
> Çözümlerin birkaç özelliği vardır ve proje öğeleri de vardır; bu özelliklere [Özellikler penceresinde](../ide/reference/properties-window.md)erişilir, **Project Designer**değil.

### <a name="c-and-javascript-projects"></a>C++ ve JavaScript projeleri

C++ ve JavaScript projeleri, proje özelliklerini yönetmek için farklı bir kullanıcı arabirimine sahiptir. Bu resimde bir C++ proje özelliği sayfası gösterilmektedir (JavaScript sayfaları benzerdir):

![Görsel C&#43;&#43; proje özellikleri](../ide/media/vs2015_projprops_cpp.png)

C++ proje özellikleri hakkında bilgi için [bkz.](/cpp/build/working-with-project-properties) JavaScript özellikleri hakkında daha fazla bilgi için Bkz. [Özellik sayfaları, JavaScript.](../ide/reference/property-pages-javascript.md)

## <a name="solution-properties"></a>Çözüm özellikleri

Çözümdeki özelliklere erişmek için **Çözüm Gezgini'ndeki** çözüm düğümüne sağ tıklayın ve **Özellikler'i**seçin. İletişim kutusunda Hata **Ayıklama** veya **Sürüm** yapıları için proje yapılandırmaları ayarlayabilir, **F5** tuşuna basıldığında hangi projelerin başlangıç projesi olması gerektiğini seçebilir ve kod çözümleme seçeneklerini ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [Çözüm ve proje özelliklerini yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties)
