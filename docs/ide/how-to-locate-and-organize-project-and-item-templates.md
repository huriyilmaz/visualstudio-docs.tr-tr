---
title: Şablonları bulun
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 480f583bb997a19bc84fcfbe6824c12a3c638784
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591053"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Nasıl yapılır: Proje ve öğe şablonları bulma ve düzenleme

Şablon dosyalarının yeni proje ve yeni öğe iletişim kutularında gösterilmesi için bilinen bir konuma yerleştirilmesi gerekir.

::: moniker range="vs-2017"

Kullanıcı şablonu konumu özel alt kategoriler de oluşturabilirsiniz ve kategorileri gösterilir **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları.

::: moniker-end

## <a name="locate-templates"></a>Şablonları bulun

Yüklü Şablonlar ve kullanıcı şablonları iki farklı konumlarda depolanır.

### <a name="installed-templates"></a>Yüklü Şablonlar

Visual Studio ile yüklü şablonlar varsayılan olarak bulunur:

::: moniker range="vs-2017"

- *% ProgramFiles (x86)%\\Microsoft Visual Studio\\2017\\\<Edition >\\Common7\IDE\ProjectTemplates\\< dil\>\\< locale ID\>*

- *% ProgramFiles (x86)%\\Microsoft Visual Studio\\2017\\\<Edition > \Common7\IDE\ItemTemplates\\< dil\>\\< locale ID\>*

Örneğin, aşağıdaki dizine Visual Basic öğesi şablonları için İngilizce (LCID 1033) vardır:

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles (x86)%\\Microsoft Visual Studio\\2019\\\<Edition >\\Common7\IDE\ProjectTemplates\\< dil\>\\< locale ID\>*

- *% ProgramFiles (x86)%\\Microsoft Visual Studio\\2019\\\<Edition > \Common7\IDE\ItemTemplates\\< dil\>\\< locale ID\>*

Örneğin, aşağıdaki dizine Visual Basic öğesi şablonları için İngilizce (LCID 1033) vardır:

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

### <a name="user-templates"></a>Kullanıcı Şablonları

Kullanıcı şablonu dizinine *. vstemplate* dosyasını içeren bir sıkıştırılmış ( *. zip*) dosya eklerseniz, şablon yeni proje ve yeni öğe iletişim kutularında görünür. Kullanıcı şablonları varsayılan olarak bulunur:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%Userprofile%\, Studio 2017 \ Templates\ıtemtemplates*

Örneğin, kullanıcı proje şablonları için aşağıdaki dizine sahip C#:

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\VisualC#*

::: moniker-end

::: moniker range=">=vs-2019"

- *%Userprofile%\, Studio 2019 \ Templates\ProjectTemplates*

- *%Userprofile%\, Studio 2019 \ Templates\ıtemtemplates*

Örneğin, kullanıcı proje şablonları için aşağıdaki dizine sahip C#:

- *C:\users\username\k\studio 2019 \ Templates\projecttemplates\görseliC#*

::: moniker-end

> [!TIP]
> **Araçlar** > **seçenekleri** > **Projeler ve çözümler** > **konumları**' nda Kullanıcı şablonlarının bilinen konumunu değiştirebilirsiniz.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Şablon düzenleme

Kategorileri **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları yüklü şablon ve kullanıcı şablonu konumlarda mevcut dizin yapılarını yansıtır. Kullanıcı şablonu dizine yeni klasörler ekleyerek kullanıcı şablonları kendi kategoriler halinde düzenlenebilir. **Yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları, kullanıcı şablonu kategorilere yaptığınız herhangi bir değişiklik gösterir.

> [!NOTE]
> Yeni bir kategori programlama dili düzeyinde oluşturulamıyor. Yeni kategori her bir dilin yalnızca oluşturulabilir.

### <a name="create-new-user-project-template-categories"></a>Yeni Kullanıcı projesi şablon kategorileri oluştur

1. Kullanıcı proje şablonu dizini programlama dili klasörde bir klasör oluşturun. Örneğin, kurmak için bir **HelloWorld** kategorisi için C# proje şablonları, şu dizin oluşturma:

    - *\%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Bu kategori için tüm şablonları yeni klasöre yerleştirin.

1. **Dosya** menüsünde **Yeni** > **Proje**' yi seçin.

   **HelloWorld** kategorisi, **Yeni proje** iletişim kutusunda, **yüklü** > **görseli C#** altında görünür.

### <a name="create-new-user-item-template-categories"></a>Yeni Kullanıcı öğesi şablon kategorileri oluştur

1. Kullanıcı öğesi şablon dizini programlama dili klasörde bir klasör oluşturun. Örneğin, kurmak için bir **HelloWorld** kategorisi için C# öğe şablonları, şu dizin oluşturma:

    - *\%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Bu kategori için tüm şablonları yeni klasöre yerleştirin.

1. Bir proje oluşturun veya varolan bir projeyi açın. Ardından **proje** menüsünde seçin **Yeni Öğe Ekle**.

   **HelloWorld** kategorisi, **Yeni öğe Ekle** iletişim kutusunda, **yüklü** >  **C# görsel öğeleri**altında görüntülenir.

### <a name="display-templates-in-parent-categories"></a>Üst kategoriler görüntüleme şablonları

Alt kategoriler kullanarak kendi üst kategorilerde görüntülenecek şablonlarında etkinleştirebilirsiniz `NumberOfParentCategoriesToRollUp` öğesinde *.vstemplate* dosya. Bu adımları proje şablonları ve öğe şablonları ile aynıdır.

1. Bulun *.zip* şablonu içeren dosya.

1. Ayıklama *.zip* dosya.

1. Açık *.vstemplate* dosyasını Visual Studio'da.

1. İçinde `TemplateData` öğe, Ekle bir `NumberOfParentCategoriesToRollUp` öğesi. Örneğin, aşağıdaki kodu, üst kategori görünür, ancak bundan daha yüksek şablonu sağlar.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Kaydet ve Kapat *.vstemplate* dosya.

1. Şablonunuzda dosyaları seçin, seçime sağ tıklayın ve > **Sıkıştırılmış (daraltılmış) klasöre** **Gönder** ' i seçin.

   Dosyalar sıkıştırılmadan bir *.zip* dosya.

1. Ayıklanan şablon dosyalarını ve eski şablonu silmek *.zip* dosya.

1. Yeni put *.zip* silinmiş olan dizinindeki *.zip* dosya.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Visual Studio şablonları)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
