---
title: Mevcut proje öğesi şablonlarını Güncelleştir
description: Daha önce oluşturduğunuz proje öğesi şablonlarını güncelleştirmek için şablonu dışarı aktarma Sihirbazı 'Nı ve diğer el ile süreçlerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e3a709070d777ebaf600fc05abf0e651eaef5b1a
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596891"
---
# <a name="how-to-update-existing-templates"></a>Nasıl yapılır: mevcut şablonları güncelleştirme

Bir şablon oluşturup dosyaları bir *. zip* dosyasına sıkıştırdıktan sonra, şablonu değiştirmek isteyebilirsiniz. Bu işlemi, şablondaki dosyaları el ile değiştirerek veya şablonu temel alan bir projeden yeni bir şablonu dışarı aktararak yapabilirsiniz.

## <a name="use-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'Nı kullanma

Visual Studio, var olan bir şablonu güncelleştirmek için kullanılabilen bir **şablonu dışarı aktarma Sihirbazı** sağlar:

1. Menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje** ' yi seçin.

1. Güncelleştirmek istediğiniz şablonu seçin ve yeni projeyi oluşturma adımlarında devam edin.

1. Visual Studio 'da projeyi değiştirin. Örneğin, çıkış türünü değiştirin veya projeye yeni bir dosya ekleyin.

1. **Proje** menüsünde, **şablonu dışarı aktar**' ı seçin.

    **Şablonu dışarı aktarma Sihirbazı** açılır.

1. Şablonu bir *. zip* dosyası olarak dışarı aktarmak için sihirbazdaki yönergeleri izleyin.

1. Seçim *. Zip* dosyasını şu dizine yerleştirin: *\<version\> %USERPROFILE%\k\studio \templates\projecttemplates* , seçim için kullanılabilir hale getirir. Şablonu **dışarı aktar sihirbazında** **şablonu otomatik olarak Visual Studio 'ya aktar** seçeneğini seçmediyseniz bu adımı gerçekleştirmeniz gerekir.

1. Eski template *. zip* dosyasını silin.

## <a name="manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirme

Sıkıştırılmış *. zip* dosyasındaki dosyaları değiştirerek, **şablonu dışarı aktarma Sihirbazı 'nı** kullanmadan mevcut bir şablonu güncelleştirebilirsiniz.

### <a name="to-manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirmek için

1. Şablonu içeren *. zip* dosyasını bulun. Kullanıcı projesi şablonları, *\<version\> %USERPROFILE%\k\studio \Templates\projecttemplates* dizininde bulunur.

1. *. Zip* dosyasını ayıklayın.

1. Geçerli şablon dosyalarını değiştirin veya silin ya da şablona yeni dosyalar ekleyin.

1. Güncelleştirilmiş davranışı veya yeni dosyaları işlemek için *. vstemplate* XML dosyasını açın, değiştirin ve kaydedin.

    *. Vstemplate* şeması hakkında daha fazla bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md). Kaynak dosyalarında parametreleştiribilecekleri hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

1. Şablonunuzda bulunan dosyaları ve sağ tıklama ya da bağlam menüsünden seçin ve **Send to**  >  **Sıkıştırılmış (daraltılmış) klasöre** Gönder ' i seçin.

    Seçtiğiniz dosyalar bir *. zip* dosyasında sıkıştırılır.

1. Yeni *. zip* dosyasını eski *. zip* dosyası ile aynı dizine yerleştirin.

1. Ayıklanan şablon dosyalarını ve eski şablon *. zip* dosyasını silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Şablon parametreleri](../ide/template-parameters.md)
