---
title: Öğe şablonları oluşturma
description: Şablon Dışarı Aktarma Sihirbazı'nı kullanarak bir öğe şablonu oluşturma hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: f2722835f21ac5fb3c3cf2c493943f281921f098
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086150"
---
# <a name="how-to-create-item-templates"></a>Nasıl kullanılır: Öğe şablonları oluşturma

Bu makalede, Şablonu Dışarı Aktarma Sihirbazı'nı kullanarak bir öğe **şablonunun nasıl oluşturul açıklanmıştır.** Şablonunuz birden çok dosyadan oluşursa, [bkz. Nasıl kullanılır: Çok dosyalı öğe şablonları oluşturma.](../ide/how-to-create-multi-file-item-templates.md)

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna öğe şablonu ekleme

1. Proje oluşturma veya proje açma Visual Studio.

1. Projeye bir öğe ekleyin ve 80000000000000000000000000000000000000000

1. Parametre değiştirmenin nerede olması gerektiğini belirtmek için kod dosyasını değiştirme. Daha fazla bilgi için, [bkz. How to: Substitute parameters in a template](../ide/how-to-substitute-parameters-in-a-template.md).

1. Şablon **Project** Dışarı Aktar'ı **seçin.**

1. Şablon **Türünü Seçin sayfasında Öğe** Şablonu'seçin, öğeyi içeren projeyi seçin ve ardından Sonraki'yi **seçin.** 

1. Dışarı **Aktar için Öğe Seç** sayfasında, şablon oluşturmak istediğiniz öğeyi seçin ve ardından Sonraki'yi **seçin.**

1. Öğe **Başvurularını Seç sayfasında,** şablona dahil etmek için derleme başvurularını seçin ve ardından Sonraki'yi **seçin.**

1. Şablon Seçeneklerini **Seçin sayfasında** şablon adını ve isteğe bağlı olarak açıklamayı, simge görüntüsünü ve önizleme görüntüsünü girin ve ardından Son'a **tıklayın.**

    Şablon dosyaları bir.zip *dosyasına* eklenir ve sihirbazda belirttiğiniz dizine kopyalanır. Varsayılan konum *%USERPROFILE%\Documents\Visual Studio \<version\> \Dışarı Aktarıldı Şablonlarım'dır.*

1. Şablonu Dışarı Aktarma Sihirbazı'nda Şablonu otomatik **olarak Visual Studio** seçeneğini **belirlemezseniz,** dışarı aktaran şablonu bulun. Ardından, bunu kullanıcı öğesi şablon dizinine kopyalayın. Varsayılan konum *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ItemTemplates konumundadır.*

1. Dosyayı Visual Studio sonra yeniden açın.

1. Yeni bir proje oluşturun veya var olan bir projeyi açın ve yeni öğe **Project** seçin veya  >   Ctrl Shift A  + **tuşlarına** + **basın.**

   Öğe şablonu Yeni Öğe **Ekle iletişim kutusunda** görünür. Şablonu Dışarı Aktarma **Sihirbazı'nda bir açıklama eklediysanız,** açıklama iletişim kutusunun sağ tarafında görünür.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Öğe şablonunun evrensel uygulama uygulaması projesinde Windows etkinleştirme

Sihirbaz, temel bir şablon oluşturmak için büyük bir çalışma yapar, ancak çoğu durumda şablonu dışarı aktardıktan sonra *.vstemplate* dosyasını el ile değiştirmeniz gerekir. Örneğin, bir Evrensel Uygulama Uygulaması projesi  için Yeni Öğe Ekle iletişim kutusunda öğenin görünmesini Windows birkaç ek adım gerçekleştirmeniz gerekir.

1. Bir öğe şablonunu dışarı aktarma için önceki bölümdeki adımları izleyin.

1. Oluşturulan *.zip* ayıkla ve *.vstemplate* dosyasını dosyanın içinde Visual Studio.

1. C# Universal Windows projesi için öğesinin içine aşağıdaki XML'yi `<TemplateData>` ekleyin:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. Bu Visual Studio *.vstemplate dosyasını kaydedin* ve kapatın.

1. *.vstemplate dosyasını kopyalayıp* dosyanın *.zip* yapıştırın.

     Dosya **Kopyala iletişim** kutusu görüntülenirse Kopyala ve **Değiştir seçeneğini** belirleyin.

Artık Yeni Öğe Ekle iletişim kutusundan bu şablonu temel alan bir Windows Evrensel Uygulama **projesine** eklemek için kullanabilirsiniz.

## <a name="enable-templates-for-specific-project-subtypes"></a>Belirli proje alt türleri için şablonları etkinleştirme

Şablonun yalnızca Windows, Office, Database veya Web gibi belirli proje alt türleri için görünmesi gerektiğini belirtebilirsiniz.

1. Öğe `ProjectType` şablonu için *.vstemplate* dosyasında öğesini bulun.

1. Öğesinin [hemen sonra bir ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi `ProjectType` ekleyin.

1. öğesinin metin değerini aşağıdaki değerlerden biri olarak ayarlayın:

    - Windows
    - Office
    - Veritabanı
    - Web

Örneğin: `<ProjectSubType>Database</ProjectSubType>`.

Aşağıdaki örnekte, projelerle ilgili bir öğe **Office** gösterir.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="manually-create-an-item-template"></a>El ile öğe şablonu oluşturma

Bazı durumlarda, sıfırdan el ile bir öğe şablonu oluşturmak istemeniz gerekebilir.

1. Bir proje ve proje öğesi oluşturun.

2. Proje öğesini şablon olarak kaydedilebilir hale gelene kadar değiştirebilirsiniz.

3. Herhangi bir yerde parametre değiştirmenin nerede gerçekleşmesi gerektiğini belirtmek için kod dosyasını değiştirme. Parametre değiştirme hakkında daha fazla bilgi için [bkz. Nasıl olur: Bir şablonda parametreleri değiştirme.](../ide/how-to-substitute-parameters-in-a-template.md)

4. Bir XML dosyası oluşturun ve proje öğesi dosyanız ile aynı *dizinde bir .vstemplate* dosya uzantısıyla kaydedin.

5. Öğe şablonu *meta verilerini sağlamak için .vstemplate* XML dosyasını düzenleyin. Daha fazla bilgi için [bkz. Şablon şeması başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md) ve önceki bölümdeki örnek.

6. *.vstemplate dosyasını* kaydedin ve kapatın.

7. **Gezgin Windows de,** şablonunuza eklemek istediğiniz dosyaları seçin. Seçime sağ tıklayın ve Sıkıştırılmış  >  **(sıkıştırılmış) klasöre Gönder'i seçin.** Seçtiğiniz dosyalar bir.zip *sıkıştırılır.*

::: moniker range="vs-2017"

8. .zip *dosyasını* kopyalayın ve kullanıcı öğesi şablonu konuma yapıştırın. Varsayılan dizin *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates dizinidir.* Daha fazla bilgi için [bkz. Nasıl kullanılır: Proje ve öğe şablonlarını bulma ve düzenleme.](../ide/how-to-locate-and-organize-project-and-item-templates.md)

::: moniker-end

::: moniker range=">=vs-2019"

8. .zip *dosyasını* kopyalayın ve kullanıcı öğesi şablonu konuma yapıştırın. Varsayılan dizin *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates dizinidir.* Daha fazla bilgi için [bkz. Nasıl kullanılır: Proje ve öğe şablonlarını bulma ve düzenleme.](../ide/how-to-locate-and-organize-project-and-item-templates.md)

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl kullanılır: Çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio şema başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
