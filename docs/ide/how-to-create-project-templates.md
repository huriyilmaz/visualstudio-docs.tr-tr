---
title: Proje şablonları oluşturma
ms.date: 01/02/2018
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: f4caebfdc4e61b683e0f1407d1522f6da2328fcf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591079"
---
# <a name="how-to-create-project-templates"></a>Nasıl yapılı: Proje şablonları oluşturma

Bu konu, şablonunuzu *.zip* dosyasında paketlereden **Dışa Aktarma Şablonu Sihirbazı'nı**kullanarak şablon oluşturmayı gösterir.

## <a name="use-the-export-template-wizard"></a>Dışa Aktarma Şablonu Sihirbazı'nı kullanma

1. Bir proje oluşturun.

    > [!NOTE]
    > Şablonun kaynağı olacak bir projeyi adlandırırken yalnızca geçerli tanımlayıcı karakterleri kullanın. Aksi takdirde, şablondan oluşturulan projelerde derleme hataları oluşabilir. Geçerli tanımlayıcı karakterler hakkında daha fazla bilgi için, [Bildirilen öğe adları (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) veya [Tanımlayıcılar (C++)](/cpp/cpp/identifiers-cpp)bakın. Alternatif olarak, sınıflar ve ad alanları için "güvenli" adlar kullanmak için [Şablon parametrelerini](../ide/template-parameters.md) kullanabilirsiniz.

2. Şablon olarak dışa aktarılacak hazır olana kadar projeyi edin. Örneğin, parametre değişiminin nerede yapılması gerektiğini belirtmek için kod dosyalarını da nızı dinlemek isteyebilirsiniz. [Bkz. Nasıl: Şablondaki parametreleri değiştirin.](../ide/how-to-substitute-parameters-in-a-template.md)

3. **Proje** menüsünde **Dışa Aktarma Şablonu'nu**seçin.

   **Dışa Aktarma Şablonu Sihirbazı** açılır.

4. Şablon **Türü Seç** sayfasında **Proje Şablonu'nu**seçin. Şablona aktarmak istediğiniz projeyi seçin ve sonra **İleri'yi**seçin.

::: moniker range="vs-2017"

5. Şablon **Seçeneklerini Seç** sayfasında şablonunuz için bir ad ve isteğe bağlı açıklama, simge ve önizleme resmi girin. Bu öğeler Yeni **Proje** iletişim kutusunda görünür. **Son**’u seçin.

   Proje bir *.zip* dosyasına dışa aktarılır ve belirtilen çıktı konumuna yerleştirilir ve seçilirse Visual Studio'ya aktarılır.

Şablonunuzu **Yeni Proje** iletişim kutusunda bulmak için **Yüklü'yi** genişletin ve ardından `ProjectType` *.vstemplate* dosyasındaki öğeye karşılık gelen kategoriyi genişletin. Örneğin, yüklü > **Visual C#** **altında**varsayılan olarak `<ProjectType>CSharp</ProjectType>` bir *.vstemplate* dosyası görüntülenir. Şablonunuzu, bu dizinde bir klasör oluşturarak ve şablonunuzun *.zip* dosyasını içine yerleştirerek proje türünün bir alt dizininde düzenleyebilirsiniz. Daha fazla bilgi için [bkz: Şablonları bulma ve düzenleme.](../ide/how-to-locate-and-organize-project-and-item-templates.md)

::: moniker-end

::: moniker range=">=vs-2019"

5. Şablon **Seçeneklerini Seç** sayfasında şablonunuz için bir ad ve isteğe bağlı açıklama, simge ve önizleme resmi girin. Bu öğeler, yeni bir proje oluşturduğunuz iletişim kutusunda görünür. **Son**’u seçin.

   Proje bir *.zip* dosyasına dışa aktarılır ve belirtilen çıktı konumuna yerleştirilir ve seçilirse Visual Studio'ya aktarılır.

Şablonunuzu yeni bir proje oluşturduğunuz iletişim kutusunda bulmak için, ada göre arayın veya listede ilerleyin. (Şu anda kullanıcı şablonları için dil veya proje türüne göre filtreleme mümkün değildir.)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Proje şablonları oluşturmanın diğer yolları

Projeyi oluşturan dosyaları bir klasörde toplayarak ve uygun meta verilere sahip bir *.vstemplate* XML dosyası oluşturarak proje şablonlarını el ile oluşturabilirsiniz. Daha fazla bilgi için [bkz: Web şablonlarını el ile oluşturun.](../ide/how-to-manually-create-web-templates.md)

Visual Studio SDK yüklüyse, **VSIX Project** şablonu kullanarak tamamlanmış şablonu dağıtım için vsix dosyasına sarabilirsiniz. Daha fazla bilgi için [VSIX proje şablonuna başlayın.](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılı: Öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [VSIX proje şablonu yla başlayın](../extensibility/getting-started-with-the-vsix-project-template.md)
