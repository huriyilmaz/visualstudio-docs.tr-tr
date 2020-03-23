---
title: Birden çok proje şablonu oluşturma
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6da7464f5e22e186edff7671744c2605bee3c9ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591092"
---
# <a name="how-to-create-multi-project-templates"></a>Nasıl yapılı: Çoklu proje şablonları oluşturma

Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. Çok proje şablonuna dayalı bir proje oluşturduğunuzda, şablondaki her proje çözüme eklenir.

Çoklu proje şablonunun iki veya daha fazla proje şablonu ve **ProjectGroup**türünden bir kök şablonu vardır.

Çoklu proje şablonları tek proje şablonlarından farklı şekilde davranmaktadır. Aşağıdaki benzersiz özelliklere sahiptirler:

- Şablon yeni bir proje oluşturmak için kullanıldığında, çoklu proje şablonundaki tek tek projelere ad atanamaz. Bunun yerine, her proje için bir ad belirtmek için *vstemplate* dosyasındaki **ProjectTemplateLink** öğesindeki **ProjectName** özniteliğini kullanın.

- Çoklu proje şablonları farklı diller için projeler içerebilir, ancak şablonun tamamı yalnızca bir kategoriye konulabilir. Vstemplate dosyasının **ProjectType** öğesinde şablon kategorisini *belirtin.*

Çoklu proje şablonu, *.zip* dosyasına sıkıştırılmış aşağıdaki öğeleri içermelidir:

- Tüm çoklu proje şablonu için kök *vstemplate* dosyası. Bu root *vstemplate* dosyası, yeni bir proje oluşturduğunuz iletişim kutusunda görüntülenen meta verileri içerir. Ayrıca şablondaki projeler için *vstemplate* dosyalarının nerede bulunacağını da belirtir. Bu dosya *.zip* dosyasının kökünde bulunmalıdır.

- Tam bir proje şablonu için gerekli olan dosyaları içeren iki veya daha fazla klasör. Klasörler, proje için tüm kod dosyalarını ve proje için bir *vstemplate* dosyasını içerir.

Örneğin, iki projesi olan bir çoklu proje şablonu *.zip* dosyası aşağıdaki dosyalara ve dizinlere sahip olabilir:

- *MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Proje1\Sınıf.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Proje2\Sınıf.vb*

Çok projeli şablonun root *vstemplate* dosyası aşağıdaki yollarla tek proje şablonundan farklıdır:

- **VSTemplate** öğesinin **Tür** özniteliği, **Project**yerine **ProjectGroup** değerine sahiptir. Örnek:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- **TemplateContent** öğesi, dahil edilen projelerin *vstemplate* dosyalarına giden yolları tanımlayan bir veya daha fazla **ProjectTemplateLink** öğesine sahip bir **ProjectCollection** öğesi içerir. Örnek:

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
> Çoklu proje şablonunun içerdiği tek tek projeler değil, yalnızca yeni proje iletişim kutusunda görünmesini istiyorsanız, iç şablonları [gizli](../extensibility/hidden-element-visual-studio-templates.md)olarak işaretleyin. Örnek:
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

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Varolan bir çözümden çoklu proje şablonu oluşturma

1. Bir çözüm oluşturun ve iki veya daha fazla proje ekleyin.

2. Bir şablona dışa aktarılacak hazır olana kadar projeleri özelleştirin.

   > [!TIP]
   > [Şablon parametrelerini](template-parameters.md) kullanıyorsanız ve üst şablondaki değişkenlere başvurmak istiyorsanız, parametrenin adını `ext_`. Örneğin, `$ext_safeprojectname$`. Ayrıca, **ProjectTemplateLink** öğesinin **CopyParameters** özniteliğini **doğru**olarak ayarlayın.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. **Proje** menüsünde **Dışa Aktarma Şablonu'nu**seçin.

   **Dışa Aktarma Şablonu Sihirbazı** açılır.

4. Şablon **Türü Seç** sayfasında **Proje Şablonu'nu**seçin. Şablona aktarmak istediğiniz projelerden birini seçin ve sonra **İleri'yi**seçin. (Çözümdeki her proje için bu adımları yinelersiniz.)

5. Şablon **Seçeneklerini Seç** sayfasında şablonunuz için bir ad ve isteğe bağlı açıklama, simge ve önizleme resmi girin. **Son**’u seçin.

   Proje bir *.zip* dosyasına dışa aktarılır ve belirtilen çıktı konumuna yerleştirilir.

   > [!NOTE]
   > Her proje ayrı ayrı bir şablona dışa aktarılmalıdır, bu nedenle çözümdeki her proje için önceki adımları yineleyin.

6. Şablonunuzun her proje için bir alt dizin içeren bir dizin oluşturun.

7. Her projenin *.zip* dosyasının içeriğini oluşturduğunuz ilgili alt dizine ayıklayın.

8. Temel dizinde *,.vstemplate* dosya uzantısı içeren bir XML dosyası oluşturun. Bu dosya, çoklu proje şablonu için meta verileri içerir. Dosyanın yapısı için aşağıdaki örneğe bakın. Her projenin *vstemplate* dosyasına göreli yolu belirttiğinden emin olun.

9. Temel dizindeki tüm dosyaları seçin ve sağ tıklatma veya bağlam menüsünden > **Sıkıştırılmış (sıkıştırılmış) klasörüne** **gönder'i**seçin.

   Dosya ve klasörler *bir .zip* dosyasına sıkıştırılır.

10. *.zip* dosyasını kullanıcı projesi şablon dizini içine kopyalayın. Varsayılan olarak, bu dizin *%USERPROFILE%\Documents\Visual Studio \<sürümü\>\Templates\ProjectTemplates'* tir.

11. Visual Studio'da > **Yeni** >  **Dosya****Dosyası'nı** seçin ve şablonunuzun göründüğünden doğrulayın.

## <a name="two-project-example"></a>İki proje örneği

Bu örnek, temel bir çok proje kök *vstemplate* dosyagösterir. Bu örnekte, şablonun windows **uygulamam** ve Sınıf **Kitaplığım**olmak üzere iki projesi vardır. **ProjectTemplateLink** öğesindeki **ProjectName** özniteliği projeye verilen adı belirtir.

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

## <a name="example-with-solution-folders"></a>Çözüm klasörleri ile örnek

Bu örnek, projeleri **Matematik Sınıfları** ve Grafik **Sınıfları**olmak üzere iki gruba bölmek için **SolutionFolder** öğesini kullanır. Şablon, ikisi her çözüm klasörüne yerleştirilen dört projeye sahiptir.

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

- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılı: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Visual Studio şablon şeması başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
- [SolutionFolder öğesi (Visual Studio şablonları)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [ProjectTemplateLink öğesi (Visual Studio şablonları)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
