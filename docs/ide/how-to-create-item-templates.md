---
title: Öğe şablonları oluşturma
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 62004c5c96fa708f98ab49f4810ec2fc1c38eadc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594727"
---
# <a name="how-to-create-item-templates"></a>Nasıl yapılı: Öğe şablonları oluşturma

Bu makalede, **Dışa Aktarma Şablonu**Sihirbazı'nı kullanarak bir madde şablonu nasıl oluşturulabileceğinizi gösterir. Şablonunuzun birden çok dosyadan oluşması durumunda, [bkz.](../ide/how-to-create-multi-file-item-templates.md)

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna öğe şablonu ekleme

1. Visual Studio'da bir proje oluşturun veya açın.

1. Projeye bir öğe ekleyin ve isterseniz değiştirin.

1. Parametre değişiminin nerede yapılması gerektiğini belirtmek için kod dosyasını değiştirin. Daha fazla bilgi için [bkz: Şablondaki parametreleri değiştirin.](../ide/how-to-substitute-parameters-in-a-template.md)

1. **Proje** menüsünde **Dışa Aktarma Şablonu'nu**seçin.

1. Şablon **Türü Seç** sayfasında **Öğe Şablonu'nu**seçin, öğeyi içeren projeyi seçin ve **sonra İleri'yi**seçin.

1. **Dışa Aktarma Öğesi Seç** sayfasında, şablon oluşturmak istediğiniz öğeyi seçin ve sonra **İleri'yi**seçin.

1. Madde **Başvurularını Seç** sayfasında şablona eklemek için derleme başvurularını seçin ve sonra **İleri'yi**seçin.

1. Şablon **Seçeneklerini Seç** sayfasında şablon adını ve isteğe bağlı açıklamayı, simge görüntüsünü ve önizleme resmini girin ve ardından **Bitir'i**seçin.

    Şablon dosyaları bir *.zip* dosyasına eklenir ve sihirbazda belirttiğiniz dizine kopyalanır. Varsayılan konum *%USERPROFILE%\Documents\Visual \<Studio\>sürümü \Dışa Aktarılan Şablonlarım.*

1. Seçeneği seçmediyseniz, **şablonu Dışa** Aktarma **Şablonu**Sihirbazı'nda Visual Studio'ya otomatik olarak aktarın, dışa aktarılan şablonu bulun. Ardından, kullanıcı öğesi şablon dizini kopyalayın. Varsayılan konum *%USERPROFILE%\Documents\Visual \<Studio\>sürümü \Şablonlar\ItemTemplates'* tir.

1. Visual Studio'yı kapatın ve yeniden açın.

1. Yeni bir proje oluşturun veya varolan bir **Project**projeyi açın ve ardından > **Project Add New Item'i** seçin veya **Ctrl**+**Shift**+A**tuşuna**basın.

   Öğe şablonu Yeni **Öğe Ekle** iletişim kutusunda görünür. **Dışa Aktarma Şablonu**Sihirbazı'na bir açıklama eklediyseniz, açıklama iletişim kutusunun sağ tarafında görüntülenir.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Öğe şablonunun Evrensel Windows Uygulaması projesinde kullanılmasını etkinleştirme

Sihirbaz, temel bir şablon oluşturmak için çok fazla çalışma yapar, ancak çoğu durumda şablonu dışa aktardıktan sonra *.vstemplate* dosyasını el ile değiştirmeniz gerekir. Örneğin, öğenin Evrensel Windows Uygulaması projesi için **Yeni Öğe Ekle** iletişim kutusunda görünmesini istiyorsanız, birkaç ek adım gerçekleştirmeniz gerekir.

1. Madde şablonu dışa aktarmak için önceki bölümdeki adımları izleyin.

1. Oluşturulan *.zip* dosyasını ayıklayın ve *.vstemplate* dosyasını Visual Studio'da açın.

1. C# Universal Windows projesi için öğenin içine `<TemplateData>` aşağıdaki XML'i ekleyin:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. Visual Studio'da *.vstemplate* dosyasını kaydedin ve kapatın.

1. *.vstemplate* dosyasını kopyalayıp *.zip* dosyasına yapıştırın.

     **Dosyayı Kopyala** iletişim kutusu görünüyorsa, **Kopyala ve Değiştir** seçeneğini belirleyin.

Artık **Yeni Öğe Ekle** iletişim kutusundan Evrensel Windows projesine bu şablonu temel alan bir öğe ekleyebilirsiniz.

## <a name="enable-templates-for-specific-project-subtypes"></a>Belirli proje alt türleri için şablonları etkinleştirme

Şablonunuzun yalnızca Windows, Office, Veritabanı veya Web gibi belirli proje alt türleri için görünmesi gerektiğini belirtebilirsiniz.

1. Öğe `ProjectType` şablonu için *.vstemplate* dosyasındaki öğeyi bulun.

1. Öğeden `ProjectType` hemen sonra [projectsubtype](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi ekleyin.

1. Öğenin metin değerini aşağıdaki değerlerden birine ayarlayın:

    - Windows
    - Office
    - Database
    - Web

Örneğin: `<ProjectSubType>Database</ProjectSubType>`.

Aşağıdaki örnek, **Office** projeleri için bir öğe şablonu gösterir.

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

## <a name="manually-create-an-item-template"></a>Öğe şablonu el ile oluşturma

Bazı durumlarda, sıfırdan el ile bir öğe şablonu oluşturmak isteyebilirsiniz.

1. Proje ve proje öğesi oluşturun.

2. Proje öğesini şablon olarak kaydedilecek hazır olana kadar değiştirin.

3. Parametre değişiminin nerede olması gerektiğini belirtmek için kod dosyasını değiştirin. Parametre değiştirme hakkında daha fazla bilgi için [bkz.](../ide/how-to-substitute-parameters-in-a-template.md)

4. Bir XML dosyası oluşturun ve proje öğesi dosyanızla aynı dizinde *.vstemplate* dosya uzantısı ile kaydedin.

5. Madde şablonu meta verilerini sağlamak için *.vstemplate* XML dosyasını edin. Daha fazla bilgi için şablon [şeması başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md) ve önceki bölümdeki örneğe bakın.

6. *.vstemplate* dosyasını kaydedin ve kapatın.

7. **Windows Gezgini'nde**şablonunuza eklemek istediğiniz dosyaları seçin. Seçimi sağ tıklatın ve > **Sıkıştırılmış (sıkıştırılmış) klasörüne** **gönder'i**seçin. Seçtiğiniz dosyalar *bir .zip* dosyasına sıkıştırılır.

::: moniker range="vs-2017"

8. *.zip* dosyasını kopyalayın ve kullanıcı öğesi şablonu konumuna yapıştırın. Varsayılan dizin *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates'* tir. Daha fazla bilgi için [bkz: Proje ve öğe şablonlarını bulma ve düzenleme.](../ide/how-to-locate-and-organize-project-and-item-templates.md)

::: moniker-end

::: moniker range=">=vs-2019"

8. *.zip* dosyasını kopyalayın ve kullanıcı öğesi şablonu konumuna yapıştırın. Varsayılan dizin *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates'* tir. Daha fazla bilgi için [bkz: Proje ve öğe şablonlarını bulma ve düzenleme.](../ide/how-to-locate-and-organize-project-and-item-templates.md)

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılı: Çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio şablon şeması başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
