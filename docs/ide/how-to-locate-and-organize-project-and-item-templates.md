---
title: Şablonları bulma
description: Proje ve öğe şablonlarını bulup düzenlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 52851b97716d6b32cc4087f19f87d060e1c608c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028052"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Nasıl kullanılır: Proje ve öğe şablonlarını bulma ve düzenleme

Şablon dosyalarının yeni projede ve yeni öğe iletişim kutularında gösterilmeleri için bilinen bir konuma yerleştirilmeleri gerekir.

::: moniker range="vs-2017"

Ayrıca, kullanıcı şablonu konumu içinde özel alt kategoriler oluşturabilirsiniz ve  kategoriler Yeni Giriş ve Project Ekle **iletişim kutularında** gösterilir.

::: moniker-end

## <a name="locate-templates"></a>Şablonları bulma

Yüklü şablonlar ve kullanıcı şablonları iki farklı konumda depolanır.

### <a name="installed-templates"></a>Yüklü şablonlar

Varsayılan olarak, Visual Studio şablonlar şu konumda bulunur:

::: moniker range="vs-2017"

- *%ProgramFiles(x86)% \\ Microsoft Visual Studio \\ 2017 \\ \<edition> \\ Common7\IDE\ProjectTemplates \\<Dil<Yerel \> \\ Kimlik\>*

- *%ProgramFiles(x86)% \\ Microsoft Visual Studio \\ 2017 \\ \<edition> \Common7\IDE\ItemTemplates \\<Dil<Yerel \> \\ Kimlik\>*

Örneğin, aşağıdaki dizinde İngilizce (LCID 1033) Visual Basic öğe şablonları bulunur:

*C: \\ Program Files (x86) \\ Microsoft Visual Studio \\ 2017 \\ Community \\ Common7 \\ IDE \\ ItemTemplates \\ VisualBasic \\ 1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *%ProgramFiles(x86)% \\ Microsoft Visual Studio \\ 2019 \\ \<edition> \\ Common7\IDE\ProjectTemplates \\<\> \\ Dil<Yerel Kimlik\>*

- *%ProgramFiles(x86)% \\ Microsoft Visual Studio \\ 2019 \\ \<edition> \Common7\IDE\ItemTemplates \\<Dil<Yerel \> \\ Kimlik\>*

Örneğin, aşağıdaki dizinde İngilizce (LCID 1033) Visual Basic öğe şablonları bulunur:

*C: \\ Program Files (x86) \\ Microsoft Visual Studio \\ 2019 \\ Community \\ Common7 \\ IDE \\ ItemTemplates \\ VisualBasic \\ 1033*

::: moniker-end

### <a name="user-templates"></a>Kullanıcı şablonları

Kullanıcı şablonu dizinine *bir* *.vstemplate* dosyası içeren sıkıştırılmış (.zip) dosyası eklersiniz, şablon yeni proje ve yeni öğe iletişim kutularında görünür. Varsayılan olarak, kullanıcı şablonları şu konumda bulunur:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*

Örneğin, aşağıdaki dizinde C# için kullanıcı projesi şablonları vardır:

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C #*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*

Örneğin, aşağıdaki dizinde C# için kullanıcı projesi şablonları vardır:

- *C:\Users\UserName\Documents\Visual Studio 2019\Templates\ProjectTemplates\Visual C #*

::: moniker-end

> [!TIP]
> Araç Seçenekleri Projeleri ve Çözüm Konumları'nın kullanıcı **şablonları**  >  **için**  >  **bilinen konumu**  >  **değiştirebilirsiniz.**

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Şablonları düzenleme

New **Project** ve Add New **Item** iletişim kutularında yer alan kategoriler, yüklü şablonda ve kullanıcı şablonu konumlarında mevcut olan dizin yapılarını gösterir. Kullanıcı şablonları, kullanıcı şablonu dizinine yeni klasörler ekleyerek kendi kategorilerine göre organize olabilir. Yeni **Project** ve **Yeni Öğe Ekle** iletişim kutuları, kullanıcı şablonu kategorilerinize yaptığınız değişiklikleri gösterir.

> [!NOTE]
> Programlama dili düzeyinde yeni bir kategori oluşturamazsiniz. Yeni kategoriler yalnızca her dil içinde oluşturulabilir.

### <a name="create-new-user-project-template-categories"></a>Yeni kullanıcı projesi şablon kategorileri oluşturma

1. Kullanıcı projesi şablon dizininde programlama dili klasöründe bir klasör oluşturun. Örneğin, C# proje şablonları **için HelloWorld** kategorisi oluşturmak için aşağıdaki dizini oluşturun:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Bu kategoriye ait tüm şablonları yeni klasöre girin.

1. Dosya menüsünde **Yeni** **dosya'Project.** > 

   HelloWorld **kategorisi,** Yüklü Visual **C# Project** Yeni Uygulama **iletişim** > **kutusunda görünür.**

### <a name="create-new-user-item-template-categories"></a>Yeni kullanıcı öğesi şablon kategorileri oluşturma

1. Kullanıcı öğesi şablon dizininde programlama dili klasöründe bir klasör oluşturun. Örneğin, C# öğe şablonları **için HelloWorld** kategorisi oluşturmak için aşağıdaki dizini oluşturun:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ItemTemplates\Visual C#\HelloWorld*

1. Bu kategoriye ait tüm şablonları yeni klasöre girin.

1. Proje oluşturun veya var olan bir projeyi açın. Ardından, **yeni** Project Ekle'yi **seçin.**

   HelloWorld **kategorisi,** Yeni Öğe **Ekle iletişim**  kutusunun Yüklü Visual C# Öğeleri > **altında görünür.**

### <a name="display-templates-in-parent-categories"></a>Şablonları üst kategorilerde görüntüleme

`NumberOfParentCategoriesToRollUp` *.vstemplate* dosyasındaki öğesini kullanarak alt kategorilerdeki şablonların üst kategorilerinde görüntülenebilir. Bu adımlar proje şablonları ve öğe şablonları için aynıdır.

1. Şablonu *.zip* dosyanın konumunu bulun.

1. .zip *ayıkla.*

1. *.vstemplate dosyasını* Visual Studio.

1. öğesine `TemplateData` bir öğesi `NumberOfParentCategoriesToRollUp` ekleyin. Örneğin, aşağıdaki kod şablonu üst kategoride görünür hale ancak daha yüksek bir kategoriye sahip değildir.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. *.vstemplate dosyasını kaydedin ve* kapatın.

1. Şablonda dosyaları seçin, seçime sağ tıklayın  ve Sıkıştırılmış > **(sıkıştırılmış) klasöre gönder'i seçin.**

   Dosyalar bir.zip *sıkıştırılır.*

1. Ayıklanan şablon dosyalarını ve eski şablon *.zip* silin.

1. Yeni *.zip* dosyasını silinen dosyanın olduğu *dizine.zip.*

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Visual Studio şema başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Visual Studio şablonları)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Nasıl: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Nasıl kullanılır: Öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
