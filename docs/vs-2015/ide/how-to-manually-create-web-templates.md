---
title: 'Nasıl yapılır: Web şablonlarını elle oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4bf604e747158c651f284c6463c2c2f65ae3c47a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651810"
---
# <a name="how-to-manually-create-web-templates"></a>Nasıl Yapılır: Web Şablonlarını Elle Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web şablonu oluşturmak diğer şablon türlerini oluşturmaktan farklıdır. Web projesi şablonları **Yeni Web sitesi Ekle** iletişim kutusunda göründüğünden ve Web projesi öğeleri programlama diline göre sınıflandırıldığından,. vstemplate dosyasının şablonu bir Web şablonu olarak belirtmesi ve programlama dilini tanımlaması gerekir.

> [!NOTE]
> Web şablonları, öğesinin özniteliği kullanılarak belirtilen boş bir. webproj dosyası içermelidir `File` `Project` . Web projeleri proje dosyaları gerektirmese de, bir Web şablonunun doğru çalışması için bu dosya gereklidir.

### <a name="to-manually-create-a-web-template"></a>El ile bir Web şablonu oluşturmak için

1. Bir Web projesi oluşturun.

2. Projedeki dosyaları değiştirin veya silin ya da projeye yeni dosyalar ekleyin.

3. Bir XML dosyası oluşturun ve bunu, projenizle aynı dizinde. vstemplate dosya adı uzantısını kullanarak kaydedin. İçindeki projeye eklemeyin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

4. Proje şablonu meta verilerini sağlamak için. vstemplate XML dosyasını yazın. Daha fazla bilgi için aşağıdaki bölümdeki örneğe bakın.

5. `ProjectType`. Vstemplate dosyasındaki öğesini bulun ve metin değerini olarak ayarlayın `Web` .

6. Öğesini izleyerek `ProjectType` bir `ProjectSubType` öğesi ekleyin ve metin değerini şablonun programlama diline ayarlayın. Programlama dili aşağıdaki değerlerden biri olabilir:

   - Step\chapter

   - VisualBasic

     Örneğin:

   ```
   <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
   </TemplateData>
   ```

7. Şablonunuzda dosyaları seçin (. vstemplate dosyasını içerir), seçime sağ tıklayın, **Gönder ' e**tıklayın ve ardından **Sıkıştırılmış (daraltılmış) klasör**' e tıklayın. Dosyalar bir. zip dosyasında sıkıştırılır.

8. . Zip şablon dosyasını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje şablonu dizinine yerleştirin. Bu dizin, varsayılan olarak, \Bir Studio *sürümü*\Ihraç şablonlar dizinidir \\ .

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir Web projesi şablonu için temel bir. vstemplate dosyasını gösterir.

```
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
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

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md) [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
