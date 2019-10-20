---
title: Proje ve öğe şablonlarına ad parametreleri ekleyin
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09d86c52fcd9ddce3c986e0bfa6c9c96f746c663
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656559"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Nasıl yapılır: şablonda parametreleri değiştirme

Şablon parametreleri, şablondan bir dosya oluşturulduğunda sınıf adları ve ad alanları gibi tanımlayıcıları değiştirmenize olanak sağlar. Mevcut şablonlara şablon parametreleri ekleyebilir veya şablon parametreleriyle kendi şablonlarınızı oluşturabilirsiniz.

Şablon parametreleri $*Parameter*$ biçiminde yazılır. Şablon parametrelerinin tüm listesi için bkz. [şablon parametreleri](../ide/template-parameters.md).

Aşağıdaki bölümde, bir ad alanının adını "güvenli proje adı" ile değiştirmek için bir şablonu nasıl değiştireceğiniz gösterilmektedir.

## <a name="example---namespace-name"></a>Örnek-ad alanı adı

1. Parametreyi şablondaki bir veya daha fazla kod dosyasına ekleyin. Örneğin:

    ```csharp
    namespace $safeprojectname$
    ```

1. Şablonun *vstemplate* dosyasında, bu dosyayı içeren `ProjectItem` öğesini bulun.

1. @No__t_0 özniteliğini `ProjectItem` öğesi için `true` olarak ayarlayın:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)