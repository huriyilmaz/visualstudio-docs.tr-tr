---
title: 'Nasıl yapılır: öğe şablonları oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9edc79002a4a2d7c2fe135d7eb4669f5f010599
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668072"
---
# <a name="how-to-create-item-templates"></a>Nasıl Yapılır: Öğe Şablonları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konunun [ilk yordamındaki](#to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box) adımlarda, **şablonu dışarı aktarma** Sihirbazı 'nı kullanarak bir öğe şablonu oluşturma işlemi gösterilir. Şablonunuz birden çok dosyadan oluşu, bkz. [nasıl yapılır: birden çok dosya öğesi şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md).

 Sihirbaz, temel şablonu oluşturmanız için çok sayıda iş yapar, ancak çoğu durumda, şablonu verdikten sonra. vstemplate dosyasını el ile değiştirmeniz gerekir. Örneğin, bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama projesi için öğenin **Yeni öğe Ekle** iletişim kutusunda görünmesini istiyorsanız birkaç ek adım gerçekleştirmeniz gerekir. Bu konudaki [ikinci yordam](#to-enable-the-item-template-to-be-used-in-a-store-project) , bu görevi gerçekleştirmenize yardımcı olur.

 Bazı durumlarda, sıfırdan elle el ile bir öğe şablonu oluşturmanız gerekebilir. [Üçüncü yordamda](#to-enable-templates-for-specific-project-sub-types) bunun nasıl yapılacağı gösterilmektedir.

 . Vstemplate dosyasında kullanılabilecek öğeler hakkında bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md) .

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Yeni öğe Ekle iletişim kutusuna özel bir proje öğesi şablonu eklemek için

1. @No__t_0 bir proje oluşturun veya açın.

2. Projeye bir öğe ekleyin ve isterseniz dosyayı değiştirin.

3. Kod dosyasını parametre değiştirmenin nerede olması gerektiğini belirtecek şekilde değiştirin. Daha fazla bilgi için bkz. [nasıl yapılır: şablonda parametreleri değiştirme](../ide/how-to-substitute-parameters-in-a-template.md).

4. **Dosya** menüsünde, **şablonu dışarı aktar**' a tıklayın.

5. **Öğe şablonu**' na tıklayın, öğeyi içeren projeyi seçin ve **İleri**' ye tıklayın.

6. Şablon oluşturmak istediğiniz öğeyi seçin ve **İleri**' ye tıklayın.

7. Şablona dahil edilecek derleme başvurularını seçin ve **İleri**' ye tıklayın.

8. Simge dosya adı, önizleme resmi, şablon adı ve şablon açıklaması yazın ve **son**' a tıklayın.

     Şablon dosyaları bir. zip dosyasına eklenir ve iletişim kutusunda belirttiğiniz herhangi bir dizini kopyalamıştır. Varsayılan konum **... \Users \\ < Kullanıcı adı \> \K\studio \<Version >**

    > [!WARNING]
    > Visual Studio 'nun önceki sürümlerinde varsayılan konum **... \Users \\ < Kullanıcı adı \> \K\studio \<Version > \Templates\ıtemtemplates**.

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Bir mağaza projesinde kullanılacak öğe şablonunu etkinleştirmek için

1. Bir öğe şablonunu dışarı aktarmak için yukarıdaki yordamdaki adımları izleyin.

2. . Vstemplate dosyasını. zip dosyasından ' a kopyalanmış olan. zip dosyasından ayıklayın. \Users \\*UserName*\Sk\studio *Version*\Templates\ıtemtemplates \ (veya **My My Templates**) klasöründedir.

3. Visual Studio 'da. vstemplate dosyasını açın.

4. Windows 8.1 bir mağaza C# projesi için. vstemplate dosyasında, açma ve kapatma `<TemplateData>` etiketi: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` IÇINDE aşağıdaki XML 'i ekleyin.

    Windows 8.1 C++ bir mağaza projesi `WinRT-Native-6.3` değerini kullanır. Windows 10 ve diğer proje türleri için bkz. [TemplateGroupID öğesi (Visual Studio şablonları)](../extensibility/templategroupid-element-visual-studio-templates.md).

    Aşağıdaki örnek, bir. vstemplate dosyasının, XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` satırı eklendikten sonra tüm içeriğini gösterir. Bu örnek C# projelere özeldir. Diğer dili ve proje türlerini belirtmek için \<ProjectType > ve [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> öğelerini \< değiştirebilirsiniz.

   ```xml
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
     <TemplateData>
       <DefaultName>MyItemStoreTemplate.xaml</DefaultName>
       <Name>MyItemStoreTemplate</Name>
       <Description>This is an example itemtemplate</Description>
       <ProjectType>CSharp</ProjectType>
       <SortOrder>10</SortOrder>
       <Icon>__TemplateIcon.ico</Icon>
       <TemplateGroupID>WinRT-Managed</TemplateGroupID>
     </TemplateData>
     <TemplateContent>
       <References />
       <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>
       <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>
     </TemplateContent>
   </VSTemplate>
   ```

    Diğer olası TemplateGroupID değerleri için bkz. [TemplateGroupID öğesi (Visual Studio şablonları)](../extensibility/templategroupid-element-visual-studio-templates.md)). Tüm. vstemplate başvurusu için bkz. [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)

5. Visual Studio 'da. vstemplate dosyasını kaydedin ve kapatın.

6. . Vstemplate dosyasını kopyalayıp içinde bulunan. zip dosyasına geri yapıştırın. \Users \\*UserName*\K\studio *Version*\Templates\ıtemtemplates \ Folder.

    **Dosya Kopyala** iletişim kutusu görüntülenirse, **Kopyala ve Değiştir** seçeneğini belirleyin.

   Artık, **Yeni öğe Ekle** iletişim kutusunu kullanarak bu şablona dayalı bir öğeyi bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projesine ekleyebilirsiniz.

   Parametre adları hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

### <a name="to-enable-templates-for-specific-project-sub-types"></a>Belirli proje alt türleri için şablonları etkinleştirmek üzere

1. Geliştirme ortamı, belirli projeler için öğe Ekle iletişim kutusundan proje öğelerini kullanılabilir hale getirmenizi sağlar. Özel öğeleri Windows, Web, Office veya veritabanı projeleri için kullanılabilir hale getirmek için bu yordamı kullanın.

    Öğe şablonu için. vstemplate dosyasında ProjectType öğesini bulun.

    ProjectType öğesinden hemen sonra bir [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi ekleyin.

2. Öğesinin metin değerini aşağıdaki değerlerden birine ayarlayın:

   1. Windows

   2. Office

   3. Veritabanı

   4. Web

      Örneğin: `<ProjectSubType>Database</ProjectSubType>`.

      Aşağıdaki örnekte, Office projeleri için kullanılabilen bir öğe şablonu gösterilmektedir.

   ```
   <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
       <TemplateData>
           <Name>Class</Name>
           <Description>An empty class file</Description>
           <Icon>Class.ico</Icon>
           <ProjectType>CSharp</ProjectType>
           <ProjectSubType>Office</ProjectSubType>
           <DefaultName>Class.cs</DefaultName>
       </TemplateData>
       <TemplateContent>
           <ProjectItem>Class1.cs</ProjectItem>
       </TemplateContent>
   </VSTemplate>

   ```

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'nı kullanmadan el ile bir öğe şablonu oluşturmak için

1. Proje ve proje öğesi oluşturun.

2. Proje öğesi bir şablon olarak kaydedilmeye hazırlanana kadar, Proje öğesini değiştirin.

3. Uygun şekilde, kod dosyasını parametre değiştirmenin nerede gerçekleşeceğini belirtecek şekilde değiştirin. Parametre değiştirme hakkında daha fazla bilgi için bkz. nasıl yapılır: şablonda parametreleri değiştirme.

4. Bir XML dosyası oluşturun ve bir. vstemplate dosya adı uzantısı kullanarak yeni öğe şabloninizle aynı dizinde kaydedin.

5. Öğe şablonu meta verileri sağlamak için. vstemplate XML dosyasını yazın. Daha fazla bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md) ve önceki bölümde bulunan örnek.

6. . Vstemplate dosyasını kaydedin ve kapatın.

7. Windows Gezgini 'nde, şablonunuza dahil etmek istediğiniz dosyaları seçin, seçime sağ tıklayın, Gönder ' e tıklayın ve ardından sıkıştırılmış (daraltılmış) klasör ' e tıklayın. Seçtiğiniz dosyalar bir. zip dosyasında sıkıştırılır.

8. . Zip dosyasını kopyalayın ve Kullanıcı öğesi şablonu konumuna yapıştırın. Visual Studio 2015 ' de varsayılan dizin.. \Users \\ < Kullanıcı adı \> \K\studio 2015 \ Templates\ıtemtemplates \\. Daha fazla bilgi için bkz. nasıl yapılır: proje ve öğe şablonlarını bulma ve düzenleme.

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md) [nasıl yapılır: birden çok dosya öğesi şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md) [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
