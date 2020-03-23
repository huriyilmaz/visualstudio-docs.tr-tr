---
title: Proje ve madde şablonlarına ad parametreleri ekleme
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9ddfe065d30b958e52e22f30f946d01d626fcf0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591417"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Nasıl kullanılır: Şablondaki yedek parametreler

Şablon parametreleri, bir dosya şablondan oluşturulduğunda sınıf adları ve ad alanları gibi tanımlayıcıları değiştirmenize izin verilir. Varolan şablonlara şablon parametreleri ekleyebilir veya şablon parametreleri ile kendi şablonlarınızı oluşturabilirsiniz.

Şablon parametreleri $*parametresi*$ biçiminde yazılır. Şablon parametrelerinin tam listesi için [Şablon parametrelerine](../ide/template-parameters.md)bakın.

Aşağıdaki bölümde, ad alanının adını "güvenli proje adı" ile değiştirmek için şablonu nasıl değiştirebilirsiniz gösterilmektedir.

## <a name="example---namespace-name"></a>Örnek - namespace adı

1. Parametreyi şablondaki kod dosyalarının bir veya birkaçına ekleyin. Örnek:

    ```csharp
    namespace $safeprojectname$
    ```

1. Şablonun *vstemplate* dosyasında, bu `ProjectItem` dosyayı içeren öğeyi bulun.

1. Öğe için `true` özniteliği ayarlayın: `ReplaceParameters` `ProjectItem`

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
