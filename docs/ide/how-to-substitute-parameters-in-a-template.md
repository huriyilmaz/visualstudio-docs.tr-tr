---
title: Proje ve öğe şablonlarına ad parametreleri ekleme
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
ms.technology: vs-ide-general
ms.openlocfilehash: 5642f12f72cdc24bb6a2ef6db921d30482f4ca0e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078316"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Nasıl yapılacaklar: Şablonda parametrelerin yerini ekleme

Şablon parametreleri, şablondan bir dosya oluşturulduğunda sınıf adları ve ad alanları gibi tanımlayıcıları değiştirmenize izin verir. Mevcut şablonlara şablon parametreleri ekleyebilir veya şablon parametreleriyle kendi şablonlarınızı oluşturabilirsiniz.

Şablon parametreleri $ parametresi $*biçiminde* yazılır. Şablon parametrelerinin tam listesi için bkz. [Şablon parametreleri.](../ide/template-parameters.md)

Aşağıdaki bölümde, bir ad alanının adını "güvenli proje adı" ile değiştirmek için şablonu nasıl değiştiryebilirsiniz?

## <a name="example---namespace-name"></a>Örnek - ad alanı adı

1. parametresini şablonda bir veya daha fazla kod dosyası içine ekler. Örnek:

    ```csharp
    namespace $safeprojectname$
    ```

1. Şablonun *vstemplate* dosyasında, bu `ProjectItem` dosyayı içeren öğesini bulun.

1. öğesi `ReplaceParameters` için `true` özniteliğini olarak `ProjectItem` ayarlayın:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
