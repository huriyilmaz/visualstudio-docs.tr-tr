---
title: Çok dosya öğesi şablonları oluşturma
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 82047b4a49db4edbea4ce965d1987f87a799a9f7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655938"
---
# <a name="how-to-create-multi-file-item-templates"></a>Nasıl yapılır: birden çok dosya öğesi şablonları oluşturma

Öğe şablonları yalnızca bir öğe belirtebilir, ancak bazen öğe birden çok dosyadan oluşur. Örneğin, bir Windows Forms öğesi şablonu aşağıdaki üç dosyayı gerektirir:

- Formun kodunu içeren bir dosya

- Form için tasarımcı bilgilerini içeren bir dosya

- Form için gömülü kaynakları içeren bir dosya

Birden çok dosya öğesi şablonları, öğe oluşturulduğunda doğru dosya uzantılarının kullanıldığından emin olmak için parametreler gerektirir. **Şablonu dışarı aktarma Sihirbazı 'nı**kullanarak çok sunuculu bir öğe şablonu oluşturursanız, bu parametreler otomatik olarak oluşturulur ve başka bir Düzenle gerekli değildir.

## <a name="use-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'Nı kullanma

Birden çok dosya öğesi şablonunu tek bir dosya öğesi şablonuyla aynı şekilde oluşturabilirsiniz. Bkz. [nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md). Sihirbazın **dışarı aktarılacağı öğeyi seçin** sayfasında, bağımlı dosyaları olan dosyayı seçin (örneğin, bir Windows Forms form dosyası). Sihirbaz, şablonda tasarımcı ve kaynak dosyaları gibi herhangi bir bağımlı dosyayı otomatik olarak içerir.

## <a name="manually-create-a-multi-file-item-template"></a>El ile birden çok dosya öğesi şablonu oluşturma

1. Bir tek dosya öğesi şablonunu el ile oluşturacağınız, ancak çoklu dosya öğesini oluşturan her dosyayı dahil ettiğiniz için öğe şablonunu oluşturun.

1. *. Vstemplate* XML dosyasında her bir dosya için bir `ProjectItem` öğesi ekleyin ve bu öğeye bir `TargetFileName` özniteliği ekleyin. @No__t_0 özniteliğinin değerini *$fileinputname $ olarak ayarlayın. FileExtension*, burada *FileExtension* , şablonda yer alan dosyanın dosya uzantısıdır. Örneğin:

    ```xml
    <ProjectItem TargetFileName="$fileinputname$.vb">
        Form1.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
        Form1.Designer.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.resx">
        Form1.resx
    </ProjectItem>
    ```

     > [!NOTE]
     > Bu şablondan türetilen bir öğe projeye eklendiğinde, dosya adları kullanıcının **Yeni öğe Ekle** iletişim kutusuna girdiği adından türetilir.

1. Şablonunuza dahil edilecek dosyaları seçin, seçime sağ tıklayın ve  > **Sıkıştırılmış (daraltılmış) klasöre** **Gönder** ' i seçin.

   Seçtiğiniz dosyalar bir *. zip* dosyasında sıkıştırılır.

1. *. Zip* dosyasını Kullanıcı öğesi şablonu konumuna kopyalayın. Varsayılan olarak dizin, *%userprofile%\, \<Version \> \Templates\ıtemtemplates*dizinidir. Daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Visual Studio 'Yu kapatın ve yeniden açın.

1. Yeni bir proje oluşturun veya var olan bir projeyi açın ve **proje**  > **Yeni öğe Ekle** ' yi seçin veya **CTRL** +**SHIFT** +**a**'ya basın.

   Çoklu dosya öğesi şablonu, **Yeni öğe Ekle** iletişim kutusunda görünür.

## <a name="example"></a>Örnek

Aşağıdaki örnekte bir Windows Forms şablonu gösterilmektedir. Bu şablonu temel alan bir öğe oluşturulduğunda, oluşturulan üç dosyanın adları **Yeni öğe Ekle** iletişim kutusuna girilen adla eşleşir.

```xml
<VSTemplate Version="2.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-file Item Template</Name>
        <Icon>Icon.ico</Icon>
        <Description>An example of a multi-file item template</Description>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">
            Form1.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
            Form1.Designer.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.resx">
            Form1.resx
        </ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Nasıl yapılır: şablonda parametreleri değiştirme](../ide/how-to-substitute-parameters-in-a-template.md)