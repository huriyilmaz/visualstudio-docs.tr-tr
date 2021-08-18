---
title: Özel Project ve Öğe Şablonları | Microsoft Docs
description: Visual Studio SDK'sı ile şablon oluşturma şablonlarının daha büyük uzantılara şablon eklemeye nasıl izin ver olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7efc545ac298830d2dd3a5ce85649941eb16fdfe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133373"
---
# <a name="create-custom-project-and-item-templates"></a>Özel proje ve öğe şablonları oluşturma

Visual Studio SDK'sı, özel bir proje şablonu ve özel öğe şablonu oluşturan proje şablonlarını içerir. Bu şablonlar bazı yaygın parametre değiştirmelerini içerir ve zip dosyası olarak oluşturur. Bunlar otomatik olarak dağıtlanmaz ve deneysel örnekte kullanılamaz. Oluşturulan zip dosyasını kullanıcı şablonu dizinine kopyalamanız gerekir.

Şablon oluşturma şablonları, şablonları daha büyük uzantılara dahil etmek için kullanılabilir. Bu, kaynak dosyalar üzerinde sürüm denetimi uygulama ve tek bir VSIX paketinde bir grup şablon projesi derlemenizi sağlar.

Ayrıca, bir şablonu, uygulama paketlerini yüklemek NuGet yapılandırabilirsiniz. Daha fazla bilgi için [bkz. NuGet şablonlarında Visual Studio paketleri.](/nuget/visual-studio-extensibility/visual-studio-templates)

Temel şablon oluşturma senaryoları için, sıkıştırılmış bir dosyaya **çıkış olarak çıkış** olarak Şablonu Dışarı Aktar sihirbazını kullansanız gerekir. Temel şablon oluşturma hakkında daha fazla bilgi için [bkz. Proje ve öğe şablonları oluşturma.](../ide/creating-project-and-item-templates.md)

> [!NOTE]
> 2017'Visual Studio başlayarak özel proje ve öğe şablonları için tarama artık gerçekleştirilmeyecek. Bunun yerine, uzantının bu şablonların yükleme konumunu açıklayan şablon bildirim dosyaları sağlaması gerekir. VSIX uzantılarınızı güncelleştirmek Visual Studio 2017'de kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız şablon bildirim dosyalarını el ile oluşturabilirsiniz. Daha fazla bilgi için, [bkz. Upgrading custom project and item templates for Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Şablon bildirimi şeması, şablon bildirim [Visual Studio başvurusunda belgelenmiş.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="create-a-project-template"></a>Proje şablonu oluşturma

1. Project Şablon projesi oluşturun. Proje şablonunu Yeni Project  iletişim kutusunda bulabilirsiniz. "proje şablonu" için arama ve C# veya Visual Basic seçin.

     Şablon bir sınıf dosyası, bir simge, *bir .vstemplate* dosyası, *ProjectTemplate.vbproj* veya *ProjectTemplate.csproj* adlı düzenlenebilir bir proje dosyası ve *genellikle resources.resx* dosyası, *AssemblyInfo* dosyası ve *.settings* dosyası gibi diğer proje türleri tarafından oluşturulan bazı dosyaları oluşturur. Her kod dosyası uygun olduğunda ortak parametre değiştirmeleri içerir.

![proje şablonu proje seçimi](media/project-template-selection.png)

2. Projeniz için gereken öğeleri ekleyin ve projeden kaldırın. Düzenlenebilir proje dosyasını, *AssemblyInfo dosyasını veya* *.vstemplate dosyasını* kaldıramazsanız.

3. *.vstemplate dosyasını ekleme* ve silme işlemlerini yansıtacak şekilde güncelleştirin. Project [](../extensibility/project-element-visual-studio-templates.md) öğesi, şablona dahil edilecek her dosya için bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) öğesi içermesi gerekir.

4. Kod dosyalarınızı ve kullanıcıya yönelik diğer içeriği değiştirme ve uygun parametre değiştirmeleri ekleme.

5. Oluşturulan içeriği gereken şekilde değiştirme.

6. Projeyi derleyin.

     Visual Studio şablon *.zip* bir dosya oluşturur. Dağıtlanmaz ve deneysel örnekte kullanılamaz.

## <a name="create-an-item-template"></a>Öğe şablonu oluşturma

1. Öğe Şablonu projesi oluşturun.

     Şablon bir sınıf dosyası, bir simge, *bir .vstemplate* dosyası ve *bir AssemblyInfo dosyası* oluşturur. Sınıf dosyası bazı ortak parametre değiştirmeleri içerir.

2. Projeniz için gereken öğeleri ekleyin ve projeden kaldırın.

3. *.vstemplate dosyasını ekleme* ve silme işlemlerini yansıtacak şekilde güncelleştirin. Project [](../extensibility/project-element-visual-studio-templates.md) öğesi, şablona dahil edilecek her dosya için bir [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) öğesi içermesi gerekir.

4. Kod dosyalarınızı ve kullanıcıya yönelik diğer içeriği değiştirme ve uygun parametre değiştirmeleri ekleme.

5. Oluşturulan içeriği gereken şekilde değiştirme.

6. Projeyi derleyin.

     Visual Studio şablonlarınızı içeren sıkıştırılmış bir dosya oluşturur. Dağıtlanmaz ve deneysel örnekte kullanılamaz.

## <a name="deployment"></a>Dağıtım

### <a name="to-deploy-the-project-or-item-template"></a>Proje veya öğe şablonunu dağıtmak için

1. VSIX projesi oluşturun. Daha fazla bilgi için bkz. [VSIX proje şablonu.](../extensibility/vsix-project-template.md)

2. VSIX projesini başlangıç projesi olarak ayarlayın. Uygulamanın **Çözüm Gezgini** VSIX proje düğümünü seçin, sağ tıklayın ve Başlangıç Olarak Ayarla'yı **Project.**

3. Proje şablonu projesini VSIX projesinin bir varlığı olarak ayarlayın. *.vsixmanifest dosyasını* açın. Varlıklar sekmesine **gidin ve** Yeni'yi **seçin.**

    1. Tür alanını **Microsoft.VisualStudio.ProjectTemplate** veya **Microsoft.VisualStudio.ItemTemplate olarak ayarlayın.** 

    2. Kaynak için A **project in current solution (Geçerli** çözümde bir proje) seçeneğini belirleyin ve ardından şablonlarınızı içeren projeyi seçin.

4. Çözümü derleme ve **F5 tuşuna basın.** Deneysel örnek görünür.

5. Bir proje şablonu projesi için, Visual C#  veya Visual Basic düğümünde Yeni Project **iletişim** kutusunda ( Dosya Yeni Project ) proje  >    >  şablon Visual Basic gerekir. Bir öğe şablonu projesi için, öğe şablonlarınızı Yeni Öğe Ekle iletişim **kutusunda listelenmiş olarak görüyorsanız.** Yeni Öğe **Ekle iletişim kutusunu** görüntülemek için, Çözüm Gezgini proje düğümünü seçin ve Yeni Öğe Ekle    >  **'yi seçin.**

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablonu başvurusu](../ide/creating-project-and-item-templates.md)
- [NuGet şablonlarında Visual Studio paketleri oluşturma](/nuget/visual-studio-extensibility/visual-studio-templates)
