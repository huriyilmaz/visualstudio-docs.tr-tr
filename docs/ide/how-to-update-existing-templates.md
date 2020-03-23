---
title: Varolan proje öğesi şablonlarını güncelleştirme
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 44f99646330d3c8a75bd94310bc0adf9073f9d49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591365"
---
# <a name="how-to-update-existing-templates"></a>Nasıl yapılsın: Varolan şablonları güncelleştirme

Bir şablon oluşturduktan ve dosyaları *bir .zip* dosyasına sıkıştırdıktan sonra şablonu değiştirmek isteyebilirsiniz. Bunu, şablondaki dosyaları el ile değiştirerek veya şablonu temel alan bir projeden yeni bir şablon dışa aktararak yapabilirsiniz.

## <a name="use-the-export-template-wizard"></a>Dışa Aktarma Şablonu Sihirbazı'nı kullanma

Visual Studio, varolan bir şablonu güncelleştirmek için kullanılabilecek bir **Dışa Aktarma Şablonu Sihirbazı** sağlar:

1. Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin.

1. Güncelleştirmek istediğiniz şablonu seçin ve yeni projeyi oluşturmak için adımlar boyunca devam edin.

1. Visual Studio'da projeyi değiştirin. Örneğin, çıktı türünü değiştirin veya projeye yeni bir dosya ekleyin.

1. **Proje** menüsünde **Dışa Aktarma Şablonu'nu**seçin.

    **Dışa Aktarma Şablonu Sihirbazı** açılır.

1. Şablonu *.zip* dosyası olarak dışa aktarmak için sihirbazdaki istemleri izleyin.

1. (İsteğe bağlı) *.zip* dosyasını aşağıdaki dizine yerleştirin: *%USERPROFILE%\Documents\Visual Studio \<sürümü\>\Templates\ProjectTemplates'ı* seçilebilir hale getirmek için. Seçeneği seçmediyseniz bu adımı gerçekleştirmeniz gerekir **Şablonu Dışa Aktarma Şablonu Sihirbazı'nda** **Visual Studio'ya otomatik olarak aktarın.**

1. Eski şablon *.zip* dosyasını silin.

## <a name="manually-update-an-existing-template"></a>Varolan bir şablonu el ile güncelleştirme

Sıkıştırılmış *.zip* dosyasındaki dosyaları değiştirerek, **Dışa Aktarma Şablonu**Sihirbazı'nı kullanmadan varolan bir şablonu güncelleştirebilirsiniz.

### <a name="to-manually-update-an-existing-template"></a>Varolan bir şablonu el ile güncelleştirmek için

1. Şablonu içeren *.zip* dosyasını bulun. Kullanıcı proje şablonları *%USERPROFILE%\Documents\Visual Studio \<\>sürümü \Templates\ProjectTemplates*adresinde bulunur.

1. *.zip* dosyasını ayıklayın.

1. Geçerli şablon dosyalarını değiştirin veya silin veya şablona yeni dosyalar ekleyin.

1. Güncelleştirilmiş davranışı veya yeni dosyaları işlemek için *.vstemplate* XML dosyasını açın, değiştirin ve kaydedin.

    *.vstemplate* şeması hakkında daha fazla bilgi için [Visual Studio şablon şeması başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)adresine bakın. Kaynak dosyalarda neleri parametrenize ekleyebilirsiniz hakkında daha fazla bilgi için [Şablon parametrelerine](../ide/template-parameters.md)bakın.

1. Şablonunuzdaki dosyaları ve sağ tıklatma veya bağlam menüsünden seçin ve > **Sıkıştırılmış (sıkıştırılmış) klasörüne** **gönder'i**seçin.

    Seçtiğiniz dosyalar *bir .zip* dosyasına sıkıştırılır.

1. Yeni *.zip* dosyasını eski *.zip* dosyasıyla aynı dizine koyun.

1. Çıkarılan şablon dosyalarını ve eski şablon *.zip* dosyasını silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Şablon parametreleri](../ide/template-parameters.md)
