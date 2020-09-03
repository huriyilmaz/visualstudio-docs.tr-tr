---
title: Özel Proje ve Öğe Şablonları Oluşturma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197404"
---
# <a name="creating-custom-project-and-item-templates"></a>Özel Proje ve Öğe Şablonları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK, özel bir proje şablonu ve özel bir öğe şablonu oluşturan proje şablonları içerir. Bu şablonlar bazı ortak parametre alternatifleri içerir ve ZIP dosyaları olarak derleyin. Bunlar otomatik olarak dağıtılmaz ve deneysel örnekte kullanılamaz. Zip dosyasını istediğiniz konuma kopyalayın

Şablon oluşturma şablonları, şablonları daha büyük uzantılara eklemenizi sağlar. Uzantılara şablonlar ekleme, kaynak dosyalarda sürüm denetimi uygulamanıza ve bir grup şablon projesini tek bir VSıX paketinde oluşturmanıza imkan tanır.

Temel şablon oluşturma senaryolarında, sıkıştırılmış bir dosyaya çıkış veren **şablonu dışarı aktarma** Sihirbazı 'nı kullanmanız gerekir. Temel şablon oluşturma hakkında daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

Visual Studio 2017 ' den başlayarak, özel proje ve öğe şablonlarının taranması artık gerçekleştirilmez. Bunun yerine, uzantı Bu şablonların yüklemesinin konumunu tanımlayan şablon bildirim dosyaları sağlamalıdır. VSıX uzantılarınızı güncelleştirmek için Preview 2 yüklemesi ' ni kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirim dosyalarını el ile oluşturmanız gerekir. Daha fazla bilgi için bkz. [yükseltme özel Visual Studio için Proje ve Öğe Şablonları 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Şablon bildirim şeması, [Visual Studio şablon bildirimi şema başvurusunda](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)belgelenmiştir.

## <a name="create-a-project-template"></a>Proje şablonu oluşturma

1. Proje şablonu projesi oluşturun. Proje şablonunu **Yeni proje** iletişim kutusunda Visual Basic veya Visual C# **genişletilebilirlik** klasöründe bulabilirsiniz.

     Şablon bir sınıf dosyası, bir simge,. vstemplate dosyası, ProjectTemplate. vbproj veya ProjectTemplate. csproj adlı düzenlenebilir bir proje dosyası ve genellikle kaynaklar. resx dosyası, bir AssemblyInfo dosyası ve bir. Settings dosyası gibi diğer proje türleri tarafından oluşturulan bazı dosyaları oluşturur. Her kod dosyası uygun yerlerde ortak parametre alternatifleri içerir.

2. Projenize proje için gereken öğeleri ekleyin ve kaldırın. Düzenlenebilir proje dosyasını, AssemblyInfo dosyasını veya. vstemplate dosyasını kaldırmayın.

3. . Vstemplate dosyasını, eklemeleri ve silmeleri yansıtacak şekilde güncelleştirin. [Proje](../extensibility/project-element-visual-studio-templates.md) öğesi, şablona dahil edilecek her bir dosya Için bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) öğesi içermelidir.

4. Kod dosyalarınızı ve kullanıcıya yönelik diğer içerikleri değiştirin ve uygun parametre alternatifleri ekleyin.

5. Oluşturulan içeriği gereken şekilde değiştirin.

6. Projeyi derleyin.

     Visual Studio, şablonunuzu içeren bir. zip dosyası oluşturur. Dağıtılmadı ve deneysel örnekte yok.

## <a name="create-an-item-template"></a>Öğe şablonu oluşturma

1. Bir öğe şablonu projesi oluşturun.

     Şablon bir sınıf dosyası, bir simge, bir. vstemplate dosyası ve bir AssemblyInfo dosyası oluşturur. Sınıf dosyası bazı ortak parametre alternatifleri içerir.

2. Projenize proje için gereken öğeleri ekleyin ve kaldırın.

3. . Vstemplate dosyasını, eklemeleri ve silmeleri yansıtacak şekilde güncelleştirin. [Proje](../extensibility/project-element-visual-studio-templates.md) öğesi, şablona dahil edilecek her bir dosya Için bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) öğesi içermelidir.

4. Kod dosyalarınızı ve kullanıcıya yönelik diğer içerikleri değiştirin ve uygun parametre alternatifleri ekleyin.

5. Oluşturulan içeriği gerektiği gibi değiştirin.

6. Projeyi derleyin.

     Visual Studio, şablonunuzu içeren sıkıştırılmış bir dosya oluşturur. Dağıtılmadı ve deneysel örnekte yok.

## <a name="deploy-the-project-or-item-template"></a>Projeyi veya öğe şablonunu dağıtma

1. VSıX projesi oluşturun. Daha fazla bilgi için bkz. [VSIX proje şablonu](../extensibility/vsix-project-template.md).

2. VSıX projesini başlangıç projesi olarak ayarlayın. **Çözüm GEZGINI**VSIX projesi düğümünü seçin, sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

3. Proje şablonu projesini VSıX projesinin bir varlığı olarak ayarlayın. . Valtmanifest dosyasını açın. **Varlıklar** sekmesine gidin ve **Yeni**' ye tıklayın.

    1. **Tür** alanını **Microsoft. VisualStudio. ProjectTemplate** veya **Microsoft. VisualStudio. ItemTemplate**olarak ayarlayın.

    2. Kaynak için **geçerli çözüm ' de bir proje** seçin ve ardından şablonunuzu içeren projeyi seçin.

4. Çözümü oluşturun ve F5 tuşuna basın. Deneysel örnek görüntülenir.

5. Proje şablonu projesi için, Visual C# veya Visual Basic düğümündeki **Yeni proje** iletişim kutusunda (**dosya/yeni/proje**) listelenen proje şablonunuzu görmeniz gerekir. Bir öğe şablonu projesi için, öğe şablonunuzu yeni öğe Ekle iletişim kutusunda görmeniz gerekir ( **Çözüm Gezgini**, proje düğümünü seçin ve **Ekle/yeni öğe**' ye tıklayın).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Şablon Başvurusu](../ide/visual-studio-template-reference.md)