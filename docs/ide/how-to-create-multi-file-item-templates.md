---
title: Çok dosyalı öğe şablonları oluşturma
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e8a6e5358a87e3d64b341c89b8ffd4cd3cf3e325
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593739"
---
# <a name="how-to-create-multi-file-item-templates"></a>Nasıl yapılı: Çok dosyalı öğe şablonları oluşturma

Öğe şablonları yalnızca bir öğe belirtebilir, ancak bazen öğe birden çok dosyadan oluşur. Örneğin, Bir Windows Forms öğe şablonu aşağıdaki üç dosyayı gerektirir:

- Formun kodunu içeren bir dosya

- Formun tasarımcı bilgilerini içeren bir dosya

- Form için katıştırılmış kaynakları içeren bir dosya

Çok dosyalı madde şablonları, öğe oluşturulduğunda doğru dosya uzantılarının kullanıldığından emin olmak için parametreler gerektirir. **Dışa Aktarma Şablonu**Sihirbazı'nı kullanarak çok dosyalı bir öğe şablonu oluşturursanız, bu parametreler otomatik olarak oluşturulur ve başka bir düzenleme gerekmez.

## <a name="use-the-export-template-wizard"></a>Dışa Aktarma Şablonu Sihirbazı'nı kullanma

Tek dosyalı öğe şablonu yla aynı şekilde çok dosyalı bir öğe şablonu oluşturabilirsiniz. Bkz. [Nasıl?](../ide/how-to-create-item-templates.md) Sihirbazın **Dışa Aktar'ı Seç** sayfasında, bağımlı dosyaları olan dosyayı (örneğin, Windows Forms form dosyası) seçin. Sihirbaz, şablona tasarımcı ve kaynak dosyaları gibi bağımlı dosyaları otomatik olarak içerir.

## <a name="manually-create-a-multi-file-item-template"></a>Çok dosyalı öğe şablonu el ile oluşturma

1. Tek dosyalı öğe şablonu el ile oluşturacağınız, ancak çok dosyalı öğeyi oluşturan her dosyayı eklediğiniz için öğe şablonu oluşturun.

1. *.vstemplate* XML dosyasında, `ProjectItem` her dosya için bir öğe `TargetFileName` ekleyin ve bu öğeye bir öznitelik ekleyin. Özniteliğin `TargetFileName` değerini $fileinputname TL olarak *ayarlayın. FileExtension*, *FileExtension* şablona dahil ediliyor dosyanın dosya uzantısı olduğu. Örnek:

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
     > Bu şablondan türetilen bir öğe projeye eklendiğinde, dosya adları kullanıcının **Yeni Öğe Ekle** iletişim kutusuna girdiği addan türetilir.

1. Şablonunuza eklenecek dosyaları seçin, seçimi sağ tıklatın ve > **Sıkıştırılmış (sıkıştırılmış) klasörüne gönder'i**seçin. **Send to**

   Seçtiğiniz dosyalar *bir .zip* dosyasına sıkıştırılır.

1. *.zip* dosyasını kullanıcı öğesi şablonu konumuna kopyalayın. Varsayılan olarak, dizin *%USERPROFILE%\Documents\Visual \<\>Studio Version \Templates\ItemTemplates'tir.* Daha fazla bilgi için [bkz: Şablonları bulma ve düzenleme.](../ide/how-to-locate-and-organize-project-and-item-templates.md)

1. Visual Studio'yı kapatın ve yeniden açın.

1. Yeni bir proje oluşturun veya varolan bir **Project**projeyi açın ve ardından > **Project Add New Item'i** seçin veya **Ctrl**+**Shift**+A**tuşuna**basın.

   Çok dosyalı öğe şablonu **Yeni Öğe Ekle** iletişim kutusunda görünür.

## <a name="example"></a>Örnek

Aşağıdaki örnekte bir Windows Forms şablonu gösterilmektedir. Bu şablona dayalı bir öğe oluşturulduğunda, oluşturulan üç dosyanın **adları, Yeni Öğe Ekle** iletişim kutusunda girilen adla eşleşir.

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
- [Nasıl yapılı: Öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Nasıl kullanılır: Şablondaki yedek parametreler](../ide/how-to-substitute-parameters-in-a-template.md)
