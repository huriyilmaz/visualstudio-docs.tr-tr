---
title: Proje şablonları oluşturma
description: Visual Studio ' de proje şablonları oluşturmak için şablonu dışarı aktarma Sihirbazı 'Nı ve diğer yöntemleri kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 8ccc1c8570d5028a8fee84d12efb583a1a6ce8be23dd468a3b63dcc32696d15f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121319341"
---
# <a name="how-to-create-project-templates"></a>Nasıl yapılır: proje şablonları oluşturma

Bu konu başlığı altında, şablonunuzu bir *.zip* dosyasında paketleyen **şablonu dışarı aktarma Sihirbazı 'nı** kullanarak nasıl şablon oluşturacağınız gösterilmektedir.

## <a name="use-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'Nı kullanma

1. Bir proje oluşturun.

    > [!NOTE]
    > Bir şablon için kaynak olacak bir proje adlandırırken yalnızca geçerli tanımlayıcı karakterler kullanın. Aksi takdirde, şablondan oluşturulan projelerde derleme hataları meydana gelebilir. geçerli tanımlayıcı karakterleri hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) veya [tanımlayıcılar (C++)](/cpp/cpp/identifiers-cpp). Alternatif olarak, sınıflar ve ad alanları için "güvenli" adlar kullanmak için [şablon parametrelerini](../ide/template-parameters.md) kullanabilirsiniz.

2. Proje, bir şablon olarak verilmeye hazırlanana kadar projeyi düzenleyin. Örneğin, parametre değiştirmenin nerede gerçekleşmesi gerektiğini belirtmek için kod dosyalarını düzenlemek isteyebilirsiniz. Bkz. [nasıl yapılır: şablonda parametreleri değiştirme](../ide/how-to-substitute-parameters-in-a-template.md).

3. **Project** menüsünde, **şablonu dışarı aktar**' ı seçin.

   **Şablonu dışarı aktarma Sihirbazı** açılır.

4. **şablon türü seç** sayfasında **Project şablon**' u seçin. Bir şablona dışarı aktarmak istediğiniz projeyi seçin ve ardından **İleri**' yi seçin.

::: moniker range="vs-2017"

5. **Şablon seçeneklerini seçin** sayfasında, şablonunuz için bir ad ve isteğe bağlı olarak bir açıklama, simge ve önizleme resmi girin. bu öğeler **yeni Project** iletişim kutusunda görünür. **Son**’u seçin.

   Proje bir *.zip* dosyasına aktarılır ve belirtilen çıkış konumuna yerleştirilir ve seçilirse, Visual Studio içine aktarılır.

**yeni Project** iletişim kutusunda şablonunuzu bulmak için, **yüklü** ' i genişletin ve ardından `ProjectType` *. vstemplate* dosyasındaki öğesine karşılık gelen kategoriyi genişletin. Örneğin, içeren bir *. vstemplate* dosyası `<ProjectType>CSharp</ProjectType>`   >  , varsayılan olarak yüklü **Visual C#** altında görünür. Şablonu, bu dizinde bir klasör oluşturup şablonun *.zip* dosyasını yerleştirerek proje türünün bir alt dizininde düzenleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. **Şablon seçeneklerini seçin** sayfasında, şablonunuz için bir ad ve isteğe bağlı olarak bir açıklama, simge ve önizleme resmi girin. Bu öğeler yeni bir proje oluşturduğunuz iletişim kutusunda görünür. **Son**’u seçin.

   Proje bir *.zip* dosyasına aktarılır ve belirtilen çıkış konumuna yerleştirilir ve seçilirse, Visual Studio içine aktarılır.

Yeni bir proje oluşturduğunuz iletişim kutusunda şablonunuzu bulmak için bunu ada göre arayın veya listede ilerleyin. (Dil veya proje türüne göre filtreleme, Kullanıcı şablonları için şu anda mümkün değildir.)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Proje şablonları oluşturmanın diğer yolları

Projeyi bir klasöre oluşturan dosyaları toplayıp, uygun meta verilerle bir *. vstemplate* XML dosyası oluşturarak proje şablonlarını el ile oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: el ile Web şablonları oluşturma](../ide/how-to-manually-create-web-templates.md).

Visual Studio SDK 'sı yüklüyse, **vsıx Project** şablonunu kullanarak bir vsıx dosyasındaki tamamlanmış şablonu sardırabilirsiniz. Daha fazla bilgi için bkz. [VSIX proje şablonunu kullanmaya başlama](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [VSıX proje şablonu ile çalışmaya başlama](../extensibility/getting-started-with-the-vsix-project-template.md)
- [Proje ve öğe şablonlarını özelleştirme](customizing-project-and-item-templates.md)
