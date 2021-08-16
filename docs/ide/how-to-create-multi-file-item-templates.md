---
title: Çok dosya öğesi şablonları oluşturma
description: birden çok dosyadan oluşan Visual Studio bir öğe şablonu oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 0917faeccdabf8af63e03b4bdf061d39dc31057f85fddca341e14f81c111e205
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372887"
---
# <a name="how-to-create-multi-file-item-templates"></a>Nasıl yapılır: birden çok dosya öğesi şablonları oluşturma

Öğe şablonları yalnızca bir öğe belirtebilir, ancak bazen öğe birden çok dosyadan oluşur. örneğin, bir Windows Forms öğesi şablonu aşağıdaki üç dosyayı gerektirir:

- Formun kodunu içeren bir dosya

- Form için tasarımcı bilgilerini içeren bir dosya

- Form için gömülü kaynakları içeren bir dosya

Birden çok dosya öğesi şablonları, öğe oluşturulduğunda doğru dosya uzantılarının kullanıldığından emin olmak için parametreler gerektirir. **Şablonu dışarı aktarma Sihirbazı 'nı** kullanarak çok sunuculu bir öğe şablonu oluşturursanız, bu parametreler otomatik olarak oluşturulur ve başka bir Düzenle gerekli değildir.

## <a name="use-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'Nı kullanma

Birden çok dosya öğesi şablonunu tek bir dosya öğesi şablonuyla aynı şekilde oluşturabilirsiniz. Bkz. [nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md). sihirbazın **dışarı aktarılacağı öğeyi seçin** sayfasında, bağımlı dosyaları olan dosyayı seçin (örneğin, bir Windows Forms form dosyası). Sihirbaz, şablonda tasarımcı ve kaynak dosyaları gibi herhangi bir bağımlı dosyayı otomatik olarak içerir.

## <a name="manually-create-a-multi-file-item-template"></a>El ile birden çok dosya öğesi şablonu oluşturma

1. Bir tek dosya öğesi şablonunu el ile oluşturacağınız, ancak çoklu dosya öğesini oluşturan her dosyayı dahil ettiğiniz için öğe şablonunu oluşturun.

1. *. Vstemplate* XML dosyasında `ProjectItem` her bir dosya için bir öğe ekleyin ve `TargetFileName` Bu öğeye bir öznitelik ekleyin. `TargetFileName`Özniteliğin değerini *$fileinputname $ olarak ayarlayın. FileExtension*, burada *FileExtension* , şablonda yer alan dosyanın dosya uzantısıdır. Örnek:

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

1. Şablonunuza dahil edilecek dosyaları seçin, seçime sağ tıklayın ve   >  **Sıkıştırılmış (daraltılmış) klasöre** Gönder ' i seçin.

   Seçtiğiniz dosyalar bir *.zip* dosyasında sıkıştırılır.

1. *.zip* dosyasını Kullanıcı öğesi şablonu konumuna kopyalayın. varsayılan olarak, dizin *%userprofile%\documents\ Visual Studio \<Version\> \templates\ıtemtemplates* şeklindedir. Daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Visual Studio kapatın ve yeniden açın.

1. yeni bir proje oluşturun veya var olan bir projeyi açın, sonra **Project**  >  **yeni öğe ekle** ' yi seçin veya **Ctrl** + **+ shıft** tuşuna basın + .

   Çoklu dosya öğesi şablonu, **Yeni öğe Ekle** iletişim kutusunda görünür.

## <a name="example"></a>Örnek

aşağıdaki örnekte bir Windows Forms şablonu gösterilmektedir. Bu şablonu temel alan bir öğe oluşturulduğunda, oluşturulan üç dosyanın adları **Yeni öğe Ekle** iletişim kutusuna girilen adla eşleşir.

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
