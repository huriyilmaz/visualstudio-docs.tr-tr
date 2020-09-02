---
title: 'Nasıl yapılır: proje ve öğe şablonlarını bulma ve düzenleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5f55de910eb77ec7ccbd205b78d5c95039e6b39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651867"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Nasıl Yapılır: Proje ve Öğe Şablonlarını Bulma ve Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablon dosyaları, şablonların **Yeni proje** ve **Yeni öğe Ekle** Iletişim kutularında görünmesi için Visual Studio 'nun tanıdığı bir konuma yerleştirilmelidir. Alt kategorilerin de Kullanıcı arabiriminde görünmesi için şablonlar için özel alt kategoriler oluşturabilirsiniz.

## <a name="locating-templates"></a>Şablonları bulma
 Varsayılan olarak, Visual Studio proje ve öğe şablonları için iki konumu arar. Bu konumlarda. vstemplate dosyası içeren sıkıştırılmış bir dosya varsa, **Yeni proje** veya **Yeni öğe Ekle** iletişim kutularında bir şablon görüntülenir.

### <a name="installed-templates"></a>Yüklü şablonlar
 Varsayılan olarak, ürünle birlikte yüklenen şablonlar şu konumda bulunur:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates \\ *dil* \\ *yerel ayarı*\

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates \\ *dil* \\ *yerel \\ ayarı*

  Örneğin, aşağıdaki dizin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] İngilizce için proje şablonlarını içerir:

  C: \\ *VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="custom-templates"></a>Özel şablonlar
 Varsayılan olarak, özel şablonlar içinde bulunur:

- \Bir Studio *sürümü*\ Templates\projecttemplates \\ *dili*\

- _Bir Studio *sürümü*\ Templates\ıtemtemplates \\ *dili*\

  Örneğin, aşağıdaki dizin özel [!INCLUDE[csprcs](../includes/csprcs-md.md)] Proje şablonları içerir:

  C:\Documents and Settings \ kullanýcýadý \\<Visual Studio Version \> \Templates\projecttemplates\visual C# \

  Özel şablonlar, yerelleştirilmiş şablonlar için bir alt dizin içermez. Özel şablonlar için varsayılan dizini, **Environment\projeleri ve çözümleri**altında **Seçenekler** iletişim kutusunda değiştirebilirsiniz.

## <a name="organizing-templates"></a>Şablonları düzenleme
 **Yeni proje** ve **Yeni öğe Ekle** iletişim kutularında bulunan kategoriler, yüklü ve özel şablon konumlarında var olan dizin yapılarını yansıtır. Bu dizin yapılarını, şablonlarınızı sizin için anlamlı bir şekilde düzenlemek için değiştirebilirsiniz.

> [!NOTE]
> Programlama dili düzeyinde yeni bir kategori oluşturamazsınız. Yeni kategoriler yalnızca her bir dil içinde oluşturulabilir.

 Belirli bir dile ait yüklenen ve özel şablonların dizin yapıları aynı yapıya sahip değilse (yani, diğeri altında olmayan bir klasör altında dizinler vardır) **Yeni proje** iletişim kutusunda görünen kategori kümesi, tüm kategorilerin birleşmesi olacaktır.

### <a name="organizing-installed-templates"></a>Yüklü şablonları düzenleme
 Programlama dili klasöründe alt dizinler oluşturarak, yüklü şablonları düzenleyebilirsiniz. Bu alt dizinler **Yeni projede** görüntülenir ve **Yeni öğe** iletişim kutularında her bir dilde sanal klasör olarak görünür.

##### <a name="to-create-new-installed-project-template-categories"></a>Yeni yüklenen proje şablonu kategorileri oluşturmak için

1. Yüklü şablon dizininin dil klasöründe bir klasör oluşturun. Örneğin, proje şablonları için bir Office kategorisi oluşturmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aşağıdaki dizini oluşturun:

    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\

2. Bu kategorinin tüm şablonlarını yeni klasöre yerleştirin.

3. Tüm örneklerini kapatın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

4. **Başlat** menüsünde, **Çalıştır**' a tıklayın, **cmd**yazın ve **Tamam**' a tıklayın.

5. Komut isteminde devenv.exe içeren dizini bulun ve **devenv/ınstallvstempsyonlar**yazın.

6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] öğesini çalıştırın.

7. **Dosya** menüsünde **Yeni** ve **Proje**’ye sırasıyla tıklayın.

8. Office kategorisinin **Yeni proje** iletişim kutusunda, altındaki **Proje türleri** bölmesinde göründüğünü doğrulayın [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

   Ayrıca, proje öğesi şablonlarının bir alt kümesini özel bir klasöre gruplayabilirsiniz.

##### <a name="to-create-new-installed-item-template-categories"></a>Yeni yüklenen öğe şablonu kategorileri oluşturmak için

1. Yüklü şablon dizininin dil klasöründe bir klasör oluşturun. Örneğin, öğe şablonları için bir Web kategorisi oluşturmak için [!INCLUDE[csprcs](../includes/csprcs-md.md)] aşağıdaki dizini oluşturun:

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\

2. Bu kategorinin tüm şablonlarını yeni klasöre yerleştirin.

3. Tüm örneklerini kapatın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

4. **Başlat** menüsünde, **Çalıştır**' a tıklayın, **cmd**yazın ve **Tamam**' a tıklayın.

5. Komut isteminde, devenv.exe içeren dizini bulun ve **devenv/setup**yazın.

6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] öğesini çalıştırın.

7. Proje oluşturun veya var olan bir projeyi açın.

8. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

9. Web kategorisinin, **Proje türleri** bölmesinde **Yeni öğe Ekle** iletişim kutusunda göründüğünü doğrulayın.

### <a name="organizing-custom-templates"></a>Özel şablonları düzenleme
 Özel şablon konumunda yeni klasörler eklenerek, özel şablonlar kendi kategorilerine düzenlenebilir. **Yeni proje** iletişim kutusu, şablon kategorileriniz üzerinde yaptığınız tüm değişiklikleri yansıtır.

##### <a name="to-create-new-custom-project-template-categories"></a>Yeni özel proje şablonu kategorileri oluşturmak için

1. Özel proje şablonu dizinindeki dil klasöründe bir klasör oluşturun. Örneğin, şablonlar için HelloWorld kategorisi oluşturmak için [!INCLUDE[csprcs](../includes/csprcs-md.md)] aşağıdaki dizini oluşturursunuz:

    \Documents \\<Visual Studio sürümü \> \ Templates\projecttemplates\csharp\helloworld\

2. Bu kategorinin tüm şablonlarını yeni klasöre yerleştirin.

3. **Dosya** menüsünde **Yeni** ve **Proje**’ye sırasıyla tıklayın.

4. Merhaba kategorisinin **Yeni proje** iletişim kutusunda, altındaki **Proje türleri** bölmesinde göründüğünü doğrulayın [!INCLUDE[csprcs](../includes/csprcs-md.md)] .

   Özel öğe şablonlarının bir alt kümesini özel bir klasöre de gruplandırabilirsiniz.

##### <a name="to-create-new-custom-item-template-categories"></a>Yeni özel öğe şablonu kategorileri oluşturmak için

1. Özel öğe şablonu dizinindeki dil klasöründe bir klasör oluşturun. Örneğin, şablonlar için HelloWorld kategorisi oluşturmak için [!INCLUDE[csprcs](../includes/csprcs-md.md)] aşağıdaki dizini oluşturun:

     \Documents \\<Visual Studio sürümü \> \ Templates\ıtemtemplates\csharp\helloworld\

2. Bu kategorinin tüm şablonlarını yeni klasöre yerleştirin.

3. Proje oluşturun veya var olan bir projeyi açın.

4. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

5. **Proje türleri** bölmesinde **Yeni öğe Ekle** iletişim kutusunda HelloWorld kategorisinin göründüğünü doğrulayın.

### <a name="displaying-templates-in-parent-categories"></a>Şablonları üst kategorilerde görüntüleme
 Alt kategorilerindeki şablonları, `NumberOfParentCategoriesToRollUp` . vstemplate dosyasındaki öğesini kullanarak üst kategorilerinde görüntülenmek üzere etkinleştirebilirsiniz. Bu adımlar hem proje şablonları hem de öğe şablonları için aynıdır.

##### <a name="to-display-templates-in-parent-categories"></a>Şablonları üst kategorilerde görüntüleme

1. Şablonu içeren. zip dosyasını bulun.

2. . Zip dosyasını ayıklayın.

3. İçindeki. vstemplate dosyasını açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

4. `TemplateData`Öğesinde, bir `NumberOfParentCategoriesToRollUp` öğesi ekleyin. Örneğin, aşağıdaki kod, şablonu üst kategoride görünür hale getirir, ancak daha fazlasını yapmaz.

    ```
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

5. . Vstemplate dosyasını kaydedin ve kapatın.

6. Şablonunuzda dosyaları seçin, seçime sağ tıklayın, **Gönder ' e**tıklayın ve ardından **Sıkıştırılmış (daraltılmış) klasör**' e tıklayın. Dosyalar bir. zip dosyasında sıkıştırılır.

7. Ayıklanan şablon dosyalarını ve eski şablon. zip dosyasını silin.

8. Yeni. zip dosyasını silinen. zip dosyasına sahip olan dizine yerleştirin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md) [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md) [NumberOfParentCategoriesToRollUp (Visual Studio şablonları)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) [nasıl yapılır: proje şablonları oluşturma](../ide/how-to-create-project-templates.md) [nasıl yapılır: öğe şablonları](../ide/how-to-create-item-templates.md) oluşturma
