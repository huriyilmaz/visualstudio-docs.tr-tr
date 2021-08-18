---
title: Web şablonları oluşturma
description: El ile bir Web şablonu oluşturmayı ve şablonun kullandığı programlama dilini belirlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 05a3bbe59c290ade7871d63a7a89d900638c5afe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101706"
---
# <a name="how-to-manually-create-web-templates"></a>Nasıl yapılır: Web şablonlarını elle oluşturma

Web şablonu oluşturmak diğer şablon türlerini oluşturmaktan farklıdır. Web projesi şablonları **Yeni Web sitesi Ekle** iletişim kutusunda göründüğünden ve Web projesi öğeleri programlama diline göre sınıflandırıldığından, *vstemplate* dosyasının şablonu bir Web şablonu olarak belirtmesi ve programlama dilini tanımlaması gerekir.

> [!NOTE]
> Web şablonlarının boş bir *. webproj* dosyası içermesi ve öğenin özniteliğinde *vstemplate* dosyasında başvurulması gerekir `File` `Project` . Web projeleri bir *. proj* proje dosyası gerektirmese de, Web şablonunun düzgün çalışması için bu Saplama dosyasını oluşturmanız gerekir.

## <a name="to-manually-create-a-web-template"></a>El ile bir Web şablonu oluşturmak için

1. Bir Web projesi oluşturun.

2. Projedeki dosyaları değiştirin veya silin ya da projeye yeni dosyalar ekleyin.

3. Bir XML dosyası oluşturun ve bunu, projenizle aynı dizinde bir *vstemplate* dosya adı uzantısıyla kaydedin. Visual Studio projeye eklemeyin.

4. Proje şablonu meta verilerini sağlamak için *vstemplate* XML dosyasını düzenleyin. Daha fazla bilgi için [aşağıdaki örneğe](#example)bakın.

5. `ProjectType` *Vstemplate* dosyasındaki öğesini bulun ve metin değerini olarak ayarlayın `Web` .

6. Öğesini izleyerek `ProjectType` bir `ProjectSubType` öğesi ekleyin ve metin değerini şablonun programlama diline ayarlayın. Programlama dili aşağıdaki değerlerden biri olabilir:

   - Step\chapter
   - VisualBasic

     Örnek:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Şablonunuzda dosyaları seçin (Bu *vstemplate* dosyasını içerir), seçime sağ tıklayın ve   >  **Sıkıştırılmış (daraltılmış) klasöre** Gönder ' i seçin. Dosyalar bir *.zip* dosyasında sıkıştırılır.

8. *.zip* şablon dosyasını Visual Studio proje şablonu dizinine yerleştirin. varsayılan olarak, bu dizin *%userprofile%\documents\ Visual Studio \<Version\> \projecttemplates* şeklindedir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir Web projesi şablonu için temel bir *vstemplate* dosyası gösterilmektedir:

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablon şeması başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
