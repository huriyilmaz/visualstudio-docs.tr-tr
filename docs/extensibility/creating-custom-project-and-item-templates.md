---
title: Özel Proje ve Öğe Şablonları Oluşturma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739455"
---
# <a name="create-custom-project-and-item-templates"></a>Özel proje ve öğe şablonları oluşturma

Visual Studio SDK, özel bir proje şablonu ve özel öğe şablonu oluşturan proje şablonları içerir. Bu şablonlar bazı ortak parametre değiştirmeleri içerir ve zip dosyaları olarak oluşturun. Bunlar otomatik olarak dağıtılamıyor ve deneysel örnekte kullanılamaz. Oluşturulan zip dosyasını kullanıcı şablondizini için kopyalamanız gerekir.

Şablon oluşturma şablonları, şablonları daha büyük uzantılara eklemenize izin sağlar. Bu, kaynak dosyalarda sürüm denetimini uygulamanıza ve bir grup şablon projeyi tek bir VSIX paketinde oluşturmanıza olanak tanır.

NuGet paketlerini yüklemek için bir şablon da yapılandırabilirsiniz. Daha fazla bilgi için [Visual Studio şablonlarında NuGet paketlerine](/nuget/visual-studio-extensibility/visual-studio-templates)bakın.

Temel şablon oluşturma senaryoları için, sıkıştırılmış bir dosyaya çıktı ları dışa aktarma **şablonu** sihirbazı kullanmanız gerekir. Temel şablon oluşturma hakkında daha fazla bilgi için [bkz.](../ide/creating-project-and-item-templates.md)

> [!NOTE]
> Visual Studio 2017'den itibaren özel proje ve öğe şablonları için tarama artık gerçekleştirilmeyecek. Bunun yerine, uzantı, bu şablonların yükleme konumunu açıklayan şablon bildirimi dosyaları sağlaması gerekir. VSIX uzantılarınızı güncellemek için Visual Studio 2017'yi kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirimi dosyalarını elle oluşturmanız gerekir. Daha fazla bilgi için [Visual Studio 2017 için özel proje ve öğe şablonlarını yükseltme ye](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)bakın. Şablon bildirimi şeması Visual Studio [şablon ula'da belgelenmiştir.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="create-a-project-template"></a>Proje şablonu oluşturma

1. Proje Şablonu projesi oluşturun. "Proje şablonu" araması yaparak ve C# veya Visual Basic sürümünü seçerek proje şablonlarını **Yeni Proje** iletişim kutusunda bulabilirsiniz.

     Şablon bir sınıf dosyası, bir simge, bir *.vstemplate* dosyası, *ProjectTemplate.vbproj* veya *ProjectTemplate.csproj*adlı bir editable proje dosyası ve genellikle diğer proje türleri tarafından oluşturulan bazı dosyalar oluşturur, böyle bir *resources.resx* dosyası, *bir AssemblyInfo* dosyası ve *.settings* dosyası. Her kod dosyası, uygun olduğunda ortak parametre değiştirmeleri içerir.

![proje şablonu proje seçimi](media/project-template-selection.png)

2. Projeniz için gerekli olan öğeleri projeye ekleyin ve kaldırın. Editable proje dosyasını, *AssemblyInfo* dosyasını veya *.vstemplate* dosyasını kaldırmayın.

3. Eklemeleri ve silmeleri yansıtacak *şekilde .vstemplate* dosyasını güncelleştirin. [Proje](../extensibility/project-element-visual-studio-templates.md) öğesi, şablona eklenecek her dosya için bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) öğesi içermelidir.

4. Kod dosyalarınızı ve kullanıcıya yönelik diğer içeriği değiştirin ve uygun parametre değiştirmeleri ekleyin.

5. Oluşturulan içeriği gerektiği gibi değiştirin.

6. Projeyi derleyin.

     Visual Studio şablonunuzu içeren bir *.zip* dosyası oluşturur. Dağıtılmadı ve deneysel örnekte kullanılamaz.

## <a name="create-an-item-template"></a>Öğe şablonu oluşturma

1. Öğe Şablonu projesi oluşturun.

     Şablon bir sınıf dosyası, bir simge, *.vstemplate* dosyası ve bir *AssemblyInfo* dosyası oluşturur. Sınıf dosyası bazı ortak parametre değiştirmeleri içerir.

2. Projeniz için gerekli olan öğeleri projeye ekleyin ve kaldırın.

3. Eklemeleri ve silmeleri yansıtacak *şekilde .vstemplate* dosyasını güncelleştirin. [Proje](../extensibility/project-element-visual-studio-templates.md) öğesi, şablona eklenecek her dosya için bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) öğesi içermelidir.

4. Kod dosyalarınızı ve kullanıcıya yönelik diğer içeriği değiştirin ve uygun parametre değiştirmeleri ekleyin.

5. Oluşturulan içeriği gerektiği gibi değiştirin.

6. Projeyi derleyin.

     Visual Studio şablonunuzu içeren sıkıştırılmış bir dosya oluşturur. Dağıtılmadı ve deneysel örnekte kullanılamaz.

## <a name="deployment"></a>Dağıtım

### <a name="to-deploy-the-project-or-item-template"></a>Proje veya madde şablonu dağıtmak için

1. Bir VSIX projesi oluşturun. Daha fazla bilgi için [VSIX proje şablonuna](../extensibility/vsix-project-template.md)bakın.

2. VSIX projesini başlangıç projesi olarak ayarlayın. Çözüm **Gezgini'nde**VSIX proje düğümünü, sağ tıklatma yı ve **Başlangıç Projesi olarak Ayarla'yı**seçin.

3. Proje şablonu projesini VSIX projesinin bir varlığı olarak ayarlayın. *.vsixmanifest* dosyasını açın. **Varlıklar** sekmesine gidin ve **Yeni'yi**tıklatın.

    1. **Tür** alanını **Microsoft.VisualStudio.ProjectTemplate veya Microsoft.VisualStudio.ItemTemplate** olarak ayarlayın. **Microsoft.VisualStudio.ItemTemplate**

    2. Kaynak için **geçerli çözüm seçeneğinde A projesini** seçin ve ardından şablonunuzu içeren projeyi seçin.

4. Çözümü oluşturun ve **F5 tuşuna**basın. Deneysel örnek görüntülenir.

5. Proje şablonu projesi için, Proje şablonunuzu **Visual** C# veya Visual Basic düğümünde Yeni Proje iletişim kutusunda **(Dosya** > **Yeni** > **Proje)** listelenmiş olarak görmeniz gerekir. Öğe şablonu projesi için, **Yeni Öğe Ekle** iletişim kutusunda öğe şablonunuzu görmeniz gerekir. **Yeni Öğe Ekle** iletişim kutusunu görüntülemek için Çözüm **Gezgini'nden**proje düğümünü seçin ve**Yeni Öğe** **Ekle'yi** > tıklatın).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablon başvurusu](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablonlarında NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates)
