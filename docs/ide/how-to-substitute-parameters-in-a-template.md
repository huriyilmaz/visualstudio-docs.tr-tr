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
manager: jmartens
ms.openlocfilehash: 6d7d0a6f45468759dc3ec2349764cf2677aa5d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869238"
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
