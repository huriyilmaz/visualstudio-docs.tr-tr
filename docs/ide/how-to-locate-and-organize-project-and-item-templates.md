---
title: Şablonları bulma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591053"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Nasıl yapilir: Proje ve madde şablonlarını bulma ve düzenleme

Şablon dosyalarının yeni projede ve yeni öğe iletişim kutularında gösterilebilmesi için bilinen bir konuma yerleştirilmelidir...

::: moniker range="vs-2017"

Ayrıca, kullanıcı şablonu konumunda özel alt kategoriler oluşturabilirsiniz ve kategoriler **Yeni Proje** ve Yeni **Öğe Ekle** iletişim kutularında gösterilir.

::: moniker-end

## <a name="locate-templates"></a>Şablonları bulma

Yüklenen şablonlar ve kullanıcı şablonları iki farklı konumda depolanır.

### <a name="installed-templates"></a>Yüklü şablonlar

Varsayılan olarak, Visual Studio ile yüklenen şablonlar şu şekilde bulunur:

::: moniker range="vs-2017"

- *%ProgramFiles(x86)%\\Microsoft\\Visual Studio\\\< \\2017 sürümü>\\ Common7\IDE\ProjectTemplates<Dil\> \\<Yerel kimlik\>*

- *%ProgramFiles(x86)%\\Microsoft\\Visual Studio\\\<2017 sürümü>\Common7\IDE\ItemTemplates\\<Dil\> \\<Yerel kimlik\>*

Örneğin, aşağıdaki dizin İngilizce (LCID 1033) için Visual Basic öğe şablonları vardır:

*C:\\Program Dosyaları\\(x86)\\Microsoft Visual\\\\Studio\\2017\\Topluluk\\Common7 IDE\\ItemTemplates VisualBasic 1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *%ProgramFiles(x86)%\\Microsoft\\Visual Studio\\\< \\2019 sürümü>\\ Common7\IDE\ProjectTemplates<Dil\> \\<Yerel kimlik\>*

- *%ProgramFiles(x86)%\\Microsoft\\Visual Studio\\\<2019 sürümü>\Common7\IDE\ItemTemplates\\<Dil\> \\<Locale ID\>*

Örneğin, aşağıdaki dizin İngilizce (LCID 1033) için Visual Basic öğe şablonları vardır:

*C:\\Program Dosyaları\\(x86)\\Microsoft Visual\\\\Studio\\2019\\Topluluk\\Common7 IDE\\ItemTemplates VisualBasic 1033*

::: moniker-end

### <a name="user-templates"></a>Kullanıcı şablonları

Kullanıcı şablon dizine *.vstemplate* dosyası içeren sıkıştırılmış (*.zip*) dosyası eklerseniz, şablon yeni projede ve yeni öğe iletişim kutularında görüntülenir. Varsayılan olarak, kullanıcı şablonları şu şekilde bulunur:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017\Şablonlar\ItemTemplates*

Örneğin, aşağıdaki dizin C# için kullanıcı proje şablonlarına sahiptir:

- *C:\Kullanıcılar\Kullanıcı Adı\Belgeler\Visual Studio 2017\Şablonlar\ProjectTemplates\Visual C #*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*

Örneğin, aşağıdaki dizin C# için kullanıcı proje şablonlarına sahiptir:

- *C:\Kullanıcılar\Kullanıcı Adı\Belgeler\Visual Studio 2019\Templates\ProjectTemplates\Visual C #*

::: moniker-end

> [!TIP]
> **Araç** > **Seçenekleri** > **Projeleri ve Çözüm** > **Konumları'nda**kullanıcı şablonları için bilinen konumu değiştirebilirsiniz.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Şablonları düzenleme

**Yeni Proje** ve Yeni **Öğe Ekle** iletişim kutularındaki kategoriler, yüklenen şablon ve kullanıcı şablonu konumlarında bulunan dizin yapılarını yansıtır. Kullanıcı şablonları, kullanıcı şablondizine yeni klasörler ekleyerek kendi kategorilerinde düzenlenebilir. **Yeni Proje** ve Yeni **Öğe Ekle** iletişim kutuları, kullanıcı şablonu kategorilerinde yaptığınız değişiklikleri gösterir.

> [!NOTE]
> Programlama dili düzeyinde yeni bir kategori oluşturamazsınız. Yeni kategoriler yalnızca her dilde oluşturulabilir.

### <a name="create-new-user-project-template-categories"></a>Yeni kullanıcı projesi şablon kategorileri oluşturma

1. Kullanıcı projesi şablon dizini programlama dili klasöründe bir klasör oluşturun. Örneğin, C# proje şablonları için bir **HelloWorld** kategorisi oluşturmak için aşağıdaki dizini oluşturun:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Bu kategoriiçin tüm şablonları yeni klasöre yerleştirin.

1. **Dosya** menüsünde **Yeni** > **Proje'yi**seçin.

   **HelloWorld** **kategorisi,** **Yüklenen** > **Visual C#** altında Yeni Proje iletişim kutusunda görünür.

### <a name="create-new-user-item-template-categories"></a>Yeni kullanıcı öğesi şablonu kategorileri oluşturma

1. Kullanıcı öğesi şablon dizini programlama dili klasöründe bir klasör oluşturun. Örneğin, C# öğesi şablonları için bir **HelloWorld** kategorisi oluşturmak için aşağıdaki dizini oluşturun:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Bu kategoriiçin tüm şablonları yeni klasöre yerleştirin.

1. Proje oluşturun veya varolan bir projeyi açın. Ardından, **Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.

   **HelloWorld** **kategorisi, Yüklü** > **Görsel C# Öğeleri'nin**altında Yeni Öğe **Ekle** iletişim kutusunda görünür.

### <a name="display-templates-in-parent-categories"></a>Şablonları üst kategorilerde görüntüleme

`NumberOfParentCategoriesToRollUp` *.vstemplate* dosyasındaki öğeyi kullanarak alt kategorilerdeki şablonların üst kategorilerde görüntülenmesini sağlayabilirsiniz. Bu adımlar proje şablonları ve öğe şablonları için aynıdır.

1. Şablonu içeren *.zip* dosyasını bulun.

1. *.zip* dosyasını ayıklayın.

1. *.vstemplate* dosyasını Visual Studio'da açın.

1. Öğeye `TemplateData` bir `NumberOfParentCategoriesToRollUp` öğe ekleyin. Örneğin, aşağıdaki kod şablonu üst kategoride görünür kılar, ancak daha yüksek değildir.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. *.vstemplate* dosyasını kaydedin ve kapatın.

1. Şablonunuzdaki dosyaları seçin, seçimi sağ tıklatın ve > **Sıkıştırılmış (sıkıştırılmış) klasörüne Gönder'i**seçin. **Send to**

   Dosyalar *bir .zip* dosyasına sıkıştırılır.

1. Çıkarılan şablon dosyalarını ve eski şablon *.zip* dosyasını silin.

1. Silinen *.zip* dosyası olan dizine yeni *.zip* dosyasını koyun.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Visual Studio şablon şeması başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Visual Studio şablonları)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Nasıl yapılı: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Nasıl yapılı: Öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
