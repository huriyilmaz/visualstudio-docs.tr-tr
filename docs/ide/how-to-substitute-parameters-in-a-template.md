---
title: Proje ve öğe şablonlarına ad parametreleri ekleyin
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3c8b6e0570567e8eb696fda61fe9db7bbd4a2f1b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283950"
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
