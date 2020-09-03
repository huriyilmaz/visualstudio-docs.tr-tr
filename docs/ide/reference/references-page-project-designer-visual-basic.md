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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565610"
---
# <a name="references-page-project-designer-visual-basic"></a>Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)

Projenizdeki başvuruları, Web başvurularını ve içeri aktarılan ad alanlarını yönetmek için **Proje Tasarımcısı** ' nın **Başvurular** sayfasını kullanın. Projeler COM bileşenleri, XML Web Hizmetleri, .NET kitaplıkları veya derlemeler ya da diğer sınıf kitaplıklarına başvuru içerebilir. Başvuruları kullanma hakkında daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md).

**Başvurular** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Ardından, menü çubuğunda **Proje**, **Özellikler** ' i seçin. Proje Tasarımcısı göründüğünde, **Başvurular** sekmesine tıklayın.

## <a name="uielement-list"></a>UIElement Listesi

Aşağıdaki seçenekler, projenizdeki başvuruları ve içeri aktarılan ad alanlarını seçmenizi veya kaldırmanızı sağlar.

**Başvuru yolları**

**Başvuru yolları** iletişim kutusuna erişmek için bu düğmeye tıklayın.

> [!NOTE]
> Proje sistemi bir derleme başvurusu bulduğunda, sistem aşağıdaki konumlara bakarak başvuruyu aşağıdaki sırayla çözümler:
>
> 1. Proje klasörü. **Tüm dosyalar** etkin olmadığında proje klasörü dosyaları **Çözüm Gezgini** görüntülenir.
> 2. **Başvuru yolları** iletişim kutusunda belirtilen klasörler.
> 3. **Başvuru Ekle** iletişim kutusunda dosyaları görüntüleyen klasörler.
> 4. Projenin obj klasörü. (Projenize bir COM başvurusu eklediğinizde, projenin obj klasörüne bir veya daha fazla derleme eklenebilir.)

 **Başvurular**

Bu liste, projede kullanılan veya kullanılmayan tüm başvuruları gösterir.

 **Ekle**

**Başvurular** listesine bir başvuru veya Web başvurusu eklemek için bu düğmeye tıklayın.

Başvuru Ekle iletişim kutusunu kullanarak projenize başvuru eklemek için **başvuru** ' yı seçin.

Web başvurusu **Ekle** iletişim kutusunu kullanarak projenize Web başvurusu eklemek Için **Web başvurusu** ' nu seçin.

 **Kaldır**

**Başvurular** listesinde bir veya daha fazla başvuru seçin, sonra silmek için bu düğmeye tıklayın.

 **Web başvurusunu Güncelleştir**

**Başvurular** listesinde bir Web başvurusu seçin ve güncelleştirmek için bu düğmeye tıklayın.

 **İçeri aktarılan ad alanları**

Kendi ad alanınızı bu kutuya yazabilir ve **Kullanıcı Içeri aktarma Ekle** ' ye tıklayarak ad alanları listesine ekleyebilirsiniz.

Kullanıcı tarafından içeri aktarılan ad alanları için diğer adlar oluşturabilirsiniz. Bunu yapmak için, biçim *diğer* = *ad alanındaki*diğer adı ve ad alanını girin. Bu, uzun ad alanları kullanıyorsanız faydalıdır, örneğin: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http` .

 **Kullanıcı Içeri aktarma Ekle**

**Içeri aktarılan ad alanları** kutusunda belirtilen ad alanını içeri aktarılan ad alanları listesine eklemek için bu düğmeye tıklayın. Düğme, yalnızca belirtilen ad alanı listede yoksa etkindir.

 **Ad alanı listesi**

Bu liste tüm kullanılabilir ad alanlarını gösterir. Projenize dahil olan ad alanları için onay kutuları seçilidir.

 **Kullanıcı Içeri aktarmayı Güncelleştir**

Ad alanları listesinde Kullanıcı tarafından belirtilen bir ad alanı seçin, **Içeri aktarılan ad alanları** kutusuna değiştirmek istediğiniz adı yazın ve ardından yeni ad alanına geçmek için bu düğmeye tıklayın. Düğme, yalnızca seçilen ad alanı, **Kullanıcı Içeri aktarma Ekle** düğmesini kullanarak listeye eklediğiniz bir ise etkindir. Şunları ekleyebilirsiniz:

- Gibi sınıflar veya ad alanları <xref:System.Math?displayProperty=fullName> .

- Gibi diğer ad almalar `VB=Microsoft.VisualBasic` .

- Gibi XML ad alanları `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">` .

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md)
- [Nasıl Yapılır: İçeri Aktarılan Ad Uzaylarını Ekleme veya Kaldırma (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports Deyimi (XML Ad Alanı)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
