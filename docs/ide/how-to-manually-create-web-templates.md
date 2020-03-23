---
title: Web şablonları oluşturma
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 245b20dd9cad465129d6c79c38e53b6379c2c09c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591014"
---
# <a name="how-to-manually-create-web-templates"></a>Nasıl yapılır: Web şablonlarını el ile oluşturma

Web şablonu oluşturmak, diğer şablon türlerini oluşturmaktan farklıdır. Web projesi şablonları **Yeni Web Sitesi Ekle** iletişim kutusunda göründüğünden ve web proje öğeleri programlama diline göre kategorilere ayırıldığı için, *vstemplate* dosyasının şablonu bir web şablonu olarak belirtmesi ve programlama dilini tanımlaması gerekir.

> [!NOTE]
> Web şablonları boş bir *.webproj* dosyası içermelidir ve `Project` öğenin özniteliği `File` içinde *vstemplate* dosyasında başvurulmalıdır. Web projeleri *bir .proj* proje dosyası gerektirmese de, web şablonu için bu saplama dosyasını oluşturmak gerekir.

## <a name="to-manually-create-a-web-template"></a>El ile web şablonu oluşturmak için

1. Bir web projesi oluşturun.

2. Projedeki dosyaları değiştirin veya silin veya projeye yeni dosyalar ekleyin.

3. Bir XML dosyası oluşturun ve projenizle aynı dizinde *bir vstemplate* dosya adı uzantısı ile kaydedin. Visual Studio'daki projeye eklemeyin.

4. Proje şablonu meta verilerini sağlamak için *vstemplate* XML dosyasını edin. Daha fazla bilgi için [aşağıdaki örneğe](#example)bakın.

5. *Vstemplate* dosyasındaki öğeyi `Web` `ProjectType` bulun ve metin değerini .

6. Öğeyi `ProjectType` takiben, `ProjectSubType` bir öğe ekleyin ve şablonun programlama diline metin değerini ayarlayın. Programlama dili aşağıdaki değerlerden biri olabilir:

   - Csharp
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

7. Şablonunuzdaki dosyaları seçin (bu *vstemplate* dosyasını içerir), seçimi sağ tıklatın ve > **Sıkıştırılmış (sıkıştırılmış) klasörüne** **gönder'i**seçin. Dosyalar *bir .zip* dosyasına sıkıştırılır.

8. *.zip* şablonu dosyasını Visual Studio proje şablon dizini'ne koyun. Varsayılan olarak, bu dizin *%USERPROFILE%\Documents\Visual Studio \<Version\>\ProjectTemplates'tir.*

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir web projesi şablonu için temel bir *vstemplate* dosyası gösterilmektedir:

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
