---
title: Öğe şablonları oluşturma
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d213ef7cd1c45043efbaad9fca4317f7a693bf4f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655855"
---
# <a name="how-to-create-item-templates"></a>Nasıl yapılır: öğe şablonları oluşturma

Bu makalede, **şablonu dışarı aktarma Sihirbazı 'nı**kullanarak bir öğe şablonu oluşturma işlemi gösterilir. Şablonunuz birden çok dosyadan oluşu, bkz. [nasıl yapılır: birden çok dosya öğesi şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md).

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Yeni öğe Ekle iletişim kutusuna bir öğe şablonu ekleyin

1. Visual Studio 'da bir proje oluşturun veya açın.

1. Projeye bir öğe ekleyin ve isterseniz dosyayı değiştirin.

1. Kod dosyasını parametre değiştirmenin nerede olması gerektiğini belirtecek şekilde değiştirin. Daha fazla bilgi için bkz. [nasıl yapılır: şablonda parametreleri değiştirme](../ide/how-to-substitute-parameters-in-a-template.md).

1. **Proje** menüsünde, **şablonu dışarı aktar**' ı seçin.

1. **Şablon türü seç** sayfasında, **öğe şablonu**' nu seçin, öğeyi içeren projeyi seçin ve ardından **İleri**' yi seçin.

1. **Dışarı aktarılacak öğeyi seçin** sayfasında, şablon oluşturmak istediğiniz öğeyi seçin ve ardından **İleri**' yi seçin.

1. **Öğe başvurularını Seç** sayfasında, şablona dahil edilecek derleme başvurularını seçin ve ardından **İleri**' yi seçin.

1. **Şablon seçeneklerini seçin** sayfasında, şablon adını ve isteğe bağlı açıklamayı, simge görüntüsünü ve önizleme görüntüsünü girip **son**' u seçin.

    Şablon dosyaları bir *. zip* dosyasına eklenir ve sihirbazda belirttiğiniz dizine kopyalanır. Varsayılan konum, *%userprofile%\, \<version \> \verden aktarılmış şablonlar*' dır.

1. Şablonu **dışarı aktarma sihirbazında** **şablonu otomatik olarak Visual Studio 'ya aktar** seçeneğini seçmediyseniz, dışarı aktarılan şablonu bulun. Ardından, bunu Kullanıcı öğesi şablon dizinine kopyalayın. Varsayılan konum, *%userprofile%\, \<version \> \Templates\ıtemtemplates dizinidir*.

1. Visual Studio 'Yu kapatın ve yeniden açın.

1. Yeni bir proje oluşturun veya var olan bir projeyi açın ve **proje**  > **Yeni öğe Ekle** ' yi seçin veya **CTRL** +**SHIFT** +**a**'ya basın.

   Öğe şablonu **Yeni öğe Ekle** iletişim kutusunda görünür. **Şablonu dışarı aktar sihirbazında**bir açıklama eklediyseniz, açıklama iletişim kutusunun sağ tarafında görünür.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Bir Evrensel Windows uygulaması projesinde kullanılacak öğe şablonunu etkinleştirin

Sihirbaz temel şablon oluşturma işinin çoğunu yapar, ancak çoğu durumda, şablonu verdikten sonra *. vstemplate* dosyasını el ile değiştirmeniz gerekir. Örneğin, bir Evrensel Windows uygulaması projesi için öğenin **Yeni öğe Ekle** iletişim kutusunda görünmesini istiyorsanız birkaç ek adım gerçekleştirmeniz gerekir.

1. Bir öğe şablonunu dışarı aktarmak için önceki bölümdeki adımları izleyin.

1. Oluşturulan *. zip* dosyasını ayıklayın ve Visual Studio 'da *. vstemplate* dosyasını açın.

1. Bir C# Evrensel Windows projesi IÇIN aşağıdaki XML 'i `<TemplateData>` öğesi içine ekleyin:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. Visual Studio 'da *. vstemplate* dosyasını kaydedin ve kapatın.

1. *. Vstemplate* dosyasını kopyalayıp *. zip* dosyasına yapıştırın.

     **Dosya Kopyala** iletişim kutusu görüntülenirse, **Kopyala ve Değiştir** seçeneğini belirleyin.

Artık, **Yeni öğe Ekle** iletişim kutusundan bu şablonu temel alan bir öğeyi Evrensel Windows projesine ekleyebilirsiniz.

## <a name="enable-templates-for-specific-project-subtypes"></a>Belirli proje alt türleri için şablonları etkinleştir

Şablonunuzun yalnızca Windows, Office, veritabanı veya Web gibi belirli proje alt türleri için görünmesini belirtebilirsiniz.

1. Öğe şablonu için *. vstemplate* dosyasında `ProjectType` öğesini bulun.

1. @No__t_1 öğeden hemen sonra bir [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi ekleyin.

1. Öğesinin metin değerini aşağıdaki değerlerden birine ayarlayın:

    - Windows
    - Office
    - Veritabanı
    - Web

Örneğin: `<ProjectSubType>Database</ProjectSubType>`.

Aşağıdaki örnekte, **Office** projeleri için bir öğe şablonu gösterilmektedir.

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

## <a name="manually-create-an-item-template"></a>El ile bir öğe şablonu oluşturun

Bazı durumlarda, sıfırdan el ile bir öğe şablonu oluşturmak isteyebilirsiniz.

1. Proje ve proje öğesi oluşturun.

2. Proje öğesi bir şablon olarak kaydedilmeye hazırlanana kadar, Proje öğesini değiştirin.

3. Kod dosyasını, her yerde parametre değiştirmenin nerede gerçekleşeceğini belirtecek şekilde değiştirin. Parametre değiştirme hakkında daha fazla bilgi için bkz [. nasıl yapılır: şablonda parametreleri değiştirme.](../ide/how-to-substitute-parameters-in-a-template.md)

4. Bir XML dosyası oluşturun ve bunu proje öğesi dosyanızdaki aynı dizinde *. vstemplate* dosya uzantısıyla kaydedin.

5. Öğe şablonu meta verileri sağlamak için *. vstemplate* XML dosyasını düzenleyin. Daha fazla bilgi için bkz. [Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md) ve önceki bölümdeki örnek.

6. *. Vstemplate* dosyasını kaydedin ve kapatın.

7. **Windows Gezgini**'nde, şablonunuza dahil etmek istediğiniz dosyaları seçin. Seçime sağ tıklayın ve  > **Sıkıştırılmış (daraltılmış) klasöre** **Gönder** ' i seçin. Seçtiğiniz dosyalar bir *. zip* dosyasında sıkıştırılır.

::: moniker range="vs-2017"

8. *. Zip* dosyasını kopyalayın ve Kullanıcı öğesi şablonu konumuna yapıştırın. Varsayılan dizin, *%userprofile%\, Studio 2017 \ Templates\ıtemtemplates*dizinidir. Daha fazla bilgi için bkz. [nasıl yapılır: proje ve öğe şablonlarını bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

8. *. Zip* dosyasını kopyalayın ve Kullanıcı öğesi şablonu konumuna yapıştırın. Varsayılan dizin, *%userprofile%\, Studio 2019 \ Templates\ıtemtemplates*dizinidir. Daha fazla bilgi için bkz. [nasıl yapılır: proje ve öğe şablonlarını bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: birden çok dosya öğesi şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
