---
title: Web şablonları oluşturma
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d121d9b970d8012aaf177c0a232cd21f6fe85d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645824"
---
# <a name="how-to-manually-create-web-templates"></a>Nasıl yapılır: Web şablonlarını elle oluşturma

Web şablonu oluşturmak diğer şablon türlerini oluşturmaktan farklıdır. Web projesi şablonları **Yeni Web sitesi Ekle** iletişim kutusunda göründüğünden ve Web projesi öğeleri programlama diline göre sınıflandırıldığından, *vstemplate* dosyasının şablonu bir Web şablonu olarak belirtmesi ve programlama dilini tanımlaması gerekir.

> [!NOTE]
> Web şablonlarının boş bir *. webproj* dosyası içermesi ve `Project` öğesinin `File` özniteliğinde *vstemplate* dosyasında başvurulması gerekir. Web projeleri bir *. proj* proje dosyası gerektirmese de, Web şablonunun düzgün çalışması için bu Saplama dosyasını oluşturmanız gerekir.

## <a name="to-manually-create-a-web-template"></a>El ile bir Web şablonu oluşturmak için

1. Bir Web projesi oluşturun.

2. Projedeki dosyaları değiştirin veya silin ya da projeye yeni dosyalar ekleyin.

3. Bir XML dosyası oluşturun ve bunu, projenizle aynı dizinde bir *vstemplate* dosya adı uzantısıyla kaydedin. Visual Studio 'da projeye eklemeyin.

4. Proje şablonu meta verilerini sağlamak için *vstemplate* XML dosyasını düzenleyin. Daha fazla bilgi için [aşağıdaki örneğe](#example)bakın.

5. *Vstemplate* dosyasında `ProjectType` öğesini bulun ve metin değerini `Web` olarak ayarlayın.

6. @No__t_0 öğesini izleyerek bir `ProjectSubType` öğesi ekleyin ve metin değerini şablonun programlama diline ayarlayın. Programlama dili aşağıdaki değerlerden biri olabilir:

   - Step\chapter
   - VisualBasic

     Örneğin:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Şablonunuzda dosyaları seçin (Bu *vstemplate* dosyasını içerir), seçime sağ tıklayın ve  > **Sıkıştırılmış (daraltılmış) klasöre** **Gönder** ' i seçin. Dosyalar bir *. zip* dosyasında sıkıştırılır.

8. *. Zip* şablon dosyasını Visual Studio proje şablonu dizinine yerleştirin. Varsayılan olarak, bu dizin *%userprofile%\bir \> \ProjectTemplates \<Version*.

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
- [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
