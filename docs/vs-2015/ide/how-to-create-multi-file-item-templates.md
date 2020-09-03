---
title: 'Nasıl yapılır: birden çok dosya öğesi şablonları oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e70039f361ac3410a8ddcccb0f139d8bdcb32ed9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668086"
---
# <a name="how-to-create-multi-file-item-templates"></a>Nasıl Yapılır: Çok Dosyalı Şablonlar Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğe şablonları yalnızca bir öğe belirtebilir, ancak bazen öğe birden çok dosyadan oluşur. Örneğin, Visual Basic için Windows Forms bir öğe şablonu aşağıdaki üç dosyayı gerektirir:

- Formun kodunu içeren bir. vb dosyası.

- Form için tasarımcı bilgilerini içeren bir. Designer. vb dosyası.

- Form için gömülü kaynakları içeren bir. resx dosyası.

  Çoklu dosya öğesi şablonları, öğesinde öğe oluşturulduğunda doğru dosya adı uzantılarının kullanıldığından emin olmak için parametreler gerektirir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . **Şablon dışarı aktarma** Sihirbazı 'nı kullanarak bir öğe şablonu oluşturursanız, bu parametreler otomatik olarak oluşturulur ve başka bir Düzenle gerekli değildir. Aşağıdaki adımlarda, doğru dosya adı uzantılarının oluşturulduğundan emin olmak için parametrelerin nasıl kullanılacağı açıklanmaktadır.

### <a name="to-manually-create-a-multi-file-item-template"></a>Birden çok dosya öğesi şablonunu el ile oluşturmak için

1. Tek dosya öğe şablonu oluşturacağınız için öğe şablonunu oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md).

2. `TargetFileName`Her öğeye öznitelik ekleyin `ProjectItem` . `TargetFileName`Özniteliklerin değerlerini $fileinputname $ olarak ayarlayın.* FileExtension*, burada *FileExtension* , şablonda yer alan dosyanın dosya adı uzantısıdır. Örneğin:

    ```
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

     Bu şablondan türetilen bir öğe projeye eklendiğinde, dosya adları kullanıcının **Yeni öğe Ekle** iletişim kutusuna girdiği adı temel alır.

3. Şablonunuza dahil edilecek dosyaları seçin, seçime sağ tıklayın, **Gönder ' e**tıklayın ve ardından **Sıkıştırılmış (daraltılmış) klasör**' e tıklayın. Seçtiğiniz dosyalar bir. zip dosyasında sıkıştırılır.

4. . Zip dosyasını Kullanıcı öğesi şablonu konumuna yerleştirin. Varsayılan olarak, dizin, \K\studio *sürümü*\ \\ Daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnekte bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Windows Forms şablonu gösterilmektedir. Bu şablonu temel alan bir öğe oluşturulduğunda, oluşturulan üç dosyanın adları **Yeni öğe Ekle** iletişim kutusuna girilen adla eşleşir.

```
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

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md) [nasıl yapılır: öğe şablonları](../ide/how-to-create-item-templates.md) [şablon parametreleri](../ide/template-parameters.md) oluşturma [nasıl yapılır: şablonda parametreleri değiştirme](../ide/how-to-substitute-parameters-in-a-template.md)
