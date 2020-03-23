---
title: Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b80427999ad841c493e61cd704b64435f81c3914
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565610"
---
# <a name="references-page-project-designer-visual-basic"></a>Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)

Projenizdeki başvuruları, web başvurularını ve içe aktarılan ad alanlarını yönetmek için **Proje Tasarımcısı'nın** **Başvurular** sayfasını kullanın. Projeler, COM bileşenlerine, XML web hizmetlerine, .NET kitaplıklarına veya derlemelerine veya diğer sınıf kitaplıklarına başvurular içerebilir. Başvuruları kullanma hakkında daha fazla bilgi için [bkz.](../../ide/managing-references-in-a-project.md)

**Başvurular** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümü **(Çözüm** düğümü değil) seçin. Ardından menü çubuğundaki **Project**, **Özellikler'i** seçin. Proje Tasarımcısı göründüğünde, **Başvurular** sekmesini tıklatın.

## <a name="uielement-list"></a>UIElement Listesi

Aşağıdaki seçenekler, projenizde başvuruları ve alınan ad alanlarını seçmenize veya kaldırmanıza olanak sağlar.

**Başvuru Yolları**

**Başvuru Yolları** iletişim kutusuna erişmek için bu düğmeyi tıklatın.

> [!NOTE]
> Proje sistemi bir derleme başvurusu bulduğunda, sistem aşağıdaki konumlara bakarak başvuruyu aşağıdaki sırayla çözer:
>
> 1. Proje klasörü. **Tüm Dosyaları Göster** etkin olmadığında, proje klasörü dosyaları Çözüm **Gezgini'nde** görünür.
> 2. **Başvuru Yolları** iletişim kutusunda belirtilen klasörler.
> 3. **Başvuru Ekle** iletişim kutusunda dosyaları görüntüleyen klasörler.
> 4. Projenin obj klasörü. (Projenize com başvurusu eklediğinizde, projenin obj klasörüne bir veya daha fazla derleme eklenebilir.)

 **Başvurular**

Bu liste, kullanılan veya kullanılmayan projedeki tüm başvuruları gösterir.

 **Ekle**

**Referanslar** listesine bir başvuru veya web başvurusu eklemek için bu düğmeyi tıklatın.

Başvuru Ekle iletişim kutusunu kullanarak projenize başvuru eklemek için **Başvuru'yu** seçin.

Web Başvurusu **Ekle** iletişim kutusunu kullanarak projenize web başvurusu eklemek için **Web Başvurusu'nu** seçin.

 **Kaldır**

**Referanslar** listesinde bir veya daha fazla başvuru seçin ve ardından silmek için bu düğmeyi tıklatın.

 **Web Başvurularını Güncelleştir**

**Referanslar** listesinde bir web başvurusu seçin ve güncellemek için bu düğmeyi tıklatın.

 **Alınan ad alanları**

Bu kutuya kendi ad alanınızı yazabilir ve ad alanları listesine eklemek için **Kullanıcı İçe Aktar'ı** tıklatın.

Kullanıcı tarafından içe aktarılan ad alanları için takma adlar oluşturabilirsiniz. Bunu yapmak için, diğer adı ve ad alanını biçim *ad*=*alanı'na*girin. Bu, örneğin uzun ad alanları kullanıyorsanız `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`yararlıdır: .

 **Kullanıcı İçe Aktarma Ekle**

**İçe aktarılan ad alanları** kutusuna, alınan ad alanları kutusunda belirtilen ad alanını eklemek için bu düğmeyi tıklatın. Düğme yalnızca belirtilen ad alanı listede zaten yoksa etkindir.

 **Ad alanları listesi**

Bu liste, kullanılabilir tüm ad alanlarını gösterir. Projenizde yer alan ad alanlarının onay kutuları seçilir.

 **Kullanıcı İçe Aktarma'yı Güncelleştir**

Ad alanları listesinde kullanıcı tarafından belirtilen bir ad alanı seçin, Içe Aktarılan **ad alanları** kutusuna değiştirmek istediğiniz adı yazın ve sonra yeni ad alanına değiştirmek için bu düğmeyi tıklatın. Düğme yalnızca seçili ad alanı **Kullanıcı İçe Aktarma** Ekle düğmesini kullanarak listeye eklediğiniz ad alanıysa etkindir. Şunları ekleyebilirsiniz:

- Sınıflar veya ad alanları, örneğin. <xref:System.Math?displayProperty=fullName>

- Diğer adı aktarımlar, örneğin. `VB=Microsoft.VisualBasic`

- XML ad alanları, `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`örneğin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md)
- [Nasıl Yapılır: İçeri Aktarılan Ad Uzaylarını Ekleme veya Kaldırma (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports Deyimi (XML Ad Alanı)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
