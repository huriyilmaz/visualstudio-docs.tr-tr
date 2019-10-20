---
title: Mevcut proje öğesi şablonlarını Güncelleştir
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee0118ce4181a12ca4c199b8174a28fb4b431063
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656536"
---
# <a name="how-to-update-existing-templates"></a>Nasıl yapılır: mevcut şablonları güncelleştirme

Bir şablon oluşturup dosyaları bir *. zip* dosyasına sıkıştırdıktan sonra, şablonu değiştirmek isteyebilirsiniz. Bu işlemi, şablondaki dosyaları el ile değiştirerek veya şablonu temel alan bir projeden yeni bir şablonu dışarı aktararak yapabilirsiniz.

## <a name="use-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'Nı kullanma

Visual Studio, var olan bir şablonu güncelleştirmek için kullanılabilen bir **şablonu dışarı aktarma Sihirbazı** sağlar:

1. Menü çubuğundan **dosya**  > **Yeni**  > **projesi** öğesini seçin.

1. Güncelleştirmek istediğiniz şablonu seçin ve yeni projeyi oluşturma adımlarında devam edin.

1. Visual Studio 'da projeyi değiştirin. Örneğin, çıkış türünü değiştirin veya projeye yeni bir dosya ekleyin.

1. **Proje** menüsünde, **şablonu dışarı aktar**' ı seçin.

    **Şablonu dışarı aktarma Sihirbazı** açılır.

1. Şablonu bir *. zip* dosyası olarak dışarı aktarmak için sihirbazdaki yönergeleri izleyin.

1. Seçim *. Zip* dosyasını şu dizine yerleştirin: *%userprofıle%\k\studio \<version \> \Templates\ProjectTemplates* seçim için kullanılabilir hale getirir. Şablonu **dışarı aktar sihirbazında** **şablonu otomatik olarak Visual Studio 'ya aktar** seçeneğini seçmediyseniz bu adımı gerçekleştirmeniz gerekir.

1. Eski template *. zip* dosyasını silin.

## <a name="manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirme

Sıkıştırılmış *. zip* dosyasındaki dosyaları değiştirerek, **şablonu dışarı aktarma Sihirbazı 'nı**kullanmadan mevcut bir şablonu güncelleştirebilirsiniz.

### <a name="to-manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirmek için

1. Şablonu içeren *. zip* dosyasını bulun. Kullanıcı projesi şablonları, *%USERPROFILE%\k\studio \<version \> \Templates\ProjectTemplates*yolunda bulunur.

1. *. Zip* dosyasını ayıklayın.

1. Geçerli şablon dosyalarını değiştirin veya silin ya da şablona yeni dosyalar ekleyin.

1. Güncelleştirilmiş davranışı veya yeni dosyaları işlemek için *. vstemplate* XML dosyasını açın, değiştirin ve kaydedin.

    *. Vstemplate* şeması hakkında daha fazla bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md). Kaynak dosyalarında parametreleştiribilecekleri hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

1. Şablonunuzda dosyaları seçin ve sağ tıklayıp bağlam menüsünden  > **Sıkıştırılmış (daraltılmış) klasöre** **Gönder** ' i seçin.

    Seçtiğiniz dosyalar bir *. zip* dosyasında sıkıştırılır.

1. Yeni *. zip* dosyasını eski *. zip* dosyası ile aynı dizine yerleştirin.

1. Ayıklanan şablon dosyalarını ve eski şablon *. zip* dosyasını silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Şablon parametreleri](../ide/template-parameters.md)