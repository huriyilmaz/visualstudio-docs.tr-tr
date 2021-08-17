---
title: Birden çok proje şablonu oluşturma
description: Aynı anda birçok proje için kapsayıcı olarak Visual Studio birden çok proje şablonu oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: dbe68e27772df3a25cdef7c5bc62211b12f77a9c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048953"
---
# <a name="how-to-create-multi-project-templates"></a>Nasıl yapılanlar: Çok projeli şablonlar oluşturma

Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. Çoklu proje şablonunu temel alan bir proje oluşturursanız, şablonda yer alan her proje çözüme eklenir.

Çok projeli bir şablonda iki veya daha fazla proje şablonu ve ProjectGroup türünde bir kök **şablon vardır.**

Çok projeli şablonlar tek proje şablonlardan farklı davranır. Aşağıdaki benzersiz özelliklere sahiptir:

- Şablon yeni bir proje oluşturmak için kullanılırken, çoklu proje şablonunda tek tek projelere ad atanamaz. Bunun yerine, *vstemplate* **dosyasındaki ProjectTemplateLink** öğesinde **ProjectName** özniteliğini kullanarak her proje için bir ad belirtin.

- Çok projeli şablonlar farklı dillere yönelik projeler içerebilir, ancak şablonun tamamı yalnızca bir kategoriye yer kapsayabilirsiniz. *Vstemplate* dosyasının **ProjectType** öğesinde şablon kategorisini belirtin.

Çok projeli bir şablon, aşağıdaki öğeleri  bir.zipiçermeli:

- Çoklu proje şablonunun tamamı için bir kök *vstemplate* dosyası. Bu kök *vstemplate* dosyası, yeni bir proje oluşturmak için iletişim kutusunda görüntülenen meta verileri içerir. Ayrıca şablonda projeler için *vstemplate* dosyalarının nerede bulunacaklarını belirtir. Bu dosya, dosyanın kök *.zip.*

- Tam bir proje şablonu için gereken dosyaları içeren iki veya daha fazla klasör. Klasörler proje için tüm kod dosyalarını ve ayrıca proje için *bir vstemplate* dosyasını içerir.

Örneğin, iki projesi olan bir *.zip* projeli bir şablon aşağıdaki dosyalara ve dizinlere sahip olabilir:

- *MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Birden çok projeli bir şablon için kök *vstemplate* dosyası aşağıdaki yollarla tek projeli şablondan farklıdır:

- **VSTemplate öğesinin** **Type** özniteliği, öğesi yerine **ProjectGroup** **değerine Project.** Örnek:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- **TemplateContent** öğesi, dahil edilen projelerin *vstemplate* dosyalarının yollarını tanımlayan bir veya daha fazla **ProjectTemplateLink** öğesine sahip bir **ProjectCollection** öğesi içerir. Örnek:

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
> Çok projeli şablonun yalnızca yeni proje iletişim kutusunda görünmesini ve içerdiği projelerin görünmesini istemiyorsanız, iç şablonları gizli olarak [işaretleyin.](../extensibility/hidden-element-visual-studio-templates.md) Örnek:
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

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Mevcut bir çözümden çok projeli şablon oluşturma

1. Bir çözüm oluşturun ve iki veya daha fazla proje ekleyin.

2. Projeleri bir şablona dışarı aktarılana kadar özelleştirin.

   > [!TIP]
   > Şablon parametrelerini [kullanıyorsanız ve üst](template-parameters.md) şablondan değişkenlere başvurmak için parametrenin adına ön ek olarak `ext_` yazın. Örneğin, `$ext_safeprojectname$`. Ayrıca **ProjectTemplateLink** **öğesinin CopyParameters** özniteliğini true olarak **ayarlayın.**
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. Şablon **Project** Dışarı Aktar'ı **seçin.**

   Şablonu **Dışarı Aktarma Sihirbazı** açılır.

4. Şablon Türünü **Seçin sayfasında Şablon'Project** **seçin.** Bir şablona dışarı aktarmayı istediğiniz projelerden birini seçin ve ardından Sonraki'yi **seçin.** (Çözümde yer alan her proje için bu adımları yineleyebilirsiniz.)

5. Şablon Seçeneklerini **Seç sayfasında,** şablonunuz için bir ad ve isteğe bağlı bir açıklama, simge ve önizleme resmi girin. **Son**’u seçin.

   Proje bir.zip *dosyasına* aktarıldı ve belirtilen çıkış konuma yerleştirildi.

   > [!NOTE]
   > Her projenin bir şablona ayrı olarak dışarı aktarılması gerekir, bu nedenle çözümde her proje için önceki adımları tekrarlayın.

6. Şablonunuz için her proje için bir alt dizin ile bir dizin oluşturun.

7. Her projenin.zip *içeriğini* oluşturduğunuz ilgili alt dizine ayıklar.

8. Temel dizinde, *.vstemplate* dosya uzantısına sahip bir XML dosyası oluşturun. Bu dosya, çoklu proje şablonunun meta verilerini içerir. Dosyanın yapısı için aşağıdaki örneğine bakın. Her projenin *vstemplate* dosyasının göreli yolunu belirttiğinizden emin olun.

9. Temel dizindeki tüm dosyaları seçin ve sağ tıklama veya bağlam menüsünden Sıkıştırılmış (sıkıştırılmış) klasöre  >  **gönder'i seçin.**

   Dosyalar ve klasörler bir dosya .zipsıkıştırılır.

10. .zip *proje* şablonu dizinine kopyalayın. Varsayılan olarak, bu dizin *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates dizinidir.*

11. Bu Visual Studio Yeni **Dosya'Project**  >    >   seçin ve şablon görüntülendiğinden emin olun.

## <a name="two-project-example"></a>İki projeli örnek

Bu örnekte, temel bir çok projeli kök *vstemplate dosyası* gösterir. Bu örnekte, şablonun iki projesi vardır: **My Windows Application** ve Sınıf **Kitaplığım.** **ProjectTemplateLink öğesinde** **ProjectName** özniteliği, projeye verilen adı belirtir.

> [!TIP]
> **ProjectName özniteliği** belirtilmezse, proje adı olarak *vstemplate* dosyasının adı kullanılır.

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

## <a name="example-with-solution-folders"></a>Çözüm klasörlerini içeren örnek

Bu örnekte **SolutionFolder öğesi,** projeleri Matematik Sınıfları ve Grafik Sınıfları olarak **iki gruba** **bölmek için kullanılır.** Şablonun dört projesi vardır ve ikisi de her çözüm klasörüne yerleştirilir.

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
- [Nasıl: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Visual Studio şema başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
- [SolutionFolder öğesi (Visual Studio şablonları)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [ProjectTemplateLink öğesi (Visual Studio şablonları)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
