---
title: 'Nasıl yapılır: birden çok proje şablonu oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1de155b71e82bb7561030cae2e1d0d4d777c9586
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668069"
---
# <a name="how-to-create-multi-project-templates"></a>Nasıl Yapılır: Birden Çok Proje Şablonu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. **Yeni proje** iletişim kutusundan çok projeli bir şablonu temel alan bir proje oluşturulduğunda, şablondaki her proje çözüme eklenir.

 Birden çok projeli bir şablon, bir. zip dosyasına sıkıştırılan aşağıdaki öğeleri içermelidir:

- Tüm çoklu proje şablonu için bir root. vstemplate dosyası. Bu root. vstemplate dosyası, **Yeni proje** iletişim kutusunun görüntülediği meta verileri içerir ve bu şablondaki projeler için. vstemplate dosyalarının nerede bulunacağını belirtir. Bu dosya,. zip dosyasının kökünde bulunmalıdır.

- Tamamlanmış bir proje şablonu için gereken dosyaları içeren bir veya daha fazla klasör. Bu, proje için tüm kod dosyalarını ve ayrıca proje için bir. vstemplate dosyasını içerir.

  Örneğin, iki projeli bir çoklu proje şablonu. zip dosyası aşağıdaki dosya ve dizinlere sahip olabilir:

  MultiProjectTemplate. vstemplate

  \Project1\Project1.vstemplate

  \Project1\Project1.vbproj

  \Project1\class.exe

  \Project2\Project2.vstemplate

  \Project2\Project2.vbproj

  \Project2\class.exe

  Çoklu proje şablonu için kök. vstemplate dosyası, tek projeli bir şablondan aşağıdaki yollarla farklılık gösterir:

- @No__t_1 öğesinin `Type` özniteliği `ProjectGroup` değerini içerir. Örneğin:

  ```
  <VSTemplate Version="2.0.0" Type="ProjectGroup"
      xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
  ```

- @No__t_0 öğesi, dahil edilen projelerin. vstemplate dosyalarının yollarını tanımlayan bir veya daha fazla `ProjectTemplateLink` öğesi olan bir `ProjectCollection` öğesi içeriyor. Örneğin:

  ```
  <TemplateContent>
      <ProjectCollection>
          <ProjectTemplateLink>
              Project1\Project1.vstemplate
          </ProjectTemplateLink>
          <ProjectTemplateLink>
              Project2\Project2.vstemplate
          </ProjectTemplateLink>
      </ProjectCollection>
  </TemplateContent>
  ```

  Çoklu proje şablonları da normal şablonlardan farklı şekilde davranır. Çoklu proje şablonları aşağıdaki benzersiz özelliklere sahiptir:

- Çoklu Proje şablonundaki ayrı projelere **Yeni proje** iletişim kutusu tarafından adlar atanamaz. Bunun yerine, her projenin adını belirtmek için `ProjectTemplateLink` öğesindeki `ProjectName` özniteliğini kullanın. Daha fazla bilgi için aşağıdaki bölümdeki ilk örneğe bakın.

- Çoklu proje şablonları farklı dillerde yazılmış projeleri içerebilir, ancak tüm şablon yalnızca bir kategoriye `ProjectType` öğesi kullanılarak yerleştirilebilir.

### <a name="to-create-a-multi-project-template"></a>Çoklu proje şablonu oluşturmak için

1. Çoklu proje şablonuna dahil edilecek projeleri oluşturun.

2. Her proje için. vstemplate dosyaları oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: proje şablonları oluşturma](../ide/how-to-create-project-templates.md).

3. Çoklu proje şablonu için meta verileri içeren bir root. vstemplate dosyası oluşturun. Daha fazla bilgi için aşağıdaki bölümdeki ilk örneğe bakın.

4. Şablonunuza dahil edilecek dosya ve klasörleri seçin, seçime sağ tıklayın, **Gönder ' e**tıklayın ve ardından **Sıkıştırılmış (daraltılmış) klasör**' e tıklayın. Dosyalar ve klasörler bir. zip dosyasında sıkıştırılır.

5. . Zip şablonu dosyasını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje şablonu dizinine koyun. Bu dizin, varsayılan olarak, \Bstudio *sürümü*\ Templates\projecttemplates \\.

## <a name="example"></a>Örnek
 Bu örnek, temel bir çoklu proje kök. vstemplate dosyasını gösterir. Bu örnekte, şablon iki proje içerir, `My Windows Application` ve `My Class Library`. @No__t_1 öğesindeki `ProjectName` özniteliği, bu projeyi atamak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adını ayarlar. @No__t_0 özniteliği yoksa,. vstemplate dosyasının adı proje adı olarak kullanılır.

```
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="example"></a>Örnek
 Bu örnek, projeleri iki gruba bölmek için `SolutionFolder` öğesini kullanır, `Math Classes` ve `Graphics Classes`. Şablon, her bir çözüm klasörüne yerleştirilmiş dört proje içerir.

```
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md) [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md) [nasıl yapılır: proje şablonları oluşturma](../ide/how-to-create-project-templates.md) [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md) [SolutionFolder öğesi (Visual Studio şablonları)](../extensibility/solutionfolder-element-visual-studio-templates.md) [ ProjectTemplateLink öğesi (Visual Studio şablonları)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
