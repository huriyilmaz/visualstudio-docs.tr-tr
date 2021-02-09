---
title: Özel proje ve öğe şablonları oluşturma | Microsoft Docs
description: Visual Studio SDK 'daki şablon oluşturma şablonlarının şablonları daha büyük uzantılara ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc5f347e3f5823613d11c8c217fcb2d29635867
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851354"
---
# <a name="create-custom-project-and-item-templates"></a>Özel proje ve öğe şablonları oluşturma

Visual Studio SDK, özel bir proje şablonu ve özel bir öğe şablonu oluşturan proje şablonları içerir. Bu şablonlar bazı ortak parametre alternatifleri içerir ve ZIP dosyaları olarak derleyin. Bunlar otomatik olarak dağıtılmaz ve deneysel örnekte kullanılamaz. Oluşturulan ZIP dosyasını Kullanıcı şablonu dizinine kopyalamanız gerekir.

Şablon oluşturma şablonları, şablonları daha büyük uzantılara eklemenizi sağlar. Bu, kaynak dosyalarda sürüm denetimi uygulamanıza ve bir grup şablon projesini tek bir VSıX paketinde oluşturmanıza olanak sağlar.

Ayrıca, NuGet paketlerini yüklemek için bir şablon yapılandırabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio şablonlarındaki NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates).

Temel şablon oluşturma senaryolarında, sıkıştırılmış bir dosyaya çıkış veren **şablonu dışarı aktarma** Sihirbazı 'nı kullanmanız gerekir. Temel şablon oluşturma hakkında daha fazla bilgi için bkz. [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Visual Studio 2017 ' den başlayarak özel proje ve öğe şablonlarının taranması artık gerçekleştirilmeyecek. Bunun yerine, uzantı Bu şablonların yüklemesinin konumunu tanımlayan şablon bildirim dosyaları sağlamalıdır. VSıX uzantılarınızı güncelleştirmek için Visual Studio 2017 ' i kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirim dosyalarını el ile oluşturmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio 2017 için özel proje ve öğe şablonlarını yükseltme](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Şablon bildirim şeması, [Visual Studio şablon bildirimi şema başvurusunda](../extensibility/visual-studio-template-manifest-schema-reference.md)belgelenmiştir.

## <a name="create-a-project-template"></a>Proje şablonu oluşturma

1. Proje şablonu projesi oluşturun. Proje şablonunu **Yeni proje** iletişim kutusunda "proje şablonu" arayarak ve C# ya da Visual Basic sürümünü seçerek bulabilirsiniz.

     Şablon bir sınıf dosyası, bir simge, *. vstemplate* dosyası, *ProjectTemplate. vbproj* veya *ProjectTemplate. csproj* adlı düzenlenebilir bir proje dosyası ve genellikle *kaynaklar. resx* dosyası, bir *AssemblyInfo* dosyası ve bir *. Settings* dosyası gibi diğer proje türleri tarafından oluşturulan bazı dosyaları oluşturur. Her kod dosyası uygun yerlerde ortak parametre alternatifleri içerir.

![Proje Şablonu proje seçimi](media/project-template-selection.png)

2. Projenize proje için gereken öğeleri ekleyin ve kaldırın. Düzenlenebilir proje dosyasını, *AssemblyInfo* dosyasını veya *. vstemplate* dosyasını kaldırmayın.

3. *. Vstemplate* dosyasını, eklemeleri ve silmeleri yansıtacak şekilde güncelleştirin. [Proje](../extensibility/project-element-visual-studio-templates.md) öğesi, şablona dahil edilecek her bir dosya Için bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) öğesi içermelidir.

4. Kod dosyalarınızı ve kullanıcıya yönelik diğer içerikleri değiştirin ve uygun parametre alternatifleri ekleyin.

5. Oluşturulan içeriği gereken şekilde değiştirin.

6. Projeyi derleyin.

     Visual Studio, şablonunuzu içeren bir *. zip* dosyası oluşturur. Dağıtılmadı ve deneysel örnekte yok.

## <a name="create-an-item-template"></a>Öğe şablonu oluşturma

1. Bir öğe şablonu projesi oluşturun.

     Şablon bir sınıf dosyası, bir simge, bir *. vstemplate* dosyası ve bir *AssemblyInfo* dosyası oluşturur. Sınıf dosyası bazı ortak parametre alternatifleri içerir.

2. Projenize proje için gereken öğeleri ekleyin ve kaldırın.

3. *. Vstemplate* dosyasını, eklemeleri ve silmeleri yansıtacak şekilde güncelleştirin. [Proje](../extensibility/project-element-visual-studio-templates.md) öğesi, şablona dahil edilecek her bir dosya Için bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) öğesi içermelidir.

4. Kod dosyalarınızı ve kullanıcıya yönelik diğer içerikleri değiştirin ve uygun parametre alternatifleri ekleyin.

5. Oluşturulan içeriği gerektiği gibi değiştirin.

6. Projeyi derleyin.

     Visual Studio, şablonunuzu içeren sıkıştırılmış bir dosya oluşturur. Dağıtılmadı ve deneysel örnekte yok.

## <a name="deployment"></a>Dağıtım

### <a name="to-deploy-the-project-or-item-template"></a>Projeyi veya öğe şablonunu dağıtmak için

1. VSıX projesi oluşturun. Daha fazla bilgi için bkz. [VSIX proje şablonu](../extensibility/vsix-project-template.md).

2. VSıX projesini başlangıç projesi olarak ayarlayın. **Çözüm GEZGINI** VSIX projesi düğümünü seçin, sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

3. Proje şablonu projesini VSıX projesinin bir varlığı olarak ayarlayın. *. Valtmanifest* dosyasını açın. **Varlıklar** sekmesine gidin ve **Yeni**' yi seçin.

    1. **Tür** alanını **Microsoft. VisualStudio. ProjectTemplate** veya **Microsoft. VisualStudio. ItemTemplate** olarak ayarlayın.

    2. Kaynak için **geçerli çözüm ' de bir proje** seçin ve ardından şablonunuzu içeren projeyi seçin.

4. Çözümü oluşturun ve **F5** tuşuna basın. Deneysel örnek görüntülenir.

5. Proje şablonu projesi için, proje şablonunuzu,Visual C# veya Visual Basic düğümündeki **Yeni proje** iletişim kutusunda (dosya  >  **Yeni**  >  **Proje**) listelendiğini görmeniz gerekir. Bir öğe şablonu projesi için, öğe şablonunuzun **Yeni öğe Ekle** iletişim kutusunda listelendiğini görmeniz gerekir. **Yeni öğe Ekle** iletişim kutusunu görüntülemek için, **Çözüm Gezgini**, proje düğümünü seçin ve   >  **Yeni öğe** Ekle ' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablon başvurusu](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablonlarındaki NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates)
