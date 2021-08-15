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
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 8638377137e9469ce1e47c606975281393241ee0296e9e974efe025352c2f5ed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121318622"
---
# <a name="how-to-update-existing-templates"></a>Nasıl yapılır: mevcut şablonları güncelleştirme

Bir şablon oluşturup dosyaları bir *.zip* dosyasına sıkıştırdıktan sonra, şablonu değiştirmek isteyebilirsiniz. Bu işlemi, şablondaki dosyaları el ile değiştirerek veya şablonu temel alan bir projeden yeni bir şablonu dışarı aktararak yapabilirsiniz.

## <a name="use-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'Nı kullanma

Visual Studio, var olan bir şablonu güncelleştirmek için kullanılabilecek bir **şablon dışarı aktarma sihirbazı** sağlar:

1. menü çubuğundan **dosya**  >  **yeni**  >  **Project** seçin.

1. Güncelleştirmek istediğiniz şablonu seçin ve yeni projeyi oluşturma adımlarında devam edin.

1. Projeyi Visual Studio değiştirin. Örneğin, çıkış türünü değiştirin veya projeye yeni bir dosya ekleyin.

1. **Project** menüsünde, **şablonu dışarı aktar**' ı seçin.

    **Şablonu dışarı aktarma Sihirbazı** açılır.

1. Şablonu bir *.zip* dosyası olarak dışarı aktarmak için sihirbazdaki yönergeleri izleyin.

1. Seçim *.zip* dosyasını şu dizine yerleştirin: *%userprofıle%\documents\ Visual Studio \<version\> \templates\projecttemplates* seçime uygun hale getirmek için. şablonu **dışarı aktar sihirbazında** **şablonu otomatik olarak Visual Studio aktar** seçeneğini seçmediyseniz bu adımı gerçekleştirmeniz gerekir.

1. Eski şablon *.zip* dosyasını silin.

## <a name="manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirme

Sıkıştırılmış *.zip* dosyadaki dosyaları değiştirerek, **şablonu dışarı aktarma Sihirbazı 'nı** kullanmadan mevcut bir şablonu güncelleştirebilirsiniz.

### <a name="to-manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirmek için

1. Şablonu içeren *.zip* dosyasını bulun. kullanıcı projesi şablonları, *%userprofile%\documents\ Visual Studio \<version\> \templates\projecttemplates* konumunda bulunur.

1. *.zip* dosyasını ayıklayın.

1. Geçerli şablon dosyalarını değiştirin veya silin ya da şablona yeni dosyalar ekleyin.

1. Güncelleştirilmiş davranışı veya yeni dosyaları işlemek için *. vstemplate* XML dosyasını açın, değiştirin ve kaydedin.

    *. vstemplate* şeması hakkında daha fazla bilgi için bkz. [Visual Studio şablon şeması başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md). Kaynak dosyalarında parametreleştiribilecekleri hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

1. Şablonunuzda bulunan dosyaları ve sağ tıklama ya da bağlam menüsünden seçin ve   >  **Sıkıştırılmış (daraltılmış) klasöre** Gönder ' i seçin.

    Seçtiğiniz dosyalar bir *.zip* dosyasında sıkıştırılır.

1. Yeni *.zip* dosyasını eski *.zip* dosyası ile aynı dizine yerleştirin.

1. Ayıklanan şablon dosyalarını ve eski şablon *.zip* dosyasını silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Şablon parametreleri](../ide/template-parameters.md)
