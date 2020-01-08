---
title: Mevcut proje öğesi şablonları güncelleştirme
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591365"
---
# <a name="how-to-update-existing-templates"></a>Nasıl yapılır: mevcut şablonları güncelleştirme

Bir şablon oluşturmak ve içine dosyaları sıkıştır sonra bir *.zip* dosyası şablonu değiştirmek isteyebilirsiniz. Bu işlemi, şablondaki dosyaları el ile değiştirerek veya şablonu temel alan bir projeden yeni bir şablonu dışarı aktararak yapabilirsiniz.

## <a name="use-the-export-template-wizard"></a>Şablonu dışarı aktarma Sihirbazı 'Nı kullanma

Visual Studio sağlar bir **şablonu Dışarı Aktarma Sihirbazı** mevcut bir şablonu güncellemek için kullanılabilir:

1. Menü çubuğundan **dosya** > **Yeni** > **projesi** öğesini seçin.

1. Güncelleştirmek istediğiniz şablonu seçin ve yeni projeyi oluşturma adımlarında devam edin.

1. Visual Studio'da proje değiştirin. Örneğin, çıkış türünü değiştirin veya projeye yeni bir dosya ekleyin.

1. Üzerinde **proje** menüsünde seçin **şablonu dışarı aktar**.

    **Şablonu Dışarı Aktarma Sihirbazı** açılır.

1. Şablon olarak dışarı aktarmak için sihirbazdaki istemleri izleyerek bir *.zip* dosya.

1. Seçim *. Zip* dosyasını şu dizine yerleştirin: *%userprofıle%\k\studio \<Version\>\Templates\ProjectTemplates* . Seçeneğini seçmediyseniz, bu adımı gerçekleştirmeniz gerekecektir **otomatik olarak şablonu Visual Studio'ya içeri aktarma** içinde **şablonu Dışarı Aktarma Sihirbazı**.

1. Eski Şablonu Sil *.zip* dosya.

## <a name="manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirme

Mevcut bir şablonu kullanmadan güncelleştirebilirsiniz **şablonu Dışarı Aktarma Sihirbazı**, sıkıştırılmış dosyalarda değiştirerek *.zip* dosya.

### <a name="to-manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirmek için

1. Bulun *.zip* şablonu içeren dosya. Kullanıcı proje şablonları konumu *%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ProjectTemplates*.

1. Ayıklama *.zip* dosya.

1. Değiştirmek ya da geçerli şablon dosyaları silin veya şablona yeni dosyalar ekleyin.

1. Açık, değiştirebilir ve Kaydet *.vstemplate* güncelleştirilmiş davranışı ya da yeni dosyaları işlemek için XML dosyası.

    Hakkında daha fazla bilgi için *.vstemplate* şema bakın [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md). Kaynak dosyalarında parametreleştirebilirsiniz hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

1. Dosyaları şablonunuzdaki ve sağ tıklayın veya bağlam menüsünü seçin ve seçin **göndermek** > **sıkıştırılmış (daraltılmış) klasör**.

    Seçtiğiniz dosyalar sıkıştırılmadan bir *.zip* dosya.

1. Yeni put *.zip* eski ile aynı dizinde dosya *.zip* dosya.

1. Ayıklanan şablon dosyalarını ve eski şablonu silmek *.zip* dosya.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Şablon parametreleri](../ide/template-parameters.md)
