---
title: Birden çok proje şablonu oluşturma
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b71af98c7d72e0b3a510f3968f3d0770cd5401df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284418"
---
# <a name="how-to-create-multi-project-templates"></a>Nasıl yapılır: birden çok proje şablonu oluşturma

Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. Çoklu proje şablonuna dayalı bir proje oluşturduğunuzda, şablondaki her proje çözüme eklenir.

Çoklu proje şablonunda iki veya daha fazla proje şablonu ve **ProjectGroup**türünde bir kök şablon vardır.

Çoklu proje şablonları, tek proje şablonlarından farklı davranır. Aşağıdaki benzersiz özelliklere sahiptir:

- Yeni bir proje oluşturmak için şablon kullanıldığında, çok projeli bir şablonda bireysel projelere ad atanamaz. Bunun yerine, her proje için bir ad belirtmek üzere *vstemplate* dosyasındaki **ProjectTemplateLink** öğesinde **ProjectName** özniteliğini kullanın.

- Çoklu proje şablonları farklı diller için projeler içerebilir, ancak tüm şablon yalnızca bir kategoriye yerleştirilebilir. *Vstemplate* dosyasının **ProjectType** öğesinde şablon kategorisini belirtin.

Birden çok projeli bir şablon, bir *. zip* dosyasına sıkıştırılan aşağıdaki öğeleri içermelidir:

- Tüm çoklu proje şablonu için bir kök *vstemplate* dosyası. Bu kök *vstemplate* dosyası, yeni bir proje oluşturduğunuz iletişim kutusunda görüntülenen meta verileri içerir. Ayrıca, şablondaki projeler için *vstemplate* dosyalarının nerede bulunacağını belirtir. Bu dosya, *. zip* dosyasının kökünde bulunmalıdır.

- Tamamlanmış bir proje şablonu için gereken dosyaları içeren iki veya daha fazla klasör. Klasörler, proje için tüm kod dosyalarını ve ayrıca proje için bir *vstemplate* dosyasını içerir.

Örneğin, iki projeli bir çoklu proje şablonu *. zip* dosyası aşağıdaki dosya ve dizinlere sahip olabilir:

- *MultiProjectTemplate. vstemplate*
- *\Project1\mytemplate5vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\class.exe*
- *\Project2\mytemplate5vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\class.exe*

Çoklu proje şablonu için kök *vstemplate* dosyası, tek projeli bir şablondan aşağıdaki yollarla farklılık gösterir:

- **Vstemplate** öğesinin **Type** özniteliği **Project**yerine **ProjectGroup** değerine sahiptir. Örneğin:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- **TemplateContent** öğesi, dahil edilen projelerin *vstemplate* dosyalarının yollarını tanımlayan bir veya daha fazla **ProjectTemplateLink** öğesine sahip bir **ProjectCollection** öğesi içeriyor. Örneğin:

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

> [!TIP]
> Yalnızca çoklu proje şablonunun yeni proje iletişim kutusunda görünmesini istiyorsanız, içerdiği ayrı projeler değil, iç şablonları [gizli](../extensibility/hidden-element-visual-studio-templates.md)olarak işaretleyin. Örneğin:
>
> ```xml
> <VSTemplate Type="Project" ... >
>     <TemplateData>
>         ...
>         <Hidden>true</Hidden>
>     </TemplateData>
>     ...
> </VSTemplate>
> ```

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Mevcut bir çözümden çok projeli bir şablon oluşturma

1. Bir çözüm oluşturun ve iki veya daha fazla proje ekleyin.

2. Projeleri bir şablona aktarılmaya hazırlanana kadar özelleştirin.

   > [!TIP]
   > [Şablon parametreleri](template-parameters.md) kullanıyorsanız ve üst şablondaki değişkenlere başvurmak istiyorsanız, parametresinin adını ile önek yapın `ext_` . Örneğin, `$ext_safeprojectname$`. Ayrıca, **ProjectTemplateLink** öğesinin **CopyParameters** özniteliğini **true**olarak ayarlayın.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. **Proje** menüsünde, **şablonu dışarı aktar**' ı seçin.

   **Şablonu dışarı aktarma Sihirbazı** açılır.

4. **Şablon türü seç** sayfasında, **proje şablonu**' nu seçin. Bir şablona dışarı aktarmak istediğiniz projelerden birini seçin ve ardından **İleri**' yi seçin. (Çözümdeki her proje için bu adımları tekrarlayabilirsiniz.)

5. **Şablon seçeneklerini seçin** sayfasında, şablonunuz için bir ad ve isteğe bağlı olarak bir açıklama, simge ve önizleme resmi girin. **Son**’u seçin.

   Proje bir *. zip* dosyasına aktarılmışsa ve belirtilen çıkış konumuna yerleştirilir.

   > [!NOTE]
   > Her proje ayrı ayrı aktarılmalıdır, bu nedenle çözümdeki her proje için önceki adımları tekrarlayın.

6. Şablonunuz için her proje için bir alt dizinle bir dizin oluşturun.

7. Her projenin *. zip* dosyasının içeriğini, oluşturduğunuz karşılık gelen alt dizine ayıklayın.

8. Taban dizininde *. vstemplate* dosya uzantısına sahıp bir XML dosyası oluşturun. Bu dosya, çoklu proje şablonu için meta verileri içerir. Dosyanın yapısı için aşağıdaki örneğe bakın. Her projenin *vstemplate* dosyasının göreli yolunu belirttiğinizden emin olun.

9. Temel dizindeki tüm dosyaları seçin ve sağ tıklama ya da bağlam menüsünden **Send to**  >  **Sıkıştırılmış (daraltılmış) klasöre**Gönder ' i seçin.

   Dosyalar ve klasörler bir *. zip* dosyasında sıkıştırılır.

10. *. Zip* dosyasını Kullanıcı projesi şablon dizinine kopyalayın. Varsayılan olarak, bu dizin *%userprofile%\, Studio \<version\> \Templates\projecttemplates*şeklindedir.

11. Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje** ' yi seçin ve şablonunuzun göründüğünü doğrulayın.

## <a name="two-project-example"></a>İki projem örneği

Bu örnek, temel bir çoklu proje kök *vstemplate* dosyasını gösterir. Bu örnekte, şablonda iki proje, **Windows Uygulamam** ve **My Class Library**vardır. **ProjectTemplateLink** öğesindeki **ProjectName** özniteliği, projeye verilen adı belirtir.

> [!TIP]
> **ProjectName** özniteliği belirtilmemişse, *vstemplate* dosyasının adı proje adı olarak kullanılır.

```xml
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

## <a name="example-with-solution-folders"></a>Çözüm klasörleriyle örnek

Bu örnek, projeleri iki gruba, **matematik sınıflarına** ve **grafik sınıflarına**bölmek için **SolutionFolder** öğesini kullanır. Şablonda her bir çözüm klasörüne yerleştirilmiş dört proje vardır.

```xml
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

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
- [SolutionFolder öğesi (Visual Studio şablonları)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [ProjectTemplateLink öğesi (Visual Studio şablonları)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
