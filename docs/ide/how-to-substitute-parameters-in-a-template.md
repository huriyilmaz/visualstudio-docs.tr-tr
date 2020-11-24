---
title: Proje ve öğe şablonlarına ad parametreleri ekleyin
description: Sınıf adları ve ad alanları gibi tanımlayıcıları değiştirmek için şablon parametrelerini değiştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ba830035f441421ca0eb83404b37319d9a9e2ca3
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596865"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Nasıl yapılır: şablonda parametreleri değiştirme

Şablon parametreleri, şablondan bir dosya oluşturulduğunda sınıf adları ve ad alanları gibi tanımlayıcıları değiştirmenize olanak sağlar. Mevcut şablonlara şablon parametreleri ekleyebilir veya şablon parametreleriyle kendi şablonlarınızı oluşturabilirsiniz.

Şablon parametreleri $*Parameter*$ biçiminde yazılır. Şablon parametrelerinin tüm listesi için bkz. [şablon parametreleri](../ide/template-parameters.md).

Aşağıdaki bölümde, bir ad alanının adını "güvenli proje adı" ile değiştirmek için bir şablonu nasıl değiştireceğiniz gösterilmektedir.

## <a name="example---namespace-name"></a>Örnek-ad alanı adı

1. Parametreyi şablondaki bir veya daha fazla kod dosyasına ekleyin. Örnek:

    ```csharp
    namespace $safeprojectname$
    ```

1. Şablonun *vstemplate* dosyasında, `ProjectItem` bu dosyayı içeren öğeyi bulun.

1. `ReplaceParameters`Öğesi için özniteliğini ayarlayın `true` `ProjectItem` :

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
