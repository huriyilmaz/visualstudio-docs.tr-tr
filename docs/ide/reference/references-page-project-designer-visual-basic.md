---
title: Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)
description: Projenizin başvurularını, web başvurularını ve içe aktarılan ad alanlarını yönetmek için Project Tasarımcısı'nın Başvurular sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 9c56614d835da1f03c4ef44f01be8ec0493dd6b1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625826"
---
# <a name="references-page-project-designer-visual-basic"></a>Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)

Projenize **başvuruları,** web **başvurularını ve Project** ad alanlarını yönetmek için Project Tasarımcısı'nın Başvurular sayfasını kullanın. Projeler COM bileşenlerine, XML web hizmetlerine, .NET kitaplıklarına veya derlemelere veya diğer sınıf kitaplıklarına başvurular içerebilir. Başvuruları kullanma hakkında daha fazla bilgi için [bkz. Projedeki başvuruları yönetme.](../../ide/managing-references-in-a-project.md)

Başvurular **sayfasına erişmek** için, içinde bir proje düğümü **(Çözüm** düğümü değil) **Çözüm Gezgini.** Ardından **menü Project** **, Özellikler'i** seçin. Project Tasarımcısı göründüğünde Başvurular **sekmesine** tıklayın.

## <a name="uielement-list"></a>UIElement Listesi

Aşağıdaki seçenekler, projenize başvuruları ve içe aktarılan ad alanlarını seçmenize veya kaldırmanıza olanak sağlar.

**Başvuru Yolları**

Başvuru Yolları iletişim kutusuna **erişmek için bu düğmeye** tıklayın.

> [!NOTE]
> Proje sistemi bir derleme başvurusu bulduğunda, sistem aşağıdaki konumlara bakarak başvuruya aşağıdaki sırayla çözümlemektedir:
>
> 1. Proje klasörü. Proje klasörü dosyaları, **Çözüm Gezgini** Dosyaları **Göster'in etkili** olmadığını gösterir.
> 2. Başvuru Yolları iletişim kutusunda **belirtilen klasörler.**
> 3. Başvuru Ekle iletişim kutusunda **dosyaları görüntü alan** klasörler.
> 4. Projenin obj klasörü. (Projenize com başvurusu eklerken, projenin obj klasörüne bir veya daha fazla derleme eklenebilir.)

 **Başvurular**

Bu liste, projede kullanılan veya kullanılmayan tüm başvuruları gösterir.

 **Ekle**

Başvurular listesine bir başvuru veya web başvurusu eklemek için **bu düğmeye** tıklayın.

Başvuru **Ekle** iletişim kutusunu kullanarak projenize başvuru eklemek için Başvuru'ya tıklayın.

Web **Başvurusu Ekle** iletişim kutusunu kullanarak projenize web başvurusu eklemek için Web **Başvurusu'seçin.**

 **Kaldır**

Başvurular listesinden bir veya daha **fazla başvuru** seçin ve silmek için bu düğmeye tıklayın.

 **Web Başvurularını Güncelleştirme**

Başvurular listesinden bir web **başvurusu seçin** ve güncelleştirmek için bu düğmeye tıklayın.

 **İçeri aktarılan ad alanları**

Bu kutuya kendi ad alanınızı yazarak Kullanıcı İçeri Aktarma **Ekle'ye** tıklar ve ad alanları listesine ekleyebilirsiniz.

Kullanıcı tarafından içe aktarılan ad alanları için diğer adlar oluşturabilirsiniz. Bunu yapmak için diğer adı ve ad alanını diğer ad alanı *biçiminde* = *girin.* Bu, uzun ad alanları kullanıyorsanız kullanışlıdır, örneğin: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http` .

 **Kullanıcı İçeri Aktarma Ekleme**

İçeri aktarılan ad alanları kutusunda belirtilen ad alanını **içe aktarılan ad** alanları listesine eklemek için bu düğmeye tıklayın. Düğme yalnızca belirtilen ad alanı listede yoksa etkindir.

 **Ad alanları listesi**

Bu listede kullanılabilir tüm ad alanları görüntülenir. Projenize dahil edilen ad alanlarının onay kutuları seçilidir.

 **Kullanıcı İçeri Aktarmayı Güncelleştirme**

Ad alanları listesinde kullanıcı tarafından belirtilen bir ad alanı seçin, İçeri aktarılan  ad alanları kutusuna ad alanını değiştirmek istediğiniz adı yazın ve ardından bu düğmeye tıklayarak yeni ad alanına değiştirin. Düğme yalnızca seçilen ad alanı, Kullanıcı İçeri Aktarma Ekle düğmesini kullanarak listeye eklenen ad **alanı olduğunda etkindir.** Şunları eklemek için:

- Sınıflar veya gibi ad <xref:System.Math?displayProperty=fullName> alanları.

- Gibi diğer adla içeri `VB=Microsoft.VisualBasic` aktarmalar.

- gibi XML ad `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">` alanları.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md)
- [Nasıl Yapılır: İçeri Aktarılan Ad Uzaylarını Ekleme veya Kaldırma (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports Deyimi (XML Ad Alanı)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
