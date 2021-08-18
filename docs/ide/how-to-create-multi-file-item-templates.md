---
title: Çok dosyalı öğe şablonları oluşturma
description: Birden çok dosyadan Visual Studio şablon oluşturma hakkında bilgi.
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
ms.openlocfilehash: c98b811f3bc2daf2048cd70b14a1060088fa1c32
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109181"
---
# <a name="how-to-create-multi-file-item-templates"></a>Nasıl kullanılır: Çok dosyalı öğe şablonları oluşturma

Öğe şablonları yalnızca bir öğe belirtse de bazen öğe birden çok dosyadan yapılır. Örneğin, Windows Forms öğe şablonu aşağıdaki üç dosya gerektirir:

- Formun kodunu içeren bir dosya

- Form için tasarımcı bilgilerini içeren bir dosya

- Form için ekli kaynakları içeren bir dosya

Çok dosyalı öğe şablonları, öğe oluşturulduğunda doğru dosya uzantılarının kullanıldığından emin olmak için parametreler gerektirir. Şablonu Dışarı Aktarma Sihirbazı'nı kullanarak çok dosyalı bir şablon oluşturursanız, bu parametreler otomatik olarak oluşturulur ve başka düzenleme gerekmez.

## <a name="use-the-export-template-wizard"></a>Şablonu Dışarı Aktarma Sihirbazı'nı kullanma

Tek dosyalı öğe şablonuyla aynı şekilde çok dosyalı bir öğe şablonu oluşturabilirsiniz. Bkz. [Nasıl kullanılır: Öğe şablonları oluşturma.](../ide/how-to-create-item-templates.md) Sihirbazın **Dışarı Aktarılacak** Öğeyi Seç sayfasında, bağımlı dosyaları olan dosyayı seçin (örneğin, Windows Forms form dosyası). Sihirbaz, şablona tasarımcı ve kaynak dosyaları gibi bağımlı dosyaları otomatik olarak içerir.

## <a name="manually-create-a-multi-file-item-template"></a>El ile çok dosyalı öğe şablonu oluşturma

1. Tek dosyalı bir öğe şablonunu el ile oluşturarak öğe şablonunu oluşturun, ancak çok dosyalı öğeyi oluşturan her dosyayı dahil edebilirsiniz.

1. *.vstemplate* XML dosyasında, her bir dosya için bir öğe ekleyin ve `ProjectItem` bu `TargetFileName` öğeye bir öznitelik ekleyin. Özniteliğin değerini `TargetFileName` *$fileinputname$ olarak ayarlayın. FileExtension*, burada *FileExtension,* şablona dahil edilen dosyanın dosya uzantısıdır. Örnek:

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
     > Bu şablondan türetilen bir öğe bir projeye eklenmiştir, dosya adları kullanıcının Yeni Öğe Ekle iletişim kutusuna girdiği **addan** türetilen.

1. Şablonunuzla birlikte dahil edilecek dosyaları seçin, seçime sağ tıklayın ve Sıkıştırılmış  >  **(sıkıştırılmış) klasöre Gönder'i seçin.**

   Seçtiğiniz dosyalar bir.zip *sıkıştırılır.*

1. Kullanıcı *.zip* şablonu konumunu kopyalayın. Varsayılan olarak dizin *%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ItemTemplates dizinidir.* Daha fazla bilgi için, [bkz. How to: Locate and organize templates](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Dosyayı Visual Studio sonra yeniden açın.

1. Yeni proje oluşturun veya var olan bir projeyi açın ve yeni öğe **Project** seçin veya  >   Ctrl Shift A  + **tuşlarına** + **basın.**

   Çok dosyalı öğe şablonu Yeni Öğe **Ekle iletişim kutusunda** görünür.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, Windows Forms şablonu gösterir. Bu şablona göre bir öğe oluşturulduğunda, oluşturulan üç dosyanın adları Yeni Öğe Ekle iletişim kutusuna **girilen adla** eş görünür.

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
- [Nasıl kullanılır: Öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Nasıl olur: Şablonda parametrelerin yerini ekleme](../ide/how-to-substitute-parameters-in-a-template.md)
