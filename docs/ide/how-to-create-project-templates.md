---
title: Proje şablonları oluşturma
ms.date: 01/02/2018
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f21c20880263a00d36c2fd21097bf8ee8c621d99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656092"
---
# <a name="how-to-create-project-templates"></a>Nasıl yapılır: proje şablonları oluşturma

Bu konu başlığı altında, şablonunuzu bir *. zip* dosyasında paketleyen **şablonu dışarı aktarma Sihirbazı 'nı**kullanarak nasıl şablon oluşturacağınız gösterilmektedir.

## <a name="use-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'Nı kullanma

1. Bir proje oluşturun.

    > [!NOTE]
    > Bir şablon için kaynak olacak bir proje adlandırırken yalnızca geçerli tanımlayıcı karakterler kullanın. Aksi takdirde, şablondan oluşturulan projelerde derleme hataları meydana gelebilir. Geçerli tanımlayıcı karakterleri hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) veya [tanımlayıcılarC++()](/cpp/cpp/identifiers-cpp). Alternatif olarak, sınıflar ve ad alanları için "güvenli" adlar kullanmak için [şablon parametrelerini](../ide/template-parameters.md) kullanabilirsiniz.

2. Proje, bir şablon olarak verilmeye hazırlanana kadar projeyi düzenleyin. Örneğin, parametre değiştirmenin nerede gerçekleşmesi gerektiğini belirtmek için kod dosyalarını düzenlemek isteyebilirsiniz. Bkz. [nasıl yapılır: şablonda parametreleri değiştirme](../ide/how-to-substitute-parameters-in-a-template.md).

3. **Proje** menüsünde, **şablonu dışarı aktar**' ı seçin.

   **Şablonu dışarı aktarma Sihirbazı** açılır.

4. **Şablon türü seç** sayfasında, **proje şablonu**' nu seçin. Bir şablona dışarı aktarmak istediğiniz projeyi seçin ve ardından **İleri**' yi seçin.

::: moniker range="vs-2017"

5. **Şablon seçeneklerini seçin** sayfasında, şablonunuz için bir ad ve isteğe bağlı olarak bir açıklama, simge ve önizleme resmi girin. Bu öğeler, **Yeni proje** iletişim kutusunda görünür. **Son**' a tıklayın.

   Proje bir *. zip* dosyasına aktarılır ve belirtilen çıktı konumuna yerleştirilir ve seçilirse, Visual Studio 'ya içeri aktarılır.

**Yeni proje** iletişim kutusunda şablonunuzu bulmak Için, **yüklü** ' i genişletin ve ardından *. vstemplate* dosyasındaki `ProjectType` öğesine karşılık gelen kategoriyi genişletin. Örneğin, `<ProjectType>CSharp</ProjectType>` içeren bir *. vstemplate* dosyası, varsayılan olarak **yüklü**  > **görseli C#** altında görünür. Bu dizinde bir klasör oluşturup şablonun *. zip* dosyasını içine yerleştirerek, şablonunuzu proje türünün bir alt dizininde düzenleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. **Şablon seçeneklerini seçin** sayfasında, şablonunuz için bir ad ve isteğe bağlı olarak bir açıklama, simge ve önizleme resmi girin. Bu öğeler yeni bir proje oluşturduğunuz iletişim kutusunda görünür. **Son**' a tıklayın.

   Proje bir *. zip* dosyasına aktarılır ve belirtilen çıktı konumuna yerleştirilir ve seçilirse, Visual Studio 'ya içeri aktarılır.

Yeni bir proje oluşturduğunuz iletişim kutusunda şablonunuzu bulmak için bunu ada göre arayın veya listede ilerleyin. (Dil veya proje türüne göre filtreleme, Kullanıcı şablonları için şu anda mümkün değildir.)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Proje şablonları oluşturmanın diğer yolları

Projeyi bir klasöre oluşturan dosyaları toplayıp, uygun meta verilerle bir *. vstemplate* XML dosyası oluşturarak proje şablonlarını el ile oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: el ile Web şablonları oluşturma](../ide/how-to-manually-create-web-templates.md).

Visual Studio SDK 'Sı yüklüyse, **VSIX proje** şablonunu kullanarak bir VSIX dosyasındaki tamamlanmış şablonu sardırabilirsiniz. Daha fazla bilgi için bkz. [VSIX proje şablonunu kullanmaya başlama](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [VSıX proje şablonu ile çalışmaya başlama](../extensibility/getting-started-with-the-vsix-project-template.md)